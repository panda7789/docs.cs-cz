---
title: 'Postupy: Povolení kontroly pravopisu v ovládacím prvku pro úpravy textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- spellchecking [WPF]
- real-time spellchecking
- TextBox control [WPF], real-time spellchecking
- spelling checker [WPF]
- checking spelling [WPF]
ms.assetid: 6f953d2b-67e8-4012-84ce-53c0e958da47
ms.openlocfilehash: 7381bafc349506d89058581e9ed62a4348a72865
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076845"
---
# <a name="how-to-enable-spell-checking-in-a-text-editing-control"></a>Postupy: Povolení kontroly pravopisu v ovládacím prvku pro úpravy textu
Následující příklad ukazuje, jak povolit kontrolu pravopisu v reálném čase <xref:System.Windows.Controls.TextBox> pomocí <xref:System.Windows.Controls.SpellCheck.IsEnabled%2A> vlastnost <xref:System.Windows.Controls.SpellCheck> třídy.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellCheckExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/spellcheckexample.xaml#spellcheckexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_procedural_snip#SpellCheckCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_procedural_snip/CSharp/SpellCheckExample.cs#spellcheckcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_procedural_snip#SpellCheckCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_procedural_snip/visualbasic/spellcheckexample.vb#spellcheckcodeexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [Použití kontroly pravopisu s místní nabídkou](how-to-use-spell-checking-with-a-context-menu.md)
- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
