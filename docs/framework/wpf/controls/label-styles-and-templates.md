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
ms.openlocfilehash: d2bb348fc9c0348fd8093452e022df7ab4e0b3f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137082"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="cc508-102">Styly a šablony popisků</span><span class="sxs-lookup"><span data-stu-id="cc508-102">Label Styles and Templates</span></span>
<span data-ttu-id="cc508-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Label> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cc508-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="cc508-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cc508-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="cc508-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="cc508-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="cc508-106">Popisek části</span><span class="sxs-lookup"><span data-stu-id="cc508-106">Label Parts</span></span>  
 <span data-ttu-id="cc508-107"><xref:System.Windows.Controls.Label> Ovládací prvek nemá žádné pojmenované součásti.</span><span class="sxs-lookup"><span data-stu-id="cc508-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="cc508-108">Popisek stavy</span><span class="sxs-lookup"><span data-stu-id="cc508-108">Label States</span></span>  
 <span data-ttu-id="cc508-109">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Label> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cc508-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="cc508-110">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="cc508-110">VisualState Name</span></span>|<span data-ttu-id="cc508-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="cc508-111">VisualStateGroup Name</span></span>|<span data-ttu-id="cc508-112">Popis</span><span class="sxs-lookup"><span data-stu-id="cc508-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="cc508-113">Platné</span><span class="sxs-lookup"><span data-stu-id="cc508-113">Valid</span></span>|<span data-ttu-id="cc508-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cc508-114">ValidationStates</span></span>|<span data-ttu-id="cc508-115">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="cc508-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="cc508-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="cc508-116">InvalidFocused</span></span>|<span data-ttu-id="cc508-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cc508-117">ValidationStates</span></span>|<span data-ttu-id="cc508-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="cc508-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="cc508-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="cc508-119">InvalidUnfocused</span></span>|<span data-ttu-id="cc508-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cc508-120">ValidationStates</span></span>|<span data-ttu-id="cc508-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="cc508-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="cc508-122">Příklad popisku ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="cc508-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="cc508-123">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Label> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cc508-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="cc508-124"><xref:System.Windows.Controls.ControlTemplate> Používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="cc508-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="cc508-125">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="cc508-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc508-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc508-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="cc508-127">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="cc508-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="cc508-128">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="cc508-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="cc508-129">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="cc508-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="cc508-130">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="cc508-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
