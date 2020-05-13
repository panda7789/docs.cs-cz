---
title: Pravidla návrhu komponent jazyka F#
description: 'Přečtěte si pokyny pro zápis komponent F #, které jsou určené pro využití jinými volajícími.'
ms.date: 05/14/2018
ms.openlocfilehash: 590bda0660d54ea73c590d31e694f3d499e0fd9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209133"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="37e21-103">Pravidla návrhu komponent jazyka F#</span><span class="sxs-lookup"><span data-stu-id="37e21-103">F# component design guidelines</span></span>

<span data-ttu-id="37e21-104">Tento dokument je sada pokynů pro návrh komponent pro programování v jazyce F # na základě pokynů pro návrh součástí F #, v14, Microsoft Research a verze, která byla původně založena a udržována společností F # Software Foundation.</span><span class="sxs-lookup"><span data-stu-id="37e21-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and a version that was originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="37e21-105">Tento dokument předpokládá, že máte zkušenosti s programováním v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="37e21-106">Mnoho je od komunity F # pro své příspěvky a užitečnou zpětnou vazbu k různým verzím tohoto průvodce.</span><span class="sxs-lookup"><span data-stu-id="37e21-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="37e21-107">Přehled</span><span class="sxs-lookup"><span data-stu-id="37e21-107">Overview</span></span>

<span data-ttu-id="37e21-108">Tento dokument popisuje některé problémy související s návrhem a kódováním komponenty F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="37e21-109">Komponenta může znamenat některý z následujících prvků:</span><span class="sxs-lookup"><span data-stu-id="37e21-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="37e21-110">Vrstva v projektu F #, která obsahuje externí uživatele v rámci daného projektu.</span><span class="sxs-lookup"><span data-stu-id="37e21-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="37e21-111">Knihovna určená pro použití v kódu F # napříč hranicemi sestavení.</span><span class="sxs-lookup"><span data-stu-id="37e21-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="37e21-112">Knihovna určená pro využití jakýmkoli jazykem .NET napříč hranicemi sestavení.</span><span class="sxs-lookup"><span data-stu-id="37e21-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="37e21-113">Knihovna určená k distribuci prostřednictvím úložiště balíčků, například [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="37e21-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="37e21-114">Techniky popsané v tomto článku se řídí [pěti zásadami dobrého kódu F #](index.md#five-principles-of-good-f-code)a využívají jak to vhodné, tak i programování objektů.</span><span class="sxs-lookup"><span data-stu-id="37e21-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="37e21-115">Bez ohledu na metodologii Návrhář komponent a knihoven čelí řadě praktických a prosaicch problémů při pokusu o vytvoření rozhraní API, které je nejsnáze použitelné pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="37e21-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="37e21-116">Conscientious použití pokynů pro [Návrh knihovny .NET](../../standard/design-guidelines/index.md) vám umožní vytvořit konzistentní sadu rozhraní API, která jsou příjemný pro využívání.</span><span class="sxs-lookup"><span data-stu-id="37e21-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="37e21-117">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="37e21-117">General guidelines</span></span>

