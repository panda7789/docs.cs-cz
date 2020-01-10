---
title: Co je nového v C# 7,1
description: Přehled nových funkcí v C# 7,1.
ms.date: 04/09/2019
ms.openlocfilehash: 5d2d6f51b6422f5b4db5c6bd275b5ffce1f695f8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714582"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="92afa-103">Co je nového v C# 7,1</span><span class="sxs-lookup"><span data-stu-id="92afa-103">What's new in C# 7.1</span></span>

<span data-ttu-id="92afa-104">C#7,1 je první bod verze pro C# jazyk.</span><span class="sxs-lookup"><span data-stu-id="92afa-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="92afa-105">Označuje zvýšené verze tempo pro daný jazyk.</span><span class="sxs-lookup"><span data-stu-id="92afa-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="92afa-106">Nové funkce můžete použít dřív, v ideálním případě, kdy je každá nová funkce připravená.</span><span class="sxs-lookup"><span data-stu-id="92afa-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="92afa-107">C#7,1 přidává schopnost nakonfigurovat kompilátor tak, aby odpovídal zadané verzi jazyka.</span><span class="sxs-lookup"><span data-stu-id="92afa-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="92afa-108">To umožňuje oddělit rozhodnutí o upgradu nástrojů od rozhodnutí upgradovat jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="92afa-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="92afa-109">C#7,1 přidá prvek konfigurace [výběru jazykové verze](../language-reference/configure-language-version.md) , tři nové funkce jazyka a nové chování kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="92afa-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="92afa-110">Nové funkce jazyka v této verzi jsou:</span><span class="sxs-lookup"><span data-stu-id="92afa-110">The new language features in this release are:</span></span>

