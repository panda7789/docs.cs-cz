---
title: 'Postupy: Vodorovné a svislé zarovnání obsahu v objektu StackPanel'
description: Naučte se upravovat orientaci obsahu v Windows Presentation Foundation StackPanel a HorizontalAlignment a VerticalAlignment podřízeného obsahu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: d3c7215d8193d1d8a72597c44cf265f5bd400ea1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167627"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a><span data-ttu-id="0ef0d-103">Postupy: Vodorovné a svislé zarovnání obsahu v objektu StackPanel</span><span class="sxs-lookup"><span data-stu-id="0ef0d-103">How to: Horizontally or Vertically Align Content in a StackPanel</span></span>
<span data-ttu-id="0ef0d-104">Tento příklad ukazuje, jak upravit <xref:System.Windows.Controls.StackPanel.Orientation%2A> obsah v rámci <xref:System.Windows.Controls.StackPanel> prvku a také jak upravit <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> podřízený obsah.</span><span class="sxs-lookup"><span data-stu-id="0ef0d-104">This example shows how to adjust the <xref:System.Windows.Controls.StackPanel.Orientation%2A> of content within a <xref:System.Windows.Controls.StackPanel> element, and also how to adjust the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> of child content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ef0d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ef0d-105">Example</span></span>  
 <span data-ttu-id="0ef0d-106">Následující příklad vytvoří tři <xref:System.Windows.Controls.ListBox> prvky v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0ef0d-106">The following example creates three <xref:System.Windows.Controls.ListBox> elements in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="0ef0d-107">Každý <xref:System.Windows.Controls.ListBox> představuje možné hodnoty <xref:System.Windows.Controls.StackPanel.Orientation%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastností, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.Controls.StackPanel> .</span><span class="sxs-lookup"><span data-stu-id="0ef0d-107">Each <xref:System.Windows.Controls.ListBox> represents the possible values of the <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> properties of a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="0ef0d-108">Když uživatel vybere hodnotu v některém z <xref:System.Windows.Controls.ListBox> elementů, změní se přidružená vlastnost <xref:System.Windows.Controls.StackPanel> a jejích podřízených <xref:System.Windows.Controls.Button> elementů.</span><span class="sxs-lookup"><span data-stu-id="0ef0d-108">When a user selects a value in any of the <xref:System.Windows.Controls.ListBox> elements, the associated property of the <xref:System.Windows.Controls.StackPanel> and its child <xref:System.Windows.Controls.Button> elements change.</span></span>  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="0ef0d-109">Následující soubor s kódem na pozadí definuje změny událostí, které jsou přidruženy k <xref:System.Windows.Controls.ListBox> změnám výběru.</span><span class="sxs-lookup"><span data-stu-id="0ef0d-109">The following code-behind file defines the changes to the events that are associated with the <xref:System.Windows.Controls.ListBox> selection changes.</span></span> <span data-ttu-id="0ef0d-110"><xref:System.Windows.Controls.StackPanel>je identifikován <xref:System.Windows.FrameworkElement.Name%2A> `sp1` .</span><span class="sxs-lookup"><span data-stu-id="0ef0d-110"><xref:System.Windows.Controls.StackPanel> is identified by the <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span></span>  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0ef0d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ef0d-111">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [<span data-ttu-id="0ef0d-112">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="0ef0d-112">Panels Overview</span></span>](panels-overview.md)
