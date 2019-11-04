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
ms.openlocfilehash: 7c4680a3ea9352e94d628e786fc8e4fd71018d00
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458252"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="e373f-102">TextBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e373f-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="e373f-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e373f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="e373f-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="e373f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e373f-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e373f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="e373f-106">Části textového pole</span><span class="sxs-lookup"><span data-stu-id="e373f-106">TextBox Parts</span></span>  
 <span data-ttu-id="e373f-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e373f-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="e373f-108">Částí</span><span class="sxs-lookup"><span data-stu-id="e373f-108">Part</span></span>|<span data-ttu-id="e373f-109">Typ</span><span class="sxs-lookup"><span data-stu-id="e373f-109">Type</span></span>|<span data-ttu-id="e373f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e373f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e373f-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="e373f-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="e373f-112">Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="e373f-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="e373f-113">Text <xref:System.Windows.Controls.TextBox> se zobrazí v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="e373f-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="e373f-114">Textové pole – stavy</span><span class="sxs-lookup"><span data-stu-id="e373f-114">TextBox States</span></span>  
 <span data-ttu-id="e373f-115">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e373f-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="e373f-116">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="e373f-116">VisualState Name</span></span>|<span data-ttu-id="e373f-117">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="e373f-117">VisualStateGroup Name</span></span>|<span data-ttu-id="e373f-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e373f-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="e373f-119">Běžnou</span><span class="sxs-lookup"><span data-stu-id="e373f-119">Normal</span></span>|<span data-ttu-id="e373f-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e373f-120">CommonStates</span></span>|<span data-ttu-id="e373f-121">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="e373f-121">The default state.</span></span>|  
|<span data-ttu-id="e373f-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="e373f-122">MouseOver</span></span>|<span data-ttu-id="e373f-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e373f-123">CommonStates</span></span>|<span data-ttu-id="e373f-124">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="e373f-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="e373f-125">Zabezpečen</span><span class="sxs-lookup"><span data-stu-id="e373f-125">Disabled</span></span>|<span data-ttu-id="e373f-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e373f-126">CommonStates</span></span>|<span data-ttu-id="e373f-127">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="e373f-127">The control is disabled.</span></span>|  
|<span data-ttu-id="e373f-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="e373f-128">ReadOnly</span></span>|<span data-ttu-id="e373f-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e373f-129">CommonStates</span></span>|<span data-ttu-id="e373f-130">Uživatel nemůže měnit text v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e373f-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="e373f-131">Zaměřil</span><span class="sxs-lookup"><span data-stu-id="e373f-131">Focused</span></span>|<span data-ttu-id="e373f-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e373f-132">FocusStates</span></span>|<span data-ttu-id="e373f-133">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="e373f-133">The control has focus.</span></span>|  
|<span data-ttu-id="e373f-134">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="e373f-134">Unfocused</span></span>|<span data-ttu-id="e373f-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e373f-135">FocusStates</span></span>|<span data-ttu-id="e373f-136">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="e373f-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="e373f-137">Platné</span><span class="sxs-lookup"><span data-stu-id="e373f-137">Valid</span></span>|<span data-ttu-id="e373f-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e373f-138">ValidationStates</span></span>|<span data-ttu-id="e373f-139">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="e373f-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e373f-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e373f-140">InvalidFocused</span></span>|<span data-ttu-id="e373f-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e373f-141">ValidationStates</span></span>|<span data-ttu-id="e373f-142">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="e373f-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e373f-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e373f-143">InvalidUnfocused</span></span>|<span data-ttu-id="e373f-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e373f-144">ValidationStates</span></span>|<span data-ttu-id="e373f-145">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="e373f-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="e373f-146">Příklad textového ControlTemplateu</span><span class="sxs-lookup"><span data-stu-id="e373f-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="e373f-147">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e373f-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="e373f-148">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="e373f-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e373f-149">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="e373f-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e373f-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e373f-150">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e373f-151">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e373f-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="e373f-152">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e373f-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="e373f-153">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e373f-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="e373f-154">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e373f-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
