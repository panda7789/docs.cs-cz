---
title: "ScrollBar – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 726e6af63d9bd8b0dedfed55af5096bc08f93e34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="13785-102">ScrollBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="13785-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="13785-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.ScrollBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="13785-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="13785-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="13785-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="13785-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="13785-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="13785-106">ScrollBar částí</span><span class="sxs-lookup"><span data-stu-id="13785-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="13785-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.Primitives.ScrollBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="13785-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="13785-108">Část</span><span class="sxs-lookup"><span data-stu-id="13785-108">Part</span></span>|<span data-ttu-id="13785-109">Typ</span><span class="sxs-lookup"><span data-stu-id="13785-109">Type</span></span>|<span data-ttu-id="13785-110">Popis</span><span class="sxs-lookup"><span data-stu-id="13785-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="13785-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="13785-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="13785-112">Kontejner elementu, který označuje pozici <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="13785-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="13785-113">ScrollBar – stavy</span><span class="sxs-lookup"><span data-stu-id="13785-113">ScrollBar States</span></span>  
 <span data-ttu-id="13785-114">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.ScrollBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="13785-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="13785-115">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="13785-115">VisualState Name</span></span>|<span data-ttu-id="13785-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="13785-116">VisualStateGroup Name</span></span>|<span data-ttu-id="13785-117">Popis</span><span class="sxs-lookup"><span data-stu-id="13785-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="13785-118">Normální</span><span class="sxs-lookup"><span data-stu-id="13785-118">Normal</span></span>|<span data-ttu-id="13785-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="13785-119">CommonStates</span></span>|<span data-ttu-id="13785-120">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="13785-120">The default state.</span></span>|  
|<span data-ttu-id="13785-121">Myš nad</span><span class="sxs-lookup"><span data-stu-id="13785-121">MouseOver</span></span>|<span data-ttu-id="13785-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="13785-122">CommonStates</span></span>|<span data-ttu-id="13785-123">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="13785-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="13785-124">zakázáno</span><span class="sxs-lookup"><span data-stu-id="13785-124">Disabled</span></span>|<span data-ttu-id="13785-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="13785-125">CommonStates</span></span>|<span data-ttu-id="13785-126">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="13785-126">The control is disabled.</span></span>|  
|<span data-ttu-id="13785-127">Platné</span><span class="sxs-lookup"><span data-stu-id="13785-127">Valid</span></span>|<span data-ttu-id="13785-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="13785-128">ValidationStates</span></span>|<span data-ttu-id="13785-129">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="13785-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="13785-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="13785-130">InvalidFocused</span></span>|<span data-ttu-id="13785-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="13785-131">ValidationStates</span></span>|<span data-ttu-id="13785-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="13785-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="13785-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="13785-133">InvalidUnfocused</span></span>|<span data-ttu-id="13785-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="13785-134">ValidationStates</span></span>|<span data-ttu-id="13785-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="13785-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="13785-136">Příklad ControlTemplate ScrollBar</span><span class="sxs-lookup"><span data-stu-id="13785-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="13785-137">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.ScrollBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="13785-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="13785-138">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="13785-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="13785-139">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="13785-139">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13785-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="13785-140">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="13785-141">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="13785-141">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="13785-142">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="13785-142">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="13785-143">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="13785-143">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="13785-144">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="13785-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
