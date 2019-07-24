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
ms.openlocfilehash: 40c1a8513608728a84b6b605f9ad18603123ea2e
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401529"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="96e23-102">mc:Ignorable – atribut</span><span class="sxs-lookup"><span data-stu-id="96e23-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="96e23-103">Určuje, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] které předpony oboru názvů, které se vyskytují v souboru označení, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] může procesor ignorovat.</span><span class="sxs-lookup"><span data-stu-id="96e23-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="96e23-104">Atribut podporuje kompatibilitu značek pro vlastní mapování oboru názvů a pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správu verzí. `mc:Ignorable`</span><span class="sxs-lookup"><span data-stu-id="96e23-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="96e23-105">Použití atributu XAML (jedna předpona)</span><span class="sxs-lookup"><span data-stu-id="96e23-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="96e23-106">Použití atributu XAML (dvě předpony)</span><span class="sxs-lookup"><span data-stu-id="96e23-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="96e23-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="96e23-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="96e23-108">*ignorablePrefix, ignorablePrefix1 atd.*</span><span class="sxs-lookup"><span data-stu-id="96e23-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="96e23-109">Libovolný platný řetězec předpony podle specifikace XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="96e23-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="96e23-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="96e23-110">*ignorableUri*</span></span>|<span data-ttu-id="96e23-111">Libovolný platný identifikátor URI pro určení oboru názvů podle specifikace XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="96e23-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="96e23-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="96e23-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="96e23-113">Element, který může být ignorován [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementacemi procesoru, pokud nelze přeložit nadřízený typ.</span><span class="sxs-lookup"><span data-stu-id="96e23-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96e23-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96e23-114">Remarks</span></span>  
 <span data-ttu-id="96e23-115">Předpona [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]oborunázvůje doporučená konvence předpony, která se použije při mapování oboru názvů kompatibility. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] `mc`</span><span class="sxs-lookup"><span data-stu-id="96e23-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="96e23-116">Prvky nebo atributy, u kterých je předpona části názvu elementu identifikována `mc:Ignorable` jako nevyvolává chyby při zpracování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesorem.</span><span class="sxs-lookup"><span data-stu-id="96e23-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="96e23-117">Pokud tento atribut nelze přeložit na nadřízený typ nebo konstruktor programování, je tento prvek ignorován.</span><span class="sxs-lookup"><span data-stu-id="96e23-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="96e23-118">Upozorňujeme však, že ignorované prvky mohou stále generovat další chyby analýzy pro další požadavky na prvky, které jsou vedlejšími účinky tohoto prvku nezpracovávány.</span><span class="sxs-lookup"><span data-stu-id="96e23-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="96e23-119">Například určitý model obsahu elementu může vyžadovat přesně jeden podřízený element, ale pokud zadaný podřízený element byl v `mc:Ignorable` předponě a zadaný podřízený element nelze přeložit na typ, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pak procesor může vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="96e23-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="96e23-120">`mc:Ignorable`vztahuje se pouze na mapování oboru názvů na řetězce identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="96e23-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="96e23-121">`mc:Ignorable`neplatí pro mapování oboru názvů na sestavení, která určují obor názvů CLR a sestavení (nebo výchozí hodnotu pro aktuální spustitelný soubor jako sestavení).</span><span class="sxs-lookup"><span data-stu-id="96e23-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a CLR namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="96e23-122">Pokud implementujete [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor, implementace procesoru nesmí vyvolat analýzu nebo zpracování chyb v rozlišení typu pro libovolný element nebo atribut, který je kvalifikován předponou, která je identifikována jako `mc:Ignorable`.</span><span class="sxs-lookup"><span data-stu-id="96e23-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="96e23-123">Ale vaše implementace procesoru stále může vyvolávat výjimky, které jsou druhotným výsledkem selhání elementu, který se nedaří načíst nebo zpracovat, jako je například příklad prvku s jedním podřízeným objektem uvedeným dříve.</span><span class="sxs-lookup"><span data-stu-id="96e23-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="96e23-124">Ve výchozím nastavení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bude procesor ignorovat obsah v rámci ignorovaného prvku.</span><span class="sxs-lookup"><span data-stu-id="96e23-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="96e23-125">Můžete však zadat další atribut, [MC: ProcessContent atribut](mc-processcontent-attribute.md), aby bylo možné pokračovat ve zpracování obsahu v rámci ignorovaného prvku následujícím dostupným nadřazeným elementem.</span><span class="sxs-lookup"><span data-stu-id="96e23-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="96e23-126">V atributu lze zadat více předpon, přičemž jako oddělovač použijte jeden nebo více prázdných znaků, například: `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="96e23-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="96e23-127">Obor názvů definuje jiné prvky a atributy, které nejsou zdokumentovány v této oblasti [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96e23-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="96e23-128">Další informace najdete v tématu [specifikace kompatibility značek XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span><span class="sxs-lookup"><span data-stu-id="96e23-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e23-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96e23-129">See also</span></span>

- <xref:System.Windows.Markup.XamlReader>
- [<span data-ttu-id="96e23-130">PresentationOptions:Freeze – atribut</span><span class="sxs-lookup"><span data-stu-id="96e23-130">PresentationOptions:Freeze Attribute</span></span>](presentationoptions-freeze-attribute.md)
- [<span data-ttu-id="96e23-131">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="96e23-131">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="96e23-132">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="96e23-132">Documents in WPF</span></span>](documents-in-wpf.md)
