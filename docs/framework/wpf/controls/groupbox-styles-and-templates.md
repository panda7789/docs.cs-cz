---
title: "GroupBox – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a39e09812c54df533fdac27b5bfcaedd3fb93ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="70bae-102">GroupBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="70bae-102">GroupBox Styles and Templates</span></span>
<span data-ttu-id="70bae-103"><a name="introduction"></a>Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.GroupBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="70bae-103"><a name="introduction"></a> This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="70bae-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="70bae-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="70bae-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="70bae-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="70bae-106">Groupbox – součásti</span><span class="sxs-lookup"><span data-stu-id="70bae-106">GroupBox Parts</span></span>  
 <span data-ttu-id="70bae-107"><xref:System.Windows.Controls.GroupBox> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="70bae-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="70bae-108">Groupbox – stavy</span><span class="sxs-lookup"><span data-stu-id="70bae-108">GroupBox States</span></span>  
 <span data-ttu-id="70bae-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.GroupBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="70bae-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="70bae-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="70bae-110">VisualState Name</span></span>|<span data-ttu-id="70bae-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="70bae-111">VisualStateGroup Name</span></span>|<span data-ttu-id="70bae-112">Popis</span><span class="sxs-lookup"><span data-stu-id="70bae-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="70bae-113">Platné</span><span class="sxs-lookup"><span data-stu-id="70bae-113">Valid</span></span>|<span data-ttu-id="70bae-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="70bae-114">ValidationStates</span></span>|<span data-ttu-id="70bae-115">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="70bae-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="70bae-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="70bae-116">InvalidFocused</span></span>|<span data-ttu-id="70bae-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="70bae-117">ValidationStates</span></span>|<span data-ttu-id="70bae-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="70bae-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="70bae-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="70bae-119">InvalidUnfocused</span></span>|<span data-ttu-id="70bae-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="70bae-120">ValidationStates</span></span>|<span data-ttu-id="70bae-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="70bae-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="70bae-122">Příklad ControlTemplate GroupBox</span><span class="sxs-lookup"><span data-stu-id="70bae-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="70bae-123">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.GroupBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="70bae-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="70bae-124"><xref:System.Windows.Controls.ControlTemplate> Používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="70bae-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="70bae-125">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="70bae-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70bae-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="70bae-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="70bae-127">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="70bae-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="70bae-128">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="70bae-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="70bae-129">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="70bae-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="70bae-130">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="70bae-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