<span data-ttu-id="37e21-118">Existuje několik univerzálních pokynů, které se vztahují na knihovny F # bez ohledu na zamýšlenou cílovou skupinu pro danou knihovnu.</span><span class="sxs-lookup"><span data-stu-id="37e21-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="37e21-119">Seznamte se s pokyny pro návrh knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="37e21-120">Bez ohledu na druh kódování F #, které provádíte, je důležité mít praktické znalosti s [pokyny pro návrh knihovny .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="37e21-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="37e21-121">Většina ostatních programátorů F # a .NET bude tyto pokyny znát a očekává, že kód .NET bude v souladu s nimi.</span><span class="sxs-lookup"><span data-stu-id="37e21-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="37e21-122">Pokyny k návrhu knihovny .NET poskytují obecné pokyny týkající se pojmenovávání, navrhování tříd a rozhraní, návrh členů (vlastnosti, metody, události atd.) a další informace a jsou užitečné první směrové reference pro celou řadu pokynů k návrhu.</span><span class="sxs-lookup"><span data-stu-id="37e21-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="37e21-123">Přidání dokumentačních komentářů XML do kódu</span><span class="sxs-lookup"><span data-stu-id="37e21-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="37e21-124">Dokumentace XML na veřejných rozhraních API zajišťuje, že uživatelé mohou při použití těchto typů a členů získat skvělé technologie IntelliSense a QuickInfo a povolit vytváření souborů dokumentace pro knihovnu.</span><span class="sxs-lookup"><span data-stu-id="37e21-124">XML documentation on public APIs ensures that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="37e21-125">V [dokumentaci XML](../language-reference/xml-documentation.md) o různých značkách XML, které lze použít pro další značky v komentářích xmldoc.</span><span class="sxs-lookup"><span data-stu-id="37e21-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="37e21-126">Můžete použít buď krátký formát komentáře XML ( `/// comment` ), nebo standardní komentáře XML ( `///<summary>comment</summary>` ).</span><span class="sxs-lookup"><span data-stu-id="37e21-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="37e21-127">Zvažte použití explicitních podpisových souborů (. fsi) pro stabilní rozhraní API knihoven a komponent.</span><span class="sxs-lookup"><span data-stu-id="37e21-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="37e21-128">Použití explicitních signatur souborů v knihovně F # poskytuje stručné shrnutí veřejného rozhraní API, které pomáhá zajistit, že znáte plný veřejný povrch vaší knihovny a poskytuje čisté oddělení mezi veřejnou dokumentací a interními podrobnostmi implementace.</span><span class="sxs-lookup"><span data-stu-id="37e21-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which helps to ensure that you know the full public surface of your library, and provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="37e21-129">Soubory signatury přidávají tření ke změně veřejného rozhraní API tím, že vyžadují změny provedené v souborech implementace i signatury.</span><span class="sxs-lookup"><span data-stu-id="37e21-129">Signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="37e21-130">V důsledku toho by se soubory signatury měly obvykle zavádět jenom v případě, že se rozhraní API stane solidified a už se neočekává, že se významně změní.</span><span class="sxs-lookup"><span data-stu-id="37e21-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="37e21-131">Vždy dodržujte osvědčené postupy pro používání řetězců v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="37e21-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="37e21-132">Dodržujte [osvědčené postupy pro používání řetězců v](../../standard/base-types/best-practices-strings.md) doprovodnéch materiálech k rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="37e21-133">Konkrétně vždy explicitně uveďte *kulturní záměr* v převodu a porovnávání řetězců (kde je to možné).</span><span class="sxs-lookup"><span data-stu-id="37e21-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="37e21-134">Pokyny pro knihovny orientované na F #</span><span class="sxs-lookup"><span data-stu-id="37e21-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="37e21-135">Tato část obsahuje doporučení pro vývoj veřejných knihoven založených na jazyce F #. To znamená, že knihovny zveřejňují veřejná rozhraní API, které mají být spotřebovány vývojáři jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="37e21-136">Existuje celá řada doporučení pro návrh knihoven, která se týkají konkrétně F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="37e21-137">Pokud nejsou k dispozici konkrétní doporučení, jsou pokyny pro návrh knihovny .NET základní doprovodné materiály.</span><span class="sxs-lookup"><span data-stu-id="37e21-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="37e21-138">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="37e21-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="37e21-139">Používání konvencí pojmenování a psaní velkých písmen v .NET</span><span class="sxs-lookup"><span data-stu-id="37e21-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="37e21-140">Následující tabulka sleduje konvence pojmenování a psaní velkých písmen v .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="37e21-141">K dispozici jsou malé dodatky, které obsahují také konstrukce F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="37e21-142">Konstrukce</span><span class="sxs-lookup"><span data-stu-id="37e21-142">Construct</span></span> | <span data-ttu-id="37e21-143">Obchodní případ</span><span class="sxs-lookup"><span data-stu-id="37e21-143">Case</span></span> | <span data-ttu-id="37e21-144">Část</span><span class="sxs-lookup"><span data-stu-id="37e21-144">Part</span></span> | <span data-ttu-id="37e21-145">Příklady</span><span class="sxs-lookup"><span data-stu-id="37e21-145">Examples</span></span> | <span data-ttu-id="37e21-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37e21-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="37e21-147">Konkrétní typy</span><span class="sxs-lookup"><span data-stu-id="37e21-147">Concrete types</span></span> | <span data-ttu-id="37e21-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-148">PascalCase</span></span> | <span data-ttu-id="37e21-149">Podstatné jméno/přídavné jméno</span><span class="sxs-lookup"><span data-stu-id="37e21-149">Noun/ adjective</span></span> | <span data-ttu-id="37e21-150">List, Double, Complex</span><span class="sxs-lookup"><span data-stu-id="37e21-150">List, Double, Complex</span></span> | <span data-ttu-id="37e21-151">Konkrétní typy jsou struktury, třídy, výčty, delegáti, záznamy a sjednocení.</span><span class="sxs-lookup"><span data-stu-id="37e21-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="37e21-152">I když názvy typů jsou tradičně malé písmeno v OCaml, F # přijalo schéma pojmenování .NET pro typy.</span><span class="sxs-lookup"><span data-stu-id="37e21-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="37e21-153">knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="37e21-153">DLLs</span></span>           | <span data-ttu-id="37e21-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-154">PascalCase</span></span> |                 | <span data-ttu-id="37e21-155">Fabrikam. Core. dll</span><span class="sxs-lookup"><span data-stu-id="37e21-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="37e21-156">Sjednocení značek</span><span class="sxs-lookup"><span data-stu-id="37e21-156">Union tags</span></span>     | <span data-ttu-id="37e21-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-157">PascalCase</span></span> | <span data-ttu-id="37e21-158">Podstatné jméno</span><span class="sxs-lookup"><span data-stu-id="37e21-158">Noun</span></span> | <span data-ttu-id="37e21-159">Nějaké, přidání, úspěch</span><span class="sxs-lookup"><span data-stu-id="37e21-159">Some, Add, Success</span></span> | <span data-ttu-id="37e21-160">Ve veřejných rozhraních API nepoužívejte předponu.</span><span class="sxs-lookup"><span data-stu-id="37e21-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="37e21-161">Volitelně můžete použít předponu, pokud interní, například`type Teams = TAlpha | TBeta | TDelta.`</span><span class="sxs-lookup"><span data-stu-id="37e21-161">Optionally use a prefix when internal, such as `type Teams = TAlpha | TBeta | TDelta.`</span></span> |
| <span data-ttu-id="37e21-162">Událost</span><span class="sxs-lookup"><span data-stu-id="37e21-162">Event</span></span>          | <span data-ttu-id="37e21-163">PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-163">PascalCase</span></span> | <span data-ttu-id="37e21-164">Příkaz</span><span class="sxs-lookup"><span data-stu-id="37e21-164">Verb</span></span> | <span data-ttu-id="37e21-165">ValueChanged / ValueChanging</span><span class="sxs-lookup"><span data-stu-id="37e21-165">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="37e21-166">Výjimky</span><span class="sxs-lookup"><span data-stu-id="37e21-166">Exceptions</span></span>     | <span data-ttu-id="37e21-167">PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-167">PascalCase</span></span> |      | <span data-ttu-id="37e21-168">WebException</span><span class="sxs-lookup"><span data-stu-id="37e21-168">WebException</span></span> | <span data-ttu-id="37e21-169">Název by měl končit "výjimkou".</span><span class="sxs-lookup"><span data-stu-id="37e21-169">Name should end with "Exception".</span></span> |
| <span data-ttu-id="37e21-170">Pole</span><span class="sxs-lookup"><span data-stu-id="37e21-170">Field</span></span>          | <span data-ttu-id="37e21-171">PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-171">PascalCase</span></span> | <span data-ttu-id="37e21-172">Podstatné jméno</span><span class="sxs-lookup"><span data-stu-id="37e21-172">Noun</span></span> | <span data-ttu-id="37e21-173">Current</span><span class="sxs-lookup"><span data-stu-id="37e21-173">CurrentName</span></span>  | |
| <span data-ttu-id="37e21-174">Typy rozhraní</span><span class="sxs-lookup"><span data-stu-id="37e21-174">Interface types</span></span> |  <span data-ttu-id="37e21-175">PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-175">PascalCase</span></span> | <span data-ttu-id="37e21-176">Podstatné jméno/přídavné jméno</span><span class="sxs-lookup"><span data-stu-id="37e21-176">Noun/ adjective</span></span> | <span data-ttu-id="37e21-177">IDisposable</span><span class="sxs-lookup"><span data-stu-id="37e21-177">IDisposable</span></span> | <span data-ttu-id="37e21-178">Název by měl začínat na "I".</span><span class="sxs-lookup"><span data-stu-id="37e21-178">Name should start with "I".</span></span> |
| <span data-ttu-id="37e21-179">Metoda</span><span class="sxs-lookup"><span data-stu-id="37e21-179">Method</span></span> |  <span data-ttu-id="37e21-180">PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-180">PascalCase</span></span> |  <span data-ttu-id="37e21-181">Příkaz</span><span class="sxs-lookup"><span data-stu-id="37e21-181">Verb</span></span> | <span data-ttu-id="37e21-182">ToString</span><span class="sxs-lookup"><span data-stu-id="37e21-182">ToString</span></span> | |
| <span data-ttu-id="37e21-183">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="37e21-183">Namespace</span></span> | <span data-ttu-id="37e21-184">PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-184">PascalCase</span></span> | | <span data-ttu-id="37e21-185">Microsoft. FSharp. Core</span><span class="sxs-lookup"><span data-stu-id="37e21-185">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="37e21-186">Obecně používejte `<Organization>.<Technology>[.<Subnamespace>]` , ale odřaďte organizaci, pokud je technologie nezávislá na organizaci.</span><span class="sxs-lookup"><span data-stu-id="37e21-186">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="37e21-187">Parametry</span><span class="sxs-lookup"><span data-stu-id="37e21-187">Parameters</span></span> | <span data-ttu-id="37e21-188">camelCase</span><span class="sxs-lookup"><span data-stu-id="37e21-188">camelCase</span></span> | <span data-ttu-id="37e21-189">Podstatné jméno</span><span class="sxs-lookup"><span data-stu-id="37e21-189">Noun</span></span> |  <span data-ttu-id="37e21-190">typeName, Transform, rozsah</span><span class="sxs-lookup"><span data-stu-id="37e21-190">typeName, transform, range</span></span> | |
| <span data-ttu-id="37e21-191">Povolit hodnoty (interní)</span><span class="sxs-lookup"><span data-stu-id="37e21-191">let values (internal)</span></span> | <span data-ttu-id="37e21-192">camelCase nebo PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-192">camelCase or PascalCase</span></span> | <span data-ttu-id="37e21-193">Podstatné jméno/příkaz</span><span class="sxs-lookup"><span data-stu-id="37e21-193">Noun/ verb</span></span> |  <span data-ttu-id="37e21-194">GetValue, myTable</span><span class="sxs-lookup"><span data-stu-id="37e21-194">getValue, myTable</span></span> |
| <span data-ttu-id="37e21-195">Povolit hodnoty (externí)</span><span class="sxs-lookup"><span data-stu-id="37e21-195">let values (external)</span></span> | <span data-ttu-id="37e21-196">camelCase nebo PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-196">camelCase or PascalCase</span></span> | <span data-ttu-id="37e21-197">Podstatné jméno/příkaz</span><span class="sxs-lookup"><span data-stu-id="37e21-197">Noun/verb</span></span>  | <span data-ttu-id="37e21-198">List. map, dates. Today</span><span class="sxs-lookup"><span data-stu-id="37e21-198">List.map, Dates.Today</span></span> | <span data-ttu-id="37e21-199">hodnoty manuálních vazeb jsou často veřejné, pokud následují tradiční vzory návrhu funkcí.</span><span class="sxs-lookup"><span data-stu-id="37e21-199">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="37e21-200">Nicméně obecně používejte PascalCase, pokud je možné identifikátor použít z jiných jazyků .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-200">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="37e21-201">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="37e21-201">Property</span></span>  | <span data-ttu-id="37e21-202">PascalCase</span><span class="sxs-lookup"><span data-stu-id="37e21-202">PascalCase</span></span>  | <span data-ttu-id="37e21-203">Podstatné jméno/přídavné jméno</span><span class="sxs-lookup"><span data-stu-id="37e21-203">Noun/ adjective</span></span>  | <span data-ttu-id="37e21-204">IsEndOfFile, BackColor</span><span class="sxs-lookup"><span data-stu-id="37e21-204">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="37e21-205">Logické vlastnosti obecně používají hodnotu a můžou být kladné, jako v IsEndOfFile, ne IsNotEndOfFile.</span><span class="sxs-lookup"><span data-stu-id="37e21-205">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="37e21-206">Vyhnout se zkratkám</span><span class="sxs-lookup"><span data-stu-id="37e21-206">Avoid abbreviations</span></span>

