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
ms.openlocfilehash: 9d2f5e4d886d8fc46ecb14dd4f1bda67debdae97
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457641"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="bd18a-102">Styly a šablony popisků</span><span class="sxs-lookup"><span data-stu-id="bd18a-102">Label Styles and Templates</span></span>
<span data-ttu-id="bd18a-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Label> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bd18a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="bd18a-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bd18a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="bd18a-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="bd18a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="bd18a-106">Popisek částí</span><span class="sxs-lookup"><span data-stu-id="bd18a-106">Label Parts</span></span>  
 <span data-ttu-id="bd18a-107"><xref:System.Windows.Controls.Label> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="bd18a-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="bd18a-108">Popisek stavy</span><span class="sxs-lookup"><span data-stu-id="bd18a-108">Label States</span></span>  
 <span data-ttu-id="bd18a-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Label> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bd18a-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="bd18a-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="bd18a-110">VisualState Name</span></span>|<span data-ttu-id="bd18a-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="bd18a-111">VisualStateGroup Name</span></span>|<span data-ttu-id="bd18a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bd18a-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="bd18a-113">Platné</span><span class="sxs-lookup"><span data-stu-id="bd18a-113">Valid</span></span>|<span data-ttu-id="bd18a-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bd18a-114">ValidationStates</span></span>|<span data-ttu-id="bd18a-115">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="bd18a-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="bd18a-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="bd18a-116">InvalidFocused</span></span>|<span data-ttu-id="bd18a-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bd18a-117">ValidationStates</span></span>|<span data-ttu-id="bd18a-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="bd18a-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="bd18a-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="bd18a-119">InvalidUnfocused</span></span>|<span data-ttu-id="bd18a-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bd18a-120">ValidationStates</span></span>|<span data-ttu-id="bd18a-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="bd18a-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="bd18a-122">Příklad ControlTemplate popisek</span><span class="sxs-lookup"><span data-stu-id="bd18a-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="bd18a-123">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Label> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bd18a-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="bd18a-124"><xref:System.Windows.Controls.ControlTemplate> Používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="bd18a-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="bd18a-125">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="bd18a-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd18a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd18a-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="bd18a-127">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="bd18a-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="bd18a-128">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="bd18a-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="bd18a-129">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="bd18a-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="bd18a-130">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="bd18a-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
