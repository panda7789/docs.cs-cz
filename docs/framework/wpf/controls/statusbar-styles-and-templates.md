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
ms.openlocfilehash: 11fa3ab6edd62f0b5484d9ccf76c101d04be353c
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457862"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="f3ddd-102">StatusBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f3ddd-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="f3ddd-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="f3ddd-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f3ddd-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f3ddd-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="f3ddd-106">Části stavový řádek</span><span class="sxs-lookup"><span data-stu-id="f3ddd-106">StatusBar Parts</span></span>  
 <span data-ttu-id="f3ddd-107"><xref:System.Windows.Controls.Primitives.StatusBar> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="f3ddd-108">Stavy stavový řádek</span><span class="sxs-lookup"><span data-stu-id="f3ddd-108">StatusBar States</span></span>  
 <span data-ttu-id="f3ddd-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="f3ddd-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="f3ddd-110">VisualState Name</span></span>|<span data-ttu-id="f3ddd-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f3ddd-111">VisualStateGroup Name</span></span>|<span data-ttu-id="f3ddd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f3ddd-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f3ddd-113">Platné</span><span class="sxs-lookup"><span data-stu-id="f3ddd-113">Valid</span></span>|<span data-ttu-id="f3ddd-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3ddd-114">ValidationStates</span></span>|<span data-ttu-id="f3ddd-115">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f3ddd-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f3ddd-116">InvalidFocused</span></span>|<span data-ttu-id="f3ddd-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3ddd-117">ValidationStates</span></span>|<span data-ttu-id="f3ddd-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f3ddd-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f3ddd-119">InvalidUnfocused</span></span>|<span data-ttu-id="f3ddd-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3ddd-120">ValidationStates</span></span>|<span data-ttu-id="f3ddd-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="f3ddd-122">StatusBarItem částí</span><span class="sxs-lookup"><span data-stu-id="f3ddd-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="f3ddd-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="f3ddd-124">Stavy stavový řádek</span><span class="sxs-lookup"><span data-stu-id="f3ddd-124">StatusBar States</span></span>  
 <span data-ttu-id="f3ddd-125">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.StatusBarItem> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="f3ddd-126">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="f3ddd-126">VisualState Name</span></span>|<span data-ttu-id="f3ddd-127">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f3ddd-127">VisualStateGroup Name</span></span>|<span data-ttu-id="f3ddd-128">Popis</span><span class="sxs-lookup"><span data-stu-id="f3ddd-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f3ddd-129">Platné</span><span class="sxs-lookup"><span data-stu-id="f3ddd-129">Valid</span></span>|<span data-ttu-id="f3ddd-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3ddd-130">ValidationStates</span></span>|<span data-ttu-id="f3ddd-131">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f3ddd-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f3ddd-132">InvalidFocused</span></span>|<span data-ttu-id="f3ddd-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3ddd-133">ValidationStates</span></span>|<span data-ttu-id="f3ddd-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f3ddd-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f3ddd-135">InvalidUnfocused</span></span>|<span data-ttu-id="f3ddd-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3ddd-136">ValidationStates</span></span>|<span data-ttu-id="f3ddd-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="f3ddd-138">Příklad ControlTemplate stavový řádek</span><span class="sxs-lookup"><span data-stu-id="f3ddd-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="f3ddd-139">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="f3ddd-140"><xref:System.Windows.Controls.ControlTemplate> Používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="f3ddd-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f3ddd-141">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f3ddd-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ddd-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3ddd-142">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="f3ddd-143">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f3ddd-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="f3ddd-144">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f3ddd-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="f3ddd-145">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f3ddd-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="f3ddd-146">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f3ddd-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
