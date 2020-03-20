---
title: 'Postupy: Použití vyhlazení s textem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182474"
---
# <a name="how-to-use-antialiasing-with-text"></a>Postupy: Použití vyhlazení s textem
*Vyhlazení* mů e být namátkovat zubaté okraje nakreslené grafiky a textu, aby se zlepšil jejich vzhled nebo čitelnost. Díky spravovaným třídám GDI+ můžete vykreslit vysoce kvalitní vyhlazovaný text a také text nižší kvality. Vykreslování s vyšší kvalitou obvykle trvá déle než vykreslování nižší kvality. Chcete-li nastavit úroveň kvality <xref:System.Drawing.Graphics.TextRenderingHint%2A> textu, <xref:System.Drawing.Graphics> nastavte vlastnost a <xref:System.Drawing.Text.TextRenderingHint> na jeden z prvků výčtu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu nakreslí text se dvěma různými nastaveními kvality.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 Následující obrázek znázorňuje výstup ukázkového kódu:  
  
 ![Snímek obrazovky, který zobrazuje text se dvěma různými nastaveními kvality.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad kódu je určen pro použití s <xref:System.Windows.Forms.PaintEventArgs> `e`windows forms a <xref:System.Windows.Forms.PaintEventHandler>vyžaduje , což je parametr .  
  
## <a name="see-also"></a>Viz také

- [Použití písem a textu](using-fonts-and-text.md)
