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
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a><span data-ttu-id="6fe3a-103">Použití proměnných všesměrového vysílání v rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="6fe3a-103">Use broadcast variables in .NET for Apache Spark</span></span>

<span data-ttu-id="6fe3a-104">V tomto článku se dozvíte, jak používat proměnné všesměrového vysílání v rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-104">In this article, you learn how to use broadcast variables in .NET for Apache Spark.</span></span> <span data-ttu-id="6fe3a-105">[Proměnné všesměrového vysílání v Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) jsou mechanismy pro sdílení proměnných v rámci prováděcích modulů, které jsou určeny jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-105">[Broadcast variables in Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) are mechanisms for sharing variables across executors that are meant to be read-only.</span></span> <span data-ttu-id="6fe3a-106">Proměnné všesměrového vysílání umožňují uchovávat v každém počítači proměnnou, která je jen pro čtení uložená v mezipaměti, a ne jejich kopii s úkoly.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-106">Broadcast variables allow you to keep a read-only variable cached on each machine rather than shipping a copy of it with tasks.</span></span> <span data-ttu-id="6fe3a-107">Pomocí proměnných všesměrového vysílání můžete každému uzlu přidělit kopii velké vstupní datové sady účinným způsobem.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-107">You can use broadcast variables to give every node a copy of a large input dataset in an efficient manner.</span></span>

<span data-ttu-id="6fe3a-108">Vzhledem k tomu, že jsou data posílána pouze jednou, mají proměnné vysílání výkonnostní přínosy ve srovnání s místními proměnnými, které jsou odeslány vykonavatelům s každou úlohou.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-108">Because the data is sent only once, broadcast variables have performance benefits when compared to local variables that are shipped to the executors with each task.</span></span> <span data-ttu-id="6fe3a-109">Podívejte se na [oficiální dokumentaci k proměnným všesměrového vysílání](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) , kde získáte hlubší znalosti proměnných všesměrového vysílání a důvody, proč se používají.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-109">Refer to the [official broadcast variable documentation](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) to get a deeper understanding of broadcast variables and why they are used.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="create-broadcast-variables"></a><span data-ttu-id="6fe3a-110">Vytvořit proměnné vysílání</span><span class="sxs-lookup"><span data-stu-id="6fe3a-110">Create broadcast variables</span></span>

<span data-ttu-id="6fe3a-111">Chcete-li vytvořit proměnnou všesměrového vysílání, zavolejte `SparkContext.Broadcast(v)` pro libovolnou proměnnou `v` .</span><span class="sxs-lookup"><span data-stu-id="6fe3a-111">To create a broadcast variable, call `SparkContext.Broadcast(v)` for any variable `v`.</span></span> <span data-ttu-id="6fe3a-112">Proměnná všesměrového vysílání je Obálka kolem proměnné `v` a její hodnota je k dispozici při volání `Value()` metody.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-112">The broadcast variable is a wrapper around the variable `v`, and its value can be accessed by calling the `Value()` method.</span></span>

<span data-ttu-id="6fe3a-113">V následujícím fragmentu kódu je vytvořena řetězcová proměnná `v` a při volání je vytvořena proměnná všesměrového vysílání `bv` `SparkContext.Broadcast(v)` .</span><span class="sxs-lookup"><span data-stu-id="6fe3a-113">In the following code snippet, a string variable `v` is created, and a broadcast variable `bv` is created when `SparkContext.Broadcast(v)`is called.</span></span> <span data-ttu-id="6fe3a-114">Všimněte si, že parametr typu pro `Broadcast` řetězec odpovídá typu proměnné, která se vysílá.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-114">Notice the type parameter for `Broadcast`, string, matches the type of the variable being broadcasted.</span></span> <span data-ttu-id="6fe3a-115">Uživatelsky definovaná funkce (UDF) vrací hodnotu `bv` .</span><span class="sxs-lookup"><span data-stu-id="6fe3a-115">The user-defined function (UDF) returns the value of `bv`.</span></span>

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a><span data-ttu-id="6fe3a-116">Odstranit proměnné vysílání</span><span class="sxs-lookup"><span data-stu-id="6fe3a-116">Delete broadcast variables</span></span>

