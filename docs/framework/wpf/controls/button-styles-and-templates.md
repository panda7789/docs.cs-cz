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
ms.openlocfilehash: 64764d43191d30c191c5d6519982b16cfc86d26e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460952"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="4b0b2-102">Styly a šablony tlačítek</span><span class="sxs-lookup"><span data-stu-id="4b0b2-102">Button Styles and Templates</span></span>
<span data-ttu-id="4b0b2-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="4b0b2-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="4b0b2-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="4b0b2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="4b0b2-106">Části tlačítek</span><span class="sxs-lookup"><span data-stu-id="4b0b2-106">Button Parts</span></span>  
 <span data-ttu-id="4b0b2-107">Ovládací prvek <xref:System.Windows.Controls.Button> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="4b0b2-108">Stavy tlačítek</span><span class="sxs-lookup"><span data-stu-id="4b0b2-108">Button States</span></span>  
 <span data-ttu-id="4b0b2-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="4b0b2-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="4b0b2-110">VisualState Name</span></span>|<span data-ttu-id="4b0b2-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="4b0b2-111">VisualStateGroup Name</span></span>|<span data-ttu-id="4b0b2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4b0b2-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="4b0b2-113">Běžnou</span><span class="sxs-lookup"><span data-stu-id="4b0b2-113">Normal</span></span>|<span data-ttu-id="4b0b2-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b0b2-114">CommonStates</span></span>|<span data-ttu-id="4b0b2-115">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-115">The default state.</span></span>|  
|<span data-ttu-id="4b0b2-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="4b0b2-116">MouseOver</span></span>|<span data-ttu-id="4b0b2-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b0b2-117">CommonStates</span></span>|<span data-ttu-id="4b0b2-118">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="4b0b2-119">Stisknete</span><span class="sxs-lookup"><span data-stu-id="4b0b2-119">Pressed</span></span>|<span data-ttu-id="4b0b2-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b0b2-120">CommonStates</span></span>|<span data-ttu-id="4b0b2-121">Ovládací prvek se stiskne.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-121">The control is pressed.</span></span>|  
|<span data-ttu-id="4b0b2-122">Zabezpečen</span><span class="sxs-lookup"><span data-stu-id="4b0b2-122">Disabled</span></span>|<span data-ttu-id="4b0b2-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b0b2-123">CommonStates</span></span>|<span data-ttu-id="4b0b2-124">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-124">The control is disabled.</span></span>|  
|<span data-ttu-id="4b0b2-125">Zaměřil</span><span class="sxs-lookup"><span data-stu-id="4b0b2-125">Focused</span></span>|<span data-ttu-id="4b0b2-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="4b0b2-126">FocusStates</span></span>|<span data-ttu-id="4b0b2-127">Ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-127">The control has focus.</span></span>|  
|<span data-ttu-id="4b0b2-128">Bez fokusu</span><span class="sxs-lookup"><span data-stu-id="4b0b2-128">Unfocused</span></span>|<span data-ttu-id="4b0b2-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="4b0b2-129">FocusStates</span></span>|<span data-ttu-id="4b0b2-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="4b0b2-131">Platné</span><span class="sxs-lookup"><span data-stu-id="4b0b2-131">Valid</span></span>|<span data-ttu-id="4b0b2-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b0b2-132">ValidationStates</span></span>|<span data-ttu-id="4b0b2-133">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="4b0b2-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="4b0b2-134">InvalidFocused</span></span>|<span data-ttu-id="4b0b2-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b0b2-135">ValidationStates</span></span>|<span data-ttu-id="4b0b2-136">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` a ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="4b0b2-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="4b0b2-137">InvalidUnfocused</span></span>|<span data-ttu-id="4b0b2-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b0b2-138">ValidationStates</span></span>|<span data-ttu-id="4b0b2-139">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` a ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="4b0b2-140">Příklad ControlTemplate tlačítka</span><span class="sxs-lookup"><span data-stu-id="4b0b2-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="4b0b2-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="4b0b2-142">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="4b0b2-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="4b0b2-143">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="4b0b2-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0b2-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b0b2-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="4b0b2-145">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="4b0b2-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="4b0b2-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4b0b2-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="4b0b2-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="4b0b2-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="4b0b2-148">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="4b0b2-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
