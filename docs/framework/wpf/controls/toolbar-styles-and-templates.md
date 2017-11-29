---
title: "ToolBar – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e153ff0fd89259dafedf6f8abb669090a944e91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="d1ab2-102">ToolBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d1ab2-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="d1ab2-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="d1ab2-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d1ab2-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d1ab2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="d1ab2-106">Části panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="d1ab2-106">ToolBar Parts</span></span>  
 <span data-ttu-id="d1ab2-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="d1ab2-108">Část</span><span class="sxs-lookup"><span data-stu-id="d1ab2-108">Part</span></span>|<span data-ttu-id="d1ab2-109">Typ</span><span class="sxs-lookup"><span data-stu-id="d1ab2-109">Type</span></span>|<span data-ttu-id="d1ab2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d1ab2-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d1ab2-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="d1ab2-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="d1ab2-112">Objekt, který obsahuje ovládací prvky na <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="d1ab2-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="d1ab2-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="d1ab2-114">Objekt, který obsahuje ovládací prvky, které jsou v oblasti přetečení <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="d1ab2-115">Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ToolBar>, může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="d1ab2-116">( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí jednotlivé položky <xref:System.Windows.Controls.ToolBar>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).</span><span class="sxs-lookup"><span data-stu-id="d1ab2-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="d1ab2-117">Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímými podřízenými z <xref:System.Windows.Controls.ScrollViewer>, musíte <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="d1ab2-118">Stavy panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="d1ab2-118">ToolBar States</span></span>  
 <span data-ttu-id="d1ab2-119">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="d1ab2-120">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="d1ab2-120">VisualState Name</span></span>|<span data-ttu-id="d1ab2-121">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d1ab2-121">VisualStateGroup Name</span></span>|<span data-ttu-id="d1ab2-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d1ab2-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d1ab2-123">Platné</span><span class="sxs-lookup"><span data-stu-id="d1ab2-123">Valid</span></span>|<span data-ttu-id="d1ab2-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1ab2-124">ValidationStates</span></span>|<span data-ttu-id="d1ab2-125">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d1ab2-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d1ab2-126">InvalidFocused</span></span>|<span data-ttu-id="d1ab2-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1ab2-127">ValidationStates</span></span>|<span data-ttu-id="d1ab2-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d1ab2-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d1ab2-129">InvalidUnfocused</span></span>|<span data-ttu-id="d1ab2-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1ab2-130">ValidationStates</span></span>|<span data-ttu-id="d1ab2-131"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="d1ab2-132">Příklad ControlTemplate panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="d1ab2-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="d1ab2-133">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="d1ab2-134">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="d1ab2-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d1ab2-135">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="d1ab2-135">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ab2-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1ab2-136">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d1ab2-137">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="d1ab2-137">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d1ab2-138">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d1ab2-138">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d1ab2-139">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="d1ab2-139">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d1ab2-140">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d1ab2-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
