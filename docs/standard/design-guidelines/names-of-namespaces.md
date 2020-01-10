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
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709228"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="7ce55-102">Názvy oborů názvů</span><span class="sxs-lookup"><span data-stu-id="7ce55-102">Names of Namespaces</span></span>
<span data-ttu-id="7ce55-103">Stejně jako u jiných pokynů pro pojmenování je cílem při pojmenovávání oborů názvů vytváření dostatečné srozumitelnosti pro programátora pomocí rozhraní, aby okamžitě věděli, co může být obsah oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7ce55-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="7ce55-104">Následující šablona určuje obecné pravidlo pro názvové obory názvů:</span><span class="sxs-lookup"><span data-stu-id="7ce55-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="7ce55-105">Zde jsou příklady:</span><span class="sxs-lookup"><span data-stu-id="7ce55-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="7ce55-106">**✓ DO** předpony oboru názvů názvy s název společnosti, aby se zabránilo obory názvů v jiné společnosti z který má stejný název.</span><span class="sxs-lookup"><span data-stu-id="7ce55-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="7ce55-107">**✓ DO** použít název stabilní, nezávislé na verzi produktu, na druhé úrovni název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7ce55-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="7ce55-108">**X DO NOT** používat organizační hierarchie jako základ pro názvy v oboru názvů hierarchií, protože názvy skupin v rámci společnosti jsou obvykle krátkodobou.</span><span class="sxs-lookup"><span data-stu-id="7ce55-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="7ce55-109">Uspořádejte hierarchii oborů názvů kolem skupin souvisejících technologií.</span><span class="sxs-lookup"><span data-stu-id="7ce55-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="7ce55-110">**✓ DO** PascalCasing a komponenty samostatného oboru názvů pomocí tečky (například `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="7ce55-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="7ce55-111">Pokud vaše značka používá netradiční velikost písmen, měli byste postupovat podle velkých a malých písmen definovaných vaší značkou, a to i v případě, že se liší od normálního velikosti oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7ce55-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="7ce55-112">**✓ CONSIDER** pomocí názvy v množném čísle obor názvů, kde je to vhodné.</span><span class="sxs-lookup"><span data-stu-id="7ce55-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="7ce55-113">Použijte například `System.Collections` místo `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="7ce55-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="7ce55-114">Názvy značek a akronymy jsou však výjimkou tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="7ce55-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="7ce55-115">Použijte například `System.IO` místo `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="7ce55-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="7ce55-116">**X DO NOT** používají stejný název pro obor názvů a typ v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7ce55-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="7ce55-117">Nepoužívejte například `Debug` jako název oboru názvů a potom zadejte třídu s názvem `Debug` ve stejném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7ce55-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="7ce55-118">Několik kompilátorů vyžaduje, aby tyto typy byly plně kvalifikované.</span><span class="sxs-lookup"><span data-stu-id="7ce55-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="7ce55-119">Konflikty oborů názvů a typů</span><span class="sxs-lookup"><span data-stu-id="7ce55-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="7ce55-120">**X DO NOT** zavést názvy obecného typu, jako `Element`, `Node`, `Log`, a `Message`.</span><span class="sxs-lookup"><span data-stu-id="7ce55-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="7ce55-121">Existuje velmi vysoká pravděpodobnost, že by to mělo způsobit konflikty názvů typů v běžných scénářích.</span><span class="sxs-lookup"><span data-stu-id="7ce55-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="7ce55-122">Měli byste kvalifikovat názvy obecných typů (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="7ce55-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="7ce55-123">Existují konkrétní pokyny pro předcházení konfliktům názvů typů pro různé kategorie oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="7ce55-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
- <span data-ttu-id="7ce55-124">**Obory názvů aplikačního modelu**</span><span class="sxs-lookup"><span data-stu-id="7ce55-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="7ce55-125">Obory názvů patřící k jednomu aplikačnímu modelu se velmi často používají společně, ale nejsou skoro nikdy použity s obory názvů jiných modelů aplikací.</span><span class="sxs-lookup"><span data-stu-id="7ce55-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="7ce55-126">Například obor názvů <xref:System.Windows.Forms?displayProperty=nameWithType> je velmi zřídka používán společně s oborem názvů <xref:System.Web.UI?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ce55-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="7ce55-127">Následuje seznam známých skupin oborů názvů aplikačního modelu:</span><span class="sxs-lookup"><span data-stu-id="7ce55-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="7ce55-128">**X DO NOT** předáte typy v oborech názvů v rámci jedné aplikace model se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="7ce55-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="7ce55-129">Nepřidejte například typ s názvem `Page` do <xref:System.Web.UI.Adapters?displayProperty=nameWithType> oboru názvů, protože <xref:System.Web.UI?displayProperty=nameWithType> obor názvů již obsahuje typ s názvem `Page`.</span><span class="sxs-lookup"><span data-stu-id="7ce55-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
- <span data-ttu-id="7ce55-130">**Obory názvů infrastruktury**</span><span class="sxs-lookup"><span data-stu-id="7ce55-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="7ce55-131">Tato skupina obsahuje obory názvů, které se při vývoji běžných aplikací importují zřídka.</span><span class="sxs-lookup"><span data-stu-id="7ce55-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="7ce55-132">Například `.Design` obory názvů se používají hlavně při vývoji programovacích nástrojů.</span><span class="sxs-lookup"><span data-stu-id="7ce55-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="7ce55-133">Předcházení konfliktům s typy v těchto oborech názvů není důležité.</span><span class="sxs-lookup"><span data-stu-id="7ce55-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
- <span data-ttu-id="7ce55-134">**Základní obory názvů**</span><span class="sxs-lookup"><span data-stu-id="7ce55-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="7ce55-135">Klíčové obory názvů zahrnují všechny obory názvů `System` s výjimkou oborů názvů modelů aplikací a oborů názvů infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="7ce55-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="7ce55-136">Mezi základní obory názvů patří mimo jiné `System`, `System.IO`, `System.Xml`a `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="7ce55-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="7ce55-137">**X DO NOT** udělení typy názvy, které by byl v konfliktu s žádným typem v oborech názvů jádra.</span><span class="sxs-lookup"><span data-stu-id="7ce55-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="7ce55-138">Například nikdy nepoužívejte `Stream` jako název typu.</span><span class="sxs-lookup"><span data-stu-id="7ce55-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="7ce55-139">Je v konfliktu s <xref:System.IO.Stream?displayProperty=nameWithType>, často používaným typem.</span><span class="sxs-lookup"><span data-stu-id="7ce55-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
- <span data-ttu-id="7ce55-140">**Skupiny oboru názvů technologií**</span><span class="sxs-lookup"><span data-stu-id="7ce55-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="7ce55-141">Tato kategorie zahrnuje všechny obory názvů se stejnými prvními dvěma uzly oboru názvů `(<Company>.<Technology>*`), například `Microsoft.Build.Utilities` a `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="7ce55-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="7ce55-142">Je důležité, aby typy patřící do jedné technologie nebyly vzájemně v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="7ce55-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="7ce55-143">**X DO NOT** přiřadit názvy typů, které by byl v konfliktu s jinými typy v rámci jedné technologie.</span><span class="sxs-lookup"><span data-stu-id="7ce55-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="7ce55-144">**X DO NOT** zavést typ konflikty v názvech mezi typy v oborech názvů technologii a na obor názvů modelu aplikace (Pokud je tato technologie není určena pro použití s modelem aplikace).</span><span class="sxs-lookup"><span data-stu-id="7ce55-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="7ce55-145">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="7ce55-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7ce55-146">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="7ce55-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce55-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ce55-147">See also</span></span>

- [<span data-ttu-id="7ce55-148">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="7ce55-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="7ce55-149">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="7ce55-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
