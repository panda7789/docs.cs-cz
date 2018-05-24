---
title: PasswordBox – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: ebc496b1b2558d8b2e310e6977ee27a82a4a8896
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="passwordbox-syles-and-templates"></a><span data-ttu-id="5c8aa-102">PasswordBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="5c8aa-102">PasswordBox Syles and Templates</span></span>
<span data-ttu-id="5c8aa-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.PasswordBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="5c8aa-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5c8aa-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="5c8aa-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="passwordbox-parts"></a><span data-ttu-id="5c8aa-106">Položka PasswordBox částí</span><span class="sxs-lookup"><span data-stu-id="5c8aa-106">PasswordBox Parts</span></span>  
 <span data-ttu-id="5c8aa-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.PasswordBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="5c8aa-108">Část</span><span class="sxs-lookup"><span data-stu-id="5c8aa-108">Part</span></span>|<span data-ttu-id="5c8aa-109">Typ</span><span class="sxs-lookup"><span data-stu-id="5c8aa-109">Type</span></span>|<span data-ttu-id="5c8aa-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5c8aa-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5c8aa-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="5c8aa-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="5c8aa-112">Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="5c8aa-113">Text <xref:System.Windows.Controls.PasswordBox> se zobrazí v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|  
  
## <a name="passwordbox-states"></a><span data-ttu-id="5c8aa-114">Položka PasswordBox stavy</span><span class="sxs-lookup"><span data-stu-id="5c8aa-114">PasswordBox States</span></span>  
 <span data-ttu-id="5c8aa-115">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.PasswordBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="5c8aa-116">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="5c8aa-116">VisualState Name</span></span>|<span data-ttu-id="5c8aa-117">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="5c8aa-117">VisualStateGroup Name</span></span>|<span data-ttu-id="5c8aa-118">Popis</span><span class="sxs-lookup"><span data-stu-id="5c8aa-118">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5c8aa-119">Normální</span><span class="sxs-lookup"><span data-stu-id="5c8aa-119">Normal</span></span>|<span data-ttu-id="5c8aa-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5c8aa-120">CommonStates</span></span>|<span data-ttu-id="5c8aa-121">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-121">The default state.</span></span>|  
|<span data-ttu-id="5c8aa-122">Myš nad</span><span class="sxs-lookup"><span data-stu-id="5c8aa-122">MouseOver</span></span>|<span data-ttu-id="5c8aa-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5c8aa-123">CommonStates</span></span>|<span data-ttu-id="5c8aa-124">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="5c8aa-125">zakázáno</span><span class="sxs-lookup"><span data-stu-id="5c8aa-125">Disabled</span></span>|<span data-ttu-id="5c8aa-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5c8aa-126">CommonStates</span></span>|<span data-ttu-id="5c8aa-127">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-127">The control is disabled.</span></span>|  
|<span data-ttu-id="5c8aa-128">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="5c8aa-128">Focused</span></span>|<span data-ttu-id="5c8aa-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5c8aa-129">FocusStates</span></span>|<span data-ttu-id="5c8aa-130">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-130">The control has focus.</span></span>|  
|<span data-ttu-id="5c8aa-131">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="5c8aa-131">Unfocused</span></span>|<span data-ttu-id="5c8aa-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5c8aa-132">FocusStates</span></span>|<span data-ttu-id="5c8aa-133">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-133">The control does not have focus.</span></span>|  
|<span data-ttu-id="5c8aa-134">Platné</span><span class="sxs-lookup"><span data-stu-id="5c8aa-134">Valid</span></span>|<span data-ttu-id="5c8aa-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5c8aa-135">ValidationStates</span></span>|<span data-ttu-id="5c8aa-136">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5c8aa-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5c8aa-137">InvalidFocused</span></span>|<span data-ttu-id="5c8aa-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5c8aa-138">ValidationStates</span></span>|<span data-ttu-id="5c8aa-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5c8aa-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5c8aa-140">InvalidUnfocused</span></span>|<span data-ttu-id="5c8aa-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5c8aa-141">ValidationStates</span></span>|<span data-ttu-id="5c8aa-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="5c8aa-143">Položka PasswordBox ControlTemplate příklad</span><span class="sxs-lookup"><span data-stu-id="5c8aa-143">PasswordBox ControlTemplate Example</span></span>  
 <span data-ttu-id="5c8aa-144">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.PasswordBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#PasswordBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]  
  
 <span data-ttu-id="5c8aa-145">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="5c8aa-145">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5c8aa-146">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="5c8aa-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8aa-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c8aa-147">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="5c8aa-148">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="5c8aa-148">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="5c8aa-149">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="5c8aa-149">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="5c8aa-150">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="5c8aa-150">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="5c8aa-151">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="5c8aa-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
