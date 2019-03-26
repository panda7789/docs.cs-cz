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
ms.openlocfilehash: ffd8600c730baca54a9cbd098dd2f37ce5ecb728
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464720"
---
# <a name="how-to-use-antialiasing-with-text"></a>Postupy: Použití vyhlazení s textem
*Vyhlazení* odkazuje na vyhlazování nerovné okraje vykresleného obrázků a textu ke zlepšení jejich vzhled nebo čitelnost. S managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy, můžete vygenerovat vysoce kvalitní antialiased text, jakož i nižší kvality text. Vyšší kvalitu vykreslování obvykle trvá zpracování déle než nižší kvality vykreslování. Chcete-li nastavit úroveň kvality text, nastavte <xref:System.Drawing.Graphics.TextRenderingHint%2A> vlastnost <xref:System.Drawing.Graphics> na jeden z elementů <xref:System.Drawing.Text.TextRenderingHint> výčet  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu kreslení textu pomocí nastavení dvou různých kvality.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 Výstup tohoto ukázkového kódu na následujícím obrázku:  
  
 ![Snímek obrazovky, který zobrazuje text dejte dvě nastavení různou kvalitu.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu kódu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:
- [Použití písem a textu](using-fonts-and-text.md)
