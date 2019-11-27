---
title: ToggleButton – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: a4c449a561017659db7f54fd3cdb8964742650de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283678"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="59704-102">ToggleButton – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="59704-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="59704-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="59704-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="59704-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="59704-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="59704-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="59704-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="59704-106">ToggleButton části</span><span class="sxs-lookup"><span data-stu-id="59704-106">ToggleButton Parts</span></span>

<span data-ttu-id="59704-107">Ovládací prvek <xref:System.Windows.Controls.Primitives.ToggleButton> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="59704-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="59704-108">ToggleButton stavy</span><span class="sxs-lookup"><span data-stu-id="59704-108">ToggleButton States</span></span>

<span data-ttu-id="59704-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="59704-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="59704-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="59704-110">VisualState Name</span></span>|<span data-ttu-id="59704-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="59704-111">VisualStateGroup Name</span></span>|<span data-ttu-id="59704-112">Popis</span><span class="sxs-lookup"><span data-stu-id="59704-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="59704-113">Normální</span><span class="sxs-lookup"><span data-stu-id="59704-113">Normal</span></span>|<span data-ttu-id="59704-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="59704-114">CommonStates</span></span>|<span data-ttu-id="59704-115">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="59704-115">The default state.</span></span>|
|<span data-ttu-id="59704-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="59704-116">MouseOver</span></span>|<span data-ttu-id="59704-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="59704-117">CommonStates</span></span>|<span data-ttu-id="59704-118">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="59704-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="59704-119">Stisknutí</span><span class="sxs-lookup"><span data-stu-id="59704-119">Pressed</span></span>|<span data-ttu-id="59704-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="59704-120">CommonStates</span></span>|<span data-ttu-id="59704-121">Ovládací prvek se stiskne.</span><span class="sxs-lookup"><span data-stu-id="59704-121">The control is pressed.</span></span>|
|<span data-ttu-id="59704-122">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="59704-122">Disabled</span></span>|<span data-ttu-id="59704-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="59704-123">CommonStates</span></span>|<span data-ttu-id="59704-124">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="59704-124">The control is disabled.</span></span>|
|<span data-ttu-id="59704-125">Zaměřil</span><span class="sxs-lookup"><span data-stu-id="59704-125">Focused</span></span>|<span data-ttu-id="59704-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="59704-126">FocusStates</span></span>|<span data-ttu-id="59704-127">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="59704-127">The control has focus.</span></span>|
|<span data-ttu-id="59704-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="59704-128">Unfocused</span></span>|<span data-ttu-id="59704-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="59704-129">FocusStates</span></span>|<span data-ttu-id="59704-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="59704-130">The control does not have focus.</span></span>|
|<span data-ttu-id="59704-131">Zaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="59704-131">Checked</span></span>|<span data-ttu-id="59704-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="59704-132">CheckStates</span></span>|<span data-ttu-id="59704-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `true`.</span><span class="sxs-lookup"><span data-stu-id="59704-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="59704-134">Není zaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="59704-134">Unchecked</span></span>|<span data-ttu-id="59704-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="59704-135">CheckStates</span></span>|<span data-ttu-id="59704-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `false`.</span><span class="sxs-lookup"><span data-stu-id="59704-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="59704-137">Neurčitá</span><span class="sxs-lookup"><span data-stu-id="59704-137">Indeterminate</span></span>|<span data-ttu-id="59704-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="59704-138">CheckStates</span></span>|<span data-ttu-id="59704-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> je `true`a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`.</span><span class="sxs-lookup"><span data-stu-id="59704-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="59704-140">Platný</span><span class="sxs-lookup"><span data-stu-id="59704-140">Valid</span></span>|<span data-ttu-id="59704-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="59704-141">ValidationStates</span></span>|<span data-ttu-id="59704-142">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="59704-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="59704-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="59704-143">InvalidFocused</span></span>|<span data-ttu-id="59704-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="59704-144">ValidationStates</span></span>|<span data-ttu-id="59704-145">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="59704-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="59704-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="59704-146">InvalidUnfocused</span></span>|<span data-ttu-id="59704-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="59704-147">ValidationStates</span></span>|<span data-ttu-id="59704-148">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="59704-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="59704-149">Pokud neurčitý vizuální stav v šabloně ovládacího prvku neexistuje, použije se jako výchozí vizuální stav Nekontrolovaná vizuální hodnota.</span><span class="sxs-lookup"><span data-stu-id="59704-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="59704-150">ToggleButton ControlTemplate – příklad</span><span class="sxs-lookup"><span data-stu-id="59704-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="59704-151">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="59704-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="59704-152">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="59704-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="59704-153">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="59704-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="59704-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59704-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="59704-155">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="59704-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="59704-156">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="59704-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="59704-157">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="59704-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="59704-158">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="59704-158">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
