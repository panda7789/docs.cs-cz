---
title: 'Postupy: Umístění kurzoru na začátku a konci textu v ovládacím prvku TextBox'
description: Naučte se umístit kurzor na začátek nebo konec textového obsahu ovládacího prvku TextBox Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: afe8b11d032b5d61fa91cbf324f02cd8415d2ea8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167506"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="d990e-103">Postupy: Umístění kurzoru na začátku a konci textu v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="d990e-103">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="d990e-104">Tento příklad ukazuje, jak umístit kurzor na začátek nebo konec textového obsahu <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d990e-104">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d990e-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d990e-105">Example</span></span>  
 <span data-ttu-id="d990e-106">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód popisuje <xref:System.Windows.Controls.TextBox> ovládací prvek a přiřazuje mu název.</span><span class="sxs-lookup"><span data-stu-id="d990e-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="d990e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d990e-107">Example</span></span>  
 <span data-ttu-id="d990e-108">Chcete-li umístit kurzor na začátek obsahu <xref:System.Windows.Controls.TextBox> ovládacího prvku, zavolejte <xref:System.Windows.Controls.TextBox.Select%2A> metodu a zadejte počáteční pozici výběru 0 a délku výběru 0.</span><span class="sxs-lookup"><span data-stu-id="d990e-108">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="d990e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d990e-109">Example</span></span>  
 <span data-ttu-id="d990e-110">Chcete-li umístit kurzor na konec obsahu <xref:System.Windows.Controls.TextBox> ovládacího prvku, zavolejte <xref:System.Windows.Controls.TextBox.Select%2A> metodu a zadejte počáteční pozici výběru rovnající se délce textového obsahu a délka výběru 0.</span><span class="sxs-lookup"><span data-stu-id="d990e-110">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="d990e-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="d990e-111">See also</span></span>

- [<span data-ttu-id="d990e-112">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="d990e-112">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="d990e-113">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="d990e-113">RichTextBox Overview</span></span>](richtextbox-overview.md)
