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
ms.openlocfilehash: f30a0abb3e4252737e513b531b8d5f49a0d47f0b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458443"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="1f65f-102">ScrollBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="1f65f-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="1f65f-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="1f65f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="1f65f-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="1f65f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1f65f-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="1f65f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="1f65f-106">Části ScrollBar</span><span class="sxs-lookup"><span data-stu-id="1f65f-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="1f65f-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="1f65f-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="1f65f-108">Částí</span><span class="sxs-lookup"><span data-stu-id="1f65f-108">Part</span></span>|<span data-ttu-id="1f65f-109">Typ</span><span class="sxs-lookup"><span data-stu-id="1f65f-109">Type</span></span>|<span data-ttu-id="1f65f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="1f65f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1f65f-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="1f65f-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="1f65f-112">Kontejner elementu, který určuje pozici <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="1f65f-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="1f65f-113">Stavy posuvníku</span><span class="sxs-lookup"><span data-stu-id="1f65f-113">ScrollBar States</span></span>  
 <span data-ttu-id="1f65f-114">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="1f65f-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="1f65f-115">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="1f65f-115">VisualState Name</span></span>|<span data-ttu-id="1f65f-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="1f65f-116">VisualStateGroup Name</span></span>|<span data-ttu-id="1f65f-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1f65f-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="1f65f-118">Běžnou</span><span class="sxs-lookup"><span data-stu-id="1f65f-118">Normal</span></span>|<span data-ttu-id="1f65f-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1f65f-119">CommonStates</span></span>|<span data-ttu-id="1f65f-120">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="1f65f-120">The default state.</span></span>|  
|<span data-ttu-id="1f65f-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="1f65f-121">MouseOver</span></span>|<span data-ttu-id="1f65f-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1f65f-122">CommonStates</span></span>|<span data-ttu-id="1f65f-123">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="1f65f-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="1f65f-124">Zabezpečen</span><span class="sxs-lookup"><span data-stu-id="1f65f-124">Disabled</span></span>|<span data-ttu-id="1f65f-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1f65f-125">CommonStates</span></span>|<span data-ttu-id="1f65f-126">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="1f65f-126">The control is disabled.</span></span>|  
|<span data-ttu-id="1f65f-127">Platné</span><span class="sxs-lookup"><span data-stu-id="1f65f-127">Valid</span></span>|<span data-ttu-id="1f65f-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1f65f-128">ValidationStates</span></span>|<span data-ttu-id="1f65f-129">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="1f65f-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1f65f-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1f65f-130">InvalidFocused</span></span>|<span data-ttu-id="1f65f-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1f65f-131">ValidationStates</span></span>|<span data-ttu-id="1f65f-132">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` a ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="1f65f-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="1f65f-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1f65f-133">InvalidUnfocused</span></span>|<span data-ttu-id="1f65f-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1f65f-134">ValidationStates</span></span>|<span data-ttu-id="1f65f-135">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` a ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="1f65f-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="1f65f-136">Příklad ControlTemplate ScrollBar</span><span class="sxs-lookup"><span data-stu-id="1f65f-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="1f65f-137">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="1f65f-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="1f65f-138">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="1f65f-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="1f65f-139">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="1f65f-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f65f-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f65f-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="1f65f-141">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="1f65f-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="1f65f-142">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="1f65f-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="1f65f-143">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="1f65f-143">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="1f65f-144">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="1f65f-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
