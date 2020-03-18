---
title: Co je nového v jazyce C# 7.1
description: Přehled nových funkcí v C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: 5d2d6f51b6422f5b4db5c6bd275b5ffce1f695f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399705"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="f9be4-103">Co je nového v jazyce C# 7.1</span><span class="sxs-lookup"><span data-stu-id="f9be4-103">What's new in C# 7.1</span></span>

<span data-ttu-id="f9be4-104">C# 7.1 je první bod vydání jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="f9be4-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="f9be4-105">To znamená zvýšenou kadenci uvolňování pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="f9be4-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="f9be4-106">Nové funkce můžete použít dříve, ideálně když je každá nová funkce připravena.</span><span class="sxs-lookup"><span data-stu-id="f9be4-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="f9be4-107">C# 7.1 přidává možnost nakonfigurovat kompilátor tak, aby odpovídal zadané verzi jazyka.</span><span class="sxs-lookup"><span data-stu-id="f9be4-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="f9be4-108">To umožňuje oddělit rozhodnutí o upgradu nástroje z rozhodnutí o upgradu jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="f9be4-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="f9be4-109">C# 7.1 přidá prvek konfigurace [výběru jazykové verze,](../language-reference/configure-language-version.md) tři nové funkce jazyka a nové chování kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f9be4-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="f9be4-110">Nové jazykové funkce v této verzi jsou:</span><span class="sxs-lookup"><span data-stu-id="f9be4-110">The new language features in this release are:</span></span>

