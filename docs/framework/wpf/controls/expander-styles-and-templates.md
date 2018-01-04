---
title: "Styly a šablony rozšíření"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 999b081d80680069d4c6fdf908814889afa60870
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="expander-styles-and-templates"></a><span data-ttu-id="21856-102">Styly a šablony rozšíření</span><span class="sxs-lookup"><span data-stu-id="21856-102">Expander Styles and Templates</span></span>
<span data-ttu-id="21856-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Expander> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21856-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Expander> control.</span></span> <span data-ttu-id="21856-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21856-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="21856-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="21856-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="expander-parts"></a><span data-ttu-id="21856-106">Expander částí</span><span class="sxs-lookup"><span data-stu-id="21856-106">Expander Parts</span></span>  
 <span data-ttu-id="21856-107"><xref:System.Windows.Controls.Expander> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="21856-107">The <xref:System.Windows.Controls.Expander> control does not have any named parts.</span></span>  
  
## <a name="expander-states"></a><span data-ttu-id="21856-108">Stavy Expander</span><span class="sxs-lookup"><span data-stu-id="21856-108">Expander States</span></span>  
 <span data-ttu-id="21856-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Expander> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21856-109">The following table lists the visual states for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
|<span data-ttu-id="21856-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="21856-110">VisualState Name</span></span>|<span data-ttu-id="21856-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="21856-111">VisualStateGroup Name</span></span>|<span data-ttu-id="21856-112">Popis</span><span class="sxs-lookup"><span data-stu-id="21856-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="21856-113">Normální</span><span class="sxs-lookup"><span data-stu-id="21856-113">Normal</span></span>|<span data-ttu-id="21856-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="21856-114">CommonStates</span></span>|<span data-ttu-id="21856-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="21856-115">The default state.</span></span>|  
|<span data-ttu-id="21856-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="21856-116">MouseOver</span></span>|<span data-ttu-id="21856-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="21856-117">CommonStates</span></span>|<span data-ttu-id="21856-118">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21856-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="21856-119">zakázáno</span><span class="sxs-lookup"><span data-stu-id="21856-119">Disabled</span></span>|<span data-ttu-id="21856-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="21856-120">CommonStates</span></span>|<span data-ttu-id="21856-121">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="21856-121">The control is disabled.</span></span>|  
|<span data-ttu-id="21856-122">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="21856-122">Focused</span></span>|<span data-ttu-id="21856-123">FocusStates</span><span class="sxs-lookup"><span data-stu-id="21856-123">FocusStates</span></span>|<span data-ttu-id="21856-124">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="21856-124">The control has focus.</span></span>|  
|<span data-ttu-id="21856-125">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="21856-125">Unfocused</span></span>|<span data-ttu-id="21856-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="21856-126">FocusStates</span></span>|<span data-ttu-id="21856-127">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="21856-127">The control does not have focus.</span></span>|  
|<span data-ttu-id="21856-128">Rozšířit</span><span class="sxs-lookup"><span data-stu-id="21856-128">Expanded</span></span>|<span data-ttu-id="21856-129">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="21856-129">ExpansionStates</span></span>|<span data-ttu-id="21856-130">Ovládací prvek je rozšířena.</span><span class="sxs-lookup"><span data-stu-id="21856-130">The control is expanded.</span></span>|  
|<span data-ttu-id="21856-131">Sbalené</span><span class="sxs-lookup"><span data-stu-id="21856-131">Collapsed</span></span>|<span data-ttu-id="21856-132">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="21856-132">ExpansionStates</span></span>|<span data-ttu-id="21856-133">Ovládací prvek není rozbalen.</span><span class="sxs-lookup"><span data-stu-id="21856-133">The control is not expanded.</span></span>|  
|<span data-ttu-id="21856-134">ExpandDown</span><span class="sxs-lookup"><span data-stu-id="21856-134">ExpandDown</span></span>|<span data-ttu-id="21856-135">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="21856-135">ExpandDirectionStates</span></span>|<span data-ttu-id="21856-136">Ovládací prvek rozšíří dolů.</span><span class="sxs-lookup"><span data-stu-id="21856-136">The control expands down.</span></span>|  
|<span data-ttu-id="21856-137">ExpandUp</span><span class="sxs-lookup"><span data-stu-id="21856-137">ExpandUp</span></span>|<span data-ttu-id="21856-138">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="21856-138">ExpandDirectionStates</span></span>|<span data-ttu-id="21856-139">Ovládací prvek rozšíří nahoru.</span><span class="sxs-lookup"><span data-stu-id="21856-139">The control expands up.</span></span>|  
|<span data-ttu-id="21856-140">ExpandLeft</span><span class="sxs-lookup"><span data-stu-id="21856-140">ExpandLeft</span></span>|<span data-ttu-id="21856-141">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="21856-141">ExpandDirectionStates</span></span>|<span data-ttu-id="21856-142">Ovládací prvek rozšíří vlevo.</span><span class="sxs-lookup"><span data-stu-id="21856-142">The control expands left.</span></span>|  
|<span data-ttu-id="21856-143">ExpandRight</span><span class="sxs-lookup"><span data-stu-id="21856-143">ExpandRight</span></span>|<span data-ttu-id="21856-144">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="21856-144">ExpandDirectionStates</span></span>|<span data-ttu-id="21856-145">Ovládací prvek rozšíří vpravo.</span><span class="sxs-lookup"><span data-stu-id="21856-145">The control expands right.</span></span>|  
|<span data-ttu-id="21856-146">Platné</span><span class="sxs-lookup"><span data-stu-id="21856-146">Valid</span></span>|<span data-ttu-id="21856-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21856-147">ValidationStates</span></span>|<span data-ttu-id="21856-148">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="21856-148">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="21856-149">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="21856-149">InvalidFocused</span></span>|<span data-ttu-id="21856-150">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21856-150">ValidationStates</span></span>|<span data-ttu-id="21856-151"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="21856-151">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="21856-152">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="21856-152">InvalidUnfocused</span></span>|<span data-ttu-id="21856-153">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21856-153">ValidationStates</span></span>|<span data-ttu-id="21856-154"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="21856-154">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="expander-controltemplate-example"></a><span data-ttu-id="21856-155">Rozšíření – příklad ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="21856-155">Expander ControlTemplate Example</span></span>  
 <span data-ttu-id="21856-156">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Expander> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="21856-156">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Expander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 <span data-ttu-id="21856-157">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="21856-157">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="21856-158">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="21856-158">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21856-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="21856-159">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="21856-160">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="21856-160">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="21856-161">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="21856-161">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="21856-162">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="21856-162">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="21856-163">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="21856-163">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
