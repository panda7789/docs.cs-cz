---
title: 'Postupy: Kreslení textu na formuláři Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: ae7749deedba03f0a63bb74099d071d5da4fe27e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172975"
---
# <a name="how-to-draw-text-on-a-windows-form"></a>Postupy: Kreslení textu na formuláři Windows
Následující příklad kódu ukazuje, jak používat <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> k vykreslení textu ve formuláři. Alternativně můžete použít <xref:System.Windows.Forms.TextRenderer> pro kreslení textu ve formuláři. Další informace najdete v tématu [jak: Kreslení textu pomocí GDI](how-to-draw-text-with-gdi.md).  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Nelze volat <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Windows.Forms.Form.Load> obslužné rutiny události. Vykreslený obsah aktivním, pokud je velikost nebo zakryto jiný formulář. formuláře. Chcete-li obsah automaticky repaint, by měly přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Arial písmo není nainstalováno.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Windows.Forms.TextRenderer.DrawText%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.TextFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Postupy: Kreslení textu pomocí GDI](how-to-draw-text-with-gdi.md)
