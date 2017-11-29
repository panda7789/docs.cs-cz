---
title: "ListBox – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df974b2f6f89c3b62c5039be9cde144d9ef62d14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="listbox-styles-and-templates"></a><span data-ttu-id="2d3f3-102">ListBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="2d3f3-102">ListBox Styles and Templates</span></span>
<span data-ttu-id="2d3f3-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="2d3f3-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2d3f3-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="2d3f3-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="listbox-parts"></a><span data-ttu-id="2d3f3-106">ListBox – součásti</span><span class="sxs-lookup"><span data-stu-id="2d3f3-106">ListBox Parts</span></span>  
 <span data-ttu-id="2d3f3-107"><xref:System.Windows.Controls.ListBox> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-107">The <xref:System.Windows.Controls.ListBox> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="2d3f3-108">Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ListBox>, může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ListBox>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="2d3f3-109">( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí jednotlivé položky <xref:System.Windows.Controls.ListBox>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).</span><span class="sxs-lookup"><span data-stu-id="2d3f3-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ListBox>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="2d3f3-110">Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímými podřízenými z <xref:System.Windows.Controls.ScrollViewer>, musíte <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="listbox-states"></a><span data-ttu-id="2d3f3-111">ListBox – stavy</span><span class="sxs-lookup"><span data-stu-id="2d3f3-111">ListBox States</span></span>  
 <span data-ttu-id="2d3f3-112">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-112">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="2d3f3-113">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="2d3f3-113">VisualState Name</span></span>|<span data-ttu-id="2d3f3-114">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="2d3f3-114">VisualStateGroup Name</span></span>|<span data-ttu-id="2d3f3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2d3f3-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2d3f3-116">Platné</span><span class="sxs-lookup"><span data-stu-id="2d3f3-116">Valid</span></span>|<span data-ttu-id="2d3f3-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-117">ValidationStates</span></span>|<span data-ttu-id="2d3f3-118">Ovládací prvek je platný.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-118">The control is valid.</span></span>|  
|<span data-ttu-id="2d3f3-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2d3f3-119">InvalidFocused</span></span>|<span data-ttu-id="2d3f3-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-120">ValidationStates</span></span>|<span data-ttu-id="2d3f3-121">Ovládací prvek není platný a má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-121">The control is not valid and has focus.</span></span>|  
|<span data-ttu-id="2d3f3-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2d3f3-122">InvalidUnfocused</span></span>|<span data-ttu-id="2d3f3-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-123">ValidationStates</span></span>|<span data-ttu-id="2d3f3-124">Ovládací prvek není platný a nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-124">The control is not valid and does not have focus.</span></span>|  
  
## <a name="listboxitem-parts"></a><span data-ttu-id="2d3f3-125">ListBoxItem částí</span><span class="sxs-lookup"><span data-stu-id="2d3f3-125">ListBoxItem Parts</span></span>  
 <span data-ttu-id="2d3f3-126"><xref:System.Windows.Controls.ListBoxItem> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-126">The <xref:System.Windows.Controls.ListBoxItem> control does not have any named parts.</span></span>  
  
## <a name="listboxitem-states"></a><span data-ttu-id="2d3f3-127">ListBoxItem stavy</span><span class="sxs-lookup"><span data-stu-id="2d3f3-127">ListBoxItem States</span></span>  
 <span data-ttu-id="2d3f3-128">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-128">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="2d3f3-129">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="2d3f3-129">VisualState Name</span></span>|<span data-ttu-id="2d3f3-130">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="2d3f3-130">VisualStateGroup Name</span></span>|<span data-ttu-id="2d3f3-131">Popis</span><span class="sxs-lookup"><span data-stu-id="2d3f3-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2d3f3-132">Normální</span><span class="sxs-lookup"><span data-stu-id="2d3f3-132">Normal</span></span>|<span data-ttu-id="2d3f3-133">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-133">CommonStates</span></span>|<span data-ttu-id="2d3f3-134">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-134">The default state.</span></span>|  
