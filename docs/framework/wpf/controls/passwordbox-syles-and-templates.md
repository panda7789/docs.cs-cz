---
title: "PasswordBox – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17a9292ef6aeba157780be5ec87d67725eb833a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="passwordbox-syles-and-templates"></a><span data-ttu-id="d70bc-102">PasswordBox – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d70bc-102">PasswordBox Syles and Templates</span></span>
<span data-ttu-id="d70bc-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.PasswordBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d70bc-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="d70bc-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d70bc-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d70bc-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d70bc-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="passwordbox-parts"></a><span data-ttu-id="d70bc-106">Položka PasswordBox částí</span><span class="sxs-lookup"><span data-stu-id="d70bc-106">PasswordBox Parts</span></span>  
 <span data-ttu-id="d70bc-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.PasswordBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d70bc-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="d70bc-108">Část</span><span class="sxs-lookup"><span data-stu-id="d70bc-108">Part</span></span>|<span data-ttu-id="d70bc-109">Typ</span><span class="sxs-lookup"><span data-stu-id="d70bc-109">Type</span></span>|<span data-ttu-id="d70bc-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d70bc-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d70bc-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="d70bc-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d70bc-112">Vizuální prvek, který může obsahovat <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="d70bc-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="d70bc-113">Text <xref:System.Windows.Controls.PasswordBox> se zobrazí v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="d70bc-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|  
  
## <a name="passwordbox-states"></a><span data-ttu-id="d70bc-114">Položka PasswordBox stavy</span><span class="sxs-lookup"><span data-stu-id="d70bc-114">PasswordBox States</span></span>  
 <span data-ttu-id="d70bc-115">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.PasswordBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d70bc-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="d70bc-116">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="d70bc-116">VisualState Name</span></span>|<span data-ttu-id="d70bc-117">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d70bc-117">VisualStateGroup Name</span></span>|<span data-ttu-id="d70bc-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d70bc-118">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d70bc-119">Normální</span><span class="sxs-lookup"><span data-stu-id="d70bc-119">Normal</span></span>|<span data-ttu-id="d70bc-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d70bc-120">CommonStates</span></span>|<span data-ttu-id="d70bc-121">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="d70bc-121">The default state.</span></span>|  
|<span data-ttu-id="d70bc-122">Myš nad</span><span class="sxs-lookup"><span data-stu-id="d70bc-122">MouseOver</span></span>|<span data-ttu-id="d70bc-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d70bc-123">CommonStates</span></span>|<span data-ttu-id="d70bc-124">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d70bc-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="d70bc-125">zakázáno</span><span class="sxs-lookup"><span data-stu-id="d70bc-125">Disabled</span></span>|<span data-ttu-id="d70bc-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d70bc-126">CommonStates</span></span>|<span data-ttu-id="d70bc-127">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="d70bc-127">The control is disabled.</span></span>|  
|<span data-ttu-id="d70bc-128">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="d70bc-128">Focused</span></span>|<span data-ttu-id="d70bc-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d70bc-129">FocusStates</span></span>|<span data-ttu-id="d70bc-130">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="d70bc-130">The control has focus.</span></span>|  
|<span data-ttu-id="d70bc-131">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="d70bc-131">Unfocused</span></span>|<span data-ttu-id="d70bc-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d70bc-132">FocusStates</span></span>|<span data-ttu-id="d70bc-133">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d70bc-133">The control does not have focus.</span></span>|  
|<span data-ttu-id="d70bc-134">Platné</span><span class="sxs-lookup"><span data-stu-id="d70bc-134">Valid</span></span>|<span data-ttu-id="d70bc-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d70bc-135">ValidationStates</span></span>|<span data-ttu-id="d70bc-136">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="d70bc-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d70bc-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d70bc-137">InvalidFocused</span></span>|<span data-ttu-id="d70bc-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d70bc-138">ValidationStates</span></span>|<span data-ttu-id="d70bc-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="d70bc-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d70bc-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d70bc-140">InvalidUnfocused</span></span>|<span data-ttu-id="d70bc-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d70bc-141">ValidationStates</span></span>|<span data-ttu-id="d70bc-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="d70bc-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="d70bc-143">Položka PasswordBox ControlTemplate příklad</span><span class="sxs-lookup"><span data-stu-id="d70bc-143">PasswordBox ControlTemplate Example</span></span>  
 <span data-ttu-id="d70bc-144">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.PasswordBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d70bc-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#PasswordBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]  
  
 <span data-ttu-id="d70bc-145">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="d70bc-145">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d70bc-146">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="d70bc-146">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d70bc-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="d70bc-147">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d70bc-148">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="d70bc-148">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d70bc-149">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d70bc-149">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d70bc-150">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="d70bc-150">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d70bc-151">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d70bc-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
