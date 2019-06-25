---
title: Co je nového v C# 7.1
description: Přehled nových funkcí v C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: a95111b6f217a2ca5c520c2d4d70efa0e23742f9
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347606"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="f4b7b-103">Co je nového v C# 7.1</span><span class="sxs-lookup"><span data-stu-id="f4b7b-103">What's new in C# 7.1</span></span>

<span data-ttu-id="f4b7b-104">C#7.1 je první verzi bodu C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="f4b7b-105">Označí zvýšená četnost pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="f4b7b-106">Můžete použít nové funkce dřív, ideálně při každé nové funkce je připravený.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="f4b7b-107">C#7.1 přidává možnost nakonfigurovat tak, aby odpovídaly zadaná verze jazyka kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="f4b7b-108">Která umožňuje oddělit rozhodnutí o upgradu nástroje z rozhodnutí o upgradu jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="f4b7b-109">C#7.1 přidává [výběr verze jazyka](../language-reference/configure-language-version.md) prvek konfigurace, tři nové funkce jazyků a nové chování kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="f4b7b-110">Nové funkce jazyků v této verzi jsou:</span><span class="sxs-lookup"><span data-stu-id="f4b7b-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="f4b7b-111">`async` `Main` – Metoda</span><span class="sxs-lookup"><span data-stu-id="f4b7b-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="f4b7b-112">Vstupní bod pro aplikaci může mít `async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="f4b7b-113">`default` literálové výrazy</span><span class="sxs-lookup"><span data-stu-id="f4b7b-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="f4b7b-114">Když jde odvodit typ cíle, můžete použít výchozí literál výrazy v výrazy s výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="f4b7b-115">Názvy elementů řazené kolekce členů odvozeného</span><span class="sxs-lookup"><span data-stu-id="f4b7b-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="f4b7b-116">Názvy elementů řazené kolekce členů lze odvodit z inicializace řazené kolekce členů v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
* [<span data-ttu-id="f4b7b-117">Porovnávání vzorů v parametrech obecného typu</span><span class="sxs-lookup"><span data-stu-id="f4b7b-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="f4b7b-118">Vzor odpovídající výrazy můžete použít pro proměnné jehož typ je parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="f4b7b-119">A konečně, má kompilátor dvě možnosti `-refout` a `-refonly` ovládacího prvku [odkazovat na generování sestavení](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="f4b7b-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="f4b7b-120">Chcete-li používat nejnovější funkce ve verzi bod, je potřeba [konfigurace verze jazyka kompilátoru](../language-reference/configure-language-version.md) a vyberte verzi.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="f4b7b-121">Zbývající část tohoto článku poskytuje přehled o jednotlivých funkcí.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="f4b7b-122">Pro jednotlivé funkce dozvíte zdůvodnění.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="f4b7b-123">Dozvíte syntaxe.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-123">You'll learn the syntax.</span></span> <span data-ttu-id="f4b7b-124">Můžete prozkoumat tyto funkce v prostředí pomocí `dotnet try` globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="f4b7b-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="f4b7b-125">Nainstalujte [dotnet – zkuste](https://github.com/dotnet/try/blob/master/README.md#setup) globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="f4b7b-126">Klonování [dotnet/try-samples](https://github.com/dotnet/try-samples) úložiště.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="f4b7b-127">Nastavit aktuální adresář *csharp7* podadresář pro *try-samples* úložiště.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="f4b7b-128">Spusťte `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="f4b7b-129">Asynchronní funkce main</span><span class="sxs-lookup"><span data-stu-id="f4b7b-129">Async main</span></span>

<span data-ttu-id="f4b7b-130">*Asynchronní funkce main* metoda vám umožňuje používat `await` ve vaší `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="f4b7b-131">Dříve byste museli napsat:</span><span class="sxs-lookup"><span data-stu-id="f4b7b-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="f4b7b-132">Teď můžete psát:</span><span class="sxs-lookup"><span data-stu-id="f4b7b-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="f4b7b-133">Pokud váš program nevrací ukončovací kód, lze deklarovat `Main` metodu, která vrací <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="f4b7b-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="f4b7b-134">Další informace o podrobnosti v [asynchronní funkce main](../programming-guide/main-and-command-args/index.md) článek v průvodce programováním.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="f4b7b-135">Výchozí literál výrazy</span><span class="sxs-lookup"><span data-stu-id="f4b7b-135">Default literal expressions</span></span>

<span data-ttu-id="f4b7b-136">Jsou výchozí literál výrazy neboli podmínky vylepšují výrazy s výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="f4b7b-137">Tyto výrazy inicializovat proměnnou na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="f4b7b-138">Dříve by píšete:</span><span class="sxs-lookup"><span data-stu-id="f4b7b-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="f4b7b-139">Nyní můžete vynechat typu inicializace na pravé straně:</span><span class="sxs-lookup"><span data-stu-id="f4b7b-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="f4b7b-140">Další informace o toto vylepšení v C# Průvodce programováním pro službu článek věnovaný tomu [výchozí hodnotu výrazy](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f4b7b-140">You can learn more about this enhancement in the C# Programming Guide article on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="f4b7b-141">Toto vylepšení se také změní některé z pravidla analýzy pro [default – klíčové slovo](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="f4b7b-141">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="f4b7b-142">Názvy elementů řazené kolekce členů odvozeného</span><span class="sxs-lookup"><span data-stu-id="f4b7b-142">Inferred tuple element names</span></span>

<span data-ttu-id="f4b7b-143">Tato funkce je malá vylepšení pro řazené kolekce členů funkce představená v C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-143">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="f4b7b-144">V mnoha případech při inicializaci řazené kolekce členů proměnných, které slouží k pravému okraji přiřazení jsou stejné jako názvy, které chcete pro elementů řazené kolekce členů:</span><span class="sxs-lookup"><span data-stu-id="f4b7b-144">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="f4b7b-145">Názvy elementů řazené kolekce členů lze odvodit z proměnných, které slouží k inicializaci řazené kolekce členů v C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="f4b7b-145">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="f4b7b-146">Další informace o tuto funkci [řazených kolekcí členů](../tuples.md) článku.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-146">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="f4b7b-147">Porovnávání vzorů v parametrech obecného typu</span><span class="sxs-lookup"><span data-stu-id="f4b7b-147">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="f4b7b-148">Počínaje C# 7.1, výraz vzoru `is` a `switch` vzor typu může mít typ parametru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-148">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="f4b7b-149">To může být zvláště užitečná při kontrole typy, které může být buď `struct` nebo `class` typy a chcete, aby se zabránilo zabalení.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-149">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="f4b7b-150">Generování sestavení odkazu</span><span class="sxs-lookup"><span data-stu-id="f4b7b-150">Reference assembly generation</span></span>

<span data-ttu-id="f4b7b-151">Existují dvě nové možnosti kompilátoru, které generují *pouze odkaz na sestavení*: [- refout](../language-reference/compiler-options/refout-compiler-option.md) a [- refout](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f4b7b-151">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="f4b7b-152">Propojené články popisují tyto možnosti a referenční sestavení podrobněji.</span><span class="sxs-lookup"><span data-stu-id="f4b7b-152">The linked articles explain these options and reference assemblies in more detail.</span></span>
