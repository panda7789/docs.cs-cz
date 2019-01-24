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
ms.openlocfilehash: 47b83ffdc2cd9a7958c8572df6fe16c9659427d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557484"
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="f381d-102">ContextMenu – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f381d-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="f381d-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ContextMenu> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f381d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="f381d-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f381d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f381d-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f381d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="f381d-106">ContextMenu – částí</span><span class="sxs-lookup"><span data-stu-id="f381d-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="f381d-107"><xref:System.Windows.Controls.ContextMenu> Ovládací prvek nemá žádné pojmenované součásti.</span><span class="sxs-lookup"><span data-stu-id="f381d-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="f381d-108">Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ContextMenu>, šablona může obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="f381d-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="f381d-109">( <xref:System.Windows.Controls.ItemsPresenter> Zobrazuje každou položku v <xref:System.Windows.Controls.ContextMenu>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).</span><span class="sxs-lookup"><span data-stu-id="f381d-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="f381d-110">Pokud <xref:System.Windows.Controls.ItemsPresenter> není za přímé podřízeného člena <xref:System.Windows.Controls.ScrollViewer>, je třeba zadat <xref:System.Windows.Controls.ItemsPresenter> názvu, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="f381d-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="f381d-111">ContextMenu – stavy</span><span class="sxs-lookup"><span data-stu-id="f381d-111">ContextMenu States</span></span>  
 <span data-ttu-id="f381d-112">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.ContextMenu> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f381d-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="f381d-113">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="f381d-113">VisualState Name</span></span>|<span data-ttu-id="f381d-114">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f381d-114">VisualStateGroup Name</span></span>|<span data-ttu-id="f381d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f381d-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f381d-116">Platné</span><span class="sxs-lookup"><span data-stu-id="f381d-116">Valid</span></span>|<span data-ttu-id="f381d-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f381d-117">ValidationStates</span></span>|<span data-ttu-id="f381d-118">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="f381d-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f381d-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f381d-119">InvalidFocused</span></span>|<span data-ttu-id="f381d-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f381d-120">ValidationStates</span></span>|<span data-ttu-id="f381d-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="f381d-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f381d-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f381d-122">InvalidUnfocused</span></span>|<span data-ttu-id="f381d-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f381d-123">ValidationStates</span></span>|<span data-ttu-id="f381d-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="f381d-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="f381d-125">Příklad šablony ControlTemplate ContextMenu</span><span class="sxs-lookup"><span data-stu-id="f381d-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="f381d-126">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ContextMenu> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f381d-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="f381d-127"><xref:System.Windows.Controls.ControlTemplate> Používá následující prostředky.</span><span class="sxs-lookup"><span data-stu-id="f381d-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f381d-128">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f381d-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f381d-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f381d-129">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f381d-130">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f381d-130">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="f381d-131">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f381d-131">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="f381d-132">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f381d-132">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="f381d-133">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f381d-133">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
