---
title: 'Pokyny pro návrh součást F #'
description: 'Přečtěte si pokyny pro tvorbu F # součásti určené pro používání jiných volající.'
ms.date: 05/14/2018
ms.openlocfilehash: 7e71710b1bc2fe3e8d7a5a091513a1432650dc04
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="00ac5-103">Pokyny pro návrh součást F #</span><span class="sxs-lookup"><span data-stu-id="00ac5-103">F# component design guidelines</span></span>

<span data-ttu-id="00ac5-104">Tento dokument je sada pokynů pro návrh součásti pro F # programování, podle F # součást pokynů pro návrh, v14, Microsoft Research a [jinou verzi](https://fsharp.org/specs/component-design-guidelines/) původně kurátorované a udržované pomocí Foundation softwaru F #.</span><span class="sxs-lookup"><span data-stu-id="00ac5-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and [another version](https://fsharp.org/specs/component-design-guidelines/) originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="00ac5-105">Tento dokument předpokládá, že jste se seznámili s F # – programování.</span><span class="sxs-lookup"><span data-stu-id="00ac5-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="00ac5-106">Mnoho díky komunity F # pro své příspěvky a užitečné zpětnou vazbu na různé verze tohoto průvodce.</span><span class="sxs-lookup"><span data-stu-id="00ac5-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="00ac5-107">Přehled</span><span class="sxs-lookup"><span data-stu-id="00ac5-107">Overview</span></span>

<span data-ttu-id="00ac5-108">Tento dokument vypadá na některé problémy, týkající se návrhu součást F # a kódování.</span><span class="sxs-lookup"><span data-stu-id="00ac5-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="00ac5-109">Součást může zahrnovat následující:</span><span class="sxs-lookup"><span data-stu-id="00ac5-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="00ac5-110">Vrstvy v projektu F #, který má externí uživatelé v rámci daného projektu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="00ac5-111">Knihovna určená pro používání F # – kód napříč hranicemi sestavení.</span><span class="sxs-lookup"><span data-stu-id="00ac5-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="00ac5-112">Knihovna určená pro používání kterémkoli jazyce platformy .NET napříč hranicemi sestavení.</span><span class="sxs-lookup"><span data-stu-id="00ac5-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="00ac5-113">Knihovnu určených pro distribuci přes úložiště balíčků, jako například [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="00ac5-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="00ac5-114">Postupujte podle technik popsaných v tomto článku [pět principů dobrý F # – kód](index.md#five-principles-of-good-f-code)a proto využívat oba funkční a objekt programování podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="00ac5-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="00ac5-115">Bez ohledu na to metodika součásti a knihovny návrháře otočená řadu praktických a prosaic problémů při pokusu vytvořit rozhraní API, které je snadno použitelný pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="00ac5-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="00ac5-116">Odepření aplikaci [pokynů pro návrh knihovny .NET](../../standard/design-guidelines/index.md) bude řídit k vytvoření konzistentního sadu rozhraní API, která jsou příjemný využívat.</span><span class="sxs-lookup"><span data-stu-id="00ac5-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="00ac5-117">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="00ac5-117">General guidelines</span></span>

<span data-ttu-id="00ac5-118">Existuje několik universal pokyny, které platí pro F # knihovny, bez ohledu na to, cílová pro knihovnu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="00ac5-119">Další pokyny pro návrh knihovny .NET</span><span class="sxs-lookup"><span data-stu-id="00ac5-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="00ac5-120">Bez ohledu na druh F # kódování vedete, je vhodné mít praktické znalosti [pokynů pro návrh knihovny .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="00ac5-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="00ac5-121">Většina jiných F # .NET programátorům bude se seznamte s těmito pokyny a očekávat kód .NET tak, aby odpovídala je.</span><span class="sxs-lookup"><span data-stu-id="00ac5-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="00ac5-122">Pokyny pro návrh knihovny .NET obsahují obecné pokyny týkající se pojmenování, navrhování třídy a rozhraní, návrh člen (vlastnosti, metody, události atd.) a další a jsou užitečné první bod odkazu pro celou řadu pokyny k návrhu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="00ac5-123">Přidání dokumentační komentáře XML do vašeho kódu</span><span class="sxs-lookup"><span data-stu-id="00ac5-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="00ac5-124">Dokumentace XML na veřejné rozhraní API Ujistěte se, že se uživatelé dostanou skvělé funkce Intellisense a Quickinfo při používání tyto typy a členy a povolit vytváření dokumentace souborů pro knihovnu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-124">XML documentation on public APIs ensure that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="00ac5-125">Najdete v článku [dokumentace XML](../language-reference/xml-documentation.md) o různé značky xml, které lze použít pro další značek v rámci xmldoc komentáře.</span><span class="sxs-lookup"><span data-stu-id="00ac5-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

