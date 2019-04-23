---
title: 'Postupy: Kreslení čáry na formuláři Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
ms.openlocfilehash: aab04b9236175cedd154b817db5a6f6450503105
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074445"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a>Postupy: Kreslení čáry na formuláři Windows
V tomto příkladu nakreslí čáru na formuláři. Obvykle při kreslení ve formuláři je zpracovat formuláře <xref:System.Windows.Forms.Control.Paint> události a provádět kreslení pomocí <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> vlastnost <xref:System.Windows.Forms.PaintEventArgs>, jak je znázorněno v tomto příkladu  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="robust-programming"></a>Robustní programování  
 Vždy byste měli zavolat <xref:System.IDisposable.Dispose%2A> na všechny objekty, které využívají systémové prostředky, jako například <xref:System.Drawing.Pen> objekty.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
