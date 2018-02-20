---
title: "Styly a šablony tlačítek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d783b3141463ca2c74ddd649848ea49e154415b6
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2018
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="3227c-102">Styly a šablony tlačítek</span><span class="sxs-lookup"><span data-stu-id="3227c-102">Button Styles and Templates</span></span>
<span data-ttu-id="3227c-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3227c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="3227c-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3227c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3227c-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="3227c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="3227c-106">Tlačítko částí</span><span class="sxs-lookup"><span data-stu-id="3227c-106">Button Parts</span></span>  
 <span data-ttu-id="3227c-107"><xref:System.Windows.Controls.Button> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="3227c-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="3227c-108">Tlačítko stavy</span><span class="sxs-lookup"><span data-stu-id="3227c-108">Button States</span></span>  
 <span data-ttu-id="3227c-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3227c-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="3227c-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="3227c-110">VisualState Name</span></span>|<span data-ttu-id="3227c-111">VisualStateGroup Name</span><span class="sxs-lookup"><span data-stu-id="3227c-111">VisualStateGroup Name</span></span>|<span data-ttu-id="3227c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3227c-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3227c-113">Normální</span><span class="sxs-lookup"><span data-stu-id="3227c-113">Normal</span></span>|<span data-ttu-id="3227c-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3227c-114">CommonStates</span></span>|<span data-ttu-id="3227c-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="3227c-115">The default state.</span></span>|  
|<span data-ttu-id="3227c-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="3227c-116">MouseOver</span></span>|<span data-ttu-id="3227c-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3227c-117">CommonStates</span></span>|<span data-ttu-id="3227c-118">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3227c-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="3227c-119">Stisknutí tlačítka</span><span class="sxs-lookup"><span data-stu-id="3227c-119">Pressed</span></span>|<span data-ttu-id="3227c-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3227c-120">CommonStates</span></span>|<span data-ttu-id="3227c-121">Stisknutí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3227c-121">The control is pressed.</span></span>|  
|<span data-ttu-id="3227c-122">zakázáno</span><span class="sxs-lookup"><span data-stu-id="3227c-122">Disabled</span></span>|<span data-ttu-id="3227c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3227c-123">CommonStates</span></span>|<span data-ttu-id="3227c-124">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="3227c-124">The control is disabled.</span></span>|  
|<span data-ttu-id="3227c-125">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="3227c-125">Focused</span></span>|<span data-ttu-id="3227c-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3227c-126">FocusStates</span></span>|<span data-ttu-id="3227c-127">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="3227c-127">The control has focus.</span></span>|  
|<span data-ttu-id="3227c-128">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="3227c-128">Unfocused</span></span>|<span data-ttu-id="3227c-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3227c-129">FocusStates</span></span>|<span data-ttu-id="3227c-130">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="3227c-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="3227c-131">Platné</span><span class="sxs-lookup"><span data-stu-id="3227c-131">Valid</span></span>|<span data-ttu-id="3227c-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3227c-132">ValidationStates</span></span>|<span data-ttu-id="3227c-133">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="3227c-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3227c-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3227c-134">InvalidFocused</span></span>|<span data-ttu-id="3227c-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3227c-135">ValidationStates</span></span>|<span data-ttu-id="3227c-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` a má právě fokus, ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3227c-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="3227c-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3227c-137">InvalidUnfocused</span></span>|<span data-ttu-id="3227c-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3227c-138">ValidationStates</span></span>|<span data-ttu-id="3227c-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` a ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="3227c-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="3227c-140">Příklad ControlTemplate tlačítko</span><span class="sxs-lookup"><span data-stu-id="3227c-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="3227c-141">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3227c-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="3227c-142">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="3227c-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3227c-143">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="3227c-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3227c-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="3227c-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="3227c-145">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="3227c-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="3227c-146">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="3227c-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="3227c-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="3227c-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="3227c-148">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="3227c-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
