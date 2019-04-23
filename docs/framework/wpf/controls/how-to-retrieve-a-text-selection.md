---
title: 'Postupy: Načtení výběru textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: b7f0b9ee02a7ace717787fc8eeb6e15649829a49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224582"
---
# <a name="how-to-retrieve-a-text-selection"></a>Postupy: Načtení výběru textu
Tento příklad ukazuje jeden ze způsobů použití <xref:System.Windows.Controls.TextBox.SelectedText%2A> vlastnost pro načtení textu, který uživatel vybral v <xref:System.Windows.Controls.TextBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad ukazuje definici <xref:System.Windows.Controls.TextBox> ovládací prvek, který obsahuje text, který chcete vybrat, a <xref:System.Windows.Controls.Button> ovládací prvek se zadaným <xref:System.Windows.Controls.Button.OnClick%2A> metody.  
  
 V tomto příkladu tlačítko s přidruženou <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události se používá k načtení výběru textu. Když uživatel klikne na tlačítko <xref:System.Windows.Controls.Button.OnClick%2A> metoda zkopíruje vybraný text do textového pole na řetězec. Zvláštní okolnosti, které výběr textu je načten (kliknutí na tlačítko), stejně jako akci prováděnou s výběr (text výběr se kopíruje do řetězce), lze snadno upravit tak, aby vyhovovaly širokou škálu scénářů.  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a>Příklad  
 Následující C# ukazuje příklad <xref:System.Windows.Controls.Button.OnClick%2A> obslužné rutiny události pro tlačítko definované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro účely tohoto příkladu.  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a>Viz také:

- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