- [<span data-ttu-id="92afa-111">Metoda `async` `Main`</span><span class="sxs-lookup"><span data-stu-id="92afa-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="92afa-112">Vstupním bodem aplikace může být modifikátor `async`.</span><span class="sxs-lookup"><span data-stu-id="92afa-112">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="92afa-113">`default` literálové výrazy</span><span class="sxs-lookup"><span data-stu-id="92afa-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="92afa-114">Můžete použít výchozí literálové výrazy ve výchozích hodnotových výrazech, pokud cílový typ lze odvodit.</span><span class="sxs-lookup"><span data-stu-id="92afa-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="92afa-115">Odvozené názvy elementů řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="92afa-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="92afa-116">Názvy prvků řazené kolekce členů lze odvodit z inicializace řazené kolekce členů v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="92afa-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
- [<span data-ttu-id="92afa-117">Porovnávání vzorů v parametrech obecného typu</span><span class="sxs-lookup"><span data-stu-id="92afa-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="92afa-118">Můžete použít výrazy porovnávání vzorů u proměnných, jejichž typ je parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="92afa-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="92afa-119">Nakonec má kompilátor dvě možnosti `-refout` a `-refonly`, které řídí [generování sestavení odkazu](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="92afa-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="92afa-120">Chcete-li používat nejnovější funkce v bodu vydání, je nutné [nakonfigurovat verzi jazyka kompilátoru](../language-reference/configure-language-version.md) a vybrat verzi.</span><span class="sxs-lookup"><span data-stu-id="92afa-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="92afa-121">Zbývající část tohoto článku poskytuje přehled jednotlivých funkcí.</span><span class="sxs-lookup"><span data-stu-id="92afa-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="92afa-122">U každé funkce se dozvíte, co je důvod na pozadí.</span><span class="sxs-lookup"><span data-stu-id="92afa-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="92afa-123">Naučíte se syntaxí.</span><span class="sxs-lookup"><span data-stu-id="92afa-123">You'll learn the syntax.</span></span> <span data-ttu-id="92afa-124">Tyto funkce můžete ve svém prostředí prozkoumat pomocí globálního nástroje `dotnet try`:</span><span class="sxs-lookup"><span data-stu-id="92afa-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="92afa-125">Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.</span><span class="sxs-lookup"><span data-stu-id="92afa-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="92afa-126">Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .</span><span class="sxs-lookup"><span data-stu-id="92afa-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="92afa-127">Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *Try-Samples* .</span><span class="sxs-lookup"><span data-stu-id="92afa-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="92afa-128">Spusťte `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="92afa-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="92afa-129">Asynchronní – hlavní</span><span class="sxs-lookup"><span data-stu-id="92afa-129">Async main</span></span>

<span data-ttu-id="92afa-130">*Asynchronní metoda Main* umožňuje použít `await` v metodě `Main`.</span><span class="sxs-lookup"><span data-stu-id="92afa-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="92afa-131">Dříve byste museli psát:</span><span class="sxs-lookup"><span data-stu-id="92afa-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="92afa-132">Nyní můžete napsat:</span><span class="sxs-lookup"><span data-stu-id="92afa-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="92afa-133">Pokud program nevrátí ukončovací kód, můžete deklarovat `Main` metodu, která vrátí <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="92afa-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="92afa-134">Další informace o podrobnostech najdete v tématu [asynchronní Hlavní](../programming-guide/main-and-command-args/index.md) článek v příručce pro programování.</span><span class="sxs-lookup"><span data-stu-id="92afa-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="92afa-135">Výchozí literálové výrazy</span><span class="sxs-lookup"><span data-stu-id="92afa-135">Default literal expressions</span></span>

<span data-ttu-id="92afa-136">Výchozí literálové výrazy představují vylepšení výchozích hodnotových výrazů.</span><span class="sxs-lookup"><span data-stu-id="92afa-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="92afa-137">Tyto výrazy inicializují proměnnou na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="92afa-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="92afa-138">Kam jste předtím napsali:</span><span class="sxs-lookup"><span data-stu-id="92afa-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="92afa-139">Nyní můžete vynechat typ na pravé straně inicializace:</span><span class="sxs-lookup"><span data-stu-id="92afa-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="92afa-140">Další informace naleznete v části [výchozí literály](../language-reference/operators/default.md#default-literal) v článku [výchozí operátor](../language-reference/operators/default.md) .</span><span class="sxs-lookup"><span data-stu-id="92afa-140">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="92afa-141">Odvozené názvy elementů řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="92afa-141">Inferred tuple element names</span></span>

<span data-ttu-id="92afa-142">Tato funkce představuje malé vylepšení funkce řazené kolekce členů představené v C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="92afa-142">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="92afa-143">V mnoha případech, kdy inicializujete řazenou kolekci členů, jsou proměnné používané pro pravou stranu přiřazení stejné jako názvy, které byste chtěli použít pro prvky řazené kolekce členů:</span><span class="sxs-lookup"><span data-stu-id="92afa-143">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="92afa-144">Názvy prvků řazené kolekce členů lze odvodit z proměnných používaných k inicializaci řazené kolekce členů v C# 7,1:</span><span class="sxs-lookup"><span data-stu-id="92afa-144">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="92afa-145">Další informace o této funkci najdete v článku o [řazených kolekcích členů](../tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="92afa-145">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="92afa-146">Porovnávání vzorů v parametrech obecného typu</span><span class="sxs-lookup"><span data-stu-id="92afa-146">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="92afa-147">Počínaje C# 7,1, výraz vzoru pro `is` a vzor typu `switch` může mít typ parametru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="92afa-147">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="92afa-148">To může být nejužitečnější při kontrole typů, které mohou být buď `struct`, nebo `class` typy a chcete se vyhnout zabalení.</span><span class="sxs-lookup"><span data-stu-id="92afa-148">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="92afa-149">Generování referenčního sestavení</span><span class="sxs-lookup"><span data-stu-id="92afa-149">Reference assembly generation</span></span>

<span data-ttu-id="92afa-150">Existují dvě nové možnosti kompilátoru, které generují *pouze referenční sestavení*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) a [-nepoužívejte refout](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="92afa-150">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="92afa-151">Odkazované články vysvětlují tyto možnosti a odkazují na sestavení podrobněji.</span><span class="sxs-lookup"><span data-stu-id="92afa-151">The linked articles explain these options and reference assemblies in more detail.</span></span>
