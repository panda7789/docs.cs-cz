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
ms.openlocfilehash: 0835c106ffbda86bca8e01bc61adebfc1ab0c2cb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459638"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="e74d0-102">GroupBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e74d0-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="e74d0-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="e74d0-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="e74d0-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="e74d0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e74d0-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e74d0-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="e74d0-106">Části Skupinový rámeček</span><span class="sxs-lookup"><span data-stu-id="e74d0-106">GroupBox Parts</span></span>  
 <span data-ttu-id="e74d0-107">Ovládací prvek <xref:System.Windows.Controls.GroupBox> neobsahuje žádné pojmenované části.</span><span class="sxs-lookup"><span data-stu-id="e74d0-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="e74d0-108">Stavy rámečku</span><span class="sxs-lookup"><span data-stu-id="e74d0-108">GroupBox States</span></span>  
 <span data-ttu-id="e74d0-109">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="e74d0-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="e74d0-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="e74d0-110">VisualState Name</span></span>|<span data-ttu-id="e74d0-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="e74d0-111">VisualStateGroup Name</span></span>|<span data-ttu-id="e74d0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e74d0-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e74d0-113">Platné</span><span class="sxs-lookup"><span data-stu-id="e74d0-113">Valid</span></span>|<span data-ttu-id="e74d0-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e74d0-114">ValidationStates</span></span>|<span data-ttu-id="e74d0-115">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="e74d0-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e74d0-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e74d0-116">InvalidFocused</span></span>|<span data-ttu-id="e74d0-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e74d0-117">ValidationStates</span></span>|<span data-ttu-id="e74d0-118">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="e74d0-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e74d0-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e74d0-119">InvalidUnfocused</span></span>|<span data-ttu-id="e74d0-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e74d0-120">ValidationStates</span></span>|<span data-ttu-id="e74d0-121">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="e74d0-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="e74d0-122">Skupinový ControlTemplate – příklad</span><span class="sxs-lookup"><span data-stu-id="e74d0-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="e74d0-123">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="e74d0-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="e74d0-124"><xref:System.Windows.Controls.ControlTemplate> používá jeden nebo více následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="e74d0-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e74d0-125">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="e74d0-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e74d0-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e74d0-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e74d0-127">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e74d0-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="e74d0-128">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e74d0-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="e74d0-129">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e74d0-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="e74d0-130">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e74d0-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
