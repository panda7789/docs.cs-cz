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
ms.openlocfilehash: 966e3adbcb57c30a55d606f6d6b8b51523ee30ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553764"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a><span data-ttu-id="d955c-102">Postupy: Použití kontroly pravopisu s místní nabídkou</span><span class="sxs-lookup"><span data-stu-id="d955c-102">How to: Use Spell Checking with a Context Menu</span></span>
<span data-ttu-id="d955c-103">Ve výchozím nastavení, když povolíte v ovládacím prvku úprav kontrolu pravopisu jako <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox>, získat volby kontrola pravopisu v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="d955c-103">By default, when you enable spell checking in an editing control like <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox>, you get spell-checking choices in the context menu.</span></span> <span data-ttu-id="d955c-104">Například pokud uživatelé klikněte pravým tlačítkem chybně, získají sadu pravopis návrhy či možnost **ignorovat všechny**.</span><span class="sxs-lookup"><span data-stu-id="d955c-104">For example, when users right-click a misspelled word, they get a set of spelling suggestions or the option to **Ignore All**.</span></span> <span data-ttu-id="d955c-105">Ale když můžete přepsat výchozí místní nabídku s vlastními vlastní kontextové nabídky, tato funkce dojde ke ztrátě a budete muset napsat kód pro znovu povolit funkci Kontrola pravopisu v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="d955c-105">However, when you override the default context menu with your own custom context menu, this functionality is lost, and you need to write code to reenable the spell-checking feature in the context menu.</span></span> <span data-ttu-id="d955c-106">Následující příklad ukazuje, jak povolit na <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d955c-106">The following example shows how to enable this on a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d955c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d955c-107">Example</span></span>  
 <span data-ttu-id="d955c-108">Následující příklad ukazuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] vytvářející <xref:System.Windows.Controls.TextBox> s některé události, které se používají k implementaci v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="d955c-108">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that creates a <xref:System.Windows.Controls.TextBox> with some events that are used to implement the context menu.</span></span>  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="d955c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d955c-109">Example</span></span>  
 <span data-ttu-id="d955c-110">Následující příklad ukazuje kód, který implementuje v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="d955c-110">The following example shows the code that implements the context menu.</span></span>  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 <span data-ttu-id="d955c-111">Kód použitý pro to s <xref:System.Windows.Controls.RichTextBox> je podobný.</span><span class="sxs-lookup"><span data-stu-id="d955c-111">The code used for doing this with a <xref:System.Windows.Controls.RichTextBox> is similar.</span></span> <span data-ttu-id="d955c-112">Hlavní rozdíl je v parametru předaný `GetSpellingError` metoda.</span><span class="sxs-lookup"><span data-stu-id="d955c-112">The main difference is in the parameter passed to the `GetSpellingError` method.</span></span> <span data-ttu-id="d955c-113">Pro <xref:System.Windows.Controls.TextBox>, předat celočíselný index pozice pomocí kurzoru:</span><span class="sxs-lookup"><span data-stu-id="d955c-113">For a <xref:System.Windows.Controls.TextBox>, pass the integer index of the caret position:</span></span>  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 <span data-ttu-id="d955c-114">Pro <xref:System.Windows.Controls.RichTextBox>, předat <xref:System.Windows.Documents.TextPointer> určující pozici pomocí kurzoru:</span><span class="sxs-lookup"><span data-stu-id="d955c-114">For a <xref:System.Windows.Controls.RichTextBox>, pass the <xref:System.Windows.Documents.TextPointer> that specifies the caret position:</span></span>  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a><span data-ttu-id="d955c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d955c-115">See Also</span></span>  
 [<span data-ttu-id="d955c-116">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="d955c-116">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="d955c-117">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="d955c-117">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="d955c-118">Povolení kontroly pravopisu v ovládacím prvku pro úpravy textu</span><span class="sxs-lookup"><span data-stu-id="d955c-118">Enable Spell Checking in a Text Editing Control</span></span>](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)  
 [<span data-ttu-id="d955c-119">Použití vlastní místní nabídky s prvkem TextBox</span><span class="sxs-lookup"><span data-stu-id="d955c-119">Use a Custom Context Menu with a TextBox</span></span>](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)
