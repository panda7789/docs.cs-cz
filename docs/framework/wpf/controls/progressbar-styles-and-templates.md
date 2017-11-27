---
title: "ProgressBar – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 475607381f16d7b42f26f12809a11d5eaf4e74bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="ddfe4-102">ProgressBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="ddfe4-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="ddfe4-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="ddfe4-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ddfe4-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ddfe4-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="ddfe4-106">ProgressBar – součásti</span><span class="sxs-lookup"><span data-stu-id="ddfe4-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="ddfe4-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="ddfe4-108">Část</span><span class="sxs-lookup"><span data-stu-id="ddfe4-108">Part</span></span>|<span data-ttu-id="ddfe4-109">Typ</span><span class="sxs-lookup"><span data-stu-id="ddfe4-109">Type</span></span>|<span data-ttu-id="ddfe4-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ddfe4-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ddfe4-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="ddfe4-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="ddfe4-112">Objekt, který označuje průběh.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="ddfe4-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="ddfe4-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="ddfe4-114">Objekt, který definuje cestu indikátoru průběhu.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="ddfe4-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="ddfe4-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="ddfe4-116">Objekt, který embellishes indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="ddfe4-117">ProgressBar – stavy</span><span class="sxs-lookup"><span data-stu-id="ddfe4-117">ProgressBar States</span></span>  
 <span data-ttu-id="ddfe4-118">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="ddfe4-119">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="ddfe4-119">VisualState Name</span></span>|<span data-ttu-id="ddfe4-120">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ddfe4-120">VisualStateGroup Name</span></span>|<span data-ttu-id="ddfe4-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ddfe4-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="ddfe4-122">Determinate</span><span class="sxs-lookup"><span data-stu-id="ddfe4-122">Determinate</span></span>|<span data-ttu-id="ddfe4-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ddfe4-123">CommonStates</span></span>|<span data-ttu-id="ddfe4-124"><xref:System.Windows.Controls.ProgressBar>sestavy průběhu na základě <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="ddfe4-125">Neurčitém</span><span class="sxs-lookup"><span data-stu-id="ddfe4-125">Indeterminate</span></span>|<span data-ttu-id="ddfe4-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ddfe4-126">CommonStates</span></span>|<span data-ttu-id="ddfe4-127"><xref:System.Windows.Controls.ProgressBar>sestavy obecný postup s opakující se vzorek.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="ddfe4-128">Platné</span><span class="sxs-lookup"><span data-stu-id="ddfe4-128">Valid</span></span>|<span data-ttu-id="ddfe4-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ddfe4-129">ValidationStates</span></span>|<span data-ttu-id="ddfe4-130">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ddfe4-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ddfe4-131">InvalidFocused</span></span>|<span data-ttu-id="ddfe4-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ddfe4-132">ValidationStates</span></span>|<span data-ttu-id="ddfe4-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ddfe4-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ddfe4-134">InvalidUnfocused</span></span>|<span data-ttu-id="ddfe4-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ddfe4-135">ValidationStates</span></span>|<span data-ttu-id="ddfe4-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="ddfe4-137">Příklad ControlTemplate ProgressBar</span><span class="sxs-lookup"><span data-stu-id="ddfe4-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="ddfe4-138">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ProgressBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="ddfe4-139">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="ddfe4-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ddfe4-140">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="ddfe4-140">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddfe4-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddfe4-141">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="ddfe4-142">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="ddfe4-142">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="ddfe4-143">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ddfe4-143">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="ddfe4-144">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="ddfe4-144">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="ddfe4-145">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="ddfe4-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