<span data-ttu-id="37e21-207">Pokyny rozhraní .NET nebrání použití zkratek (například "použít `OnButtonClick` místo `OnBtnClick` ").</span><span class="sxs-lookup"><span data-stu-id="37e21-207">The .NET guidelines discourage the use of abbreviations (for example, "use `OnButtonClick` rather than `OnBtnClick`").</span></span> <span data-ttu-id="37e21-208">Společné zkratky, například `Async` pro "asynchronní", jsou tolerovány.</span><span class="sxs-lookup"><span data-stu-id="37e21-208">Common abbreviations, such as `Async` for "Asynchronous", are tolerated.</span></span> <span data-ttu-id="37e21-209">Tento návod se někdy ignoruje pro funkční programování; například `List.iter` používá zkratku pro "ITER".</span><span class="sxs-lookup"><span data-stu-id="37e21-209">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for "iterate".</span></span> <span data-ttu-id="37e21-210">Z tohoto důvodu je použití zkratek v programovacím jazyce F # do-F # tolerováno, ale při návrhu veřejné součásti by se však mělo obecně vyhnout.</span><span class="sxs-lookup"><span data-stu-id="37e21-210">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="37e21-211">Vyhnout se kolizí názvů malých a velkých písmen</span><span class="sxs-lookup"><span data-stu-id="37e21-211">Avoid casing name collisions</span></span>

<span data-ttu-id="37e21-212">Pokyny pro rozhraní .NET říkají, že samotný velká a malá písmena nelze použít k rozlišení kolizí názvů, protože některé jazyky klienta (například Visual Basic) rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="37e21-212">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="37e21-213">Použijte akronymy tam, kde je to vhodné</span><span class="sxs-lookup"><span data-stu-id="37e21-213">Use acronyms where appropriate</span></span>

<span data-ttu-id="37e21-214">Akronymy jako XML nejsou zkratky a jsou široce používány v knihovnách .NET v netučném formátu (XML).</span><span class="sxs-lookup"><span data-stu-id="37e21-214">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="37e21-215">Měly by se používat jenom známé, široce rozpoznané zkratky.</span><span class="sxs-lookup"><span data-stu-id="37e21-215">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="37e21-216">Použití PascalCase pro názvy obecných parametrů</span><span class="sxs-lookup"><span data-stu-id="37e21-216">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="37e21-217">Použijte PascalCase pro názvy obecných parametrů ve veřejných rozhraních API, včetně pro knihovny založené na F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-217">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="37e21-218">Konkrétně použijte názvy jako,, `T` `U` `T1` , `T2` pro libovolný obecný parametr a, pokud jsou specifické názvy, potom pro knihovny pro jazyk F # použijte názvy, například, `Key` , (nikoli například `Value` `Arg` `TKey` ).</span><span class="sxs-lookup"><span data-stu-id="37e21-218">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="37e21-219">Pro veřejné funkce a hodnoty v modulech F # použijte buď PascalCase, nebo camelCase.</span><span class="sxs-lookup"><span data-stu-id="37e21-219">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="37e21-220">camelCase se používá pro veřejné funkce, které jsou navržené tak, aby se používaly jako nekvalifikované (například `invalidArg` ), a pro "standardní funkce shromažďování" (například list. map).</span><span class="sxs-lookup"><span data-stu-id="37e21-220">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the "standard collection functions" (for example, List.map).</span></span> <span data-ttu-id="37e21-221">V obou těchto případech se názvy funkcí chovají podobně jako klíčová slova v jazyce.</span><span class="sxs-lookup"><span data-stu-id="37e21-221">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="37e21-222">Návrh objektu, typu a modulu</span><span class="sxs-lookup"><span data-stu-id="37e21-222">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="37e21-223">Použijte obory názvů nebo moduly, které obsahují vaše typy a moduly.</span><span class="sxs-lookup"><span data-stu-id="37e21-223">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="37e21-224">Každý soubor F # v komponentě by měl začínat buď deklarací oboru názvů, nebo deklarací modulu.</span><span class="sxs-lookup"><span data-stu-id="37e21-224">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="37e21-225">or</span><span class="sxs-lookup"><span data-stu-id="37e21-225">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="37e21-226">Rozdíly mezi použitím modulů a oborů názvů k uspořádání kódu na nejvyšší úrovni jsou následující:</span><span class="sxs-lookup"><span data-stu-id="37e21-226">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="37e21-227">Obory názvů můžou zahrnovat víc souborů.</span><span class="sxs-lookup"><span data-stu-id="37e21-227">Namespaces can span multiple files</span></span>
* <span data-ttu-id="37e21-228">Obory názvů nemůžou obsahovat funkce F #, pokud nejsou v rámci vnitřního modulu.</span><span class="sxs-lookup"><span data-stu-id="37e21-228">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="37e21-229">Kód pro daný modul musí být obsažen v rámci jednoho souboru.</span><span class="sxs-lookup"><span data-stu-id="37e21-229">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="37e21-230">Moduly nejvyšší úrovně můžou obsahovat funkce jazyka F # bez nutnosti interního modulu.</span><span class="sxs-lookup"><span data-stu-id="37e21-230">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="37e21-231">Volba mezi oborem názvů nebo modulem na nejvyšší úrovni má vliv na zkompilované formy kódu, a proto ovlivní zobrazení z jiných jazyků .NET by mělo být vaše rozhraní API nakonec spotřebováno mimo kód F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-231">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="37e21-232">Použití metod a vlastností pro vnitřní operace s typy objektů</span><span class="sxs-lookup"><span data-stu-id="37e21-232">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="37e21-233">Při práci s objekty je vhodné zajistit, aby se funkce spotřebních funkcí implementovaly jako metody a vlastnosti tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="37e21-233">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="37e21-234">Hromadná funkčnost daného člena nemusí být nutně implementovaná v tomto členu, ale spotřební část této funkce by měla být.</span><span class="sxs-lookup"><span data-stu-id="37e21-234">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="37e21-235">Použití tříd k zapouzdření proměnlivého stavu</span><span class="sxs-lookup"><span data-stu-id="37e21-235">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="37e21-236">V F # stačí, když tento stav není zapouzdřený jinou jazykovou konstrukcí, jako je například uzavření, výraz sekvence nebo asynchronní výpočty.</span><span class="sxs-lookup"><span data-stu-id="37e21-236">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="37e21-237">Seskupení souvisejících operací pomocí rozhraní</span><span class="sxs-lookup"><span data-stu-id="37e21-237">Use interfaces to group related operations</span></span>

