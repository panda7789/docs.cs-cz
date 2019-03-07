---
title: RepeatButton – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
ms.openlocfilehash: 86f212326bc707e4b07b8cab8d9a95d4f6ef8920
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57507316"
---
# <a name="repeatbutton-styles-and-templates"></a><span data-ttu-id="38f56-102">RepeatButton – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="38f56-102">RepeatButton Styles and Templates</span></span>

<span data-ttu-id="38f56-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.RepeatButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="38f56-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="38f56-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="38f56-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="38f56-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="38f56-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="repeatbutton-parts"></a><span data-ttu-id="38f56-106">RepeatButton částí</span><span class="sxs-lookup"><span data-stu-id="38f56-106">RepeatButton Parts</span></span>

<span data-ttu-id="38f56-107"><xref:System.Windows.Controls.Primitives.RepeatButton> Ovládací prvek nemá žádné pojmenované součásti.</span><span class="sxs-lookup"><span data-stu-id="38f56-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>

## <a name="repeatbutton-states"></a><span data-ttu-id="38f56-108">RepeatButton stavy</span><span class="sxs-lookup"><span data-stu-id="38f56-108">RepeatButton States</span></span>

<span data-ttu-id="38f56-109">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.RepeatButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="38f56-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

|<span data-ttu-id="38f56-110">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="38f56-110">VisualState Name</span></span>|<span data-ttu-id="38f56-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="38f56-111">VisualStateGroup Name</span></span>|<span data-ttu-id="38f56-112">Popis</span><span class="sxs-lookup"><span data-stu-id="38f56-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="38f56-113">Normální</span><span class="sxs-lookup"><span data-stu-id="38f56-113">Normal</span></span>|<span data-ttu-id="38f56-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="38f56-114">CommonStates</span></span>|<span data-ttu-id="38f56-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="38f56-115">The default state.</span></span>|
|<span data-ttu-id="38f56-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="38f56-116">MouseOver</span></span>|<span data-ttu-id="38f56-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="38f56-117">CommonStates</span></span>|<span data-ttu-id="38f56-118">Je ukazatel myši umístěn nad ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="38f56-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="38f56-119">Stisknutí</span><span class="sxs-lookup"><span data-stu-id="38f56-119">Pressed</span></span>|<span data-ttu-id="38f56-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="38f56-120">CommonStates</span></span>|<span data-ttu-id="38f56-121">Stisknutí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="38f56-121">The control is pressed.</span></span>|
|<span data-ttu-id="38f56-122">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="38f56-122">Disabled</span></span>|<span data-ttu-id="38f56-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="38f56-123">CommonStates</span></span>|<span data-ttu-id="38f56-124">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="38f56-124">The control is disabled.</span></span>|
|<span data-ttu-id="38f56-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="38f56-125">Focused</span></span>|<span data-ttu-id="38f56-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="38f56-126">FocusStates</span></span>|<span data-ttu-id="38f56-127">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="38f56-127">The control has focus.</span></span>|
|<span data-ttu-id="38f56-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="38f56-128">Unfocused</span></span>|<span data-ttu-id="38f56-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="38f56-129">FocusStates</span></span>|<span data-ttu-id="38f56-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="38f56-130">The control does not have focus.</span></span>|
|<span data-ttu-id="38f56-131">Platné</span><span class="sxs-lookup"><span data-stu-id="38f56-131">Valid</span></span>|<span data-ttu-id="38f56-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="38f56-132">ValidationStates</span></span>|<span data-ttu-id="38f56-133">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="38f56-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="38f56-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="38f56-134">InvalidFocused</span></span>|<span data-ttu-id="38f56-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="38f56-135">ValidationStates</span></span>|<span data-ttu-id="38f56-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="38f56-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="38f56-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="38f56-137">InvalidUnfocused</span></span>|<span data-ttu-id="38f56-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="38f56-138">ValidationStates</span></span>|<span data-ttu-id="38f56-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="38f56-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="38f56-140">Příklad RepeatButton ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="38f56-140">RepeatButton ControlTemplate Example</span></span>

<span data-ttu-id="38f56-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.RepeatButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="38f56-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

<span data-ttu-id="38f56-142">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="38f56-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="38f56-143">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="38f56-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="38f56-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38f56-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="38f56-145">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="38f56-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="38f56-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="38f56-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="38f56-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="38f56-147">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="38f56-148">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="38f56-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
