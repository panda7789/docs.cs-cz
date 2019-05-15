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
ms.openlocfilehash: c10852273eeb3caea01f448e4cbef571f20769bd
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592042"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a>Postupy: Obsluha vstupu klávesnice na úrovni formuláře
Windows Forms poskytuje možnost zpracovávat zprávy týkající se klávesnice na úrovni formuláře před mailů ovládacího prvku. Toto téma ukazuje, jak tento úkol provést.  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a>Aby se zpracovala zpráva klávesnice na úrovni formuláře  
  
- Zpracování <xref:System.Windows.Forms.Control.KeyPress> nebo <xref:System.Windows.Forms.Control.KeyDown> událost úvodní formulář a nastavte <xref:System.Windows.Forms.Form.KeyPreview%2A> vlastnost formuláře `true` tak, aby klávesnice zprávy jsou přijímány formuláři dřív, než dorazí všechny ovládací prvky ve formuláři. Následující kód například zpracovává <xref:System.Windows.Forms.Control.KeyPress> události zjišťuje všechny číslicemi a využívání '1', '4' a '7'.  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je celá aplikace výše uvedeného příkladu. Zahrnuje aplikace <xref:System.Windows.Forms.TextBox> společně s několika další ovládací prvky, které umožňují přesunout zaměření <xref:System.Windows.Forms.TextBox>. <xref:System.Windows.Forms.Control.KeyPress> Událostí hlavním <xref:System.Windows.Forms.Form> využívá '1', '4' a '7' a <xref:System.Windows.Forms.Control.KeyPress> událost <xref:System.Windows.Forms.TextBox> využívá '2', '5' a '8' při zobrazování zbývající klíče. Porovnání <xref:System.Windows.Forms.MessageBox> výstup, když stisknete klávesu chvíli počet klíčů <xref:System.Windows.Forms.TextBox> má fokus se <xref:System.Windows.Forms.MessageBox> výstup po stisknutí kláves čísel při, zaměřuje se na jeden z jiných ovládacích prvků.  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- [Vstup z klávesnice v aplikaci Windows Forms](keyboard-input-in-a-windows-forms-application.md)
