---
title: "Styly a šablony rámců"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 603c4f766b836c7a301cc151112457ddb0972d10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="78d26-102">Styly a šablony rámců</span><span class="sxs-lookup"><span data-stu-id="78d26-102">Frame Styles and Templates</span></span>
<span data-ttu-id="78d26-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78d26-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="78d26-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78d26-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="78d26-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="78d26-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="78d26-106">Části rámce</span><span class="sxs-lookup"><span data-stu-id="78d26-106">Frame Parts</span></span>  
 <span data-ttu-id="78d26-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78d26-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="78d26-108">Část</span><span class="sxs-lookup"><span data-stu-id="78d26-108">Part</span></span>|<span data-ttu-id="78d26-109">Typ</span><span class="sxs-lookup"><span data-stu-id="78d26-109">Type</span></span>|<span data-ttu-id="78d26-110">Popis</span><span class="sxs-lookup"><span data-stu-id="78d26-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="78d26-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="78d26-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="78d26-112">Oblast obsahu.</span><span class="sxs-lookup"><span data-stu-id="78d26-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="78d26-113">Stavy rámce</span><span class="sxs-lookup"><span data-stu-id="78d26-113">Frame States</span></span>  
 <span data-ttu-id="78d26-114">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78d26-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="78d26-115">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="78d26-115">VisualState Name</span></span>|<span data-ttu-id="78d26-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="78d26-116">VisualStateGroup Name</span></span>|<span data-ttu-id="78d26-117">Popis</span><span class="sxs-lookup"><span data-stu-id="78d26-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="78d26-118">Platné</span><span class="sxs-lookup"><span data-stu-id="78d26-118">Valid</span></span>|<span data-ttu-id="78d26-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="78d26-119">ValidationStates</span></span>|<span data-ttu-id="78d26-120">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="78d26-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="78d26-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="78d26-121">InvalidFocused</span></span>|<span data-ttu-id="78d26-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="78d26-122">ValidationStates</span></span>|<span data-ttu-id="78d26-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="78d26-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="78d26-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="78d26-124">InvalidUnfocused</span></span>|<span data-ttu-id="78d26-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="78d26-125">ValidationStates</span></span>|<span data-ttu-id="78d26-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="78d26-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="78d26-127">Element ControlTemplate příklad s rámečkem</span><span class="sxs-lookup"><span data-stu-id="78d26-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="78d26-128">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78d26-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="78d26-129">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="78d26-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="78d26-130">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="78d26-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78d26-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="78d26-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="78d26-132">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="78d26-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="78d26-133">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="78d26-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="78d26-134">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="78d26-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="78d26-135">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="78d26-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
