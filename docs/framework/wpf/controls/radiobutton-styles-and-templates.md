---
title: "RadioButton – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], RadioButton
- RadioButton [WPF], styles and templates
- ControlTemplate [WPF], RadioButton
- states [WPF], RadioButton
- templates [WPF], RadioButton
- parts [WPF], RadioButton
ms.assetid: 9acf93f7-dd2f-4010-8ce0-1edd81c52ae2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 05b5f2124e6d8817b03171af5308c116e9339ecb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="radiobutton-styles-and-templates"></a><span data-ttu-id="d9beb-102">RadioButton – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d9beb-102">RadioButton Styles and Templates</span></span>
<span data-ttu-id="d9beb-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.RadioButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9beb-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.RadioButton> control.</span></span> <span data-ttu-id="d9beb-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9beb-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d9beb-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d9beb-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="radiobutton-parts"></a><span data-ttu-id="d9beb-106">RadioButton částí</span><span class="sxs-lookup"><span data-stu-id="d9beb-106">RadioButton Parts</span></span>  
 <span data-ttu-id="d9beb-107"><xref:System.Windows.Controls.RadioButton> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="d9beb-107">The <xref:System.Windows.Controls.RadioButton> control does not have any named parts.</span></span>  
  
## <a name="radiobutton-states"></a><span data-ttu-id="d9beb-108">Stavy RadioButton</span><span class="sxs-lookup"><span data-stu-id="d9beb-108">RadioButton States</span></span>  
 <span data-ttu-id="d9beb-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.RadioButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9beb-109">The following table lists the visual states for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
|<span data-ttu-id="d9beb-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="d9beb-110">VisualState Name</span></span>|<span data-ttu-id="d9beb-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d9beb-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d9beb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d9beb-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="d9beb-113">Normální</span><span class="sxs-lookup"><span data-stu-id="d9beb-113">Normal</span></span>|<span data-ttu-id="d9beb-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-114">CommonStates</span></span>|<span data-ttu-id="d9beb-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="d9beb-115">The default state.</span></span>|  
|<span data-ttu-id="d9beb-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="d9beb-116">MouseOver</span></span>|<span data-ttu-id="d9beb-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-117">CommonStates</span></span>|<span data-ttu-id="d9beb-118">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9beb-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="d9beb-119">Stisknutí tlačítka</span><span class="sxs-lookup"><span data-stu-id="d9beb-119">Pressed</span></span>|<span data-ttu-id="d9beb-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-120">CommonStates</span></span>|<span data-ttu-id="d9beb-121">Stisknutí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9beb-121">The control is pressed.</span></span>|  
|<span data-ttu-id="d9beb-122">zakázáno</span><span class="sxs-lookup"><span data-stu-id="d9beb-122">Disabled</span></span>|<span data-ttu-id="d9beb-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-123">CommonStates</span></span>|<span data-ttu-id="d9beb-124">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="d9beb-124">The control is disabled.</span></span>|  
|<span data-ttu-id="d9beb-125">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="d9beb-125">Focused</span></span>|<span data-ttu-id="d9beb-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-126">FocusStates</span></span>|<span data-ttu-id="d9beb-127">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="d9beb-127">The control has focus.</span></span>|  
|<span data-ttu-id="d9beb-128">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="d9beb-128">Unfocused</span></span>|<span data-ttu-id="d9beb-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-129">FocusStates</span></span>|<span data-ttu-id="d9beb-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d9beb-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="d9beb-131">Zaškrtnutí</span><span class="sxs-lookup"><span data-stu-id="d9beb-131">Checked</span></span>|<span data-ttu-id="d9beb-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-132">CheckStates</span></span>|<span data-ttu-id="d9beb-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>je `true`.</span><span class="sxs-lookup"><span data-stu-id="d9beb-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="d9beb-134">Nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="d9beb-134">Unchecked</span></span>|<span data-ttu-id="d9beb-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-135">CheckStates</span></span>|<span data-ttu-id="d9beb-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>je `false`.</span><span class="sxs-lookup"><span data-stu-id="d9beb-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="d9beb-137">Neurčitém</span><span class="sxs-lookup"><span data-stu-id="d9beb-137">Indeterminate</span></span>|<span data-ttu-id="d9beb-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-138">CheckStates</span></span>|<span data-ttu-id="d9beb-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>je `true`, a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `null`.</span><span class="sxs-lookup"><span data-stu-id="d9beb-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="d9beb-140">Platné</span><span class="sxs-lookup"><span data-stu-id="d9beb-140">Valid</span></span>|<span data-ttu-id="d9beb-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-141">ValidationStates</span></span>|<span data-ttu-id="d9beb-142">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="d9beb-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d9beb-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d9beb-143">InvalidFocused</span></span>|<span data-ttu-id="d9beb-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-144">ValidationStates</span></span>|<span data-ttu-id="d9beb-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="d9beb-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d9beb-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d9beb-146">InvalidUnfocused</span></span>|<span data-ttu-id="d9beb-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9beb-147">ValidationStates</span></span>|<span data-ttu-id="d9beb-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d9beb-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="radiobutton-controltemplate-example"></a><span data-ttu-id="d9beb-149">Příklad ControlTemplate RadioButton</span><span class="sxs-lookup"><span data-stu-id="d9beb-149">RadioButton ControlTemplate Example</span></span>  
 <span data-ttu-id="d9beb-150">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.RadioButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9beb-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#RadioButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/radiobutton.xaml#radiobutton)]  
  
 <span data-ttu-id="d9beb-151">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="d9beb-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d9beb-152">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="d9beb-152">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9beb-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9beb-153">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d9beb-154">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="d9beb-154">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d9beb-155">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d9beb-155">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d9beb-156">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d9beb-156">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d9beb-157">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d9beb-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
