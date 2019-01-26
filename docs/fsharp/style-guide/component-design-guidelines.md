---
title: F#Pokyny k návrhu komponenty
description: Přečtěte si pokyny pro zápis F# součásti určené pro využití dalších volajícími.
ms.date: 05/14/2018
ms.openlocfilehash: c61e4cd9098388b356c71c325d66c760fa866cf0
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066022"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="c4899-103">F#Pokyny k návrhu komponenty</span><span class="sxs-lookup"><span data-stu-id="c4899-103">F# component design guidelines</span></span>

<span data-ttu-id="c4899-104">Tento dokument je sada součástí pokyny návrhu pro F# programování, na základě F# pokyny k návrhu komponenty, v14 Microsoft Research a [jinou verzi](https://fsharp.org/specs/component-design-guidelines/) původně připravili a udržuje F# Software Foundation.</span><span class="sxs-lookup"><span data-stu-id="c4899-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and [another version](https://fsharp.org/specs/component-design-guidelines/) originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="c4899-105">Tento dokument předpokládá, že máte zkušenosti s F# programování.</span><span class="sxs-lookup"><span data-stu-id="c4899-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="c4899-106">Mnoho k F# komunity pro své příspěvky a užitečné zpětné vazby na různé verze tohoto průvodce.</span><span class="sxs-lookup"><span data-stu-id="c4899-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="c4899-107">Přehled</span><span class="sxs-lookup"><span data-stu-id="c4899-107">Overview</span></span>

<span data-ttu-id="c4899-108">Tento dokument vypadá na některé z problémů souvisejících s F# komponenta, návrh a psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="c4899-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="c4899-109">Komponenta může znamenat některý z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="c4899-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="c4899-110">Vrstvy v vaše F# projekt, který obsahuje externí uživatele v rámci tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="c4899-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="c4899-111">Knihovna určené ke spotřebě F# kódu přes hranice sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4899-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="c4899-112">Knihovna určena pro použití v jakémkoliv jazyce .NET přes hranice sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4899-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="c4899-113">Knihovny určené k distribuci přes úložiště balíčků, jako například [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="c4899-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="c4899-114">Použijte techniky popsané v tomto článku [pět zásadami dobrého F# kód](index.md#five-principles-of-good-f-code)a proto využívají obě funkční a objekt programování podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c4899-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="c4899-115">Bez ohledu na to metodologie komponenty a knihovny návrháře čelí celou řadu praktických a prosaic problémů při pokusu o vytvoření rozhraní API, které je snadno použitelný pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="c4899-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="c4899-116">Odepření aplikací [pokyny k návrhu knihovny .NET](../../standard/design-guidelines/index.md) bude řídit vytváření konzistentní sadu rozhraní API, která jsou příjemný využívat.</span><span class="sxs-lookup"><span data-stu-id="c4899-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="c4899-117">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="c4899-117">General guidelines</span></span>

