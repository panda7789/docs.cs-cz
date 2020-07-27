---
title: TextBox – styly a šablony
description: Přečtěte si o stylech a šablonách ovládacího prvku TextBox Windows Presentation Foundation. Upravte ControlTemplate tak, aby měl ovládací prvek jedinečný vzhled.
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 0e15fd40f5590ee46da49cc6c0d5fb30e051f7e4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164731"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="fb43b-104">TextBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="fb43b-104">TextBox Styles and Templates</span></span>
<span data-ttu-id="fb43b-105">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.TextBox> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fb43b-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="fb43b-106">Můžete změnit výchozí nastavení <xref:System.Windows.Controls.ControlTemplate> a dát ovládacímu prvku jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="fb43b-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="fb43b-107">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="fb43b-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="fb43b-108">Části textového pole</span><span class="sxs-lookup"><span data-stu-id="fb43b-108">TextBox Parts</span></span>  
 <span data-ttu-id="fb43b-109">V následující tabulce jsou uvedeny pojmenované části <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb43b-109">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="fb43b-110">Část</span><span class="sxs-lookup"><span data-stu-id="fb43b-110">Part</span></span>|<span data-ttu-id="fb43b-111">Typ</span><span class="sxs-lookup"><span data-stu-id="fb43b-111">Type</span></span>|<span data-ttu-id="fb43b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fb43b-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fb43b-113">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="fb43b-113">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="fb43b-114">Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="fb43b-114">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="fb43b-115">Text <xref:System.Windows.Controls.TextBox> je zobrazen v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="fb43b-115">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="fb43b-116">Textové pole – stavy</span><span class="sxs-lookup"><span data-stu-id="fb43b-116">TextBox States</span></span>  
 <span data-ttu-id="fb43b-117">V následující tabulce jsou uvedeny vizuální stavy <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb43b-117">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="fb43b-118">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="fb43b-118">VisualState Name</span></span>|<span data-ttu-id="fb43b-119">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="fb43b-119">VisualStateGroup Name</span></span>|<span data-ttu-id="fb43b-120">Popis</span><span class="sxs-lookup"><span data-stu-id="fb43b-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="fb43b-121">Normální</span><span class="sxs-lookup"><span data-stu-id="fb43b-121">Normal</span></span>|<span data-ttu-id="fb43b-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb43b-122">CommonStates</span></span>|<span data-ttu-id="fb43b-123">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="fb43b-123">The default state.</span></span>|  
|<span data-ttu-id="fb43b-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="fb43b-124">MouseOver</span></span>|<span data-ttu-id="fb43b-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb43b-125">CommonStates</span></span>|<span data-ttu-id="fb43b-126">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="fb43b-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="fb43b-127">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="fb43b-127">Disabled</span></span>|<span data-ttu-id="fb43b-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb43b-128">CommonStates</span></span>|<span data-ttu-id="fb43b-129">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="fb43b-129">The control is disabled.</span></span>|  
|<span data-ttu-id="fb43b-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="fb43b-130">ReadOnly</span></span>|<span data-ttu-id="fb43b-131">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb43b-131">CommonStates</span></span>|<span data-ttu-id="fb43b-132">Uživatel nemůže změnit text v <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="fb43b-132">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="fb43b-133">Focused</span><span class="sxs-lookup"><span data-stu-id="fb43b-133">Focused</span></span>|<span data-ttu-id="fb43b-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fb43b-134">FocusStates</span></span>|<span data-ttu-id="fb43b-135">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="fb43b-135">The control has focus.</span></span>|  
|<span data-ttu-id="fb43b-136">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="fb43b-136">Unfocused</span></span>|<span data-ttu-id="fb43b-137">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fb43b-137">FocusStates</span></span>|<span data-ttu-id="fb43b-138">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="fb43b-138">The control does not have focus.</span></span>|  
|<span data-ttu-id="fb43b-139">Platné</span><span class="sxs-lookup"><span data-stu-id="fb43b-139">Valid</span></span>|<span data-ttu-id="fb43b-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb43b-140">ValidationStates</span></span>|<span data-ttu-id="fb43b-141">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídu a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojenou vlastnost je `false` .</span><span class="sxs-lookup"><span data-stu-id="fb43b-141">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="fb43b-142">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="fb43b-142">InvalidFocused</span></span>|<span data-ttu-id="fb43b-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb43b-143">ValidationStates</span></span>|<span data-ttu-id="fb43b-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost má `true` fokus na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fb43b-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="fb43b-145">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="fb43b-145">InvalidUnfocused</span></span>|<span data-ttu-id="fb43b-146">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb43b-146">ValidationStates</span></span>|<span data-ttu-id="fb43b-147"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="fb43b-147">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="fb43b-148">Příklad textového ControlTemplateu</span><span class="sxs-lookup"><span data-stu-id="fb43b-148">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="fb43b-149">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TextBox> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fb43b-149">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="fb43b-150">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="fb43b-150">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="fb43b-151">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="fb43b-151">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb43b-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb43b-152">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="fb43b-153">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="fb43b-153">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="fb43b-154">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="fb43b-154">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="fb43b-155">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="fb43b-155">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="fb43b-156">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="fb43b-156">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
