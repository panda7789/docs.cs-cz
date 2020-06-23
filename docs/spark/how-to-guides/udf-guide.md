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
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a><span data-ttu-id="12dbd-103">Vytváření uživatelem definovaných funkcí (UDF) v rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="12dbd-103">Create user-defined functions (UDF) in .NET for Apache Spark</span></span>

<span data-ttu-id="12dbd-104">V tomto článku se dozvíte, jak používat uživatelsky definované funkce (UDF) v rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="12dbd-104">In this article, you learn how to use user-defined functions (UDF) in .NET for Apache Spark.</span></span> <span data-ttu-id="12dbd-105">[UDF)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) je funkce Sparku, která umožňuje používat vlastní funkce k rozšiřování integrovaných funkcí systému.</span><span class="sxs-lookup"><span data-stu-id="12dbd-105">[UDFs)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) are a Spark feature that allow you to use custom functions to extend the system's built-in functionality.</span></span> <span data-ttu-id="12dbd-106">UDF transformuje hodnoty z jednoho řádku v tabulce a vytvoří v závislosti na logice definované v systému souborů UDF jednu odpovídající výstupní hodnotu na řádek.</span><span class="sxs-lookup"><span data-stu-id="12dbd-106">UDFs transform values from a single row within a table to produce a single corresponding output value per row based on the logic defined in the UDF.</span></span>

## <a name="define-udfs"></a><span data-ttu-id="12dbd-107">Definovat UDF</span><span class="sxs-lookup"><span data-stu-id="12dbd-107">Define UDFs</span></span>

<span data-ttu-id="12dbd-108">Zkontrolujte následující definice systému souborů UDF:</span><span class="sxs-lookup"><span data-stu-id="12dbd-108">Review the following UDF definition:</span></span>

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

<span data-ttu-id="12dbd-109">Systém souborů UDF přebírá `string` jako vstup ve formě [sloupce](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) datového [rámce](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) a vrátí objekt `string` s `hello` připojením před vstupem.</span><span class="sxs-lookup"><span data-stu-id="12dbd-109">The UDF takes a `string` as an input in the form of a [Column](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) of a [Dataframe](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) and returns a `string` with `hello` appended in front of the input.</span></span>

<span data-ttu-id="12dbd-110">Následující `df` datový rámec obsahuje seznam názvů:</span><span class="sxs-lookup"><span data-stu-id="12dbd-110">The following DataFrame `df` contains a list of names:</span></span>

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

<span data-ttu-id="12dbd-111">Teď použijte výše definovaný `udf` pro datový rámec `df` :</span><span class="sxs-lookup"><span data-stu-id="12dbd-111">Now let's apply the above defined `udf` to the DataFrame `df`:</span></span>

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

<span data-ttu-id="12dbd-112">Následující datový rámec `udfResult` je výsledkem systému souborů UDF:</span><span class="sxs-lookup"><span data-stu-id="12dbd-112">The following DataFrame `udfResult` is the result of the UDF:</span></span>

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