<span data-ttu-id="37e21-238">Použijte typy rozhraní, které reprezentují sadu operací.</span><span class="sxs-lookup"><span data-stu-id="37e21-238">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="37e21-239">Jedná se o preferované možnosti, jako jsou například řazené kolekce členů funkcí nebo záznamů funkcí.</span><span class="sxs-lookup"><span data-stu-id="37e21-239">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="37e21-240">V upřednostňovaném pořadí:</span><span class="sxs-lookup"><span data-stu-id="37e21-240">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="37e21-241">Rozhraní jsou koncepty první třídy v rozhraní .NET, které můžete použít k dosažení, k čemu by vám funktory normálně dodávat.</span><span class="sxs-lookup"><span data-stu-id="37e21-241">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="37e21-242">Kromě toho mohou být použity ke kódování existenční typů do programu, které záznamy funkcí nemůžou.</span><span class="sxs-lookup"><span data-stu-id="37e21-242">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a><span data-ttu-id="37e21-243">Použití modulu k seskupení funkcí, které fungují na kolekcích</span><span class="sxs-lookup"><span data-stu-id="37e21-243">Use a module to group functions that act on collections</span></span>

<span data-ttu-id="37e21-244">Při definování typu kolekce zvažte poskytnutí standardní sady operací jako `CollectionType.map` a `CollectionType.iter` ) pro nové typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="37e21-244">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="37e21-245">Pokud tento modul zahrnete, použijte standardní zásady vytváření názvů pro funkce, které najdete v FSharp. Core.</span><span class="sxs-lookup"><span data-stu-id="37e21-245">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="37e21-246">Použití modulu k seskupení funkcí pro běžné a kanonické funkce, zejména v případě matematických a DSL knihoven</span><span class="sxs-lookup"><span data-stu-id="37e21-246">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="37e21-247">Například `Microsoft.FSharp.Core.Operators` je automaticky otevřená kolekce funkcí na nejvyšší úrovni (například `abs` a `sin` ) poskytovaná FSharp. Core. dll.</span><span class="sxs-lookup"><span data-stu-id="37e21-247">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="37e21-248">Knihovna statistik může také obsahovat modul s funkcemi `erf` a `erfc` , kde je tento modul navržený tak, aby byl explicitně nebo automaticky otevřen.</span><span class="sxs-lookup"><span data-stu-id="37e21-248">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="37e21-249">Zvažte použití RequireQualifiedAccess a pečlivé použití atributů AutoOpen.</span><span class="sxs-lookup"><span data-stu-id="37e21-249">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="37e21-250">Přidání `[<RequireQualifiedAccess>]` atributu do modulu znamená, že modul nemůže být otevřen a že odkazy na prvky modulu vyžadují explicitní kvalifikovaný přístup.</span><span class="sxs-lookup"><span data-stu-id="37e21-250">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="37e21-251">`Microsoft.FSharp.Collections.List`Modul má například tento atribut.</span><span class="sxs-lookup"><span data-stu-id="37e21-251">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="37e21-252">To je užitečné v případě, že funkce a hodnoty v modulu mají názvy, které jsou pravděpodobně v konfliktu s názvy v jiných modulech.</span><span class="sxs-lookup"><span data-stu-id="37e21-252">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="37e21-253">Vyžadování kvalifikovaného přístupu může značně prodloužit dlouhodobou udržovatelnost a možnost využití knihovny.</span><span class="sxs-lookup"><span data-stu-id="37e21-253">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="37e21-254">Přidání `[<AutoOpen>]` atributu do modulu znamená, že se modul otevře při otevření nadřazeného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="37e21-254">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="37e21-255">`[<AutoOpen>]`Atribut může být použit také na sestavení, aby označoval modul, který je automaticky otevřen při odkazování na sestavení.</span><span class="sxs-lookup"><span data-stu-id="37e21-255">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="37e21-256">Například statistická knihovna **MathsHeaven. Statistics** může obsahovat `module MathsHeaven.Statistics.Operators` obsahující funkce `erf` a `erfc` .</span><span class="sxs-lookup"><span data-stu-id="37e21-256">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="37e21-257">Je vhodné označit tento modul jako `[<AutoOpen>]` .</span><span class="sxs-lookup"><span data-stu-id="37e21-257">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="37e21-258">To znamená, `open MathsHeaven.Statistics` že tento modul také otevřete a přenesete názvy `erf` a `erfc` do rozsahu.</span><span class="sxs-lookup"><span data-stu-id="37e21-258">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="37e21-259">Jiné vhodné použití `[<AutoOpen>]` je pro moduly obsahující rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="37e21-259">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="37e21-260">Nadměrné `[<AutoOpen>]` využití potenciálních zákazníků pro zneužitelné obory názvů a atribut by měl být použit s péčí.</span><span class="sxs-lookup"><span data-stu-id="37e21-260">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="37e21-261">Pro konkrétní knihovny v konkrétních doménách může rozumné využití `[<AutoOpen>]` vést k lepší použitelnosti.</span><span class="sxs-lookup"><span data-stu-id="37e21-261">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="37e21-262">Zvažte možnost definovat členy operátoru pro třídy, kde je vhodné použít dobře známé operátory</span><span class="sxs-lookup"><span data-stu-id="37e21-262">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="37e21-263">Někdy se třídy používají k modelování matematických konstrukcí, jako jsou vektory.</span><span class="sxs-lookup"><span data-stu-id="37e21-263">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="37e21-264">V případě, že doménová model obsahuje známé operátory, je třeba je definovat jako členy, kteří jsou pro tuto třídu vnitřní.</span><span class="sxs-lookup"><span data-stu-id="37e21-264">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="37e21-265">Tyto pokyny odpovídají obecným pokynům rozhraní .NET pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="37e21-265">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="37e21-266">V kódování F # ale může být také důležité, protože tyto typy je možné používat ve spojení s funkcemi F # a s omezeními členů, jako je list. sumBy –.</span><span class="sxs-lookup"><span data-stu-id="37e21-266">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="37e21-267">Zvažte použití zkompilovaného typu k poskytnutí. Popisný název pro ostatní uživatele jazyka .NET</span><span class="sxs-lookup"><span data-stu-id="37e21-267">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="37e21-268">Někdy můžete chtít pojmenovat něco v jednom stylu pro příjemce F # (například statického člena v malých písmenech, aby se zobrazilo, jako by šlo o funkci vázanou na modul), ale měl jiný styl pro název při kompilaci do sestavení.</span><span class="sxs-lookup"><span data-stu-id="37e21-268">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="37e21-269">Atribut můžete použít `[<CompiledName>]` k poskytnutí jiného stylu pro kód, který nespotřebovává kód jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-269">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="37e21-270">Pomocí `[<CompiledName>]` můžete použít konvence vytváření názvů .NET pro uživatele, kteří nejsou v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-270">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="37e21-271">Použití přetížení metody pro členské funkce, pokud to uděláte, poskytuje jednodušší rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="37e21-271">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="37e21-272">Přetížení metody je výkonný nástroj pro zjednodušení rozhraní API, které může potřebovat provést podobné funkce, ale s různými možnostmi nebo argumenty.</span><span class="sxs-lookup"><span data-stu-id="37e21-272">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="37e21-273">V F # je častější přetížení na základě počtu argumentů, nikoli typů argumentů.</span><span class="sxs-lookup"><span data-stu-id="37e21-273">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="37e21-274">Skryje reprezentace typů záznamů a sjednocení, pokud je návrh těchto typů nejspíš vyvíjejí.</span><span class="sxs-lookup"><span data-stu-id="37e21-274">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="37e21-275">Vyhněte se odhalení konkrétních reprezentace objektů.</span><span class="sxs-lookup"><span data-stu-id="37e21-275">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="37e21-276">Například konkrétní reprezentace hodnot není zjištěna <xref:System.DateTime> externím a veřejným rozhraním API návrhu knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-276">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="37e21-277">V době běhu zná modul CLR (Common Language Runtime) potvrzenou implementaci, která bude použita v celém spuštění.</span><span class="sxs-lookup"><span data-stu-id="37e21-277">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="37e21-278">Zkompilovaný kód však sám nevyužívá závislosti na konkrétní reprezentace.</span><span class="sxs-lookup"><span data-stu-id="37e21-278">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="37e21-279">Nepoužívejte dědičnost implementace pro rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="37e21-279">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="37e21-280">V F # se dědičnost implementace používá zřídka.</span><span class="sxs-lookup"><span data-stu-id="37e21-280">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="37e21-281">Kromě toho jsou Hierarchie dědičnosti často složité a obtížně se mění, když dorazíte na nové požadavky.</span><span class="sxs-lookup"><span data-stu-id="37e21-281">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="37e21-282">Implementace dědičnosti v F # stále existuje kvůli kompatibilitě a vzácným případům, kde se jedná o nejlepší řešení problému, ale při navrhování polymorfismu, jako je například implementace rozhraní, byste měli v programech F # vyzkoušet alternativní techniky.</span><span class="sxs-lookup"><span data-stu-id="37e21-282">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="37e21-283">Signatury funkcí a členů</span><span class="sxs-lookup"><span data-stu-id="37e21-283">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="37e21-284">Použít řazené kolekce členů pro návratové hodnoty při vrácení malého počtu více nesouvisejících hodnot</span><span class="sxs-lookup"><span data-stu-id="37e21-284">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="37e21-285">Tady je dobrý příklad použití řazené kolekce členů v návratovém typu:</span><span class="sxs-lookup"><span data-stu-id="37e21-285">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="37e21-286">U návratových typů obsahujících mnoho komponent nebo v případě, že komponenty souvisejí s jedinou identifikovatelnou entitou, zvažte použití pojmenovaného typu namísto řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="37e21-286">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="37e21-287">Použití `Async<T>` pro asynchronní programování na hranicích rozhraní API F #</span><span class="sxs-lookup"><span data-stu-id="37e21-287">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="37e21-288">Pokud je k dispozici odpovídající synchronní operace s názvem, `Operation` která vrací `T` , pak by měla být asynchronní operace pojmenována, pokud se vrátí `AsyncOperation` `Async<T>` nebo `OperationAsync` vrátí `Task<T>` .</span><span class="sxs-lookup"><span data-stu-id="37e21-288">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="37e21-289">Pro běžně používané typy .NET, které zpřístupňují Begin/End metody, zvažte použití `Async.FromBeginEnd` metody pro zápis rozšiřujících metod jako fasádu a poskytnutí asynchronního programovacího modelu F # těmto rozhraním API .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-289">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="37e21-290">Výjimky</span><span class="sxs-lookup"><span data-stu-id="37e21-290">Exceptions</span></span>

