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
ms.openlocfilehash: 145c58064b8557f9cb4730ec9272c354c7aa9c1b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378975"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>Postupy: Posunutí obsahu použitím rozhraní IScrollInfo
Tento příklad ukazuje, jak posunutí obsahu použitím <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje funkce <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní. V příkladu se vytvoří <xref:System.Windows.Controls.StackPanel> prvek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , která je vnořená v nadřazeném prvku <xref:System.Windows.Controls.ScrollViewer>. Podřízené prvky <xref:System.Windows.Controls.StackPanel> posunout logicky pomocí metody určené <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní a přetypování na instanci <xref:System.Windows.Controls.StackPanel> (`sp1`) v kódu.  
  
 [!code-xaml[IScrollInfoMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 Každý <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru aktivuje přidruženou vlastní metodu, která řídí chování posouvání v <xref:System.Windows.Controls.StackPanel>. Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> a <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> metod; také obecně ukazuje způsob použití všech metod umístění, která <xref:System.Windows.Controls.Primitives.IScrollInfo> třída definuje.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [ScrollViewer – přehled](scrollviewer-overview.md)
- [Témata s postupy](scrollviewer-how-to-topics.md)
- [Přehled panelu](panels-overview.md)
