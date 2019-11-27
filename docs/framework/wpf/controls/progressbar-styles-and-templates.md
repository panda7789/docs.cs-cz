---
title: ProgressBar – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 6551701e86dd6abcd42f143f146c7bdadfeabbcf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283452"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="17ffc-102">ProgressBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="17ffc-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="17ffc-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="17ffc-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="17ffc-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="17ffc-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="17ffc-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="17ffc-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="17ffc-106">Součásti ProgressBar</span><span class="sxs-lookup"><span data-stu-id="17ffc-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="17ffc-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="17ffc-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="17ffc-108">Částí</span><span class="sxs-lookup"><span data-stu-id="17ffc-108">Part</span></span>|<span data-ttu-id="17ffc-109">Typ</span><span class="sxs-lookup"><span data-stu-id="17ffc-109">Type</span></span>|<span data-ttu-id="17ffc-110">Popis</span><span class="sxs-lookup"><span data-stu-id="17ffc-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="17ffc-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="17ffc-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="17ffc-112">Objekt, který označuje průběh.</span><span class="sxs-lookup"><span data-stu-id="17ffc-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="17ffc-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="17ffc-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="17ffc-114">Objekt, který definuje cestu indikátoru průběhu.</span><span class="sxs-lookup"><span data-stu-id="17ffc-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="17ffc-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="17ffc-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="17ffc-116">Objekt, který embellishes indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="17ffc-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="17ffc-117">Stavy ProgressBar</span><span class="sxs-lookup"><span data-stu-id="17ffc-117">ProgressBar States</span></span>  
 <span data-ttu-id="17ffc-118">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="17ffc-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="17ffc-119">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="17ffc-119">VisualState Name</span></span>|<span data-ttu-id="17ffc-120">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="17ffc-120">VisualStateGroup Name</span></span>|<span data-ttu-id="17ffc-121">Popis</span><span class="sxs-lookup"><span data-stu-id="17ffc-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="17ffc-122">Determinate</span><span class="sxs-lookup"><span data-stu-id="17ffc-122">Determinate</span></span>|<span data-ttu-id="17ffc-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="17ffc-123">CommonStates</span></span>|<span data-ttu-id="17ffc-124"><xref:System.Windows.Controls.ProgressBar> sestaví průběh na základě vlastnosti <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="17ffc-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="17ffc-125">Neurčitá</span><span class="sxs-lookup"><span data-stu-id="17ffc-125">Indeterminate</span></span>|<span data-ttu-id="17ffc-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="17ffc-126">CommonStates</span></span>|<span data-ttu-id="17ffc-127"><xref:System.Windows.Controls.ProgressBar> sestavuje obecný průběh pomocí opakujícího se vzoru.</span><span class="sxs-lookup"><span data-stu-id="17ffc-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="17ffc-128">Platný</span><span class="sxs-lookup"><span data-stu-id="17ffc-128">Valid</span></span>|<span data-ttu-id="17ffc-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17ffc-129">ValidationStates</span></span>|<span data-ttu-id="17ffc-130">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="17ffc-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="17ffc-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="17ffc-131">InvalidFocused</span></span>|<span data-ttu-id="17ffc-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17ffc-132">ValidationStates</span></span>|<span data-ttu-id="17ffc-133">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="17ffc-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="17ffc-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="17ffc-134">InvalidUnfocused</span></span>|<span data-ttu-id="17ffc-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17ffc-135">ValidationStates</span></span>|<span data-ttu-id="17ffc-136">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="17ffc-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="17ffc-137">Příklad ControlTemplate ProgressBar</span><span class="sxs-lookup"><span data-stu-id="17ffc-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="17ffc-138">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="17ffc-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="17ffc-139">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="17ffc-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="17ffc-140">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="17ffc-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ffc-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17ffc-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="17ffc-142">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="17ffc-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="17ffc-143">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="17ffc-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="17ffc-144">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="17ffc-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="17ffc-145">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="17ffc-145">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
