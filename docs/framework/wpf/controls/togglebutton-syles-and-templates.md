---
title: "ToggleButton – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ecd6696ff9d62b4aa3397ac8567edc3fb387ba96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="togglebutton-syles-and-templates"></a><span data-ttu-id="80956-102">ToggleButton – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="80956-102">ToggleButton Syles and Templates</span></span>
<span data-ttu-id="80956-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.ToggleButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="80956-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="80956-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="80956-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="80956-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="80956-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="togglebutton-parts"></a><span data-ttu-id="80956-106">Přepínací tlačítko částí</span><span class="sxs-lookup"><span data-stu-id="80956-106">ToggleButton Parts</span></span>  
 <span data-ttu-id="80956-107"><xref:System.Windows.Controls.Primitives.ToggleButton> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="80956-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>  
  
## <a name="togglebutton-states"></a><span data-ttu-id="80956-108">Přepínací tlačítko stavy</span><span class="sxs-lookup"><span data-stu-id="80956-108">ToggleButton States</span></span>  
 <span data-ttu-id="80956-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.ToggleButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="80956-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
|<span data-ttu-id="80956-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="80956-110">VisualState Name</span></span>|<span data-ttu-id="80956-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="80956-111">VisualStateGroup Name</span></span>|<span data-ttu-id="80956-112">Popis</span><span class="sxs-lookup"><span data-stu-id="80956-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="80956-113">Normální</span><span class="sxs-lookup"><span data-stu-id="80956-113">Normal</span></span>|<span data-ttu-id="80956-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="80956-114">CommonStates</span></span>|<span data-ttu-id="80956-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="80956-115">The default state.</span></span>|  
|<span data-ttu-id="80956-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="80956-116">MouseOver</span></span>|<span data-ttu-id="80956-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="80956-117">CommonStates</span></span>|<span data-ttu-id="80956-118">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="80956-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="80956-119">Stisknutí tlačítka</span><span class="sxs-lookup"><span data-stu-id="80956-119">Pressed</span></span>|<span data-ttu-id="80956-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="80956-120">CommonStates</span></span>|<span data-ttu-id="80956-121">Stisknutí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="80956-121">The control is pressed.</span></span>|  
|<span data-ttu-id="80956-122">zakázáno</span><span class="sxs-lookup"><span data-stu-id="80956-122">Disabled</span></span>|<span data-ttu-id="80956-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="80956-123">CommonStates</span></span>|<span data-ttu-id="80956-124">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="80956-124">The control is disabled.</span></span>|  
|<span data-ttu-id="80956-125">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="80956-125">Focused</span></span>|<span data-ttu-id="80956-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="80956-126">FocusStates</span></span>|<span data-ttu-id="80956-127">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="80956-127">The control has focus.</span></span>|  
|<span data-ttu-id="80956-128">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="80956-128">Unfocused</span></span>|<span data-ttu-id="80956-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="80956-129">FocusStates</span></span>|<span data-ttu-id="80956-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="80956-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="80956-131">Zaškrtnutí</span><span class="sxs-lookup"><span data-stu-id="80956-131">Checked</span></span>|<span data-ttu-id="80956-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="80956-132">CheckStates</span></span>|<span data-ttu-id="80956-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>je `true`.</span><span class="sxs-lookup"><span data-stu-id="80956-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="80956-134">Nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="80956-134">Unchecked</span></span>|<span data-ttu-id="80956-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="80956-135">CheckStates</span></span>|<span data-ttu-id="80956-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>je `false`.</span><span class="sxs-lookup"><span data-stu-id="80956-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="80956-137">Neurčitém</span><span class="sxs-lookup"><span data-stu-id="80956-137">Indeterminate</span></span>|<span data-ttu-id="80956-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="80956-138">CheckStates</span></span>|<span data-ttu-id="80956-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>je `true`, a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `null`.</span><span class="sxs-lookup"><span data-stu-id="80956-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="80956-140">Platné</span><span class="sxs-lookup"><span data-stu-id="80956-140">Valid</span></span>|<span data-ttu-id="80956-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="80956-141">ValidationStates</span></span>|<span data-ttu-id="80956-142">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="80956-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="80956-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="80956-143">InvalidFocused</span></span>|<span data-ttu-id="80956-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="80956-144">ValidationStates</span></span>|<span data-ttu-id="80956-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="80956-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="80956-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="80956-146">InvalidUnfocused</span></span>|<span data-ttu-id="80956-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="80956-147">ValidationStates</span></span>|<span data-ttu-id="80956-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="80956-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="80956-149">Pokud neurčitého stavu visual v šabloně ovládací prvek neexistuje, bude stav nezaškrtnuté visual použít jako výchozí visual stav.</span><span class="sxs-lookup"><span data-stu-id="80956-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>  
  
## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="80956-150">Přepínací tlačítko ControlTemplate příklad</span><span class="sxs-lookup"><span data-stu-id="80956-150">ToggleButton ControlTemplate Example</span></span>  
 <span data-ttu-id="80956-151">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.ToggleButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="80956-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToggleButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
 <span data-ttu-id="80956-152">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="80956-152">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="80956-153">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="80956-153">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80956-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="80956-154">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="80956-155">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="80956-155">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="80956-156">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="80956-156">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="80956-157">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="80956-157">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="80956-158">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="80956-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
