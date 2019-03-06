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
ms.openlocfilehash: 16f087051e438fa0dbe248c46b0ec555c07cc06c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367905"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="8ebc6-102">TextBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="8ebc6-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="8ebc6-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="8ebc6-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8ebc6-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="8ebc6-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="8ebc6-106">Části textového pole</span><span class="sxs-lookup"><span data-stu-id="8ebc6-106">TextBox Parts</span></span>  
 <span data-ttu-id="8ebc6-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="8ebc6-108">Část</span><span class="sxs-lookup"><span data-stu-id="8ebc6-108">Part</span></span>|<span data-ttu-id="8ebc6-109">Typ</span><span class="sxs-lookup"><span data-stu-id="8ebc6-109">Type</span></span>|<span data-ttu-id="8ebc6-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8ebc6-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8ebc6-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="8ebc6-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="8ebc6-112">Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="8ebc6-113">Text <xref:System.Windows.Controls.TextBox> se zobrazí v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="8ebc6-114">TextBox – stavy</span><span class="sxs-lookup"><span data-stu-id="8ebc6-114">TextBox States</span></span>  
 <span data-ttu-id="8ebc6-115">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="8ebc6-116">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="8ebc6-116">VisualState Name</span></span>|<span data-ttu-id="8ebc6-117">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="8ebc6-117">VisualStateGroup Name</span></span>|<span data-ttu-id="8ebc6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8ebc6-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="8ebc6-119">Normální</span><span class="sxs-lookup"><span data-stu-id="8ebc6-119">Normal</span></span>|<span data-ttu-id="8ebc6-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8ebc6-120">CommonStates</span></span>|<span data-ttu-id="8ebc6-121">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-121">The default state.</span></span>|  
|<span data-ttu-id="8ebc6-122">Myš nad</span><span class="sxs-lookup"><span data-stu-id="8ebc6-122">MouseOver</span></span>|<span data-ttu-id="8ebc6-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8ebc6-123">CommonStates</span></span>|<span data-ttu-id="8ebc6-124">Je ukazatel myši umístěn nad ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="8ebc6-125">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="8ebc6-125">Disabled</span></span>|<span data-ttu-id="8ebc6-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8ebc6-126">CommonStates</span></span>|<span data-ttu-id="8ebc6-127">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-127">The control is disabled.</span></span>|  
|<span data-ttu-id="8ebc6-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="8ebc6-128">ReadOnly</span></span>|<span data-ttu-id="8ebc6-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8ebc6-129">CommonStates</span></span>|<span data-ttu-id="8ebc6-130">Uživatel nemůže změnit text <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="8ebc6-131">Fokus</span><span class="sxs-lookup"><span data-stu-id="8ebc6-131">Focused</span></span>|<span data-ttu-id="8ebc6-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8ebc6-132">FocusStates</span></span>|<span data-ttu-id="8ebc6-133">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-133">The control has focus.</span></span>|  
|<span data-ttu-id="8ebc6-134">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="8ebc6-134">Unfocused</span></span>|<span data-ttu-id="8ebc6-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8ebc6-135">FocusStates</span></span>|<span data-ttu-id="8ebc6-136">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="8ebc6-137">Platné</span><span class="sxs-lookup"><span data-stu-id="8ebc6-137">Valid</span></span>|<span data-ttu-id="8ebc6-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8ebc6-138">ValidationStates</span></span>|<span data-ttu-id="8ebc6-139">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="8ebc6-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="8ebc6-140">InvalidFocused</span></span>|<span data-ttu-id="8ebc6-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8ebc6-141">ValidationStates</span></span>|<span data-ttu-id="8ebc6-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="8ebc6-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="8ebc6-143">InvalidUnfocused</span></span>|<span data-ttu-id="8ebc6-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8ebc6-144">ValidationStates</span></span>|<span data-ttu-id="8ebc6-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="8ebc6-146">Příklad textového pole ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="8ebc6-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="8ebc6-147">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="8ebc6-148">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="8ebc6-149">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="8ebc6-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ebc6-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ebc6-150">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="8ebc6-151">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="8ebc6-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="8ebc6-152">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="8ebc6-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="8ebc6-153">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="8ebc6-153">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="8ebc6-154">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="8ebc6-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
