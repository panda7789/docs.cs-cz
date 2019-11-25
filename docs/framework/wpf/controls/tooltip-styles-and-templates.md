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
ms.openlocfilehash: c7a14034d665c124d01e8a4b43c5d42968241925
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283650"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="6d86c-102">ToolTip – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="6d86c-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="6d86c-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="6d86c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="6d86c-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="6d86c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6d86c-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="6d86c-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="6d86c-106">Části popisu</span><span class="sxs-lookup"><span data-stu-id="6d86c-106">ToolTip Parts</span></span>  
 <span data-ttu-id="6d86c-107">Ovládací prvek <xref:System.Windows.Controls.ToolTip> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="6d86c-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="6d86c-108">Stavy tlačítek</span><span class="sxs-lookup"><span data-stu-id="6d86c-108">ToolTip States</span></span>  
 <span data-ttu-id="6d86c-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="6d86c-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="6d86c-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="6d86c-110">VisualState Name</span></span>|<span data-ttu-id="6d86c-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6d86c-111">VisualStateGroup Name</span></span>|<span data-ttu-id="6d86c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6d86c-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6d86c-113">Zavřeno</span><span class="sxs-lookup"><span data-stu-id="6d86c-113">Closed</span></span>|<span data-ttu-id="6d86c-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="6d86c-114">OpenStates</span></span>|<span data-ttu-id="6d86c-115">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="6d86c-115">The default state.</span></span>|  
|<span data-ttu-id="6d86c-116">Otevřít</span><span class="sxs-lookup"><span data-stu-id="6d86c-116">Open</span></span>|<span data-ttu-id="6d86c-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="6d86c-117">OpenStates</span></span>|<span data-ttu-id="6d86c-118"><xref:System.Windows.Controls.ToolTip> je viditelný.</span><span class="sxs-lookup"><span data-stu-id="6d86c-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="6d86c-119">Platné</span><span class="sxs-lookup"><span data-stu-id="6d86c-119">Valid</span></span>|<span data-ttu-id="6d86c-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6d86c-120">ValidationStates</span></span>|<span data-ttu-id="6d86c-121">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="6d86c-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6d86c-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6d86c-122">InvalidFocused</span></span>|<span data-ttu-id="6d86c-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6d86c-123">ValidationStates</span></span>|<span data-ttu-id="6d86c-124">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="6d86c-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6d86c-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6d86c-125">InvalidUnfocused</span></span>|<span data-ttu-id="6d86c-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6d86c-126">ValidationStates</span></span>|<span data-ttu-id="6d86c-127">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="6d86c-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="6d86c-128">Příklad ControlTemplate popisu</span><span class="sxs-lookup"><span data-stu-id="6d86c-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="6d86c-129">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="6d86c-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="6d86c-130">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="6d86c-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6d86c-131">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="6d86c-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d86c-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d86c-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="6d86c-133">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="6d86c-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="6d86c-134">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6d86c-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="6d86c-135">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="6d86c-135">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="6d86c-136">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="6d86c-136">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
