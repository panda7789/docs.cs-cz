---
title: "Obecné zásady vytváření názvů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dde3adbb7640978829dea4b977ed14eec38a9077
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="general-naming-conventions"></a><span data-ttu-id="35ea4-102">Obecné zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="35ea4-102">General Naming Conventions</span></span>
<span data-ttu-id="35ea4-103">Tato část popisuje obecné zásady vytváření názvů vztahující se k výběru word pokyny k používání zkratky a zkratky a doporučení na tom, jak zamezit pomocí názvů konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="35ea4-103">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>  
  
## <a name="word-choice"></a><span data-ttu-id="35ea4-104">Výběr aplikace Word</span><span class="sxs-lookup"><span data-stu-id="35ea4-104">Word Choice</span></span>  
 <span data-ttu-id="35ea4-105">**PROVEĎTE ✓** zvolte snadno čitelné identifikátor názvy.</span><span class="sxs-lookup"><span data-stu-id="35ea4-105">**✓ DO** choose easily readable identifier names.</span></span>  
  
 <span data-ttu-id="35ea4-106">Například vlastnost s názvem `HorizontalAlignment` je angličtina srozumitelnější než `AlignmentHorizontal`.</span><span class="sxs-lookup"><span data-stu-id="35ea4-106">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>  
  
 <span data-ttu-id="35ea4-107">**PROVEĎTE ✓** upřednostnit čitelnost přes jako stručný výtah.</span><span class="sxs-lookup"><span data-stu-id="35ea4-107">**✓ DO** favor readability over brevity.</span></span>  
  
 <span data-ttu-id="35ea4-108">Název vlastnosti `CanScrollHorizontally` je lepší, než `ScrollableX` (skrytého odkaz na ose x).</span><span class="sxs-lookup"><span data-stu-id="35ea4-108">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>  
  
 <span data-ttu-id="35ea4-109">**X nesmí** použít podtržítka, pomlčky nebo jiné nealfanumerické znaky.</span><span class="sxs-lookup"><span data-stu-id="35ea4-109">**X DO NOT** use underscores, hyphens, or any other nonalphanumeric characters.</span></span>  
  
 <span data-ttu-id="35ea4-110">**X nesmí** použijte Maďarská zápis.</span><span class="sxs-lookup"><span data-stu-id="35ea4-110">**X DO NOT** use Hungarian notation.</span></span>  
  
 <span data-ttu-id="35ea4-111">**X nepoužívejte** pomocí identifikátorů, které je v konfliktu s slov široce používá programovací jazyky.</span><span class="sxs-lookup"><span data-stu-id="35ea4-111">**X AVOID** using identifiers that conflict with keywords of widely used programming languages.</span></span>  
  
 <span data-ttu-id="35ea4-112">Podle pravidla 4 z specifikace CLS (Common Language) musíte zadat všechny jazyky kompatibilní mechanismus, který umožňuje přístup k pojmenované položky, které používají klíčové slovo daného jazyka jako identifikátor.</span><span class="sxs-lookup"><span data-stu-id="35ea4-112">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="35ea4-113">C#, například používá znak jako mechanismus řídicí v tomto případě @.</span><span class="sxs-lookup"><span data-stu-id="35ea4-113">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="35ea4-114">Je však stále vhodné se vyhnout běžné klíčová slova, protože je mnohem obtížnější pro použití metody s řídicí sekvence než jeden bez ní.</span><span class="sxs-lookup"><span data-stu-id="35ea4-114">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>  
  
## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="35ea4-115">Pomocí zkratky a zkratky</span><span class="sxs-lookup"><span data-stu-id="35ea4-115">Using Abbreviations and Acronyms</span></span>  
 <span data-ttu-id="35ea4-116">**X nesmí** použít zkratky nebo staženiny jako součást identifikátoru názvy.</span><span class="sxs-lookup"><span data-stu-id="35ea4-116">**X DO NOT** use abbreviations or contractions as part of identifier names.</span></span>  
  
 <span data-ttu-id="35ea4-117">Například použít `GetWindow` místo `GetWin`.</span><span class="sxs-lookup"><span data-stu-id="35ea4-117">For example, use `GetWindow` rather than `GetWin`.</span></span>  
  
 <span data-ttu-id="35ea4-118">**X nesmí** žádné režim, které nejsou široce používaný a to i v případě, že jsou pouze v případě, že je nutné použít.</span><span class="sxs-lookup"><span data-stu-id="35ea4-118">**X DO NOT** use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>  
  
