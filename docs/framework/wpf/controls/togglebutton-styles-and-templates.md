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
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805920"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="8bb4e-102">ToggleButton – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="8bb4e-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="8bb4e-103">Toto téma popisuje styly a <xref:System.Windows.Controls.Primitives.ToggleButton> šablony ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="8bb4e-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> prvek, aby ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8bb4e-105">Další informace naleznete [v tématu Vytvoření šablony ovládacího prvku](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="8bb4e-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="8bb4e-106">Součásti přepínačů</span><span class="sxs-lookup"><span data-stu-id="8bb4e-106">ToggleButton Parts</span></span>

<span data-ttu-id="8bb4e-107">Ovládací <xref:System.Windows.Controls.Primitives.ToggleButton> prvek nemá žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="8bb4e-108">Stavy přepínacích tlačítek</span><span class="sxs-lookup"><span data-stu-id="8bb4e-108">ToggleButton States</span></span>

<span data-ttu-id="8bb4e-109">V následující tabulce jsou uvedeny stavy vizuálu ovládacího <xref:System.Windows.Controls.Primitives.ToggleButton> prvku.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="8bb4e-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="8bb4e-110">VisualState Name</span></span>|<span data-ttu-id="8bb4e-111">Název visualstategroup</span><span class="sxs-lookup"><span data-stu-id="8bb4e-111">VisualStateGroup Name</span></span>|<span data-ttu-id="8bb4e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8bb4e-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="8bb4e-113">Normální</span><span class="sxs-lookup"><span data-stu-id="8bb4e-113">Normal</span></span>|<span data-ttu-id="8bb4e-114">Běžné státy</span><span class="sxs-lookup"><span data-stu-id="8bb4e-114">CommonStates</span></span>|<span data-ttu-id="8bb4e-115">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-115">The default state.</span></span>|
|<span data-ttu-id="8bb4e-116">Mouseover</span><span class="sxs-lookup"><span data-stu-id="8bb4e-116">MouseOver</span></span>|<span data-ttu-id="8bb4e-117">Běžné státy</span><span class="sxs-lookup"><span data-stu-id="8bb4e-117">CommonStates</span></span>|<span data-ttu-id="8bb4e-118">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="8bb4e-119">Pressed</span><span class="sxs-lookup"><span data-stu-id="8bb4e-119">Pressed</span></span>|<span data-ttu-id="8bb4e-120">Běžné státy</span><span class="sxs-lookup"><span data-stu-id="8bb4e-120">CommonStates</span></span>|<span data-ttu-id="8bb4e-121">Ovládací prvek je stisknut.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-121">The control is pressed.</span></span>|
|<span data-ttu-id="8bb4e-122">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="8bb4e-122">Disabled</span></span>|<span data-ttu-id="8bb4e-123">Běžné státy</span><span class="sxs-lookup"><span data-stu-id="8bb4e-123">CommonStates</span></span>|<span data-ttu-id="8bb4e-124">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-124">The control is disabled.</span></span>|
|<span data-ttu-id="8bb4e-125">Focused</span><span class="sxs-lookup"><span data-stu-id="8bb4e-125">Focused</span></span>|<span data-ttu-id="8bb4e-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8bb4e-126">FocusStates</span></span>|<span data-ttu-id="8bb4e-127">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-127">The control has focus.</span></span>|
|<span data-ttu-id="8bb4e-128">Rozostřený</span><span class="sxs-lookup"><span data-stu-id="8bb4e-128">Unfocused</span></span>|<span data-ttu-id="8bb4e-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8bb4e-129">FocusStates</span></span>|<span data-ttu-id="8bb4e-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-130">The control does not have focus.</span></span>|
|<span data-ttu-id="8bb4e-131">Zaškrtnuté</span><span class="sxs-lookup"><span data-stu-id="8bb4e-131">Checked</span></span>|<span data-ttu-id="8bb4e-132">Zkontrolovat stavy</span><span class="sxs-lookup"><span data-stu-id="8bb4e-132">CheckStates</span></span>|<span data-ttu-id="8bb4e-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `true`.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="8bb4e-134">Nekontrolovaná</span><span class="sxs-lookup"><span data-stu-id="8bb4e-134">Unchecked</span></span>|<span data-ttu-id="8bb4e-135">Zkontrolovat stavy</span><span class="sxs-lookup"><span data-stu-id="8bb4e-135">CheckStates</span></span>|<span data-ttu-id="8bb4e-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> je `false`.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="8bb4e-137">Neurčitý</span><span class="sxs-lookup"><span data-stu-id="8bb4e-137">Indeterminate</span></span>|<span data-ttu-id="8bb4e-138">Zkontrolovat stavy</span><span class="sxs-lookup"><span data-stu-id="8bb4e-138">CheckStates</span></span>|<span data-ttu-id="8bb4e-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>je `true`a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`je .</span><span class="sxs-lookup"><span data-stu-id="8bb4e-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="8bb4e-140">Platné</span><span class="sxs-lookup"><span data-stu-id="8bb4e-140">Valid</span></span>|<span data-ttu-id="8bb4e-141">Stavy ověření</span><span class="sxs-lookup"><span data-stu-id="8bb4e-141">ValidationStates</span></span>|<span data-ttu-id="8bb4e-142">Ovládací prvek <xref:System.Windows.Controls.Validation> používá třídu a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> `false`připojené vlastnosti je .</span><span class="sxs-lookup"><span data-stu-id="8bb4e-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="8bb4e-143">Neplatnéfocené</span><span class="sxs-lookup"><span data-stu-id="8bb4e-143">InvalidFocused</span></span>|<span data-ttu-id="8bb4e-144">Stavy ověření</span><span class="sxs-lookup"><span data-stu-id="8bb4e-144">ValidationStates</span></span>|<span data-ttu-id="8bb4e-145">Připojená <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> vlastnost `true` je a ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|
|<span data-ttu-id="8bb4e-146">Neplatnýnezaostřený</span><span class="sxs-lookup"><span data-stu-id="8bb4e-146">InvalidUnfocused</span></span>|<span data-ttu-id="8bb4e-147">Stavy ověření</span><span class="sxs-lookup"><span data-stu-id="8bb4e-147">ValidationStates</span></span>|<span data-ttu-id="8bb4e-148">Připojené <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> vlastnosti `true` je a ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="8bb4e-149">Pokud neurčitý vizuální stav neexistuje v šabloně ovládacího prvku, bude jako výchozí vizuální stav použit nekontrolovaný vizuální stav.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="8bb4e-150">Příklad šablony ovládacího prvku togglebutton</span><span class="sxs-lookup"><span data-stu-id="8bb4e-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="8bb4e-151">Následující příklad ukazuje, jak <xref:System.Windows.Controls.ControlTemplate> definovat <xref:System.Windows.Controls.Primitives.ToggleButton> pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="8bb4e-152">Předchozí příklad používá jeden nebo více z následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="8bb4e-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="8bb4e-153">Kompletní ukázku naleznete [v tématu Styling s ukázkou řídicích šablon](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="8bb4e-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="8bb4e-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bb4e-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="8bb4e-155">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="8bb4e-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="8bb4e-156">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="8bb4e-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="8bb4e-157">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="8bb4e-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="8bb4e-158">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="8bb4e-158">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
