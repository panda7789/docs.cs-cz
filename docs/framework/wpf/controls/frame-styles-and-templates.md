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
ms.openlocfilehash: 6b084cfa31efebe2456871a99cd810741aa26609
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131015"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="15544-102">Styly a šablony rámců</span><span class="sxs-lookup"><span data-stu-id="15544-102">Frame Styles and Templates</span></span>
<span data-ttu-id="15544-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="15544-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="15544-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="15544-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="15544-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="15544-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="15544-106">Části rámce</span><span class="sxs-lookup"><span data-stu-id="15544-106">Frame Parts</span></span>  
 <span data-ttu-id="15544-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="15544-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="15544-108">Část</span><span class="sxs-lookup"><span data-stu-id="15544-108">Part</span></span>|<span data-ttu-id="15544-109">Type</span><span class="sxs-lookup"><span data-stu-id="15544-109">Type</span></span>|<span data-ttu-id="15544-110">Popis</span><span class="sxs-lookup"><span data-stu-id="15544-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="15544-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="15544-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="15544-112">Oblast obsahu.</span><span class="sxs-lookup"><span data-stu-id="15544-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="15544-113">Stavy snímků</span><span class="sxs-lookup"><span data-stu-id="15544-113">Frame States</span></span>  
 <span data-ttu-id="15544-114">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="15544-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="15544-115">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="15544-115">VisualState Name</span></span>|<span data-ttu-id="15544-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="15544-116">VisualStateGroup Name</span></span>|<span data-ttu-id="15544-117">Popis</span><span class="sxs-lookup"><span data-stu-id="15544-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="15544-118">Platné</span><span class="sxs-lookup"><span data-stu-id="15544-118">Valid</span></span>|<span data-ttu-id="15544-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15544-119">ValidationStates</span></span>|<span data-ttu-id="15544-120">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="15544-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="15544-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="15544-121">InvalidFocused</span></span>|<span data-ttu-id="15544-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15544-122">ValidationStates</span></span>|<span data-ttu-id="15544-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="15544-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="15544-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="15544-124">InvalidUnfocused</span></span>|<span data-ttu-id="15544-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15544-125">ValidationStates</span></span>|<span data-ttu-id="15544-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="15544-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="15544-127">Příklad šablony ControlTemplate rámce</span><span class="sxs-lookup"><span data-stu-id="15544-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="15544-128">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="15544-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="15544-129">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="15544-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="15544-130">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="15544-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15544-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15544-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="15544-132">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="15544-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="15544-133">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="15544-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="15544-134">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="15544-134">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="15544-135">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="15544-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
