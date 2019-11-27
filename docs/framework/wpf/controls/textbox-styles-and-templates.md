---
title: TextBox – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 41e390c261836909240cc146a48729d48c4a410e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283702"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="60b53-102">TextBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="60b53-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="60b53-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="60b53-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="60b53-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="60b53-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="60b53-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="60b53-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="60b53-106">Části textového pole</span><span class="sxs-lookup"><span data-stu-id="60b53-106">TextBox Parts</span></span>  
 <span data-ttu-id="60b53-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="60b53-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="60b53-108">Částí</span><span class="sxs-lookup"><span data-stu-id="60b53-108">Part</span></span>|<span data-ttu-id="60b53-109">Typ</span><span class="sxs-lookup"><span data-stu-id="60b53-109">Type</span></span>|<span data-ttu-id="60b53-110">Popis</span><span class="sxs-lookup"><span data-stu-id="60b53-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="60b53-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="60b53-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="60b53-112">Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="60b53-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="60b53-113">Text <xref:System.Windows.Controls.TextBox> se zobrazí v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="60b53-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="60b53-114">Textové pole – stavy</span><span class="sxs-lookup"><span data-stu-id="60b53-114">TextBox States</span></span>  
 <span data-ttu-id="60b53-115">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="60b53-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="60b53-116">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="60b53-116">VisualState Name</span></span>|<span data-ttu-id="60b53-117">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="60b53-117">VisualStateGroup Name</span></span>|<span data-ttu-id="60b53-118">Popis</span><span class="sxs-lookup"><span data-stu-id="60b53-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="60b53-119">Normální</span><span class="sxs-lookup"><span data-stu-id="60b53-119">Normal</span></span>|<span data-ttu-id="60b53-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="60b53-120">CommonStates</span></span>|<span data-ttu-id="60b53-121">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="60b53-121">The default state.</span></span>|  
|<span data-ttu-id="60b53-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="60b53-122">MouseOver</span></span>|<span data-ttu-id="60b53-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="60b53-123">CommonStates</span></span>|<span data-ttu-id="60b53-124">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="60b53-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="60b53-125">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="60b53-125">Disabled</span></span>|<span data-ttu-id="60b53-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="60b53-126">CommonStates</span></span>|<span data-ttu-id="60b53-127">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="60b53-127">The control is disabled.</span></span>|  
|<span data-ttu-id="60b53-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="60b53-128">ReadOnly</span></span>|<span data-ttu-id="60b53-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="60b53-129">CommonStates</span></span>|<span data-ttu-id="60b53-130">Uživatel nemůže měnit text v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="60b53-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="60b53-131">Zaměřil</span><span class="sxs-lookup"><span data-stu-id="60b53-131">Focused</span></span>|<span data-ttu-id="60b53-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="60b53-132">FocusStates</span></span>|<span data-ttu-id="60b53-133">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="60b53-133">The control has focus.</span></span>|  
|<span data-ttu-id="60b53-134">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="60b53-134">Unfocused</span></span>|<span data-ttu-id="60b53-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="60b53-135">FocusStates</span></span>|<span data-ttu-id="60b53-136">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="60b53-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="60b53-137">Platný</span><span class="sxs-lookup"><span data-stu-id="60b53-137">Valid</span></span>|<span data-ttu-id="60b53-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="60b53-138">ValidationStates</span></span>|<span data-ttu-id="60b53-139">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="60b53-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="60b53-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="60b53-140">InvalidFocused</span></span>|<span data-ttu-id="60b53-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="60b53-141">ValidationStates</span></span>|<span data-ttu-id="60b53-142">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="60b53-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="60b53-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="60b53-143">InvalidUnfocused</span></span>|<span data-ttu-id="60b53-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="60b53-144">ValidationStates</span></span>|<span data-ttu-id="60b53-145">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="60b53-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="60b53-146">Příklad textového ControlTemplateu</span><span class="sxs-lookup"><span data-stu-id="60b53-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="60b53-147">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="60b53-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="60b53-148">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="60b53-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="60b53-149">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="60b53-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60b53-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60b53-150">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="60b53-151">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="60b53-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="60b53-152">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="60b53-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="60b53-153">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="60b53-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="60b53-154">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="60b53-154">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
