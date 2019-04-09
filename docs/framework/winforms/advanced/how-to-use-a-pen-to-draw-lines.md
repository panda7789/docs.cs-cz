---
title: 'Postupy: Kreslení čar pomocí pera'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 8b4eb7684e15ffd5b0b528771490ba66f3b7bb45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156517"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a>Postupy: Kreslení čar pomocí pera
Kreslení čar, je nutné <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.DrawLine%2A> metody a <xref:System.Drawing.Pen> ukládá funkce na řádku, jako je barva a šířka.  
  
## <a name="example"></a>Příklad  
 Následující příklad nakreslí čáru z (20, 10) na (300, 100). První příkaz používá <xref:System.Drawing.Pen.%23ctor%2A> konstruktoru třídy pro vytváření černého pera. Jeden argument předaný do <xref:System.Drawing.Pen.%23ctor%2A> je konstruktor <xref:System.Drawing.Color> objekt vytvořený pomocí <xref:System.Drawing.Color.FromArgb%2A> metoda. Hodnoty použité k vytvoření <xref:System.Drawing.Color> objektu – (255, 0, 0, 0), odpovídají alfa, červené, zelené a modré součásti barvy. Tyto hodnoty definují neprůhledné černé pera.  
  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs>`e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Pen>
- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
- [Pera, čáry a obdélníky v GDI+](pens-lines-and-rectangles-in-gdi.md)
