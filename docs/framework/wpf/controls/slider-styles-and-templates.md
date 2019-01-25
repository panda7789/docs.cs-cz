---
title: Styly a šablony posuvníku
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
ms.openlocfilehash: 3b56b26716eb2ffc0a776085579c4d5df09e3ace
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596251"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="10d6c-102">Styly a šablony posuvníku</span><span class="sxs-lookup"><span data-stu-id="10d6c-102">Slider Styles and Templates</span></span>
<span data-ttu-id="10d6c-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="10d6c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="10d6c-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="10d6c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="10d6c-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="10d6c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="10d6c-106">Části posuvníku</span><span class="sxs-lookup"><span data-stu-id="10d6c-106">Slider Parts</span></span>  
 <span data-ttu-id="10d6c-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="10d6c-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="10d6c-108">Část</span><span class="sxs-lookup"><span data-stu-id="10d6c-108">Part</span></span>|<span data-ttu-id="10d6c-109">Typ</span><span class="sxs-lookup"><span data-stu-id="10d6c-109">Type</span></span>|<span data-ttu-id="10d6c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="10d6c-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="10d6c-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="10d6c-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="10d6c-112">Kontejner pro prvek, který označuje pozici <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="10d6c-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="10d6c-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="10d6c-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="10d6c-114">Prvek, který se zobrazí oblast výběru podél <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="10d6c-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="10d6c-115">Výběr rozsahu je viditelná pouze tehdy, pokud <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="10d6c-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="10d6c-116">Stavy posuvníku</span><span class="sxs-lookup"><span data-stu-id="10d6c-116">Slider States</span></span>  
 <span data-ttu-id="10d6c-117">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="10d6c-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="10d6c-118">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="10d6c-118">VisualState Name</span></span>|<span data-ttu-id="10d6c-119">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="10d6c-119">VisualStateGroup Name</span></span>|<span data-ttu-id="10d6c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="10d6c-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="10d6c-121">Normální</span><span class="sxs-lookup"><span data-stu-id="10d6c-121">Normal</span></span>|<span data-ttu-id="10d6c-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="10d6c-122">CommonStates</span></span>|<span data-ttu-id="10d6c-123">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="10d6c-123">The default state.</span></span>|  
|<span data-ttu-id="10d6c-124">Myš nad</span><span class="sxs-lookup"><span data-stu-id="10d6c-124">MouseOver</span></span>|<span data-ttu-id="10d6c-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="10d6c-125">CommonStates</span></span>|<span data-ttu-id="10d6c-126">Je ukazatel myši umístěn nad ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="10d6c-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="10d6c-127">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="10d6c-127">Disabled</span></span>|<span data-ttu-id="10d6c-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="10d6c-128">CommonStates</span></span>|<span data-ttu-id="10d6c-129">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="10d6c-129">The control is disabled.</span></span>|  
|<span data-ttu-id="10d6c-130">Fokus</span><span class="sxs-lookup"><span data-stu-id="10d6c-130">Focused</span></span>|<span data-ttu-id="10d6c-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="10d6c-131">FocusStates</span></span>|<span data-ttu-id="10d6c-132">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="10d6c-132">The control has focus.</span></span>|  
|<span data-ttu-id="10d6c-133">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="10d6c-133">Unfocused</span></span>|<span data-ttu-id="10d6c-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="10d6c-134">FocusStates</span></span>|<span data-ttu-id="10d6c-135">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="10d6c-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="10d6c-136">Platné</span><span class="sxs-lookup"><span data-stu-id="10d6c-136">Valid</span></span>|<span data-ttu-id="10d6c-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="10d6c-137">ValidationStates</span></span>|<span data-ttu-id="10d6c-138">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="10d6c-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="10d6c-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="10d6c-139">InvalidFocused</span></span>|<span data-ttu-id="10d6c-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="10d6c-140">ValidationStates</span></span>|<span data-ttu-id="10d6c-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="10d6c-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="10d6c-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="10d6c-142">InvalidUnfocused</span></span>|<span data-ttu-id="10d6c-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="10d6c-143">ValidationStates</span></span>|<span data-ttu-id="10d6c-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="10d6c-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="10d6c-145">Příklad šablony ControlTemplate posuvníku</span><span class="sxs-lookup"><span data-stu-id="10d6c-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="10d6c-146">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="10d6c-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="10d6c-147">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="10d6c-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="10d6c-148">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="10d6c-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10d6c-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10d6c-149">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="10d6c-150">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="10d6c-150">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="10d6c-151">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="10d6c-151">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="10d6c-152">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="10d6c-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="10d6c-153">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="10d6c-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
