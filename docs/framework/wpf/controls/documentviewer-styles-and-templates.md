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
ms.openlocfilehash: 217fa0ff7b8c34de817a269effbf64311bbea7f2
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="fb5b1-102">DocumentViewer – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="fb5b1-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="fb5b1-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb5b1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="fb5b1-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb5b1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="fb5b1-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="fb5b1-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="fb5b1-106">Třídy DocumentViewer částí</span><span class="sxs-lookup"><span data-stu-id="fb5b1-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="fb5b1-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb5b1-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="fb5b1-108">Část</span><span class="sxs-lookup"><span data-stu-id="fb5b1-108">Part</span></span>|<span data-ttu-id="fb5b1-109">Typ</span><span class="sxs-lookup"><span data-stu-id="fb5b1-109">Type</span></span>|<span data-ttu-id="fb5b1-110">Popis</span><span class="sxs-lookup"><span data-stu-id="fb5b1-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fb5b1-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="fb5b1-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="fb5b1-112">Obsah a posouvání oblasti.</span><span class="sxs-lookup"><span data-stu-id="fb5b1-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="fb5b1-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="fb5b1-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="fb5b1-114">Do vyhledávacího pole v dolní části ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="fb5b1-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="fb5b1-115">Třídy DocumentViewer stavy</span><span class="sxs-lookup"><span data-stu-id="fb5b1-115">DocumentViewer States</span></span>  
 <span data-ttu-id="fb5b1-116">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb5b1-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="fb5b1-117">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="fb5b1-117">VisualState Name</span></span>|<span data-ttu-id="fb5b1-118">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="fb5b1-118">VisualStateGroup Name</span></span>|<span data-ttu-id="fb5b1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="fb5b1-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fb5b1-120">Platné</span><span class="sxs-lookup"><span data-stu-id="fb5b1-120">Valid</span></span>|<span data-ttu-id="fb5b1-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb5b1-121">ValidationStates</span></span>|<span data-ttu-id="fb5b1-122">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="fb5b1-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="fb5b1-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="fb5b1-123">InvalidFocused</span></span>|<span data-ttu-id="fb5b1-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb5b1-124">ValidationStates</span></span>|<span data-ttu-id="fb5b1-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="fb5b1-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="fb5b1-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="fb5b1-126">InvalidUnfocused</span></span>|<span data-ttu-id="fb5b1-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb5b1-127">ValidationStates</span></span>|<span data-ttu-id="fb5b1-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="fb5b1-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="fb5b1-129">Příklad ControlTemplate třídy DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="fb5b1-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="fb5b1-130">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fb5b1-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="fb5b1-131">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="fb5b1-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="fb5b1-132">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="fb5b1-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb5b1-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb5b1-133">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="fb5b1-134">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="fb5b1-134">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="fb5b1-135">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="fb5b1-135">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="fb5b1-136">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="fb5b1-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="fb5b1-137">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="fb5b1-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
