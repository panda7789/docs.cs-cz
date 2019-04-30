---
title: Názvy oborů názvů
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
author: KrzysztofCwalina
ms.openlocfilehash: 0099c5c8a863023099b377e139461606de3e1e1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940982"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="5466c-102">Názvy oborů názvů</span><span class="sxs-lookup"><span data-stu-id="5466c-102">Names of Namespaces</span></span>
<span data-ttu-id="5466c-103">Jako s další pokyny pro pojmenování, cílem při pojmenování obory názvů vytváří dostatečná přehlednost pro programátora pomocí rozhraní hned vědět, co je pravděpodobné, že obsah oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5466c-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="5466c-104">Následující šablony určuje obecné pravidlo pro pojmenování obory názvů:</span><span class="sxs-lookup"><span data-stu-id="5466c-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="5466c-105">Následují příklady:</span><span class="sxs-lookup"><span data-stu-id="5466c-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="5466c-106">**✓ DO** předpony oboru názvů názvy s název společnosti, aby se zabránilo obory názvů v jiné společnosti z který má stejný název.</span><span class="sxs-lookup"><span data-stu-id="5466c-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="5466c-107">**✓ DO** použít název stabilní, nezávislé na verzi produktu, na druhé úrovni název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5466c-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="5466c-108">**X DO NOT** používat organizační hierarchie jako základ pro názvy v oboru názvů hierarchií, protože názvy skupin v rámci společnosti jsou obvykle krátkodobou.</span><span class="sxs-lookup"><span data-stu-id="5466c-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="5466c-109">Uspořádání hierarchie oborů názvů okolo skupin souvisejících technologiích.</span><span class="sxs-lookup"><span data-stu-id="5466c-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="5466c-110">**✓ DO** PascalCasing a komponenty samostatného oboru názvů pomocí tečky (například `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="5466c-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="5466c-111">Pokud vlastní značky využívá netradičních velká a malá písmena, postupujte i v případě, že odchylují od malých a velkých písmen normální obor názvů malých a velkých písmen definované vlastní značky.</span><span class="sxs-lookup"><span data-stu-id="5466c-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="5466c-112">**✓ CONSIDER** pomocí názvy v množném čísle obor názvů, kde je to vhodné.</span><span class="sxs-lookup"><span data-stu-id="5466c-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="5466c-113">Například použít `System.Collections` místo `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="5466c-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="5466c-114">Názvy a zkratky jsou však výjimkou tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="5466c-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="5466c-115">Například použít `System.IO` místo `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="5466c-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="5466c-116">**X DO NOT** používají stejný název pro obor názvů a typ v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5466c-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="5466c-117">Například nepoužívejte `Debug` jako obor názvů pojmenujte a také zadat třídu s názvem `Debug` ve stejném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5466c-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="5466c-118">Několik kompilátory vyžadují tyto typy jako plně kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="5466c-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="5466c-119">Obory názvů a typ název je v konfliktu</span><span class="sxs-lookup"><span data-stu-id="5466c-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="5466c-120">**X DO NOT** zavést názvy obecného typu, jako `Element`, `Node`, `Log`, a `Message`.</span><span class="sxs-lookup"><span data-stu-id="5466c-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="5466c-121">Je velmi vysoká pravděpodobnost, že díky tomu povede k zadání názvu je v konfliktu v běžných scénářích.</span><span class="sxs-lookup"><span data-stu-id="5466c-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="5466c-122">By měl kvalifikovat názvy obecných typů (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="5466c-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="5466c-123">Existují konkrétní pokyny ke vyhnutí se konfliktům název typu pro různé kategorie oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="5466c-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
- <span data-ttu-id="5466c-124">**Obory názvů modelu aplikace**</span><span class="sxs-lookup"><span data-stu-id="5466c-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="5466c-125">Obory názvů, které patří do jedné aplikační model se často používají společně, ale jsou téměř nikdy používat s obory názvů modelů jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="5466c-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="5466c-126">Například <xref:System.Windows.Forms?displayProperty=nameWithType> obor názvů je velmi zřídka použít v kombinaci s <xref:System.Web.UI?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5466c-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="5466c-127">Následuje seznam známých aplikaci modelu obor názvů skupin:</span><span class="sxs-lookup"><span data-stu-id="5466c-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="5466c-128">**X DO NOT** předáte typy v oborech názvů v rámci jedné aplikace model se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="5466c-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="5466c-129">Například nepřidávejte typ s názvem `Page` k <xref:System.Web.UI.Adapters?displayProperty=nameWithType> obor názvů, protože <xref:System.Web.UI?displayProperty=nameWithType> již obsahuje typ s názvem oboru názvů `Page`.</span><span class="sxs-lookup"><span data-stu-id="5466c-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
- <span data-ttu-id="5466c-130">**Obory názvů infrastruktury**</span><span class="sxs-lookup"><span data-stu-id="5466c-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="5466c-131">Tato skupina obsahuje obory názvů, které se importují jen zřídka během vývoje běžných aplikací.</span><span class="sxs-lookup"><span data-stu-id="5466c-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="5466c-132">Například `.Design` oborů názvů se používá hlavně při vývoji programovacích nástrojů.</span><span class="sxs-lookup"><span data-stu-id="5466c-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="5466c-133">Vyhnutí se konfliktům s typy v těchto oborech názvů není důležité.</span><span class="sxs-lookup"><span data-stu-id="5466c-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
- <span data-ttu-id="5466c-134">**Obory názvů jádra**</span><span class="sxs-lookup"><span data-stu-id="5466c-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="5466c-135">Základní oborů názvů patří všechny `System` obory názvů, s výjimkou obory názvů modelů aplikací a infrastruktury obory názvů.</span><span class="sxs-lookup"><span data-stu-id="5466c-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="5466c-136">Obory názvů Core patří mimo jiné `System`, `System.IO`, `System.Xml`, a `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="5466c-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="5466c-137">**X DO NOT** udělení typy názvy, které by byl v konfliktu s žádným typem v oborech názvů jádra.</span><span class="sxs-lookup"><span data-stu-id="5466c-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="5466c-138">Například nikdy nepoužívejte `Stream` jako název typu.</span><span class="sxs-lookup"><span data-stu-id="5466c-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="5466c-139">By byla v konfliktu s <xref:System.IO.Stream?displayProperty=nameWithType>, velmi často používána typu.</span><span class="sxs-lookup"><span data-stu-id="5466c-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
- <span data-ttu-id="5466c-140">**Obor názvů skupin technologie**</span><span class="sxs-lookup"><span data-stu-id="5466c-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="5466c-141">Tato kategorie zahrnuje všechny obory názvů se stejným první dva uzly oboru názvů `(<Company>.<Technology>*`), jako například `Microsoft.Build.Utilities` a `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="5466c-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="5466c-142">Je důležité, že typy, které patří do jedné technologie nejsou v konfliktu mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="5466c-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="5466c-143">**X DO NOT** přiřadit názvy typů, které by byl v konfliktu s jinými typy v rámci jedné technologie.</span><span class="sxs-lookup"><span data-stu-id="5466c-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="5466c-144">**X DO NOT** zavést typ konflikty v názvech mezi typy v oborech názvů technologii a na obor názvů modelu aplikace (Pokud je tato technologie není určena pro použití s modelem aplikace).</span><span class="sxs-lookup"><span data-stu-id="5466c-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="5466c-145">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="5466c-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5466c-146">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="5466c-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5466c-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5466c-147">See also</span></span>

- [<span data-ttu-id="5466c-148">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="5466c-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="5466c-149">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="5466c-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
