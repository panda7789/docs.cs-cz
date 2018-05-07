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
ms.openlocfilehash: b4da666934be7dd182838d870e54e496b2646901
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a>Postupy: Použití metod pro posunutí obsahu prvku ScrollViewer
Tento příklad ukazuje, jak používat posouvání metody třídy <xref:System.Windows.Controls.ScrollViewer> elementu. Tyto metody poskytují přírůstkové posouvání obsahu, buď čára, nebo podle stránky, <xref:System.Windows.Controls.ScrollViewer>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Windows.Controls.ScrollViewer> s názvem `sv1`, který je hostitelem podřízenou <xref:System.Windows.Controls.TextBlock> elementu. Protože <xref:System.Windows.Controls.TextBlock> je větší než nadřazená <xref:System.Windows.Controls.ScrollViewer>, chcete-li povolit procházení se zobrazí posuvníky. <xref:System.Windows.Controls.Button> prvky, které představují různé posouvání metody jsou ukotven na levé straně v samostatném <xref:System.Windows.Controls.StackPanel>. Každý <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru volá související vlastní metodu, která řídí chování posouvání v <xref:System.Windows.Controls.ScrollViewer>.  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 Následující příklad používá <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> a <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> metody.  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.StackPanel>
