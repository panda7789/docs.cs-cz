---
title: "CheckBox – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], CheckBox
- templates [WPF], CheckBox
- parts [WPF], CheckBox
- ControlTemplate [WPF], CheckBox
- CheckBox [WPF], styles and templates
- styles [WPF], CheckBox
ms.assetid: bfdaec96-d101-4d3d-864d-c27e6b621d03
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c901d710e96cd111104b9fef2219b157377adc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="checkbox-styles-and-templates"></a><span data-ttu-id="c2bd7-102">CheckBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="c2bd7-102">CheckBox Styles and Templates</span></span>
<span data-ttu-id="c2bd7-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.CheckBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.CheckBox> control.</span></span> <span data-ttu-id="c2bd7-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c2bd7-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c2bd7-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="checkbox-parts"></a><span data-ttu-id="c2bd7-106">Zaškrtávací políčko částí</span><span class="sxs-lookup"><span data-stu-id="c2bd7-106">CheckBox Parts</span></span>  
 <span data-ttu-id="c2bd7-107"><xref:System.Windows.Controls.CheckBox> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-107">The <xref:System.Windows.Controls.CheckBox> control does not have any named parts.</span></span>  
  
## <a name="checkbox-states"></a><span data-ttu-id="c2bd7-108">Stavy zaškrtávacího políčka</span><span class="sxs-lookup"><span data-stu-id="c2bd7-108">CheckBox States</span></span>  
 <span data-ttu-id="c2bd7-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.CheckBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-109">The following table lists the visual states for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
|<span data-ttu-id="c2bd7-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="c2bd7-110">VisualState Name</span></span>|<span data-ttu-id="c2bd7-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c2bd7-111">VisualStateGroup Name</span></span>|<span data-ttu-id="c2bd7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c2bd7-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="c2bd7-113">Normální</span><span class="sxs-lookup"><span data-stu-id="c2bd7-113">Normal</span></span>|<span data-ttu-id="c2bd7-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-114">CommonStates</span></span>|<span data-ttu-id="c2bd7-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-115">The default state.</span></span>|  
|<span data-ttu-id="c2bd7-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="c2bd7-116">MouseOver</span></span>|<span data-ttu-id="c2bd7-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-117">CommonStates</span></span>|<span data-ttu-id="c2bd7-118">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="c2bd7-119">Stisknutí tlačítka</span><span class="sxs-lookup"><span data-stu-id="c2bd7-119">Pressed</span></span>|<span data-ttu-id="c2bd7-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-120">CommonStates</span></span>|<span data-ttu-id="c2bd7-121">Stisknutí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-121">The control is pressed.</span></span>|  
|<span data-ttu-id="c2bd7-122">zakázáno</span><span class="sxs-lookup"><span data-stu-id="c2bd7-122">Disabled</span></span>|<span data-ttu-id="c2bd7-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-123">CommonStates</span></span>|<span data-ttu-id="c2bd7-124">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-124">The control is disabled.</span></span>|  
|<span data-ttu-id="c2bd7-125">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="c2bd7-125">Focused</span></span>|<span data-ttu-id="c2bd7-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-126">FocusStates</span></span>|<span data-ttu-id="c2bd7-127">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-127">The control has focus.</span></span>|  
|<span data-ttu-id="c2bd7-128">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="c2bd7-128">Unfocused</span></span>|<span data-ttu-id="c2bd7-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-129">FocusStates</span></span>|<span data-ttu-id="c2bd7-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="c2bd7-131">Zaškrtnutí</span><span class="sxs-lookup"><span data-stu-id="c2bd7-131">Checked</span></span>|<span data-ttu-id="c2bd7-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-132">CheckStates</span></span>|<span data-ttu-id="c2bd7-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>je `true`.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="c2bd7-134">Nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="c2bd7-134">Unchecked</span></span>|<span data-ttu-id="c2bd7-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-135">CheckStates</span></span>|<span data-ttu-id="c2bd7-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>je `false`.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="c2bd7-137">Neurčitém</span><span class="sxs-lookup"><span data-stu-id="c2bd7-137">Indeterminate</span></span>|<span data-ttu-id="c2bd7-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-138">CheckStates</span></span>|<span data-ttu-id="c2bd7-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>je `true`, a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `null`.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="c2bd7-140">Platné</span><span class="sxs-lookup"><span data-stu-id="c2bd7-140">Valid</span></span>|<span data-ttu-id="c2bd7-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-141">ValidationStates</span></span>|<span data-ttu-id="c2bd7-142">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c2bd7-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c2bd7-143">InvalidUnfocused</span></span>|<span data-ttu-id="c2bd7-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-144">ValidationStates</span></span>|<span data-ttu-id="c2bd7-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c2bd7-146">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c2bd7-146">InvalidFocused</span></span>|<span data-ttu-id="c2bd7-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c2bd7-147">ValidationStates</span></span>|<span data-ttu-id="c2bd7-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="checkbox-controltemplate-example"></a><span data-ttu-id="c2bd7-149">Příklad zaškrtávacího políčka ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c2bd7-149">CheckBox ControlTemplate Example</span></span>  
 <span data-ttu-id="c2bd7-150">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.CheckBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#CheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/checkbox.xaml#checkbox)]  
  
 <span data-ttu-id="c2bd7-151">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="c2bd7-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c2bd7-152">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="c2bd7-152">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2bd7-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2bd7-153">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c2bd7-154">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="c2bd7-154">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="c2bd7-155">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c2bd7-155">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="c2bd7-156">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="c2bd7-156">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c2bd7-157">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c2bd7-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
