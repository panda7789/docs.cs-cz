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
ms.openlocfilehash: 04225458e9889c511b7aaa359239512e316cbb26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="expander-styles-and-templates"></a><span data-ttu-id="44f79-102">Styly a šablony rozšíření</span><span class="sxs-lookup"><span data-stu-id="44f79-102">Expander Styles and Templates</span></span>
<span data-ttu-id="44f79-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Expander> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="44f79-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Expander> control.</span></span> <span data-ttu-id="44f79-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="44f79-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="44f79-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="44f79-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="expander-parts"></a><span data-ttu-id="44f79-106">Expander částí</span><span class="sxs-lookup"><span data-stu-id="44f79-106">Expander Parts</span></span>  
 <span data-ttu-id="44f79-107"><xref:System.Windows.Controls.Expander> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="44f79-107">The <xref:System.Windows.Controls.Expander> control does not have any named parts.</span></span>  
  
## <a name="expander-states"></a><span data-ttu-id="44f79-108">Stavy Expander</span><span class="sxs-lookup"><span data-stu-id="44f79-108">Expander States</span></span>  
 <span data-ttu-id="44f79-109">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Expander> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="44f79-109">The following table lists the visual states for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
|<span data-ttu-id="44f79-110">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="44f79-110">VisualState Name</span></span>|<span data-ttu-id="44f79-111">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="44f79-111">VisualStateGroup Name</span></span>|<span data-ttu-id="44f79-112">Popis</span><span class="sxs-lookup"><span data-stu-id="44f79-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="44f79-113">Normální</span><span class="sxs-lookup"><span data-stu-id="44f79-113">Normal</span></span>|<span data-ttu-id="44f79-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="44f79-114">CommonStates</span></span>|<span data-ttu-id="44f79-115">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="44f79-115">The default state.</span></span>|  
|<span data-ttu-id="44f79-116">Myš nad</span><span class="sxs-lookup"><span data-stu-id="44f79-116">MouseOver</span></span>|<span data-ttu-id="44f79-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="44f79-117">CommonStates</span></span>|<span data-ttu-id="44f79-118">Ukazatel myši je umístěn nad ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="44f79-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="44f79-119">zakázáno</span><span class="sxs-lookup"><span data-stu-id="44f79-119">Disabled</span></span>|<span data-ttu-id="44f79-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="44f79-120">CommonStates</span></span>|<span data-ttu-id="44f79-121">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="44f79-121">The control is disabled.</span></span>|  
|<span data-ttu-id="44f79-122">Zaměřuje</span><span class="sxs-lookup"><span data-stu-id="44f79-122">Focused</span></span>|<span data-ttu-id="44f79-123">FocusStates</span><span class="sxs-lookup"><span data-stu-id="44f79-123">FocusStates</span></span>|<span data-ttu-id="44f79-124">Ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="44f79-124">The control has focus.</span></span>|  
|<span data-ttu-id="44f79-125">Nezaostřená</span><span class="sxs-lookup"><span data-stu-id="44f79-125">Unfocused</span></span>|<span data-ttu-id="44f79-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="44f79-126">FocusStates</span></span>|<span data-ttu-id="44f79-127">Ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="44f79-127">The control does not have focus.</span></span>|  
|<span data-ttu-id="44f79-128">Rozšířit</span><span class="sxs-lookup"><span data-stu-id="44f79-128">Expanded</span></span>|<span data-ttu-id="44f79-129">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="44f79-129">ExpansionStates</span></span>|<span data-ttu-id="44f79-130">Ovládací prvek je rozšířena.</span><span class="sxs-lookup"><span data-stu-id="44f79-130">The control is expanded.</span></span>|  
|<span data-ttu-id="44f79-131">Sbalené</span><span class="sxs-lookup"><span data-stu-id="44f79-131">Collapsed</span></span>|<span data-ttu-id="44f79-132">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="44f79-132">ExpansionStates</span></span>|<span data-ttu-id="44f79-133">Ovládací prvek není rozbalen.</span><span class="sxs-lookup"><span data-stu-id="44f79-133">The control is not expanded.</span></span>|  
|<span data-ttu-id="44f79-134">ExpandDown</span><span class="sxs-lookup"><span data-stu-id="44f79-134">ExpandDown</span></span>|<span data-ttu-id="44f79-135">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="44f79-135">ExpandDirectionStates</span></span>|<span data-ttu-id="44f79-136">Ovládací prvek rozšíří dolů.</span><span class="sxs-lookup"><span data-stu-id="44f79-136">The control expands down.</span></span>|  
|<span data-ttu-id="44f79-137">ExpandUp</span><span class="sxs-lookup"><span data-stu-id="44f79-137">ExpandUp</span></span>|<span data-ttu-id="44f79-138">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="44f79-138">ExpandDirectionStates</span></span>|<span data-ttu-id="44f79-139">Ovládací prvek rozšíří nahoru.</span><span class="sxs-lookup"><span data-stu-id="44f79-139">The control expands up.</span></span>|  
|<span data-ttu-id="44f79-140">ExpandLeft</span><span class="sxs-lookup"><span data-stu-id="44f79-140">ExpandLeft</span></span>|<span data-ttu-id="44f79-141">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="44f79-141">ExpandDirectionStates</span></span>|<span data-ttu-id="44f79-142">Ovládací prvek rozšíří vlevo.</span><span class="sxs-lookup"><span data-stu-id="44f79-142">The control expands left.</span></span>|  
|<span data-ttu-id="44f79-143">ExpandRight</span><span class="sxs-lookup"><span data-stu-id="44f79-143">ExpandRight</span></span>|<span data-ttu-id="44f79-144">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="44f79-144">ExpandDirectionStates</span></span>|<span data-ttu-id="44f79-145">Ovládací prvek rozšíří vpravo.</span><span class="sxs-lookup"><span data-stu-id="44f79-145">The control expands right.</span></span>|  
|<span data-ttu-id="44f79-146">Platné</span><span class="sxs-lookup"><span data-stu-id="44f79-146">Valid</span></span>|<span data-ttu-id="44f79-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="44f79-147">ValidationStates</span></span>|<span data-ttu-id="44f79-148">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="44f79-148">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="44f79-149">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="44f79-149">InvalidFocused</span></span>|<span data-ttu-id="44f79-150">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="44f79-150">ValidationStates</span></span>|<span data-ttu-id="44f79-151"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="44f79-151">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="44f79-152">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="44f79-152">InvalidUnfocused</span></span>|<span data-ttu-id="44f79-153">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="44f79-153">ValidationStates</span></span>|<span data-ttu-id="44f79-154"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="44f79-154">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="expander-controltemplate-example"></a><span data-ttu-id="44f79-155">Rozšíření – příklad ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="44f79-155">Expander ControlTemplate Example</span></span>  
 <span data-ttu-id="44f79-156">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Expander> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="44f79-156">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Expander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 <span data-ttu-id="44f79-157">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="44f79-157">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="44f79-158">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="44f79-158">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f79-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="44f79-159">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="44f79-160">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="44f79-160">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="44f79-161">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="44f79-161">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="44f79-162">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="44f79-162">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="44f79-163">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="44f79-163">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
