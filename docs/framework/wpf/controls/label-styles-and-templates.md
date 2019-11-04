---
title: Styly a šablony popisků
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
ms.openlocfilehash: c3bf4dc629bbb3e4ea21862c6893b001749f4649
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459400"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="6fd1c-102">Styly a šablony popisků</span><span class="sxs-lookup"><span data-stu-id="6fd1c-102">Label Styles and Templates</span></span>
<span data-ttu-id="6fd1c-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="6fd1c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="6fd1c-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="6fd1c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6fd1c-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6fd1c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="6fd1c-106">Části popisku</span><span class="sxs-lookup"><span data-stu-id="6fd1c-106">Label Parts</span></span>  
 <span data-ttu-id="6fd1c-107">Ovládací prvek <xref:System.Windows.Controls.Label> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="6fd1c-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="6fd1c-108">Stavy štítků</span><span class="sxs-lookup"><span data-stu-id="6fd1c-108">Label States</span></span>  
 <span data-ttu-id="6fd1c-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="6fd1c-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="6fd1c-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="6fd1c-110">VisualState Name</span></span>|<span data-ttu-id="6fd1c-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6fd1c-111">VisualStateGroup Name</span></span>|<span data-ttu-id="6fd1c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6fd1c-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6fd1c-113">Platné</span><span class="sxs-lookup"><span data-stu-id="6fd1c-113">Valid</span></span>|<span data-ttu-id="6fd1c-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6fd1c-114">ValidationStates</span></span>|<span data-ttu-id="6fd1c-115">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="6fd1c-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6fd1c-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6fd1c-116">InvalidFocused</span></span>|<span data-ttu-id="6fd1c-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6fd1c-117">ValidationStates</span></span>|<span data-ttu-id="6fd1c-118">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="6fd1c-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6fd1c-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6fd1c-119">InvalidUnfocused</span></span>|<span data-ttu-id="6fd1c-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6fd1c-120">ValidationStates</span></span>|<span data-ttu-id="6fd1c-121">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="6fd1c-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="6fd1c-122">Příklad ControlTemplate popisku</span><span class="sxs-lookup"><span data-stu-id="6fd1c-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="6fd1c-123">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="6fd1c-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="6fd1c-124"><xref:System.Windows.Controls.ControlTemplate> používá jeden nebo více následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="6fd1c-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6fd1c-125">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="6fd1c-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd1c-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fd1c-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="6fd1c-127">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="6fd1c-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="6fd1c-128">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6fd1c-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="6fd1c-129">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="6fd1c-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="6fd1c-130">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="6fd1c-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
