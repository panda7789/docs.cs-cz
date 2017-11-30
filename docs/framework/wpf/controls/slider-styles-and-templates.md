---
title: "Styly a šablony posuvníku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9dfa340cf42e5e7ed105bf14eb0f7a24ea85a1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="0b4bc-102">Styly a šablony posuvníku</span><span class="sxs-lookup"><span data-stu-id="0b4bc-102">Slider Styles and Templates</span></span>
<span data-ttu-id="0b4bc-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="0b4bc-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="0b4bc-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="0b4bc-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="0b4bc-106">Části posuvníku</span><span class="sxs-lookup"><span data-stu-id="0b4bc-106">Slider Parts</span></span>  
 <span data-ttu-id="0b4bc-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="0b4bc-108">Část</span><span class="sxs-lookup"><span data-stu-id="0b4bc-108">Part</span></span>|<span data-ttu-id="0b4bc-109">Typ</span><span class="sxs-lookup"><span data-stu-id="0b4bc-109">Type</span></span>|<span data-ttu-id="0b4bc-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0b4bc-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0b4bc-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="0b4bc-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="0b4bc-112">Kontejner elementu, který označuje pozici <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="0b4bc-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="0b4bc-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="0b4bc-114">Element, který zobrazí výběr rozsahu společně <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="0b4bc-115">Výběr rozsahu je viditelná pouze v případě <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> vlastnost je `true`.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="0b4bc-116">Stavy posuvníku</span><span class="sxs-lookup"><span data-stu-id="0b4bc-116">Slider States</span></span>  
 <span data-ttu-id="0b4bc-117">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="0b4bc-118">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="0b4bc-118">VisualState Name</span></span>|<span data-ttu-id="0b4bc-119">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="0b4bc-119">VisualStateGroup Name</span></span>|<span data-ttu-id="0b4bc-120">Popis</span><span class="sxs-lookup"><span data-stu-id="0b4bc-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="0b4bc-121">Normální</span><span class="sxs-lookup"><span data-stu-id="0b4bc-121">Normal</span></span>|<span data-ttu-id="0b4bc-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0b4bc-122">CommonStates</span></span>|<span data-ttu-id="0b4bc-123">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-123">The default state.</span></span>|  
|<span data-ttu-id="0b4bc-124">Myš nad</span><span class="sxs-lookup"><span data-stu-id="0b4bc-124">MouseOver</span></span>|<span data-ttu-id="0b4bc-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0b4bc-125">CommonStates</span></span>|<span data-ttu-id="0b4bc-126">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="0b4bc-127">zakázáno</span><span class="sxs-lookup"><span data-stu-id="0b4bc-127">Disabled</span></span>|<span data-ttu-id="0b4bc-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0b4bc-128">CommonStates</span></span>|<span data-ttu-id="0b4bc-129">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-129">The control is disabled.</span></span>|  
|<span data-ttu-id="0b4bc-130">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="0b4bc-130">Focused</span></span>|<span data-ttu-id="0b4bc-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="0b4bc-131">FocusStates</span></span>|<span data-ttu-id="0b4bc-132">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-132">The control has focus.</span></span>|  
|<span data-ttu-id="0b4bc-133">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="0b4bc-133">Unfocused</span></span>|<span data-ttu-id="0b4bc-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="0b4bc-134">FocusStates</span></span>|<span data-ttu-id="0b4bc-135">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="0b4bc-136">Platné</span><span class="sxs-lookup"><span data-stu-id="0b4bc-136">Valid</span></span>|<span data-ttu-id="0b4bc-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0b4bc-137">ValidationStates</span></span>|<span data-ttu-id="0b4bc-138">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="0b4bc-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="0b4bc-139">InvalidFocused</span></span>|<span data-ttu-id="0b4bc-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0b4bc-140">ValidationStates</span></span>|<span data-ttu-id="0b4bc-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="0b4bc-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="0b4bc-142">InvalidUnfocused</span></span>|<span data-ttu-id="0b4bc-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0b4bc-143">ValidationStates</span></span>|<span data-ttu-id="0b4bc-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="0b4bc-145">Příklad ControlTemplate posuvníku</span><span class="sxs-lookup"><span data-stu-id="0b4bc-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="0b4bc-146">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Slider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="0b4bc-147">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="0b4bc-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="0b4bc-148">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="0b4bc-148">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b4bc-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b4bc-149">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="0b4bc-150">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="0b4bc-150">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="0b4bc-151">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="0b4bc-151">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="0b4bc-152">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="0b4bc-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="0b4bc-153">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="0b4bc-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
