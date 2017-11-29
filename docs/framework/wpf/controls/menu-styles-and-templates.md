---
title: "Styly a šablony nabídky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e007ae09e57353446feb13b3693e62c985f522d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="menu-styles-and-templates"></a><span data-ttu-id="08ebb-102">Styly a šablony nabídky</span><span class="sxs-lookup"><span data-stu-id="08ebb-102">Menu Styles and Templates</span></span>
<span data-ttu-id="08ebb-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Menu> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08ebb-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Menu> control.</span></span> <span data-ttu-id="08ebb-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08ebb-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="08ebb-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="08ebb-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="menu-parts"></a><span data-ttu-id="08ebb-106">Části nabídky</span><span class="sxs-lookup"><span data-stu-id="08ebb-106">Menu Parts</span></span>  
 <span data-ttu-id="08ebb-107"><xref:System.Windows.Controls.Menu> Ovládací prvek nemá žádné pojmenované částí.</span><span class="sxs-lookup"><span data-stu-id="08ebb-107">The <xref:System.Windows.Controls.Menu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="08ebb-108">Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Menu>, může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="08ebb-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.Menu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="08ebb-109">( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí jednotlivé položky <xref:System.Windows.Controls.Menu>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).</span><span class="sxs-lookup"><span data-stu-id="08ebb-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.Menu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="08ebb-110">Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímými podřízenými z <xref:System.Windows.Controls.ScrollViewer>, musíte <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="08ebb-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menu-states"></a><span data-ttu-id="08ebb-111">Stavy nabídky</span><span class="sxs-lookup"><span data-stu-id="08ebb-111">Menu States</span></span>  
 <span data-ttu-id="08ebb-112">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Menu> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08ebb-112">The following table lists the visual states for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="08ebb-113">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="08ebb-113">VisualState Name</span></span>|<span data-ttu-id="08ebb-114">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="08ebb-114">VisualStateGroup Name</span></span>|<span data-ttu-id="08ebb-115">Popis</span><span class="sxs-lookup"><span data-stu-id="08ebb-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="08ebb-116">Platné</span><span class="sxs-lookup"><span data-stu-id="08ebb-116">Valid</span></span>|<span data-ttu-id="08ebb-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08ebb-117">ValidationStates</span></span>|<span data-ttu-id="08ebb-118">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="08ebb-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="08ebb-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="08ebb-119">InvalidFocused</span></span>|<span data-ttu-id="08ebb-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08ebb-120">ValidationStates</span></span>|<span data-ttu-id="08ebb-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="08ebb-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="08ebb-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="08ebb-122">InvalidUnfocused</span></span>|<span data-ttu-id="08ebb-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08ebb-123">ValidationStates</span></span>|<span data-ttu-id="08ebb-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="08ebb-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menuitem-parts"></a><span data-ttu-id="08ebb-125">Části MenuItem</span><span class="sxs-lookup"><span data-stu-id="08ebb-125">MenuItem Parts</span></span>  
 <span data-ttu-id="08ebb-126">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.Menu> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08ebb-126">The following table lists the named parts for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="08ebb-127">Část</span><span class="sxs-lookup"><span data-stu-id="08ebb-127">Part</span></span>|<span data-ttu-id="08ebb-128">Typ</span><span class="sxs-lookup"><span data-stu-id="08ebb-128">Type</span></span>|<span data-ttu-id="08ebb-129">Popis</span><span class="sxs-lookup"><span data-stu-id="08ebb-129">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="08ebb-130">PART_Popup</span><span class="sxs-lookup"><span data-stu-id="08ebb-130">PART_Popup</span></span>|<xref:System.Windows.Controls.Primitives.Popup>|<span data-ttu-id="08ebb-131">Oblasti podnabídky.</span><span class="sxs-lookup"><span data-stu-id="08ebb-131">The area for the submenu.</span></span>|  
  
 <span data-ttu-id="08ebb-132">Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.MenuItem>, může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="08ebb-132">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.MenuItem>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="08ebb-133">( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí jednotlivé položky <xref:System.Windows.Controls.MenuItem>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).</span><span class="sxs-lookup"><span data-stu-id="08ebb-133">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.MenuItem>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="08ebb-134">Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímými podřízenými z <xref:System.Windows.Controls.ScrollViewer>, musíte <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="08ebb-134">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menuitem-states"></a><span data-ttu-id="08ebb-135">Stavy MenuItem</span><span class="sxs-lookup"><span data-stu-id="08ebb-135">MenuItem States</span></span>  
 <span data-ttu-id="08ebb-136">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.MenuItem> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08ebb-136">The following table lists the visual states for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
|<span data-ttu-id="08ebb-137">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="08ebb-137">VisualState Name</span></span>|<span data-ttu-id="08ebb-138">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="08ebb-138">VisualStateGroup Name</span></span>|<span data-ttu-id="08ebb-139">Popis</span><span class="sxs-lookup"><span data-stu-id="08ebb-139">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="08ebb-140">Platné</span><span class="sxs-lookup"><span data-stu-id="08ebb-140">Valid</span></span>|<span data-ttu-id="08ebb-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08ebb-141">ValidationStates</span></span>|<span data-ttu-id="08ebb-142">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="08ebb-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="08ebb-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="08ebb-143">InvalidFocused</span></span>|<span data-ttu-id="08ebb-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08ebb-144">ValidationStates</span></span>|<span data-ttu-id="08ebb-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="08ebb-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="08ebb-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="08ebb-146">InvalidUnfocused</span></span>|<span data-ttu-id="08ebb-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08ebb-147">ValidationStates</span></span>|<span data-ttu-id="08ebb-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="08ebb-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a><span data-ttu-id="08ebb-149">Nabídky a příklad ControlTemplate MenuItem</span><span class="sxs-lookup"><span data-stu-id="08ebb-149">Menu and MenuItem ControlTemplate Example</span></span>  
 <span data-ttu-id="08ebb-150">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Menu> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08ebb-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Menu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 <span data-ttu-id="08ebb-151">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.MenuItem> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08ebb-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 <span data-ttu-id="08ebb-152">V následujícím příkladu je definován `MenuScrollViewer`, který se používá v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="08ebb-152">The following example defines the `MenuScrollViewer`, which is used in the previous example.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <span data-ttu-id="08ebb-153"><xref:System.Windows.Controls.ControlTemplate> Příklady pomocí jednoho nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="08ebb-153">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="08ebb-154">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="08ebb-154">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ebb-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="08ebb-155">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="08ebb-156">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="08ebb-156">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="08ebb-157">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="08ebb-157">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="08ebb-158">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="08ebb-158">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="08ebb-159">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="08ebb-159">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
