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
ms.openlocfilehash: 6b25c555d5e6cac93b2e1518b25e7880ab77c866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552009"
---
# <a name="how-to-retrieve-a-text-selection"></a>Postupy: Načtení výběru textu
Tento příklad ukazuje jeden ze způsobů použití <xref:System.Windows.Controls.TextBox.SelectedText%2A> vlastnost k načtení textu, který uživatel vybral v <xref:System.Windows.Controls.TextBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad zobrazuje definici <xref:System.Windows.Controls.TextBox> ovládací prvek, který obsahuje chcete vybrat, text a <xref:System.Windows.Controls.Button> ovládací prvek se zadaným <xref:System.Windows.Controls.Button.OnClick%2A> metoda.  
  
 V tomto příkladu tlačítko s přiřazený <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události se používá k načtení výběr textu. Když uživatel klikne na tlačítko <xref:System.Windows.Controls.Button.OnClick%2A> metoda zkopíruje všechny vybraný text do textového pole na řetězec. Zvláštní okolnosti, které výběr textu je načíst (kliknutím na tlačítko), stejně jako akce s výběr (kopírování výběr textu na řetězec), můžete snadno upravit tak, aby dokázala pojmout širokou škálu scénářů.  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a>Příklad  
 C# ukazuje následující příklad <xref:System.Windows.Controls.Button.OnClick%2A> obslužné rutiny události pro tlačítko definovaný v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v tomto příkladu.  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a>Viz také  
 [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
