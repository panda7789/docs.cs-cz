---
title: Styly a šablony oken
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Window
- templates [WPF], Window
- styles [WPF], Window
- ControlTemplate [WPF], Window
- Window [WPF], styles and templates
- states [WPF], Window
ms.assetid: 2dfdf025-347b-4342-bf28-95206c273f35
ms.openlocfilehash: 01233c5d0179e1a6f9bed651cd1f18058bfac168
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283602"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="70349-102">Styly a šablony oken</span><span class="sxs-lookup"><span data-stu-id="70349-102">Window Styles and Templates</span></span>
<span data-ttu-id="70349-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="70349-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="70349-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="70349-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="70349-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="70349-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="70349-106">Části okna</span><span class="sxs-lookup"><span data-stu-id="70349-106">Window Parts</span></span>  
 <span data-ttu-id="70349-107">Ovládací prvek <xref:System.Windows.Window> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="70349-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="70349-108">Stavy oken</span><span class="sxs-lookup"><span data-stu-id="70349-108">Window States</span></span>  
 <span data-ttu-id="70349-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="70349-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="70349-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="70349-110">VisualState Name</span></span>|<span data-ttu-id="70349-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="70349-111">VisualStateGroup Name</span></span>|<span data-ttu-id="70349-112">Popis</span><span class="sxs-lookup"><span data-stu-id="70349-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="70349-113">Platné</span><span class="sxs-lookup"><span data-stu-id="70349-113">Valid</span></span>|<span data-ttu-id="70349-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="70349-114">ValidationStates</span></span>|<span data-ttu-id="70349-115">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="70349-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="70349-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="70349-116">InvalidFocused</span></span>|<span data-ttu-id="70349-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="70349-117">ValidationStates</span></span>|<span data-ttu-id="70349-118">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="70349-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="70349-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="70349-119">InvalidUnfocused</span></span>|<span data-ttu-id="70349-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="70349-120">ValidationStates</span></span>|<span data-ttu-id="70349-121">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="70349-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="70349-122">Příklad okna ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="70349-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="70349-123">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="70349-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="70349-124"><xref:System.Windows.Controls.ControlTemplate> používá jeden nebo více následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="70349-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="70349-125">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="70349-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70349-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70349-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="70349-127">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="70349-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="70349-128">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="70349-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="70349-129">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="70349-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="70349-130">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="70349-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
