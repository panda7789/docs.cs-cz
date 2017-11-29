---
title: "Postupy: Vodorovné a svislé zarovnání obsahu v objektu StackPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bccf0455c736d14bd77113841603022d4c362787
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a><span data-ttu-id="fb9e7-102">Postupy: Vodorovné a svislé zarovnání obsahu v objektu StackPanel</span><span class="sxs-lookup"><span data-stu-id="fb9e7-102">How to: Horizontally or Vertically Align Content in a StackPanel</span></span>
<span data-ttu-id="fb9e7-103">Tento příklad ukazuje, jak upravit <xref:System.Windows.Controls.StackPanel.Orientation%2A> obsahu v rámci <xref:System.Windows.Controls.StackPanel> element a také jak upravit <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> podřízené obsahu.</span><span class="sxs-lookup"><span data-stu-id="fb9e7-103">This example shows how to adjust the <xref:System.Windows.Controls.StackPanel.Orientation%2A> of content within a <xref:System.Windows.Controls.StackPanel> element, and also how to adjust the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> of child content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb9e7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb9e7-104">Example</span></span>  
 <span data-ttu-id="fb9e7-105">Následující příklad vytvoří tři <xref:System.Windows.Controls.ListBox> elementů v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fb9e7-105">The following example creates three <xref:System.Windows.Controls.ListBox> elements in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="fb9e7-106">Každý <xref:System.Windows.Controls.ListBox> představuje možných hodnot <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnosti <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="fb9e7-106">Each <xref:System.Windows.Controls.ListBox> represents the possible values of the <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> properties of a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="fb9e7-107">Když uživatel vybere hodnotu v některém z <xref:System.Windows.Controls.ListBox> elementy, přidružené vlastnosti <xref:System.Windows.Controls.StackPanel> a jeho podřízené <xref:System.Windows.Controls.Button> elementy změnit.</span><span class="sxs-lookup"><span data-stu-id="fb9e7-107">When a user selects a value in any of the <xref:System.Windows.Controls.ListBox> elements, the associated property of the <xref:System.Windows.Controls.StackPanel> and its child <xref:System.Windows.Controls.Button> elements change.</span></span>  
  
 [!code-xaml[StackPanelIntroSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="fb9e7-108">Následující soubor kódu definuje změny k událostem, které jsou přidružené <xref:System.Windows.Controls.ListBox> výběr změny.</span><span class="sxs-lookup"><span data-stu-id="fb9e7-108">The following code-behind file defines the changes to the events that are associated with the <xref:System.Windows.Controls.ListBox> selection changes.</span></span> <span data-ttu-id="fb9e7-109"><xref:System.Windows.Controls.StackPanel>je identifikována <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span><span class="sxs-lookup"><span data-stu-id="fb9e7-109"><xref:System.Windows.Controls.StackPanel> is identified by the <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span></span>  
  
 [!code-csharp[StackPanelIntroSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="fb9e7-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb9e7-110">See Also</span></span>  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 [<span data-ttu-id="fb9e7-111">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="fb9e7-111">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