<span data-ttu-id="c4899-118">Existuje několik univerzální pokyny, které se vztahují F# knihoven, bez ohledu na jeho zamýšlenou cílovou skupinou pro knihovnu.</span><span class="sxs-lookup"><span data-stu-id="c4899-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="c4899-119">Přečtěte si pokyny pro návrh knihovna .NET</span><span class="sxs-lookup"><span data-stu-id="c4899-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="c4899-120">Bez ohledu na typ z F# kódování provádíte, je důležité mít praktické znalosti [pokyny k návrhu knihovny .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="c4899-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="c4899-121">Většina jiných F# a programátory na platformě .NET se seznamte s těmito pokyny a očekávají kód .NET a odpovídat na ně.</span><span class="sxs-lookup"><span data-stu-id="c4899-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="c4899-122">Pokyny pro návrh knihovny .NET poskytují obecné pokyny týkající se názvů, navrhování tříd a rozhraní, návrhu člena (vlastnosti, metody, události atd.) a další a jsou užitečné první bod odkazu pro širokou škálu pokyny k návrhu.</span><span class="sxs-lookup"><span data-stu-id="c4899-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="c4899-123">Přidání komentáře k dokumentaci XML do kódu</span><span class="sxs-lookup"><span data-stu-id="c4899-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="c4899-124">Dokumentace XML v rámci veřejných API Ujistěte se, že se uživatelé dostanou skvělé technologie Intellisense a rychlé informace, při použití těchto typů a členů a povolit vytváření dokumentace pro knihovny souborů.</span><span class="sxs-lookup"><span data-stu-id="c4899-124">XML documentation on public APIs ensure that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="c4899-125">Zobrazit [dokumentace XML](../language-reference/xml-documentation.md) o různých značky xml, které lze použít pro další kód v rámci xmldoc komentáře.</span><span class="sxs-lookup"><span data-stu-id="c4899-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="c4899-126">Můžete použít buď krátký tvar XML komentáře (`/// comment`), nebo standardní komentáře XML (`///<summary>comment</summary>`).</span><span class="sxs-lookup"><span data-stu-id="c4899-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="c4899-127">Zvažte použití explicitního podpis souborů (.fsi) pro stabilní knihovny a komponenty rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c4899-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="c4899-128">Použití souborů explicitní podpisy v F# knihovna nabízí stručné shrnutí veřejné rozhraní API, které obě pomáhá zajistit, že znáte úplné veřejné povrchu vaše knihovna také poskytuje čisté oddělení mezi veřejné dokumentaci a interní Podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="c4899-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which both helps to ensure that you know the full public surface of your library, as well as provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="c4899-129">Všimněte si, že podpis souborů přidat případná problémová místa na měnící se veřejné rozhraní API, tak, že vyžaduje změny v implementaci a podpis souborů.</span><span class="sxs-lookup"><span data-stu-id="c4899-129">Note that signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="c4899-130">V důsledku toho podpis souborů by měl obvykle jenom zavést při rozhraní API má stát ztuhly a již má výrazně změnit.</span><span class="sxs-lookup"><span data-stu-id="c4899-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="c4899-131">Vždy postupujte podle osvědčené postupy pro používání řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="c4899-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="c4899-132">Postupujte podle [osvědčené postupy pro používání řetězců v .NET](../../standard/base-types/best-practices-strings.md) pokyny.</span><span class="sxs-lookup"><span data-stu-id="c4899-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="c4899-133">Konkrétně se vždy explicitně uvést *kulturní záměr* převod a porovnání řetězců (v případě potřeby).</span><span class="sxs-lookup"><span data-stu-id="c4899-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="c4899-134">Pokyny pro F#-směřující knihovny</span><span class="sxs-lookup"><span data-stu-id="c4899-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="c4899-135">Tato část nabízí doporučení pro vývoj veřejné F#-směřující knihoven; To znamená, knihovny vystavení veřejné rozhraní API, která mají být využívány službou F# vývojáři.</span><span class="sxs-lookup"><span data-stu-id="c4899-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="c4899-136">Existuje široká škála návrh knihovny doporučení platí konkrétně pro F#.</span><span class="sxs-lookup"><span data-stu-id="c4899-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="c4899-137">Chybí konkrétní doporučení, které následují jsou pokyny pro návrh knihovny .NET pokyny pro použití náhradní lokality.</span><span class="sxs-lookup"><span data-stu-id="c4899-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="c4899-138">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="c4899-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="c4899-139">Použití .NET konvence pojmenování a malá a velká písmena</span><span class="sxs-lookup"><span data-stu-id="c4899-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="c4899-140">V následující tabulce dodržovat konvence pojmenování a malá a velká písmena .NET.</span><span class="sxs-lookup"><span data-stu-id="c4899-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="c4899-141">Existují malé doplňky také F# vytvoří.</span><span class="sxs-lookup"><span data-stu-id="c4899-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="c4899-142">Konstrukce</span><span class="sxs-lookup"><span data-stu-id="c4899-142">Construct</span></span> | <span data-ttu-id="c4899-143">případ</span><span class="sxs-lookup"><span data-stu-id="c4899-143">Case</span></span> | <span data-ttu-id="c4899-144">Část</span><span class="sxs-lookup"><span data-stu-id="c4899-144">Part</span></span> | <span data-ttu-id="c4899-145">Příklady</span><span class="sxs-lookup"><span data-stu-id="c4899-145">Examples</span></span> | <span data-ttu-id="c4899-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4899-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="c4899-147">Konkrétní typy</span><span class="sxs-lookup"><span data-stu-id="c4899-147">Concrete types</span></span> | <span data-ttu-id="c4899-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-148">PascalCase</span></span> | <span data-ttu-id="c4899-149">Podstatné jméno / tvary přídavných jmen</span><span class="sxs-lookup"><span data-stu-id="c4899-149">Noun/ adjective</span></span> | <span data-ttu-id="c4899-150">Seznam, Double, komplexní</span><span class="sxs-lookup"><span data-stu-id="c4899-150">List, Double, Complex</span></span> | <span data-ttu-id="c4899-151">Konkrétní typy jsou struktury, třídy, výčty, delegáti, záznamů a sjednocení.</span><span class="sxs-lookup"><span data-stu-id="c4899-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="c4899-152">I když jsou tradičně malá písmena v OCaml, názvy typů F# přijala schéma pojmenování .NET pro typy.</span><span class="sxs-lookup"><span data-stu-id="c4899-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="c4899-153">knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="c4899-153">DLLs</span></span>           | <span data-ttu-id="c4899-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-154">PascalCase</span></span> |                 | <span data-ttu-id="c4899-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="c4899-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="c4899-156">Sjednocení značky</span><span class="sxs-lookup"><span data-stu-id="c4899-156">Union tags</span></span>     | <span data-ttu-id="c4899-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-157">PascalCase</span></span> | <span data-ttu-id="c4899-158">Podstatné jméno</span><span class="sxs-lookup"><span data-stu-id="c4899-158">Noun</span></span> | <span data-ttu-id="c4899-159">Některé, přidat, úspěch</span><span class="sxs-lookup"><span data-stu-id="c4899-159">Some, Add, Success</span></span> | <span data-ttu-id="c4899-160">Nepoužívejte předponu ve veřejných rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c4899-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="c4899-161">Volitelně použít předponu, když je to interní, jako například \`Zadejte týmů = TAlpha</span><span class="sxs-lookup"><span data-stu-id="c4899-161">Optionally use a prefix when internal, such as \`type Teams = TAlpha</span></span> | <span data-ttu-id="c4899-162">TBeta</span><span class="sxs-lookup"><span data-stu-id="c4899-162">TBeta</span></span> | <span data-ttu-id="c4899-163">TDelta.\`</span><span class="sxs-lookup"><span data-stu-id="c4899-163">TDelta.\`</span></span> |
| <span data-ttu-id="c4899-164">Událost</span><span class="sxs-lookup"><span data-stu-id="c4899-164">Event</span></span>          | <span data-ttu-id="c4899-165">PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-165">PascalCase</span></span> | <span data-ttu-id="c4899-166">Příkaz</span><span class="sxs-lookup"><span data-stu-id="c4899-166">Verb</span></span> | <span data-ttu-id="c4899-167">ValueChanged / ValueChanging</span><span class="sxs-lookup"><span data-stu-id="c4899-167">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="c4899-168">Výjimky</span><span class="sxs-lookup"><span data-stu-id="c4899-168">Exceptions</span></span>     | <span data-ttu-id="c4899-169">PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-169">PascalCase</span></span> |      | <span data-ttu-id="c4899-170">WebException</span><span class="sxs-lookup"><span data-stu-id="c4899-170">WebException</span></span> | <span data-ttu-id="c4899-171">Název by měl končit "Výjimek".</span><span class="sxs-lookup"><span data-stu-id="c4899-171">Name should end with “Exception”.</span></span> |
| <span data-ttu-id="c4899-172">Pole</span><span class="sxs-lookup"><span data-stu-id="c4899-172">Field</span></span>          | <span data-ttu-id="c4899-173">PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-173">PascalCase</span></span> | <span data-ttu-id="c4899-174">Podstatné jméno</span><span class="sxs-lookup"><span data-stu-id="c4899-174">Noun</span></span> | <span data-ttu-id="c4899-175">CurrentName</span><span class="sxs-lookup"><span data-stu-id="c4899-175">CurrentName</span></span>  | |
| <span data-ttu-id="c4899-176">Typy rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4899-176">Interface types</span></span> |  <span data-ttu-id="c4899-177">PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-177">PascalCase</span></span> | <span data-ttu-id="c4899-178">Podstatné jméno / tvary přídavných jmen</span><span class="sxs-lookup"><span data-stu-id="c4899-178">Noun/ adjective</span></span> | <span data-ttu-id="c4899-179">Rozhraní IDisposable</span><span class="sxs-lookup"><span data-stu-id="c4899-179">IDisposable</span></span> | <span data-ttu-id="c4899-180">Název by měl začínat "I".</span><span class="sxs-lookup"><span data-stu-id="c4899-180">Name should start with “I”.</span></span> |
| <span data-ttu-id="c4899-181">Metoda</span><span class="sxs-lookup"><span data-stu-id="c4899-181">Method</span></span> |  <span data-ttu-id="c4899-182">PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-182">PascalCase</span></span> |  <span data-ttu-id="c4899-183">Příkaz</span><span class="sxs-lookup"><span data-stu-id="c4899-183">Verb</span></span> | <span data-ttu-id="c4899-184">ToString</span><span class="sxs-lookup"><span data-stu-id="c4899-184">ToString</span></span> | |
| <span data-ttu-id="c4899-185">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="c4899-185">Namespace</span></span> | <span data-ttu-id="c4899-186">PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-186">PascalCase</span></span> | | <span data-ttu-id="c4899-187">Microsoft.FSharp.Core</span><span class="sxs-lookup"><span data-stu-id="c4899-187">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="c4899-188">Obvykle používají `<Organization>.<Technology>[.<Subnamespace>]`, i když vyřadit organizace, pokud se tato technologie je nezávislé na organizaci.</span><span class="sxs-lookup"><span data-stu-id="c4899-188">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="c4899-189">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4899-189">Parameters</span></span> | <span data-ttu-id="c4899-190">camelCase</span><span class="sxs-lookup"><span data-stu-id="c4899-190">camelCase</span></span> | <span data-ttu-id="c4899-191">Podstatné jméno</span><span class="sxs-lookup"><span data-stu-id="c4899-191">Noun</span></span> |  <span data-ttu-id="c4899-192">typeName, transformace, rozsahu</span><span class="sxs-lookup"><span data-stu-id="c4899-192">typeName, transform, range</span></span> | |
| <span data-ttu-id="c4899-193">umožní hodnoty (interní)</span><span class="sxs-lookup"><span data-stu-id="c4899-193">let values (internal)</span></span> | <span data-ttu-id="c4899-194">camelCase nebo formátu PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-194">camelCase or PascalCase</span></span> | <span data-ttu-id="c4899-195">Podstatné jméno / příkaz</span><span class="sxs-lookup"><span data-stu-id="c4899-195">Noun/ verb</span></span> |  <span data-ttu-id="c4899-196">getValue myTable</span><span class="sxs-lookup"><span data-stu-id="c4899-196">getValue, myTable</span></span> |
| <span data-ttu-id="c4899-197">umožní hodnoty (externí)</span><span class="sxs-lookup"><span data-stu-id="c4899-197">let values (external)</span></span> | <span data-ttu-id="c4899-198">camelCase nebo formátu PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-198">camelCase or PascalCase</span></span> | <span data-ttu-id="c4899-199">Podstatné jméno/příkaz</span><span class="sxs-lookup"><span data-stu-id="c4899-199">Noun/verb</span></span>  | <span data-ttu-id="c4899-200">List.map Dates.Today</span><span class="sxs-lookup"><span data-stu-id="c4899-200">List.map, Dates.Today</span></span> | <span data-ttu-id="c4899-201">vazbou let hodnoty jsou často veřejné, pokud následující vzory návrhu tradiční funkční.</span><span class="sxs-lookup"><span data-stu-id="c4899-201">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="c4899-202">Ale obecně používejte PascalCase identifikátor lze použít v jiných jazycích rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c4899-202">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="c4899-203">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c4899-203">Property</span></span>  | <span data-ttu-id="c4899-204">PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-204">PascalCase</span></span>  | <span data-ttu-id="c4899-205">Podstatné jméno / tvary přídavných jmen</span><span class="sxs-lookup"><span data-stu-id="c4899-205">Noun/ adjective</span></span>  | <span data-ttu-id="c4899-206">IsEndOfFile, BackColor</span><span class="sxs-lookup"><span data-stu-id="c4899-206">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="c4899-207">Logické vlastnosti obecně použití je a můžete a musí být kladná, stejně jako v IsEndOfFile, ne IsNotEndOfFile.</span><span class="sxs-lookup"><span data-stu-id="c4899-207">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="c4899-208">Vyhněte se zkratky</span><span class="sxs-lookup"><span data-stu-id="c4899-208">Avoid abbreviations</span></span>

