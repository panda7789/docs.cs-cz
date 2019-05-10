---
title: 'Postupy: Definování pořadí vykreslování ukotvených ovládacích prvků ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], specifying z-order
- z-order
ms.assetid: 8b595429-ba9f-46af-9c55-3d5cc53f7fff
ms.openlocfilehash: b7643c9599ceeba08cbe9f5580739043f6d89edc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666329"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a>Postupy: Definování pořadí vykreslování ukotvených ovládacích prvků ToolStrip
Na pozici <xref:System.Windows.Forms.ToolStrip> ovládacího prvku správně s ukotvení, je třeba umístit ovládací prvek správně v pořadí vykreslování formuláře.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak uspořádat <xref:System.Windows.Forms.ToolStrip> ovládacího prvku a ukotvených <xref:System.Windows.Forms.MenuStrip> ovládacího prvku tak, že zadáte pořadí vykreslování.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 Pořadí je určen podle pořadí, ve kterém <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.MenuStrip>  
  
 ovládací prvky jsou přidány do formuláře <xref:System.Windows.Forms.Control.Controls%2A> kolekce.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 Pořadí těchto volání <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metody a zobrazení vliv na rozložení.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>
- <xref:System.Windows.Forms.Control.Controls%2A>
- <xref:System.Windows.Forms.Control.Dock%2A>
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
