---
title: StatusBar – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
ms.openlocfilehash: ee3bd060268d5ab6f713a74f871d7de0dd77782b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660460"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="da796-102">StatusBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="da796-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="da796-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="da796-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="da796-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="da796-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="da796-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="da796-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="da796-106">StatusBar – částí</span><span class="sxs-lookup"><span data-stu-id="da796-106">StatusBar Parts</span></span>  
 <span data-ttu-id="da796-107"><xref:System.Windows.Controls.Primitives.StatusBar> Ovládací prvek nemá žádné pojmenované součásti.</span><span class="sxs-lookup"><span data-stu-id="da796-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="da796-108">StatusBar – stavy</span><span class="sxs-lookup"><span data-stu-id="da796-108">StatusBar States</span></span>  
 <span data-ttu-id="da796-109">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="da796-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="da796-110">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="da796-110">VisualState Name</span></span>|<span data-ttu-id="da796-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="da796-111">VisualStateGroup Name</span></span>|<span data-ttu-id="da796-112">Popis</span><span class="sxs-lookup"><span data-stu-id="da796-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="da796-113">Platné</span><span class="sxs-lookup"><span data-stu-id="da796-113">Valid</span></span>|<span data-ttu-id="da796-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="da796-114">ValidationStates</span></span>|<span data-ttu-id="da796-115">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="da796-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="da796-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="da796-116">InvalidFocused</span></span>|<span data-ttu-id="da796-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="da796-117">ValidationStates</span></span>|<span data-ttu-id="da796-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="da796-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="da796-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="da796-119">InvalidUnfocused</span></span>|<span data-ttu-id="da796-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="da796-120">ValidationStates</span></span>|<span data-ttu-id="da796-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="da796-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="da796-122">StatusBarItem částí</span><span class="sxs-lookup"><span data-stu-id="da796-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="da796-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> Ovládací prvek nemá žádné pojmenované součásti.</span><span class="sxs-lookup"><span data-stu-id="da796-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="da796-124">StatusBar – stavy</span><span class="sxs-lookup"><span data-stu-id="da796-124">StatusBar States</span></span>  
 <span data-ttu-id="da796-125">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.StatusBarItem> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="da796-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="da796-126">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="da796-126">VisualState Name</span></span>|<span data-ttu-id="da796-127">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="da796-127">VisualStateGroup Name</span></span>|<span data-ttu-id="da796-128">Popis</span><span class="sxs-lookup"><span data-stu-id="da796-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="da796-129">Platné</span><span class="sxs-lookup"><span data-stu-id="da796-129">Valid</span></span>|<span data-ttu-id="da796-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="da796-130">ValidationStates</span></span>|<span data-ttu-id="da796-131">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="da796-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="da796-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="da796-132">InvalidFocused</span></span>|<span data-ttu-id="da796-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="da796-133">ValidationStates</span></span>|<span data-ttu-id="da796-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="da796-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="da796-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="da796-135">InvalidUnfocused</span></span>|<span data-ttu-id="da796-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="da796-136">ValidationStates</span></span>|<span data-ttu-id="da796-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="da796-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="da796-138">StatusBar – příklad šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="da796-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="da796-139">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="da796-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="da796-140"><xref:System.Windows.Controls.ControlTemplate> Používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="da796-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="da796-141">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="da796-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da796-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da796-142">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="da796-143">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="da796-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="da796-144">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="da796-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="da796-145">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="da796-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="da796-146">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="da796-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
