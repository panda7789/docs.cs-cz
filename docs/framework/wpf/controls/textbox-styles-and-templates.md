---
title: "TextBox – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d4fdb652876f2df049b71c18b0b79b7b435da8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="08fc2-102">TextBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="08fc2-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="08fc2-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08fc2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="08fc2-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08fc2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="08fc2-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="08fc2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="08fc2-106">Části textového pole</span><span class="sxs-lookup"><span data-stu-id="08fc2-106">TextBox Parts</span></span>  
 <span data-ttu-id="08fc2-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08fc2-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="08fc2-108">Část</span><span class="sxs-lookup"><span data-stu-id="08fc2-108">Part</span></span>|<span data-ttu-id="08fc2-109">Typ</span><span class="sxs-lookup"><span data-stu-id="08fc2-109">Type</span></span>|<span data-ttu-id="08fc2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="08fc2-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="08fc2-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="08fc2-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="08fc2-112">Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="08fc2-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="08fc2-113">Text <xref:System.Windows.Controls.TextBox> se zobrazí v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="08fc2-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="08fc2-114">Stavy TextBox</span><span class="sxs-lookup"><span data-stu-id="08fc2-114">TextBox States</span></span>  
 <span data-ttu-id="08fc2-115">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08fc2-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="08fc2-116">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="08fc2-116">VisualState Name</span></span>|<span data-ttu-id="08fc2-117">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="08fc2-117">VisualStateGroup Name</span></span>|<span data-ttu-id="08fc2-118">Popis</span><span class="sxs-lookup"><span data-stu-id="08fc2-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="08fc2-119">Normální</span><span class="sxs-lookup"><span data-stu-id="08fc2-119">Normal</span></span>|<span data-ttu-id="08fc2-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="08fc2-120">CommonStates</span></span>|<span data-ttu-id="08fc2-121">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="08fc2-121">The default state.</span></span>|  
|<span data-ttu-id="08fc2-122">Myš nad</span><span class="sxs-lookup"><span data-stu-id="08fc2-122">MouseOver</span></span>|<span data-ttu-id="08fc2-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="08fc2-123">CommonStates</span></span>|<span data-ttu-id="08fc2-124">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08fc2-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="08fc2-125">zakázáno</span><span class="sxs-lookup"><span data-stu-id="08fc2-125">Disabled</span></span>|<span data-ttu-id="08fc2-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="08fc2-126">CommonStates</span></span>|<span data-ttu-id="08fc2-127">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="08fc2-127">The control is disabled.</span></span>|  
|<span data-ttu-id="08fc2-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="08fc2-128">ReadOnly</span></span>|<span data-ttu-id="08fc2-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="08fc2-129">CommonStates</span></span>|<span data-ttu-id="08fc2-130">Uživatel nemůže změnit text v <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="08fc2-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="08fc2-131">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="08fc2-131">Focused</span></span>|<span data-ttu-id="08fc2-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="08fc2-132">FocusStates</span></span>|<span data-ttu-id="08fc2-133">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="08fc2-133">The control has focus.</span></span>|  
|<span data-ttu-id="08fc2-134">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="08fc2-134">Unfocused</span></span>|<span data-ttu-id="08fc2-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="08fc2-135">FocusStates</span></span>|<span data-ttu-id="08fc2-136">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="08fc2-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="08fc2-137">Platné</span><span class="sxs-lookup"><span data-stu-id="08fc2-137">Valid</span></span>|<span data-ttu-id="08fc2-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08fc2-138">ValidationStates</span></span>|<span data-ttu-id="08fc2-139">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="08fc2-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="08fc2-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="08fc2-140">InvalidFocused</span></span>|<span data-ttu-id="08fc2-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08fc2-141">ValidationStates</span></span>|<span data-ttu-id="08fc2-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="08fc2-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="08fc2-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="08fc2-143">InvalidUnfocused</span></span>|<span data-ttu-id="08fc2-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08fc2-144">ValidationStates</span></span>|<span data-ttu-id="08fc2-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="08fc2-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="08fc2-146">Element ControlTemplate příklad textového pole</span><span class="sxs-lookup"><span data-stu-id="08fc2-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="08fc2-147">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08fc2-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="08fc2-148">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="08fc2-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="08fc2-149">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="08fc2-149">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08fc2-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="08fc2-150">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="08fc2-151">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="08fc2-151">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="08fc2-152">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="08fc2-152">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="08fc2-153">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="08fc2-153">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="08fc2-154">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="08fc2-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
