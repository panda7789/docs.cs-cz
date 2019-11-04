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
ms.openlocfilehash: 3a1bea39ba9b6d2cff9937a3fee1d1de41daf16b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459882"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="9bfd7-102">ProgressBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="9bfd7-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="9bfd7-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="9bfd7-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9bfd7-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="9bfd7-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="9bfd7-106">Součásti ProgressBar</span><span class="sxs-lookup"><span data-stu-id="9bfd7-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="9bfd7-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="9bfd7-108">Částí</span><span class="sxs-lookup"><span data-stu-id="9bfd7-108">Part</span></span>|<span data-ttu-id="9bfd7-109">Typ</span><span class="sxs-lookup"><span data-stu-id="9bfd7-109">Type</span></span>|<span data-ttu-id="9bfd7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9bfd7-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9bfd7-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="9bfd7-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="9bfd7-112">Objekt, který označuje průběh.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="9bfd7-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="9bfd7-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="9bfd7-114">Objekt, který definuje cestu indikátoru průběhu.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="9bfd7-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="9bfd7-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="9bfd7-116">Objekt, který embellishes indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="9bfd7-117">Stavy ProgressBar</span><span class="sxs-lookup"><span data-stu-id="9bfd7-117">ProgressBar States</span></span>  
 <span data-ttu-id="9bfd7-118">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="9bfd7-119">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="9bfd7-119">VisualState Name</span></span>|<span data-ttu-id="9bfd7-120">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="9bfd7-120">VisualStateGroup Name</span></span>|<span data-ttu-id="9bfd7-121">Popis</span><span class="sxs-lookup"><span data-stu-id="9bfd7-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="9bfd7-122">Zrušit ukončení</span><span class="sxs-lookup"><span data-stu-id="9bfd7-122">Determinate</span></span>|<span data-ttu-id="9bfd7-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="9bfd7-123">CommonStates</span></span>|<span data-ttu-id="9bfd7-124"><xref:System.Windows.Controls.ProgressBar> sestaví průběh na základě vlastnosti <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="9bfd7-125">Definované</span><span class="sxs-lookup"><span data-stu-id="9bfd7-125">Indeterminate</span></span>|<span data-ttu-id="9bfd7-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="9bfd7-126">CommonStates</span></span>|<span data-ttu-id="9bfd7-127"><xref:System.Windows.Controls.ProgressBar> sestavuje obecný průběh pomocí opakujícího se vzoru.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="9bfd7-128">Platné</span><span class="sxs-lookup"><span data-stu-id="9bfd7-128">Valid</span></span>|<span data-ttu-id="9bfd7-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9bfd7-129">ValidationStates</span></span>|<span data-ttu-id="9bfd7-130">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9bfd7-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9bfd7-131">InvalidFocused</span></span>|<span data-ttu-id="9bfd7-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9bfd7-132">ValidationStates</span></span>|<span data-ttu-id="9bfd7-133">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="9bfd7-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9bfd7-134">InvalidUnfocused</span></span>|<span data-ttu-id="9bfd7-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9bfd7-135">ValidationStates</span></span>|<span data-ttu-id="9bfd7-136">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="9bfd7-137">Příklad ControlTemplate ProgressBar</span><span class="sxs-lookup"><span data-stu-id="9bfd7-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="9bfd7-138">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="9bfd7-139">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="9bfd7-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9bfd7-140">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="9bfd7-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bfd7-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9bfd7-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="9bfd7-142">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="9bfd7-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="9bfd7-143">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="9bfd7-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="9bfd7-144">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="9bfd7-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="9bfd7-145">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="9bfd7-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
