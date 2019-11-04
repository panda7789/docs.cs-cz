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
ms.openlocfilehash: 70a2002ab114f2bbd6a4e550ae9006e214ee27a5
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458415"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="faaa1-102">ScrollViewer – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="faaa1-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="faaa1-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="faaa1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="faaa1-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="faaa1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="faaa1-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="faaa1-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="faaa1-106">ScrollViewer části</span><span class="sxs-lookup"><span data-stu-id="faaa1-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="faaa1-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="faaa1-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="faaa1-108">Částí</span><span class="sxs-lookup"><span data-stu-id="faaa1-108">Part</span></span>|<span data-ttu-id="faaa1-109">Typ</span><span class="sxs-lookup"><span data-stu-id="faaa1-109">Type</span></span>|<span data-ttu-id="faaa1-110">Popis</span><span class="sxs-lookup"><span data-stu-id="faaa1-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="faaa1-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="faaa1-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="faaa1-112">Zástupný text pro obsah v <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="faaa1-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="faaa1-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="faaa1-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="faaa1-114"><xref:System.Windows.Controls.Primitives.ScrollBar> slouží k vodorovnému posouvání obsahu.</span><span class="sxs-lookup"><span data-stu-id="faaa1-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="faaa1-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="faaa1-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="faaa1-116"><xref:System.Windows.Controls.Primitives.ScrollBar> slouží k posunu obsahu svisle.</span><span class="sxs-lookup"><span data-stu-id="faaa1-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="faaa1-117">ScrollViewer stavy</span><span class="sxs-lookup"><span data-stu-id="faaa1-117">ScrollViewer States</span></span>  
 <span data-ttu-id="faaa1-118">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="faaa1-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="faaa1-119">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="faaa1-119">VisualState Name</span></span>|<span data-ttu-id="faaa1-120">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="faaa1-120">VisualStateGroup Name</span></span>|<span data-ttu-id="faaa1-121">Popis</span><span class="sxs-lookup"><span data-stu-id="faaa1-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="faaa1-122">Platné</span><span class="sxs-lookup"><span data-stu-id="faaa1-122">Valid</span></span>|<span data-ttu-id="faaa1-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="faaa1-123">ValidationStates</span></span>|<span data-ttu-id="faaa1-124">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="faaa1-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="faaa1-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="faaa1-125">InvalidFocused</span></span>|<span data-ttu-id="faaa1-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="faaa1-126">ValidationStates</span></span>|<span data-ttu-id="faaa1-127">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="faaa1-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="faaa1-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="faaa1-128">InvalidUnfocused</span></span>|<span data-ttu-id="faaa1-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="faaa1-129">ValidationStates</span></span>|<span data-ttu-id="faaa1-130">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="faaa1-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="faaa1-131">ScrollViewer ControlTemplate – příklad</span><span class="sxs-lookup"><span data-stu-id="faaa1-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="faaa1-132">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="faaa1-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="faaa1-133">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="faaa1-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="faaa1-134">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="faaa1-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faaa1-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="faaa1-135">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="faaa1-136">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="faaa1-136">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="faaa1-137">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="faaa1-137">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="faaa1-138">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="faaa1-138">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="faaa1-139">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="faaa1-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
