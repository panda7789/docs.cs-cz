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
ms.openlocfilehash: 9c6a8ad0a954d244fb693e25965ab52dda114068
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459845"
---
# <a name="repeatbutton-styles-and-templates"></a><span data-ttu-id="6e603-102">RepeatButton – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="6e603-102">RepeatButton Styles and Templates</span></span>

<span data-ttu-id="6e603-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="6e603-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="6e603-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="6e603-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6e603-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6e603-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="repeatbutton-parts"></a><span data-ttu-id="6e603-106">RepeatButton části</span><span class="sxs-lookup"><span data-stu-id="6e603-106">RepeatButton Parts</span></span>

<span data-ttu-id="6e603-107">Ovládací prvek <xref:System.Windows.Controls.Primitives.RepeatButton> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="6e603-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>

## <a name="repeatbutton-states"></a><span data-ttu-id="6e603-108">RepeatButton stavy</span><span class="sxs-lookup"><span data-stu-id="6e603-108">RepeatButton States</span></span>

<span data-ttu-id="6e603-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="6e603-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

|<span data-ttu-id="6e603-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="6e603-110">VisualState Name</span></span>|<span data-ttu-id="6e603-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6e603-111">VisualStateGroup Name</span></span>|<span data-ttu-id="6e603-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6e603-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="6e603-113">Běžnou</span><span class="sxs-lookup"><span data-stu-id="6e603-113">Normal</span></span>|<span data-ttu-id="6e603-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6e603-114">CommonStates</span></span>|<span data-ttu-id="6e603-115">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="6e603-115">The default state.</span></span>|
|<span data-ttu-id="6e603-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="6e603-116">MouseOver</span></span>|<span data-ttu-id="6e603-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6e603-117">CommonStates</span></span>|<span data-ttu-id="6e603-118">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="6e603-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="6e603-119">Stisknete</span><span class="sxs-lookup"><span data-stu-id="6e603-119">Pressed</span></span>|<span data-ttu-id="6e603-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6e603-120">CommonStates</span></span>|<span data-ttu-id="6e603-121">Ovládací prvek se stiskne.</span><span class="sxs-lookup"><span data-stu-id="6e603-121">The control is pressed.</span></span>|
|<span data-ttu-id="6e603-122">Zabezpečen</span><span class="sxs-lookup"><span data-stu-id="6e603-122">Disabled</span></span>|<span data-ttu-id="6e603-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6e603-123">CommonStates</span></span>|<span data-ttu-id="6e603-124">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="6e603-124">The control is disabled.</span></span>|
|<span data-ttu-id="6e603-125">Zaměřil</span><span class="sxs-lookup"><span data-stu-id="6e603-125">Focused</span></span>|<span data-ttu-id="6e603-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6e603-126">FocusStates</span></span>|<span data-ttu-id="6e603-127">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="6e603-127">The control has focus.</span></span>|
|<span data-ttu-id="6e603-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="6e603-128">Unfocused</span></span>|<span data-ttu-id="6e603-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6e603-129">FocusStates</span></span>|<span data-ttu-id="6e603-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="6e603-130">The control does not have focus.</span></span>|
|<span data-ttu-id="6e603-131">Platné</span><span class="sxs-lookup"><span data-stu-id="6e603-131">Valid</span></span>|<span data-ttu-id="6e603-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6e603-132">ValidationStates</span></span>|<span data-ttu-id="6e603-133">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="6e603-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="6e603-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6e603-134">InvalidFocused</span></span>|<span data-ttu-id="6e603-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6e603-135">ValidationStates</span></span>|<span data-ttu-id="6e603-136">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="6e603-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="6e603-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6e603-137">InvalidUnfocused</span></span>|<span data-ttu-id="6e603-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6e603-138">ValidationStates</span></span>|<span data-ttu-id="6e603-139">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="6e603-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="6e603-140">RepeatButton ControlTemplate – příklad</span><span class="sxs-lookup"><span data-stu-id="6e603-140">RepeatButton ControlTemplate Example</span></span>

<span data-ttu-id="6e603-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="6e603-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

<span data-ttu-id="6e603-142">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="6e603-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="6e603-143">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="6e603-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e603-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e603-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="6e603-145">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="6e603-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="6e603-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6e603-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="6e603-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="6e603-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="6e603-148">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="6e603-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
