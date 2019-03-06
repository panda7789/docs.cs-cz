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
ms.openlocfilehash: 38d41aa6710fd13ffd2a5d13a6900a1a05303f35
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377804"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a><span data-ttu-id="ff5b6-102">Postupy: Použití kontroly pravopisu s místní nabídkou</span><span class="sxs-lookup"><span data-stu-id="ff5b6-102">How to: Use Spell Checking with a Context Menu</span></span>
<span data-ttu-id="ff5b6-103">Ve výchozím nastavení, jako jsou při povolení kontroly pravopisu v ovládací prvek úprav <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox>, získáte možnosti kontroly pravopisu v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="ff5b6-103">By default, when you enable spell checking in an editing control like <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox>, you get spell-checking choices in the context menu.</span></span> <span data-ttu-id="ff5b6-104">Například když uživatelé klikněte pravým tlačítkem na chybně napsaná slova, dostanou sadu návrhy pravopisu nebo možnost **Přeskakovat vše**.</span><span class="sxs-lookup"><span data-stu-id="ff5b6-104">For example, when users right-click a misspelled word, they get a set of spelling suggestions or the option to **Ignore All**.</span></span> <span data-ttu-id="ff5b6-105">Ale když přepíšete výchozí kontextové nabídky s vlastním vlastní místní nabídky, této funkce dojde ke ztrátě a je nutné napsat kód, který znovu povolit funkci kontrolu pravopisu v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="ff5b6-105">However, when you override the default context menu with your own custom context menu, this functionality is lost, and you need to write code to reenable the spell-checking feature in the context menu.</span></span> <span data-ttu-id="ff5b6-106">Následující příklad ukazuje, jak ji povolit u <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ff5b6-106">The following example shows how to enable this on a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff5b6-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff5b6-107">Example</span></span>  
 <span data-ttu-id="ff5b6-108">Následující příklad ukazuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , který vytváří <xref:System.Windows.Controls.TextBox> s některé události, které se používají k implementaci v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="ff5b6-108">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that creates a <xref:System.Windows.Controls.TextBox> with some events that are used to implement the context menu.</span></span>  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="ff5b6-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff5b6-109">Example</span></span>  
 <span data-ttu-id="ff5b6-110">Následující příklad ukazuje kód, který implementuje v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="ff5b6-110">The following example shows the code that implements the context menu.</span></span>  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 <span data-ttu-id="ff5b6-111">Kód používá tato funkce se <xref:System.Windows.Controls.RichTextBox> je podobná.</span><span class="sxs-lookup"><span data-stu-id="ff5b6-111">The code used for doing this with a <xref:System.Windows.Controls.RichTextBox> is similar.</span></span> <span data-ttu-id="ff5b6-112">Hlavní rozdíl je v parametr předaný `GetSpellingError` metody.</span><span class="sxs-lookup"><span data-stu-id="ff5b6-112">The main difference is in the parameter passed to the `GetSpellingError` method.</span></span> <span data-ttu-id="ff5b6-113">Pro <xref:System.Windows.Controls.TextBox>, předejte celočíselný index pozice blikajícího kurzoru:</span><span class="sxs-lookup"><span data-stu-id="ff5b6-113">For a <xref:System.Windows.Controls.TextBox>, pass the integer index of the caret position:</span></span>  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 <span data-ttu-id="ff5b6-114">Pro <xref:System.Windows.Controls.RichTextBox>, předejte <xref:System.Windows.Documents.TextPointer> určující pozici blikajícího kurzoru:</span><span class="sxs-lookup"><span data-stu-id="ff5b6-114">For a <xref:System.Windows.Controls.RichTextBox>, pass the <xref:System.Windows.Documents.TextPointer> that specifies the caret position:</span></span>  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a><span data-ttu-id="ff5b6-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff5b6-115">See also</span></span>
- [<span data-ttu-id="ff5b6-116">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="ff5b6-116">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="ff5b6-117">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="ff5b6-117">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="ff5b6-118">Povolení kontroly pravopisu v ovládacím prvku pro úpravy textu</span><span class="sxs-lookup"><span data-stu-id="ff5b6-118">Enable Spell Checking in a Text Editing Control</span></span>](how-to-enable-spell-checking-in-a-text-editing-control.md)
- [<span data-ttu-id="ff5b6-119">Použití vlastní místní nabídky s prvkem TextBox</span><span class="sxs-lookup"><span data-stu-id="ff5b6-119">Use a Custom Context Menu with a TextBox</span></span>](how-to-use-a-custom-context-menu-with-a-textbox.md)
