---
title: StatusBar – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
ms.openlocfilehash: b1dd575d58571b845fc849ca432ad440d1ce3ec4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458270"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="d0a25-102">StatusBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d0a25-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="d0a25-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="d0a25-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="d0a25-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="d0a25-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d0a25-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d0a25-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="d0a25-106">Části stavový řádek</span><span class="sxs-lookup"><span data-stu-id="d0a25-106">StatusBar Parts</span></span>  
 <span data-ttu-id="d0a25-107">Ovládací prvek <xref:System.Windows.Controls.Primitives.StatusBar> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="d0a25-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="d0a25-108">Stavový řádek</span><span class="sxs-lookup"><span data-stu-id="d0a25-108">StatusBar States</span></span>  
 <span data-ttu-id="d0a25-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="d0a25-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="d0a25-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="d0a25-110">VisualState Name</span></span>|<span data-ttu-id="d0a25-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d0a25-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d0a25-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d0a25-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d0a25-113">Platné</span><span class="sxs-lookup"><span data-stu-id="d0a25-113">Valid</span></span>|<span data-ttu-id="d0a25-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d0a25-114">ValidationStates</span></span>|<span data-ttu-id="d0a25-115">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="d0a25-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d0a25-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d0a25-116">InvalidFocused</span></span>|<span data-ttu-id="d0a25-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d0a25-117">ValidationStates</span></span>|<span data-ttu-id="d0a25-118">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="d0a25-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d0a25-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d0a25-119">InvalidUnfocused</span></span>|<span data-ttu-id="d0a25-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d0a25-120">ValidationStates</span></span>|<span data-ttu-id="d0a25-121">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="d0a25-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="d0a25-122">StatusBarItem části</span><span class="sxs-lookup"><span data-stu-id="d0a25-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="d0a25-123">Ovládací prvek <xref:System.Windows.Controls.Primitives.StatusBarItem> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="d0a25-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="d0a25-124">Stavový řádek</span><span class="sxs-lookup"><span data-stu-id="d0a25-124">StatusBar States</span></span>  
 <span data-ttu-id="d0a25-125">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Primitives.StatusBarItem>.</span><span class="sxs-lookup"><span data-stu-id="d0a25-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="d0a25-126">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="d0a25-126">VisualState Name</span></span>|<span data-ttu-id="d0a25-127">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d0a25-127">VisualStateGroup Name</span></span>|<span data-ttu-id="d0a25-128">Popis</span><span class="sxs-lookup"><span data-stu-id="d0a25-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d0a25-129">Platné</span><span class="sxs-lookup"><span data-stu-id="d0a25-129">Valid</span></span>|<span data-ttu-id="d0a25-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d0a25-130">ValidationStates</span></span>|<span data-ttu-id="d0a25-131">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="d0a25-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d0a25-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d0a25-132">InvalidFocused</span></span>|<span data-ttu-id="d0a25-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d0a25-133">ValidationStates</span></span>|<span data-ttu-id="d0a25-134">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="d0a25-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d0a25-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d0a25-135">InvalidUnfocused</span></span>|<span data-ttu-id="d0a25-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d0a25-136">ValidationStates</span></span>|<span data-ttu-id="d0a25-137">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="d0a25-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="d0a25-138">Příklad ControlTemplate se stavem</span><span class="sxs-lookup"><span data-stu-id="d0a25-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="d0a25-139">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="d0a25-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="d0a25-140"><xref:System.Windows.Controls.ControlTemplate> používá jeden nebo více následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="d0a25-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d0a25-141">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="d0a25-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a25-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0a25-142">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d0a25-143">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="d0a25-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d0a25-144">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d0a25-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d0a25-145">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d0a25-145">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="d0a25-146">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d0a25-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
