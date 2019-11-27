---
title: Styly a šablony jezdce
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: 0d0d88e3b527beacfa5f879027e696aa75b18147
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283682"
---
# <a name="thumb-styles-and-templates"></a><span data-ttu-id="2902c-102">Styly a šablony jezdce</span><span class="sxs-lookup"><span data-stu-id="2902c-102">Thumb Styles and Templates</span></span>

<span data-ttu-id="2902c-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="2902c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="2902c-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="2902c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2902c-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="2902c-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="thumb-parts"></a><span data-ttu-id="2902c-106">Části s miniaturami</span><span class="sxs-lookup"><span data-stu-id="2902c-106">Thumb Parts</span></span>

<span data-ttu-id="2902c-107">Ovládací prvek <xref:System.Windows.Controls.Primitives.Thumb> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="2902c-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>

## <a name="thumb-states"></a><span data-ttu-id="2902c-108">Stavy miniatur</span><span class="sxs-lookup"><span data-stu-id="2902c-108">Thumb States</span></span>

<span data-ttu-id="2902c-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="2902c-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

|<span data-ttu-id="2902c-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="2902c-110">VisualState Name</span></span>|<span data-ttu-id="2902c-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="2902c-111">VisualStateGroup Name</span></span>|<span data-ttu-id="2902c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2902c-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="2902c-113">Normální</span><span class="sxs-lookup"><span data-stu-id="2902c-113">Normal</span></span>|<span data-ttu-id="2902c-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2902c-114">CommonStates</span></span>|<span data-ttu-id="2902c-115">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="2902c-115">The default state.</span></span>|
|<span data-ttu-id="2902c-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="2902c-116">MouseOver</span></span>|<span data-ttu-id="2902c-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2902c-117">CommonStates</span></span>|<span data-ttu-id="2902c-118">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="2902c-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="2902c-119">Stisknutí</span><span class="sxs-lookup"><span data-stu-id="2902c-119">Pressed</span></span>|<span data-ttu-id="2902c-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2902c-120">CommonStates</span></span>|<span data-ttu-id="2902c-121">Ovládací prvek se stiskne.</span><span class="sxs-lookup"><span data-stu-id="2902c-121">The control is pressed.</span></span>|
|<span data-ttu-id="2902c-122">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="2902c-122">Disabled</span></span>|<span data-ttu-id="2902c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2902c-123">CommonStates</span></span>|<span data-ttu-id="2902c-124">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="2902c-124">The control is disabled.</span></span>|
|<span data-ttu-id="2902c-125">Zaměřil</span><span class="sxs-lookup"><span data-stu-id="2902c-125">Focused</span></span>|<span data-ttu-id="2902c-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="2902c-126">FocusStates</span></span>|<span data-ttu-id="2902c-127">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="2902c-127">The control has focus.</span></span>|
|<span data-ttu-id="2902c-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="2902c-128">Unfocused</span></span>|<span data-ttu-id="2902c-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="2902c-129">FocusStates</span></span>|<span data-ttu-id="2902c-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="2902c-130">The control does not have focus.</span></span>|
|<span data-ttu-id="2902c-131">Platný</span><span class="sxs-lookup"><span data-stu-id="2902c-131">Valid</span></span>|<span data-ttu-id="2902c-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2902c-132">ValidationStates</span></span>|<span data-ttu-id="2902c-133">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="2902c-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="2902c-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2902c-134">InvalidFocused</span></span>|<span data-ttu-id="2902c-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2902c-135">ValidationStates</span></span>|<span data-ttu-id="2902c-136">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="2902c-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="2902c-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2902c-137">InvalidUnfocused</span></span>|<span data-ttu-id="2902c-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2902c-138">ValidationStates</span></span>|<span data-ttu-id="2902c-139">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="2902c-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="thumb-controltemplate-example"></a><span data-ttu-id="2902c-140">Příklad ControlTemplate pro palec</span><span class="sxs-lookup"><span data-stu-id="2902c-140">Thumb ControlTemplate Example</span></span>

<span data-ttu-id="2902c-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="2902c-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

<span data-ttu-id="2902c-142">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="2902c-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="2902c-143">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="2902c-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="2902c-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2902c-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2902c-145">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="2902c-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="2902c-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="2902c-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="2902c-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="2902c-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="2902c-148">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="2902c-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
