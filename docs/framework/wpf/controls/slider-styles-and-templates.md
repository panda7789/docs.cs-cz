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
ms.openlocfilehash: f533142d5ba202bd4aaf628487eaaa2a18a535d0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283390"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="f07c1-102">Styly a šablony posuvníku</span><span class="sxs-lookup"><span data-stu-id="f07c1-102">Slider Styles and Templates</span></span>
<span data-ttu-id="f07c1-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="f07c1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="f07c1-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="f07c1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f07c1-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="f07c1-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="f07c1-106">Části jezdce</span><span class="sxs-lookup"><span data-stu-id="f07c1-106">Slider Parts</span></span>  
 <span data-ttu-id="f07c1-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="f07c1-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="f07c1-108">Částí</span><span class="sxs-lookup"><span data-stu-id="f07c1-108">Part</span></span>|<span data-ttu-id="f07c1-109">Typ</span><span class="sxs-lookup"><span data-stu-id="f07c1-109">Type</span></span>|<span data-ttu-id="f07c1-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f07c1-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f07c1-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="f07c1-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="f07c1-112">Kontejner elementu, který určuje pozici <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="f07c1-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="f07c1-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="f07c1-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="f07c1-114">Element, který zobrazuje rozsah výběru podél <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="f07c1-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="f07c1-115">Rozsah výběru je viditelný pouze v případě, že je vlastnost <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> `true`.</span><span class="sxs-lookup"><span data-stu-id="f07c1-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="f07c1-116">Stavy jezdců</span><span class="sxs-lookup"><span data-stu-id="f07c1-116">Slider States</span></span>  
 <span data-ttu-id="f07c1-117">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="f07c1-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="f07c1-118">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="f07c1-118">VisualState Name</span></span>|<span data-ttu-id="f07c1-119">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f07c1-119">VisualStateGroup Name</span></span>|<span data-ttu-id="f07c1-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f07c1-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="f07c1-121">Normální</span><span class="sxs-lookup"><span data-stu-id="f07c1-121">Normal</span></span>|<span data-ttu-id="f07c1-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f07c1-122">CommonStates</span></span>|<span data-ttu-id="f07c1-123">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="f07c1-123">The default state.</span></span>|  
|<span data-ttu-id="f07c1-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="f07c1-124">MouseOver</span></span>|<span data-ttu-id="f07c1-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f07c1-125">CommonStates</span></span>|<span data-ttu-id="f07c1-126">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="f07c1-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f07c1-127">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="f07c1-127">Disabled</span></span>|<span data-ttu-id="f07c1-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f07c1-128">CommonStates</span></span>|<span data-ttu-id="f07c1-129">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="f07c1-129">The control is disabled.</span></span>|  
|<span data-ttu-id="f07c1-130">Zaměřil</span><span class="sxs-lookup"><span data-stu-id="f07c1-130">Focused</span></span>|<span data-ttu-id="f07c1-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f07c1-131">FocusStates</span></span>|<span data-ttu-id="f07c1-132">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="f07c1-132">The control has focus.</span></span>|  
|<span data-ttu-id="f07c1-133">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="f07c1-133">Unfocused</span></span>|<span data-ttu-id="f07c1-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f07c1-134">FocusStates</span></span>|<span data-ttu-id="f07c1-135">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="f07c1-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="f07c1-136">Platné</span><span class="sxs-lookup"><span data-stu-id="f07c1-136">Valid</span></span>|<span data-ttu-id="f07c1-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f07c1-137">ValidationStates</span></span>|<span data-ttu-id="f07c1-138">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="f07c1-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f07c1-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f07c1-139">InvalidFocused</span></span>|<span data-ttu-id="f07c1-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f07c1-140">ValidationStates</span></span>|<span data-ttu-id="f07c1-141">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="f07c1-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f07c1-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f07c1-142">InvalidUnfocused</span></span>|<span data-ttu-id="f07c1-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f07c1-143">ValidationStates</span></span>|<span data-ttu-id="f07c1-144">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="f07c1-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="f07c1-145">Příklad posuvníku ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f07c1-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="f07c1-146">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="f07c1-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="f07c1-147">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="f07c1-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f07c1-148">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f07c1-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f07c1-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f07c1-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f07c1-150">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f07c1-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f07c1-151">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f07c1-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f07c1-152">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f07c1-152">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f07c1-153">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="f07c1-153">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