|<span data-ttu-id="2d3f3-135">Myš nad</span><span class="sxs-lookup"><span data-stu-id="2d3f3-135">MouseOver</span></span>|<span data-ttu-id="2d3f3-136">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-136">CommonStates</span></span>|<span data-ttu-id="2d3f3-137">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-137">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="2d3f3-138">zakázáno</span><span class="sxs-lookup"><span data-stu-id="2d3f3-138">Disabled</span></span>|<span data-ttu-id="2d3f3-139">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-139">CommonStates</span></span>|<span data-ttu-id="2d3f3-140">Položka je zakázána.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-140">The item is disabled.</span></span>|  
|<span data-ttu-id="2d3f3-141">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="2d3f3-141">Focused</span></span>|<span data-ttu-id="2d3f3-142">FocusStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-142">FocusStates</span></span>|<span data-ttu-id="2d3f3-143">Položka má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-143">The item has focus.</span></span>|  
|<span data-ttu-id="2d3f3-144">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="2d3f3-144">Unfocused</span></span>|<span data-ttu-id="2d3f3-145">FocusStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-145">FocusStates</span></span>|<span data-ttu-id="2d3f3-146">Položka nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-146">The item does not have focus.</span></span>|  
|<span data-ttu-id="2d3f3-147">Nezaškrtnuté</span><span class="sxs-lookup"><span data-stu-id="2d3f3-147">Unselected</span></span>|<span data-ttu-id="2d3f3-148">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-148">SelectionStates</span></span>|<span data-ttu-id="2d3f3-149">Položka není vybrána.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-149">The item is not selected.</span></span>|  
|<span data-ttu-id="2d3f3-150">Vybrané</span><span class="sxs-lookup"><span data-stu-id="2d3f3-150">Selected</span></span>|<span data-ttu-id="2d3f3-151">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-151">SelectionStates</span></span>|<span data-ttu-id="2d3f3-152">Položka se currentlyplate vybrané.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-152">The item is currentlyplate selected.</span></span>|  
|<span data-ttu-id="2d3f3-153">SelectedUnfocused</span><span class="sxs-lookup"><span data-stu-id="2d3f3-153">SelectedUnfocused</span></span>|<span data-ttu-id="2d3f3-154">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-154">SelectionStates</span></span>|<span data-ttu-id="2d3f3-155">Položka je vybrána, ale nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-155">The item is selected, but does not have focus.</span></span>|  
|<span data-ttu-id="2d3f3-156">Platné</span><span class="sxs-lookup"><span data-stu-id="2d3f3-156">Valid</span></span>|<span data-ttu-id="2d3f3-157">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-157">ValidationStates</span></span>|<span data-ttu-id="2d3f3-158">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-158">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2d3f3-159">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2d3f3-159">InvalidFocused</span></span>|<span data-ttu-id="2d3f3-160">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-160">ValidationStates</span></span>|<span data-ttu-id="2d3f3-161"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-161">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2d3f3-162">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2d3f3-162">InvalidUnfocused</span></span>|<span data-ttu-id="2d3f3-163">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d3f3-163">ValidationStates</span></span>|<span data-ttu-id="2d3f3-164"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-164">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listbox-controltemplate-example"></a><span data-ttu-id="2d3f3-165">Příklad ControlTemplate ListBox</span><span class="sxs-lookup"><span data-stu-id="2d3f3-165">ListBox ControlTemplate Example</span></span>  
 <span data-ttu-id="2d3f3-166">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ListBoxItem> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-166">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ListBox> and <xref:System.Windows.Controls.ListBoxItem> controls.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 <span data-ttu-id="2d3f3-167">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="2d3f3-167">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2d3f3-168">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="2d3f3-168">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d3f3-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d3f3-169">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="2d3f3-170">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="2d3f3-170">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="2d3f3-171">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="2d3f3-171">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="2d3f3-172">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="2d3f3-172">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="2d3f3-173">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="2d3f3-173">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
