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
ms.openlocfilehash: 64b5b66f7f32ea31b51b4da990ceede4078c27cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790959"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="d1212-102">StatusBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d1212-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="d1212-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d1212-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="d1212-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d1212-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d1212-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d1212-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="d1212-106">StatusBar – částí</span><span class="sxs-lookup"><span data-stu-id="d1212-106">StatusBar Parts</span></span>  
 <span data-ttu-id="d1212-107"><xref:System.Windows.Controls.Primitives.StatusBar> Ovládací prvek nemá žádné pojmenované součásti.</span><span class="sxs-lookup"><span data-stu-id="d1212-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="d1212-108">StatusBar – stavy</span><span class="sxs-lookup"><span data-stu-id="d1212-108">StatusBar States</span></span>  
 <span data-ttu-id="d1212-109">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d1212-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="d1212-110">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="d1212-110">VisualState Name</span></span>|<span data-ttu-id="d1212-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d1212-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d1212-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d1212-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d1212-113">Platné</span><span class="sxs-lookup"><span data-stu-id="d1212-113">Valid</span></span>|<span data-ttu-id="d1212-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1212-114">ValidationStates</span></span>|<span data-ttu-id="d1212-115">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="d1212-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d1212-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d1212-116">InvalidFocused</span></span>|<span data-ttu-id="d1212-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1212-117">ValidationStates</span></span>|<span data-ttu-id="d1212-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="d1212-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d1212-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d1212-119">InvalidUnfocused</span></span>|<span data-ttu-id="d1212-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1212-120">ValidationStates</span></span>|<span data-ttu-id="d1212-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d1212-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="d1212-122">StatusBarItem částí</span><span class="sxs-lookup"><span data-stu-id="d1212-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="d1212-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> Ovládací prvek nemá žádné pojmenované součásti.</span><span class="sxs-lookup"><span data-stu-id="d1212-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="d1212-124">StatusBar – stavy</span><span class="sxs-lookup"><span data-stu-id="d1212-124">StatusBar States</span></span>  
 <span data-ttu-id="d1212-125">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.StatusBarItem> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d1212-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="d1212-126">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="d1212-126">VisualState Name</span></span>|<span data-ttu-id="d1212-127">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d1212-127">VisualStateGroup Name</span></span>|<span data-ttu-id="d1212-128">Popis</span><span class="sxs-lookup"><span data-stu-id="d1212-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d1212-129">Platné</span><span class="sxs-lookup"><span data-stu-id="d1212-129">Valid</span></span>|<span data-ttu-id="d1212-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1212-130">ValidationStates</span></span>|<span data-ttu-id="d1212-131">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="d1212-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d1212-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d1212-132">InvalidFocused</span></span>|<span data-ttu-id="d1212-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1212-133">ValidationStates</span></span>|<span data-ttu-id="d1212-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="d1212-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d1212-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d1212-135">InvalidUnfocused</span></span>|<span data-ttu-id="d1212-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1212-136">ValidationStates</span></span>|<span data-ttu-id="d1212-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d1212-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="d1212-138">StatusBar – příklad šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d1212-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="d1212-139">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d1212-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="d1212-140"><xref:System.Windows.Controls.ControlTemplate> Používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="d1212-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d1212-141">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="d1212-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1212-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1212-142">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d1212-143">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="d1212-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d1212-144">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d1212-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d1212-145">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d1212-145">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="d1212-146">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d1212-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
