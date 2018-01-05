---
title: "Styly a šablony jezdce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 780ddc07c79aab111c17f9e7e551cfde85c68f3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="d0ac4-102">Styly a šablony jezdce</span><span class="sxs-lookup"><span data-stu-id="d0ac4-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="d0ac4-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="d0ac4-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d0ac4-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d0ac4-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="d0ac4-106">Jezdec částí</span><span class="sxs-lookup"><span data-stu-id="d0ac4-106">Thumb Parts</span></span>  
 <span data-ttu-id="d0ac4-107"><xref:System.Windows.Controls.Primitives.Thumb> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="d0ac4-108">Jezdec stavy</span><span class="sxs-lookup"><span data-stu-id="d0ac4-108">Thumb States</span></span>  
 <span data-ttu-id="d0ac4-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="d0ac4-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="d0ac4-110">VisualState Name</span></span>|<span data-ttu-id="d0ac4-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d0ac4-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d0ac4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d0ac4-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d0ac4-113">Normální</span><span class="sxs-lookup"><span data-stu-id="d0ac4-113">Normal</span></span>|<span data-ttu-id="d0ac4-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d0ac4-114">CommonStates</span></span>|<span data-ttu-id="d0ac4-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-115">The default state.</span></span>|  
|<span data-ttu-id="d0ac4-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="d0ac4-116">MouseOver</span></span>|<span data-ttu-id="d0ac4-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d0ac4-117">CommonStates</span></span>|<span data-ttu-id="d0ac4-118">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="d0ac4-119">Stisknutí tlačítka</span><span class="sxs-lookup"><span data-stu-id="d0ac4-119">Pressed</span></span>|<span data-ttu-id="d0ac4-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d0ac4-120">CommonStates</span></span>|<span data-ttu-id="d0ac4-121">Stisknutí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-121">The control is pressed.</span></span>|  
|<span data-ttu-id="d0ac4-122">zakázáno</span><span class="sxs-lookup"><span data-stu-id="d0ac4-122">Disabled</span></span>|<span data-ttu-id="d0ac4-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d0ac4-123">CommonStates</span></span>|<span data-ttu-id="d0ac4-124">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-124">The control is disabled.</span></span>|  
|<span data-ttu-id="d0ac4-125">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="d0ac4-125">Focused</span></span>|<span data-ttu-id="d0ac4-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d0ac4-126">FocusStates</span></span>|<span data-ttu-id="d0ac4-127">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-127">The control has focus.</span></span>|  
|<span data-ttu-id="d0ac4-128">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="d0ac4-128">Unfocused</span></span>|<span data-ttu-id="d0ac4-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d0ac4-129">FocusStates</span></span>|<span data-ttu-id="d0ac4-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="d0ac4-131">Platné</span><span class="sxs-lookup"><span data-stu-id="d0ac4-131">Valid</span></span>|<span data-ttu-id="d0ac4-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d0ac4-132">ValidationStates</span></span>|<span data-ttu-id="d0ac4-133">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d0ac4-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d0ac4-134">InvalidFocused</span></span>|<span data-ttu-id="d0ac4-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d0ac4-135">ValidationStates</span></span>|<span data-ttu-id="d0ac4-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d0ac4-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d0ac4-137">InvalidUnfocused</span></span>|<span data-ttu-id="d0ac4-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d0ac4-138">ValidationStates</span></span>|<span data-ttu-id="d0ac4-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="d0ac4-140">Příklad ControlTemplate jezdec</span><span class="sxs-lookup"><span data-stu-id="d0ac4-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="d0ac4-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.Thumb> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="d0ac4-142">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="d0ac4-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d0ac4-143">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="d0ac4-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ac4-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0ac4-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d0ac4-145">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="d0ac4-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d0ac4-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d0ac4-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d0ac4-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d0ac4-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d0ac4-148">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d0ac4-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
