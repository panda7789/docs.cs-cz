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
ms.openlocfilehash: f948cf2b4f4cd2a4cb73b0cd5fc754240c850b83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770523"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="faa28-102">ProgressBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="faa28-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="faa28-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="faa28-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="faa28-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="faa28-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="faa28-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="faa28-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="faa28-106">Ovládací prvek ProgressBar částí</span><span class="sxs-lookup"><span data-stu-id="faa28-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="faa28-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="faa28-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="faa28-108">Část</span><span class="sxs-lookup"><span data-stu-id="faa28-108">Part</span></span>|<span data-ttu-id="faa28-109">Type</span><span class="sxs-lookup"><span data-stu-id="faa28-109">Type</span></span>|<span data-ttu-id="faa28-110">Popis</span><span class="sxs-lookup"><span data-stu-id="faa28-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="faa28-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="faa28-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="faa28-112">Objekt, který označuje průběh.</span><span class="sxs-lookup"><span data-stu-id="faa28-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="faa28-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="faa28-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="faa28-114">Objekt, který definuje cestu indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="faa28-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="faa28-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="faa28-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="faa28-116">Objekt, který embellishes indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="faa28-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="faa28-117">ProgressBar – stavy</span><span class="sxs-lookup"><span data-stu-id="faa28-117">ProgressBar States</span></span>  
 <span data-ttu-id="faa28-118">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="faa28-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="faa28-119">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="faa28-119">VisualState Name</span></span>|<span data-ttu-id="faa28-120">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="faa28-120">VisualStateGroup Name</span></span>|<span data-ttu-id="faa28-121">Popis</span><span class="sxs-lookup"><span data-stu-id="faa28-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="faa28-122">Determinate</span><span class="sxs-lookup"><span data-stu-id="faa28-122">Determinate</span></span>|<span data-ttu-id="faa28-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="faa28-123">CommonStates</span></span>|<span data-ttu-id="faa28-124"><xref:System.Windows.Controls.ProgressBar> Zobrazuje průběh na základě <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="faa28-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="faa28-125">Neurčitá</span><span class="sxs-lookup"><span data-stu-id="faa28-125">Indeterminate</span></span>|<span data-ttu-id="faa28-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="faa28-126">CommonStates</span></span>|<span data-ttu-id="faa28-127"><xref:System.Windows.Controls.ProgressBar> Zobrazuje obecný průběh se opakující se vzorem.</span><span class="sxs-lookup"><span data-stu-id="faa28-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="faa28-128">Platné</span><span class="sxs-lookup"><span data-stu-id="faa28-128">Valid</span></span>|<span data-ttu-id="faa28-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="faa28-129">ValidationStates</span></span>|<span data-ttu-id="faa28-130">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="faa28-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="faa28-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="faa28-131">InvalidFocused</span></span>|<span data-ttu-id="faa28-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="faa28-132">ValidationStates</span></span>|<span data-ttu-id="faa28-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="faa28-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="faa28-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="faa28-134">InvalidUnfocused</span></span>|<span data-ttu-id="faa28-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="faa28-135">ValidationStates</span></span>|<span data-ttu-id="faa28-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="faa28-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="faa28-137">Příklad šablony ControlTemplate ProgressBar</span><span class="sxs-lookup"><span data-stu-id="faa28-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="faa28-138">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="faa28-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="faa28-139">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="faa28-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="faa28-140">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="faa28-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa28-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="faa28-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="faa28-142">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="faa28-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="faa28-143">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="faa28-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="faa28-144">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="faa28-144">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="faa28-145">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="faa28-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
