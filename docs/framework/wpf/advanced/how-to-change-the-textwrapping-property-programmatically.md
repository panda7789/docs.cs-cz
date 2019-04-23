---
title: 'Postupy: Změna vlastnosti TextWrapping pomocí programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
ms.openlocfilehash: 21ca31d24121492fe6927cd533d5b3c0785b5a28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974997"
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>Postupy: Změna vlastnosti TextWrapping pomocí programu
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak změnit hodnotu <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> vlastnost prostřednictvím kódu programu.  
  
 Tři <xref:System.Windows.Controls.Button> prvky jsou umístěny v rámci <xref:System.Windows.Controls.StackPanel> prvek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Každý <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí pro <xref:System.Windows.Controls.Button> odpovídá obslužné rutiny události v kódu. Obslužné rutiny událostí použijte stejný název jako <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> hodnota, použijí se na `txt2` po kliknutí na tlačítko. Navíc textu v `txt1` ( <xref:System.Windows.Controls.TextBlock> to není znázorněné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) aktualizován, aby odrážel změnu v hodnotě vlastnosti.  
  
 [!code-xaml[TextWrapProperty#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>
- <xref:System.Windows.TextWrapping>
