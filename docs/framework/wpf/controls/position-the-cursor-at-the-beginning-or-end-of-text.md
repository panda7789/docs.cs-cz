---
title: 'Postupy: Umístění kurzoru na začátek nebo konec textu v ovládacím prvku TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: 3d7da5daf09e06938b8366e0f5f98a599cae4571
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186222"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="ba1b0-102">Postupy: Umístění kurzoru na začátek nebo konec textu v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="ba1b0-102">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="ba1b0-103">Tento příklad ukazuje, jak umístění kurzoru na začátku nebo konci textového obsahu <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba1b0-103">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba1b0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba1b0-104">Example</span></span>  
 <span data-ttu-id="ba1b0-105">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód popisuje <xref:System.Windows.Controls.TextBox> řídit a přiřadí ji názvu.</span><span class="sxs-lookup"><span data-stu-id="ba1b0-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="ba1b0-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba1b0-106">Example</span></span>  
 <span data-ttu-id="ba1b0-107">Umístěte kurzor na začátek obsahu <xref:System.Windows.Controls.TextBox> řídit, zavolejte <xref:System.Windows.Controls.TextBox.Select%2A> metoda a zadejte výběr start pozice 0 a výběr délku 0.</span><span class="sxs-lookup"><span data-stu-id="ba1b0-107">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="ba1b0-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba1b0-108">Example</span></span>  
 <span data-ttu-id="ba1b0-109">Do umístění kurzoru na konec obsahu <xref:System.Windows.Controls.TextBox> řídit, zavolejte <xref:System.Windows.Controls.TextBox.Select%2A> metoda a zadat počáteční pozice výběru rovna délku obsahu textu a výběr délku 0.</span><span class="sxs-lookup"><span data-stu-id="ba1b0-109">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="ba1b0-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba1b0-110">See also</span></span>

- [<span data-ttu-id="ba1b0-111">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="ba1b0-111">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="ba1b0-112">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="ba1b0-112">RichTextBox Overview</span></span>](richtextbox-overview.md)
