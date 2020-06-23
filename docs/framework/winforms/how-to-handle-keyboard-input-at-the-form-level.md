---
title: 'Postupy: Obsluha vstupu klávesnice na úrovni formuláře'
description: Naučte se, jak zpracovat vstup z klávesnice pro model Windows Forms na úrovni formuláře, než se zprávy dostanou k ovládacímu prvku.
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
ms.openlocfilehash: 6f0695b6f665a613e0e4e001a4f9bbfc09dd45ed
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904153"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a>Postupy: Obsluha vstupu klávesnice na úrovni formuláře
Model Windows Forms poskytuje možnost zpracovávat zprávy klávesnice na úrovni formuláře před tím, než se zprávy dostanou k ovládacímu prvku. V tomto tématu se dozvíte, jak tento úkol provést.  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a>Zpracování zprávy klávesnice na úrovni formuláře  
  
- Zpracujte <xref:System.Windows.Forms.Control.KeyPress> událost nebo <xref:System.Windows.Forms.Control.KeyDown> formuláře po spuštění a nastavte <xref:System.Windows.Forms.Form.KeyPreview%2A> vlastnost formuláře tak, aby byla `true` zpráva klávesnicí přijímána formulářem předtím, než dosáhnou všech ovládacích prvků ve formuláři. Následující příklad kódu zpracovává <xref:System.Windows.Forms.Control.KeyPress> událost tím, že detekuje všechny klíče čísel a spotřebovává "1", "4" a "7".  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je celá aplikace pro výše uvedený příklad. Aplikace zahrnuje <xref:System.Windows.Forms.TextBox> spolu s několika dalšími ovládacími prvky, které umožňují přesunout fokus z <xref:System.Windows.Forms.TextBox> . <xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.Form> Při zobrazení zbývajících klíčů událost Main spotřebuje "1", "4" a "7" a <xref:System.Windows.Forms.Control.KeyPress> událost " <xref:System.Windows.Forms.TextBox> 2", "5" a "8". Porovnejte <xref:System.Windows.Forms.MessageBox> výstup, když stisknete klávesu s číslem, zatímco při <xref:System.Windows.Forms.TextBox> stisknutí klávesy s číslem se zaměříte na <xref:System.Windows.Forms.MessageBox> výstup, zatímco se fokus nachází na jednom z dalších ovládacích prvků.  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také

- [Vstup z klávesnice ve formulářové aplikaci Windows](keyboard-input-in-a-windows-forms-application.md)