## <a name="avoiding-language-specific-names"></a><span data-ttu-id="35ea4-119">Zamezení názvy konkrétní jazyk</span><span class="sxs-lookup"><span data-stu-id="35ea4-119">Avoiding Language-Specific Names</span></span>  
 <span data-ttu-id="35ea4-120">**PROVEĎTE ✓** používá sémanticky zajímavé názvy namísto klíčová slova specifická pro jazyk pro názvy typů.</span><span class="sxs-lookup"><span data-stu-id="35ea4-120">**✓ DO** use semantically interesting names rather than language-specific keywords for type names.</span></span>  
  
 <span data-ttu-id="35ea4-121">Například `GetLength` je lepší název než `GetInt`.</span><span class="sxs-lookup"><span data-stu-id="35ea4-121">For example, `GetLength` is a better name than `GetInt`.</span></span>  
  
 <span data-ttu-id="35ea4-122">**PROVEĎTE ✓** použít obecný název typu CLR, nikoli název konkrétní jazyk, ve výjimečných případech, pokud identifikátor nemá význam sémantického nad rámec jeho typu.</span><span class="sxs-lookup"><span data-stu-id="35ea4-122">**✓ DO** use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>  
  
 <span data-ttu-id="35ea4-123">Například metoda převodu na <xref:System.Int64> by měl být pojmenován `ToInt64`, nikoli `ToLong` (protože <xref:System.Int64> je název CLR jazyka C# – konkrétní alias `long`).</span><span class="sxs-lookup"><span data-stu-id="35ea4-123">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="35ea4-124">Následující tabulka představuje několik základních datových typů pomocí názvy typů CLR (stejně jako odpovídající názvy typů pro C#, Visual Basic a C++).</span><span class="sxs-lookup"><span data-stu-id="35ea4-124">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>  
  
|<span data-ttu-id="35ea4-125">C#</span><span class="sxs-lookup"><span data-stu-id="35ea4-125">C#</span></span>|<span data-ttu-id="35ea4-126">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35ea4-126">Visual Basic</span></span>|<span data-ttu-id="35ea4-127">C++</span><span class="sxs-lookup"><span data-stu-id="35ea4-127">C++</span></span>|<span data-ttu-id="35ea4-128">CLR</span><span class="sxs-lookup"><span data-stu-id="35ea4-128">CLR</span></span>|  
|---------|------------------|-----------|---------|  
|<span data-ttu-id="35ea4-129">**SByte –**</span><span class="sxs-lookup"><span data-stu-id="35ea4-129">**sbyte**</span></span>|<span data-ttu-id="35ea4-130">**SByte –**</span><span class="sxs-lookup"><span data-stu-id="35ea4-130">**SByte**</span></span>|<span data-ttu-id="35ea4-131">**Char**</span><span class="sxs-lookup"><span data-stu-id="35ea4-131">**char**</span></span>|<span data-ttu-id="35ea4-132">**SByte –**</span><span class="sxs-lookup"><span data-stu-id="35ea4-132">**SByte**</span></span>|  
|<span data-ttu-id="35ea4-133">**bajtů**</span><span class="sxs-lookup"><span data-stu-id="35ea4-133">**byte**</span></span>|<span data-ttu-id="35ea4-134">**Bajtů**</span><span class="sxs-lookup"><span data-stu-id="35ea4-134">**Byte**</span></span>|<span data-ttu-id="35ea4-135">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="35ea4-135">**unsigned char**</span></span>|<span data-ttu-id="35ea4-136">**Bajtů**</span><span class="sxs-lookup"><span data-stu-id="35ea4-136">**Byte**</span></span>|  
|<span data-ttu-id="35ea4-137">**krátký**</span><span class="sxs-lookup"><span data-stu-id="35ea4-137">**short**</span></span>|<span data-ttu-id="35ea4-138">**Krátký**</span><span class="sxs-lookup"><span data-stu-id="35ea4-138">**Short**</span></span>|<span data-ttu-id="35ea4-139">**krátký**</span><span class="sxs-lookup"><span data-stu-id="35ea4-139">**short**</span></span>|<span data-ttu-id="35ea4-140">**Int16**</span><span class="sxs-lookup"><span data-stu-id="35ea4-140">**Int16**</span></span>|  
|<span data-ttu-id="35ea4-141">**ushort –**</span><span class="sxs-lookup"><span data-stu-id="35ea4-141">**ushort**</span></span>|<span data-ttu-id="35ea4-142">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="35ea4-142">**UInt16**</span></span>|<span data-ttu-id="35ea4-143">**short bez znaménka**</span><span class="sxs-lookup"><span data-stu-id="35ea4-143">**unsigned short**</span></span>|<span data-ttu-id="35ea4-144">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="35ea4-144">**UInt16**</span></span>|  
|<span data-ttu-id="35ea4-145">**celá čísla**</span><span class="sxs-lookup"><span data-stu-id="35ea4-145">**int**</span></span>|<span data-ttu-id="35ea4-146">**Celé číslo**</span><span class="sxs-lookup"><span data-stu-id="35ea4-146">**Integer**</span></span>|<span data-ttu-id="35ea4-147">**celá čísla**</span><span class="sxs-lookup"><span data-stu-id="35ea4-147">**int**</span></span>|<span data-ttu-id="35ea4-148">**Int32**</span><span class="sxs-lookup"><span data-stu-id="35ea4-148">**Int32**</span></span>|  
|<span data-ttu-id="35ea4-149">**uint**</span><span class="sxs-lookup"><span data-stu-id="35ea4-149">**uint**</span></span>|<span data-ttu-id="35ea4-150">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="35ea4-150">**UInt32**</span></span>|<span data-ttu-id="35ea4-151">**int bez znaménka**</span><span class="sxs-lookup"><span data-stu-id="35ea4-151">**unsigned int**</span></span>|<span data-ttu-id="35ea4-152">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="35ea4-152">**UInt32**</span></span>|  
|<span data-ttu-id="35ea4-153">**dlouhá**</span><span class="sxs-lookup"><span data-stu-id="35ea4-153">**long**</span></span>|<span data-ttu-id="35ea4-154">**Dlouhá**</span><span class="sxs-lookup"><span data-stu-id="35ea4-154">**Long**</span></span>|<span data-ttu-id="35ea4-155">**__int64**</span><span class="sxs-lookup"><span data-stu-id="35ea4-155">**__int64**</span></span>|<span data-ttu-id="35ea4-156">**Int64**</span><span class="sxs-lookup"><span data-stu-id="35ea4-156">**Int64**</span></span>|  
|<span data-ttu-id="35ea4-157">**ulong –**</span><span class="sxs-lookup"><span data-stu-id="35ea4-157">**ulong**</span></span>|<span data-ttu-id="35ea4-158">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="35ea4-158">**UInt64**</span></span>|<span data-ttu-id="35ea4-159">**__int64 bez znaménka**</span><span class="sxs-lookup"><span data-stu-id="35ea4-159">**unsigned __int64**</span></span>|<span data-ttu-id="35ea4-160">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="35ea4-160">**UInt64**</span></span>|  
|<span data-ttu-id="35ea4-161">**plovoucí desetinná čárka**</span><span class="sxs-lookup"><span data-stu-id="35ea4-161">**float**</span></span>|<span data-ttu-id="35ea4-162">**Jeden**</span><span class="sxs-lookup"><span data-stu-id="35ea4-162">**Single**</span></span>|<span data-ttu-id="35ea4-163">**plovoucí desetinná čárka**</span><span class="sxs-lookup"><span data-stu-id="35ea4-163">**float**</span></span>|<span data-ttu-id="35ea4-164">**Jeden**</span><span class="sxs-lookup"><span data-stu-id="35ea4-164">**Single**</span></span>|  
|<span data-ttu-id="35ea4-165">**Double**</span><span class="sxs-lookup"><span data-stu-id="35ea4-165">**double**</span></span>|<span data-ttu-id="35ea4-166">**Double**</span><span class="sxs-lookup"><span data-stu-id="35ea4-166">**Double**</span></span>|<span data-ttu-id="35ea4-167">**Double**</span><span class="sxs-lookup"><span data-stu-id="35ea4-167">**double**</span></span>|<span data-ttu-id="35ea4-168">**Double**</span><span class="sxs-lookup"><span data-stu-id="35ea4-168">**Double**</span></span>|  
|<span data-ttu-id="35ea4-169">**BOOL**</span><span class="sxs-lookup"><span data-stu-id="35ea4-169">**bool**</span></span>|<span data-ttu-id="35ea4-170">**Logická hodnota**</span><span class="sxs-lookup"><span data-stu-id="35ea4-170">**Boolean**</span></span>|<span data-ttu-id="35ea4-171">**BOOL**</span><span class="sxs-lookup"><span data-stu-id="35ea4-171">**bool**</span></span>|<span data-ttu-id="35ea4-172">**Logická hodnota**</span><span class="sxs-lookup"><span data-stu-id="35ea4-172">**Boolean**</span></span>|  
|<span data-ttu-id="35ea4-173">**Char**</span><span class="sxs-lookup"><span data-stu-id="35ea4-173">**char**</span></span>|<span data-ttu-id="35ea4-174">**Char –**</span><span class="sxs-lookup"><span data-stu-id="35ea4-174">**Char**</span></span>|<span data-ttu-id="35ea4-175">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="35ea4-175">**wchar_t**</span></span>|<span data-ttu-id="35ea4-176">**Char –**</span><span class="sxs-lookup"><span data-stu-id="35ea4-176">**Char**</span></span>|  
|<span data-ttu-id="35ea4-177">**řetězec**</span><span class="sxs-lookup"><span data-stu-id="35ea4-177">**string**</span></span>|<span data-ttu-id="35ea4-178">**Řetězec**</span><span class="sxs-lookup"><span data-stu-id="35ea4-178">**String**</span></span>|<span data-ttu-id="35ea4-179">**Řetězec**</span><span class="sxs-lookup"><span data-stu-id="35ea4-179">**String**</span></span>|<span data-ttu-id="35ea4-180">**Řetězec**</span><span class="sxs-lookup"><span data-stu-id="35ea4-180">**String**</span></span>|  
|<span data-ttu-id="35ea4-181">**objekt**</span><span class="sxs-lookup"><span data-stu-id="35ea4-181">**object**</span></span>|<span data-ttu-id="35ea4-182">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="35ea4-182">**Object**</span></span>|<span data-ttu-id="35ea4-183">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="35ea4-183">**Object**</span></span>|<span data-ttu-id="35ea4-184">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="35ea4-184">**Object**</span></span>|  
  
 <span data-ttu-id="35ea4-185">**PROVEĎTE ✓** použít běžný název, například `value` nebo `item`, místo opakování název typu ve výjimečných případech, pokud identifikátor nemá žádný význam sémantického a typ parametru není důležité.</span><span class="sxs-lookup"><span data-stu-id="35ea4-185">**✓ DO**  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>  
  
## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="35ea4-186">Pojmenování nové verze stávajících rozhraní API</span><span class="sxs-lookup"><span data-stu-id="35ea4-186">Naming New Versions of Existing APIs</span></span>  
 <span data-ttu-id="35ea4-187">**PROVEĎTE ✓** použijte název podobná staré rozhraní API, při vytváření nové verze existujícího rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="35ea4-187">**✓ DO** use a name similar to the old API when creating new versions of an existing API.</span></span>  
  
 <span data-ttu-id="35ea4-188">To pomůže zvýrazněte vztah mezi rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="35ea4-188">This helps to highlight the relationship between the APIs.</span></span>  
  
 <span data-ttu-id="35ea4-189">**PROVEĎTE ✓** přednost přidání příponu místo předpony označující novou verzi existujícího rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="35ea4-189">**✓ DO** prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>  
  
 <span data-ttu-id="35ea4-190">To vám pomůže zjišťování při procházení dokumentace, nebo pomocí Intellisense.</span><span class="sxs-lookup"><span data-stu-id="35ea4-190">This will assist discovery when browsing documentation, or using Intellisense.</span></span> <span data-ttu-id="35ea4-191">Stará verze rozhraní API se uspořádají blízko nových rozhraní API, protože většina prohlížečů a Intellisense zobrazí identifikátory v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="35ea4-191">The old version of the API will be organized close to the new APIs, because most browsers and Intellisense show identifiers in alphabetical order.</span></span>  
  
 <span data-ttu-id="35ea4-192">**✓ ZVAŽTE** pomocí identifikátor úplně nový, ale smysluplný místo přidávání příponu nebo předponu.</span><span class="sxs-lookup"><span data-stu-id="35ea4-192">**✓ CONSIDER** using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>  
  
 <span data-ttu-id="35ea4-193">**PROVEĎTE ✓** používá číselnou příponou se k označení novou verzi existujícího rozhraní API, zvlášť pokud existující název rozhraní API je pouze název, který dává smysl (tj. Pokud je oborový standard) a Pokud Přidání všechny smysluplný přípony (nebo změna názvu) není aplikace možnost ropriate.</span><span class="sxs-lookup"><span data-stu-id="35ea4-193">**✓ DO** use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>  
  
 <span data-ttu-id="35ea4-194">**X nesmí** "Ex" (nebo podobná) používat příponu pro identifikátor ho odlišuje od dřívější verzi rozhraní API stejné.</span><span class="sxs-lookup"><span data-stu-id="35ea4-194">**X DO NOT** use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>  
  
 <span data-ttu-id="35ea4-195">**PROVEĎTE ✓** používají "64" příponu zaváděné verze rozhraní API, která pracovat 64bitové celé číslo (dlouhých celých čísel) namísto 32bitové celé číslo.</span><span class="sxs-lookup"><span data-stu-id="35ea4-195">**✓ DO** use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="35ea4-196">Potřebujete použít tuto metodu, pokud existuje existujícího rozhraní API 32-bit; nedělají nic pro nové rozhraní API s 64bitovou verzi.</span><span class="sxs-lookup"><span data-stu-id="35ea4-196">You only need to take this approach when the existing 32-bit API exists; don’t do it for brand new APIs with only a 64-bit version.</span></span>  
  
 <span data-ttu-id="35ea4-197">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="35ea4-197">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="35ea4-198">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="35ea4-198">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ea4-199">Viz také</span><span class="sxs-lookup"><span data-stu-id="35ea4-199">See Also</span></span>  
 [<span data-ttu-id="35ea4-200">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="35ea4-200">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="35ea4-201">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="35ea4-201">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
