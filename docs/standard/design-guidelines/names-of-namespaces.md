---
title: "Názvy oborů názvů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4fc0cb9183fde33887a3e84bb30cc3f79892586e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-namespaces"></a><span data-ttu-id="e5224-102">Názvy oborů názvů</span><span class="sxs-lookup"><span data-stu-id="e5224-102">Names of Namespaces</span></span>
<span data-ttu-id="e5224-103">Jako s další pokyny pro pojmenování, cílem obory názvů v názvu je vytvoření dostatečně jasně pro programátory pomocí rozhraní okamžitě vědět, co je pravděpodobné, že obsah oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e5224-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="e5224-104">Následující šablony určuje obecná pravidla pro názvy oborů názvů:</span><span class="sxs-lookup"><span data-stu-id="e5224-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="e5224-105">Následují příklady:</span><span class="sxs-lookup"><span data-stu-id="e5224-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="e5224-106">**PROVEĎTE ✓** předpony oboru názvů názvy s název společnosti, aby se zabránilo obory názvů v jiné společnosti z který má stejný název.</span><span class="sxs-lookup"><span data-stu-id="e5224-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="e5224-107">**PROVEĎTE ✓** použít název stabilní, nezávislé na verzi produktu, na druhé úrovni název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e5224-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="e5224-108">**X nesmí** používat organizační hierarchie jako základ pro názvy v oboru názvů hierarchií, protože názvy skupin v rámci společnosti jsou obvykle krátkodobou.</span><span class="sxs-lookup"><span data-stu-id="e5224-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="e5224-109">Uspořádejte hierarchie oborů názvů kolem skupiny souvisejících technologiích.</span><span class="sxs-lookup"><span data-stu-id="e5224-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="e5224-110">**PROVEĎTE ✓** PascalCasing a komponenty samostatného oboru názvů pomocí tečky (například `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="e5224-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="e5224-111">Pokud vaší značkou aktivuje netradičních velká a malá písmena, řiďte se malá a velká písmena definované vaší značkou, i v případě, že odchylují od normální obor názvů velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="e5224-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="e5224-112">**✓ ZVAŽTE** pomocí názvy v množném čísle obor názvů, kde je to vhodné.</span><span class="sxs-lookup"><span data-stu-id="e5224-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="e5224-113">Například použít `System.Collections` místo `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="e5224-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="e5224-114">Značky jména a zkratky jsou ale výjimky pro toto pravidlo.</span><span class="sxs-lookup"><span data-stu-id="e5224-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="e5224-115">Například použít `System.IO` místo `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="e5224-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="e5224-116">**X nesmí** používají stejný název pro obor názvů a typ v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e5224-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="e5224-117">Například nepoužívejte `Debug` jako obor názvů název a také poskytují třídy s názvem `Debug` ve stejném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e5224-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="e5224-118">Několik kompilátory vyžadují tyto typy jako plně kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="e5224-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="e5224-119">Obory názvů a typ konflikty názvů</span><span class="sxs-lookup"><span data-stu-id="e5224-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="e5224-120">**X nesmí** zavést názvy obecného typu, jako `Element`, `Node`, `Log`, a `Message`.</span><span class="sxs-lookup"><span data-stu-id="e5224-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="e5224-121">Je velmi vysoká pravděpodobnost, že povede k zadání názvu Pokud tak učiníte, je v konfliktu společné scénáře.</span><span class="sxs-lookup"><span data-stu-id="e5224-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="e5224-122">Použijte následující postup názvy obecného typu (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="e5224-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="e5224-123">Existují konkrétní pokyny pro vyhnutí se konfliktům název typu pro různé kategorie obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e5224-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
-   <span data-ttu-id="e5224-124">**Obory názvů model aplikace**</span><span class="sxs-lookup"><span data-stu-id="e5224-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="e5224-125">Obory názvů, které patří do jedné aplikace modelu se velmi často používají společně, ale používají se téměř žádné s obory názvů modelů jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5224-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="e5224-126">Například <xref:System.Windows.Forms?displayProperty=nameWithType> obor názvů je velmi málo používané společně s <xref:System.Web.UI?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e5224-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="e5224-127">Následuje seznam skupin obor názvů modelu dobře známé aplikací:</span><span class="sxs-lookup"><span data-stu-id="e5224-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="e5224-128">**X nesmí** předáte typy v oborech názvů v rámci jedné aplikace model se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="e5224-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="e5224-129">Například nepřidávejte typ s názvem `Page` k <xref:System.Web.UI.Adapters?displayProperty=nameWithType> obor názvů, protože <xref:System.Web.UI?displayProperty=nameWithType> obor názvů již obsahuje typ s názvem `Page`.</span><span class="sxs-lookup"><span data-stu-id="e5224-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
-   <span data-ttu-id="e5224-130">**Obory názvů infrastruktury**</span><span class="sxs-lookup"><span data-stu-id="e5224-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="e5224-131">Tato skupina obsahuje obory názvů, které importují zřídka během vývoje aplikace běžné.</span><span class="sxs-lookup"><span data-stu-id="e5224-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="e5224-132">Například `.Design` obory názvů se používá hlavně při vývoji programování nástroje.</span><span class="sxs-lookup"><span data-stu-id="e5224-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="e5224-133">Vyhnutí se konfliktům s typy v těchto oborů názvů není důležité.</span><span class="sxs-lookup"><span data-stu-id="e5224-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
-   <span data-ttu-id="e5224-134">**Obory názvů jádra**</span><span class="sxs-lookup"><span data-stu-id="e5224-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="e5224-135">Obory názvů základní zahrnout všechny `System` obory názvů, s výjimkou obory názvů modelů aplikace a infrastrukturu obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e5224-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="e5224-136">Obory názvů jádra, patří mimo jiné, `System`, `System.IO`, `System.Xml`, a `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="e5224-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="e5224-137">**X nesmí** udělení typy názvy, které by byl v konfliktu s žádným typem v oborech názvů jádra.</span><span class="sxs-lookup"><span data-stu-id="e5224-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="e5224-138">Například nikdy nepoužívejte `Stream` jako název typu.</span><span class="sxs-lookup"><span data-stu-id="e5224-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="e5224-139">By byl v konfliktu s <xref:System.IO.Stream?displayProperty=nameWithType>, velmi často používá typu.</span><span class="sxs-lookup"><span data-stu-id="e5224-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
-   <span data-ttu-id="e5224-140">**Obor názvů skupin technologie**</span><span class="sxs-lookup"><span data-stu-id="e5224-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="e5224-141">Tato kategorie zahrnuje všechny obory názvů se stejným první dva uzly obor názvů `(<Company>.<Technology>*`), jako například `Microsoft.Build.Utilities` a `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="e5224-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="e5224-142">Je důležité, aby typy, které patří do jedné technologie nedošlo ke konfliktu mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="e5224-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="e5224-143">**X nesmí** přiřadit názvy typů, které by byl v konfliktu s jinými typy v rámci jedné technologie.</span><span class="sxs-lookup"><span data-stu-id="e5224-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="e5224-144">**X nesmí** zavést typ konflikty v názvech mezi typy v oborech názvů technologii a na obor názvů modelu aplikace (Pokud je tato technologie není určena pro použití s modelem aplikace).</span><span class="sxs-lookup"><span data-stu-id="e5224-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="e5224-145">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="e5224-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e5224-146">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="e5224-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5224-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5224-147">See Also</span></span>  
 [<span data-ttu-id="e5224-148">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="e5224-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="e5224-149">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="e5224-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
