---
title: ToolBar – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
ms.openlocfilehash: a984311234386cb205d5db35f18a743ca535ff05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283658"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="e7152-102">ToolBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e7152-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="e7152-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="e7152-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="e7152-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="e7152-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e7152-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="e7152-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="e7152-106">Části panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="e7152-106">ToolBar Parts</span></span>  
 <span data-ttu-id="e7152-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="e7152-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="e7152-108">Částí</span><span class="sxs-lookup"><span data-stu-id="e7152-108">Part</span></span>|<span data-ttu-id="e7152-109">Typ</span><span class="sxs-lookup"><span data-stu-id="e7152-109">Type</span></span>|<span data-ttu-id="e7152-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e7152-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e7152-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="e7152-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="e7152-112">Objekt, který obsahuje ovládací prvky na <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="e7152-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="e7152-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="e7152-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="e7152-114">Objekt, který obsahuje ovládací prvky, které jsou v oblasti přetečení <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="e7152-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="e7152-115">Když vytvoříte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ToolBar>, šablona může v <xref:System.Windows.Controls.ScrollViewer>obsahovat <xref:System.Windows.Controls.ItemsPresenter>.</span><span class="sxs-lookup"><span data-stu-id="e7152-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="e7152-116">(<xref:System.Windows.Controls.ItemsPresenter> zobrazuje každou položku v <xref:System.Windows.Controls.ToolBar>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v rámci ovládacího prvku).</span><span class="sxs-lookup"><span data-stu-id="e7152-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="e7152-117">Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímým podřízeným <xref:System.Windows.Controls.ScrollViewer>, je nutné zadat <xref:System.Windows.Controls.ItemsPresenter> název `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="e7152-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="e7152-118">Stavy panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="e7152-118">ToolBar States</span></span>  
 <span data-ttu-id="e7152-119">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="e7152-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="e7152-120">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="e7152-120">VisualState Name</span></span>|<span data-ttu-id="e7152-121">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="e7152-121">VisualStateGroup Name</span></span>|<span data-ttu-id="e7152-122">Popis</span><span class="sxs-lookup"><span data-stu-id="e7152-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e7152-123">Platný</span><span class="sxs-lookup"><span data-stu-id="e7152-123">Valid</span></span>|<span data-ttu-id="e7152-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e7152-124">ValidationStates</span></span>|<span data-ttu-id="e7152-125">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="e7152-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e7152-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e7152-126">InvalidFocused</span></span>|<span data-ttu-id="e7152-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e7152-127">ValidationStates</span></span>|<span data-ttu-id="e7152-128">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="e7152-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e7152-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e7152-129">InvalidUnfocused</span></span>|<span data-ttu-id="e7152-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e7152-130">ValidationStates</span></span>|<span data-ttu-id="e7152-131">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="e7152-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="e7152-132">ControlTemplate – příklad panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="e7152-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="e7152-133">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="e7152-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="e7152-134">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="e7152-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e7152-135">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="e7152-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7152-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7152-136">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e7152-137">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e7152-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="e7152-138">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e7152-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="e7152-139">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="e7152-139">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="e7152-140">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="e7152-140">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