<span data-ttu-id="00ac5-126">Můžete použít buď krátkých úseků XML – komentáře (`/// comment`), nebo standardní komentáře XML (`///<summary>comment</summary>`).</span><span class="sxs-lookup"><span data-stu-id="00ac5-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="00ac5-127">Zvažte použití explicitního signatury (.fsi) pro stabilní knihovny a součást rozhraní API</span><span class="sxs-lookup"><span data-stu-id="00ac5-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="00ac5-128">Pomocí souborů explicitní podpisy knihovny F # obsahuje stručné shrnutí veřejné rozhraní API, které oba pomáhá zajistit, že jste vědět úplné veřejný prostor knihovny, stejně jako poskytuje čistou oddělení mezi veřejné dokumentaci a interní Podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="00ac5-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which both helps to ensure that you know the full public surface of your library, as well as provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="00ac5-129">Všimněte si, že soubory podpisu přidat třecí změnou veřejné rozhraní API, tím, že změny v rámci implementace i podpis souborů.</span><span class="sxs-lookup"><span data-stu-id="00ac5-129">Note that signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="00ac5-130">V důsledku toho signatury obvykle pouze třeba zavést když má stát zpevněné rozhraní API a už očekává se významně změní.</span><span class="sxs-lookup"><span data-stu-id="00ac5-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="00ac5-131">Vždy použijte osvědčené postupy pro používání řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="00ac5-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="00ac5-132">Postupujte podle [osvědčené postupy pro používání řetězců v .NET](../../standard/base-types/best-practices-strings.md) pokyny.</span><span class="sxs-lookup"><span data-stu-id="00ac5-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="00ac5-133">Konkrétně vždy explicitně stavu *kulturního záměr* v převodu a porovnávání řetězců (v případě potřeby).</span><span class="sxs-lookup"><span data-stu-id="00ac5-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="00ac5-134">Pokyny pro F #-facing knihovny</span><span class="sxs-lookup"><span data-stu-id="00ac5-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="00ac5-135">Tato část nabízí doporučení pro vývoj veřejné F #-facing knihovny; To znamená, knihovny vystavení veřejná rozhraní API, které jsou určené pro F # vývojáři.</span><span class="sxs-lookup"><span data-stu-id="00ac5-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="00ac5-136">Existuje mnoho různých z knihovny návrhu doporučení platí konkrétně pro F #.</span><span class="sxs-lookup"><span data-stu-id="00ac5-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="00ac5-137">Chybí konkrétní doporučení, které následují jsou pokynů pro návrh knihovny .NET záložní pokyny.</span><span class="sxs-lookup"><span data-stu-id="00ac5-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="00ac5-138">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="00ac5-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="00ac5-139">Použít konvence pojmenování a velkých písmen v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="00ac5-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="00ac5-140">V následující tabulce dodržovat konvence pojmenování a velkých písmen v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="00ac5-141">Existují malé dodatky zahrnout také konstrukce jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="00ac5-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="00ac5-142">Konstrukce</span><span class="sxs-lookup"><span data-stu-id="00ac5-142">Construct</span></span> | <span data-ttu-id="00ac5-143">Případ</span><span class="sxs-lookup"><span data-stu-id="00ac5-143">Case</span></span> | <span data-ttu-id="00ac5-144">Část</span><span class="sxs-lookup"><span data-stu-id="00ac5-144">Part</span></span> | <span data-ttu-id="00ac5-145">Příklady</span><span class="sxs-lookup"><span data-stu-id="00ac5-145">Examples</span></span> | <span data-ttu-id="00ac5-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00ac5-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="00ac5-147">Konkrétní typy</span><span class="sxs-lookup"><span data-stu-id="00ac5-147">Concrete types</span></span> | <span data-ttu-id="00ac5-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-148">PascalCase</span></span> | <span data-ttu-id="00ac5-149">Podstatné jméno / tvary přídavných jmen</span><span class="sxs-lookup"><span data-stu-id="00ac5-149">Noun/ adjective</span></span> | <span data-ttu-id="00ac5-150">Seznam, Double, komplexní</span><span class="sxs-lookup"><span data-stu-id="00ac5-150">List, Double, Complex</span></span> | <span data-ttu-id="00ac5-151">Konkrétní typy jsou struktury, třídy, výčty, delegáti, záznamy a sjednocení.</span><span class="sxs-lookup"><span data-stu-id="00ac5-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="00ac5-152">Názvy typů si tradičně malá písmena v OCaml, F # přijal schéma pojmenování .NET pro typy.</span><span class="sxs-lookup"><span data-stu-id="00ac5-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="00ac5-153">knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="00ac5-153">DLLs</span></span>           | <span data-ttu-id="00ac5-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-154">PascalCase</span></span> |                 | <span data-ttu-id="00ac5-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="00ac5-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="00ac5-156">Union – značky</span><span class="sxs-lookup"><span data-stu-id="00ac5-156">Union tags</span></span>     | <span data-ttu-id="00ac5-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-157">PascalCase</span></span> | <span data-ttu-id="00ac5-158">podstatné jméno</span><span class="sxs-lookup"><span data-stu-id="00ac5-158">Noun</span></span> | <span data-ttu-id="00ac5-159">Některé, přidat, úspěch</span><span class="sxs-lookup"><span data-stu-id="00ac5-159">Some, Add, Success</span></span> | <span data-ttu-id="00ac5-160">Nepoužívejte předponu veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="00ac5-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="00ac5-161">Volitelně použijte předponu při interní, například ", zadejte týmy = TAlpha</span><span class="sxs-lookup"><span data-stu-id="00ac5-161">Optionally use a prefix when internal, such as \`\`\`type Teams = TAlpha</span></span> | <span data-ttu-id="00ac5-162">TBeta</span><span class="sxs-lookup"><span data-stu-id="00ac5-162">TBeta</span></span> | <span data-ttu-id="00ac5-163">TDelta. ".</span><span class="sxs-lookup"><span data-stu-id="00ac5-163">TDelta.\`\`\`</span></span> |
| <span data-ttu-id="00ac5-164">Událost</span><span class="sxs-lookup"><span data-stu-id="00ac5-164">Event</span></span>          | <span data-ttu-id="00ac5-165">PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-165">PascalCase</span></span> | <span data-ttu-id="00ac5-166">Příkaz</span><span class="sxs-lookup"><span data-stu-id="00ac5-166">Verb</span></span> | <span data-ttu-id="00ac5-167">ValueChanged / ValueChanging</span><span class="sxs-lookup"><span data-stu-id="00ac5-167">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="00ac5-168">Výjimky</span><span class="sxs-lookup"><span data-stu-id="00ac5-168">Exceptions</span></span>     | <span data-ttu-id="00ac5-169">PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-169">PascalCase</span></span> |      | <span data-ttu-id="00ac5-170">Výjimku WebException</span><span class="sxs-lookup"><span data-stu-id="00ac5-170">WebException</span></span> | <span data-ttu-id="00ac5-171">Název musí končit "Výjimky".</span><span class="sxs-lookup"><span data-stu-id="00ac5-171">Name should end with “Exception”.</span></span> |
| <span data-ttu-id="00ac5-172">Pole</span><span class="sxs-lookup"><span data-stu-id="00ac5-172">Field</span></span>          | <span data-ttu-id="00ac5-173">PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-173">PascalCase</span></span> | <span data-ttu-id="00ac5-174">podstatné jméno</span><span class="sxs-lookup"><span data-stu-id="00ac5-174">Noun</span></span> | <span data-ttu-id="00ac5-175">CurrentName</span><span class="sxs-lookup"><span data-stu-id="00ac5-175">CurrentName</span></span>  | |
| <span data-ttu-id="00ac5-176">Typy rozhraní</span><span class="sxs-lookup"><span data-stu-id="00ac5-176">Interface types</span></span> |  <span data-ttu-id="00ac5-177">PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-177">PascalCase</span></span> | <span data-ttu-id="00ac5-178">Podstatné jméno / tvary přídavných jmen</span><span class="sxs-lookup"><span data-stu-id="00ac5-178">Noun/ adjective</span></span> | <span data-ttu-id="00ac5-179">Rozhraní IDisposable</span><span class="sxs-lookup"><span data-stu-id="00ac5-179">IDisposable</span></span> | <span data-ttu-id="00ac5-180">Název by měla začínat znakem "I".</span><span class="sxs-lookup"><span data-stu-id="00ac5-180">Name should start with “I”.</span></span> |
| <span data-ttu-id="00ac5-181">Metoda</span><span class="sxs-lookup"><span data-stu-id="00ac5-181">Method</span></span> |  <span data-ttu-id="00ac5-182">PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-182">PascalCase</span></span> |  <span data-ttu-id="00ac5-183">Příkaz</span><span class="sxs-lookup"><span data-stu-id="00ac5-183">Verb</span></span> | <span data-ttu-id="00ac5-184">ToString</span><span class="sxs-lookup"><span data-stu-id="00ac5-184">ToString</span></span> | |
| <span data-ttu-id="00ac5-185">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="00ac5-185">Namespace</span></span> | <span data-ttu-id="00ac5-186">PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-186">PascalCase</span></span> | | <span data-ttu-id="00ac5-187">Microsoft.FSharp.Core</span><span class="sxs-lookup"><span data-stu-id="00ac5-187">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="00ac5-188">Obecně používat `<Organization>.<Technology>[.<Subnamespace>]`, ale vyřadit organizace, pokud se tato technologie je nezávislá organizace.</span><span class="sxs-lookup"><span data-stu-id="00ac5-188">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="00ac5-189">Parametry</span><span class="sxs-lookup"><span data-stu-id="00ac5-189">Parameters</span></span> | <span data-ttu-id="00ac5-190">camelCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-190">camelCase</span></span> | <span data-ttu-id="00ac5-191">podstatné jméno</span><span class="sxs-lookup"><span data-stu-id="00ac5-191">Noun</span></span> |  <span data-ttu-id="00ac5-192">typeName, transformace, rozsahu</span><span class="sxs-lookup"><span data-stu-id="00ac5-192">typeName, transform, range</span></span> | |
| <span data-ttu-id="00ac5-193">let – hodnoty (interní)</span><span class="sxs-lookup"><span data-stu-id="00ac5-193">let values (internal)</span></span> | <span data-ttu-id="00ac5-194">camelCase nebo PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-194">camelCase or PascalCase</span></span> | <span data-ttu-id="00ac5-195">Podstatné jméno / operaci</span><span class="sxs-lookup"><span data-stu-id="00ac5-195">Noun/ verb</span></span> |  <span data-ttu-id="00ac5-196">getValue myTable</span><span class="sxs-lookup"><span data-stu-id="00ac5-196">getValue, myTable</span></span> |
| <span data-ttu-id="00ac5-197">let – hodnoty (externí)</span><span class="sxs-lookup"><span data-stu-id="00ac5-197">let values (external)</span></span> | <span data-ttu-id="00ac5-198">camelCase nebo PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-198">camelCase or PascalCase</span></span> | <span data-ttu-id="00ac5-199">Podstatné jméno/operaci</span><span class="sxs-lookup"><span data-stu-id="00ac5-199">Noun/verb</span></span>  | <span data-ttu-id="00ac5-200">List.map –, Dates.Today</span><span class="sxs-lookup"><span data-stu-id="00ac5-200">List.map, Dates.Today</span></span> | <span data-ttu-id="00ac5-201">vázané na umožňují hodnoty jsou často při veřejné následující vzory návrhu tradiční funkční.</span><span class="sxs-lookup"><span data-stu-id="00ac5-201">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="00ac5-202">Obecně použití však PascalCase identifikátor lze z jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-202">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="00ac5-203">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="00ac5-203">Property</span></span>  | <span data-ttu-id="00ac5-204">PascalCase</span><span class="sxs-lookup"><span data-stu-id="00ac5-204">PascalCase</span></span>  | <span data-ttu-id="00ac5-205">Podstatné jméno / tvary přídavných jmen</span><span class="sxs-lookup"><span data-stu-id="00ac5-205">Noun/ adjective</span></span>  | <span data-ttu-id="00ac5-206">IsEndOfFile, barva pozadí</span><span class="sxs-lookup"><span data-stu-id="00ac5-206">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="00ac5-207">Logická hodnota vlastnosti obecně použití je a a musí být kladná, stejně jako IsEndOfFile, není IsNotEndOfFile.</span><span class="sxs-lookup"><span data-stu-id="00ac5-207">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="00ac5-208">Vyhněte se zkratky</span><span class="sxs-lookup"><span data-stu-id="00ac5-208">Avoid abbreviations</span></span>

