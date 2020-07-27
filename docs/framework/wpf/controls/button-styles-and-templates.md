---
title: Styly a šablony tlačítek
description: Přečtěte si o stylech a šablonách ovládacího prvku tlačítko Windows Presentation Foundation. Upravte ControlTemplate tak, aby měl ovládací prvek jedinečný vzhled.
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: 11509adeef397f26eb040e6e98d0edb333b2515f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166263"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="65a35-104">Styly a šablony tlačítek</span><span class="sxs-lookup"><span data-stu-id="65a35-104">Button Styles and Templates</span></span>
<span data-ttu-id="65a35-105">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Button> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="65a35-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="65a35-106">Můžete změnit výchozí nastavení <xref:System.Windows.Controls.ControlTemplate> a dát ovládacímu prvku jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="65a35-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="65a35-107">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="65a35-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="65a35-108">Části tlačítek</span><span class="sxs-lookup"><span data-stu-id="65a35-108">Button Parts</span></span>  
 <span data-ttu-id="65a35-109"><xref:System.Windows.Controls.Button>Ovládací prvek nemá žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="65a35-109">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="65a35-110">Stavy tlačítek</span><span class="sxs-lookup"><span data-stu-id="65a35-110">Button States</span></span>  
 <span data-ttu-id="65a35-111">V následující tabulce jsou uvedeny vizuální stavy <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="65a35-111">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="65a35-112">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="65a35-112">VisualState Name</span></span>|<span data-ttu-id="65a35-113">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="65a35-113">VisualStateGroup Name</span></span>|<span data-ttu-id="65a35-114">Popis</span><span class="sxs-lookup"><span data-stu-id="65a35-114">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="65a35-115">Normální</span><span class="sxs-lookup"><span data-stu-id="65a35-115">Normal</span></span>|<span data-ttu-id="65a35-116">CommonStates</span><span class="sxs-lookup"><span data-stu-id="65a35-116">CommonStates</span></span>|<span data-ttu-id="65a35-117">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="65a35-117">The default state.</span></span>|  
|<span data-ttu-id="65a35-118">MouseOver</span><span class="sxs-lookup"><span data-stu-id="65a35-118">MouseOver</span></span>|<span data-ttu-id="65a35-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="65a35-119">CommonStates</span></span>|<span data-ttu-id="65a35-120">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="65a35-120">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="65a35-121">Pressed</span><span class="sxs-lookup"><span data-stu-id="65a35-121">Pressed</span></span>|<span data-ttu-id="65a35-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="65a35-122">CommonStates</span></span>|<span data-ttu-id="65a35-123">Ovládací prvek se stiskne.</span><span class="sxs-lookup"><span data-stu-id="65a35-123">The control is pressed.</span></span>|  
|<span data-ttu-id="65a35-124">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="65a35-124">Disabled</span></span>|<span data-ttu-id="65a35-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="65a35-125">CommonStates</span></span>|<span data-ttu-id="65a35-126">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="65a35-126">The control is disabled.</span></span>|  
|<span data-ttu-id="65a35-127">Focused</span><span class="sxs-lookup"><span data-stu-id="65a35-127">Focused</span></span>|<span data-ttu-id="65a35-128">FocusStates</span><span class="sxs-lookup"><span data-stu-id="65a35-128">FocusStates</span></span>|<span data-ttu-id="65a35-129">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="65a35-129">The control has focus.</span></span>|  
|<span data-ttu-id="65a35-130">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="65a35-130">Unfocused</span></span>|<span data-ttu-id="65a35-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="65a35-131">FocusStates</span></span>|<span data-ttu-id="65a35-132">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="65a35-132">The control does not have focus.</span></span>|  
|<span data-ttu-id="65a35-133">Platné</span><span class="sxs-lookup"><span data-stu-id="65a35-133">Valid</span></span>|<span data-ttu-id="65a35-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="65a35-134">ValidationStates</span></span>|<span data-ttu-id="65a35-135">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídu a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojenou vlastnost je `false` .</span><span class="sxs-lookup"><span data-stu-id="65a35-135">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="65a35-136">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="65a35-136">InvalidFocused</span></span>|<span data-ttu-id="65a35-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="65a35-137">ValidationStates</span></span>|<span data-ttu-id="65a35-138"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost je `true` a ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="65a35-138">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="65a35-139">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="65a35-139">InvalidUnfocused</span></span>|<span data-ttu-id="65a35-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="65a35-140">ValidationStates</span></span>|<span data-ttu-id="65a35-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost je `true` a ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="65a35-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="65a35-142">Příklad ControlTemplate tlačítka</span><span class="sxs-lookup"><span data-stu-id="65a35-142">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="65a35-143">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="65a35-143">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="65a35-144">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="65a35-144">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="65a35-145">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="65a35-145">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a35-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="65a35-146">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="65a35-147">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="65a35-147">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="65a35-148">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="65a35-148">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="65a35-149">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="65a35-149">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="65a35-150">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="65a35-150">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
