---
title: ScrollBar – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: f85a6fb31adac71541eed31a1ccfde9e06028af7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361145"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="86b28-102">ScrollBar – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="86b28-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="86b28-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Primitives.ScrollBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="86b28-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="86b28-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="86b28-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="86b28-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="86b28-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="86b28-106">Části posuvník</span><span class="sxs-lookup"><span data-stu-id="86b28-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="86b28-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.Primitives.ScrollBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="86b28-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="86b28-108">Část</span><span class="sxs-lookup"><span data-stu-id="86b28-108">Part</span></span>|<span data-ttu-id="86b28-109">Typ</span><span class="sxs-lookup"><span data-stu-id="86b28-109">Type</span></span>|<span data-ttu-id="86b28-110">Popis</span><span class="sxs-lookup"><span data-stu-id="86b28-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="86b28-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="86b28-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="86b28-112">Kontejner pro prvek, který označuje pozici <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="86b28-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="86b28-113">ScrollBar – stavy</span><span class="sxs-lookup"><span data-stu-id="86b28-113">ScrollBar States</span></span>  
 <span data-ttu-id="86b28-114">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.ScrollBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="86b28-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="86b28-115">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="86b28-115">VisualState Name</span></span>|<span data-ttu-id="86b28-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="86b28-116">VisualStateGroup Name</span></span>|<span data-ttu-id="86b28-117">Popis</span><span class="sxs-lookup"><span data-stu-id="86b28-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="86b28-118">Normální</span><span class="sxs-lookup"><span data-stu-id="86b28-118">Normal</span></span>|<span data-ttu-id="86b28-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="86b28-119">CommonStates</span></span>|<span data-ttu-id="86b28-120">Ve výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="86b28-120">The default state.</span></span>|  
|<span data-ttu-id="86b28-121">Myš nad</span><span class="sxs-lookup"><span data-stu-id="86b28-121">MouseOver</span></span>|<span data-ttu-id="86b28-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="86b28-122">CommonStates</span></span>|<span data-ttu-id="86b28-123">Je ukazatel myši umístěn nad ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="86b28-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="86b28-124">Zakázáno</span><span class="sxs-lookup"><span data-stu-id="86b28-124">Disabled</span></span>|<span data-ttu-id="86b28-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="86b28-125">CommonStates</span></span>|<span data-ttu-id="86b28-126">Ovládací prvek je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="86b28-126">The control is disabled.</span></span>|  
|<span data-ttu-id="86b28-127">Platné</span><span class="sxs-lookup"><span data-stu-id="86b28-127">Valid</span></span>|<span data-ttu-id="86b28-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="86b28-128">ValidationStates</span></span>|<span data-ttu-id="86b28-129">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="86b28-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="86b28-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="86b28-130">InvalidFocused</span></span>|<span data-ttu-id="86b28-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="86b28-131">ValidationStates</span></span>|<span data-ttu-id="86b28-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="86b28-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="86b28-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="86b28-133">InvalidUnfocused</span></span>|<span data-ttu-id="86b28-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="86b28-134">ValidationStates</span></span>|<span data-ttu-id="86b28-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="86b28-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="86b28-136">Příklad šablony ControlTemplate posuvník</span><span class="sxs-lookup"><span data-stu-id="86b28-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="86b28-137">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Primitives.ScrollBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="86b28-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="86b28-138">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="86b28-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="86b28-139">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="86b28-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b28-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86b28-140">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="86b28-141">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="86b28-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="86b28-142">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="86b28-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="86b28-143">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="86b28-143">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="86b28-144">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="86b28-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
