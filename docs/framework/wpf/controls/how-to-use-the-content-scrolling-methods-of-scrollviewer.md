---
title: 'Postupy: Použití metod pro posunutí obsahu prvku ScrollViewer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: e81c63de16d09de8435d5ec49a013bf8dc5927cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142152"
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a>Postupy: Použití metod pro posunutí obsahu prvku ScrollViewer
Tento příklad ukazuje způsob použití metod pro posunutí posouvání <xref:System.Windows.Controls.ScrollViewer> elementu. Tyto metody poskytují přírůstkové posouvání obsahu, řádek nebo stránky, v <xref:System.Windows.Controls.ScrollViewer>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Windows.Controls.ScrollViewer> s názvem `sv1`, který je hostitelem podřízený <xref:System.Windows.Controls.TextBlock> elementu. Vzhledem k tomu, <xref:System.Windows.Controls.TextBlock> je větší, než může nadřazený <xref:System.Windows.Controls.ScrollViewer>, zobrazí posuvníky, chcete-li povolit posouvání. <xref:System.Windows.Controls.Button> prvky, které představují různé metody posunování jsou ukotveny na levé straně v samostatném <xref:System.Windows.Controls.StackPanel>. Každý <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor volá související vlastní metodu, která řídí chování posouvání v <xref:System.Windows.Controls.ScrollViewer>.  
  
 [!code-xaml[ScrollViewerMethods#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 V následujícím příkladu <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> a <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> metody.  
  
 [!code-csharp[ScrollViewerMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.StackPanel>
