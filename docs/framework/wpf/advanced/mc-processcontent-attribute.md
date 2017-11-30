---
title: "mc:ProcessContent – atribut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aaf83fe66d5367d5e51428cb8f35aa88c12c9c39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="f4595-102">mc:ProcessContent – atribut</span><span class="sxs-lookup"><span data-stu-id="f4595-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="f4595-103">Určuje, které [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy by měl mít pořád obsah zpracovává příslušné nadřazené elementy, i když může být ignorována okamžitou nadřazeného elementu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru kvůli určení [mc: Ignorovatelná atribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) .</span><span class="sxs-lookup"><span data-stu-id="f4595-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).</span></span> <span data-ttu-id="f4595-104">`mc:ProcessContent` Podporuje atribut kompatibility značek pro vlastní obor názvů mapování i pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správy verzí.</span><span class="sxs-lookup"><span data-stu-id="f4595-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f4595-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="f4595-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f4595-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="f4595-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4595-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="f4595-107">*ignorablePrefix*</span></span>|<span data-ttu-id="f4595-108">Všechny platnou předponu řetězec podle specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="f4595-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="f4595-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="f4595-109">*ignorableUri*</span></span>|<span data-ttu-id="f4595-110">Všechny platný identifikátor URI pro určení oboru názvů podle specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="f4595-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="f4595-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="f4595-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="f4595-112">Element, který můžete ignorovat podle [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementace zpracovatelů, pokud základní typ nelze přeložit.</span><span class="sxs-lookup"><span data-stu-id="f4595-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="f4595-113">*[obsah]*</span><span class="sxs-lookup"><span data-stu-id="f4595-113">*[content]*</span></span>|<span data-ttu-id="f4595-114">*ThisElementCanBeIgnored* je označena Ignorovatelná.</span><span class="sxs-lookup"><span data-stu-id="f4595-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="f4595-115">Pokud procesor ignoruje daný element *[obsah]* zpracovává *objekt*.</span><span class="sxs-lookup"><span data-stu-id="f4595-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4595-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4595-116">Remarks</span></span>  
 <span data-ttu-id="f4595-117">Ve výchozím nastavení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru bude ignorovat obsahu v rámci elementu ignorováno.</span><span class="sxs-lookup"><span data-stu-id="f4595-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="f4595-118">Můžete zadat konkrétní element podle `mc:ProcessContent`a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru bude pokračovat ve zpracování obsahu v rámci prvku ignorováno.</span><span class="sxs-lookup"><span data-stu-id="f4595-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="f4595-119">To by obvykle použijí, pokud je v rámci několik značek, alespoň jeden z nich je Ignorovatelná a alespoň jeden z nich není Ignorovatelná vnořený obsah.</span><span class="sxs-lookup"><span data-stu-id="f4595-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="f4595-120">Několik předpon je možné zadat atribut, pomocí oddělovače místo, například: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="f4595-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="f4595-121">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Definuje obor názvů další elementy a atributy, které nejsou popsané v této oblasti [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4595-121">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="f4595-122">Další informace najdete v tématu [specifikace kompatibility značek XML](http://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="f4595-122">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4595-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4595-123">See Also</span></span>  
 [<span data-ttu-id="f4595-124">MC: Ignorovatelná atribut</span><span class="sxs-lookup"><span data-stu-id="f4595-124">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [<span data-ttu-id="f4595-125">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="f4595-125">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