<span data-ttu-id="00ac5-209">Pokyny pro rozhraní .NET omezit používání zkratky (například "použít `OnButtonClick` místo `OnBtnClick`").</span><span class="sxs-lookup"><span data-stu-id="00ac5-209">The .NET guidelines discourage the use of abbreviations (for example, “use `OnButtonClick` rather than `OnBtnClick`”).</span></span> <span data-ttu-id="00ac5-210">Běžné zkratky, jako například `Async` pro "Asynchronního", jsou tolerovat.</span><span class="sxs-lookup"><span data-stu-id="00ac5-210">Common abbreviations, such as `Async` for “Asynchronous”, are tolerated.</span></span> <span data-ttu-id="00ac5-211">Tyto obecné zásady se někdy ignoruje při funkční programování; například `List.iter` používá zkratkou pro "iteraci".</span><span class="sxs-lookup"><span data-stu-id="00ac5-211">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for “iterate”.</span></span> <span data-ttu-id="00ac5-212">Z tohoto důvodu pomocí zkratky obvykle tolerovat ve větší míře v jazyce F #-na-F # – programování, ale stále obecně je nutno v návrhu veřejné součásti.</span><span class="sxs-lookup"><span data-stu-id="00ac5-212">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="00ac5-213">Vyhněte se velká a malá písmena kolize názvů</span><span class="sxs-lookup"><span data-stu-id="00ac5-213">Avoid casing name collisions</span></span>

<span data-ttu-id="00ac5-214">Pokyny pro rozhraní .NET Řekněme, že velká a malá písmena samostatně nelze použít k rozlišení kolize názvů, protože některé jazyky klienta (například Visual Basic) jsou velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="00ac5-214">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="00ac5-215">Použijte režim, kde je to vhodné</span><span class="sxs-lookup"><span data-stu-id="00ac5-215">Use acronyms where appropriate</span></span>

<span data-ttu-id="00ac5-216">Režim například XML nejsou zkratky a jsou široce používaných v knihovny .NET v nezačínající formuláře (Xml).</span><span class="sxs-lookup"><span data-stu-id="00ac5-216">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="00ac5-217">Měli použít pouze známé, široce uznávané režim.</span><span class="sxs-lookup"><span data-stu-id="00ac5-217">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="00ac5-218">Použití PascalCase pro obecný parametr názvy</span><span class="sxs-lookup"><span data-stu-id="00ac5-218">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="00ac5-219">Použít PascalCase pro obecný parametr názvy v veřejná rozhraní API, včetně pro F #-facing knihovny.</span><span class="sxs-lookup"><span data-stu-id="00ac5-219">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="00ac5-220">Konkrétně použít názvy jako `T`, `U`, `T1`, `T2` pro libovolný obecné parametry, když konkrétní názvy smysl, pak pro F # – přístupných knihovny používat názvy jako `Key`, `Value`, `Arg`(ale ne například `TKey`).</span><span class="sxs-lookup"><span data-stu-id="00ac5-220">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="00ac5-221">Použít PascalCase nebo camelCase pro veřejné funkce a hodnoty v modulech F #</span><span class="sxs-lookup"><span data-stu-id="00ac5-221">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="00ac5-222">camelCase se používá pro veřejné funkce, které jsou určeny k použití nekvalifikované (například `invalidArg`) a pro "funkce standardního shromažďování" (například list.map –).</span><span class="sxs-lookup"><span data-stu-id="00ac5-222">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the “standard collection functions” (for example, List.map).</span></span> <span data-ttu-id="00ac5-223">V obou těchto případech názvy funkcí mnohem fungovat stejně jako klíčová slova v jazyce.</span><span class="sxs-lookup"><span data-stu-id="00ac5-223">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="00ac5-224">Objekt, typ a modul návrhu</span><span class="sxs-lookup"><span data-stu-id="00ac5-224">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="00ac5-225">Použití oborů názvů nebo moduly obsahovat typy a modulů</span><span class="sxs-lookup"><span data-stu-id="00ac5-225">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="00ac5-226">Každý soubor F # součásti by měl začínat obráceným deklaraci oboru názvů nebo deklaraci modulu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-226">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="00ac5-227">or</span><span class="sxs-lookup"><span data-stu-id="00ac5-227">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="00ac5-228">Rozdíly mezi použitím modulů a obory názvů pro uspořádání kódu na nejvyšší úrovni jsou následující:</span><span class="sxs-lookup"><span data-stu-id="00ac5-228">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="00ac5-229">Obory názvů může mít rozsah více souborů</span><span class="sxs-lookup"><span data-stu-id="00ac5-229">Namespaces can span multiple files</span></span>
* <span data-ttu-id="00ac5-230">Obory názvů nesmí obsahovat F # funkce, které nejsou v rámci vnitřní modulu</span><span class="sxs-lookup"><span data-stu-id="00ac5-230">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="00ac5-231">Kód pro jakékoli dané modul musí být obsaženy v rámci jednoho souboru</span><span class="sxs-lookup"><span data-stu-id="00ac5-231">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="00ac5-232">Moduly nejvyšší úrovně může obsahovat funkce F # bez nutnosti vnitřní modulu</span><span class="sxs-lookup"><span data-stu-id="00ac5-232">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="00ac5-233">Volba mezi nejvyšší úrovně oboru názvů nebo modul ovlivňuje formuláři zkompilovaný kód a proto ovlivní zobrazení jinými jazyky rozhraní .NET by měl vaše rozhraní API nakonec využijí mimo F # – kód.</span><span class="sxs-lookup"><span data-stu-id="00ac5-233">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="00ac5-234">Použití metod a vlastností pro operace vnitřní pro typy objektů</span><span class="sxs-lookup"><span data-stu-id="00ac5-234">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="00ac5-235">Při práci s objekty, je nejvhodnější zajistit, že použití funkce je implementovaná jako metody a vlastnosti typu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-235">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="00ac5-236">Hromadné funkce pro daný člen nemusí nutně implementaci do tohoto člena, ale musí být použití část této funkce.</span><span class="sxs-lookup"><span data-stu-id="00ac5-236">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="00ac5-237">Použití tříd pro zapouzdření měnitelný stavu</span><span class="sxs-lookup"><span data-stu-id="00ac5-237">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="00ac5-238">V F # to jenom je potřeba udělat kde, není stav již zapouzdřené pomocí jiný jazyk konstrukce, například uzavření, pořadí výraz nebo asynchronní výpočty.</span><span class="sxs-lookup"><span data-stu-id="00ac5-238">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="00ac5-239">Použít rozhraní k seskupení operací souvisejících s</span><span class="sxs-lookup"><span data-stu-id="00ac5-239">Use interfaces to group related operations</span></span>

<span data-ttu-id="00ac5-240">Použijte rozhraní typy, které představují sadu operací.</span><span class="sxs-lookup"><span data-stu-id="00ac5-240">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="00ac5-241">Toto je upřednostňovaný k jiné možnosti, například řazené kolekce členů funkcí nebo záznamy funkcí.</span><span class="sxs-lookup"><span data-stu-id="00ac5-241">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="00ac5-242">V preference na:</span><span class="sxs-lookup"><span data-stu-id="00ac5-242">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

<span data-ttu-id="00ac5-243">Rozhraní jsou prvotřídní koncepty v rozhraní .NET, který můžete použít k dosažení co Functors by za normálních okolností získáte.</span><span class="sxs-lookup"><span data-stu-id="00ac5-243">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="00ac5-244">Kromě toho se můžete použitá ke kódování existenční typy do programu, který nelze záznamy funkcí.</span><span class="sxs-lookup"><span data-stu-id="00ac5-244">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a><span data-ttu-id="00ac5-245">Pomocí modulu do funkce skupin, které jednají na kolekce</span><span class="sxs-lookup"><span data-stu-id="00ac5-245">Use a module to group functions which act on collections</span></span>

