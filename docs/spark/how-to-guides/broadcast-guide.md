---
title: Použití proměnných všesměrového vysílání v rozhraní .NET pro Apache Spark
description: Naučte se používat v rozhraní .NET proměnné všesměrového vysílání pro Apache Spark aplikace.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: d86b160855cc4d3f3a6502f5606d4766b7c06aa0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617853"
---
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a>Použití proměnných všesměrového vysílání v rozhraní .NET pro Apache Spark

V tomto článku se dozvíte, jak používat proměnné všesměrového vysílání v rozhraní .NET pro Apache Spark. [Proměnné všesměrového vysílání v Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) jsou mechanismy pro sdílení proměnných v rámci prováděcích modulů, které jsou určeny jen pro čtení. Proměnné všesměrového vysílání umožňují uchovávat v každém počítači proměnnou, která je jen pro čtení uložená v mezipaměti, a ne jejich kopii s úkoly. Pomocí proměnných všesměrového vysílání můžete každému uzlu přidělit kopii velké vstupní datové sady účinným způsobem.

Vzhledem k tomu, že jsou data posílána pouze jednou, mají proměnné vysílání výkonnostní přínosy ve srovnání s místními proměnnými, které jsou odeslány vykonavatelům s každou úlohou. Podívejte se na [oficiální dokumentaci k proměnným všesměrového vysílání](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) , kde získáte hlubší znalosti proměnných všesměrového vysílání a důvody, proč se používají.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="create-broadcast-variables"></a>Vytvořit proměnné vysílání

Chcete-li vytvořit proměnnou všesměrového vysílání, zavolejte `SparkContext.Broadcast(v)` pro libovolnou proměnnou `v` . Proměnná všesměrového vysílání je Obálka kolem proměnné `v` a její hodnota je k dispozici při volání `Value()` metody.

V následujícím fragmentu kódu je vytvořena řetězcová proměnná `v` a při volání je vytvořena proměnná všesměrového vysílání `bv` `SparkContext.Broadcast(v)` . Všimněte si, že parametr typu pro `Broadcast` řetězec odpovídá typu proměnné, která se vysílá. Uživatelsky definovaná funkce (UDF) vrací hodnotu `bv` .

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a>Odstranit proměnné vysílání

Proměnnou vysílání lze odstranit ze všech prováděcích modulů voláním `Destroy()` metody.

```csharp
bv.Destroy();
```

`Destroy()`odstraní všechna data a metadata související s proměnnou všesměrového vysílání a měla by se používat opatrně. Jakmile je proměnná všesměrového vysílání zničena, nelze ji znovu použít.

## <a name="limit-broadcast-variable-scope-in-udfs"></a>Omezení oboru proměnné všesměrového vysílání v UDF

Při použití proměnných vysílání v UDF je nutné omezit rozsah proměnné pouze na systém UDF, který odkazuje na proměnnou. [Návod k používání UDF](udf-guide.md) popisuje tento jev podrobněji. Obor je obzvláště rozhodující při volání `Destroy()` proměnné všesměrového vysílání.

Pokud je proměnná všesměrového vysílání, která byla zničena, viditelná nebo přístupná z jiných UDF, získá se pro serializaci všemi UDF, i když na ně neodkazuje. Rozhraní .NET pro Apache Spark nemůže serializovat zničenou proměnnou všesměrového vysílání, což má za následek chybu. Následující fragment kódu ukazuje tuto chybu:

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

// Using the broadcast variable in a UDF:
Func<Column, Column> udf1 = Udf<string, string>(
    str => $"{str}: {bv.Value()}");

// Destroying bv
bv.Destroy();

// Calling udf1 after destroying bv throws the following expected exception:
// org.apache.spark.SparkException: Attempted to use Broadcast(0) after it was destroyed
df.Select(udf1(df["_1"])).Show();

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 throws the following (unexpected) exception:
// [Error] [JvmBridge] org.apache.spark.SparkException: Task not serializable
df.Select(udf2(df["_1"])).Show();
```

Následující fragment kódu ukazuje, jak zajistit, aby zničení `bv` neovlivnilo `udf2` kvůli neočekávanému chování serializace:

```csharp
string v = "Variable to be broadcasted";
// Restricting the visibility of bv to only the UDF referencing it
{
    Broadcast<string> bv = SparkContext.Broadcast(v);

    // Using the broadcast variable in a UDF:
    Func<Column, Column> udf1 = Udf<string, string>(
        str => $"{str}: {bv.Value()}");

    // Destroying bv
    bv.Destroy();
}

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 works fine as expected
df.Select(udf2(df["_1"])).Show();
```

## <a name="next-steps"></a>Další kroky

* [Začínáme s .NET pro Apache Spark](../tutorials/get-started.md)
* [Ladění rozhraní .NET pro Apache Spark aplikaci ve Windows](debug.md)
* [Nasazení rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí](deploy-worker-udf-binaries.md)
