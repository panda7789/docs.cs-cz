---
title: PasswordBox – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 227ccbda8d570868258508935a5d95f0f40663ab
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458836"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="dd8ef-102">PasswordBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="dd8ef-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="dd8ef-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="dd8ef-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="dd8ef-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="dd8ef-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="dd8ef-106">PasswordBox části</span><span class="sxs-lookup"><span data-stu-id="dd8ef-106">PasswordBox Parts</span></span>

<span data-ttu-id="dd8ef-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="dd8ef-108">Částí</span><span class="sxs-lookup"><span data-stu-id="dd8ef-108">Part</span></span>|<span data-ttu-id="dd8ef-109">Typ</span><span class="sxs-lookup"><span data-stu-id="dd8ef-109">Type</span></span>|<span data-ttu-id="dd8ef-110">Popis</span><span class="sxs-lookup"><span data-stu-id="dd8ef-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="dd8ef-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="dd8ef-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="dd8ef-112">Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="dd8ef-113">Text <xref:System.Windows.Controls.PasswordBox> se zobrazí v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="dd8ef-114">PasswordBox stavy</span><span class="sxs-lookup"><span data-stu-id="dd8ef-114">PasswordBox States</span></span>

<span data-ttu-id="dd8ef-115">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="dd8ef-116">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="dd8ef-116">VisualState Name</span></span>|<span data-ttu-id="dd8ef-117">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="dd8ef-117">VisualStateGroup Name</span></span>|<span data-ttu-id="dd8ef-118">Popis</span><span class="sxs-lookup"><span data-stu-id="dd8ef-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="dd8ef-119">Běžnou</span><span class="sxs-lookup"><span data-stu-id="dd8ef-119">Normal</span></span>|<span data-ttu-id="dd8ef-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="dd8ef-120">CommonStates</span></span>|<span data-ttu-id="dd8ef-121">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-121">The default state.</span></span>|
|<span data-ttu-id="dd8ef-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="dd8ef-122">MouseOver</span></span>|<span data-ttu-id="dd8ef-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="dd8ef-123">CommonStates</span></span>|<span data-ttu-id="dd8ef-124">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="dd8ef-125">Zabezpečen</span><span class="sxs-lookup"><span data-stu-id="dd8ef-125">Disabled</span></span>|<span data-ttu-id="dd8ef-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="dd8ef-126">CommonStates</span></span>|<span data-ttu-id="dd8ef-127">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-127">The control is disabled.</span></span>|
|<span data-ttu-id="dd8ef-128">Zaměřil</span><span class="sxs-lookup"><span data-stu-id="dd8ef-128">Focused</span></span>|<span data-ttu-id="dd8ef-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="dd8ef-129">FocusStates</span></span>|<span data-ttu-id="dd8ef-130">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-130">The control has focus.</span></span>|
|<span data-ttu-id="dd8ef-131">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="dd8ef-131">Unfocused</span></span>|<span data-ttu-id="dd8ef-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="dd8ef-132">FocusStates</span></span>|<span data-ttu-id="dd8ef-133">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-133">The control does not have focus.</span></span>|
|<span data-ttu-id="dd8ef-134">Platné</span><span class="sxs-lookup"><span data-stu-id="dd8ef-134">Valid</span></span>|<span data-ttu-id="dd8ef-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="dd8ef-135">ValidationStates</span></span>|<span data-ttu-id="dd8ef-136">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="dd8ef-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="dd8ef-137">InvalidFocused</span></span>|<span data-ttu-id="dd8ef-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="dd8ef-138">ValidationStates</span></span>|<span data-ttu-id="dd8ef-139">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="dd8ef-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="dd8ef-140">InvalidUnfocused</span></span>|<span data-ttu-id="dd8ef-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="dd8ef-141">ValidationStates</span></span>|<span data-ttu-id="dd8ef-142">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="dd8ef-143">PasswordBox ControlTemplate – příklad</span><span class="sxs-lookup"><span data-stu-id="dd8ef-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="dd8ef-144">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="dd8ef-145">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="dd8ef-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="dd8ef-146">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="dd8ef-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd8ef-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd8ef-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="dd8ef-148">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="dd8ef-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="dd8ef-149">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="dd8ef-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="dd8ef-150">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="dd8ef-150">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="dd8ef-151">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="dd8ef-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
