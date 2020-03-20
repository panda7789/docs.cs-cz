---
title: GroupBox – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187482"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="ee878-102">GroupBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="ee878-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="ee878-103">Toto téma popisuje styly a <xref:System.Windows.Controls.GroupBox> šablony ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ee878-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="ee878-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> prvek, aby ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="ee878-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ee878-105">Další informace naleznete [v tématu Vytvoření šablony ovládacího prvku](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="ee878-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a><span data-ttu-id="ee878-106">Součásti GroupBox</span><span class="sxs-lookup"><span data-stu-id="ee878-106">GroupBox Parts</span></span>  
 <span data-ttu-id="ee878-107">Ovládací <xref:System.Windows.Controls.GroupBox> prvek nemá žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="ee878-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a><span data-ttu-id="ee878-108">Stavy GroupBox</span><span class="sxs-lookup"><span data-stu-id="ee878-108">GroupBox States</span></span>  
 <span data-ttu-id="ee878-109">V následující tabulce jsou uvedeny stavy vizuálu ovládacího <xref:System.Windows.Controls.GroupBox> prvku.</span><span class="sxs-lookup"><span data-stu-id="ee878-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="ee878-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="ee878-110">VisualState Name</span></span>|<span data-ttu-id="ee878-111">Název visualstategroup</span><span class="sxs-lookup"><span data-stu-id="ee878-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ee878-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ee878-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ee878-113">Platné</span><span class="sxs-lookup"><span data-stu-id="ee878-113">Valid</span></span>|<span data-ttu-id="ee878-114">Stavy ověření</span><span class="sxs-lookup"><span data-stu-id="ee878-114">ValidationStates</span></span>|<span data-ttu-id="ee878-115">Ovládací prvek <xref:System.Windows.Controls.Validation> používá třídu a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> `false`připojené vlastnosti je .</span><span class="sxs-lookup"><span data-stu-id="ee878-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ee878-116">Neplatnéfocené</span><span class="sxs-lookup"><span data-stu-id="ee878-116">InvalidFocused</span></span>|<span data-ttu-id="ee878-117">Stavy ověření</span><span class="sxs-lookup"><span data-stu-id="ee878-117">ValidationStates</span></span>|<span data-ttu-id="ee878-118">Připojená <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="ee878-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ee878-119">Neplatnýnezaostřený</span><span class="sxs-lookup"><span data-stu-id="ee878-119">InvalidUnfocused</span></span>|<span data-ttu-id="ee878-120">Stavy ověření</span><span class="sxs-lookup"><span data-stu-id="ee878-120">ValidationStates</span></span>|<span data-ttu-id="ee878-121">Připojená <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="ee878-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="ee878-122">Příklad šablony ovládacího prvku GroupBox</span><span class="sxs-lookup"><span data-stu-id="ee878-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="ee878-123">Následující příklad ukazuje, jak <xref:System.Windows.Controls.ControlTemplate> definovat <xref:System.Windows.Controls.GroupBox> pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ee878-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="ee878-124">Používá <xref:System.Windows.Controls.ControlTemplate> jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="ee878-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ee878-125">Kompletní ukázku naleznete [v tématu Styling s ukázkou řídicích šablon](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="ee878-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee878-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee878-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ee878-127">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="ee878-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ee878-128">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ee878-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ee878-129">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="ee878-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ee878-130">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="ee878-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
