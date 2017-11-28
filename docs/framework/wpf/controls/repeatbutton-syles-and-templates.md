---
title: "RepeatButton – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4895757e909d5e15fd6540b19e1eeec414e1f4e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="repeatbutton-syles-and-templates"></a><span data-ttu-id="21056-102">RepeatButton – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="21056-102">RepeatButton Syles and Templates</span></span>
<span data-ttu-id="21056-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.RepeatButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21056-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="21056-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21056-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="21056-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="21056-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="repeatbutton-parts"></a><span data-ttu-id="21056-106">RepeatButton částí</span><span class="sxs-lookup"><span data-stu-id="21056-106">RepeatButton Parts</span></span>  
 <span data-ttu-id="21056-107"><xref:System.Windows.Controls.Primitives.RepeatButton> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="21056-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>  
  
## <a name="repeatbutton-states"></a><span data-ttu-id="21056-108">RepeatButton stavy</span><span class="sxs-lookup"><span data-stu-id="21056-108">RepeatButton States</span></span>  
 <span data-ttu-id="21056-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.RepeatButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21056-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>  
  
|<span data-ttu-id="21056-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="21056-110">VisualState Name</span></span>|<span data-ttu-id="21056-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="21056-111">VisualStateGroup Name</span></span>|<span data-ttu-id="21056-112">Popis</span><span class="sxs-lookup"><span data-stu-id="21056-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="21056-113">Normální</span><span class="sxs-lookup"><span data-stu-id="21056-113">Normal</span></span>|<span data-ttu-id="21056-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="21056-114">CommonStates</span></span>|<span data-ttu-id="21056-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="21056-115">The default state.</span></span>|  
|<span data-ttu-id="21056-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="21056-116">MouseOver</span></span>|<span data-ttu-id="21056-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="21056-117">CommonStates</span></span>|<span data-ttu-id="21056-118">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21056-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="21056-119">Stisknutí tlačítka</span><span class="sxs-lookup"><span data-stu-id="21056-119">Pressed</span></span>|<span data-ttu-id="21056-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="21056-120">CommonStates</span></span>|<span data-ttu-id="21056-121">Stisknutí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21056-121">The control is pressed.</span></span>|  
|<span data-ttu-id="21056-122">zakázáno</span><span class="sxs-lookup"><span data-stu-id="21056-122">Disabled</span></span>|<span data-ttu-id="21056-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="21056-123">CommonStates</span></span>|<span data-ttu-id="21056-124">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="21056-124">The control is disabled.</span></span>|  
|<span data-ttu-id="21056-125">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="21056-125">Focused</span></span>|<span data-ttu-id="21056-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="21056-126">FocusStates</span></span>|<span data-ttu-id="21056-127">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="21056-127">The control has focus.</span></span>|  
|<span data-ttu-id="21056-128">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="21056-128">Unfocused</span></span>|<span data-ttu-id="21056-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="21056-129">FocusStates</span></span>|<span data-ttu-id="21056-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="21056-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="21056-131">Platné</span><span class="sxs-lookup"><span data-stu-id="21056-131">Valid</span></span>|<span data-ttu-id="21056-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21056-132">ValidationStates</span></span>|<span data-ttu-id="21056-133">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="21056-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="21056-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="21056-134">InvalidFocused</span></span>|<span data-ttu-id="21056-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21056-135">ValidationStates</span></span>|<span data-ttu-id="21056-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="21056-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="21056-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="21056-137">InvalidUnfocused</span></span>|<span data-ttu-id="21056-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21056-138">ValidationStates</span></span>|<span data-ttu-id="21056-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="21056-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="21056-140">Příklad ControlTemplate RepeatButton</span><span class="sxs-lookup"><span data-stu-id="21056-140">RepeatButton ControlTemplate Example</span></span>  
 <span data-ttu-id="21056-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.RepeatButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21056-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#RepeatButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]  
  
 <span data-ttu-id="21056-142">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="21056-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="21056-143">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="21056-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21056-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="21056-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="21056-145">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="21056-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="21056-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="21056-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="21056-147">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="21056-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="21056-148">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="21056-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
