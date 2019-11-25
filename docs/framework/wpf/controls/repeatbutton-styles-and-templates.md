---
title: RepeatButton – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
ms.openlocfilehash: 8585e98536fd908daa11f21da395cab44924d612
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283430"
---
# <a name="repeatbutton-styles-and-templates"></a><span data-ttu-id="916a5-102">RepeatButton – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="916a5-102">RepeatButton Styles and Templates</span></span>

<span data-ttu-id="916a5-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="916a5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="916a5-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="916a5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="916a5-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="916a5-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="repeatbutton-parts"></a><span data-ttu-id="916a5-106">RepeatButton části</span><span class="sxs-lookup"><span data-stu-id="916a5-106">RepeatButton Parts</span></span>

<span data-ttu-id="916a5-107">Ovládací prvek <xref:System.Windows.Controls.Primitives.RepeatButton> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="916a5-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>

## <a name="repeatbutton-states"></a><span data-ttu-id="916a5-108">RepeatButton stavy</span><span class="sxs-lookup"><span data-stu-id="916a5-108">RepeatButton States</span></span>

<span data-ttu-id="916a5-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="916a5-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

|<span data-ttu-id="916a5-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="916a5-110">VisualState Name</span></span>|<span data-ttu-id="916a5-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="916a5-111">VisualStateGroup Name</span></span>|<span data-ttu-id="916a5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="916a5-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="916a5-113">Normální</span><span class="sxs-lookup"><span data-stu-id="916a5-113">Normal</span></span>|<span data-ttu-id="916a5-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="916a5-114">CommonStates</span></span>|<span data-ttu-id="916a5-115">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="916a5-115">The default state.</span></span>|
|<span data-ttu-id="916a5-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="916a5-116">MouseOver</span></span>|<span data-ttu-id="916a5-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="916a5-117">CommonStates</span></span>|<span data-ttu-id="916a5-118">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="916a5-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="916a5-119">Stisknutí</span><span class="sxs-lookup"><span data-stu-id="916a5-119">Pressed</span></span>|<span data-ttu-id="916a5-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="916a5-120">CommonStates</span></span>|<span data-ttu-id="916a5-121">Ovládací prvek se stiskne.</span><span class="sxs-lookup"><span data-stu-id="916a5-121">The control is pressed.</span></span>|
|<span data-ttu-id="916a5-122">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="916a5-122">Disabled</span></span>|<span data-ttu-id="916a5-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="916a5-123">CommonStates</span></span>|<span data-ttu-id="916a5-124">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="916a5-124">The control is disabled.</span></span>|
|<span data-ttu-id="916a5-125">Zaměřil</span><span class="sxs-lookup"><span data-stu-id="916a5-125">Focused</span></span>|<span data-ttu-id="916a5-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="916a5-126">FocusStates</span></span>|<span data-ttu-id="916a5-127">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="916a5-127">The control has focus.</span></span>|
|<span data-ttu-id="916a5-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="916a5-128">Unfocused</span></span>|<span data-ttu-id="916a5-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="916a5-129">FocusStates</span></span>|<span data-ttu-id="916a5-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="916a5-130">The control does not have focus.</span></span>|
|<span data-ttu-id="916a5-131">Platné</span><span class="sxs-lookup"><span data-stu-id="916a5-131">Valid</span></span>|<span data-ttu-id="916a5-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="916a5-132">ValidationStates</span></span>|<span data-ttu-id="916a5-133">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="916a5-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="916a5-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="916a5-134">InvalidFocused</span></span>|<span data-ttu-id="916a5-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="916a5-135">ValidationStates</span></span>|<span data-ttu-id="916a5-136">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="916a5-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="916a5-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="916a5-137">InvalidUnfocused</span></span>|<span data-ttu-id="916a5-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="916a5-138">ValidationStates</span></span>|<span data-ttu-id="916a5-139">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="916a5-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="916a5-140">RepeatButton ControlTemplate – příklad</span><span class="sxs-lookup"><span data-stu-id="916a5-140">RepeatButton ControlTemplate Example</span></span>

<span data-ttu-id="916a5-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="916a5-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

<span data-ttu-id="916a5-142">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="916a5-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="916a5-143">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="916a5-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="916a5-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="916a5-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="916a5-145">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="916a5-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="916a5-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="916a5-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="916a5-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="916a5-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="916a5-148">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="916a5-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
