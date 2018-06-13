---
title: Vložené styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: 9c06f61bce1e17770fa0a9b9ed7a0e20625a79ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545880"
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="e3dcb-102">Vložené styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e3dcb-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="e3dcb-103"> poskytuje <xref:System.Windows.Style> objekty a objekty šablony (<xref:System.Windows.FrameworkTemplate> podtřídy) jako způsob, jak definovat vzhled elementu v prostředků, tak, aby bylo možné několikrát.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-103"> provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="e3dcb-104">Z tohoto důvodu atributy v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] které přebírají typy <xref:System.Windows.Style> a <xref:System.Windows.FrameworkTemplate> definovat nové vložené místo prostředků odkazuje na existující styly a šablony téměř vždy.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="e3dcb-105">Omezení vložené styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e3dcb-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="e3dcb-106">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], styl a šablony vlastnosti technicky jde nastavit v jednom ze dvou způsobů.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="e3dcb-107">Můžete tak, aby odkazovaly styl, který byl definován v rámci prostředku, například pomocí syntaxe atribut `<` *objekt*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="e3dcb-108">Nebo můžete definovat vložené styl pro instanci pomocí syntaxe element vlastnost:</span><span class="sxs-lookup"><span data-stu-id="e3dcb-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 <span data-ttu-id="e3dcb-109">`<` *Objekt* `>`</span><span class="sxs-lookup"><span data-stu-id="e3dcb-109">`<` *object* `>`</span></span>  
  
 <span data-ttu-id="e3dcb-110">`<` *Objekt* `.Style>`</span><span class="sxs-lookup"><span data-stu-id="e3dcb-110">`<` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="e3dcb-111">`<` `Style`  `.../>`</span><span class="sxs-lookup"><span data-stu-id="e3dcb-111">`<` `Style`  `.../>`</span></span>  
  
 <span data-ttu-id="e3dcb-112">`</` *Objekt* `.Style>`</span><span class="sxs-lookup"><span data-stu-id="e3dcb-112">`</` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="e3dcb-113">`</` *Objekt* `>`</span><span class="sxs-lookup"><span data-stu-id="e3dcb-113">`</` *object* `>`</span></span>  
  
 <span data-ttu-id="e3dcb-114">Používání atributu je mnohem víc běžné.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-114">The attribute usage is much more common.</span></span> <span data-ttu-id="e3dcb-115">Styl, který je definována vložením a není definovaná v prostředky nutně rozsah obsahující element jenom a nelze znovu použít tak snadno, protože nemá žádné klíč prostředku.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-115">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="e3dcb-116">Obecně je univerzální a užitečné styl definované prostředků a je v souladu s obecné Další [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programovací model zásada oddělování program logiku v kódu z návrhu v kódu.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-116">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="e3dcb-117">Obvykle neexistuje žádný důvod k nastavení vložené styl nebo šablony, i když chcete používat tento styl nebo šablony v daném umístění.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-117">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="e3dcb-118">Většina elementů, které může provádět styl nebo šablony také podporují vlastnost obsahu a obsahu modelu.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-118">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="e3dcb-119">Pokud používáte pouze ať logického stromu vytvoříte jednou prostřednictvím stylů nebo ukázka, bylo by to bylo ještě jednodušší právě vyplníte vlastnost tohoto obsahu ekvivalentní podřízených elementů v přímé značek.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-119">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="e3dcb-120">To by zcela nepoužívat mechanismy style a šablony.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-120">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="e3dcb-121">Ostatních syntaxí povolené rozšíření značek, které vracejí objekt je také možné styly a šablony.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-121">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="e3dcb-122">Dva taková rozšíření, které mají možné scénáře zahrnují [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) a <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="e3dcb-122">Two such extensions that have possible scenarios include [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3dcb-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3dcb-123">See Also</span></span>  
 [<span data-ttu-id="e3dcb-124">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e3dcb-124">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
