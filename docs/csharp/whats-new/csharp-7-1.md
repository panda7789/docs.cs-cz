---
title: Co je nového v C# 7.1
description: Přehled nových funkcí v C# 7.1.
ms.date: 08/16/2017
ms.openlocfilehash: 565db102284424f9d8f6fa04ec9c74b52c9da0e6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728651"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="41021-103">Co je nového v C# 7.1</span><span class="sxs-lookup"><span data-stu-id="41021-103">What's new in C# 7.1</span></span>

<span data-ttu-id="41021-104">C# 7.1 je první bod release to jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="41021-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="41021-105">Označuje vyšší verzi cadence pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="41021-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="41021-106">Můžete vytvořit nové funkce dříve, v ideálním případě při každé nové funkce je připraven.</span><span class="sxs-lookup"><span data-stu-id="41021-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="41021-107">C# 7.1 přidá možnost konfigurace kompilátoru tak, aby odpovídaly zadaná verze jazyka.</span><span class="sxs-lookup"><span data-stu-id="41021-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="41021-108">Která umožňuje oddělit rozhodnutí pro upgrade nástroje z rozhodnutí o upgrade jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="41021-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="41021-109">C# 7.1 přidá [výběr verze jazyka](../language-reference/configure-language-version.md) konfigurační prvek, tři nové jazykové funkce a nové chování kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="41021-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="41021-110">Mezi nové jazykové funkce v této verzi jsou:</span><span class="sxs-lookup"><span data-stu-id="41021-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="41021-111">`async` `Main` – Metoda</span><span class="sxs-lookup"><span data-stu-id="41021-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="41021-112">Vstupní bod pro aplikace může mít `async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="41021-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="41021-113">`default` literálové výrazy</span><span class="sxs-lookup"><span data-stu-id="41021-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="41021-114">Výchozí literálu výrazy můžete použít ve výrazech hodnot výchozí při lze odvodit typ cíle.</span><span class="sxs-lookup"><span data-stu-id="41021-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="41021-115">Názvy elementů odvozené řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="41021-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="41021-116">Názvy elementů řazené kolekce členů lze odvodit z inicializace řazené kolekce členů v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="41021-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="41021-117">Nakonec kompilátor má dvě možnosti `/refout` a `/refonly` tuto kontrolu [odkazovat vytváření sestavení](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="41021-117">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="41021-118">Chcete-li použít nejnovější funkce ve verzi bod, je potřeba [konfigurace jazyková verze kompilátoru](../language-reference/configure-language-version.md) a vyberte verzi.</span><span class="sxs-lookup"><span data-stu-id="41021-118">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

## <a name="async-main"></a><span data-ttu-id="41021-119">Asynchronní hlavní</span><span class="sxs-lookup"><span data-stu-id="41021-119">Async main</span></span>

<span data-ttu-id="41021-120">*Asynchronní hlavní* metoda umožňuje používat `await` ve vaší `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="41021-120">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="41021-121">Dříve museli byste zápisu:</span><span class="sxs-lookup"><span data-stu-id="41021-121">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="41021-122">Teď můžete napsat:</span><span class="sxs-lookup"><span data-stu-id="41021-122">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="41021-123">Pokud není váš program vrátí ukončovací kód, můžou deklarovat `Main` metodu, která vrátí <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="41021-123">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="41021-124">Si můžete přečíst více o podrobnostech v [asynchronní hlavní](../programming-guide/main-and-command-args/index.md) tématu v Průvodci programování.</span><span class="sxs-lookup"><span data-stu-id="41021-124">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="41021-125">Výchozí literálu výrazy</span><span class="sxs-lookup"><span data-stu-id="41021-125">Default literal expressions</span></span>

<span data-ttu-id="41021-126">Výchozí literálu výrazy jsou vylepšení výrazy výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="41021-126">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="41021-127">Tyto výrazy inicializovat proměnné na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="41021-127">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="41021-128">Pokud jste dříve by zápisu:</span><span class="sxs-lookup"><span data-stu-id="41021-128">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="41021-129">Nyní můžete vynechat typ na pravé straně inicializace:</span><span class="sxs-lookup"><span data-stu-id="41021-129">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="41021-130">Další informace o toto vylepšení v tématu Průvodce programováním v C# na [výchozí hodnotu výrazy](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="41021-130">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="41021-131">Toto vylepšení také změní některé analýzy pravidel pro [default – klíčové slovo](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="41021-131">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="41021-132">Názvy elementů odvozené řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="41021-132">Inferred tuple element names</span></span>

<span data-ttu-id="41021-133">Tato funkce je malý vylepšení pro funkci řazených kolekcí členů byla zavedená v C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="41021-133">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="41021-134">Kolikrát při inicializaci řazené kolekce členů proměnných, které slouží pro pravé straně přiřazení jsou stejné jako názvy, které chcete pro elementy řazené kolekce členů:</span><span class="sxs-lookup"><span data-stu-id="41021-134">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="41021-135">Názvy elementů řazené kolekce členů lze odvodit z proměnných, které slouží k chybě při inicializaci řazené kolekce členů v C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="41021-135">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="41021-136">Další informace o této funkci v [řazených kolekcí členů](../tuples.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="41021-136">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="41021-137">Vytváření odkaz na sestavení</span><span class="sxs-lookup"><span data-stu-id="41021-137">Reference assembly generation</span></span>

<span data-ttu-id="41021-138">Existují dvě nové možnosti kompilátoru, která generují *pouze odkaz na sestavení*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) a [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="41021-138">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="41021-139">Propojené témata popisují tyto možnosti a odkaz na sestavení podrobněji.</span><span class="sxs-lookup"><span data-stu-id="41021-139">The linked topics explain these options and reference assemblies in more detail.</span></span>
