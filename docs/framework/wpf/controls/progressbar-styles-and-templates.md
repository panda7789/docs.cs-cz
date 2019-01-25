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
ms.openlocfilehash: 7e410642e6153ed8064b2ddfb38fddd9cce6f4de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525375"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="621e5-102">ProgressBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="621e5-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="621e5-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="621e5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="621e5-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="621e5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="621e5-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="621e5-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="621e5-106">Ovládací prvek ProgressBar částí</span><span class="sxs-lookup"><span data-stu-id="621e5-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="621e5-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="621e5-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="621e5-108">Část</span><span class="sxs-lookup"><span data-stu-id="621e5-108">Part</span></span>|<span data-ttu-id="621e5-109">Typ</span><span class="sxs-lookup"><span data-stu-id="621e5-109">Type</span></span>|<span data-ttu-id="621e5-110">Popis</span><span class="sxs-lookup"><span data-stu-id="621e5-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="621e5-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="621e5-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="621e5-112">Objekt, který označuje průběh.</span><span class="sxs-lookup"><span data-stu-id="621e5-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="621e5-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="621e5-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="621e5-114">Objekt, který definuje cestu indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="621e5-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="621e5-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="621e5-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="621e5-116">Objekt, který embellishes indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="621e5-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="621e5-117">ProgressBar – stavy</span><span class="sxs-lookup"><span data-stu-id="621e5-117">ProgressBar States</span></span>  
 <span data-ttu-id="621e5-118">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="621e5-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="621e5-119">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="621e5-119">VisualState Name</span></span>|<span data-ttu-id="621e5-120">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="621e5-120">VisualStateGroup Name</span></span>|<span data-ttu-id="621e5-121">Popis</span><span class="sxs-lookup"><span data-stu-id="621e5-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="621e5-122">Determinate</span><span class="sxs-lookup"><span data-stu-id="621e5-122">Determinate</span></span>|<span data-ttu-id="621e5-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="621e5-123">CommonStates</span></span>|<span data-ttu-id="621e5-124"><xref:System.Windows.Controls.ProgressBar> Zobrazuje průběh na základě <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="621e5-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="621e5-125">Neurčitá</span><span class="sxs-lookup"><span data-stu-id="621e5-125">Indeterminate</span></span>|<span data-ttu-id="621e5-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="621e5-126">CommonStates</span></span>|<span data-ttu-id="621e5-127"><xref:System.Windows.Controls.ProgressBar> Zobrazuje obecný průběh se opakující se vzorem.</span><span class="sxs-lookup"><span data-stu-id="621e5-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="621e5-128">Platné</span><span class="sxs-lookup"><span data-stu-id="621e5-128">Valid</span></span>|<span data-ttu-id="621e5-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="621e5-129">ValidationStates</span></span>|<span data-ttu-id="621e5-130">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="621e5-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="621e5-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="621e5-131">InvalidFocused</span></span>|<span data-ttu-id="621e5-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="621e5-132">ValidationStates</span></span>|<span data-ttu-id="621e5-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="621e5-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="621e5-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="621e5-134">InvalidUnfocused</span></span>|<span data-ttu-id="621e5-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="621e5-135">ValidationStates</span></span>|<span data-ttu-id="621e5-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="621e5-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="621e5-137">Příklad šablony ControlTemplate ProgressBar</span><span class="sxs-lookup"><span data-stu-id="621e5-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="621e5-138">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="621e5-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="621e5-139">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="621e5-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="621e5-140">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="621e5-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="621e5-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="621e5-141">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="621e5-142">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="621e5-142">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="621e5-143">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="621e5-143">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="621e5-144">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="621e5-144">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="621e5-145">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="621e5-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
