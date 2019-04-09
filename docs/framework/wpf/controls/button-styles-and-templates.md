---
title: Styly a šablony tlačítek
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: ec64c7c2051b12cba01135054a90e54864b7386a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116334"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="1b387-102">Styly a šablony tlačítek</span><span class="sxs-lookup"><span data-stu-id="1b387-102">Button Styles and Templates</span></span>
<span data-ttu-id="1b387-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1b387-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="1b387-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1b387-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1b387-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="1b387-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="1b387-106">Tlačítko částí</span><span class="sxs-lookup"><span data-stu-id="1b387-106">Button Parts</span></span>  
 <span data-ttu-id="1b387-107"><xref:System.Windows.Controls.Button> Ovládací prvek nemá žádné pojmenované součásti.</span><span class="sxs-lookup"><span data-stu-id="1b387-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="1b387-108">Stavy tlačítka</span><span class="sxs-lookup"><span data-stu-id="1b387-108">Button States</span></span>  
 <span data-ttu-id="1b387-109">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1b387-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="1b387-110">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="1b387-110">VisualState Name</span></span>|<span data-ttu-id="1b387-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="1b387-111">VisualStateGroup Name</span></span>|<span data-ttu-id="1b387-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1b387-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1b387-113">Normální</span><span class="sxs-lookup"><span data-stu-id="1b387-113">Normal</span></span>|<span data-ttu-id="1b387-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1b387-114">CommonStates</span></span>|<span data-ttu-id="1b387-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="1b387-115">The default state.</span></span>|  
|<span data-ttu-id="1b387-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="1b387-116">MouseOver</span></span>|<span data-ttu-id="1b387-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1b387-117">CommonStates</span></span>|<span data-ttu-id="1b387-118">Je ukazatel myši umístěn nad ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="1b387-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="1b387-119">Stisknutí</span><span class="sxs-lookup"><span data-stu-id="1b387-119">Pressed</span></span>|<span data-ttu-id="1b387-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1b387-120">CommonStates</span></span>|<span data-ttu-id="1b387-121">Stisknutí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1b387-121">The control is pressed.</span></span>|  
|<span data-ttu-id="1b387-122">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="1b387-122">Disabled</span></span>|<span data-ttu-id="1b387-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1b387-123">CommonStates</span></span>|<span data-ttu-id="1b387-124">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="1b387-124">The control is disabled.</span></span>|  
|<span data-ttu-id="1b387-125">Fokus</span><span class="sxs-lookup"><span data-stu-id="1b387-125">Focused</span></span>|<span data-ttu-id="1b387-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="1b387-126">FocusStates</span></span>|<span data-ttu-id="1b387-127">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="1b387-127">The control has focus.</span></span>|  
|<span data-ttu-id="1b387-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="1b387-128">Unfocused</span></span>|<span data-ttu-id="1b387-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="1b387-129">FocusStates</span></span>|<span data-ttu-id="1b387-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="1b387-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="1b387-131">Platné</span><span class="sxs-lookup"><span data-stu-id="1b387-131">Valid</span></span>|<span data-ttu-id="1b387-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1b387-132">ValidationStates</span></span>|<span data-ttu-id="1b387-133">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="1b387-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1b387-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1b387-134">InvalidFocused</span></span>|<span data-ttu-id="1b387-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1b387-135">ValidationStates</span></span>|<span data-ttu-id="1b387-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` a ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="1b387-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="1b387-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1b387-137">InvalidUnfocused</span></span>|<span data-ttu-id="1b387-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1b387-138">ValidationStates</span></span>|<span data-ttu-id="1b387-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` a ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="1b387-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="1b387-140">Příklad tlačítko ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="1b387-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="1b387-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1b387-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="1b387-142">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="1b387-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="1b387-143">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="1b387-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b387-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b387-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="1b387-145">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="1b387-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="1b387-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="1b387-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="1b387-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="1b387-147">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="1b387-148">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="1b387-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
