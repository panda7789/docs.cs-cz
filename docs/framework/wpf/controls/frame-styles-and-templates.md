---
title: Styly a šablony rámců
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
ms.openlocfilehash: de853198c97c99319bea4a816c9a6eca5dc5d917
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283731"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="86be8-102">Styly a šablony rámců</span><span class="sxs-lookup"><span data-stu-id="86be8-102">Frame Styles and Templates</span></span>
<span data-ttu-id="86be8-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="86be8-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="86be8-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="86be8-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="86be8-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="86be8-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="86be8-106">Části rámečku</span><span class="sxs-lookup"><span data-stu-id="86be8-106">Frame Parts</span></span>  
 <span data-ttu-id="86be8-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="86be8-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="86be8-108">Částí</span><span class="sxs-lookup"><span data-stu-id="86be8-108">Part</span></span>|<span data-ttu-id="86be8-109">Typ</span><span class="sxs-lookup"><span data-stu-id="86be8-109">Type</span></span>|<span data-ttu-id="86be8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="86be8-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="86be8-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="86be8-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="86be8-112">Oblast obsahu.</span><span class="sxs-lookup"><span data-stu-id="86be8-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="86be8-113">Stavy snímků</span><span class="sxs-lookup"><span data-stu-id="86be8-113">Frame States</span></span>  
 <span data-ttu-id="86be8-114">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="86be8-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="86be8-115">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="86be8-115">VisualState Name</span></span>|<span data-ttu-id="86be8-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="86be8-116">VisualStateGroup Name</span></span>|<span data-ttu-id="86be8-117">Popis</span><span class="sxs-lookup"><span data-stu-id="86be8-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="86be8-118">Platný</span><span class="sxs-lookup"><span data-stu-id="86be8-118">Valid</span></span>|<span data-ttu-id="86be8-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="86be8-119">ValidationStates</span></span>|<span data-ttu-id="86be8-120">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="86be8-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="86be8-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="86be8-121">InvalidFocused</span></span>|<span data-ttu-id="86be8-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="86be8-122">ValidationStates</span></span>|<span data-ttu-id="86be8-123">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="86be8-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="86be8-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="86be8-124">InvalidUnfocused</span></span>|<span data-ttu-id="86be8-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="86be8-125">ValidationStates</span></span>|<span data-ttu-id="86be8-126">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="86be8-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="86be8-127">Příklad ControlTemplate rámců</span><span class="sxs-lookup"><span data-stu-id="86be8-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="86be8-128">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="86be8-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="86be8-129">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="86be8-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="86be8-130">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="86be8-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86be8-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86be8-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="86be8-132">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="86be8-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="86be8-133">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="86be8-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="86be8-134">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="86be8-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="86be8-135">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="86be8-135">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
