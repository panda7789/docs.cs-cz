---
title: "ToolTip – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec946e7982983519a317ee1936e8584eef63479c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="11f1e-102">ToolTip – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="11f1e-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="11f1e-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ToolTip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="11f1e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="11f1e-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="11f1e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="11f1e-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="11f1e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="11f1e-106">Popis části</span><span class="sxs-lookup"><span data-stu-id="11f1e-106">ToolTip Parts</span></span>  
 <span data-ttu-id="11f1e-107"><xref:System.Windows.Controls.ToolTip> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="11f1e-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="11f1e-108">Popisek stavy</span><span class="sxs-lookup"><span data-stu-id="11f1e-108">ToolTip States</span></span>  
 <span data-ttu-id="11f1e-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ToolTip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="11f1e-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="11f1e-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="11f1e-110">VisualState Name</span></span>|<span data-ttu-id="11f1e-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="11f1e-111">VisualStateGroup Name</span></span>|<span data-ttu-id="11f1e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="11f1e-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="11f1e-113">Zavřeno</span><span class="sxs-lookup"><span data-stu-id="11f1e-113">Closed</span></span>|<span data-ttu-id="11f1e-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="11f1e-114">OpenStates</span></span>|<span data-ttu-id="11f1e-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="11f1e-115">The default state.</span></span>|  
|<span data-ttu-id="11f1e-116">Otevřít</span><span class="sxs-lookup"><span data-stu-id="11f1e-116">Open</span></span>|<span data-ttu-id="11f1e-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="11f1e-117">OpenStates</span></span>|<span data-ttu-id="11f1e-118"><xref:System.Windows.Controls.ToolTip> Je viditelná.</span><span class="sxs-lookup"><span data-stu-id="11f1e-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="11f1e-119">Platné</span><span class="sxs-lookup"><span data-stu-id="11f1e-119">Valid</span></span>|<span data-ttu-id="11f1e-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="11f1e-120">ValidationStates</span></span>|<span data-ttu-id="11f1e-121">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="11f1e-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="11f1e-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="11f1e-122">InvalidFocused</span></span>|<span data-ttu-id="11f1e-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="11f1e-123">ValidationStates</span></span>|<span data-ttu-id="11f1e-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="11f1e-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="11f1e-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="11f1e-125">InvalidUnfocused</span></span>|<span data-ttu-id="11f1e-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="11f1e-126">ValidationStates</span></span>|<span data-ttu-id="11f1e-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="11f1e-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="11f1e-128">Příklad popisku ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="11f1e-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="11f1e-129">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ToolTip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="11f1e-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="11f1e-130">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="11f1e-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="11f1e-131">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="11f1e-131">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11f1e-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="11f1e-132">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="11f1e-133">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="11f1e-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="11f1e-134">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="11f1e-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="11f1e-135">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="11f1e-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="11f1e-136">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="11f1e-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
