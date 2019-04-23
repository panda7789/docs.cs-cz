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
# <a name="how-to-enable-spell-checking-in-a-text-editing-control"></a><span data-ttu-id="a983d-102">Postupy: Povolení kontroly pravopisu v ovládacím prvku pro úpravy textu</span><span class="sxs-lookup"><span data-stu-id="a983d-102">How to: Enable Spell Checking in a Text Editing Control</span></span>
<span data-ttu-id="a983d-103">Následující příklad ukazuje, jak povolit kontrolu pravopisu v reálném čase <xref:System.Windows.Controls.TextBox> pomocí <xref:System.Windows.Controls.SpellCheck.IsEnabled%2A> vlastnost <xref:System.Windows.Controls.SpellCheck> třídy.</span><span class="sxs-lookup"><span data-stu-id="a983d-103">The following example shows how to enable real-time spell checking in a <xref:System.Windows.Controls.TextBox> by using the <xref:System.Windows.Controls.SpellCheck.IsEnabled%2A> property of the <xref:System.Windows.Controls.SpellCheck> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a983d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a983d-104">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellCheckExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/spellcheckexample.xaml#spellcheckexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_procedural_snip#SpellCheckCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_procedural_snip/CSharp/SpellCheckExample.cs#spellcheckcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_procedural_snip#SpellCheckCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_procedural_snip/visualbasic/spellcheckexample.vb#spellcheckcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a983d-105">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a983d-105">See also</span></span>

- [<span data-ttu-id="a983d-106">Použití kontroly pravopisu s místní nabídkou</span><span class="sxs-lookup"><span data-stu-id="a983d-106">Use Spell Checking with a Context Menu</span></span>](how-to-use-spell-checking-with-a-context-menu.md)
- [<span data-ttu-id="a983d-107">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="a983d-107">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="a983d-108">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="a983d-108">RichTextBox Overview</span></span>](richtextbox-overview.md)