<span data-ttu-id="c4899-209">Pokyny .NET bránit použití zkratky (například "použít `OnButtonClick` spíše než `OnBtnClick`").</span><span class="sxs-lookup"><span data-stu-id="c4899-209">The .NET guidelines discourage the use of abbreviations (for example, “use `OnButtonClick` rather than `OnBtnClick`”).</span></span> <span data-ttu-id="c4899-210">Běžné zkratky, jako například `Async` pro "Asynchronní", jsou tolerovat.</span><span class="sxs-lookup"><span data-stu-id="c4899-210">Common abbreviations, such as `Async` for “Asynchronous”, are tolerated.</span></span> <span data-ttu-id="c4899-211">Toto pravidlo je někdy ignorován pro funkční programování. například `List.iter` používá zkratkou pro "iterovat".</span><span class="sxs-lookup"><span data-stu-id="c4899-211">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for “iterate”.</span></span> <span data-ttu-id="c4899-212">Z tohoto důvodu pomocí zkratky obvykle tolerovat do značné míry v F#- na -F# programování, ale mělo by se vyhnout stále obecně veřejné součásti návrhu.</span><span class="sxs-lookup"><span data-stu-id="c4899-212">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="c4899-213">Vyhněte se malá a velká písmena kolize názvů</span><span class="sxs-lookup"><span data-stu-id="c4899-213">Avoid casing name collisions</span></span>

<span data-ttu-id="c4899-214">Pokyny .NET Řekněme, že malá a velká písmena samostatně nelze použít k rozlišení kolize názvů, protože některé jazyky klienta (například Visual Basic) jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="c4899-214">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="c4899-215">Použití zkratky, kde je to vhodné</span><span class="sxs-lookup"><span data-stu-id="c4899-215">Use acronyms where appropriate</span></span>

<span data-ttu-id="c4899-216">Zkratky, jako je například XML nejsou zkratky a běžně používané knihovny .NET v podobě nezačínající (Xml).</span><span class="sxs-lookup"><span data-stu-id="c4899-216">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="c4899-217">Pouze by měla sloužit dobře známou a široce uznávané zkratky.</span><span class="sxs-lookup"><span data-stu-id="c4899-217">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="c4899-218">Použít pro obecný parametr názvy PascalCase</span><span class="sxs-lookup"><span data-stu-id="c4899-218">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="c4899-219">Pomocí PascalCase pro obecný parametr názvy ve veřejných rozhraní API, včetně F#-směřující knihovny.</span><span class="sxs-lookup"><span data-stu-id="c4899-219">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="c4899-220">Zejména použijte názvy jako `T`, `U`, `T1`, `T2` pro libovolný obecných parametrů a konkrétní názvy dávat smysl, pak F#– různé knihovny používají názvy jako `Key`, `Value`, `Arg` (ale ne třeba `TKey`).</span><span class="sxs-lookup"><span data-stu-id="c4899-220">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="c4899-221">Pomocí PascalCase nebo camelCase pro veřejné funkce a hodnoty v F# moduly</span><span class="sxs-lookup"><span data-stu-id="c4899-221">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="c4899-222">camelCase se používá pro veřejné funkce, které jsou určeny pro použití nekvalifikované (například `invalidArg`) a pro "funkce standardní kolekce" (například List.map).</span><span class="sxs-lookup"><span data-stu-id="c4899-222">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the “standard collection functions” (for example, List.map).</span></span> <span data-ttu-id="c4899-223">V obou těchto případech se názvy funkcí fungují podobně jako klíčová slova v jazyce.</span><span class="sxs-lookup"><span data-stu-id="c4899-223">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="c4899-224">Objekt, typ a modul návrhu</span><span class="sxs-lookup"><span data-stu-id="c4899-224">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="c4899-225">Použití oboru názvů nebo moduly tak, aby obsahovala modulů a typů</span><span class="sxs-lookup"><span data-stu-id="c4899-225">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="c4899-226">Každý F# soubor v komponentě by měl začínat deklarace oboru názvů nebo modulu deklarace.</span><span class="sxs-lookup"><span data-stu-id="c4899-226">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="c4899-227">or</span><span class="sxs-lookup"><span data-stu-id="c4899-227">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="c4899-228">Rozdíly mezi použitím modulů a oborů názvů k uspořádání kódu na nejvyšší úrovni jsou následující:</span><span class="sxs-lookup"><span data-stu-id="c4899-228">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="c4899-229">Obory názvů může zahrnovat více souborů</span><span class="sxs-lookup"><span data-stu-id="c4899-229">Namespaces can span multiple files</span></span>
* <span data-ttu-id="c4899-230">Obory názvů nemůžou obsahovat F# funkce, které nejsou v rámci vnitřní modul</span><span class="sxs-lookup"><span data-stu-id="c4899-230">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="c4899-231">Kód pro libovolný daný modul musí být obsažena v rámci jednoho souboru</span><span class="sxs-lookup"><span data-stu-id="c4899-231">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="c4899-232">Moduly nejvyšší úrovně může obsahovat F# funkce bez nutnosti pro vnitřní modul</span><span class="sxs-lookup"><span data-stu-id="c4899-232">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="c4899-233">Volba mezi nejvyšší úrovně oboru názvů nebo modulu ovlivňuje kompilovaný formy kód a proto bude mít vliv na zobrazení z jiných jazyků .NET by vaše rozhraní API nakonec využívat mimo F# kódu.</span><span class="sxs-lookup"><span data-stu-id="c4899-233">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="c4899-234">Použijte metody a vlastnosti pro operace, které jsou přirozené pro typy objektů</span><span class="sxs-lookup"><span data-stu-id="c4899-234">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="c4899-235">Při práci s objekty, je nejvhodnější zajistit, že použitelné funkce je implementovaná jako metody a vlastnosti tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="c4899-235">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="c4899-236">Hromadné funkce pro daný člen nemusí nutně je implementovat do tohoto člena, ale by měl být použitelné částí, které tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="c4899-236">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="c4899-237">Použití tříd k zapouzdření proměnlivý stav</span><span class="sxs-lookup"><span data-stu-id="c4899-237">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="c4899-238">V F#, to jenom je potřeba udělat kde, stav se už zapouzdřená pomocí konstrukce jazyka, jako je například uzávěru, výrazu pořadí nebo asynchronní výpočet.</span><span class="sxs-lookup"><span data-stu-id="c4899-238">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="c4899-239">Pomocí rozhraní můžete seskupovat související operace</span><span class="sxs-lookup"><span data-stu-id="c4899-239">Use interfaces to group related operations</span></span>

