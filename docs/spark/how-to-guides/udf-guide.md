---
title: Vytváření uživatelem definovaných funkcí (UDF) v rozhraní .NET pro Apache Spark
description: Naučte se implementovat uživatelsky definované funkce (UDF) v rozhraní .NET pro Apache Spark aplikace.
ms.date: 06/11/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: fe3dec187f94f84adb1217c39ff6aabc4b4db1c5
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2020
ms.locfileid: "85142014"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a>Vytváření uživatelem definovaných funkcí (UDF) v rozhraní .NET pro Apache Spark

V tomto článku se dozvíte, jak používat uživatelsky definované funkce (UDF) v rozhraní .NET pro Apache Spark. [UDF)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) je funkce Sparku, která umožňuje používat vlastní funkce k rozšiřování integrovaných funkcí systému. UDF transformuje hodnoty z jednoho řádku v tabulce a vytvoří v závislosti na logice definované v systému souborů UDF jednu odpovídající výstupní hodnotu na řádek.

## <a name="define-udfs"></a>Definovat UDF

Zkontrolujte následující definice systému souborů UDF:

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

Systém souborů UDF přebírá `string` jako vstup ve formě [sloupce](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) datového [rámce](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) a vrátí objekt `string` s `hello` připojením před vstupem.

Následující `df` datový rámec obsahuje seznam názvů:

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

Teď použijte výše definovaný `udf` pro datový rámec `df` :

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

Následující datový rámec `udfResult` je výsledkem systému souborů UDF:

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

Pokud chcete lépe pochopit, jak implementovat UDF, přečtěte si [pomocné funkce systému souborů UDF](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) a [Příklady](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) na GitHubu.

## <a name="udf-serialization"></a>Serializace systému souborů UDF

Vzhledem k tomu, že UDF jsou funkce, které je třeba spustit na pracovních procesech, musí být tyto pracovní procesy serializovány a odesílány do pracovních částí z ovladače. [Delegát](../../csharp/programming-guide/delegates/index.md), který je odkazem na metodu, musí být serializován i jeho [cíl](xref:System.Delegate.Target%2A), což je instance třídy, na které aktuální delegát vyvolá metodu instance. V tomto [příkladu kódu na GitHubu](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) získáte lepší přehled o tom, jak se provádí serializace systému souborů UDF.

Rozhraní .NET pro Apache Spark používá .NET Core, které nepodporují serializaci delegátů. Místo toho se reflexe používá k serializaci cíle, kde je definován delegát. Pokud je ve společném oboru definováno více delegátů, mají sdílený uzávěr, který se stal cílem reflexe pro serializaci.

### <a name="serialization-example"></a>Příklad serializace

Následující fragment kódu definuje dvě řetězcové proměnné, na které se odkazuje ve dvou delegátech funkce, které vracejí příslušné řetězce v důsledku:

```csharp
using System;

public class C {
    public void M() {
        string s1 = "s1";
        string s2 = "s2";
        Func<string, string> a = str => s1;
        Func<string, string> b = str => s2;
    }
}
```

Výše uvedený kód jazyka C# generuje následující kód jazyka C# zpětného překladu (kreditového zdroje: [sharplab.IO](https://sharplab.io)) z kompilátoru:

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        public string s2;

        internal string <M>b__0(string str)
        {
            return s1;
        }

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        <>c__DisplayClass0_.s2 = "s2";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_.<M>b__1);
    }
}
```

`func`A `func2` sdílejí stejný uzávěr `<>c__DisplayClass0_0` , což je cíl, který je serializován při serializaci delegátů `func` a `func2` . I když `Func<string, string> a` je odkaz pouze na `s1` , `s2` je také serializován, pokud jsou bajty odesílány pracovníkům.

To může způsobit neočekávané chování za běhu (jako v případě použití [proměnných všesměrového vysílání](broadcast-guide.md)), což je důvod, proč doporučujeme omezit viditelnost proměnných používaných ve funkci na rozsah této funkce.

Následující fragment kódu je doporučeným způsobem, jak implementovat požadované chování serializace:

```csharp
using System;

public class C {
    public void M() {
        {
            string s1 = "s1";
            Func<string, string> a = str => s1;
        }
        {
            string s2 = "s2";
            Func<string, string> b = str => s2;
        }
    }
}
```

Výše uvedený kód jazyka C# generuje následující kód jazyka C# zpětného překladu (kreditového zdroje: [sharplab.IO](https://sharplab.io)) z kompilátoru:

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        internal string <M>b__0(string str)
        {
            return s1;
        }
    }

    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_1
    {
        public string s2;

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        <>c__DisplayClass0_1 <>c__DisplayClass0_2 = new <>c__DisplayClass0_1();
        <>c__DisplayClass0_2.s2 = "s2";
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_2.<M>b__1);
    }
}
```

Všimněte si, že `func` ani `func2` nadále nesdílí uzavření a mají vlastní samostatné uzávěry `<>c__DisplayClass0_0` a `<>c__DisplayClass0_1` v uvedeném pořadí. Při použití jako cíle pro serializaci nebude pro delegáta serializována žádná jiná než odkazovaná proměnná. Toto chování je důležité vzít v úvahu při implementaci více UDF ve společném oboru.

## <a name="some-spark-udf-caveats"></a>Některá upozornění Sparku UDF

* Hodnoty null v UDF mohou vyvolat výjimky. Je zodpovědný vývojář, který je zpracovává.
* UDF nevyužívá optimalizace poskytované integrovanými funkcemi Spark, takže se doporučuje použít vestavěné funkce, pokud je to možné.

## <a name="next-steps"></a>Další kroky

* [Začínáme s .NET pro Apache Spark](../tutorials/get-started.md)
* [Ladění rozhraní .NET pro Apache Spark aplikaci ve Windows](debug.md)
