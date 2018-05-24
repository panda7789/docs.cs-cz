---
title: ContextMenu – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
ms.openlocfilehash: 671fb0a4f178c9e16149f6d47945670ea0e64d48
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="fb05a-102">ContextMenu – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="fb05a-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="fb05a-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ContextMenu> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb05a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="fb05a-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb05a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="fb05a-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="fb05a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="fb05a-106">ContextMenu – součásti</span><span class="sxs-lookup"><span data-stu-id="fb05a-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="fb05a-107"><xref:System.Windows.Controls.ContextMenu> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="fb05a-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="fb05a-108">Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ContextMenu>, může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="fb05a-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="fb05a-109">( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí jednotlivé položky <xref:System.Windows.Controls.ContextMenu>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).</span><span class="sxs-lookup"><span data-stu-id="fb05a-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="fb05a-110">Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímými podřízenými z <xref:System.Windows.Controls.ScrollViewer>, musíte <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="fb05a-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="fb05a-111">ContextMenu – stavy</span><span class="sxs-lookup"><span data-stu-id="fb05a-111">ContextMenu States</span></span>  
 <span data-ttu-id="fb05a-112">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ContextMenu> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb05a-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="fb05a-113">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="fb05a-113">VisualState Name</span></span>|<span data-ttu-id="fb05a-114">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="fb05a-114">VisualStateGroup Name</span></span>|<span data-ttu-id="fb05a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="fb05a-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fb05a-116">Platné</span><span class="sxs-lookup"><span data-stu-id="fb05a-116">Valid</span></span>|<span data-ttu-id="fb05a-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb05a-117">ValidationStates</span></span>|<span data-ttu-id="fb05a-118">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="fb05a-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="fb05a-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="fb05a-119">InvalidFocused</span></span>|<span data-ttu-id="fb05a-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb05a-120">ValidationStates</span></span>|<span data-ttu-id="fb05a-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="fb05a-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="fb05a-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="fb05a-122">InvalidUnfocused</span></span>|<span data-ttu-id="fb05a-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb05a-123">ValidationStates</span></span>|<span data-ttu-id="fb05a-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="fb05a-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="fb05a-125">Příklad ControlTemplate ContextMenu</span><span class="sxs-lookup"><span data-stu-id="fb05a-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="fb05a-126">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ContextMenu> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb05a-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="fb05a-127"><xref:System.Windows.Controls.ControlTemplate> Používá následující prostředky.</span><span class="sxs-lookup"><span data-stu-id="fb05a-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="fb05a-128">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="fb05a-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb05a-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb05a-129">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="fb05a-130">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="fb05a-130">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="fb05a-131">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="fb05a-131">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="fb05a-132">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="fb05a-132">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="fb05a-133">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="fb05a-133">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
