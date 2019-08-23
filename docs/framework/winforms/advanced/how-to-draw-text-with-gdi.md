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
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956545"
---
# <a name="how-to-draw-text-with-gdi"></a>Postupy: Kreslení textu pomocí GDI
<xref:System.Windows.Forms.TextRenderer.DrawText%2A> Pomocí metody<xref:System.Windows.Forms.TextRenderer> ve třídě můžete získat přístup k funkcím GDI pro vykreslování textu ve formuláři nebo ovládacím prvku. Vykreslování textu GDI obvykle nabízí lepší výkon a přesnější měření textu než GDI+.  
  
> [!NOTE]
> <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody<xref:System.Windows.Forms.TextRenderer> třídy nejsou podporovány pro tisk. Při tisku vždy používejte <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak kreslit text na více řádcích v rámci obdélníku pomocí <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Chcete-li vykreslit <xref:System.Windows.Forms.TextRenderer> text s třídou, <xref:System.Drawing.IDeviceContext>budete potřebovat, <xref:System.Drawing.Font>například <xref:System.Drawing.Graphics> , a, umístění pro vykreslení textu a barvu, ve které má být vykreslen. Volitelně můžete určit formátování textu pomocí <xref:System.Windows.Forms.TextFormatFlags> výčtu.  
  
 Další informace o tom <xref:System.Drawing.Graphics>, jak získat, najdete v tématu [How to: Vytvoření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md). Další informace o konstrukci a <xref:System.Drawing.Font>naleznete v tématu [How to: Sestavte rodiny písem](how-to-construct-font-families-and-fonts.md)a písma.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad kódu je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, <xref:System.Windows.Forms.PaintEventHandler>který je parametrem.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [Použití písem a textu](using-fonts-and-text.md)
