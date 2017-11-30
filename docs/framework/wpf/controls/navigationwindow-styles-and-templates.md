---
title: "NavigationWindow – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b48b0b4451f0cf93b86ee448db255f337a859b74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="9cf0b-102">NavigationWindow – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="9cf0b-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="9cf0b-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Navigation.NavigationWindow> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9cf0b-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="9cf0b-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9cf0b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9cf0b-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="9cf0b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="9cf0b-106">Části okně navigace</span><span class="sxs-lookup"><span data-stu-id="9cf0b-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="9cf0b-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Navigation.NavigationWindow> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9cf0b-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="9cf0b-108">Část</span><span class="sxs-lookup"><span data-stu-id="9cf0b-108">Part</span></span>|<span data-ttu-id="9cf0b-109">Typ</span><span class="sxs-lookup"><span data-stu-id="9cf0b-109">Type</span></span>|<span data-ttu-id="9cf0b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9cf0b-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9cf0b-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="9cf0b-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="9cf0b-112">Oblasti pro obsah.</span><span class="sxs-lookup"><span data-stu-id="9cf0b-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="9cf0b-113">Stavy okně navigace</span><span class="sxs-lookup"><span data-stu-id="9cf0b-113">NavigationWindow States</span></span>  
 <span data-ttu-id="9cf0b-114">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Navigation.NavigationWindow> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9cf0b-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="9cf0b-115">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="9cf0b-115">VisualState Name</span></span>|<span data-ttu-id="9cf0b-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="9cf0b-116">VisualStateGroup Name</span></span>|<span data-ttu-id="9cf0b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="9cf0b-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9cf0b-118">Platné</span><span class="sxs-lookup"><span data-stu-id="9cf0b-118">Valid</span></span>|<span data-ttu-id="9cf0b-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9cf0b-119">ValidationStates</span></span>|<span data-ttu-id="9cf0b-120">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="9cf0b-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9cf0b-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9cf0b-121">InvalidFocused</span></span>|<span data-ttu-id="9cf0b-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9cf0b-122">ValidationStates</span></span>|<span data-ttu-id="9cf0b-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="9cf0b-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="9cf0b-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9cf0b-124">InvalidUnfocused</span></span>|<span data-ttu-id="9cf0b-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9cf0b-125">ValidationStates</span></span>|<span data-ttu-id="9cf0b-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="9cf0b-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="9cf0b-127">Příklad ControlTemplate okně navigace</span><span class="sxs-lookup"><span data-stu-id="9cf0b-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="9cf0b-128">I když tento příklad obsahuje všechny prvky, které jsou definovány v <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Navigation.NavigationWindow> ve výchozím nastavení, konkrétní hodnoty by měla být představit jako příklady.</span><span class="sxs-lookup"><span data-stu-id="9cf0b-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="9cf0b-129">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="9cf0b-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9cf0b-130">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="9cf0b-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf0b-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cf0b-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="9cf0b-132">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="9cf0b-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="9cf0b-133">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="9cf0b-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="9cf0b-134">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="9cf0b-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="9cf0b-135">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="9cf0b-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
