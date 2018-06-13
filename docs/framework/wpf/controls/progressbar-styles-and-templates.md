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
ms.openlocfilehash: 89aea3e80fe17ece8a17f62f62290d34ddd55c60
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
ms.locfileid: "34456920"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="9c4c4-102">ProgressBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="9c4c4-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="9c4c4-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="9c4c4-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9c4c4-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="9c4c4-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="9c4c4-106">ProgressBar – součásti</span><span class="sxs-lookup"><span data-stu-id="9c4c4-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="9c4c4-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="9c4c4-108">Část</span><span class="sxs-lookup"><span data-stu-id="9c4c4-108">Part</span></span>|<span data-ttu-id="9c4c4-109">Typ</span><span class="sxs-lookup"><span data-stu-id="9c4c4-109">Type</span></span>|<span data-ttu-id="9c4c4-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9c4c4-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9c4c4-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="9c4c4-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="9c4c4-112">Objekt, který označuje průběh.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="9c4c4-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="9c4c4-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="9c4c4-114">Objekt, který definuje cestu indikátoru průběhu.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="9c4c4-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="9c4c4-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="9c4c4-116">Objekt, který embellishes indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="9c4c4-117">ProgressBar – stavy</span><span class="sxs-lookup"><span data-stu-id="9c4c4-117">ProgressBar States</span></span>  
 <span data-ttu-id="9c4c4-118">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="9c4c4-119">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="9c4c4-119">VisualState Name</span></span>|<span data-ttu-id="9c4c4-120">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="9c4c4-120">VisualStateGroup Name</span></span>|<span data-ttu-id="9c4c4-121">Popis</span><span class="sxs-lookup"><span data-stu-id="9c4c4-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="9c4c4-122">Determinate</span><span class="sxs-lookup"><span data-stu-id="9c4c4-122">Determinate</span></span>|<span data-ttu-id="9c4c4-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="9c4c4-123">CommonStates</span></span>|<span data-ttu-id="9c4c4-124"><xref:System.Windows.Controls.ProgressBar> sestavy průběhu na základě <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="9c4c4-125">Neurčitém</span><span class="sxs-lookup"><span data-stu-id="9c4c4-125">Indeterminate</span></span>|<span data-ttu-id="9c4c4-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="9c4c4-126">CommonStates</span></span>|<span data-ttu-id="9c4c4-127"><xref:System.Windows.Controls.ProgressBar> sestavy obecný postup s opakující se vzorek.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="9c4c4-128">Platné</span><span class="sxs-lookup"><span data-stu-id="9c4c4-128">Valid</span></span>|<span data-ttu-id="9c4c4-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9c4c4-129">ValidationStates</span></span>|<span data-ttu-id="9c4c4-130">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9c4c4-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9c4c4-131">InvalidFocused</span></span>|<span data-ttu-id="9c4c4-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9c4c4-132">ValidationStates</span></span>|<span data-ttu-id="9c4c4-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="9c4c4-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9c4c4-134">InvalidUnfocused</span></span>|<span data-ttu-id="9c4c4-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9c4c4-135">ValidationStates</span></span>|<span data-ttu-id="9c4c4-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="9c4c4-137">Příklad ControlTemplate ProgressBar</span><span class="sxs-lookup"><span data-stu-id="9c4c4-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="9c4c4-138">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="9c4c4-139">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="9c4c4-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9c4c4-140">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="9c4c4-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c4c4-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c4c4-141">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="9c4c4-142">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="9c4c4-142">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="9c4c4-143">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="9c4c4-143">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="9c4c4-144">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="9c4c4-144">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="9c4c4-145">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="9c4c4-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
