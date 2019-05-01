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
ms.openlocfilehash: 385a69ad2bd17ae4c51437245915109aad446bdf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970973"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="f9862-102">Styly a šablony posuvníku</span><span class="sxs-lookup"><span data-stu-id="f9862-102">Slider Styles and Templates</span></span>
<span data-ttu-id="f9862-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f9862-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="f9862-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f9862-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f9862-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f9862-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="f9862-106">Části posuvníku</span><span class="sxs-lookup"><span data-stu-id="f9862-106">Slider Parts</span></span>  
 <span data-ttu-id="f9862-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f9862-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="f9862-108">Část</span><span class="sxs-lookup"><span data-stu-id="f9862-108">Part</span></span>|<span data-ttu-id="f9862-109">Type</span><span class="sxs-lookup"><span data-stu-id="f9862-109">Type</span></span>|<span data-ttu-id="f9862-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f9862-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f9862-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="f9862-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="f9862-112">Kontejner pro prvek, který označuje pozici <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="f9862-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="f9862-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="f9862-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="f9862-114">Prvek, který se zobrazí oblast výběru podél <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="f9862-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="f9862-115">Výběr rozsahu je viditelná pouze tehdy, pokud <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="f9862-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="f9862-116">Stavy posuvníku</span><span class="sxs-lookup"><span data-stu-id="f9862-116">Slider States</span></span>  
 <span data-ttu-id="f9862-117">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f9862-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="f9862-118">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="f9862-118">VisualState Name</span></span>|<span data-ttu-id="f9862-119">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f9862-119">VisualStateGroup Name</span></span>|<span data-ttu-id="f9862-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f9862-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="f9862-121">Normální</span><span class="sxs-lookup"><span data-stu-id="f9862-121">Normal</span></span>|<span data-ttu-id="f9862-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f9862-122">CommonStates</span></span>|<span data-ttu-id="f9862-123">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="f9862-123">The default state.</span></span>|  
|<span data-ttu-id="f9862-124">Myš nad</span><span class="sxs-lookup"><span data-stu-id="f9862-124">MouseOver</span></span>|<span data-ttu-id="f9862-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f9862-125">CommonStates</span></span>|<span data-ttu-id="f9862-126">Je ukazatel myši umístěn nad ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f9862-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f9862-127">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="f9862-127">Disabled</span></span>|<span data-ttu-id="f9862-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f9862-128">CommonStates</span></span>|<span data-ttu-id="f9862-129">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="f9862-129">The control is disabled.</span></span>|  
|<span data-ttu-id="f9862-130">Fokus</span><span class="sxs-lookup"><span data-stu-id="f9862-130">Focused</span></span>|<span data-ttu-id="f9862-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f9862-131">FocusStates</span></span>|<span data-ttu-id="f9862-132">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="f9862-132">The control has focus.</span></span>|  
|<span data-ttu-id="f9862-133">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="f9862-133">Unfocused</span></span>|<span data-ttu-id="f9862-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f9862-134">FocusStates</span></span>|<span data-ttu-id="f9862-135">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="f9862-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="f9862-136">Platné</span><span class="sxs-lookup"><span data-stu-id="f9862-136">Valid</span></span>|<span data-ttu-id="f9862-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f9862-137">ValidationStates</span></span>|<span data-ttu-id="f9862-138">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="f9862-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f9862-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f9862-139">InvalidFocused</span></span>|<span data-ttu-id="f9862-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f9862-140">ValidationStates</span></span>|<span data-ttu-id="f9862-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="f9862-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f9862-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f9862-142">InvalidUnfocused</span></span>|<span data-ttu-id="f9862-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f9862-143">ValidationStates</span></span>|<span data-ttu-id="f9862-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="f9862-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="f9862-145">Příklad šablony ControlTemplate posuvníku</span><span class="sxs-lookup"><span data-stu-id="f9862-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="f9862-146">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f9862-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="f9862-147">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="f9862-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f9862-148">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f9862-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9862-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9862-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f9862-150">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f9862-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f9862-151">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f9862-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f9862-152">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f9862-152">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="f9862-153">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f9862-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
