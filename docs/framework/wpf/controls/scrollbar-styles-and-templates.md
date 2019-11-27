---
title: ScrollBar – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 7093a78555aefd73f9bb05c0a7b5fab6b66176fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283413"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="b4118-102">ScrollBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="b4118-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="b4118-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="b4118-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="b4118-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="b4118-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b4118-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="b4118-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="b4118-106">Části ScrollBar</span><span class="sxs-lookup"><span data-stu-id="b4118-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="b4118-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="b4118-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="b4118-108">Částí</span><span class="sxs-lookup"><span data-stu-id="b4118-108">Part</span></span>|<span data-ttu-id="b4118-109">Typ</span><span class="sxs-lookup"><span data-stu-id="b4118-109">Type</span></span>|<span data-ttu-id="b4118-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b4118-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b4118-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="b4118-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="b4118-112">Kontejner elementu, který určuje pozici <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="b4118-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="b4118-113">Stavy posuvníku</span><span class="sxs-lookup"><span data-stu-id="b4118-113">ScrollBar States</span></span>  
 <span data-ttu-id="b4118-114">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="b4118-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="b4118-115">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="b4118-115">VisualState Name</span></span>|<span data-ttu-id="b4118-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="b4118-116">VisualStateGroup Name</span></span>|<span data-ttu-id="b4118-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b4118-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="b4118-118">Normální</span><span class="sxs-lookup"><span data-stu-id="b4118-118">Normal</span></span>|<span data-ttu-id="b4118-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b4118-119">CommonStates</span></span>|<span data-ttu-id="b4118-120">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="b4118-120">The default state.</span></span>|  
|<span data-ttu-id="b4118-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="b4118-121">MouseOver</span></span>|<span data-ttu-id="b4118-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b4118-122">CommonStates</span></span>|<span data-ttu-id="b4118-123">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="b4118-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="b4118-124">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="b4118-124">Disabled</span></span>|<span data-ttu-id="b4118-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b4118-125">CommonStates</span></span>|<span data-ttu-id="b4118-126">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="b4118-126">The control is disabled.</span></span>|  
|<span data-ttu-id="b4118-127">Platný</span><span class="sxs-lookup"><span data-stu-id="b4118-127">Valid</span></span>|<span data-ttu-id="b4118-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b4118-128">ValidationStates</span></span>|<span data-ttu-id="b4118-129">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="b4118-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b4118-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b4118-130">InvalidFocused</span></span>|<span data-ttu-id="b4118-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b4118-131">ValidationStates</span></span>|<span data-ttu-id="b4118-132">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` a ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="b4118-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="b4118-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b4118-133">InvalidUnfocused</span></span>|<span data-ttu-id="b4118-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b4118-134">ValidationStates</span></span>|<span data-ttu-id="b4118-135">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` a ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="b4118-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="b4118-136">Příklad ControlTemplate ScrollBar</span><span class="sxs-lookup"><span data-stu-id="b4118-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="b4118-137">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="b4118-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="b4118-138">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="b4118-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b4118-139">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="b4118-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4118-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4118-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b4118-141">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="b4118-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="b4118-142">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="b4118-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="b4118-143">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="b4118-143">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="b4118-144">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b4118-144">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
