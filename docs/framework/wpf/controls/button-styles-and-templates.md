---
title: Styly a šablony tlačítek
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: 854160e8b1b049fdb2f3421b9eb24cf410f33672
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="4b8d0-102">Styly a šablony tlačítek</span><span class="sxs-lookup"><span data-stu-id="4b8d0-102">Button Styles and Templates</span></span>
<span data-ttu-id="4b8d0-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="4b8d0-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="4b8d0-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="4b8d0-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="4b8d0-106">Tlačítko částí</span><span class="sxs-lookup"><span data-stu-id="4b8d0-106">Button Parts</span></span>  
 <span data-ttu-id="4b8d0-107"><xref:System.Windows.Controls.Button> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="4b8d0-108">Tlačítko stavy</span><span class="sxs-lookup"><span data-stu-id="4b8d0-108">Button States</span></span>  
 <span data-ttu-id="4b8d0-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="4b8d0-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="4b8d0-110">VisualState Name</span></span>|<span data-ttu-id="4b8d0-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="4b8d0-111">VisualStateGroup Name</span></span>|<span data-ttu-id="4b8d0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4b8d0-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="4b8d0-113">Normální</span><span class="sxs-lookup"><span data-stu-id="4b8d0-113">Normal</span></span>|<span data-ttu-id="4b8d0-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b8d0-114">CommonStates</span></span>|<span data-ttu-id="4b8d0-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-115">The default state.</span></span>|  
|<span data-ttu-id="4b8d0-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="4b8d0-116">MouseOver</span></span>|<span data-ttu-id="4b8d0-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b8d0-117">CommonStates</span></span>|<span data-ttu-id="4b8d0-118">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="4b8d0-119">Stisknutí tlačítka</span><span class="sxs-lookup"><span data-stu-id="4b8d0-119">Pressed</span></span>|<span data-ttu-id="4b8d0-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b8d0-120">CommonStates</span></span>|<span data-ttu-id="4b8d0-121">Stisknutí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-121">The control is pressed.</span></span>|  
|<span data-ttu-id="4b8d0-122">zakázáno</span><span class="sxs-lookup"><span data-stu-id="4b8d0-122">Disabled</span></span>|<span data-ttu-id="4b8d0-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b8d0-123">CommonStates</span></span>|<span data-ttu-id="4b8d0-124">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-124">The control is disabled.</span></span>|  
|<span data-ttu-id="4b8d0-125">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="4b8d0-125">Focused</span></span>|<span data-ttu-id="4b8d0-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="4b8d0-126">FocusStates</span></span>|<span data-ttu-id="4b8d0-127">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-127">The control has focus.</span></span>|  
|<span data-ttu-id="4b8d0-128">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="4b8d0-128">Unfocused</span></span>|<span data-ttu-id="4b8d0-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="4b8d0-129">FocusStates</span></span>|<span data-ttu-id="4b8d0-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="4b8d0-131">Platné</span><span class="sxs-lookup"><span data-stu-id="4b8d0-131">Valid</span></span>|<span data-ttu-id="4b8d0-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b8d0-132">ValidationStates</span></span>|<span data-ttu-id="4b8d0-133">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="4b8d0-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="4b8d0-134">InvalidFocused</span></span>|<span data-ttu-id="4b8d0-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b8d0-135">ValidationStates</span></span>|<span data-ttu-id="4b8d0-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` a má právě fokus, ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="4b8d0-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="4b8d0-137">InvalidUnfocused</span></span>|<span data-ttu-id="4b8d0-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b8d0-138">ValidationStates</span></span>|<span data-ttu-id="4b8d0-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` a ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="4b8d0-140">Příklad ControlTemplate tlačítko</span><span class="sxs-lookup"><span data-stu-id="4b8d0-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="4b8d0-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="4b8d0-142">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="4b8d0-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="4b8d0-143">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="4b8d0-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8d0-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b8d0-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="4b8d0-145">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="4b8d0-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="4b8d0-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4b8d0-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="4b8d0-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="4b8d0-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="4b8d0-148">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="4b8d0-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