<span data-ttu-id="c4899-240">Představuje sadu operací pomocí typy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4899-240">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="c4899-241">Toto je upřednostňována před další možnosti, jako je například řazených kolekcí členů, funkcí nebo záznamy o funkce.</span><span class="sxs-lookup"><span data-stu-id="c4899-241">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="c4899-242">V preference pro:</span><span class="sxs-lookup"><span data-stu-id="c4899-242">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="c4899-243">Rozhraní jsou prvotřídní koncepty v .NET, která vám umožní dosáhnout co Funktory by obvykle poskytují.</span><span class="sxs-lookup"><span data-stu-id="c4899-243">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="c4899-244">Kromě toho se můžete použít ke kódování existenční typů do programu, který zaznamenává funkce nelze.</span><span class="sxs-lookup"><span data-stu-id="c4899-244">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a><span data-ttu-id="c4899-245">Použít modul a funkce skupiny, které fungují v kolekcích</span><span class="sxs-lookup"><span data-stu-id="c4899-245">Use a module to group functions which act on collections</span></span>

<span data-ttu-id="c4899-246">Při definování typu kolekce vezměte v úvahu poskytuje standardní sadu operací, jako jsou `CollectionType.map` a `CollectionType.iter`) pro nové typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="c4899-246">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="c4899-247">Pokud zahrnete tyto modul, použijte standardní zásady vytváření názvů pro funkce v FSharp.Core.</span><span class="sxs-lookup"><span data-stu-id="c4899-247">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="c4899-248">Použít modul a funkce skupiny pro běžné, kanonické funkce, zejména v matematické a knihovny DSL</span><span class="sxs-lookup"><span data-stu-id="c4899-248">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="c4899-249">Například `Microsoft.FSharp.Core.Operators` je automaticky otevřené kolekce funkce nejvyšší úrovně (třeba `abs` a `sin`) poskytované FSharp.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="c4899-249">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="c4899-250">Obdobně statistiky knihovny mohou zahrnovat modul s funkcí `erf` a `erfc`, ve kterém se tento modul slouží k explicitně nebo automaticky otevřít.</span><span class="sxs-lookup"><span data-stu-id="c4899-250">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="c4899-251">Zvažte použití RequireQualifiedAccess a pečlivě použití AutoOpen atributů</span><span class="sxs-lookup"><span data-stu-id="c4899-251">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="c4899-252">Přidávání `[<RequireQualifiedAccess>]` atribut do modulu označuje, že modul nelze otevřít, a přístup, vyžaduje explicitní odkazy na elementy modulu kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="c4899-252">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="c4899-253">Například `Microsoft.FSharp.Collections.List` modul nemá tento atribut.</span><span class="sxs-lookup"><span data-stu-id="c4899-253">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="c4899-254">To je užitečné, když funkce a hodnoty v modulu mají názvy, které jsou pravděpodobně v konfliktu s názvy v dalších modulů.</span><span class="sxs-lookup"><span data-stu-id="c4899-254">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="c4899-255">Které vyžadují přístup pro kvalifikovaný může výrazně zvýšit dlouhodobou udržovatelnost a ovlivňujících knihovny.</span><span class="sxs-lookup"><span data-stu-id="c4899-255">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="c4899-256">Přidávání `[<AutoOpen>]` atribut do modulu znamená, že modul se otevřou při otevření nadřazeného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c4899-256">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="c4899-257">`[<AutoOpen>]` Atribut může také použít k sestavení k označení modulu, který se automaticky otevře, když na toto sestavení odkazuje.</span><span class="sxs-lookup"><span data-stu-id="c4899-257">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="c4899-258">Například knihovna statistiky **MathsHeaven.Statistics** může obsahovat `module MathsHeaven.Statistics.Operators` obsahující funkce `erf` a `erfc`.</span><span class="sxs-lookup"><span data-stu-id="c4899-258">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="c4899-259">Je možné logicky označit tento modul jako `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="c4899-259">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="c4899-260">To znamená, že `open MathsHeaven.Statistics` také otevřít tento modul a převést názvy `erf` a `erfc` do oboru.</span><span class="sxs-lookup"><span data-stu-id="c4899-260">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="c4899-261">Použití jiného dobré `[<AutoOpen>]` je pro moduly obsahující metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c4899-261">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="c4899-262">Nadměrné použití z `[<AutoOpen>]` potenciálních zákazníků na znečištěné obory názvů a atribut by měla být používána opatrně.</span><span class="sxs-lookup"><span data-stu-id="c4899-262">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="c4899-263">Pro konkrétní knihovny z určitých domén, rozumné využívání `[<AutoOpen>]` může mít za následek lepší použitelnost.</span><span class="sxs-lookup"><span data-stu-id="c4899-263">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="c4899-264">Definovat operátor členy ve třídách, kdy je vhodné pomocí známých operátorů</span><span class="sxs-lookup"><span data-stu-id="c4899-264">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="c4899-265">Někdy třídy se používají k modelování matematické konstrukce, jako jsou vektory.</span><span class="sxs-lookup"><span data-stu-id="c4899-265">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="c4899-266">Pokud má doména modelovaných dobře známých operátorů, je definují jako členy, které jsou přirozené pro třídu je užitečné.</span><span class="sxs-lookup"><span data-stu-id="c4899-266">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="c4899-267">Tyto doprovodné materiály odpovídá obecné pokyny .NET pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="c4899-267">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="c4899-268">Však může být také důležité v F# psaní kódu, jako to umožňuje těchto typů, který se má použít ve spojení s F# funkcí a metod s omezeními členů, jako je například List.sumBy.</span><span class="sxs-lookup"><span data-stu-id="c4899-268">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="c4899-269">Zvažte použití compiledname – pro zajištění. NET – popisný název pro ostatní uživatelé jazyka .NET</span><span class="sxs-lookup"><span data-stu-id="c4899-269">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="c4899-270">Někdy můžete chtít název ve stylu jeden pro F# příjemci (třeba statický člen malými písmeny, tak že se objeví jako by šlo modulu vázané funkce), ale mají jiný styl pro název při kompilaci do sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4899-270">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="c4899-271">Můžete použít `[<CompiledName>]` atribut zadejte jiný styl pro jiné F# využívání sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="c4899-271">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="c4899-272">S použitím `[<CompiledName>]`, můžete použít zásady vytváření názvů .NET pro jiné F# příjemci sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4899-272">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="c4899-273">Použijte přetížení metody pro členské funkce, pokud to poskytuje rozhraní API jednodušší</span><span class="sxs-lookup"><span data-stu-id="c4899-273">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="c4899-274">Přetížení metody je výkonný nástroj pro zjednodušení rozhraní API, které může být zapotřebí provést podobné funkce, ale s jinou možností nebo argumenty.</span><span class="sxs-lookup"><span data-stu-id="c4899-274">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="c4899-275">V F#, je běžné přetížení na počet argumentů, spíše než typy argumentů.</span><span class="sxs-lookup"><span data-stu-id="c4899-275">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="c4899-276">Skrýt reprezentace záznam a typy sjednocení, pokud návrh z těchto typů je pravděpodobně rozvoj</span><span class="sxs-lookup"><span data-stu-id="c4899-276">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="c4899-277">Zamezení odhalení konkrétní reprezentace objektů.</span><span class="sxs-lookup"><span data-stu-id="c4899-277">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="c4899-278">Například konkrétní reprezentace <xref:System.DateTime> hodnoty neposkytuje externí, veřejné rozhraní API návrhu knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="c4899-278">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="c4899-279">V době běhu modul Common Language Runtime ví potvrzené implementace, která se použije v průběhu provádění.</span><span class="sxs-lookup"><span data-stu-id="c4899-279">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="c4899-280">Ale zkompilovaný kód nebude sám sbírání závislosti na konkrétní reprezentace.</span><span class="sxs-lookup"><span data-stu-id="c4899-280">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="c4899-281">Vyhněte se použití implementace dědičnosti pro rozšíření</span><span class="sxs-lookup"><span data-stu-id="c4899-281">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="c4899-282">V F#, implementace dědičnosti je zřídka se používá.</span><span class="sxs-lookup"><span data-stu-id="c4899-282">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="c4899-283">Hierarchie dědičnosti jsou navíc často složité a těžko změnit příchod nové požadavky.</span><span class="sxs-lookup"><span data-stu-id="c4899-283">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="c4899-284">Implementace dědičnosti se stále nachází v F# pro kompatibilitu a výjimečných případech, kdy je nejlepší řešení problému, ale alternativní postupy, které se má hledat v vaše F# programy při návrhu pro polymorfismus, jako je například rozhraní implementace.</span><span class="sxs-lookup"><span data-stu-id="c4899-284">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="c4899-285">Funkce a člen podpisy</span><span class="sxs-lookup"><span data-stu-id="c4899-285">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="c4899-286">Použití řazených kolekcí členů pro vrácené hodnoty při vrácení malý počet víc nesouvisejících hodnot</span><span class="sxs-lookup"><span data-stu-id="c4899-286">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="c4899-287">Tady je typickým příkladem použití řazené kolekce členů v návratovém typu:</span><span class="sxs-lookup"><span data-stu-id="c4899-287">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="c4899-288">Návratové typy obsahující mnoho komponent, nebo pokud komponenty se vztahují k jedné entity identifikovatelné, zvažte použití pojmenovaného typu namísto řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="c4899-288">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="c4899-289">Použití `Async<T>` pro asynchronní programování v F# hranice rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c4899-289">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="c4899-290">Pokud je odpovídající synchronní operace s názvem `Operation` , která vrací `T`, pak by měl být pojmenován asynchronní operace `AsyncOperation` vrátí-li `Async<T>` nebo `OperationAsync` vrátí-li `Task<T>`.</span><span class="sxs-lookup"><span data-stu-id="c4899-290">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="c4899-291">Pro běžně používané typy .NET, která zpřístupňují metody Begin/End, zvažte použití `Async.FromBeginEnd` zápis rozšiřující metody jako adaptační vrstva poskytnout F# asynchronní programovací model pro tato rozhraní API pro .NET.</span><span class="sxs-lookup"><span data-stu-id="c4899-291">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

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

