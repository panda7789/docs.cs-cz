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
ms.openlocfilehash: 24def466509c12eb69307de139e83dd5a1ed5ce4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211618"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="f284e-102">ToolTip – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f284e-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="f284e-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ToolTip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f284e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="f284e-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f284e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f284e-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f284e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="f284e-106">Popis části</span><span class="sxs-lookup"><span data-stu-id="f284e-106">ToolTip Parts</span></span>  
 <span data-ttu-id="f284e-107"><xref:System.Windows.Controls.ToolTip> Ovládací prvek nemá žádné pojmenované součásti.</span><span class="sxs-lookup"><span data-stu-id="f284e-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="f284e-108">Popis stavu</span><span class="sxs-lookup"><span data-stu-id="f284e-108">ToolTip States</span></span>  
 <span data-ttu-id="f284e-109">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.ToolTip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f284e-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="f284e-110">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="f284e-110">VisualState Name</span></span>|<span data-ttu-id="f284e-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f284e-111">VisualStateGroup Name</span></span>|<span data-ttu-id="f284e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f284e-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f284e-113">Zavřeno</span><span class="sxs-lookup"><span data-stu-id="f284e-113">Closed</span></span>|<span data-ttu-id="f284e-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="f284e-114">OpenStates</span></span>|<span data-ttu-id="f284e-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="f284e-115">The default state.</span></span>|  
|<span data-ttu-id="f284e-116">Otevřít</span><span class="sxs-lookup"><span data-stu-id="f284e-116">Open</span></span>|<span data-ttu-id="f284e-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="f284e-117">OpenStates</span></span>|<span data-ttu-id="f284e-118"><xref:System.Windows.Controls.ToolTip> Je viditelný.</span><span class="sxs-lookup"><span data-stu-id="f284e-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="f284e-119">Platné</span><span class="sxs-lookup"><span data-stu-id="f284e-119">Valid</span></span>|<span data-ttu-id="f284e-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f284e-120">ValidationStates</span></span>|<span data-ttu-id="f284e-121">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="f284e-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f284e-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f284e-122">InvalidFocused</span></span>|<span data-ttu-id="f284e-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f284e-123">ValidationStates</span></span>|<span data-ttu-id="f284e-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="f284e-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f284e-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f284e-125">InvalidUnfocused</span></span>|<span data-ttu-id="f284e-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f284e-126">ValidationStates</span></span>|<span data-ttu-id="f284e-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="f284e-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="f284e-128">Příklad popisu tlačítka objektu ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f284e-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="f284e-129">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ToolTip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f284e-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="f284e-130">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="f284e-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f284e-131">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f284e-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f284e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f284e-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f284e-133">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f284e-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f284e-134">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f284e-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f284e-135">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f284e-135">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="f284e-136">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f284e-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
