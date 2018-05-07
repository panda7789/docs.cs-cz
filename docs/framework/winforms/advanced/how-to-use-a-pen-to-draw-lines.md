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
ms.openlocfilehash: 6a728bcaf9946b2b92ce0ee97599f4c4fd0fea69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-pen-to-draw-lines"></a>Postupy: Kreslení čar pomocí pera
Kreslení čar, musíte <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Graphics> Objekt poskytuje <xref:System.Drawing.Graphics.DrawLine%2A> metody a <xref:System.Drawing.Pen> objekt ukládá funkce na řádku, jako je například barva a šířka.  
  
## <a name="example"></a>Příklad  
 Následující příklad nevykresluje řádek ze (20, 10) na (300, 100). První příkaz používá <xref:System.Drawing.Pen.%23ctor%2A> třída – konstruktor k vytvoření pera černé. Jeden argument předaný <xref:System.Drawing.Pen.%23ctor%2A> konstruktor je <xref:System.Drawing.Color> objekt vytvořený pomocí <xref:System.Drawing.Color.FromArgb%2A> metoda. Hodnoty použité k vytvoření <xref:System.Drawing.Color> objektu – (255, 0, 0, 0) – odpovídají komponenty alfa, červené, zelené a modré barvy. Tyto hodnoty definovat neprůhledného černé pero.  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Pen>  
 [Kreslení čar a obrazců pomocí pera](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Pera, čáry a obdélníky v GDI+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
