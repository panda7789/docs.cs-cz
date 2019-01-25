---
title: Styly a šablony rámců
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
ms.openlocfilehash: fbe49ae98e0fe281500ae37d53a3d47ff1d0b03a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700266"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="3b552-102">Styly a šablony rámců</span><span class="sxs-lookup"><span data-stu-id="3b552-102">Frame Styles and Templates</span></span>
<span data-ttu-id="3b552-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3b552-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="3b552-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3b552-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3b552-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="3b552-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="3b552-106">Části rámce</span><span class="sxs-lookup"><span data-stu-id="3b552-106">Frame Parts</span></span>  
 <span data-ttu-id="3b552-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3b552-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="3b552-108">Část</span><span class="sxs-lookup"><span data-stu-id="3b552-108">Part</span></span>|<span data-ttu-id="3b552-109">Typ</span><span class="sxs-lookup"><span data-stu-id="3b552-109">Type</span></span>|<span data-ttu-id="3b552-110">Popis</span><span class="sxs-lookup"><span data-stu-id="3b552-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3b552-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="3b552-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="3b552-112">Oblast obsahu.</span><span class="sxs-lookup"><span data-stu-id="3b552-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="3b552-113">Stavy snímků</span><span class="sxs-lookup"><span data-stu-id="3b552-113">Frame States</span></span>  
 <span data-ttu-id="3b552-114">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3b552-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="3b552-115">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="3b552-115">VisualState Name</span></span>|<span data-ttu-id="3b552-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="3b552-116">VisualStateGroup Name</span></span>|<span data-ttu-id="3b552-117">Popis</span><span class="sxs-lookup"><span data-stu-id="3b552-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3b552-118">Platné</span><span class="sxs-lookup"><span data-stu-id="3b552-118">Valid</span></span>|<span data-ttu-id="3b552-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3b552-119">ValidationStates</span></span>|<span data-ttu-id="3b552-120">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="3b552-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3b552-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3b552-121">InvalidFocused</span></span>|<span data-ttu-id="3b552-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3b552-122">ValidationStates</span></span>|<span data-ttu-id="3b552-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="3b552-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3b552-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3b552-124">InvalidUnfocused</span></span>|<span data-ttu-id="3b552-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3b552-125">ValidationStates</span></span>|<span data-ttu-id="3b552-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="3b552-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="3b552-127">Příklad šablony ControlTemplate rámce</span><span class="sxs-lookup"><span data-stu-id="3b552-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="3b552-128">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3b552-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="3b552-129">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="3b552-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3b552-130">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="3b552-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b552-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b552-131">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3b552-132">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="3b552-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="3b552-133">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="3b552-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="3b552-134">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="3b552-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="3b552-135">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="3b552-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
