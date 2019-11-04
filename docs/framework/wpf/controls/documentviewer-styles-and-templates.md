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
ms.openlocfilehash: 7a812ff913703e3aa8408da8a11d28ee5adfa7fd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460344"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="d9485-102">DocumentViewer – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d9485-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="d9485-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="d9485-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="d9485-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="d9485-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d9485-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d9485-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="d9485-106">DocumentViewer části</span><span class="sxs-lookup"><span data-stu-id="d9485-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="d9485-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="d9485-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="d9485-108">Částí</span><span class="sxs-lookup"><span data-stu-id="d9485-108">Part</span></span>|<span data-ttu-id="d9485-109">Typ</span><span class="sxs-lookup"><span data-stu-id="d9485-109">Type</span></span>|<span data-ttu-id="d9485-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d9485-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d9485-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="d9485-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="d9485-112">Oblast obsahu a posouvání.</span><span class="sxs-lookup"><span data-stu-id="d9485-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="d9485-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="d9485-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="d9485-114">Vyhledávací pole, ve výchozím nastavení v dolní části.</span><span class="sxs-lookup"><span data-stu-id="d9485-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="d9485-115">DocumentViewer stavy</span><span class="sxs-lookup"><span data-stu-id="d9485-115">DocumentViewer States</span></span>  
 <span data-ttu-id="d9485-116">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="d9485-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="d9485-117">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="d9485-117">VisualState Name</span></span>|<span data-ttu-id="d9485-118">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="d9485-118">VisualStateGroup Name</span></span>|<span data-ttu-id="d9485-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d9485-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d9485-120">Platné</span><span class="sxs-lookup"><span data-stu-id="d9485-120">Valid</span></span>|<span data-ttu-id="d9485-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9485-121">ValidationStates</span></span>|<span data-ttu-id="d9485-122">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="d9485-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d9485-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d9485-123">InvalidFocused</span></span>|<span data-ttu-id="d9485-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9485-124">ValidationStates</span></span>|<span data-ttu-id="d9485-125">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="d9485-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d9485-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d9485-126">InvalidUnfocused</span></span>|<span data-ttu-id="d9485-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9485-127">ValidationStates</span></span>|<span data-ttu-id="d9485-128">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="d9485-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="d9485-129">DocumentViewer ControlTemplate – příklad</span><span class="sxs-lookup"><span data-stu-id="d9485-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="d9485-130">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="d9485-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="d9485-131">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="d9485-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d9485-132">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="d9485-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9485-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9485-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d9485-134">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="d9485-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d9485-135">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d9485-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d9485-136">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="d9485-136">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="d9485-137">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="d9485-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
