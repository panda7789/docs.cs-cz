---
title: ToolTip – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
ms.openlocfilehash: 53b21f610ba957370fac70b79e6a827d624b6473
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457291"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="d3e5c-102">ToolTip – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d3e5c-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="d3e5c-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ToolTip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d3e5c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="d3e5c-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d3e5c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d3e5c-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d3e5c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="d3e5c-106">Popis části</span><span class="sxs-lookup"><span data-stu-id="d3e5c-106">ToolTip Parts</span></span>  
 <span data-ttu-id="d3e5c-107"><xref:System.Windows.Controls.ToolTip> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="d3e5c-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="d3e5c-108">Popisek stavy</span><span class="sxs-lookup"><span data-stu-id="d3e5c-108">ToolTip States</span></span>  
 <span data-ttu-id="d3e5c-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ToolTip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d3e5c-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="d3e5c-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="d3e5c-110">VisualState Name</span></span>|<span data-ttu-id="d3e5c-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d3e5c-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d3e5c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d3e5c-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d3e5c-113">Zavřeno</span><span class="sxs-lookup"><span data-stu-id="d3e5c-113">Closed</span></span>|<span data-ttu-id="d3e5c-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="d3e5c-114">OpenStates</span></span>|<span data-ttu-id="d3e5c-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="d3e5c-115">The default state.</span></span>|  
|<span data-ttu-id="d3e5c-116">Otevřít</span><span class="sxs-lookup"><span data-stu-id="d3e5c-116">Open</span></span>|<span data-ttu-id="d3e5c-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="d3e5c-117">OpenStates</span></span>|<span data-ttu-id="d3e5c-118"><xref:System.Windows.Controls.ToolTip> Je viditelná.</span><span class="sxs-lookup"><span data-stu-id="d3e5c-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="d3e5c-119">Platné</span><span class="sxs-lookup"><span data-stu-id="d3e5c-119">Valid</span></span>|<span data-ttu-id="d3e5c-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d3e5c-120">ValidationStates</span></span>|<span data-ttu-id="d3e5c-121">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="d3e5c-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d3e5c-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d3e5c-122">InvalidFocused</span></span>|<span data-ttu-id="d3e5c-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d3e5c-123">ValidationStates</span></span>|<span data-ttu-id="d3e5c-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="d3e5c-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d3e5c-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d3e5c-125">InvalidUnfocused</span></span>|<span data-ttu-id="d3e5c-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d3e5c-126">ValidationStates</span></span>|<span data-ttu-id="d3e5c-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d3e5c-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="d3e5c-128">Příklad popisku ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d3e5c-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="d3e5c-129">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ToolTip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d3e5c-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="d3e5c-130">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="d3e5c-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d3e5c-131">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="d3e5c-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e5c-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3e5c-132">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d3e5c-133">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="d3e5c-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d3e5c-134">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d3e5c-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d3e5c-135">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d3e5c-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d3e5c-136">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d3e5c-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
