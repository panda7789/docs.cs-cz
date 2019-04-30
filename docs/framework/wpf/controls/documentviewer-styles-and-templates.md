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
ms.openlocfilehash: 4e91a640b36e4793567c9e728fd71ec8ce596743
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911765"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="14cfc-102">DocumentViewer – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="14cfc-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="14cfc-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="14cfc-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="14cfc-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="14cfc-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="14cfc-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="14cfc-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="14cfc-106">DocumentViewer – částí</span><span class="sxs-lookup"><span data-stu-id="14cfc-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="14cfc-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="14cfc-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="14cfc-108">Část</span><span class="sxs-lookup"><span data-stu-id="14cfc-108">Part</span></span>|<span data-ttu-id="14cfc-109">Type</span><span class="sxs-lookup"><span data-stu-id="14cfc-109">Type</span></span>|<span data-ttu-id="14cfc-110">Popis</span><span class="sxs-lookup"><span data-stu-id="14cfc-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="14cfc-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="14cfc-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="14cfc-112">Obsah a oblast posouvání.</span><span class="sxs-lookup"><span data-stu-id="14cfc-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="14cfc-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="14cfc-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="14cfc-114">Pole Hledat v dolní části ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="14cfc-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="14cfc-115">DocumentViewer – stavy</span><span class="sxs-lookup"><span data-stu-id="14cfc-115">DocumentViewer States</span></span>  
 <span data-ttu-id="14cfc-116">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="14cfc-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="14cfc-117">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="14cfc-117">VisualState Name</span></span>|<span data-ttu-id="14cfc-118">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="14cfc-118">VisualStateGroup Name</span></span>|<span data-ttu-id="14cfc-119">Popis</span><span class="sxs-lookup"><span data-stu-id="14cfc-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="14cfc-120">Platné</span><span class="sxs-lookup"><span data-stu-id="14cfc-120">Valid</span></span>|<span data-ttu-id="14cfc-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="14cfc-121">ValidationStates</span></span>|<span data-ttu-id="14cfc-122">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="14cfc-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="14cfc-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="14cfc-123">InvalidFocused</span></span>|<span data-ttu-id="14cfc-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="14cfc-124">ValidationStates</span></span>|<span data-ttu-id="14cfc-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="14cfc-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="14cfc-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="14cfc-126">InvalidUnfocused</span></span>|<span data-ttu-id="14cfc-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="14cfc-127">ValidationStates</span></span>|<span data-ttu-id="14cfc-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="14cfc-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="14cfc-129">DocumentViewer – příklad šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="14cfc-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="14cfc-130">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="14cfc-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="14cfc-131">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="14cfc-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="14cfc-132">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="14cfc-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14cfc-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14cfc-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="14cfc-134">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="14cfc-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="14cfc-135">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="14cfc-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="14cfc-136">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="14cfc-136">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="14cfc-137">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="14cfc-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