### <a name="exceptions"></a><span data-ttu-id="c4899-292">Výjimky</span><span class="sxs-lookup"><span data-stu-id="c4899-292">Exceptions</span></span>

<span data-ttu-id="c4899-293">Zobrazit [Správa chyb](conventions.md#error-management) Další informace o řádném používání výjimky, výsledky a možnosti.</span><span class="sxs-lookup"><span data-stu-id="c4899-293">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="c4899-294">Členy rozšíření</span><span class="sxs-lookup"><span data-stu-id="c4899-294">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="c4899-295">Pečlivě použít F# členy rozšíření v F#- na -F# komponenty</span><span class="sxs-lookup"><span data-stu-id="c4899-295">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="c4899-296">F#členy rozšíření by měla obecně sloužit pouze pro operace, které jsou v tomto uzávěru vnitřní operace spojené s typem ve většině režimech použití.</span><span class="sxs-lookup"><span data-stu-id="c4899-296">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="c4899-297">Jeden společný slouží k poskytování rozhraní API, která jsou k více idiomatickou F# pro různé typy .NET:</span><span class="sxs-lookup"><span data-stu-id="c4899-297">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="c4899-298">Typy sjednocení</span><span class="sxs-lookup"><span data-stu-id="c4899-298">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="c4899-299">Používat rozlišovaných unionů místo hierarchií tříd stromovou strukturou dat</span><span class="sxs-lookup"><span data-stu-id="c4899-299">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="c4899-300">Jako stromové struktury jsou definované rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="c4899-300">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="c4899-301">Toto je nevhodnou s dědičnosti, ale elegantní s rozlišovaná sjednocení.</span><span class="sxs-lookup"><span data-stu-id="c4899-301">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="c4899-302">Představující data jako stromové struktury s Rozlišované sjednocení také umožňuje využívat úplnosti v porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="c4899-302">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="c4899-303">Použití `[<RequireQualifiedAccess>]` na názvy případu nejsou dostatečně jedinečné typy sjednocení</span><span class="sxs-lookup"><span data-stu-id="c4899-303">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="c4899-304">Může být pro vás sami v doméně, kde je nejlepší název pro různé věci, jako je například rozlišovaného sjednocení s případy se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="c4899-304">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="c4899-305">Můžete použít `[<RequireQualifiedAccess>]` k rozlišení velikosti písmen názvů, pokud se chcete vyhnout, aktivuje se matoucí chyby vzniklé v důsledku stínováním závisí na řazení `open` příkazy</span><span class="sxs-lookup"><span data-stu-id="c4899-305">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="c4899-306">Skrýt reprezentace rozlišovaná sjednocení binární kompatibilních rozhraní API, pokud návrh z těchto typů je pravděpodobně rozvoj</span><span class="sxs-lookup"><span data-stu-id="c4899-306">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="c4899-307">Typy sjednocení se opírají o F# porovnávání vzorů formulářů stručné programovací model.</span><span class="sxs-lookup"><span data-stu-id="c4899-307">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="c4899-308">Jak už bylo zmíněno dříve, měli byste se vyhnout, odhalení reprezentace konkrétní data, pokud je pravděpodobné vyvíjí, návrh tyto typy.</span><span class="sxs-lookup"><span data-stu-id="c4899-308">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="c4899-309">Například reprezentace diskriminované sjednocení může být skrytá používání soukromý nebo interní prohlášení, nebo pomocí souboru podpisu.</span><span class="sxs-lookup"><span data-stu-id="c4899-309">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="c4899-310">Pokud uvedete rozlišovaná sjednocení bez, možná bude obtížné verze knihovny bez narušení uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="c4899-310">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="c4899-311">Místo toho zvažte odhalení nejmíň jeden aktivní vzory tak, aby povolovala porovnávání vzorů přes hodnoty stejného typu.</span><span class="sxs-lookup"><span data-stu-id="c4899-311">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="c4899-312">Aktivní vzory poskytují alternativní způsob, jak poskytnout F# zákazníky prostřednictvím porovnávání vzorů při obcházení vystavení F# přímo typy sjednocení.</span><span class="sxs-lookup"><span data-stu-id="c4899-312">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="c4899-313">Vložené funkce a členská omezení</span><span class="sxs-lookup"><span data-stu-id="c4899-313">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="c4899-314">Definujte obecná numerické algoritmy použití vložených funkcí s staticky řešeného obecné typy a předpokládané členská omezení</span><span class="sxs-lookup"><span data-stu-id="c4899-314">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="c4899-315">Aritmetické členská omezení a F# porovnání omezení jsou standardní pro F# programování.</span><span class="sxs-lookup"><span data-stu-id="c4899-315">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="c4899-316">Zvažte například následující kód:</span><span class="sxs-lookup"><span data-stu-id="c4899-316">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="c4899-317">Typ této funkce je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c4899-317">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="c4899-318">Toto je vhodná funkce pro veřejné rozhraní API v matematické knihovně.</span><span class="sxs-lookup"><span data-stu-id="c4899-318">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="c4899-319">Vyhněte se použití členská omezení pro simulaci typu třídy a duck psaní</span><span class="sxs-lookup"><span data-stu-id="c4899-319">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="c4899-320">Je možné simulovat pomocí "duck psát" F# omezeními člena.</span><span class="sxs-lookup"><span data-stu-id="c4899-320">It is possible to simulate “duck typing” using F# member constraints.</span></span> <span data-ttu-id="c4899-321">Ale členy, které pomocí tohoto objektu není v obecné je třeba použít F#- na -F# návrhy knihovny.</span><span class="sxs-lookup"><span data-stu-id="c4899-321">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="c4899-322">Je to proto, že knihovna návrhy založené na neznámého nebo nestandardní implicitní omezení vést k uživatelský kód pro nepřizpůsobitelným a vázané na jednu konkrétní architekturu vzor.</span><span class="sxs-lookup"><span data-stu-id="c4899-322">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="c4899-323">Kromě toho je vhodné šance, že se hojně používají členská omezení tímto způsobem může vést k velmi dlouhé kompilace časy.</span><span class="sxs-lookup"><span data-stu-id="c4899-323">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="c4899-324">Definice – operátor</span><span class="sxs-lookup"><span data-stu-id="c4899-324">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="c4899-325">Vyhněte se definování vlastní symbolické operátory</span><span class="sxs-lookup"><span data-stu-id="c4899-325">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="c4899-326">Vlastní operátory jsou nezbytné v některých situacích a jsou velmi užitečné konvenční zařízení v rámci rozsáhlý implementační kód.</span><span class="sxs-lookup"><span data-stu-id="c4899-326">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="c4899-327">Pro nové uživatele do knihovny jsou často pojmenované funkce usnadňuje používání.</span><span class="sxs-lookup"><span data-stu-id="c4899-327">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="c4899-328">Kromě toho vlastní symbolické operátory může být obtížné dokumentů a uživatelé najdou obtížnější k vyhledání nápovědy operátorů, protože existující v integrovaném vývojovém prostředí a hledání.</span><span class="sxs-lookup"><span data-stu-id="c4899-328">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="c4899-329">V důsledku toho je nejvhodnější publikovat vaše funkce jako pojmenované funkce a členy a kromě toho zpřístupnit operátory pro tuto funkci pouze v případě, že konvenční výhody převáží nad dokumentace a kognitivní náklady s nimi.</span><span class="sxs-lookup"><span data-stu-id="c4899-329">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="c4899-330">Měrné jednotky</span><span class="sxs-lookup"><span data-stu-id="c4899-330">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="c4899-331">Pečlivě použít měrné jednotky pro přidání typovou bezpečnost v F# kódu</span><span class="sxs-lookup"><span data-stu-id="c4899-331">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="c4899-332">Další informace o psaní za jednotky měření se vymažou při prohlížení jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c4899-332">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="c4899-333">Mějte na paměti, že součásti rozhraní .NET, nástroje a reflexe se zobrazí typy sítí SAN jednotky.</span><span class="sxs-lookup"><span data-stu-id="c4899-333">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="c4899-334">Například C# uživatelé uvidí `float` spíše než `float<kg>`.</span><span class="sxs-lookup"><span data-stu-id="c4899-334">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="c4899-335">Zkratky typů</span><span class="sxs-lookup"><span data-stu-id="c4899-335">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="c4899-336">Zkratky typů pečlivě slouží ke zjednodušení F# kódu</span><span class="sxs-lookup"><span data-stu-id="c4899-336">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="c4899-337">Součásti rozhraní .NET, nástroje a reflexe nezobrazí zkrácené názvy typů.</span><span class="sxs-lookup"><span data-stu-id="c4899-337">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="c4899-338">Významné použití zkratek typů lze také nastavit domény zobrazí složitější, než kolik jich je skutečně, který by mohl zaměnit příjemci.</span><span class="sxs-lookup"><span data-stu-id="c4899-338">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="c4899-339">Zkratky typů pro veřejné typy, členy a vlastnosti by měla být vnitřně liší od těch, které jsou k dispozici na na typ, který se u zkracovaného vyhnout</span><span class="sxs-lookup"><span data-stu-id="c4899-339">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="c4899-340">V takovém případě typ, který se u zkracovaného odhalí příliš mnoho o reprezentaci skutečný typ definuje.</span><span class="sxs-lookup"><span data-stu-id="c4899-340">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="c4899-341">Místo toho zvažte možnost uzavřít – zkratka typu třídy nebo diskriminované sjednocení jedním případem (nebo když zásadní je výkon, zvažte použití typu Struktura zabalit zkratky).</span><span class="sxs-lookup"><span data-stu-id="c4899-341">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="c4899-342">Je třeba chtěli definovat více mapy jako speciální případ F# namapovat, například:</span><span class="sxs-lookup"><span data-stu-id="c4899-342">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="c4899-343">Ale operace logického tečkami u tohoto typu nejsou stejná jako operace na mapě – například je možné logicky, že operátor vyhledávání mapy. [klíče] vrátí prázdný seznam, pokud není klíč ve slovníku, namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="c4899-343">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="c4899-344">Pokyny pro knihovny pro použití v jiných jazycích rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="c4899-344">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="c4899-345">Při navrhování knihoven pro použití v jiných jazycích .NET, je potřeba dodržovat [pokyny k návrhu knihovny .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="c4899-345">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="c4899-346">V tomto dokumentu tyto knihovny jsou označeny jako vanilla knihovny .NET, nikoli F#-směřující knihoven, které používají F# sestaví bez omezení.</span><span class="sxs-lookup"><span data-stu-id="c4899-346">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="c4899-347">Navrhování vanilla knihovny .NET znamená, že znáte a jsou idiomatickou API, konzistentní se zbytkem rozhraní .NET Framework poskytuje minimalizací použití F#-konkrétní konstrukce ve veřejném rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c4899-347">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="c4899-348">Pravidla jsou vysvětlené v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="c4899-348">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="c4899-349">Navrhování Namespace a typ (pro knihovny pro použití v jiných jazycích rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="c4899-349">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="c4899-350">Použít zásady vytváření názvů .NET pro veřejné rozhraní API součásti</span><span class="sxs-lookup"><span data-stu-id="c4899-350">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="c4899-351">Věnujte zvláštní pozornost použití zkrácené názvy a pokyny .NET malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="c4899-351">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="c4899-352">Použijte obory názvů, typy a členy jako primární organizační struktury komponent</span><span class="sxs-lookup"><span data-stu-id="c4899-352">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="c4899-353">Všechny soubory, které obsahují veřejná funkce by měl začínat `namespace` deklaraci a jenom veřejně přístupných entity v oborech názvů by měl být typy.</span><span class="sxs-lookup"><span data-stu-id="c4899-353">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="c4899-354">Nepoužívejte F# moduly.</span><span class="sxs-lookup"><span data-stu-id="c4899-354">Do not use F# modules.</span></span>

<span data-ttu-id="c4899-355">Použijte neveřejné moduly pro uložení implementační kód, typy nástrojů a funkcí nástroje.</span><span class="sxs-lookup"><span data-stu-id="c4899-355">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="c4899-356">Statické typy by měly být upřednostňované nad modulů, protože umožňují pro budoucí vývoj rozhraní API použít přetížení a dalších konceptech rozhraní .NET API návrhu, které se nedá použít v F# moduly.</span><span class="sxs-lookup"><span data-stu-id="c4899-356">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="c4899-357">Například místo následující veřejné rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="c4899-357">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="c4899-358">Zvažte místo toho:</span><span class="sxs-lookup"><span data-stu-id="c4899-358">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="c4899-359">Použití F# typy záznamů v vanilla rozhraní API pro .NET, pokud nebude vyvíjí návrhu typy</span><span class="sxs-lookup"><span data-stu-id="c4899-359">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="c4899-360">F#typy záznamů se kompilují do jednoduchého třída rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c4899-360">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="c4899-361">Toto jsou vhodné pro některé jednoduché a stabilní typy v rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c4899-361">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="c4899-362">Měli byste zvážit použití `[<NoEquality>]` a `[<NoComparison>]` atributů, které mají potlačit automatické generování rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4899-362">You should consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="c4899-363">Také Vyhněte se použití pole proměnlivé záznam v vanilla rozhraní .NET API jako tyto zpřístupňuje veřejné pole.</span><span class="sxs-lookup"><span data-stu-id="c4899-363">Also avoid using mutable record fields in vanilla .NET APIs as these exposes a public field.</span></span> <span data-ttu-id="c4899-364">Vždy zvažte, zda by třída poskytují pružnější možnosti pro budoucí vývoj rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c4899-364">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="c4899-365">Například následující F# kód poskytuje veřejné rozhraní API C# příjemce:</span><span class="sxs-lookup"><span data-stu-id="c4899-365">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="c4899-366">F#:</span><span class="sxs-lookup"><span data-stu-id="c4899-366">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="c4899-367">C#:</span><span class="sxs-lookup"><span data-stu-id="c4899-367">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="c4899-368">Skrýt reprezentace F# sjednocovacím typům v vanilla rozhraní API pro .NET</span><span class="sxs-lookup"><span data-stu-id="c4899-368">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="c4899-369">F#typy sjednocení nejsou používány často přes hranice součástí to i v případě F#- na -F# psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="c4899-369">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="c4899-370">Jsou zařízení s vynikající implementaci při použití interně v rámci komponenty a knihovny.</span><span class="sxs-lookup"><span data-stu-id="c4899-370">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="c4899-371">Při navrhování vanilla rozhraní API .NET, vezměte v úvahu skrytí reprezentací typu union s použitím privátní prohlášení nebo soubor s podpisem.</span><span class="sxs-lookup"><span data-stu-id="c4899-371">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="c4899-372">Může také rozšířit typy, které používají reprezentaci typu union s členy interně k poskytování požadované. NET přístupem k rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c4899-372">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="c4899-373">Návrh grafického uživatelského rozhraní a další komponenty pomocí návrhové vzory architektury</span><span class="sxs-lookup"><span data-stu-id="c4899-373">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="c4899-374">K dispozici mnoho různých rozhraní v rámci .NET, jako je ASP.NET, WinForms a WPF.</span><span class="sxs-lookup"><span data-stu-id="c4899-374">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="c4899-375">Konvence pojmenování a návrh pro každý by měl použít, pokud navrhujete komponenty pro použití v tyto architektury.</span><span class="sxs-lookup"><span data-stu-id="c4899-375">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="c4899-376">Například pro WPF programování, použijte WPF vzory návrhu pro třídy, kterou navrhujete.</span><span class="sxs-lookup"><span data-stu-id="c4899-376">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="c4899-377">Pro modely v programování uživatelské rozhraní, použijte vzorů návrhu, jako je například události a kolekcí založených na oznámení, jako jsou ty uvedené v <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="c4899-377">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="c4899-378">Návrh objektů a členů (pro knihovny pro použití v jiných jazycích rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="c4899-378">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="c4899-379">Vystavení události .NET pomocí clievent – atribut</span><span class="sxs-lookup"><span data-stu-id="c4899-379">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="c4899-380">Vytvořit `DelegateEvent` s konkrétní .NET typ, který přebírá objekt delegáta a `EventArgs` (spíše než výjimku `Event`, který právě používá `FSharpHandler` typ ve výchozím nastavení) tak, aby se události publikují známé způsobem, který jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c4899-380">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

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

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a><span data-ttu-id="c4899-381">Vystavení asynchronních operací jako metody, které vracejí úlohy .NET</span><span class="sxs-lookup"><span data-stu-id="c4899-381">Expose asynchronous operations as methods which return .NET tasks</span></span>

<span data-ttu-id="c4899-382">Úkoly se používají v .NET představující aktivní asynchronní výpočty.</span><span class="sxs-lookup"><span data-stu-id="c4899-382">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="c4899-383">Úlohy jsou obecně menší složení než F# `Async<T>` objekty, protože představují "již provádění" úkoly a nemůže skládat dohromady způsoby, které provádí paralelní složení nebo které skrýt šíření zrušení signály a ostatní kontextové parametry.</span><span class="sxs-lookup"><span data-stu-id="c4899-383">Tasks are in general less compositional than F# `Async<T>` objects, since they represent “already executing” tasks and can’t be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="c4899-384">Bez ohledu na to, jsou metody, které vracejí úlohy standardní reprezentace asynchronní programování v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c4899-384">However, despite this, methods which return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="c4899-385">Často budete také chtít přijmout explicitní rušícího tokenu:</span><span class="sxs-lookup"><span data-stu-id="c4899-385">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="c4899-386">Použití .NET typy delegátů namísto F# funkce typy</span><span class="sxs-lookup"><span data-stu-id="c4899-386">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="c4899-387">Tady "F# funkce typy" znamená "šipka" typy, jako jsou `int -> int`.</span><span class="sxs-lookup"><span data-stu-id="c4899-387">Here “F# function types” mean “arrow” types like `int -> int`.</span></span>

<span data-ttu-id="c4899-388">Namísto toto:</span><span class="sxs-lookup"><span data-stu-id="c4899-388">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="c4899-389">postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="c4899-389">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="c4899-390">F# Typ funkce se zobrazí jako `class FSharpFunc<T,U>` do jiných jazyků .NET a je méně vhodná pro jazykové funkce a nástroje, které rozumí typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="c4899-390">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understand delegate types.</span></span> <span data-ttu-id="c4899-391">Při vytváření vyššího řádu metoda cílí na rozhraní .NET Framework 3.5 nebo vyšší, `System.Func` a `System.Action` Delegáti jsou správné rozhraní API pro publikování a umožňuje vývojářům .NET způsobem bezproblémové využití těchto rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c4899-391">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="c4899-392">(Při cílení na rozhraní .NET Framework 2.0, jsou omezeny více typy definované v systému delegáta; zvažte použití delegáta předdefinované typy, jako `System.Converter<T,U>` nebo definování konkrétního delegáta typu.)</span><span class="sxs-lookup"><span data-stu-id="c4899-392">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="c4899-393">Na druhou stranu, nejsou přirozené pro delegáty rozhraní .NET F#-směřující knihovny (naleznete v další části F#-směřující knihovny).</span><span class="sxs-lookup"><span data-stu-id="c4899-393">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="c4899-394">V důsledku toho je běžné strategie implementace při vývoji vyššího řádu metody pro vanilla knihovny .NET pro vytváření všech na implementaci pomocí F# funkce typů a pak vytvořte veřejné rozhraní API pomocí delegátů jako adaptační vrstva dynamického zajišťování imitovaná skutečné F#implementace.</span><span class="sxs-lookup"><span data-stu-id="c4899-394">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="c4899-395">Použití vzoru TryGetValue místo vrácení F# hodnot a dáváte přednost přetížení metody k pořízení F# možnost hodnoty jako argumenty</span><span class="sxs-lookup"><span data-stu-id="c4899-395">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="c4899-396">Obecné vzory pro použití F# typ možnosti v rozhraní API jsou lepší implementované v vanilla návrh rozhraní API .NET pomocí rozhraní .NET standard techniky.</span><span class="sxs-lookup"><span data-stu-id="c4899-396">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="c4899-397">Místo vrácení F# hodnotu možnosti, zvažte použití návratový typ bool plus výstupní parametr jako vzor "TryGetValue".</span><span class="sxs-lookup"><span data-stu-id="c4899-397">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="c4899-398">A místo pořízení F# možnost hodnoty jako parametry, zvažte použití metody přetížení nebo volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="c4899-398">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

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

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="c4899-399">Použití rozhraní .NET kolekci typů IEnumerable\<T\> a IDictionary\<klíč, hodnota\> pro parametry a návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="c4899-399">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="c4899-400">Vyhněte se použití konkrétní kolekci typů jako je například pole .NET `T[]`, F# typy `list<T>`, `Map<Key,Value>` a `Set<T>`, a typy, jako konkrétní kolekci .NET `Dictionary<Key,Value>`.</span><span class="sxs-lookup"><span data-stu-id="c4899-400">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="c4899-401">Pokyny pro návrh knihovny .NET mají dobrou Rady týkající se použití různé typy kolekcí, jako je `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="c4899-401">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="c4899-402">Některé použití polí (`T[]`) přijatelná v některých případech z důvodů výkonu.</span><span class="sxs-lookup"><span data-stu-id="c4899-402">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="c4899-403">Všimněte si, že zejména `seq<T>` je jenom F# alias pro `IEnumerable<T>`, a proto je sekvence často odpovídající typ pro vanilla rozhraní .NET API.</span><span class="sxs-lookup"><span data-stu-id="c4899-403">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="c4899-404">Místo F# uvádí:</span><span class="sxs-lookup"><span data-stu-id="c4899-404">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="c4899-405">Použití F# pořadí:</span><span class="sxs-lookup"><span data-stu-id="c4899-405">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="c4899-406">Použijte typ jednotky jako pouze vstupní typ metody k definici metody argumentu nula, nebo jako jediná návratový typ pro definování metody vracející hodnotu void</span><span class="sxs-lookup"><span data-stu-id="c4899-406">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="c4899-407">Vyhněte se dalších možnostech použití typu jednotky.</span><span class="sxs-lookup"><span data-stu-id="c4899-407">Avoid other uses of the unit type.</span></span> <span data-ttu-id="c4899-408">Toto jsou dobré:</span><span class="sxs-lookup"><span data-stu-id="c4899-408">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="c4899-409">Toto je chybný:</span><span class="sxs-lookup"><span data-stu-id="c4899-409">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="c4899-410">Kontrola hodnot null na hranicích vanilla rozhraní .NET API</span><span class="sxs-lookup"><span data-stu-id="c4899-410">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="c4899-411">F#implementace kódu obvykle má menší počet hodnot null, z důvodu neměnné návrhových postupů a omezení použití literály s hodnotou null pro F# typy.</span><span class="sxs-lookup"><span data-stu-id="c4899-411">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="c4899-412">Jinými jazyky rozhraní .NET často použít null jako hodnotu mnohem častěji.</span><span class="sxs-lookup"><span data-stu-id="c4899-412">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="c4899-413">Z tohoto důvodu F# kód, který vystavuje vanilla rozhraní .NET API by měl Zkontrolujte parametry pro hodnotu null na hranici rozhraní API a zabránit toku hlouběji do těchto hodnot F# implementační kód.</span><span class="sxs-lookup"><span data-stu-id="c4899-413">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="c4899-414">`isNull` Funkce nebo porovnávání vzorů `null` vzor lze použít.</span><span class="sxs-lookup"><span data-stu-id="c4899-414">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="c4899-415">Nepoužívejte řazené kolekce členů jako návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="c4899-415">Avoid using tuples as return values</span></span>

<span data-ttu-id="c4899-416">Místo toho raději vracející typ s názvem držením agregovaná data, nebo použití výstupním parametrů vrátit více hodnot.</span><span class="sxs-lookup"><span data-stu-id="c4899-416">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="c4899-417">I když existují řazených kolekcí členů a strukturovaných řazených kolekcí členů v rozhraní .NET (včetně C# – jazyková podpora strukturovaných řazených kolekcí členů), se nejčastěji není poskytují ideální a očekávané rozhraní API pro vývojáře na platformě .NET.</span><span class="sxs-lookup"><span data-stu-id="c4899-417">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="c4899-418">Nepoužívejte curryfikace parametrů</span><span class="sxs-lookup"><span data-stu-id="c4899-418">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="c4899-419">Místo toho použijte .NET konvence volání `Method(arg1,arg2,…,argN)`.</span><span class="sxs-lookup"><span data-stu-id="c4899-419">Instead, use .NET calling conventions `Method(arg1,arg2,…,argN)`.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="c4899-420">Tip: Pokud vytváříte knihovny pro použití v kterémkoli jazyce platformy .NET, pak náhradu ve skutečnosti je některé experimentální C# a programování a zkontrolujte, že knihoven "chování přímo" z těchto jazyků Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c4899-420">Tip: If you’re designing libraries for use from any .NET language, then there’s no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="c4899-421">Nástroje, jako je .NET Reflector a prohlížeče objektů služby Visual Studio můžete použít také k zajištění, že knihovny a jejich dokumentaci zobrazují podle očekávání pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="c4899-421">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="c4899-422">Příloha</span><span class="sxs-lookup"><span data-stu-id="c4899-422">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="c4899-423">Příklad návrhu začátku do konce F# kód pro použití jinými jazyky rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="c4899-423">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="c4899-424">Vezměte v úvahu následující třídy:</span><span class="sxs-lookup"><span data-stu-id="c4899-424">Consider the following class:</span></span>

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

<span data-ttu-id="c4899-425">Odvozené F# typ této třídy je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c4899-425">The inferred F# type of this class is as follows:</span></span>

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

<span data-ttu-id="c4899-426">Pojďme se podívat na to, jak to F# typu se zobrazí na programátorovi použít jiný jazyk .NET.</span><span class="sxs-lookup"><span data-stu-id="c4899-426">Let’s take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="c4899-427">Přibližná jazyka C# "podpis" je například následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c4899-427">For example, the approximate C# “signature” is as follows:</span></span>

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

<span data-ttu-id="c4899-428">Existují některé důležité body, které Všimněte si, jak F# představuje vytvoří tady.</span><span class="sxs-lookup"><span data-stu-id="c4899-428">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="c4899-429">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c4899-429">For example:</span></span>

* <span data-ttu-id="c4899-430">Byla zachována metadat – například názvy argumentů.</span><span class="sxs-lookup"><span data-stu-id="c4899-430">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="c4899-431">F#metody, které přebírají dva argumenty, které se stanou C# metodám, které přebírají dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="c4899-431">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="c4899-432">Funkce a seznamy budou odkazy na odpovídající typy v F# knihovny.</span><span class="sxs-lookup"><span data-stu-id="c4899-432">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="c4899-433">Následující kód ukazuje, jak upravit tento kód vzít v úvahu Tyhle věci.</span><span class="sxs-lookup"><span data-stu-id="c4899-433">The following code shows how to adjust this code to take these things into account.</span></span>

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

<span data-ttu-id="c4899-434">Odvozené F# typ kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="c4899-434">The inferred F# type of the code is as follows:</span></span>

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

<span data-ttu-id="c4899-435">Signatura jazyka C# je teď následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c4899-435">The C# signature is now as follows:</span></span>

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

<span data-ttu-id="c4899-436">Tyto opravy provedli připravili k použití tohoto typu, jako součást vanilla knihovny .NET jsou následující:</span><span class="sxs-lookup"><span data-stu-id="c4899-436">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="c4899-437">Upravit několik názvů: `Point1`, `n`, `l`, a `f` začal být `RadialPoint`, `count`, `factor`, a `transform`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c4899-437">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="c4899-438">Používá typ vrácené hodnoty `seq<RadialPoint>` místo `RadialPoint list` změnou seznamu pomocí konstrukce `[ ... ]` pořadí konstrukce pomocí `IEnumerable<RadialPoint>`.</span><span class="sxs-lookup"><span data-stu-id="c4899-438">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="c4899-439">Používá typ delegáta .NET `System.Func` místo F# typ funkce.</span><span class="sxs-lookup"><span data-stu-id="c4899-439">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="c4899-440">Díky tomu je mnohem nicer využívat v kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="c4899-440">This makes it far nicer to consume in C# code.</span></span>
