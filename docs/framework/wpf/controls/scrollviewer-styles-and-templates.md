---
title: ScrollViewer – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
ms.openlocfilehash: 9c0edfd7ab4772eb9a1f5ecdd3db611fa36bf8d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226830"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="deedb-102">ScrollViewer – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="deedb-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="deedb-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="deedb-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="deedb-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="deedb-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="deedb-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="deedb-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="deedb-106">Scrollviewer – částí</span><span class="sxs-lookup"><span data-stu-id="deedb-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="deedb-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="deedb-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="deedb-108">Část</span><span class="sxs-lookup"><span data-stu-id="deedb-108">Part</span></span>|<span data-ttu-id="deedb-109">Type</span><span class="sxs-lookup"><span data-stu-id="deedb-109">Type</span></span>|<span data-ttu-id="deedb-110">Popis</span><span class="sxs-lookup"><span data-stu-id="deedb-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="deedb-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="deedb-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="deedb-112">Zástupný symbol pro obsah <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="deedb-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="deedb-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="deedb-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="deedb-114"><xref:System.Windows.Controls.Primitives.ScrollBar> Umožňuje posouvat obsah vodorovně.</span><span class="sxs-lookup"><span data-stu-id="deedb-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="deedb-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="deedb-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="deedb-116"><xref:System.Windows.Controls.Primitives.ScrollBar> Používá posouvat obsah svisle.</span><span class="sxs-lookup"><span data-stu-id="deedb-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="deedb-117">Scrollviewer – stavy</span><span class="sxs-lookup"><span data-stu-id="deedb-117">ScrollViewer States</span></span>  
 <span data-ttu-id="deedb-118">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="deedb-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="deedb-119">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="deedb-119">VisualState Name</span></span>|<span data-ttu-id="deedb-120">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="deedb-120">VisualStateGroup Name</span></span>|<span data-ttu-id="deedb-121">Popis</span><span class="sxs-lookup"><span data-stu-id="deedb-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="deedb-122">Platné</span><span class="sxs-lookup"><span data-stu-id="deedb-122">Valid</span></span>|<span data-ttu-id="deedb-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="deedb-123">ValidationStates</span></span>|<span data-ttu-id="deedb-124">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="deedb-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="deedb-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="deedb-125">InvalidFocused</span></span>|<span data-ttu-id="deedb-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="deedb-126">ValidationStates</span></span>|<span data-ttu-id="deedb-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="deedb-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="deedb-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="deedb-128">InvalidUnfocused</span></span>|<span data-ttu-id="deedb-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="deedb-129">ValidationStates</span></span>|<span data-ttu-id="deedb-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="deedb-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="deedb-131">Scrollviewer – příklad šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="deedb-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="deedb-132">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="deedb-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="deedb-133">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="deedb-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="deedb-134">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="deedb-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deedb-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="deedb-135">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="deedb-136">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="deedb-136">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="deedb-137">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="deedb-137">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="deedb-138">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="deedb-138">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="deedb-139">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="deedb-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
