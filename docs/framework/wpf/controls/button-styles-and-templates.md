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
ms.openlocfilehash: ef9f85848ebdda9dc4ae15d0f54847eacd46e24d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283584"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="95867-102">Styly a šablony tlačítek</span><span class="sxs-lookup"><span data-stu-id="95867-102">Button Styles and Templates</span></span>
<span data-ttu-id="95867-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="95867-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="95867-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="95867-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="95867-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="95867-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="95867-106">Části tlačítek</span><span class="sxs-lookup"><span data-stu-id="95867-106">Button Parts</span></span>  
 <span data-ttu-id="95867-107">Ovládací prvek <xref:System.Windows.Controls.Button> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="95867-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="95867-108">Stavy tlačítek</span><span class="sxs-lookup"><span data-stu-id="95867-108">Button States</span></span>  
 <span data-ttu-id="95867-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="95867-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="95867-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="95867-110">VisualState Name</span></span>|<span data-ttu-id="95867-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="95867-111">VisualStateGroup Name</span></span>|<span data-ttu-id="95867-112">Popis</span><span class="sxs-lookup"><span data-stu-id="95867-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="95867-113">Normální</span><span class="sxs-lookup"><span data-stu-id="95867-113">Normal</span></span>|<span data-ttu-id="95867-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="95867-114">CommonStates</span></span>|<span data-ttu-id="95867-115">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="95867-115">The default state.</span></span>|  
|<span data-ttu-id="95867-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="95867-116">MouseOver</span></span>|<span data-ttu-id="95867-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="95867-117">CommonStates</span></span>|<span data-ttu-id="95867-118">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="95867-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="95867-119">Stisknutí</span><span class="sxs-lookup"><span data-stu-id="95867-119">Pressed</span></span>|<span data-ttu-id="95867-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="95867-120">CommonStates</span></span>|<span data-ttu-id="95867-121">Ovládací prvek se stiskne.</span><span class="sxs-lookup"><span data-stu-id="95867-121">The control is pressed.</span></span>|  
|<span data-ttu-id="95867-122">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="95867-122">Disabled</span></span>|<span data-ttu-id="95867-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="95867-123">CommonStates</span></span>|<span data-ttu-id="95867-124">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="95867-124">The control is disabled.</span></span>|  
|<span data-ttu-id="95867-125">Zaměřil</span><span class="sxs-lookup"><span data-stu-id="95867-125">Focused</span></span>|<span data-ttu-id="95867-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="95867-126">FocusStates</span></span>|<span data-ttu-id="95867-127">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="95867-127">The control has focus.</span></span>|  
|<span data-ttu-id="95867-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="95867-128">Unfocused</span></span>|<span data-ttu-id="95867-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="95867-129">FocusStates</span></span>|<span data-ttu-id="95867-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="95867-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="95867-131">Platný</span><span class="sxs-lookup"><span data-stu-id="95867-131">Valid</span></span>|<span data-ttu-id="95867-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="95867-132">ValidationStates</span></span>|<span data-ttu-id="95867-133">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="95867-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="95867-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="95867-134">InvalidFocused</span></span>|<span data-ttu-id="95867-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="95867-135">ValidationStates</span></span>|<span data-ttu-id="95867-136">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` a ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="95867-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="95867-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="95867-137">InvalidUnfocused</span></span>|<span data-ttu-id="95867-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="95867-138">ValidationStates</span></span>|<span data-ttu-id="95867-139">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` a ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="95867-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="95867-140">Příklad ControlTemplate tlačítka</span><span class="sxs-lookup"><span data-stu-id="95867-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="95867-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="95867-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="95867-142">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="95867-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="95867-143">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="95867-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95867-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95867-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="95867-145">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="95867-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="95867-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="95867-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="95867-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="95867-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="95867-148">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="95867-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
