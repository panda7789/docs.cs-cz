---
title: 'Postupy: Posunutí obsahu použitím rozhraní IScrollInfo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 8154a626c6bf48a59be0540f857c0c51d59a26c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>Postupy: Posunutí obsahu použitím rozhraní IScrollInfo
Tento příklad ukazuje, jak posouvat obsah pomocí <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje funkce <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní. V příkladu se vytváří <xref:System.Windows.Controls.StackPanel> element v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] který vnořen v nadřazené <xref:System.Windows.Controls.ScrollViewer>. Podřízených elementů <xref:System.Windows.Controls.StackPanel> posunout logicky pomocí metody definované <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní a přetypování na instanci <xref:System.Windows.Controls.StackPanel> (`sp1`) v kódu.  
  
 [!code-xaml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 Každý <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aktivuje souboru k přidružené vlastní metodu, která řídí chování posouvání v <xref:System.Windows.Controls.StackPanel>. Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> a <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> metody; také obecně ukazuje, jak použít umísťovací metody, <xref:System.Windows.Controls.Primitives.IScrollInfo> třída definuje.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 <xref:System.Windows.Controls.StackPanel>  
 [ScrollViewer – přehled](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)