<span data-ttu-id="6fe3a-117">Proměnnou vysílání lze odstranit ze všech prováděcích modulů voláním `Destroy()` metody.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-117">The broadcast variable can be deleted from all executors by calling the `Destroy()` method.</span></span>

```csharp
bv.Destroy();
```

<span data-ttu-id="6fe3a-118">`Destroy()`odstraní všechna data a metadata související s proměnnou všesměrového vysílání a měla by se používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-118">`Destroy()` deletes all data and metadata related to the broadcast variable and should be used with caution.</span></span> <span data-ttu-id="6fe3a-119">Jakmile je proměnná všesměrového vysílání zničena, nelze ji znovu použít.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-119">Once a broadcast variable is destroyed, it can't be used again.</span></span>

## <a name="limit-broadcast-variable-scope-in-udfs"></a><span data-ttu-id="6fe3a-120">Omezení oboru proměnné všesměrového vysílání v UDF</span><span class="sxs-lookup"><span data-stu-id="6fe3a-120">Limit broadcast variable scope in UDFs</span></span>

<span data-ttu-id="6fe3a-121">Při použití proměnných vysílání v UDF je nutné omezit rozsah proměnné pouze na systém UDF, který odkazuje na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-121">When you use broadcast variables in UDFs, you need to limit the scope of the variable to only the UDF that is referencing the variable.</span></span> <span data-ttu-id="6fe3a-122">[Návod k používání UDF](udf-guide.md) popisuje tento jev podrobněji.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-122">The [guide to using UDFs](udf-guide.md) describes this phenomenon in detail.</span></span> <span data-ttu-id="6fe3a-123">Obor je obzvláště rozhodující při volání `Destroy()` proměnné všesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-123">Scope is especially crucial when you call `Destroy()` on the broadcast variable.</span></span>

<span data-ttu-id="6fe3a-124">Pokud je proměnná všesměrového vysílání, která byla zničena, viditelná nebo přístupná z jiných UDF, získá se pro serializaci všemi UDF, i když na ně neodkazuje.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-124">If the broadcast variable that has been destroyed is visible to or accessible from other UDFs, it gets picked up for serialization by all of the UDFs, even if it is not being referenced by them.</span></span> <span data-ttu-id="6fe3a-125">Rozhraní .NET pro Apache Spark nemůže serializovat zničenou proměnnou všesměrového vysílání, což má za následek chybu.</span><span class="sxs-lookup"><span data-stu-id="6fe3a-125">.NET for Apache Spark is unable to serialize the destroyed broadcast variable, which results in an error.</span></span> <span data-ttu-id="6fe3a-126">Následující fragment kódu ukazuje tuto chybu:</span><span class="sxs-lookup"><span data-stu-id="6fe3a-126">The following code snippet demonstrates this error:</span></span>

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

<span data-ttu-id="6fe3a-127">Následující fragment kódu ukazuje, jak zajistit, aby zničení `bv` neovlivnilo `udf2` kvůli neočekávanému chování serializace:</span><span class="sxs-lookup"><span data-stu-id="6fe3a-127">The following code snippet demonstrates how to ensure that destroying `bv` doesn't affect `udf2` because of an unexpected serialization behavior:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="6fe3a-128">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6fe3a-128">Next steps</span></span>

* [<span data-ttu-id="6fe3a-129">Začínáme s .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="6fe3a-129">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="6fe3a-130">Ladění rozhraní .NET pro Apache Spark aplikaci ve Windows</span><span class="sxs-lookup"><span data-stu-id="6fe3a-130">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
* [<span data-ttu-id="6fe3a-131">Nasazení rozhraní .NET pro Apache Spark pro pracovní procesy a uživatelem definované binární soubory funkcí</span><span class="sxs-lookup"><span data-stu-id="6fe3a-131">Deploy .NET for Apache Spark worker and user-defined function binaries</span></span>](deploy-worker-udf-binaries.md)
