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
ms.openlocfilehash: e14ab0ebc7d44e2792307b16c7c0581ff7a71bc6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740822"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="59b83-102">mc:Ignorable – atribut</span><span class="sxs-lookup"><span data-stu-id="59b83-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="59b83-103">Určuje, které předpony oboru názvů XML zjištěné v souboru značek mohou být [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesorem ignorovány.</span><span class="sxs-lookup"><span data-stu-id="59b83-103">Specifies which XML namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="59b83-104">Atribut `mc:Ignorable` podporuje kompatibilitu značek pro vlastní mapování oboru názvů a pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správu verzí.</span><span class="sxs-lookup"><span data-stu-id="59b83-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="59b83-105">Použití atributu XAML (jedna předpona)</span><span class="sxs-lookup"><span data-stu-id="59b83-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="59b83-106">Použití atributu XAML (dvě předpony)</span><span class="sxs-lookup"><span data-stu-id="59b83-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```xaml  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="59b83-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="59b83-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="59b83-108">*ignorablePrefix, ignorablePrefix1 atd.*</span><span class="sxs-lookup"><span data-stu-id="59b83-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="59b83-109">Libovolný platný řetězec předpony podle specifikace XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="59b83-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="59b83-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="59b83-110">*ignorableUri*</span></span>|<span data-ttu-id="59b83-111">Libovolný platný identifikátor URI pro určení oboru názvů podle specifikace XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="59b83-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="59b83-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="59b83-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="59b83-113">Element, který může být ignorován pomocí implementace [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] procesoru, pokud nelze přeložit nadřízený typ.</span><span class="sxs-lookup"><span data-stu-id="59b83-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59b83-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59b83-114">Remarks</span></span>  
 <span data-ttu-id="59b83-115">Předpona oboru názvů `mc` XML je doporučená konvence předpony, která se má použít při mapování `http://schemas.openxmlformats.org/markup-compatibility/2006`oboru názvů kompatibility [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59b83-115">The `mc` XML namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace `http://schemas.openxmlformats.org/markup-compatibility/2006`.</span></span>  
  
 <span data-ttu-id="59b83-116">Prvky nebo atributy, kde předpona v názvu elementu je identifikována jako `mc:Ignorable` nevyvolává chyby při zpracování procesorem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59b83-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="59b83-117">Pokud tento atribut nelze přeložit na nadřízený typ nebo konstruktor programování, je tento prvek ignorován.</span><span class="sxs-lookup"><span data-stu-id="59b83-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="59b83-118">Upozorňujeme však, že ignorované prvky mohou stále generovat další chyby analýzy pro další požadavky na prvky, které jsou vedlejšími účinky tohoto prvku nezpracovávány.</span><span class="sxs-lookup"><span data-stu-id="59b83-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="59b83-119">Například určitý model obsahu elementu může vyžadovat přesně jeden podřízený element, ale pokud byl zadaný podřízený element v předponě `mc:Ignorable` a zadaný podřízený element nelze přeložit na typ, pak procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] může vyvolat chybu.</span><span class="sxs-lookup"><span data-stu-id="59b83-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="59b83-120">`mc:Ignorable` se vztahuje pouze na mapování oboru názvů na řetězce identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="59b83-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="59b83-121">`mc:Ignorable` se nevztahuje na mapování oboru názvů na sestavení, která určují obor názvů CLR a sestavení (nebo výchozí hodnotu pro aktuální spustitelný soubor jako sestavení).</span><span class="sxs-lookup"><span data-stu-id="59b83-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a CLR namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="59b83-122">Pokud implementujete [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor, vaše implementace procesoru nesmí vyvolávat analýzu nebo zpracování chyb na rozlišení typu pro libovolný element nebo atribut, který je kvalifikován předponou identifikovanou jako `mc:Ignorable`.</span><span class="sxs-lookup"><span data-stu-id="59b83-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="59b83-123">Ale vaše implementace procesoru stále může vyvolávat výjimky, které jsou druhotným výsledkem selhání elementu, který se nedaří načíst nebo zpracovat, jako je například příklad prvku s jedním podřízeným objektem uvedeným dříve.</span><span class="sxs-lookup"><span data-stu-id="59b83-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="59b83-124">Ve výchozím nastavení bude procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorovat obsah v rámci ignorovaného prvku.</span><span class="sxs-lookup"><span data-stu-id="59b83-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="59b83-125">Můžete však zadat další atribut, [MC: ProcessContent atribut](mc-processcontent-attribute.md), aby bylo možné pokračovat ve zpracování obsahu v rámci ignorovaného prvku následujícím dostupným nadřazeným elementem.</span><span class="sxs-lookup"><span data-stu-id="59b83-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="59b83-126">V atributu lze zadat více předpon s použitím jednoho nebo více prázdných znaků jako oddělovače, například: `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="59b83-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="59b83-127">Obor názvů `http://schemas.openxmlformats.org/markup-compatibility/2006` definuje další prvky a atributy, které nejsou zdokumentovány v této oblasti sady SDK.</span><span class="sxs-lookup"><span data-stu-id="59b83-127">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="59b83-128">Další informace najdete v tématu [specifikace kompatibility značek XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span><span class="sxs-lookup"><span data-stu-id="59b83-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b83-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59b83-129">See also</span></span>

- <xref:System.Windows.Markup.XamlReader>
- [<span data-ttu-id="59b83-130">PresentationOptions:Freeze – atribut</span><span class="sxs-lookup"><span data-stu-id="59b83-130">PresentationOptions:Freeze Attribute</span></span>](presentationoptions-freeze-attribute.md)
- [<span data-ttu-id="59b83-131">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="59b83-131">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="59b83-132">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="59b83-132">Documents in WPF</span></span>](documents-in-wpf.md)
