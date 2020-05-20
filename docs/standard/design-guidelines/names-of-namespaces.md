---
title: Názvy oborů názvů
description: Tyto pokyny slouží k vytváření názvů oborů názvů jako součást pokynů pro navrhování knihoven, které rozšíří a komunikují s knihovnami .NET.
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 0ad98af240cf8d1041d6a8b64ab71a56e763f76f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419054"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="ea183-103">Názvy oborů názvů</span><span class="sxs-lookup"><span data-stu-id="ea183-103">Names of Namespaces</span></span>
<span data-ttu-id="ea183-104">Stejně jako u jiných pokynů pro pojmenování je cílem při pojmenovávání oborů názvů vytváření dostatečné srozumitelnosti pro programátora pomocí rozhraní, aby okamžitě věděli, co může být obsah oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ea183-104">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="ea183-105">Následující šablona určuje obecné pravidlo pro názvové obory názvů:</span><span class="sxs-lookup"><span data-stu-id="ea183-105">The following template specifies the general rule for naming namespaces:</span></span>

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 <span data-ttu-id="ea183-106">Tady jsou příklady:</span><span class="sxs-lookup"><span data-stu-id="ea183-106">The following are examples:</span></span>

 <span data-ttu-id="ea183-107">`Fabrikam.Math` `Litware.Security`</span><span class="sxs-lookup"><span data-stu-id="ea183-107">`Fabrikam.Math` `Litware.Security`</span></span>

 <span data-ttu-id="ea183-108">✔️ DĚLAT předpony názvů oborů názvů s názvem společnosti, aby názvy oborů názvů z různých společností nemusely mít stejný název.</span><span class="sxs-lookup"><span data-stu-id="ea183-108">✔️ DO prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>

 <span data-ttu-id="ea183-109">✔️ použít stabilní název produktu nezávislý na verzi na druhé úrovni názvu oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ea183-109">✔️ DO use a stable, version-independent product name at the second level of a namespace name.</span></span>

 <span data-ttu-id="ea183-110">❌Nepoužívejte hierarchie organizace jako základ názvů v hierarchiích oboru názvů, protože názvy skupin v rámci společnosti mají být krátkodobé.</span><span class="sxs-lookup"><span data-stu-id="ea183-110">❌ DO NOT use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="ea183-111">Uspořádejte hierarchii oborů názvů kolem skupin souvisejících technologií.</span><span class="sxs-lookup"><span data-stu-id="ea183-111">Organize the hierarchy of namespaces around groups of related technologies.</span></span>

 <span data-ttu-id="ea183-112">✔️ použít PascalCasing a samostatné komponenty oboru názvů s tečkami (například `Microsoft.Office.PowerPoint` ).</span><span class="sxs-lookup"><span data-stu-id="ea183-112">✔️ DO use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="ea183-113">Pokud vaše značka používá netradiční velikost písmen, měli byste postupovat podle velkých a malých písmen definovaných vaší značkou, a to i v případě, že se liší od normálního velikosti oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ea183-113">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>

 <span data-ttu-id="ea183-114">v případě potřeby ✔️ ZVÁŽIT použití názvů v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="ea183-114">✔️ CONSIDER using plural namespace names where appropriate.</span></span>

 <span data-ttu-id="ea183-115">Můžete například namísto `System.Collections` použít `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="ea183-115">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="ea183-116">Názvy značek a akronymy jsou však výjimkou tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="ea183-116">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="ea183-117">Můžete například namísto `System.IO` použít `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="ea183-117">For example, use `System.IO` instead of `System.IOs`.</span></span>

 <span data-ttu-id="ea183-118">❌Nepoužívejte stejný název pro obor názvů a typ v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ea183-118">❌ DO NOT use the same name for a namespace and a type in that namespace.</span></span>

 <span data-ttu-id="ea183-119">Například Nepoužívejte `Debug` jako název oboru názvů a pak také poskytněte třídu s názvem `Debug` ve stejném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ea183-119">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="ea183-120">Několik kompilátorů vyžaduje, aby tyto typy byly plně kvalifikované.</span><span class="sxs-lookup"><span data-stu-id="ea183-120">Several compilers require such types to be fully qualified.</span></span>

### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="ea183-121">Konflikty oborů názvů a typů</span><span class="sxs-lookup"><span data-stu-id="ea183-121">Namespaces and Type Name Conflicts</span></span>
 <span data-ttu-id="ea183-122">❌Neveďte názvy obecných typů `Element` , například, `Node` , `Log` a `Message` .</span><span class="sxs-lookup"><span data-stu-id="ea183-122">❌ DO NOT introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>

 <span data-ttu-id="ea183-123">Existuje velmi vysoká pravděpodobnost, že by to mělo způsobit konflikty názvů typů v běžných scénářích.</span><span class="sxs-lookup"><span data-stu-id="ea183-123">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="ea183-124">Měli byste kvalifikovat názvy obecných typů ( `FormElement` , `XmlNode` , `EventLog` , `SoapMessage` ).</span><span class="sxs-lookup"><span data-stu-id="ea183-124">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>

 <span data-ttu-id="ea183-125">Existují konkrétní pokyny pro předcházení konfliktům názvů typů pro různé kategorie oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="ea183-125">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>

