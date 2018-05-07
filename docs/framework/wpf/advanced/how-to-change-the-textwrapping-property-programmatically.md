---
title: 'Postupy: Změna vlastnosti TextWrapping z programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
ms.openlocfilehash: 1b0f039f0484d1d1e73c3c12af06e0faffbce1cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>Postupy: Změna vlastnosti TextWrapping z programu
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak změnit hodnotu <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> vlastnost prostřednictvím kódu programu.  
  
 Tři <xref:System.Windows.Controls.Button> elementy jsou umístěny v rámci <xref:System.Windows.Controls.StackPanel> element v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Každý <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí pro <xref:System.Windows.Controls.Button> odpovídá obslužnou rutinu v kódu. Obslužné rutiny událostí používají stejný název jako <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> hodnotu, použijí se na `txt2` při kliknutí na tlačítko. Navíc text v `txt1` ( <xref:System.Windows.Controls.TextBlock> to není znázorněné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) se aktualizuje, aby odrážely změny ve vlastnosti.  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>  
 <xref:System.Windows.TextWrapping>
