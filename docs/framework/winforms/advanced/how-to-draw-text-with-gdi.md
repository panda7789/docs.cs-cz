---
title: 'Postupy: Kreslení textu pomocí GDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3d5b79e82185c044314ff8807b86835ef6a87c45
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505904"
---
# <a name="how-to-draw-text-with-gdi"></a>Postupy: Kreslení textu pomocí GDI
S <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metodu <xref:System.Windows.Forms.TextRenderer> třídy, funkce se zpřístupní GDI pro kreslení textu na formulář nebo ovládací prvek. Vykreslování textu GDI obvykle nabízí lepší výkon a přesnější text měření než rozhraní GDI +.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> třídy nejsou podporovány pro tisk. Při tisku, vždy používejte <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak na více řádků v rámci obdélníku pomocí vykreslení textu <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 K vykreslení textu pomocí <xref:System.Windows.Forms.TextRenderer> třídy, je nutné <xref:System.Drawing.IDeviceContext>, například <xref:System.Drawing.Graphics> a <xref:System.Drawing.Font>, umístění pro kreslení textu a barvy, ve kterém má být vykreslena. Volitelně můžete zadat formátování s použitím textu <xref:System.Windows.Forms.TextFormatFlags> výčtu.  
  
 Další informace o získání <xref:System.Drawing.Graphics>, naleznete v tématu [jak: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md). Další informace o vytváření <xref:System.Drawing.Font>, naleznete v tématu [jak: Vytváření rodin písem a písem](how-to-construct-font-families-and-fonts.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu kódu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [Použití písem a textu](using-fonts-and-text.md)
