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
ms.openlocfilehash: 35fcd9c15bf44d15a08c16d58847698c5ec6e574
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283509"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="797e6-102">Styly a šablony popisků</span><span class="sxs-lookup"><span data-stu-id="797e6-102">Label Styles and Templates</span></span>
<span data-ttu-id="797e6-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="797e6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="797e6-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="797e6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="797e6-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="797e6-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="797e6-106">Části popisku</span><span class="sxs-lookup"><span data-stu-id="797e6-106">Label Parts</span></span>  
 <span data-ttu-id="797e6-107">Ovládací prvek <xref:System.Windows.Controls.Label> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="797e6-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="797e6-108">Stavy štítků</span><span class="sxs-lookup"><span data-stu-id="797e6-108">Label States</span></span>  
 <span data-ttu-id="797e6-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="797e6-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="797e6-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="797e6-110">VisualState Name</span></span>|<span data-ttu-id="797e6-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="797e6-111">VisualStateGroup Name</span></span>|<span data-ttu-id="797e6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="797e6-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="797e6-113">Platné</span><span class="sxs-lookup"><span data-stu-id="797e6-113">Valid</span></span>|<span data-ttu-id="797e6-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="797e6-114">ValidationStates</span></span>|<span data-ttu-id="797e6-115">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="797e6-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="797e6-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="797e6-116">InvalidFocused</span></span>|<span data-ttu-id="797e6-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="797e6-117">ValidationStates</span></span>|<span data-ttu-id="797e6-118">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="797e6-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="797e6-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="797e6-119">InvalidUnfocused</span></span>|<span data-ttu-id="797e6-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="797e6-120">ValidationStates</span></span>|<span data-ttu-id="797e6-121">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="797e6-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="797e6-122">Příklad ControlTemplate popisku</span><span class="sxs-lookup"><span data-stu-id="797e6-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="797e6-123">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="797e6-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="797e6-124"><xref:System.Windows.Controls.ControlTemplate> používá jeden nebo více následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="797e6-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="797e6-125">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="797e6-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="797e6-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="797e6-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="797e6-127">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="797e6-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="797e6-128">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="797e6-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="797e6-129">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="797e6-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="797e6-130">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="797e6-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
