---
title: "DocumentViewer – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7027fbee6a35b9219e65c9964db9a038e942f14e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="52dd7-102">DocumentViewer – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="52dd7-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="52dd7-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="52dd7-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="52dd7-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="52dd7-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="52dd7-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="52dd7-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="52dd7-106">Třídy DocumentViewer částí</span><span class="sxs-lookup"><span data-stu-id="52dd7-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="52dd7-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="52dd7-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="52dd7-108">Část</span><span class="sxs-lookup"><span data-stu-id="52dd7-108">Part</span></span>|<span data-ttu-id="52dd7-109">Typ</span><span class="sxs-lookup"><span data-stu-id="52dd7-109">Type</span></span>|<span data-ttu-id="52dd7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="52dd7-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="52dd7-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="52dd7-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="52dd7-112">Obsah a posouvání oblasti.</span><span class="sxs-lookup"><span data-stu-id="52dd7-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="52dd7-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="52dd7-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="52dd7-114">Do vyhledávacího pole v dolní části ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="52dd7-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="52dd7-115">Třídy DocumentViewer stavy</span><span class="sxs-lookup"><span data-stu-id="52dd7-115">DocumentViewer States</span></span>  
 <span data-ttu-id="52dd7-116">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="52dd7-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="52dd7-117">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="52dd7-117">VisualState Name</span></span>|<span data-ttu-id="52dd7-118">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="52dd7-118">VisualStateGroup Name</span></span>|<span data-ttu-id="52dd7-119">Popis</span><span class="sxs-lookup"><span data-stu-id="52dd7-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="52dd7-120">Platné</span><span class="sxs-lookup"><span data-stu-id="52dd7-120">Valid</span></span>|<span data-ttu-id="52dd7-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="52dd7-121">ValidationStates</span></span>|<span data-ttu-id="52dd7-122">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="52dd7-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="52dd7-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="52dd7-123">InvalidFocused</span></span>|<span data-ttu-id="52dd7-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="52dd7-124">ValidationStates</span></span>|<span data-ttu-id="52dd7-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="52dd7-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="52dd7-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="52dd7-126">InvalidUnfocused</span></span>|<span data-ttu-id="52dd7-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="52dd7-127">ValidationStates</span></span>|<span data-ttu-id="52dd7-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="52dd7-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="52dd7-129">Příklad ControlTemplate třídy DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="52dd7-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="52dd7-130">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.DocumentViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="52dd7-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="52dd7-131">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="52dd7-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="52dd7-132">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="52dd7-132">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52dd7-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="52dd7-133">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="52dd7-134">Styly ovládacího prvku a šablony</span><span class="sxs-lookup"><span data-stu-id="52dd7-134">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="52dd7-135">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="52dd7-135">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="52dd7-136">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="52dd7-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="52dd7-137">Přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="52dd7-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
