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
ms.openlocfilehash: ebd21829591b8fefe87aeba0b86280f18eff4f06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62023829"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="1edf5-102">Styly a šablony oken</span><span class="sxs-lookup"><span data-stu-id="1edf5-102">Window Styles and Templates</span></span>
<span data-ttu-id="1edf5-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Window> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1edf5-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="1edf5-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1edf5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1edf5-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="1edf5-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="1edf5-106">Součásti okna</span><span class="sxs-lookup"><span data-stu-id="1edf5-106">Window Parts</span></span>  
 <span data-ttu-id="1edf5-107"><xref:System.Windows.Window> Ovládací prvek nemá žádné pojmenované součásti.</span><span class="sxs-lookup"><span data-stu-id="1edf5-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="1edf5-108">Okno stavy</span><span class="sxs-lookup"><span data-stu-id="1edf5-108">Window States</span></span>  
 <span data-ttu-id="1edf5-109">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Window> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1edf5-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="1edf5-110">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="1edf5-110">VisualState Name</span></span>|<span data-ttu-id="1edf5-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="1edf5-111">VisualStateGroup Name</span></span>|<span data-ttu-id="1edf5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1edf5-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1edf5-113">Platné</span><span class="sxs-lookup"><span data-stu-id="1edf5-113">Valid</span></span>|<span data-ttu-id="1edf5-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1edf5-114">ValidationStates</span></span>|<span data-ttu-id="1edf5-115">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="1edf5-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1edf5-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1edf5-116">InvalidFocused</span></span>|<span data-ttu-id="1edf5-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1edf5-117">ValidationStates</span></span>|<span data-ttu-id="1edf5-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="1edf5-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="1edf5-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1edf5-119">InvalidUnfocused</span></span>|<span data-ttu-id="1edf5-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1edf5-120">ValidationStates</span></span>|<span data-ttu-id="1edf5-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="1edf5-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="1edf5-122">Příklad okna ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="1edf5-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="1edf5-123">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Window> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1edf5-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="1edf5-124"><xref:System.Windows.Controls.ControlTemplate> Používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="1edf5-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="1edf5-125">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="1edf5-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1edf5-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1edf5-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="1edf5-127">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="1edf5-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="1edf5-128">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="1edf5-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="1edf5-129">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="1edf5-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="1edf5-130">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="1edf5-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
