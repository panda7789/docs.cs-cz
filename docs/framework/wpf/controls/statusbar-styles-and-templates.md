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
ms.workload: dotnet
ms.openlocfilehash: 370f8f9bc61ffbdd3b98743d11f61613803e6d98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="7bf83-102">StatusBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="7bf83-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="7bf83-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7bf83-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="7bf83-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7bf83-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7bf83-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="7bf83-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="7bf83-106">Části stavový řádek</span><span class="sxs-lookup"><span data-stu-id="7bf83-106">StatusBar Parts</span></span>  
 <span data-ttu-id="7bf83-107"><xref:System.Windows.Controls.Primitives.StatusBar> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="7bf83-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="7bf83-108">Stavy stavový řádek</span><span class="sxs-lookup"><span data-stu-id="7bf83-108">StatusBar States</span></span>  
 <span data-ttu-id="7bf83-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7bf83-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="7bf83-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="7bf83-110">VisualState Name</span></span>|<span data-ttu-id="7bf83-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7bf83-111">VisualStateGroup Name</span></span>|<span data-ttu-id="7bf83-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7bf83-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7bf83-113">Platné</span><span class="sxs-lookup"><span data-stu-id="7bf83-113">Valid</span></span>|<span data-ttu-id="7bf83-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7bf83-114">ValidationStates</span></span>|<span data-ttu-id="7bf83-115">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="7bf83-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7bf83-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7bf83-116">InvalidFocused</span></span>|<span data-ttu-id="7bf83-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7bf83-117">ValidationStates</span></span>|<span data-ttu-id="7bf83-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="7bf83-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7bf83-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7bf83-119">InvalidUnfocused</span></span>|<span data-ttu-id="7bf83-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7bf83-120">ValidationStates</span></span>|<span data-ttu-id="7bf83-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="7bf83-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="7bf83-122">StatusBarItem částí</span><span class="sxs-lookup"><span data-stu-id="7bf83-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="7bf83-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="7bf83-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="7bf83-124">Stavy stavový řádek</span><span class="sxs-lookup"><span data-stu-id="7bf83-124">StatusBar States</span></span>  
 <span data-ttu-id="7bf83-125">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.StatusBarItem> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7bf83-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="7bf83-126">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="7bf83-126">VisualState Name</span></span>|<span data-ttu-id="7bf83-127">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7bf83-127">VisualStateGroup Name</span></span>|<span data-ttu-id="7bf83-128">Popis</span><span class="sxs-lookup"><span data-stu-id="7bf83-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7bf83-129">Platné</span><span class="sxs-lookup"><span data-stu-id="7bf83-129">Valid</span></span>|<span data-ttu-id="7bf83-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7bf83-130">ValidationStates</span></span>|<span data-ttu-id="7bf83-131">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="7bf83-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7bf83-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7bf83-132">InvalidFocused</span></span>|<span data-ttu-id="7bf83-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7bf83-133">ValidationStates</span></span>|<span data-ttu-id="7bf83-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="7bf83-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7bf83-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7bf83-135">InvalidUnfocused</span></span>|<span data-ttu-id="7bf83-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7bf83-136">ValidationStates</span></span>|<span data-ttu-id="7bf83-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="7bf83-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="7bf83-138">Příklad ControlTemplate stavový řádek</span><span class="sxs-lookup"><span data-stu-id="7bf83-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="7bf83-139">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7bf83-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="7bf83-140"><xref:System.Windows.Controls.ControlTemplate> Používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="7bf83-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7bf83-141">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="7bf83-141">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf83-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bf83-142">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="7bf83-143">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="7bf83-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="7bf83-144">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="7bf83-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="7bf83-145">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="7bf83-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="7bf83-146">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="7bf83-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
