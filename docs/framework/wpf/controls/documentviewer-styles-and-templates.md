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
ms.openlocfilehash: b120359e63c2916e82b79b2f7b7f1aa5426be99c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369640"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="13045-102">DocumentViewer – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="13045-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="13045-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="13045-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="13045-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="13045-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="13045-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="13045-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="13045-106">DocumentViewer – částí</span><span class="sxs-lookup"><span data-stu-id="13045-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="13045-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="13045-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="13045-108">Část</span><span class="sxs-lookup"><span data-stu-id="13045-108">Part</span></span>|<span data-ttu-id="13045-109">Typ</span><span class="sxs-lookup"><span data-stu-id="13045-109">Type</span></span>|<span data-ttu-id="13045-110">Popis</span><span class="sxs-lookup"><span data-stu-id="13045-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="13045-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="13045-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="13045-112">Obsah a oblast posouvání.</span><span class="sxs-lookup"><span data-stu-id="13045-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="13045-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="13045-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="13045-114">Pole Hledat v dolní části ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="13045-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="13045-115">DocumentViewer – stavy</span><span class="sxs-lookup"><span data-stu-id="13045-115">DocumentViewer States</span></span>  
 <span data-ttu-id="13045-116">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="13045-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="13045-117">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="13045-117">VisualState Name</span></span>|<span data-ttu-id="13045-118">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="13045-118">VisualStateGroup Name</span></span>|<span data-ttu-id="13045-119">Popis</span><span class="sxs-lookup"><span data-stu-id="13045-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="13045-120">Platné</span><span class="sxs-lookup"><span data-stu-id="13045-120">Valid</span></span>|<span data-ttu-id="13045-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="13045-121">ValidationStates</span></span>|<span data-ttu-id="13045-122">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="13045-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="13045-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="13045-123">InvalidFocused</span></span>|<span data-ttu-id="13045-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="13045-124">ValidationStates</span></span>|<span data-ttu-id="13045-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="13045-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="13045-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="13045-126">InvalidUnfocused</span></span>|<span data-ttu-id="13045-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="13045-127">ValidationStates</span></span>|<span data-ttu-id="13045-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="13045-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="13045-129">DocumentViewer – příklad šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="13045-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="13045-130">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="13045-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="13045-131">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="13045-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="13045-132">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="13045-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13045-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13045-133">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="13045-134">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="13045-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="13045-135">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="13045-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="13045-136">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="13045-136">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="13045-137">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="13045-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
