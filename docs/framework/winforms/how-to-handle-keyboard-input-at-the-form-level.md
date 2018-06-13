---
title: 'Postupy: Obsluha vstupu klávesnice na úrovni formuláře'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: 4913d68d7a7cced75f87d80a3bf4d099ae68b3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541093"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a>Postupy: Obsluha vstupu klávesnice na úrovni formuláře
Windows Forms poskytuje možnost pro zpracování zprávy klávesnice na úrovni formuláře před zprávy dosáhnout ovládacího prvku. Toto téma ukazuje, jak k provedení této úlohy.  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a>Zpracování zpráv klávesnice na úrovni formuláře  
  
-   Zpracování <xref:System.Windows.Forms.Control.KeyPress> nebo <xref:System.Windows.Forms.Control.KeyDown> události formulář spuštění a nastavte <xref:System.Windows.Forms.Form.KeyPreview%2A> vlastnost formuláře `true` tak, aby přijímá zprávy klávesnice formuláře než dosáhnou všechny ovládací prvky na formuláři. Následující kód například zpracovává <xref:System.Windows.Forms.Control.KeyPress> událostí zjišťuje všechny číslicemi a využívání '1', '4' a '7'.  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu se bude celá aplikace pro výše uvedeném příkladu. Zahrnuje aplikace <xref:System.Windows.Forms.TextBox> společně s několik dalších ovládacích prvků, které umožňují přesunout fokus z <xref:System.Windows.Forms.TextBox>. <xref:System.Windows.Forms.Control.KeyPress> Událostí hlavních <xref:System.Windows.Forms.Form> využívá '1', '4' a '7' a <xref:System.Windows.Forms.Control.KeyPress> události <xref:System.Windows.Forms.TextBox> využívá '2', '5' a '8' při zobrazování zbývající klíče. Porovnání <xref:System.Windows.Forms.MessageBox> výstup po stisknutí klávesy číslo klíče chvíli <xref:System.Windows.Forms.TextBox> má právě fokus s <xref:System.Windows.Forms.MessageBox> výstup po stisknutí kláves číslo při zaměřuje se na některý z dalších ovládacích prvků.  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Vstup z klávesnice v aplikaci Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
