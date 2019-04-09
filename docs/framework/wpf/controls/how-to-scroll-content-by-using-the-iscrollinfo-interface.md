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
ms.openlocfilehash: 6ebd8268e1358b45709885c07e6b096d5f806ebb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098543"
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
- [– postupy](scrollviewer-how-to-topics.md)
- [Přehled panelů](panels-overview.md)
