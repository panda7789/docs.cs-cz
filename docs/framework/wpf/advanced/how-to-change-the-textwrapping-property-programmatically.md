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
ms.openlocfilehash: 70dc73fe16ebb98e466c4363e5ac26562329dcd4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362263"
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>Postupy: Změna vlastnosti TextWrapping z programu
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak změnit hodnotu <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> vlastnost prostřednictvím kódu programu.  
  
 Tři <xref:System.Windows.Controls.Button> prvky jsou umístěny v rámci <xref:System.Windows.Controls.StackPanel> prvek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Každý <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí pro <xref:System.Windows.Controls.Button> odpovídá obslužné rutiny události v kódu. Obslužné rutiny událostí použijte stejný název jako <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> hodnota, použijí se na `txt2` po kliknutí na tlačítko. Navíc textu v `txt1` ( <xref:System.Windows.Controls.TextBlock> to není znázorněné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) aktualizován, aby odrážel změnu v hodnotě vlastnosti.  
  
 [!code-xaml[TextWrapProperty#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>
- <xref:System.Windows.TextWrapping>
