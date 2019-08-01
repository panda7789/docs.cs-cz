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
ms.openlocfilehash: 016556fb825ddf60af7dc572d6fda7323b9bb09d
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671972"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="e934a-102">ScrollBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e934a-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="e934a-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.ScrollBar> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e934a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="e934a-104">Můžete změnit výchozí nastavení <xref:System.Windows.Controls.ControlTemplate> a dát ovládacímu prvku jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="e934a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e934a-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e934a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="e934a-106">Části ScrollBar</span><span class="sxs-lookup"><span data-stu-id="e934a-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="e934a-107">V následující tabulce jsou uvedeny pojmenované části <xref:System.Windows.Controls.Primitives.ScrollBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e934a-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="e934a-108">Částí</span><span class="sxs-lookup"><span data-stu-id="e934a-108">Part</span></span>|<span data-ttu-id="e934a-109">type</span><span class="sxs-lookup"><span data-stu-id="e934a-109">Type</span></span>|<span data-ttu-id="e934a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e934a-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e934a-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="e934a-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="e934a-112">Kontejner elementu, který označuje pozici <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="e934a-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="e934a-113">Stavy posuvníku</span><span class="sxs-lookup"><span data-stu-id="e934a-113">ScrollBar States</span></span>  
 <span data-ttu-id="e934a-114">V následující tabulce jsou uvedeny vizuální stavy <xref:System.Windows.Controls.Primitives.ScrollBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e934a-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="e934a-115">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="e934a-115">VisualState Name</span></span>|<span data-ttu-id="e934a-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="e934a-116">VisualStateGroup Name</span></span>|<span data-ttu-id="e934a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e934a-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="e934a-118">Normální</span><span class="sxs-lookup"><span data-stu-id="e934a-118">Normal</span></span>|<span data-ttu-id="e934a-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e934a-119">CommonStates</span></span>|<span data-ttu-id="e934a-120">Výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="e934a-120">The default state.</span></span>|  
|<span data-ttu-id="e934a-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="e934a-121">MouseOver</span></span>|<span data-ttu-id="e934a-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e934a-122">CommonStates</span></span>|<span data-ttu-id="e934a-123">Ukazatel myši je umístěn nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="e934a-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="e934a-124">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="e934a-124">Disabled</span></span>|<span data-ttu-id="e934a-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e934a-125">CommonStates</span></span>|<span data-ttu-id="e934a-126">Ovládací prvek je zakázán.</span><span class="sxs-lookup"><span data-stu-id="e934a-126">The control is disabled.</span></span>|  
|<span data-ttu-id="e934a-127">Platné</span><span class="sxs-lookup"><span data-stu-id="e934a-127">Valid</span></span>|<span data-ttu-id="e934a-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e934a-128">ValidationStates</span></span>|<span data-ttu-id="e934a-129">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídu <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> a připojenou vlastnost je `false`.</span><span class="sxs-lookup"><span data-stu-id="e934a-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e934a-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e934a-130">InvalidFocused</span></span>|<span data-ttu-id="e934a-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e934a-131">ValidationStates</span></span>|<span data-ttu-id="e934a-132">Připojená vlastnost je `true` a ovládací prvek má fokus. <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e934a-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="e934a-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e934a-133">InvalidUnfocused</span></span>|<span data-ttu-id="e934a-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e934a-134">ValidationStates</span></span>|<span data-ttu-id="e934a-135">Připojená vlastnost je `true` a ovládací prvek nemá fokus. <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e934a-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="e934a-136">Příklad ControlTemplate ScrollBar</span><span class="sxs-lookup"><span data-stu-id="e934a-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="e934a-137">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Primitives.ScrollBar> pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e934a-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="e934a-138">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="e934a-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e934a-139">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="e934a-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e934a-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e934a-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e934a-141">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e934a-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="e934a-142">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e934a-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="e934a-143">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e934a-143">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="e934a-144">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e934a-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
