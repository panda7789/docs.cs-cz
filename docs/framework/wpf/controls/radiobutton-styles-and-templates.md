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
ms.openlocfilehash: 384a587fe01fb69ff5d377f2aa34d03ff110880d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="radiobutton-styles-and-templates"></a><span data-ttu-id="f2231-102">RadioButton – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f2231-102">RadioButton Styles and Templates</span></span>
<span data-ttu-id="f2231-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.RadioButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2231-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.RadioButton> control.</span></span> <span data-ttu-id="f2231-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2231-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f2231-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f2231-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="radiobutton-parts"></a><span data-ttu-id="f2231-106">RadioButton částí</span><span class="sxs-lookup"><span data-stu-id="f2231-106">RadioButton Parts</span></span>  
 <span data-ttu-id="f2231-107"><xref:System.Windows.Controls.RadioButton> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="f2231-107">The <xref:System.Windows.Controls.RadioButton> control does not have any named parts.</span></span>  
  
## <a name="radiobutton-states"></a><span data-ttu-id="f2231-108">Stavy RadioButton</span><span class="sxs-lookup"><span data-stu-id="f2231-108">RadioButton States</span></span>  
 <span data-ttu-id="f2231-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.RadioButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2231-109">The following table lists the visual states for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
|<span data-ttu-id="f2231-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="f2231-110">VisualState Name</span></span>|<span data-ttu-id="f2231-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f2231-111">VisualStateGroup Name</span></span>|<span data-ttu-id="f2231-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f2231-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="f2231-113">Normální</span><span class="sxs-lookup"><span data-stu-id="f2231-113">Normal</span></span>|<span data-ttu-id="f2231-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f2231-114">CommonStates</span></span>|<span data-ttu-id="f2231-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="f2231-115">The default state.</span></span>|  
|<span data-ttu-id="f2231-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="f2231-116">MouseOver</span></span>|<span data-ttu-id="f2231-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f2231-117">CommonStates</span></span>|<span data-ttu-id="f2231-118">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2231-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f2231-119">Stisknutí tlačítka</span><span class="sxs-lookup"><span data-stu-id="f2231-119">Pressed</span></span>|<span data-ttu-id="f2231-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f2231-120">CommonStates</span></span>|<span data-ttu-id="f2231-121">Stisknutí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2231-121">The control is pressed.</span></span>|  
|<span data-ttu-id="f2231-122">zakázáno</span><span class="sxs-lookup"><span data-stu-id="f2231-122">Disabled</span></span>|<span data-ttu-id="f2231-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f2231-123">CommonStates</span></span>|<span data-ttu-id="f2231-124">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="f2231-124">The control is disabled.</span></span>|  
|<span data-ttu-id="f2231-125">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="f2231-125">Focused</span></span>|<span data-ttu-id="f2231-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f2231-126">FocusStates</span></span>|<span data-ttu-id="f2231-127">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="f2231-127">The control has focus.</span></span>|  
|<span data-ttu-id="f2231-128">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="f2231-128">Unfocused</span></span>|<span data-ttu-id="f2231-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f2231-129">FocusStates</span></span>|<span data-ttu-id="f2231-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="f2231-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="f2231-131">Zaškrtnutí</span><span class="sxs-lookup"><span data-stu-id="f2231-131">Checked</span></span>|<span data-ttu-id="f2231-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="f2231-132">CheckStates</span></span>|<span data-ttu-id="f2231-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>je `true`.</span><span class="sxs-lookup"><span data-stu-id="f2231-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="f2231-134">Nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="f2231-134">Unchecked</span></span>|<span data-ttu-id="f2231-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="f2231-135">CheckStates</span></span>|<span data-ttu-id="f2231-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>je `false`.</span><span class="sxs-lookup"><span data-stu-id="f2231-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="f2231-137">Neurčitém</span><span class="sxs-lookup"><span data-stu-id="f2231-137">Indeterminate</span></span>|<span data-ttu-id="f2231-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="f2231-138">CheckStates</span></span>|<span data-ttu-id="f2231-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>je `true`, a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `null`.</span><span class="sxs-lookup"><span data-stu-id="f2231-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="f2231-140">Platné</span><span class="sxs-lookup"><span data-stu-id="f2231-140">Valid</span></span>|<span data-ttu-id="f2231-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f2231-141">ValidationStates</span></span>|<span data-ttu-id="f2231-142">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="f2231-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f2231-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f2231-143">InvalidFocused</span></span>|<span data-ttu-id="f2231-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f2231-144">ValidationStates</span></span>|<span data-ttu-id="f2231-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="f2231-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f2231-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f2231-146">InvalidUnfocused</span></span>|<span data-ttu-id="f2231-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f2231-147">ValidationStates</span></span>|<span data-ttu-id="f2231-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="f2231-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="radiobutton-controltemplate-example"></a><span data-ttu-id="f2231-149">Příklad ControlTemplate RadioButton</span><span class="sxs-lookup"><span data-stu-id="f2231-149">RadioButton ControlTemplate Example</span></span>  
 <span data-ttu-id="f2231-150">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.RadioButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2231-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#RadioButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/radiobutton.xaml#radiobutton)]  
  
 <span data-ttu-id="f2231-151">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="f2231-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f2231-152">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="f2231-152">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2231-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2231-153">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="f2231-154">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="f2231-154">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="f2231-155">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f2231-155">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="f2231-156">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="f2231-156">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="f2231-157">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f2231-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