<span data-ttu-id="00ac5-246">Při definování typu kolekce, vezměte v úvahu poskytuje standardní sadu operací, jako `CollectionType.map` a `CollectionType.iter`) pro nové typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="00ac5-246">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="00ac5-247">Pokud zahrnete takové modul, postupujte podle standardní zásady vytváření názvů pro funkce v FSharp.Core nalezen.</span><span class="sxs-lookup"><span data-stu-id="00ac5-247">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="00ac5-248">Pomocí modulu do funkcí skupiny pro běžné, kanonické funkce, zejména v matematické a DSL knihovny</span><span class="sxs-lookup"><span data-stu-id="00ac5-248">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="00ac5-249">Například `Microsoft.FSharp.Core.Operators` je automaticky otevřenou kolekci nejvyšší úrovně funkcí (jako je `abs` a `sin`) poskytované FSharp.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="00ac5-249">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="00ac5-250">Podobně knihovnu statistiky mohou zahrnovat modul s funkcí `erf` a `erfc`, kde se tento modul slouží k explicitně nebo automaticky otevřít.</span><span class="sxs-lookup"><span data-stu-id="00ac5-250">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="00ac5-251">Zvažte použití RequireQualifiedAccess a pečlivě použití AutoOpen atributů</span><span class="sxs-lookup"><span data-stu-id="00ac5-251">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="00ac5-252">Přidávání `[<RequireQualifiedAccess>]` atribut na modul označuje, že modul nemusí otevřít a že vyžadují explicitní odkazy na elementy modulu kvalifikovaný přístup.</span><span class="sxs-lookup"><span data-stu-id="00ac5-252">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="00ac5-253">Například `Microsoft.FSharp.Collections.List` modul má tento atribut.</span><span class="sxs-lookup"><span data-stu-id="00ac5-253">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="00ac5-254">To je užitečné, když funkce a hodnoty v modulu mají názvy, které mohou v konfliktu s názvy v dalších modulů.</span><span class="sxs-lookup"><span data-stu-id="00ac5-254">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="00ac5-255">Vyžadování kvalifikovaný přístup může výrazně zvýšit dlouhodobé udržovatelnosti a evolvability knihovny.</span><span class="sxs-lookup"><span data-stu-id="00ac5-255">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="00ac5-256">Přidávání `[<AutoOpen>]` atribut na modul znamená modul se otevře, když je otevřen obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="00ac5-256">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="00ac5-257">`[<AutoOpen>]` Atribut může také použít k sestavení udávajících modul, který se automaticky otevře při odkazování na sestavení.</span><span class="sxs-lookup"><span data-stu-id="00ac5-257">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="00ac5-258">Například knihovnu statistiky **MathsHeaven.Statistics** může obsahovat `module MathsHeaven.Statistics.Operators` obsahující funkce `erf` a `erfc`.</span><span class="sxs-lookup"><span data-stu-id="00ac5-258">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="00ac5-259">Je možné logicky označit tento modul jako `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="00ac5-259">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="00ac5-260">To znamená `open MathsHeaven.Statistics` rovněž otevřete tento modul a převést názvy `erf` a `erfc` do oboru.</span><span class="sxs-lookup"><span data-stu-id="00ac5-260">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="00ac5-261">Použití jiné dobré `[<AutoOpen>]` je pro moduly, který obsahuje rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="00ac5-261">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="00ac5-262">Nadměrné použití z `[<AutoOpen>]` za následek znečištěného obory názvů a atribut by měl použít dát pozor.</span><span class="sxs-lookup"><span data-stu-id="00ac5-262">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="00ac5-263">Pro konkrétní knihovny v konkrétní domény, rozumné využívání `[<AutoOpen>]` může vést k lepší použitelnost.</span><span class="sxs-lookup"><span data-stu-id="00ac5-263">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="00ac5-264">Vezměte v úvahu definování operátor členy na třídy, kde je odpovídající pomocí známých operátorů</span><span class="sxs-lookup"><span data-stu-id="00ac5-264">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="00ac5-265">Třídy se někdy používají pro modelování matematickém konstrukce, jako je například vektory.</span><span class="sxs-lookup"><span data-stu-id="00ac5-265">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="00ac5-266">Pokud má doména modelovaných dobře známé operátory, je definují jako členy do třídy vnitřní je užitečné.</span><span class="sxs-lookup"><span data-stu-id="00ac5-266">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="00ac5-267">V tomto návodu odpovídá obecné pokyny .NET pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="00ac5-267">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="00ac5-268">Však může být v F # kódování jako to umožňuje tyto typy použije ve spojení s F # funkce a metody s omezeními člena, jako je například list.sumby – kromě důležité.</span><span class="sxs-lookup"><span data-stu-id="00ac5-268">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="00ac5-269">Zvažte použití compiledname – k poskytování. NET popisný název pro ostatní příjemce jazyk rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="00ac5-269">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="00ac5-270">V některých případech můžete chtít název něco v jeden styl pro spotřebitele F # (například statický člen v malá písmena, takže se objeví jako by šlo vázané na modulu funkce), ale mají jiný styl pro název, když je přeložen do sestavení.</span><span class="sxs-lookup"><span data-stu-id="00ac5-270">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="00ac5-271">Můžete použít `[<CompiledName>]` atribut zajistit jiný styl pro jiný F # – kód využívání sestavení.</span><span class="sxs-lookup"><span data-stu-id="00ac5-271">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="00ac5-272">Pomocí `[<CompiledName>]`, můžete použít zásady vytváření názvů .NET pro jiný F # spotřebiteli sestavení.</span><span class="sxs-lookup"><span data-stu-id="00ac5-272">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="00ac5-273">Použijte přetížení metody pro členské funkce, pokud Důvodem jsou jednodušší rozhraní API</span><span class="sxs-lookup"><span data-stu-id="00ac5-273">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="00ac5-274">Přetěžování metody je výkonný nástroj pro zjednodušenou rozhraní API, které můžete využít podobné funkce, ale s různými možnostmi nebo argumenty.</span><span class="sxs-lookup"><span data-stu-id="00ac5-274">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="00ac5-275">V jazyce F # je dnes běžné k přetížení na počet argumentů než typy argumentů.</span><span class="sxs-lookup"><span data-stu-id="00ac5-275">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="00ac5-276">Skrýt reprezentace záznam a typy union, pokud tyto typy v návrhu je pravděpodobné, vyvíjí</span><span class="sxs-lookup"><span data-stu-id="00ac5-276">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="00ac5-277">Vyhněte se odhalil konkrétní reprezentace objektů.</span><span class="sxs-lookup"><span data-stu-id="00ac5-277">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="00ac5-278">Například konkrétní reprezentace <xref:System.DateTime> hodnoty není zjištěné při externí, veřejné rozhraní API návrhu knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-278">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="00ac5-279">V době běhu modul Common Language Runtime zná potvrdit implementace, která se použije v průběhu provádění.</span><span class="sxs-lookup"><span data-stu-id="00ac5-279">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="00ac5-280">Ale zkompilovaný kód není sám vyzvedávat závislosti na konkrétní reprezentace.</span><span class="sxs-lookup"><span data-stu-id="00ac5-280">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="00ac5-281">Vyhněte se použití implementace dědičnosti rozšíření</span><span class="sxs-lookup"><span data-stu-id="00ac5-281">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="00ac5-282">V F # je používána zřídka implementace dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="00ac5-282">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="00ac5-283">Kromě toho hierarchie dědičnosti jsou často složitá a obtížná změnit příchod nové požadavky.</span><span class="sxs-lookup"><span data-stu-id="00ac5-283">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="00ac5-284">Implementace dědičnosti stále existuje v jazyce F # pro kompatibilitu a výjimečných případech, kdy je nejlepší řešení problémů, ale alternativní techniky se má hledat v programů F # při návrhu polymorfismus, jako je například implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="00ac5-284">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="00ac5-285">Funkce a člen podpisy</span><span class="sxs-lookup"><span data-stu-id="00ac5-285">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="00ac5-286">Při vrácení malý počet nesouvisejícími více hodnot použijte řazených kolekcí členů pro vrácené hodnoty</span><span class="sxs-lookup"><span data-stu-id="00ac5-286">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="00ac5-287">Tady je dobrým příkladem použití řazené kolekce členů v návratový typ:</span><span class="sxs-lookup"><span data-stu-id="00ac5-287">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="00ac5-288">Návratové typy obsahující mnoho součásti nebo kde komponenty se vztahují k jedné osobní entity, zvažte použití pojmenovaného typu místo řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="00ac5-288">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="00ac5-289">Použití `Async<T>` pro asynchronní programování v F # API hranice</span><span class="sxs-lookup"><span data-stu-id="00ac5-289">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="00ac5-290">Pokud je odpovídající synchronní operace s názvem `Operation` , který vrací `T`, pak by měl být pojmenován asynchronní operace `AsyncOperation` vrátí-li `Async<T>` nebo `OperationAsync` vrátí-li `Task<T>`.</span><span class="sxs-lookup"><span data-stu-id="00ac5-290">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="00ac5-291">Běžně používané typy .NET, které zveřejňují začátek/konec metody, zvažte použití `Async.FromBeginEnd` zápis metody rozšíření jako průčelí za k poskytování F # asynchronní programovací model těchto rozhraní API technologie .NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-291">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="00ac5-292">Výjimky</span><span class="sxs-lookup"><span data-stu-id="00ac5-292">Exceptions</span></span>

<span data-ttu-id="00ac5-293">Výjimky jsou výjimečných v rozhraní .NET; To znamená že nedojde často za běhu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-293">Exceptions are exceptional in .NET; that is, they should not occur frequently at runtime.</span></span> <span data-ttu-id="00ac5-294">Pokud tomu tak je, je cenné informace, které obsahují.</span><span class="sxs-lookup"><span data-stu-id="00ac5-294">When they do, the information they contain is valuable.</span></span> <span data-ttu-id="00ac5-295">Výjimky jsou základní prvotřídní konceptu .NET; proto IT způsobem, které příslušné aplikace výjimky by měla být použity jako součást návrhu rozhraní součásti.</span><span class="sxs-lookup"><span data-stu-id="00ac5-295">Exceptions are a core first class concept of .NET; it hence follows that appropriate application of the Exceptions should be used as part of the design of the interface of a component.</span></span>

#### <a name="follow-the-net-guidelines-for-exceptions"></a><span data-ttu-id="00ac5-296">Postupujte podle pokynů .NET pro výjimky</span><span class="sxs-lookup"><span data-stu-id="00ac5-296">Follow the .NET guidelines for exceptions</span></span>

<span data-ttu-id="00ac5-297">[Pokynů pro návrh knihovny .NET](../../standard/design-guidelines/exceptions.md) poskytnout vynikající Rady ohledně použití výjimek v kontextu všechny .NET – programování.</span><span class="sxs-lookup"><span data-stu-id="00ac5-297">The [.NET Library Design Guidelines](../../standard/design-guidelines/exceptions.md) give excellent advice on the use of exceptions in the context of all .NET programming.</span></span> <span data-ttu-id="00ac5-298">Některé z těchto pokynů jsou následující:</span><span class="sxs-lookup"><span data-stu-id="00ac5-298">Some of these guidelines are as follows:</span></span>

* <span data-ttu-id="00ac5-299">Nepoužívejte výjimky pro normálního toku řízení.</span><span class="sxs-lookup"><span data-stu-id="00ac5-299">Do not use exceptions for normal flow of control.</span></span> <span data-ttu-id="00ac5-300">I když tato technika se často používá v jazycích, jako je například OCaml, jsou náchylné chyb a může být neefektivní na rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-300">Although this technique is often used in languages such as OCaml, it is bug-prone and can be inefficient on .NET.</span></span> <span data-ttu-id="00ac5-301">Místo toho zvažte vrácení `None` hodnota označující selhání, které je běžné nebo se očekává výskyt možnosti.</span><span class="sxs-lookup"><span data-stu-id="00ac5-301">Instead, consider returning a `None` option value to indicate a failure that is a common or expected occurrence.</span></span>

* <span data-ttu-id="00ac5-302">Dokument výjimky vyvolané vaše komponenty pro při volání funkce používána nesprávně.</span><span class="sxs-lookup"><span data-stu-id="00ac5-302">Document exceptions thrown by your components when a function is used incorrectly.</span></span>

* <span data-ttu-id="00ac5-303">Pokud je to možné, využívejte stávající výjimky z oborů názvů systému.</span><span class="sxs-lookup"><span data-stu-id="00ac5-303">Where possible, employ existing exceptions from the System namespaces.</span></span> <span data-ttu-id="00ac5-304">Vyhněte se <xref:System.ApplicationException>, ačkoli.</span><span class="sxs-lookup"><span data-stu-id="00ac5-304">Avoid <xref:System.ApplicationException>, though.</span></span>

* <span data-ttu-id="00ac5-305">Nevyvolá výjimku <xref:System.Exception> když bude řídicí kód uživatele.</span><span class="sxs-lookup"><span data-stu-id="00ac5-305">Do not throw <xref:System.Exception> when it will escape to user code.</span></span> <span data-ttu-id="00ac5-306">To zahrnuje zabraňující použití `failwith`, `failwithf`, které jsou užitečné funkce pro použití ve vytváření skriptů a pro kód ve vývoji, ale měla by být odebrána z knihovny kódu F # považuje vyvolání konkrétnější typ výjimky.</span><span class="sxs-lookup"><span data-stu-id="00ac5-306">This includes avoiding the use of `failwith`, `failwithf`, which are handy functions for use in scripting and for code under development, but should be removed from F# library code in favor of throwing a more specific exception type.</span></span>

* <span data-ttu-id="00ac5-307">Použití `nullArg`, `invalidArg`, a `invalidOp` jako mechanizmus pro throw <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, a <xref:System.InvalidOperationException> při vhodné.</span><span class="sxs-lookup"><span data-stu-id="00ac5-307">Use `nullArg`, `invalidArg`, and `invalidOp` as the mechanism to throw <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, and <xref:System.InvalidOperationException> when appropriate.</span></span>

#### <a name="consider-using-option-values-for-return-types-when-failure-is-not-an-exceptional-scenario"></a><span data-ttu-id="00ac5-308">Vezměte v úvahu při selhání není výjimečných scénář pomocí hodnoty možnosti pro návratové typy</span><span class="sxs-lookup"><span data-stu-id="00ac5-308">Consider using option values for return types when failure is not an exceptional scenario</span></span>

<span data-ttu-id="00ac5-309">Rozhraní .NET přístup k výjimkám je, že by měl být "výjimečných;" To znamená že má vzniknout poměrně málo.</span><span class="sxs-lookup"><span data-stu-id="00ac5-309">The .NET approach to exceptions is that they should be “exceptional”; that is, they should occur relatively infrequently.</span></span> <span data-ttu-id="00ac5-310">Některé operace (například vyhledávání tabulku) však mohou selhat často.</span><span class="sxs-lookup"><span data-stu-id="00ac5-310">However, some operations (for example, searching a table) may fail frequently.</span></span> <span data-ttu-id="00ac5-311">Hodnoty možnosti F # jsou vynikající způsob představují návratové typy z těchto operací.</span><span class="sxs-lookup"><span data-stu-id="00ac5-311">F# option values are an excellent way to represent the return types of these operations.</span></span> <span data-ttu-id="00ac5-312">Tyto operace obvykle začínají předponou názvu "zkuste":</span><span class="sxs-lookup"><span data-stu-id="00ac5-312">These operations conventionally start with the name prefix “try”:</span></span>

```fsharp
// bad: throws exception if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// bad: returns -1 if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// good: returns None if no element meets criteria
member this.TryFindFirstIndex(pred : 'T -> bool) : int option =
    ...
```

### <a name="extension-members"></a><span data-ttu-id="00ac5-313">Rozšíření členy</span><span class="sxs-lookup"><span data-stu-id="00ac5-313">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="00ac5-314">Pečlivě použít F # rozšíření členy v jazyce F #-na-F # součásti</span><span class="sxs-lookup"><span data-stu-id="00ac5-314">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="00ac5-315">F # rozšíření členy obecně lze používat pouze pro operace, které jsou v uzavření vnitřní operace, které souvisí s typem ve většině režimech použití.</span><span class="sxs-lookup"><span data-stu-id="00ac5-315">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="00ac5-316">Jeden běžné slouží k poskytování rozhraní API, která jsou více idiomatickou k F # pro různé typy .NET:</span><span class="sxs-lookup"><span data-stu-id="00ac5-316">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="00ac5-317">Sjednocení typů</span><span class="sxs-lookup"><span data-stu-id="00ac5-317">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="00ac5-318">Použití rozlišovaná sjednocení místo hierarchie tříd pro stromovou strukturou data</span><span class="sxs-lookup"><span data-stu-id="00ac5-318">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="00ac5-319">Jako stromové struktury jsou rekurzivně definované.</span><span class="sxs-lookup"><span data-stu-id="00ac5-319">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="00ac5-320">Toto je nevhodných s použitím dědičnosti, ale elegantní s Rozlišované sjednocení.</span><span class="sxs-lookup"><span data-stu-id="00ac5-320">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="00ac5-321">Představující stromu jako data s Rozlišované sjednocení také umožňuje využívat úplnosti v porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="00ac5-321">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="00ac5-322">Použití `[<RequireQualifiedAccess>]` na union typy, jejichž případu názvy nejsou dostatečně jedinečné</span><span class="sxs-lookup"><span data-stu-id="00ac5-322">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="00ac5-323">V doméně, kde se stejným názvem je nejlepší název pro různé akce, jako je například Rozlišované sjednocení případech může najít sami.</span><span class="sxs-lookup"><span data-stu-id="00ac5-323">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="00ac5-324">Můžete použít `[<RequireQualifiedAccess>]` kvůli zajištění jednoznačnosti rozlišování názvů, aby se zabránilo spouštění matoucí chyby kvůli stínový provoz závisí na pořadí `open` příkazy</span><span class="sxs-lookup"><span data-stu-id="00ac5-324">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="00ac5-325">Skrýt reprezentace rozlišovaná sjednocení pro binární kompatibilní rozhraní API, pokud je pravděpodobné, vyvíjí návrhu z těchto typů</span><span class="sxs-lookup"><span data-stu-id="00ac5-325">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="00ac5-326">Sjednocení typů spoléhají na F # porovnávání formuláře pro stručného programovací model.</span><span class="sxs-lookup"><span data-stu-id="00ac5-326">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="00ac5-327">Jak je uvedeno nahoře, neměli byste odhalil reprezentace konkrétní data, pokud je pravděpodobné, vyvíjí návrh tyto typy.</span><span class="sxs-lookup"><span data-stu-id="00ac5-327">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="00ac5-328">Například reprezentace rozlišovaná sjednocení může být skryté pomocí deklaraci soukromý nebo interní nebo podpis souboru.</span><span class="sxs-lookup"><span data-stu-id="00ac5-328">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="00ac5-329">Pokud odhalit rozlišovaná sjednocení bez, může být obtížné verze knihovnu, aniž by vás uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-329">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="00ac5-330">Místo toho zvažte odhalil jeden nebo více aktivní vzorky tak, aby povolovala porovnávání se přes hodnoty stejného typu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-330">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="00ac5-331">Aktivní vzorky zadejte jiný způsob, jak poskytnout příjemci knihovny F # pro porovnávání a snižuje přímo vystavení sjednocení typů F #.</span><span class="sxs-lookup"><span data-stu-id="00ac5-331">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="00ac5-332">Vložené funkce a omezení člena</span><span class="sxs-lookup"><span data-stu-id="00ac5-332">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="00ac5-333">Definujte obecné číselné algoritmy vložené funkce pomocí omezení předpokládané člen a statisticky obecné typy</span><span class="sxs-lookup"><span data-stu-id="00ac5-333">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="00ac5-334">Aritmetické člen omezení a omezení porovnání F # jsou standard pro F # – programování.</span><span class="sxs-lookup"><span data-stu-id="00ac5-334">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="00ac5-335">Zvažte například následující kód:</span><span class="sxs-lookup"><span data-stu-id="00ac5-335">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="00ac5-336">Typ této funkce je následující:</span><span class="sxs-lookup"><span data-stu-id="00ac5-336">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="00ac5-337">Toto je vhodné funkce pro veřejné rozhraní API v matematickém knihovně.</span><span class="sxs-lookup"><span data-stu-id="00ac5-337">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="00ac5-338">Vyhněte se použití omezení člen simulace typu třídy a kachní zadáním</span><span class="sxs-lookup"><span data-stu-id="00ac5-338">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="00ac5-339">Je možné k simulaci "divokou zadáním" použití omezení člen F #.</span><span class="sxs-lookup"><span data-stu-id="00ac5-339">It is possible to simulate “duck typing” using F# member constraints.</span></span> <span data-ttu-id="00ac5-340">Však členy, které pomocí tohoto objektu není v obecné je třeba používat v F #-na-návrhů knihovny F #.</span><span class="sxs-lookup"><span data-stu-id="00ac5-340">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="00ac5-341">Je to proto, že knihovna návrhy založené na neznámého nebo nestandardní implicitní omezení můžou vést k uživatelského kódu se pevná a vázané na jednu konkrétní framework vzor.</span><span class="sxs-lookup"><span data-stu-id="00ac5-341">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="00ac5-342">Kromě toho je dobré pravděpodobné, že výrazně využívá člen omezení tímto způsobem může mít za následek kompilace velmi dlouhé časy.</span><span class="sxs-lookup"><span data-stu-id="00ac5-342">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="00ac5-343">Definice – operátor</span><span class="sxs-lookup"><span data-stu-id="00ac5-343">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="00ac5-344">Vyhněte se definování vlastní symbolický operátory</span><span class="sxs-lookup"><span data-stu-id="00ac5-344">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="00ac5-345">Vlastní operátory je nezbytné v některých situacích a jsou velmi užitečné konvenční zařízení v rámci rozsáhlý soubor implementaci kódu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-345">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="00ac5-346">Pro nové uživatele knihovny se často funkce s názvem snadněji používat.</span><span class="sxs-lookup"><span data-stu-id="00ac5-346">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="00ac5-347">Kromě toho může být obtížné dokumentu vlastní symbolický operátory a uživatelé najít obtížné vyhledat nápovědu k operátory z důvodu omezení existující v IDE a vyhledávacího.</span><span class="sxs-lookup"><span data-stu-id="00ac5-347">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="00ac5-348">V důsledku toho je nejvhodnější publikovat vaše funkce jako funkce s názvem a členy a pouze v případě, že konvenční výhody převáží nad dokumentace a kognitivní náklady toho, aby kromě vystavit operátory pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="00ac5-348">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="00ac5-349">Měrné jednotky</span><span class="sxs-lookup"><span data-stu-id="00ac5-349">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="00ac5-350">Pečlivě použijte měrné jednotky pro zabezpečení přidané typů v F # – kód</span><span class="sxs-lookup"><span data-stu-id="00ac5-350">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="00ac5-351">Další informace o zadáte pro jednotky míry se vymaže při prohlížení jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-351">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="00ac5-352">Pamatujte, že součásti rozhraní .NET, nástroje a reflexe uvidí typy sítí SAN jednotky.</span><span class="sxs-lookup"><span data-stu-id="00ac5-352">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="00ac5-353">Například C# uživatelé uvidí `float` místo `float<kg>`.</span><span class="sxs-lookup"><span data-stu-id="00ac5-353">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="00ac5-354">Zkratky typů</span><span class="sxs-lookup"><span data-stu-id="00ac5-354">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="00ac5-355">Pečlivě použití zkratky typů ke zjednodušení F # – kód</span><span class="sxs-lookup"><span data-stu-id="00ac5-355">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="00ac5-356">Součásti rozhraní .NET, nástroje a reflexe neuvidí zkrácené názvy typů.</span><span class="sxs-lookup"><span data-stu-id="00ac5-356">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="00ac5-357">Významné používání zkratky typů provést také domény zobrazí složitější než ve skutečnosti je, která by mohla matou příjemci.</span><span class="sxs-lookup"><span data-stu-id="00ac5-357">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="00ac5-358">Vyhněte se zkratky typů pro veřejné typy, jejíž členové a vlastnosti by měla být vnitřně liší od těch, které jsou k dispozici na typ se používá zkratka</span><span class="sxs-lookup"><span data-stu-id="00ac5-358">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="00ac5-359">V takovém případě zjistí typ se používá zkratka příliš mnoho o reprezentace skutečný typ definovaný.</span><span class="sxs-lookup"><span data-stu-id="00ac5-359">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="00ac5-360">Místo toho zvažte zabalení zkratka v typu třídy nebo jeden případ rozlišovaná sjednocení (nebo, když výkonu je nezbytné, zvažte použití typu Struktura zabalit zkratku).</span><span class="sxs-lookup"><span data-stu-id="00ac5-360">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="00ac5-361">Je třeba tempting k definování více mapy ve speciálním případě F # mapy, například:</span><span class="sxs-lookup"><span data-stu-id="00ac5-361">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="00ac5-362">Ale logické tečkami operace u tohoto typu nejsou stejná jako operace na mapě – například je možné logicky, aby operátor vyhledávání map. [klíče] vrátí prázdný seznam, pokud není klíč ve slovníku místo vyvolání k výjimce.</span><span class="sxs-lookup"><span data-stu-id="00ac5-362">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="00ac5-363">Pokyny pro knihovny pro použití jiných jazyků .NET</span><span class="sxs-lookup"><span data-stu-id="00ac5-363">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="00ac5-364">Při navrhování knihovny pro použití jiných jazyků .NET, je potřeba dodržovat [pokynů pro návrh knihovny .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="00ac5-364">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="00ac5-365">V tomto dokumentu tyto knihovny jsou označeny jako vanilla knihovny .NET, a F #-facing knihovny, které používají F # vytvoří bez omezení.</span><span class="sxs-lookup"><span data-stu-id="00ac5-365">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="00ac5-366">Navrhování vanilla knihovny .NET znamená poskytující známé a idiomatickou rozhraní API konzistentní se zbytkem rozhraní .NET Framework pomocí minimalizace použití F # – konkrétní konstrukce v veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="00ac5-366">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="00ac5-367">Pravidla jsou vysvětlené v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="00ac5-367">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="00ac5-368">Návrh Namespace a typ (pro knihovny pro použití jiných jazyků .NET)</span><span class="sxs-lookup"><span data-stu-id="00ac5-368">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="00ac5-369">Použít zásady vytváření názvů .NET pro veřejné rozhraní API komponent</span><span class="sxs-lookup"><span data-stu-id="00ac5-369">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="00ac5-370">Věnujte zvláštní pozornost použití zkrácené názvy a podle pokynů .NET malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="00ac5-370">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="00ac5-371">Obory názvů, typy a členy použít jako primární organizační struktury komponent</span><span class="sxs-lookup"><span data-stu-id="00ac5-371">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="00ac5-372">Všechny soubory obsahující veřejný funkce by měl začínat obráceným `namespace` deklarace a pouze veřejné entity v oborech názvů by měl být typy.</span><span class="sxs-lookup"><span data-stu-id="00ac5-372">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="00ac5-373">Nepoužívejte F # moduly.</span><span class="sxs-lookup"><span data-stu-id="00ac5-373">Do not use F# modules.</span></span>

<span data-ttu-id="00ac5-374">Použijte moduly neveřejný pro implementaci kódu, nástroj typy a funkce nástroj.</span><span class="sxs-lookup"><span data-stu-id="00ac5-374">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="00ac5-375">Statické typy by měly být upřednostňované přes moduly, protože umožňují pro budoucí vývoj rozhraní API používat přetížení a další koncepty .NET API návrhu, které nesmí být použity v F # moduly.</span><span class="sxs-lookup"><span data-stu-id="00ac5-375">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="00ac5-376">Například místo následující veřejné rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="00ac5-376">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="00ac5-377">Místo toho zvažte:</span><span class="sxs-lookup"><span data-stu-id="00ac5-377">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="00ac5-378">Pokud nebude momentální návrh typy používat typy záznamů F # ve vanilla rozhraní API technologie .NET</span><span class="sxs-lookup"><span data-stu-id="00ac5-378">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="00ac5-379">Typy záznamů F # zkompilovat na třídu jednoduché rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-379">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="00ac5-380">Toto jsou vhodné pro některé typy jednoduchý, stabilní rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="00ac5-380">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="00ac5-381">Měli byste zvážit použití `[<NoEquality>]` a `[<NoComparison>]` atributy potlačit automatické generování rozhraní.</span><span class="sxs-lookup"><span data-stu-id="00ac5-381">You should consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="00ac5-382">Také Vyhněte se používání měnitelný záznam pole v vanilla rozhraní API technologie .NET jako tyto zpřístupňuje veřejné pole.</span><span class="sxs-lookup"><span data-stu-id="00ac5-382">Also avoid using mutable record fields in vanilla .NET APIs as these exposes a public field.</span></span> <span data-ttu-id="00ac5-383">Vždy zvažte, zda by třída poskytují flexibilnější možnost pro budoucí vývoj rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="00ac5-383">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="00ac5-384">Například následující kód F # zpřístupní veřejné rozhraní API k příjemce C#:</span><span class="sxs-lookup"><span data-stu-id="00ac5-384">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="00ac5-385">F #:</span><span class="sxs-lookup"><span data-stu-id="00ac5-385">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

<span data-ttu-id="00ac5-386">C#:</span><span class="sxs-lookup"><span data-stu-id="00ac5-386">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="00ac5-387">Skrýt reprezentace typů F # union v vanilla rozhraní API technologie .NET</span><span class="sxs-lookup"><span data-stu-id="00ac5-387">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="00ac5-388">Sjednocení typů F # nejsou obvykle používány napříč hranicemi součásti i pro F #-na-F # kódování.</span><span class="sxs-lookup"><span data-stu-id="00ac5-388">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="00ac5-389">Jsou zařízení s vynikající implementace, pokud se používá interně v rámci komponenty a knihovny.</span><span class="sxs-lookup"><span data-stu-id="00ac5-389">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="00ac5-390">Při navrhování vanilla .NET API, vezměte v úvahu skrytí reprezentaci typu union pomocí deklaraci privátní nebo soubor podpisu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-390">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="00ac5-391">Může také posílení typů, které používají znázornění union interně se členy k poskytování požadované. Rozhraní API NET přístupem.</span><span class="sxs-lookup"><span data-stu-id="00ac5-391">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="00ac5-392">Návrh grafického uživatelského rozhraní a další součásti pomocí vzory návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="00ac5-392">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="00ac5-393">Mnoho různých rozhraní nejsou k dispozici v rámci .NET, například WinForms, WPF a ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-393">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="00ac5-394">Konvence pojmenování a návrhu pro každý by měl použít, pokud navrhujete komponenty pro použití v tyto architektury.</span><span class="sxs-lookup"><span data-stu-id="00ac5-394">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="00ac5-395">Například pro WPF programování, přijímat WPF vzory návrhu pro třídy, které jsou návrhu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-395">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="00ac5-396">Pro modely v programování uživatelské rozhraní, použijte vzory návrhu, jako jsou události a kolekce založené na oznámení jsou uvedené v <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="00ac5-396">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="00ac5-397">Objekt a člen návrhu (pro knihovny pro použití jiných jazyků .NET)</span><span class="sxs-lookup"><span data-stu-id="00ac5-397">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="00ac5-398">Vystavení události .NET pomocí clievent – atribut</span><span class="sxs-lookup"><span data-stu-id="00ac5-398">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="00ac5-399">Vytvořit `DelegateEvent` s konkrétní .NET delegovat typ, který přebírá objekt a `EventArgs` (místo `Event`, který právě používá `FSharpHandler` typu ve výchozím nastavení), aby se události publikují v známé způsob, jak jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-399">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a><span data-ttu-id="00ac5-400">Vystavit asynchronních operací v metody, které vrací úlohy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="00ac5-400">Expose asynchronous operations as methods which return .NET tasks</span></span>

<span data-ttu-id="00ac5-401">Úlohy se používají v rozhraní .NET představují active asynchronní výpočty.</span><span class="sxs-lookup"><span data-stu-id="00ac5-401">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="00ac5-402">Úlohy jsou v obecné složení méně než F # `Async<T>` objekty, protože představují "již provádění" úlohy a nemůže obsahovat současně způsoby, provést paralelní složení, nebo které skrýt šíření zrušení signály a jiných Kontextové parametry.</span><span class="sxs-lookup"><span data-stu-id="00ac5-402">Tasks are in general less compositional than F# `Async<T>` objects, since they represent “already executing” tasks and can’t be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="00ac5-403">Bez ohledu na to, jsou metody, které vrací úlohy standardní reprezentace asynchronní programování v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-403">However, despite this, methods which return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="00ac5-404">Často budete také chtít přijímat token explicitní zrušení:</span><span class="sxs-lookup"><span data-stu-id="00ac5-404">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="00ac5-405">Použití delegáta typy .NET místo funkce typů F #</span><span class="sxs-lookup"><span data-stu-id="00ac5-405">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="00ac5-406">Zde "typů F # funkce" znamená "šipku" typy jako `int -> int`.</span><span class="sxs-lookup"><span data-stu-id="00ac5-406">Here “F# function types” mean “arrow” types like `int -> int`.</span></span>

<span data-ttu-id="00ac5-407">Místo:</span><span class="sxs-lookup"><span data-stu-id="00ac5-407">Instead of this:</span></span>

```fsharp
member this.Transform(f:int->int) =
    ...
```

<span data-ttu-id="00ac5-408">postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="00ac5-408">Do this:</span></span>

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

<span data-ttu-id="00ac5-409">Typ funkce F # se zobrazí jako `class FSharpFunc<T,U>` do jiných jazyků .NET a je méně vhodný pro jazykové funkce a nástrojů, které pochopit typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="00ac5-409">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understand delegate types.</span></span> <span data-ttu-id="00ac5-410">Při vytváření vyšší pořadí metodu cílení na rozhraní .NET Framework 3.5 nebo vyšší, `System.Func` a `System.Action` Delegáti jsou správné rozhraní API pro publikování a umožňuje vývojářům rozhraní .NET způsobem nízkým třením využívají tato rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="00ac5-410">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="00ac5-411">(Při cílení na rozhraní .NET Framework 2.0, jsou typy definované v systému delegáta omezenější, zvažte použití delegáta předdefinované typy jako `System.Converter<T,U>` nebo definování typu konkrétní delegáta.)</span><span class="sxs-lookup"><span data-stu-id="00ac5-411">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="00ac5-412">Na straně překlopit .NET delegáti nejsou přirozené pro F # – čelí knihovny (viz další část v F # – čelí knihovny).</span><span class="sxs-lookup"><span data-stu-id="00ac5-412">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="00ac5-413">V důsledku toho je společné strategie implementace při vývoji vyšší pořadí metody pro vanilla knihovny .NET k vytváření všech implementace pomocí funkce typů F # a pak vytvořte veřejné rozhraní API použití delegátů jako dynamické průčelí za na skutečné F # implementace.</span><span class="sxs-lookup"><span data-stu-id="00ac5-413">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="00ac5-414">Použití vzoru TryGetValue místo vrácení hodnoty možnosti F # a dáváte přednost přetěžování metody k pořízení F # hodnoty možnosti jako argumenty</span><span class="sxs-lookup"><span data-stu-id="00ac5-414">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="00ac5-415">Běžné způsoby použití typu možnosti F # rozhraní API jsou lepší implementované v vanilla rozhraní API technologie .NET pomocí standardní .NET návrh techniky.</span><span class="sxs-lookup"><span data-stu-id="00ac5-415">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="00ac5-416">Místo vrací hodnotu možnosti F #, zvažte použití návratový typ bool plus výstupní parametr jako vzor "TryGetValue".</span><span class="sxs-lookup"><span data-stu-id="00ac5-416">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="00ac5-417">A místo trvá F # hodnoty možnosti jako parametry, zvažte použití metody přetížení nebo volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="00ac5-417">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="00ac5-418">Použití rozhraní .NET kolekce typy rozhraní IEnumerable\<T\> a IDictionary\<klíče, hodnota\> pro parametry a návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="00ac5-418">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="00ac5-419">Nepoužívejte typech konkrétní kolekce například pole .NET `T[]`, typů F # `list<T>`, `Map<Key,Value>` a `Set<T>`, a .NET collection konkrétní typy, jako `Dictionary<Key,Value>`.</span><span class="sxs-lookup"><span data-stu-id="00ac5-419">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="00ac5-420">Pokyny pro návrh knihovny .NET mají dobrou Rady týkající se použití různé typy kolekcí, jako je `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="00ac5-420">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="00ac5-421">Některé použití polí (`T[]`) je přijatelné v některých případech z důvodů výkonu.</span><span class="sxs-lookup"><span data-stu-id="00ac5-421">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="00ac5-422">Všimněte si, že zejména `seq<T>` je právě F # alias pro `IEnumerable<T>`, a proto je seq často příslušného typu pro vanilla .NET API.</span><span class="sxs-lookup"><span data-stu-id="00ac5-422">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="00ac5-423">Místo toho jazyka F # uvádí:</span><span class="sxs-lookup"><span data-stu-id="00ac5-423">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names : string list) =
    ...
```

<span data-ttu-id="00ac5-424">Pomocí F # pořadí:</span><span class="sxs-lookup"><span data-stu-id="00ac5-424">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="00ac5-425">Použijte typ jednotky jako pouze vstupní typ metody definovat metodu argumentu nula, nebo jako jediný návratový typ definovat metodu vrácení void</span><span class="sxs-lookup"><span data-stu-id="00ac5-425">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="00ac5-426">Vyhněte se ostatní používá typ jednotky.</span><span class="sxs-lookup"><span data-stu-id="00ac5-426">Avoid other uses of the unit type.</span></span> <span data-ttu-id="00ac5-427">Jsou to funkční:</span><span class="sxs-lookup"><span data-stu-id="00ac5-427">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

<span data-ttu-id="00ac5-428">To je chybný.:</span><span class="sxs-lookup"><span data-stu-id="00ac5-428">This is bad:</span></span>

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="00ac5-429">Zkontrolujte hodnoty null na hranicích vanilla rozhraní API .NET</span><span class="sxs-lookup"><span data-stu-id="00ac5-429">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="00ac5-430">F # – kód implementace obvykle obsahují méně hodnoty null, z důvodu vzory návrhu neměnné a omezení použití null literálů pro typy F #.</span><span class="sxs-lookup"><span data-stu-id="00ac5-430">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="00ac5-431">Jinými jazyky rozhraní .NET často používají jako hodnota null mnohem častěji.</span><span class="sxs-lookup"><span data-stu-id="00ac5-431">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="00ac5-432">Z toho důvodu F # kód, který je vystavení vanilla .NET API Zkontrolujte parametry pro hodnotu null na hranici rozhraní API a zabránit tyto hodnoty toku hlubší do kódu implementace F #.</span><span class="sxs-lookup"><span data-stu-id="00ac5-432">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="00ac5-433">`isNull` Funkce nebo na porovnávání vzorů `null` vzor lze použít.</span><span class="sxs-lookup"><span data-stu-id="00ac5-433">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="00ac5-434">Nepoužívejte řazených kolekcí členů jako návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="00ac5-434">Avoid using tuples as return values</span></span>

<span data-ttu-id="00ac5-435">Místo toho raději vrácení pojmenovaného typu, který obsahuje agregovaná data, nebo pomocí výstupní parametry vrátit více hodnot.</span><span class="sxs-lookup"><span data-stu-id="00ac5-435">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="00ac5-436">I když existují řazených kolekcí členů a struktura řazených kolekcí členů v rozhraní .NET (včetně C# jazyková podpora pro řazené kolekce členů struktury), nejčastěji není zadá ideální a očekávaná rozhraní API pro vývojáře .NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-436">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="00ac5-437">Nepoužívejte currying parametrů</span><span class="sxs-lookup"><span data-stu-id="00ac5-437">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="00ac5-438">Místo toho použijte rozhraní .NET konvence volání ``Method(arg1,arg2,…,argN)``.</span><span class="sxs-lookup"><span data-stu-id="00ac5-438">Instead, use .NET calling conventions ``Method(arg1,arg2,…,argN)``.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="00ac5-439">Tip: Pokud navrhujete knihovny pro použití v kterémkoli jazyce platformy .NET, nejsou žádné nenahrazuje ve skutečnosti to některé experimentální C# a Visual Basic programování zajistit, aby knihovnách "chování právo" z těchto jazyků.</span><span class="sxs-lookup"><span data-stu-id="00ac5-439">Tip: If you’re designing libraries for use from any .NET language, then there’s no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="00ac5-440">Nástroje, jako je rozhraní .NET Reflector a prohlížeče objektů Visual Studio můžete také zajistit, aby knihovny a jejich dokumentace zobrazily podle očekávání pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="00ac5-440">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="00ac5-441">Příloha</span><span class="sxs-lookup"><span data-stu-id="00ac5-441">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="00ac5-442">Příklad začátku do konce navrhování F # – kód pro použití jinými jazyky rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="00ac5-442">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="00ac5-443">Vezměte v úvahu následující třídy:</span><span class="sxs-lookup"><span data-stu-id="00ac5-443">Consider the following class:</span></span>

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

<span data-ttu-id="00ac5-444">Odvozené F # typ této třídy je následující:</span><span class="sxs-lookup"><span data-stu-id="00ac5-444">The inferred F# type of this class is as follows:</span></span>

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

<span data-ttu-id="00ac5-445">Podívejme se na tom, jak se vyskytuje tento typ F # pro programátory, použití jiného jazyka .NET.</span><span class="sxs-lookup"><span data-stu-id="00ac5-445">Let’s take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="00ac5-446">Přibližná jazyka C# "podpis" je například takto:</span><span class="sxs-lookup"><span data-stu-id="00ac5-446">For example, the approximate C# “signature” is as follows:</span></span>

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

<span data-ttu-id="00ac5-447">Existují některé důležité body Všimněte o jak F # představuje konstrukce sem.</span><span class="sxs-lookup"><span data-stu-id="00ac5-447">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="00ac5-448">Příklad:</span><span class="sxs-lookup"><span data-stu-id="00ac5-448">For example:</span></span>

* <span data-ttu-id="00ac5-449">Metadata, jako jsou názvy argumentu bylo zachováno.</span><span class="sxs-lookup"><span data-stu-id="00ac5-449">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="00ac5-450">F # metod, které berou dva argumenty stát C# metod, které berou dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="00ac5-450">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="00ac5-451">Funkce a seznamy budou odkazy na odpovídající typy v knihovně F #.</span><span class="sxs-lookup"><span data-stu-id="00ac5-451">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="00ac5-452">Následující kód ukazuje, jak upravit tento kód vzít v úvahu tyto věci.</span><span class="sxs-lookup"><span data-stu-id="00ac5-452">The following code shows how to adjust this code to take these things into account.</span></span>

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

<span data-ttu-id="00ac5-453">Odvozené F # typ kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="00ac5-453">The inferred F# type of the code is as follows:</span></span>

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

<span data-ttu-id="00ac5-454">Podpis C# je teď následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="00ac5-454">The C# signature is now as follows:</span></span>

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

<span data-ttu-id="00ac5-455">Opravy provedené připravit tento typ pro použití jako součást vanilla knihovny .NET jsou následující:</span><span class="sxs-lookup"><span data-stu-id="00ac5-455">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="00ac5-456">Upravit několik názvů: `Point1`, `n`, `l`, a `f` aktivovala `RadialPoint`, `count`, `factor`, a `transform`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="00ac5-456">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="00ac5-457">Použít návratovým typem `seq<RadialPoint>` místo `RadialPoint list` změnou seznamu konstrukce pomocí `[ ... ]` pořadí vytváření pomocí `IEnumerable<RadialPoint>`.</span><span class="sxs-lookup"><span data-stu-id="00ac5-457">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="00ac5-458">Použít typ formátu .NET delegáta `System.Func` místo typ funkce F #.</span><span class="sxs-lookup"><span data-stu-id="00ac5-458">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="00ac5-459">Díky tomu je mnohem nicer využívat v kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="00ac5-459">This makes it far nicer to consume in C# code.</span></span>
