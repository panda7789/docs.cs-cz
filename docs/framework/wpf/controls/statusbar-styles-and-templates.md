---
title: "StatusBar – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 570edc023467fb6e95cdcba23b75ac53397797c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="d2330-102">StatusBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d2330-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="d2330-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d2330-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="d2330-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d2330-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d2330-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d2330-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="d2330-106">Části stavový řádek</span><span class="sxs-lookup"><span data-stu-id="d2330-106">StatusBar Parts</span></span>  
 <span data-ttu-id="d2330-107"><xref:System.Windows.Controls.Primitives.StatusBar> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="d2330-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="d2330-108">Stavy stavový řádek</span><span class="sxs-lookup"><span data-stu-id="d2330-108">StatusBar States</span></span>  
 <span data-ttu-id="d2330-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d2330-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="d2330-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="d2330-110">VisualState Name</span></span>|<span data-ttu-id="d2330-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d2330-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d2330-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d2330-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d2330-113">Platné</span><span class="sxs-lookup"><span data-stu-id="d2330-113">Valid</span></span>|<span data-ttu-id="d2330-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2330-114">ValidationStates</span></span>|<span data-ttu-id="d2330-115">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="d2330-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d2330-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d2330-116">InvalidFocused</span></span>|<span data-ttu-id="d2330-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2330-117">ValidationStates</span></span>|<span data-ttu-id="d2330-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="d2330-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d2330-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d2330-119">InvalidUnfocused</span></span>|<span data-ttu-id="d2330-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2330-120">ValidationStates</span></span>|<span data-ttu-id="d2330-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d2330-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="d2330-122">StatusBarItem částí</span><span class="sxs-lookup"><span data-stu-id="d2330-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="d2330-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="d2330-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="d2330-124">Stavy stavový řádek</span><span class="sxs-lookup"><span data-stu-id="d2330-124">StatusBar States</span></span>  
 <span data-ttu-id="d2330-125">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.StatusBarItem> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d2330-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="d2330-126">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="d2330-126">VisualState Name</span></span>|<span data-ttu-id="d2330-127">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d2330-127">VisualStateGroup Name</span></span>|<span data-ttu-id="d2330-128">Popis</span><span class="sxs-lookup"><span data-stu-id="d2330-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d2330-129">Platné</span><span class="sxs-lookup"><span data-stu-id="d2330-129">Valid</span></span>|<span data-ttu-id="d2330-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2330-130">ValidationStates</span></span>|<span data-ttu-id="d2330-131">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="d2330-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d2330-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d2330-132">InvalidFocused</span></span>|<span data-ttu-id="d2330-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2330-133">ValidationStates</span></span>|<span data-ttu-id="d2330-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="d2330-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d2330-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d2330-135">InvalidUnfocused</span></span>|<span data-ttu-id="d2330-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d2330-136">ValidationStates</span></span>|<span data-ttu-id="d2330-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d2330-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="d2330-138">Příklad ControlTemplate stavový řádek</span><span class="sxs-lookup"><span data-stu-id="d2330-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="d2330-139">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d2330-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="d2330-140"><xref:System.Windows.Controls.ControlTemplate> Používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="d2330-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d2330-141">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="d2330-141">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2330-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2330-142">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d2330-143">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="d2330-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d2330-144">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d2330-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d2330-145">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="d2330-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d2330-146">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d2330-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
