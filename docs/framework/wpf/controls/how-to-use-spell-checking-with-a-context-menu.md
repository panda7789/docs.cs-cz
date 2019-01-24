---
title: 'Postupy: Použití kontroly pravopisu s místní nabídkou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
ms.openlocfilehash: 2b6790fd4d5d2e322a46bd98ed19e7b88c4923c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713113"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>Postupy: Použití kontroly pravopisu s místní nabídkou
Ve výchozím nastavení, jako jsou při povolení kontroly pravopisu v ovládací prvek úprav <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox>, získáte možnosti kontroly pravopisu v místní nabídce. Například když uživatelé klikněte pravým tlačítkem na chybně napsaná slova, dostanou sadu návrhy pravopisu nebo možnost **Přeskakovat vše**. Ale když přepíšete výchozí kontextové nabídky s vlastním vlastní místní nabídky, této funkce dojde ke ztrátě a je nutné napsat kód, který znovu povolit funkci kontrolu pravopisu v místní nabídce. Následující příklad ukazuje, jak ji povolit u <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , který vytváří <xref:System.Windows.Controls.TextBox> s některé události, které se používají k implementaci v místní nabídce.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kód, který implementuje v místní nabídce.  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 Kód používá tato funkce se <xref:System.Windows.Controls.RichTextBox> je podobná. Hlavní rozdíl je v parametr předaný `GetSpellingError` metody. Pro <xref:System.Windows.Controls.TextBox>, předejte celočíselný index pozice blikajícího kurzoru:  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 Pro <xref:System.Windows.Controls.RichTextBox>, předejte <xref:System.Windows.Documents.TextPointer> určující pozici blikajícího kurzoru:  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>Viz také:
- [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
- [Povolení kontroly pravopisu v ovládacím prvku pro úpravy textu](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)
- [Použití vlastní místní nabídky s prvkem TextBox](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)
