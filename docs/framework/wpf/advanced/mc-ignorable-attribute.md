---
title: mc:Ignorable – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: e8fa4c084ae9c775a18de06c344b2c0b439c2b1b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467812"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="aaddb-102">mc:Ignorable – atribut</span><span class="sxs-lookup"><span data-stu-id="aaddb-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="aaddb-103">Určuje, které [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] předpony oboru názvů v souboru označení může ignorovat. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru.</span><span class="sxs-lookup"><span data-stu-id="aaddb-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="aaddb-104">`mc:Ignorable` Atribut podporuje kompatibility značek pro vlastní obor názvů mapování a pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správy verzí.</span><span class="sxs-lookup"><span data-stu-id="aaddb-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="aaddb-105">Použití atributu XAML (jeden předpony)</span><span class="sxs-lookup"><span data-stu-id="aaddb-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="aaddb-106">Použití atributu XAML (dvě předpony)</span><span class="sxs-lookup"><span data-stu-id="aaddb-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="aaddb-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="aaddb-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aaddb-108">*ignorablePrefix ignorablePrefix1, atd.*</span><span class="sxs-lookup"><span data-stu-id="aaddb-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="aaddb-109">Libovolný platnou předponu řetězec podle specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="aaddb-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="aaddb-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="aaddb-110">*ignorableUri*</span></span>|<span data-ttu-id="aaddb-111">Libovolný platný identifikátor URI pro určení oboru názvů, podle specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="aaddb-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="aaddb-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="aaddb-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="aaddb-113">Element, který lze ignorovat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementace, pokud nadřazený typ není možné přeložit.</span><span class="sxs-lookup"><span data-stu-id="aaddb-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaddb-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aaddb-114">Remarks</span></span>  
 <span data-ttu-id="aaddb-115">`mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Předponu oboru názvů je předpona doporučené konvence pro použití při mapování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] oboru názvů kompatibility [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aaddb-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="aaddb-116">Elementy nebo atributy, kde předpona názvu elementu jsou označeny jako `mc:Ignorable` nebude vyvolat chyby při zpracování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru.</span><span class="sxs-lookup"><span data-stu-id="aaddb-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="aaddb-117">Pokud tento atribut nebylo možné přeložit na základní typ nebo programovací konstrukce, je tento prvek ignorován.</span><span class="sxs-lookup"><span data-stu-id="aaddb-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="aaddb-118">Upozorňujeme ale, ignorované prvků může být stále generovat další chyby analýzy pro další prvek požadavky, které jsou vedlejší účinky tohoto prvku není zpracována.</span><span class="sxs-lookup"><span data-stu-id="aaddb-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="aaddb-119">Například model obsahu konkrétní elementu může vyžadovat přesně jeden podřízený element, ale pokud byl zadaný podřízený element v `mc:Ignorable` předponu a zadaný podřízený element nebylo možné přeložit na typ, pak bude [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] může procesor vyvolat chyby.</span><span class="sxs-lookup"><span data-stu-id="aaddb-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="aaddb-120">`mc:Ignorable` platí jenom pro mapování názvového prostoru na identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="aaddb-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="aaddb-121">`mc:Ignorable` neplatí pro mapování názvového prostoru do sestavení, které určují [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obor názvů a sestavení (nebo výchozí aktuální spustitelného souboru jako sestavení).</span><span class="sxs-lookup"><span data-stu-id="aaddb-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="aaddb-122">Při implementaci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru, procesoru implementace nesmí vyvolat analýzu a zpracování chyb v rozlišení typů pro libovolný element nebo atribut, který je kvalifikována předponu, která je označena jako `mc:Ignorable`.</span><span class="sxs-lookup"><span data-stu-id="aaddb-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="aaddb-123">Ale implementace procesoru stále může vyvolat výjimky, které jsou výsledkem sekundární nedaří načíst nebo zpracovat, jako je například dříve uvedeného příkladu jeden podřízený element elementu.</span><span class="sxs-lookup"><span data-stu-id="aaddb-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="aaddb-124">Ve výchozím nastavení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor bude ignorovat obsah v rámci elementu ignorované.</span><span class="sxs-lookup"><span data-stu-id="aaddb-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="aaddb-125">Můžete však zadat atribut Další [MC: processcontent – atribut](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), trvalé zpracování obsahu v rámci elementu ignorované podle dalšího k dispozici nadřazený element.</span><span class="sxs-lookup"><span data-stu-id="aaddb-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="aaddb-126">Dá se zadat více předpony v atribut, pomocí jednoho nebo více prázdných znaků jako oddělovač, například: `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="aaddb-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="aaddb-127">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Obor názvů definuje další prvky a atributy, které nejsou uvedené v této oblasti [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aaddb-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="aaddb-128">Další informace najdete v tématu [specifikace kompatibility značek XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span><span class="sxs-lookup"><span data-stu-id="aaddb-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaddb-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="aaddb-129">See Also</span></span>  
 <xref:System.Windows.Markup.XamlReader>  
 [<span data-ttu-id="aaddb-130">PresentationOptions:Freeze – atribut</span><span class="sxs-lookup"><span data-stu-id="aaddb-130">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [<span data-ttu-id="aaddb-131">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="aaddb-131">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="aaddb-132">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="aaddb-132">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
