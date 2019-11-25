---
title: DocumentViewer – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
ms.openlocfilehash: ac1dc4f74a8e8f3ad2e84c6d50239ec827306c28
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283534"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="5229a-102">DocumentViewer – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="5229a-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="5229a-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="5229a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="5229a-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="5229a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5229a-105">Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="5229a-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="5229a-106">DocumentViewer části</span><span class="sxs-lookup"><span data-stu-id="5229a-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="5229a-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="5229a-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="5229a-108">Částí</span><span class="sxs-lookup"><span data-stu-id="5229a-108">Part</span></span>|<span data-ttu-id="5229a-109">Typ</span><span class="sxs-lookup"><span data-stu-id="5229a-109">Type</span></span>|<span data-ttu-id="5229a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5229a-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5229a-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="5229a-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="5229a-112">Oblast obsahu a posouvání.</span><span class="sxs-lookup"><span data-stu-id="5229a-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="5229a-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="5229a-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="5229a-114">Vyhledávací pole, ve výchozím nastavení v dolní části.</span><span class="sxs-lookup"><span data-stu-id="5229a-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="5229a-115">DocumentViewer stavy</span><span class="sxs-lookup"><span data-stu-id="5229a-115">DocumentViewer States</span></span>  
 <span data-ttu-id="5229a-116">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="5229a-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="5229a-117">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="5229a-117">VisualState Name</span></span>|<span data-ttu-id="5229a-118">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="5229a-118">VisualStateGroup Name</span></span>|<span data-ttu-id="5229a-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5229a-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5229a-120">Platné</span><span class="sxs-lookup"><span data-stu-id="5229a-120">Valid</span></span>|<span data-ttu-id="5229a-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5229a-121">ValidationStates</span></span>|<span data-ttu-id="5229a-122">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="5229a-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5229a-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5229a-123">InvalidFocused</span></span>|<span data-ttu-id="5229a-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5229a-124">ValidationStates</span></span>|<span data-ttu-id="5229a-125">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="5229a-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5229a-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5229a-126">InvalidUnfocused</span></span>|<span data-ttu-id="5229a-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5229a-127">ValidationStates</span></span>|<span data-ttu-id="5229a-128">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="5229a-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="5229a-129">DocumentViewer ControlTemplate – příklad</span><span class="sxs-lookup"><span data-stu-id="5229a-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="5229a-130">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="5229a-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="5229a-131">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="5229a-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5229a-132">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="5229a-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5229a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5229a-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="5229a-134">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="5229a-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="5229a-135">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="5229a-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="5229a-136">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="5229a-136">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="5229a-137">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="5229a-137">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