<span data-ttu-id="12dbd-113">Pokud chcete lépe pochopit, jak implementovat UDF, přečtěte si [pomocné funkce systému souborů UDF](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) a [Příklady](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="12dbd-113">To better understand how to implement UDFs, review the [UDF helper functions](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) and [examples](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) on GitHub.</span></span>

## <a name="udf-serialization"></a><span data-ttu-id="12dbd-114">Serializace systému souborů UDF</span><span class="sxs-lookup"><span data-stu-id="12dbd-114">UDF serialization</span></span>

<span data-ttu-id="12dbd-115">Vzhledem k tomu, že UDF jsou funkce, které je třeba spustit na pracovních procesech, musí být tyto pracovní procesy serializovány a odesílány do pracovních částí z ovladače.</span><span class="sxs-lookup"><span data-stu-id="12dbd-115">Because UDFs are functions that need to be executed on workers, they have to be serialized and sent to the workers as part of the payload from the driver.</span></span> <span data-ttu-id="12dbd-116">[Delegát](../../csharp/programming-guide/delegates/index.md), který je odkazem na metodu, musí být serializován i jeho [cíl](xref:System.Delegate.Target%2A), což je instance třídy, na které aktuální delegát vyvolá metodu instance.</span><span class="sxs-lookup"><span data-stu-id="12dbd-116">The [delegate](../../csharp/programming-guide/delegates/index.md), which is a reference to the method, needs to be serialized as well as its [target](xref:System.Delegate.Target%2A), which is the class instance on which the current delegate invokes the instance method.</span></span> <span data-ttu-id="12dbd-117">V tomto [příkladu kódu na GitHubu](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) získáte lepší přehled o tom, jak se provádí serializace systému souborů UDF.</span><span class="sxs-lookup"><span data-stu-id="12dbd-117">Review this [code example in GitHub](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) to get a better understanding of how UDF serialization is being done.</span></span>

<span data-ttu-id="12dbd-118">Rozhraní .NET pro Apache Spark používá .NET Core, které nepodporují serializaci delegátů.</span><span class="sxs-lookup"><span data-stu-id="12dbd-118">.NET for Apache Spark uses .NET Core, which doesn't support serializing delegates.</span></span> <span data-ttu-id="12dbd-119">Místo toho se reflexe používá k serializaci cíle, kde je definován delegát.</span><span class="sxs-lookup"><span data-stu-id="12dbd-119">Instead, reflection is used to serialize the target where the delegate is defined.</span></span> <span data-ttu-id="12dbd-120">Pokud je ve společném oboru definováno více delegátů, mají sdílený uzávěr, který se stal cílem reflexe pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="12dbd-120">When multiple delegates are defined in a common scope, they have a shared closure that becomes the target of reflection for serialization.</span></span>

### <a name="serialization-example"></a><span data-ttu-id="12dbd-121">Příklad serializace</span><span class="sxs-lookup"><span data-stu-id="12dbd-121">Serialization example</span></span>

<span data-ttu-id="12dbd-122">Následující fragment kódu definuje dvě řetězcové proměnné, na které se odkazuje ve dvou delegátech funkce, které vracejí příslušné řetězce v důsledku:</span><span class="sxs-lookup"><span data-stu-id="12dbd-122">The following code snippet defines two string variables that are being referenced in two function delegates that return the respective strings as a result:</span></span>

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

<span data-ttu-id="12dbd-123">Výše uvedený kód jazyka C# generuje následující kód jazyka C# zpětného překladu (kreditového zdroje: [sharplab.IO](https://sharplab.io)) z kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="12dbd-123">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="12dbd-124">`func`A `func2` sdílejí stejný uzávěr `<>c__DisplayClass0_0` , což je cíl, který je serializován při serializaci delegátů `func` a `func2` .</span><span class="sxs-lookup"><span data-stu-id="12dbd-124">Both `func` and `func2` share the same closure `<>c__DisplayClass0_0`, which is the target that is serialized when serializing the delegates `func` and `func2`.</span></span> <span data-ttu-id="12dbd-125">I když `Func<string, string> a` je odkaz pouze na `s1` , `s2` je také serializován, pokud jsou bajty odesílány pracovníkům.</span><span class="sxs-lookup"><span data-stu-id="12dbd-125">Even though `Func<string, string> a` is only referencing `s1`, `s2` is also serialized when the bytes are sent to the workers.</span></span>

<span data-ttu-id="12dbd-126">To může způsobit neočekávané chování za běhu (jako v případě použití [proměnných všesměrového vysílání](broadcast-guide.md)), což je důvod, proč doporučujeme omezit viditelnost proměnných používaných ve funkci na rozsah této funkce.</span><span class="sxs-lookup"><span data-stu-id="12dbd-126">This can lead to some unexpected behaviors at runtime (like in the case of using [broadcast variables](broadcast-guide.md)), which is why we recommend that you restrict the visibility of the variables used in a function to that function's scope.</span></span>

<span data-ttu-id="12dbd-127">Následující fragment kódu je doporučeným způsobem, jak implementovat požadované chování serializace:</span><span class="sxs-lookup"><span data-stu-id="12dbd-127">The following code snippet is the recommended way to implement the desired serialization behavior:</span></span>

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

<span data-ttu-id="12dbd-128">Výše uvedený kód jazyka C# generuje následující kód jazyka C# zpětného překladu (kreditového zdroje: [sharplab.IO](https://sharplab.io)) z kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="12dbd-128">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="12dbd-129">Všimněte si, že `func` ani `func2` nadále nesdílí uzavření a mají vlastní samostatné uzávěry `<>c__DisplayClass0_0` a `<>c__DisplayClass0_1` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="12dbd-129">Notice that `func` and `func2` no longer share a closure, and they have their own separate closures `<>c__DisplayClass0_0` and `<>c__DisplayClass0_1` respectively.</span></span> <span data-ttu-id="12dbd-130">Při použití jako cíle pro serializaci nebude pro delegáta serializována žádná jiná než odkazovaná proměnná.</span><span class="sxs-lookup"><span data-stu-id="12dbd-130">When used as the target for serialization, nothing other than the referenced variables will get serialized for the delegate.</span></span> <span data-ttu-id="12dbd-131">Toto chování je důležité vzít v úvahu při implementaci více UDF ve společném oboru.</span><span class="sxs-lookup"><span data-stu-id="12dbd-131">This behavior is important to keep in mind while implementing multiple UDFs in a common scope.</span></span>

## <a name="some-spark-udf-caveats"></a><span data-ttu-id="12dbd-132">Některá upozornění Sparku UDF</span><span class="sxs-lookup"><span data-stu-id="12dbd-132">Some Spark UDF caveats</span></span>

* <span data-ttu-id="12dbd-133">Hodnoty null v UDF mohou vyvolat výjimky.</span><span class="sxs-lookup"><span data-stu-id="12dbd-133">Null values in UDFs can throw exceptions.</span></span> <span data-ttu-id="12dbd-134">Je zodpovědný vývojář, který je zpracovává.</span><span class="sxs-lookup"><span data-stu-id="12dbd-134">It's the responsibility of the developer to handle them.</span></span>
* <span data-ttu-id="12dbd-135">UDF nevyužívá optimalizace poskytované integrovanými funkcemi Spark, takže se doporučuje použít vestavěné funkce, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="12dbd-135">UDFs don't leverage the optimizations provided by Spark's built-in functions, so it's recommended to use built-in functions where possible.</span></span>

## <a name="next-steps"></a><span data-ttu-id="12dbd-136">Další kroky</span><span class="sxs-lookup"><span data-stu-id="12dbd-136">Next steps</span></span>

* [<span data-ttu-id="12dbd-137">Začínáme s .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="12dbd-137">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="12dbd-138">Ladění rozhraní .NET pro Apache Spark aplikaci ve Windows</span><span class="sxs-lookup"><span data-stu-id="12dbd-138">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
