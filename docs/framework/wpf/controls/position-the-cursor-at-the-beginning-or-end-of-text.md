---
title: "Postupy: Umístění kurzoru na začátku a konci textu v ovládacím prvku TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0efa81a9606235b214f30a8c6febb94ea2968714
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="43c0f-102">Postupy: Umístění kurzoru na začátku a konci textu v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="43c0f-102">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="43c0f-103">Tento příklad ukazuje, jak umístěte kurzor na začátku nebo na konci textového obsahu <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="43c0f-103">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43c0f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="43c0f-104">Example</span></span>  
 <span data-ttu-id="43c0f-105">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód popisuje <xref:System.Windows.Controls.TextBox> řízení a přiřadí ji název.</span><span class="sxs-lookup"><span data-stu-id="43c0f-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="43c0f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="43c0f-106">Example</span></span>  
 <span data-ttu-id="43c0f-107">Umístěte kurzor na začátek obsah <xref:System.Windows.Controls.TextBox> řídit, volejte <xref:System.Windows.Controls.TextBox.Select%2A> metoda a zadejte výběr spustit pozice 0 a výběr délku 0.</span><span class="sxs-lookup"><span data-stu-id="43c0f-107">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="43c0f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="43c0f-108">Example</span></span>  
 <span data-ttu-id="43c0f-109">Umístěte kurzor na konci obsahu <xref:System.Windows.Controls.TextBox> řídit, volejte <xref:System.Windows.Controls.TextBox.Select%2A> metoda a zadejte počáteční pozice výběru rovna délce textu obsahu a výběr délku 0.</span><span class="sxs-lookup"><span data-stu-id="43c0f-109">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="43c0f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="43c0f-110">See Also</span></span>  
 [<span data-ttu-id="43c0f-111">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="43c0f-111">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="43c0f-112">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="43c0f-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
