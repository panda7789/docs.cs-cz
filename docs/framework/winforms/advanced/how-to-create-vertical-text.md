---
title: 'Postupy: Vytvoření svislého textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182564"
---
# <a name="how-to-create-vertical-text"></a>Postupy: Vytvoření svislého textu
Pomocí objektu <xref:System.Drawing.StringFormat> můžete určit, že text bude nakreslen svisle, nikoli vodorovně.  
  
## <a name="example"></a>Příklad  
 Následující příklad přiřadí <xref:System.Drawing.StringFormatFlags.DirectionVertical> hodnotu <xref:System.Drawing.StringFormat.FormatFlags%2A> vlastnosti <xref:System.Drawing.StringFormat> objektu. Tento <xref:System.Drawing.StringFormat> objekt je <xref:System.Drawing.Graphics.DrawString%2A> předán metodě třídy. <xref:System.Drawing.Graphics> Hodnota <xref:System.Drawing.StringFormatFlags.DirectionVertical> je členem výčtu. <xref:System.Drawing.StringFormatFlags>  
  
 Následující obrázek znázorňuje svislý text:
  
 ![Grafika znázorněná text svislých písem.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Předchozí příklad je určen pro použití s windows <xref:System.Windows.Forms.PaintEventArgs> `e` forms a vyžaduje <xref:System.Windows.Forms.PaintEventHandler>, což je parametr .  
  
## <a name="see-also"></a>Viz také

- [Postupy: Kreslení textu pomocí GDI](how-to-draw-text-with-gdi.md)