<span data-ttu-id="37e21-291">Informace o vhodném použití výjimek, výsledků a možností najdete v tématu [Správa chyb](conventions.md#error-management) .</span><span class="sxs-lookup"><span data-stu-id="37e21-291">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="37e21-292">Členové rozšíření</span><span class="sxs-lookup"><span data-stu-id="37e21-292">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="37e21-293">Pečlivě použít členy rozšíření F # v komponentách F # až-F #</span><span class="sxs-lookup"><span data-stu-id="37e21-293">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="37e21-294">Členy rozšíření F # by obecně měly být použity pouze pro operace, které jsou v uzávěru vnitřních operací přidružených k typu ve většině jeho režimů použití.</span><span class="sxs-lookup"><span data-stu-id="37e21-294">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="37e21-295">Jedním z běžných použití je poskytnout rozhraní API, která jsou idiomatickou na F # pro různé typy rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="37e21-295">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="37e21-296">Typy sjednocení</span><span class="sxs-lookup"><span data-stu-id="37e21-296">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="37e21-297">Použití rozlišených sjednocení namísto hierarchií tříd pro data strukturovaná v stromové struktuře</span><span class="sxs-lookup"><span data-stu-id="37e21-297">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="37e21-298">Struktury podobné stromu jsou rekurzivně definovány.</span><span class="sxs-lookup"><span data-stu-id="37e21-298">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="37e21-299">To je nevhodné při dědění, ale elegantní s rozlišenými Sjednoceními.</span><span class="sxs-lookup"><span data-stu-id="37e21-299">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="37e21-300">Představují-li data ve stromové struktuře s rozlišenými Sjednoceními, také vám umožní těžit z úplnosti v porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="37e21-300">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="37e21-301">Použití `[<RequireQualifiedAccess>]` na typech sjednocení, jejichž názvy případů nejsou dostatečně jedinečné</span><span class="sxs-lookup"><span data-stu-id="37e21-301">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="37e21-302">Můžete se setkat s doménou, ve které je stejný název nejlepším názvem pro různé věci, jako jsou například rozlišené případy sjednocení.</span><span class="sxs-lookup"><span data-stu-id="37e21-302">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="37e21-303">Můžete použít k jednoznačnému rozlišení `[<RequireQualifiedAccess>]` názvů případů, aby nedocházelo k matoucím chybám kvůli stínům, které jsou závislé na řazení `open` příkazů.</span><span class="sxs-lookup"><span data-stu-id="37e21-303">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="37e21-304">Skryje reprezentace rozlišených sjednocení pro binární kompatibilní rozhraní API, pokud je návrh těchto typů nejspíš vyvíjejí.</span><span class="sxs-lookup"><span data-stu-id="37e21-304">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="37e21-305">Typy sjednocení spoléhají na formuláře porovnávání vzorů F # pro stručný programovací model.</span><span class="sxs-lookup"><span data-stu-id="37e21-305">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="37e21-306">Jak už bylo uvedeno dříve, měli byste se vyhnout odhalení konkrétních reprezentace dat, pokud je návrh těchto typů pravděpodobně vyvíjejí.</span><span class="sxs-lookup"><span data-stu-id="37e21-306">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="37e21-307">Například reprezentace rozlišeného sjednocení může být skrytá pomocí soukromé nebo interní deklarace nebo pomocí souboru signatury.</span><span class="sxs-lookup"><span data-stu-id="37e21-307">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="37e21-308">Pokud nerozlišujete rozlišené sjednocení, může se stát, že budete mít zavedenou verzi vaší knihovny bez přerušení uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="37e21-308">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="37e21-309">Místo toho zvažte odhalení jednoho nebo více aktivních vzorů, které umožní porovnávání vzorů přes hodnoty vašeho typu.</span><span class="sxs-lookup"><span data-stu-id="37e21-309">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="37e21-310">Aktivní vzory poskytují alternativní způsob, jak poskytnout spotřebitelům F # s porovnáváním vzorů, přičemž se vyhnete vystavování typů sjednocení F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-310">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="37e21-311">Vložené funkce a omezení členů</span><span class="sxs-lookup"><span data-stu-id="37e21-311">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="37e21-312">Definování obecných číselných algoritmů pomocí vložených funkcí s implicitními omezeními členů a staticky vyřešenými obecnými typy</span><span class="sxs-lookup"><span data-stu-id="37e21-312">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="37e21-313">Omezení aritmetických členů a porovnání F # jsou standardem pro programování v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-313">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="37e21-314">Zvažte například následující kód:</span><span class="sxs-lookup"><span data-stu-id="37e21-314">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="37e21-315">Typ této funkce je následující:</span><span class="sxs-lookup"><span data-stu-id="37e21-315">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="37e21-316">Toto je vhodná funkce pro veřejné rozhraní API v matematické knihovně.</span><span class="sxs-lookup"><span data-stu-id="37e21-316">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="37e21-317">Nepoužívejte omezení členů pro simulaci tříd typů a ztraceného psaní</span><span class="sxs-lookup"><span data-stu-id="37e21-317">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="37e21-318">Je možné simulovat "ztracené psaní" pomocí omezení členů F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-318">It is possible to simulate "duck typing" using F# member constraints.</span></span> <span data-ttu-id="37e21-319">Nicméně členové, kteří používají toto by, by neměly být obecně použity v návrzích knihovny F # do-F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-319">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="37e21-320">Důvodem je to, že návrhy knihovny založené na neznámých nebo nestandardních implicitních omezeních mají za následek neflexibilní a vázané na jeden konkrétní model rozhraní.</span><span class="sxs-lookup"><span data-stu-id="37e21-320">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="37e21-321">Kromě toho existuje dobrý šanci, že těžké použití omezení členů tímto způsobem může vést k velmi dlouhé době kompilace.</span><span class="sxs-lookup"><span data-stu-id="37e21-321">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="37e21-322">Definice operátorů</span><span class="sxs-lookup"><span data-stu-id="37e21-322">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="37e21-323">Vyhněte se definování vlastních symbolických operátorů</span><span class="sxs-lookup"><span data-stu-id="37e21-323">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="37e21-324">Vlastní operátory jsou v některých situacích nezbytné a jsou vysoce užitečná pro Zápisová zařízení v rámci velkého těla implementačního kódu.</span><span class="sxs-lookup"><span data-stu-id="37e21-324">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="37e21-325">Pro nové uživatele knihovny jsou pojmenované funkce často snáze používány.</span><span class="sxs-lookup"><span data-stu-id="37e21-325">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="37e21-326">Kromě toho mohou být vlastní symbolické operátory obtížné dokumentovat a uživatelé naleznou snadnější vyhledávání v nápovědě k operátorům z důvodu stávajících omezení v prostředí IDE a vyhledávacích strojích.</span><span class="sxs-lookup"><span data-stu-id="37e21-326">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="37e21-327">V důsledku toho je nejlepší publikovat vaše funkce jako pojmenované funkce a členy a dále vystavit operátory pro tuto funkci pouze v případě, že tyto výhody převáží dokumentaci a náklady na vnímání.</span><span class="sxs-lookup"><span data-stu-id="37e21-327">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="37e21-328">Měrné jednotky</span><span class="sxs-lookup"><span data-stu-id="37e21-328">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="37e21-329">Pečlivě používejte měrné jednotky pro přidání bezpečnosti typů v kódu F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-329">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="37e21-330">Další informace o zadávání pro měrné jednotky se vymažou při prohlížení jinými jazyky .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-330">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="37e21-331">Mějte na paměti, že komponenty, nástroje a reflexe rozhraní .NET uvidí typy – jednotky sítě SAN.</span><span class="sxs-lookup"><span data-stu-id="37e21-331">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="37e21-332">Například příjemci C# uvidí `float` místo `float<kg>` .</span><span class="sxs-lookup"><span data-stu-id="37e21-332">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="37e21-333">Zkratky typů</span><span class="sxs-lookup"><span data-stu-id="37e21-333">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="37e21-334">Používejte pečlivě zkratky typů pro zjednodušení kódu F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-334">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="37e21-335">Komponenty, nástroje a reflexe rozhraní .NET nebudou pro typy zobrazovat zkrácené názvy.</span><span class="sxs-lookup"><span data-stu-id="37e21-335">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="37e21-336">Významným využitím zkratek typu může být taky, že doména vypadá složitější než ve skutečnosti, což by mohlo Zaměňujte uživatele.</span><span class="sxs-lookup"><span data-stu-id="37e21-336">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="37e21-337">Vyhněte se zkratkám typu pro veřejné typy, jejichž členy a vlastnosti by měly být vnitřně odlišné od těch, které jsou k dispozici pro zkrácený typ.</span><span class="sxs-lookup"><span data-stu-id="37e21-337">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="37e21-338">V tomto případě typ, který se zkracuje, je příliš velký o reprezentace vlastního typu, který je definován.</span><span class="sxs-lookup"><span data-stu-id="37e21-338">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="37e21-339">Místo toho zvažte zabalení zkratky v typu třídy nebo samostatného sjednocení sjednocení (nebo, pokud je zásadní výkon, zvažte použití typu struktury k zabalení zkratky).</span><span class="sxs-lookup"><span data-stu-id="37e21-339">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="37e21-340">Například se nachází na definování násobného mapování jako speciálního případu mapy F #, například:</span><span class="sxs-lookup"><span data-stu-id="37e21-340">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="37e21-341">Nicméně logické operace zápisu tečky na tomto typu nejsou stejné jako operace na mapě – například je vhodné, aby bylo mapování operátoru vyhledávání přijatelné. [key] vrátí prázdný seznam, pokud klíč není ve slovníku, namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="37e21-341">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="37e21-342">Pokyny pro knihovny pro použití z jiných jazyků .NET</span><span class="sxs-lookup"><span data-stu-id="37e21-342">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="37e21-343">Při navrhování knihoven pro použití z jiných jazyků .NET je důležité dodržovat [pokyny pro návrh knihovny .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="37e21-343">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="37e21-344">V tomto dokumentu jsou tyto knihovny označeny jako Vanilla knihovny .NET, na rozdíl od knihoven F #, které používají konstrukce F # bez omezení.</span><span class="sxs-lookup"><span data-stu-id="37e21-344">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="37e21-345">Návrh vanillach knihoven .NET znamená, že rozhraní API pro známé a idiomatickou, která jsou konzistentní se zbytkem .NET Framework tím, že minimalizují použití konstrukcí specifických pro jazyk F # ve veřejném rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="37e21-345">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="37e21-346">Pravidla jsou vysvětlena v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="37e21-346">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="37e21-347">Obor názvů a typ – návrh (pro knihovny používané z jiných jazyků rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="37e21-347">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="37e21-348">Použití konvencí vytváření názvů .NET pro veřejné rozhraní API vašich komponent</span><span class="sxs-lookup"><span data-stu-id="37e21-348">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="37e21-349">Věnujte zvláštní pozornost použití zkrácených názvů a pokynů pro psaní velkých písmen .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-349">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="37e21-350">Použití oborů názvů, typů a členů jako primární struktury organizace pro vaše komponenty</span><span class="sxs-lookup"><span data-stu-id="37e21-350">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="37e21-351">Všechny soubory obsahující veřejné funkce by měly začínat `namespace` deklarací a v oborech názvů by měly být jenom veřejné entity s přístupem.</span><span class="sxs-lookup"><span data-stu-id="37e21-351">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="37e21-352">Nepoužívejte moduly F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-352">Do not use F# modules.</span></span>

<span data-ttu-id="37e21-353">Používejte neveřejné moduly pro uchování implementačního kódu, typů nástrojů a funkcí nástrojů.</span><span class="sxs-lookup"><span data-stu-id="37e21-353">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="37e21-354">Statické typy by měly být upřednostňovány přes moduly, protože umožňují budoucí vývoj rozhraní API k použití přetížení a dalších konceptů návrhu rozhraní .NET API, které nesmí být použity v modulech jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-354">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="37e21-355">Například místo následujícího veřejného rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="37e21-355">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="37e21-356">Zvažte místo toho:</span><span class="sxs-lookup"><span data-stu-id="37e21-356">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="37e21-357">Použití typů záznamů jazyka F # v rozhraních API Vanilla .NET, pokud se návrh typů nevyvíjí</span><span class="sxs-lookup"><span data-stu-id="37e21-357">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="37e21-358">Typy záznamů F # jsou zkompilovány do jednoduché třídy .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-358">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="37e21-359">Ty jsou vhodné pro některé jednoduché a stabilní typy v rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="37e21-359">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="37e21-360">Zvažte použití `[<NoEquality>]` atributů a `[<NoComparison>]` pro potlačení automatické generace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="37e21-360">Consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="37e21-361">Nepoužívejte také proměnlivá pole záznamů v rozhraních API Vanilla .NET, protože tyto položky zveřejňují veřejné pole.</span><span class="sxs-lookup"><span data-stu-id="37e21-361">Also avoid using mutable record fields in vanilla .NET APIs as these expose a public field.</span></span> <span data-ttu-id="37e21-362">Vždy zvažte, zda by třída poskytovala pružnější možnost pro budoucí vývoj rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="37e21-362">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="37e21-363">Například následující kód F # zveřejňuje veřejné rozhraní API pro příjemce v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="37e21-363">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="37e21-364">F#:</span><span class="sxs-lookup"><span data-stu-id="37e21-364">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="37e21-365">C#:</span><span class="sxs-lookup"><span data-stu-id="37e21-365">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="37e21-366">Skrýt reprezentace typů sjednocení F # v rozhraních API Vanilla .NET</span><span class="sxs-lookup"><span data-stu-id="37e21-366">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="37e21-367">Typy sjednocení jazyka f # se běžně nepoužívají napříč hranicemi součástí, dokonce i pro kódování F # až-F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-367">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="37e21-368">Jsou to skvělé implementační zařízení, když se interně používá v rámci komponent a knihoven.</span><span class="sxs-lookup"><span data-stu-id="37e21-368">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="37e21-369">Při návrhu rozhraní Vanilla .NET API zvažte skrytí reprezentace typu sjednocení pomocí soukromé deklarace nebo souboru signatury.</span><span class="sxs-lookup"><span data-stu-id="37e21-369">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="37e21-370">Můžete také rozšířit typy, které používají reprezentace sjednocení interně se členy, aby poskytovaly požadované. Rozhraní API pro NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-370">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="37e21-371">Návrh grafického uživatelského rozhraní a dalších komponent pomocí vzorů návrhu rozhraní</span><span class="sxs-lookup"><span data-stu-id="37e21-371">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="37e21-372">V rozhraní .NET je k dispozici mnoho různých platforem, jako jsou WinForms, WPF a ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-372">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="37e21-373">Pokud navrhujete komponenty pro použití v těchto rozhraních, měli byste použít konvence pojmenování a návrhu pro každý z nich.</span><span class="sxs-lookup"><span data-stu-id="37e21-373">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="37e21-374">Například pro programování v WPF můžete pro třídy, které navrhujete, přijmout vzory návrhu WPF.</span><span class="sxs-lookup"><span data-stu-id="37e21-374">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="37e21-375">Pro modely v programování uživatelského rozhraní použijte vzory návrhu, jako jsou události a kolekce založené na oznámeních, jako jsou ty, které se nacházejí v <xref:System.Collections.ObjectModel> .</span><span class="sxs-lookup"><span data-stu-id="37e21-375">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="37e21-376">Návrh objektů a členů (pro knihovny používané z jiných jazyků rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="37e21-376">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="37e21-377">Použití atributu CLIEvent k vystavení událostí .NET</span><span class="sxs-lookup"><span data-stu-id="37e21-377">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="37e21-378">Sestavte a `DelegateEvent` s konkrétním typem delegáta .NET, který přebírá objekt a `EventArgs` (spíše než `Event` a, který pouze používá `FSharpHandler` typ ve výchozím nastavení), aby byly události publikovány známým způsobem pro jiné jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-378">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a><span data-ttu-id="37e21-379">Zveřejňujte asynchronní operace jako metody, které vracejí úlohy .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-379">Expose asynchronous operations as methods that return .NET tasks</span></span>

<span data-ttu-id="37e21-380">Úlohy se používají v rozhraní .NET ke znázornění aktivních asynchronních výpočtů.</span><span class="sxs-lookup"><span data-stu-id="37e21-380">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="37e21-381">Úlohy jsou všeobecně méně kompozice než objekty F # `Async<T>` , protože představují "již prováděné" úlohy a nemohou být složeny způsobem, který provádí paralelní složení nebo které skrývají šíření signálů zrušení a dalších kontextových parametrů.</span><span class="sxs-lookup"><span data-stu-id="37e21-381">Tasks are in general less compositional than F# `Async<T>` objects, since they represent "already executing" tasks and can't be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="37e21-382">Nicméně navzdory tomu metody, které vracejí úkoly, jsou standardní reprezentace asynchronního programování v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-382">However, despite this, methods that return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="37e21-383">Často také budete chtít přijmout explicitní token zrušení:</span><span class="sxs-lookup"><span data-stu-id="37e21-383">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="37e21-384">Použití typů delegátů .NET namísto typů funkcí F #</span><span class="sxs-lookup"><span data-stu-id="37e21-384">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="37e21-385">Zde "typy funkcí F #" znamenají "šipky" jako `int -> int` .</span><span class="sxs-lookup"><span data-stu-id="37e21-385">Here "F# function types" mean "arrow" types like `int -> int`.</span></span>

<span data-ttu-id="37e21-386">Místo toho:</span><span class="sxs-lookup"><span data-stu-id="37e21-386">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="37e21-387">Postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="37e21-387">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="37e21-388">Typ funkce F # se zobrazí jako `class FSharpFunc<T,U>` jiné jazyky .NET a je méně vhodný pro jazykové funkce a nástroje, které rozumí typům delegátů.</span><span class="sxs-lookup"><span data-stu-id="37e21-388">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understands delegate types.</span></span> <span data-ttu-id="37e21-389">Při vytváření vyšších objednávek, které cílí na .NET Framework 3,5 nebo vyšší, `System.Func` jsou delegáti a držitelé rozhraní `System.Action` API správná rozhraní API k publikování, aby mohli vývojáři rozhraní .NET spotřebovávat tato rozhraní API, a to s nízkým třením.</span><span class="sxs-lookup"><span data-stu-id="37e21-389">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="37e21-390">(Při cílení na .NET Framework 2,0 jsou typy delegátů definované systémem omezenější; zvažte použití předdefinovaných typů delegátů, jako je `System.Converter<T,U>` nebo definování konkrétního typu delegáta.)</span><span class="sxs-lookup"><span data-stu-id="37e21-390">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="37e21-391">Na překlopení nejsou Delegáti .NET pro knihovny orientované na F # přirozené (viz další část knihoven s podporou jazyka F #).</span><span class="sxs-lookup"><span data-stu-id="37e21-391">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="37e21-392">V důsledku toho je společná implementační strategie při vývoji metod vyšších pořadí pro knihovny Vanilla .NET určena k vytváření všech implementací pomocí typů funkcí jazyka F # a následnému vytvoření veřejného rozhraní API pomocí delegátů jako tenké fasády základem aktuální implementace F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-392">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="37e21-393">Použijte vzor TryGetValue místo vrácení hodnot možností F # a preferovat přetížení metody, aby se jako argumenty použily hodnoty možností jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-393">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="37e21-394">Běžné vzory použití pro typ možnosti jazyka F # v rozhraních API jsou lépe implementované v rozhraních API Vanilla .NET pomocí standardních technik návrhu .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-394">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="37e21-395">Místo vrácení hodnoty možnosti jazyka F # zvažte použití návratového typu bool plus výstupní parametr jako ve vzoru "TryGetValue".</span><span class="sxs-lookup"><span data-stu-id="37e21-395">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="37e21-396">A místo toho, aby jako parametry používaly hodnoty možností jazyka F #, zvažte použití přetížení metod nebo nepovinných argumentů.</span><span class="sxs-lookup"><span data-stu-id="37e21-396">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="37e21-397">Použijte rozhraní .NET Collection Types IEnumerable \< T \> a \< klíč IDictionary, hodnotu \> parametrů a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="37e21-397">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="37e21-398">Vyhněte se použití konkrétního typu kolekce, jako jsou pole .NET `T[]` , typy F # `list<T>` `Map<Key,Value>` a `Set<T>` a konkrétní typy kolekcí .NET, jako `Dictionary<Key,Value>` je například.</span><span class="sxs-lookup"><span data-stu-id="37e21-398">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="37e21-399">Pokyny pro návrh knihovny .NET mají dobré rady týkající se použití různých typů kolekcí, jako je `IEnumerable<T>` .</span><span class="sxs-lookup"><span data-stu-id="37e21-399">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="37e21-400">Některé použití polí ( `T[]` ) je v některých případech přijatelné z důvodů výkonu.</span><span class="sxs-lookup"><span data-stu-id="37e21-400">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="37e21-401">Pamatujte, že `seq<T>` je to pouze alias F # pro `IEnumerable<T>` , a proto SEQ je často vhodný typ pro rozhraní .NET API Vanilla.</span><span class="sxs-lookup"><span data-stu-id="37e21-401">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="37e21-402">Místo seznamů F #:</span><span class="sxs-lookup"><span data-stu-id="37e21-402">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="37e21-403">Použijte sekvence F #:</span><span class="sxs-lookup"><span data-stu-id="37e21-403">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="37e21-404">Použijte typ jednotky jako jediný vstupní typ metody pro definování metody s nulovým argumentem nebo jako jediný návratový typ pro definování metody vracející typ void.</span><span class="sxs-lookup"><span data-stu-id="37e21-404">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="37e21-405">Vyhněte se jiným použití typu jednotky.</span><span class="sxs-lookup"><span data-stu-id="37e21-405">Avoid other uses of the unit type.</span></span> <span data-ttu-id="37e21-406">Jsou dobré:</span><span class="sxs-lookup"><span data-stu-id="37e21-406">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="37e21-407">Toto je chybné:</span><span class="sxs-lookup"><span data-stu-id="37e21-407">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="37e21-408">Kontrolovat hodnoty null v hranicích rozhraní .NET API Vanilla</span><span class="sxs-lookup"><span data-stu-id="37e21-408">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="37e21-409">Implementační kód F # má za následek méně hodnot null, z důvodu neměnných vzorů návrhu a omezení použití literálů null pro typy F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-409">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="37e21-410">Jiné jazyky rozhraní .NET často používají hodnotu null jako hodnotu mnohem častěji.</span><span class="sxs-lookup"><span data-stu-id="37e21-410">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="37e21-411">Z tohoto důvodu kód F #, který vystavuje rozhraní Vanilla .NET API, by měl kontrolovat parametry pro hodnotu null na hranici rozhraní API a zabránit přetečení těchto hodnot do kódu implementace F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-411">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="37e21-412">`isNull`Lze použít funkci nebo porovnávání vzorů pro `null` vzor.</span><span class="sxs-lookup"><span data-stu-id="37e21-412">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="37e21-413">Nepoužívejte řazené kolekce členů jako návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="37e21-413">Avoid using tuples as return values</span></span>

<span data-ttu-id="37e21-414">Místo toho preferovat vrácení pojmenovaného typu, který uchovává agregovaná data, nebo použití parametrů out k vrácení více hodnot.</span><span class="sxs-lookup"><span data-stu-id="37e21-414">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="37e21-415">I když existují řazené kolekce členů a struktury v rozhraní .NET (včetně podpory jazyka C# pro řazené kolekce členů struktury), většinou neposkytují ideální a očekávané rozhraní API pro vývojáře na platformě .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-415">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="37e21-416">Vyhněte se použití procesu curryfikace parametrů</span><span class="sxs-lookup"><span data-stu-id="37e21-416">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="37e21-417">Místo toho použijte konvence volání rozhraní .NET `Method(arg1,arg2,…,argN)` .</span><span class="sxs-lookup"><span data-stu-id="37e21-417">Instead, use .NET calling conventions `Method(arg1,arg2,…,argN)`.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="37e21-418">Tip: Pokud navrhujete knihovny pro použití z libovolného jazyka .NET, nemusíte ve skutečnosti provádět nějaké experimentální prostředí C# a Visual Basic, aby se zajistilo, že se vaše knihovny "chovají" v těchto jazycích.</span><span class="sxs-lookup"><span data-stu-id="37e21-418">Tip: If you're designing libraries for use from any .NET language, then there's no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="37e21-419">Můžete také použít nástroje, jako je například reflektor .NET a Visual Studio Prohlížeč objektů, abyste zajistili, že se knihovny a dokumentace zobrazují podle očekávání vývojářům.</span><span class="sxs-lookup"><span data-stu-id="37e21-419">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="37e21-420">Příloha</span><span class="sxs-lookup"><span data-stu-id="37e21-420">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="37e21-421">Komplexní příklad návrhu kódu F # pro použití v jiných jazycích .NET</span><span class="sxs-lookup"><span data-stu-id="37e21-421">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="37e21-422">Vezměte v úvahu následující třídu:</span><span class="sxs-lookup"><span data-stu-id="37e21-422">Consider the following class:</span></span>

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

<span data-ttu-id="37e21-423">Odvozený typ F # této třídy je následující:</span><span class="sxs-lookup"><span data-stu-id="37e21-423">The inferred F# type of this class is as follows:</span></span>

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

<span data-ttu-id="37e21-424">Pojďme se podívat, jak se tento typ F # zobrazuje programátorovi pomocí jiného jazyka .NET.</span><span class="sxs-lookup"><span data-stu-id="37e21-424">Let's take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="37e21-425">Například přibližný podpis C# "signatura" je následující:</span><span class="sxs-lookup"><span data-stu-id="37e21-425">For example, the approximate C# "signature" is as follows:</span></span>

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="37e21-426">Existují některé důležité body, které si všimněte, jak jazyk F # představuje konstrukce.</span><span class="sxs-lookup"><span data-stu-id="37e21-426">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="37e21-427">Příklad:</span><span class="sxs-lookup"><span data-stu-id="37e21-427">For example:</span></span>

* <span data-ttu-id="37e21-428">Metadata, jako jsou názvy argumentů, byla zachována.</span><span class="sxs-lookup"><span data-stu-id="37e21-428">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="37e21-429">Metody F #, které přijímají dva argumenty, se stanou metodami jazyka C#, které přijímají dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="37e21-429">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="37e21-430">Funkce a seznamy se stanou odkazy na odpovídající typy v knihovně F #.</span><span class="sxs-lookup"><span data-stu-id="37e21-430">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="37e21-431">Následující kód ukazuje, jak upravit tento kód, aby se tyto věci zohlednily.</span><span class="sxs-lookup"><span data-stu-id="37e21-431">The following code shows how to adjust this code to take these things into account.</span></span>

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

<span data-ttu-id="37e21-432">Odvozený typ F # kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="37e21-432">The inferred F# type of the code is as follows:</span></span>

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

<span data-ttu-id="37e21-433">Signatura jazyka C# je teď následující:</span><span class="sxs-lookup"><span data-stu-id="37e21-433">The C# signature is now as follows:</span></span>

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="37e21-434">Tyto opravy pro přípravu tohoto typu pro použití jako součást knihovny .NET Vanilla jsou následující:</span><span class="sxs-lookup"><span data-stu-id="37e21-434">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="37e21-435">Bylo upraveno několik názvů: `Point1` , `n` , `l` a `f` `RadialPoint` `count` `factor` `transform` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="37e21-435">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="37e21-436">Byl použit návratový typ `seq<RadialPoint>` místo `RadialPoint list` pomocí změny konstrukce seznamu pomocí `[ ... ]` pro konstrukci sekvence pomocí `IEnumerable<RadialPoint>` .</span><span class="sxs-lookup"><span data-stu-id="37e21-436">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="37e21-437">Místo typu funkce F # se použil typ delegáta .NET `System.Func` .</span><span class="sxs-lookup"><span data-stu-id="37e21-437">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="37e21-438">Díky tomu se nicero, že se spotřebuje v kódu C#.</span><span class="sxs-lookup"><span data-stu-id="37e21-438">This makes it far nicer to consume in C# code.</span></span>