- <span data-ttu-id="ea183-126">**Obory názvů aplikačního modelu**</span><span class="sxs-lookup"><span data-stu-id="ea183-126">**Application model namespaces**</span></span>

     <span data-ttu-id="ea183-127">Obory názvů patřící k jednomu aplikačnímu modelu se velmi často používají společně, ale nejsou skoro nikdy použity s obory názvů jiných modelů aplikací.</span><span class="sxs-lookup"><span data-stu-id="ea183-127">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="ea183-128">Například <xref:System.Windows.Forms?displayProperty=nameWithType> obor názvů je velmi zřídka používán společně s <xref:System.Web.UI?displayProperty=nameWithType> oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="ea183-128">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ea183-129">Následuje seznam známých skupin oborů názvů aplikačního modelu:</span><span class="sxs-lookup"><span data-stu-id="ea183-129">The following is a list of well-known application model namespace groups:</span></span>

     <span data-ttu-id="ea183-130">`System.Windows*` `System.Web.UI*`</span><span class="sxs-lookup"><span data-stu-id="ea183-130">`System.Windows*` `System.Web.UI*`</span></span>

     <span data-ttu-id="ea183-131">❌Nedávejte stejný název typům v oborech názvů v rámci jednoho aplikačního modelu.</span><span class="sxs-lookup"><span data-stu-id="ea183-131">❌ DO NOT give the same name to types in namespaces within a single application model.</span></span>

     <span data-ttu-id="ea183-132">Nepřidejte například typ s názvem `Page` do <xref:System.Web.UI.Adapters?displayProperty=nameWithType> oboru názvů, protože <xref:System.Web.UI?displayProperty=nameWithType> obor názvů již obsahuje typ s názvem `Page` .</span><span class="sxs-lookup"><span data-stu-id="ea183-132">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>

- <span data-ttu-id="ea183-133">**Obory názvů infrastruktury**</span><span class="sxs-lookup"><span data-stu-id="ea183-133">**Infrastructure namespaces**</span></span>

     <span data-ttu-id="ea183-134">Tato skupina obsahuje obory názvů, které se při vývoji běžných aplikací importují zřídka.</span><span class="sxs-lookup"><span data-stu-id="ea183-134">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="ea183-135">Například `.Design` obory názvů se používají hlavně při vývoji programovacích nástrojů.</span><span class="sxs-lookup"><span data-stu-id="ea183-135">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="ea183-136">Předcházení konfliktům s typy v těchto oborech názvů není důležité.</span><span class="sxs-lookup"><span data-stu-id="ea183-136">Avoiding conflicts with types in these namespaces is not critical.</span></span>

- <span data-ttu-id="ea183-137">**Základní obory názvů**</span><span class="sxs-lookup"><span data-stu-id="ea183-137">**Core namespaces**</span></span>

     <span data-ttu-id="ea183-138">Klíčové obory názvů zahrnují všechny `System` obory názvů kromě oborů názvů modelů aplikací a oborů názvů infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="ea183-138">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="ea183-139">Mezi základní obory názvů patří mimo jiné,,, `System` `System.IO` `System.Xml` a `System.Net` .</span><span class="sxs-lookup"><span data-stu-id="ea183-139">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>

     <span data-ttu-id="ea183-140">❌Nezadávejte názvy typů, které by mohly být v konfliktu s jakýmkoli typem v základních oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="ea183-140">❌ DO NOT give types names that would conflict with any type in the Core namespaces.</span></span>

     <span data-ttu-id="ea183-141">Například nikdy nepoužívejte `Stream` jako název typu.</span><span class="sxs-lookup"><span data-stu-id="ea183-141">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="ea183-142">Je v konfliktu s <xref:System.IO.Stream?displayProperty=nameWithType> , nejčastěji používaným typem.</span><span class="sxs-lookup"><span data-stu-id="ea183-142">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>

- <span data-ttu-id="ea183-143">**Skupiny oboru názvů technologií**</span><span class="sxs-lookup"><span data-stu-id="ea183-143">**Technology namespace groups**</span></span>

     <span data-ttu-id="ea183-144">Tato kategorie zahrnuje všechny obory názvů se stejnými prvními dvěma uzly oboru názvů `(<Company>.<Technology>*` , například `Microsoft.Build.Utilities` a `Microsoft.Build.Tasks` .</span><span class="sxs-lookup"><span data-stu-id="ea183-144">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="ea183-145">Je důležité, aby typy patřící do jedné technologie nebyly vzájemně v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="ea183-145">It is important that types belonging to a single technology do not conflict with each other.</span></span>

     <span data-ttu-id="ea183-146">❌Nepřiřazujte názvy typů, které by mohly být v konfliktu s jinými typy v rámci jedné technologie.</span><span class="sxs-lookup"><span data-stu-id="ea183-146">❌ DO NOT assign type names that would conflict with other types within a single technology.</span></span>

     <span data-ttu-id="ea183-147">❌Nezavádí konflikty názvů typů mezi typy v oborech názvů technologie a oborem názvů aplikačního modelu (Pokud technologie není určena pro použití s modelem aplikace).</span><span class="sxs-lookup"><span data-stu-id="ea183-147">❌ DO NOT introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>

 <span data-ttu-id="ea183-148">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="ea183-148">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ea183-149">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="ea183-149">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ea183-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea183-150">See also</span></span>

- [<span data-ttu-id="ea183-151">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="ea183-151">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ea183-152">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="ea183-152">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
