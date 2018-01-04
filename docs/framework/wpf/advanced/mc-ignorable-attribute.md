---
title: "mc:Ignorable – atribut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9767b721321b34030a2f276a90c618c658645207
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="500b3-102">mc:Ignorable – atribut</span><span class="sxs-lookup"><span data-stu-id="500b3-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="500b3-103">Určuje, které [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] předpony oboru názvů v souboru kódu může být ignorována [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru.</span><span class="sxs-lookup"><span data-stu-id="500b3-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="500b3-104">`mc:Ignorable` Podporuje atribut kompatibility značek pro vlastní obor názvů mapování i pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správy verzí.</span><span class="sxs-lookup"><span data-stu-id="500b3-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="500b3-105">Použití atributu XAML (jednu předponu)</span><span class="sxs-lookup"><span data-stu-id="500b3-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="500b3-106">Použití atributu XAML (dvě předpony)</span><span class="sxs-lookup"><span data-stu-id="500b3-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="500b3-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="500b3-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="500b3-108">*ignorablePrefix, ignorablePrefix1, atd.*</span><span class="sxs-lookup"><span data-stu-id="500b3-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="500b3-109">Všechny platnou předponu řetězec podle specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="500b3-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="500b3-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="500b3-110">*ignorableUri*</span></span>|<span data-ttu-id="500b3-111">Všechny platný identifikátor URI pro určení oboru názvů podle specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="500b3-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="500b3-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="500b3-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="500b3-113">Element, který můžete ignorovat podle [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementace zpracovatelů, pokud základní typ nelze přeložit.</span><span class="sxs-lookup"><span data-stu-id="500b3-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="500b3-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="500b3-114">Remarks</span></span>  
 <span data-ttu-id="500b3-115">`mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Předponu oboru názvů je doporučené předponu konvence pro použití při mapování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obor názvů kompatibility [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="500b3-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="500b3-116">Elementy nebo atributy, kde jsou předpony část název elementu označeny jako `mc:Ignorable` nevydá chyby při zpracování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru.</span><span class="sxs-lookup"><span data-stu-id="500b3-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="500b3-117">Pokud tento atribut nelze přeložit na základní typ nebo programovací konstrukce, že element ignorován.</span><span class="sxs-lookup"><span data-stu-id="500b3-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="500b3-118">Pozor ale ignoruje elementy může generovat stále další chyby analyzátoru element další požadavky, které jsou vedlejší účinky tohoto prvku nejsou zpracována.</span><span class="sxs-lookup"><span data-stu-id="500b3-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="500b3-119">Model obsahu určitý element může například vyžadovat přesně jeden podřízený element, ale pokud byl zadaný podřízený element v `mc:Ignorable` předponu a zadaný podřízený element nebylo možné přeložit na typ, pak se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] může procesoru vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="500b3-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="500b3-120">`mc:Ignorable`platí jenom pro mapování oboru názvů na identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="500b3-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="500b3-121">`mc:Ignorable`nelze použít u mapování oboru názvů do sestavení, které určují [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obor názvů a sestavení (nebo výchozí nastavení aktuální spustitelného souboru jako sestavení).</span><span class="sxs-lookup"><span data-stu-id="500b3-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="500b3-122">Pokud implementujete [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru, implementaci procesoru nesmí vyvolat analýza nebo zpracování chyb v řešení typu pro element nebo atribut, který je kvalifikován předponu, která je označena jako `mc:Ignorable`.</span><span class="sxs-lookup"><span data-stu-id="500b3-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="500b3-123">Ale implementaci procesoru může být stále spojeno výjimky, které jsou výsledkem sekundární elementu nedaří se načíst nebo zpracovat, jako je například jeden podřízený element zadána dříve.</span><span class="sxs-lookup"><span data-stu-id="500b3-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="500b3-124">Ve výchozím nastavení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru bude ignorovat obsahu v rámci elementu ignorováno.</span><span class="sxs-lookup"><span data-stu-id="500b3-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="500b3-125">Můžete však zadat atribut Další [mc:ProcessContent atribut](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), trvalá zpracování obsahu v rámci elementu ignorováno další dostupné nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="500b3-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="500b3-126">V atributu, například pomocí jednoho nebo více znaky prázdné znaky jako oddělovače, lze zadat více předpony: `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="500b3-126">Multiple prefixes can be specified in the attribute, using one or more whitespace characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  
  
 <span data-ttu-id="500b3-127">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Definuje obor názvů další elementy a atributy, které nejsou popsané v této oblasti [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="500b3-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="500b3-128">Další informace najdete v tématu [specifikace kompatibility značek XML](http://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="500b3-128">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="500b3-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="500b3-129">See Also</span></span>  
 <xref:System.Windows.Markup.XamlReader>  
 [<span data-ttu-id="500b3-130">PresentationOptions:Freeze – atribut</span><span class="sxs-lookup"><span data-stu-id="500b3-130">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [<span data-ttu-id="500b3-131">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="500b3-131">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="500b3-132">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="500b3-132">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
