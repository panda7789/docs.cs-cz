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
ms.openlocfilehash: 4112306dab648d022e171401f5b9b362f2c91fdc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460759"
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="0aa17-102">ContextMenu – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="0aa17-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="0aa17-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="0aa17-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="0aa17-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="0aa17-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="0aa17-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="0aa17-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="0aa17-106">Dopředné části</span><span class="sxs-lookup"><span data-stu-id="0aa17-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="0aa17-107">Ovládací prvek <xref:System.Windows.Controls.ContextMenu> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="0aa17-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="0aa17-108">Když vytvoříte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ContextMenu>, šablona může v <xref:System.Windows.Controls.ScrollViewer>obsahovat <xref:System.Windows.Controls.ItemsPresenter>.</span><span class="sxs-lookup"><span data-stu-id="0aa17-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="0aa17-109">(<xref:System.Windows.Controls.ItemsPresenter> zobrazuje každou položku v <xref:System.Windows.Controls.ContextMenu>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v rámci ovládacího prvku).</span><span class="sxs-lookup"><span data-stu-id="0aa17-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="0aa17-110">Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímým podřízeným <xref:System.Windows.Controls.ScrollViewer>, je nutné zadat <xref:System.Windows.Controls.ItemsPresenter> název `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="0aa17-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="0aa17-111">Stavy dostavování</span><span class="sxs-lookup"><span data-stu-id="0aa17-111">ContextMenu States</span></span>  
 <span data-ttu-id="0aa17-112">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="0aa17-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="0aa17-113">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="0aa17-113">VisualState Name</span></span>|<span data-ttu-id="0aa17-114">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="0aa17-114">VisualStateGroup Name</span></span>|<span data-ttu-id="0aa17-115">Popis</span><span class="sxs-lookup"><span data-stu-id="0aa17-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0aa17-116">Platné</span><span class="sxs-lookup"><span data-stu-id="0aa17-116">Valid</span></span>|<span data-ttu-id="0aa17-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0aa17-117">ValidationStates</span></span>|<span data-ttu-id="0aa17-118">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="0aa17-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="0aa17-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="0aa17-119">InvalidFocused</span></span>|<span data-ttu-id="0aa17-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0aa17-120">ValidationStates</span></span>|<span data-ttu-id="0aa17-121">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="0aa17-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="0aa17-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="0aa17-122">InvalidUnfocused</span></span>|<span data-ttu-id="0aa17-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0aa17-123">ValidationStates</span></span>|<span data-ttu-id="0aa17-124">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="0aa17-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="0aa17-125">ControlTemplate příklad pro nabídku</span><span class="sxs-lookup"><span data-stu-id="0aa17-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="0aa17-126">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="0aa17-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="0aa17-127"><xref:System.Windows.Controls.ControlTemplate> používá následující zdroje informací.</span><span class="sxs-lookup"><span data-stu-id="0aa17-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="0aa17-128">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="0aa17-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa17-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0aa17-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="0aa17-130">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="0aa17-130">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="0aa17-131">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="0aa17-131">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="0aa17-132">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="0aa17-132">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="0aa17-133">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="0aa17-133">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