- [<span data-ttu-id="f9be4-111">`async``Main` metoda</span><span class="sxs-lookup"><span data-stu-id="f9be4-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="f9be4-112">Vstupní bod pro aplikaci `async` může mít modifikátor.</span><span class="sxs-lookup"><span data-stu-id="f9be4-112">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="f9be4-113">`default`doslovné výrazy</span><span class="sxs-lookup"><span data-stu-id="f9be4-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="f9be4-114">Výchozí literálové výrazy můžete použít ve výchozích výrazech hodnoty, když lze odvodit cílový typ.</span><span class="sxs-lookup"><span data-stu-id="f9be4-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="f9be4-115">Odvozené názvy prvků řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="f9be4-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="f9be4-116">Názvy prvků řazené kolekce členů lze odvodit z inicializace řazené kolekce členů v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="f9be4-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
- [<span data-ttu-id="f9be4-117">Porovnávání vzorů u parametrů obecného typu</span><span class="sxs-lookup"><span data-stu-id="f9be4-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="f9be4-118">Výrazy shody vzoru můžete použít u proměnných, jejichž typ je parametrem obecného typu.</span><span class="sxs-lookup"><span data-stu-id="f9be4-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="f9be4-119">Nakonec kompilátor má `-refout` dvě `-refonly` možnosti a že generování [sestavení referenční](#reference-assembly-generation)ovládací prvek .</span><span class="sxs-lookup"><span data-stu-id="f9be4-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="f9be4-120">Chcete-li v bodové verzi používat nejnovější funkce, je třeba [nakonfigurovat jazykovou verzi kompilátoru](../language-reference/configure-language-version.md) a vybrat její verzi.</span><span class="sxs-lookup"><span data-stu-id="f9be4-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="f9be4-121">Zbývající část tohoto článku obsahuje přehled jednotlivých funkcí.</span><span class="sxs-lookup"><span data-stu-id="f9be4-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="f9be4-122">U každé funkce se dozvíte důvody, které za ní stojí.</span><span class="sxs-lookup"><span data-stu-id="f9be4-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="f9be4-123">Naučíte se syntaxi.</span><span class="sxs-lookup"><span data-stu-id="f9be4-123">You'll learn the syntax.</span></span> <span data-ttu-id="f9be4-124">Tyto funkce můžete prozkoumat ve `dotnet try` vašem prostředí pomocí globálního nástroje:</span><span class="sxs-lookup"><span data-stu-id="f9be4-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="f9be4-125">Nainstalujte globální nástroj [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)</span><span class="sxs-lookup"><span data-stu-id="f9be4-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="f9be4-126">Klonovat úložiště [dotnet/try-samples.](https://github.com/dotnet/try-samples)</span><span class="sxs-lookup"><span data-stu-id="f9be4-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="f9be4-127">Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *try-samples.*</span><span class="sxs-lookup"><span data-stu-id="f9be4-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="f9be4-128">Spusťte `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="f9be4-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="f9be4-129">Asynchronní hlavní</span><span class="sxs-lookup"><span data-stu-id="f9be4-129">Async main</span></span>

<span data-ttu-id="f9be4-130">*Asynchronní hlavní* metoda umožňuje `await` použít `Main` ve vaší metodě.</span><span class="sxs-lookup"><span data-stu-id="f9be4-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="f9be4-131">Dříve budete muset napsat:</span><span class="sxs-lookup"><span data-stu-id="f9be4-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="f9be4-132">Nyní můžete napsat:</span><span class="sxs-lookup"><span data-stu-id="f9be4-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="f9be4-133">Pokud program nevrátí ukončovací kód, můžete `Main` deklarovat metodu, která vrací <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="f9be4-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="f9be4-134">Můžete si přečíst více o podrobnostech v hlavním článku [asynchronní](../programming-guide/main-and-command-args/index.md) v programovací příručce.</span><span class="sxs-lookup"><span data-stu-id="f9be4-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="f9be4-135">Výchozí literálové výrazy</span><span class="sxs-lookup"><span data-stu-id="f9be4-135">Default literal expressions</span></span>

<span data-ttu-id="f9be4-136">Výchozí literálové výrazy jsou vylepšením výchozích výrazů hodnot.</span><span class="sxs-lookup"><span data-stu-id="f9be4-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="f9be4-137">Tyto výrazy inicializují proměnnou na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f9be4-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="f9be4-138">Kde jste dříve napsali:</span><span class="sxs-lookup"><span data-stu-id="f9be4-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="f9be4-139">Nyní můžete vynechat typ na pravé straně inicializace:</span><span class="sxs-lookup"><span data-stu-id="f9be4-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="f9be4-140">Další informace naleznete ve [výchozím části literálu](../language-reference/operators/default.md#default-literal) v článku [výchozího operátora.](../language-reference/operators/default.md)</span><span class="sxs-lookup"><span data-stu-id="f9be4-140">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="f9be4-141">Odvozené názvy prvků řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="f9be4-141">Inferred tuple element names</span></span>

<span data-ttu-id="f9be4-142">Tato funkce je malé vylepšení funkce řazené kolekce členů zavedené v C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="f9be4-142">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="f9be4-143">Mnohokrát při inicializaci n-tice, proměnné použité pro pravé straně přiřazení jsou stejné jako názvy, které chcete pro n-tice prvky:</span><span class="sxs-lookup"><span data-stu-id="f9be4-143">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="f9be4-144">Názvy n-tice prvky lze odvodit z proměnné použité k inicializaci n-tice v C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="f9be4-144">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="f9be4-145">Další informace o této funkci najdete v článku [n-tic.](../tuples.md)</span><span class="sxs-lookup"><span data-stu-id="f9be4-145">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="f9be4-146">Porovnávání vzorů u parametrů obecného typu</span><span class="sxs-lookup"><span data-stu-id="f9be4-146">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="f9be4-147">Počínaje C# 7.1, vzor `is` výraz `switch` a vzorek typu může mít typ parametru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="f9be4-147">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="f9be4-148">To může být nejužitečnější při kontrole `struct` `class` typů, které mohou být buď nebo typy a chcete se vyhnout zabalení.</span><span class="sxs-lookup"><span data-stu-id="f9be4-148">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="f9be4-149">Generování referenčního sestavení</span><span class="sxs-lookup"><span data-stu-id="f9be4-149">Reference assembly generation</span></span>

<span data-ttu-id="f9be4-150">Existují dvě nové možnosti kompilátoru, které generují *sestavení pouze pro odkazy*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) a [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f9be4-150">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="f9be4-151">Propojené články vysvětlují tyto možnosti a referenční sestavení podrobněji.</span><span class="sxs-lookup"><span data-stu-id="f9be4-151">The linked articles explain these options and reference assemblies in more detail.</span></span>
