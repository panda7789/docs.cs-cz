---
title: Styly a šablony jezdce
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: e987932e00be09fdf5ac34bb2bfb24a890368a15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596381"
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="5b676-102">Styly a šablony jezdce</span><span class="sxs-lookup"><span data-stu-id="5b676-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="5b676-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5b676-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="5b676-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5b676-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5b676-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="5b676-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="5b676-106">Jezdec částí</span><span class="sxs-lookup"><span data-stu-id="5b676-106">Thumb Parts</span></span>  
 <span data-ttu-id="5b676-107"><xref:System.Windows.Controls.Primitives.Thumb> Ovládací prvek nemá žádné pojmenované součásti.</span><span class="sxs-lookup"><span data-stu-id="5b676-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="5b676-108">Stavy jezdce</span><span class="sxs-lookup"><span data-stu-id="5b676-108">Thumb States</span></span>  
 <span data-ttu-id="5b676-109">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5b676-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="5b676-110">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="5b676-110">VisualState Name</span></span>|<span data-ttu-id="5b676-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="5b676-111">VisualStateGroup Name</span></span>|<span data-ttu-id="5b676-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5b676-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5b676-113">Normální</span><span class="sxs-lookup"><span data-stu-id="5b676-113">Normal</span></span>|<span data-ttu-id="5b676-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5b676-114">CommonStates</span></span>|<span data-ttu-id="5b676-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="5b676-115">The default state.</span></span>|  
|<span data-ttu-id="5b676-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="5b676-116">MouseOver</span></span>|<span data-ttu-id="5b676-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5b676-117">CommonStates</span></span>|<span data-ttu-id="5b676-118">Je ukazatel myši umístěn nad ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5b676-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="5b676-119">Stisknutí</span><span class="sxs-lookup"><span data-stu-id="5b676-119">Pressed</span></span>|<span data-ttu-id="5b676-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5b676-120">CommonStates</span></span>|<span data-ttu-id="5b676-121">Stisknutí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5b676-121">The control is pressed.</span></span>|  
|<span data-ttu-id="5b676-122">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="5b676-122">Disabled</span></span>|<span data-ttu-id="5b676-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5b676-123">CommonStates</span></span>|<span data-ttu-id="5b676-124">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="5b676-124">The control is disabled.</span></span>|  
|<span data-ttu-id="5b676-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="5b676-125">Focused</span></span>|<span data-ttu-id="5b676-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5b676-126">FocusStates</span></span>|<span data-ttu-id="5b676-127">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="5b676-127">The control has focus.</span></span>|  
|<span data-ttu-id="5b676-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="5b676-128">Unfocused</span></span>|<span data-ttu-id="5b676-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5b676-129">FocusStates</span></span>|<span data-ttu-id="5b676-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="5b676-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="5b676-131">Platné</span><span class="sxs-lookup"><span data-stu-id="5b676-131">Valid</span></span>|<span data-ttu-id="5b676-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5b676-132">ValidationStates</span></span>|<span data-ttu-id="5b676-133">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="5b676-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5b676-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5b676-134">InvalidFocused</span></span>|<span data-ttu-id="5b676-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5b676-135">ValidationStates</span></span>|<span data-ttu-id="5b676-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="5b676-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5b676-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5b676-137">InvalidUnfocused</span></span>|<span data-ttu-id="5b676-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5b676-138">ValidationStates</span></span>|<span data-ttu-id="5b676-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="5b676-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="5b676-140">Příklad Thumb ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="5b676-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="5b676-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5b676-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="5b676-142">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="5b676-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5b676-143">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="5b676-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b676-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b676-144">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="5b676-145">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="5b676-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="5b676-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="5b676-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="5b676-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="5b676-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="5b676-148">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="5b676-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
