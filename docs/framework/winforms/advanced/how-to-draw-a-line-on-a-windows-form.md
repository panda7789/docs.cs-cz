---
title: 'Postupy: Kreslení čáry v rozhraní Windows Forms'
description: Naučte se, jak na formuláři nakreslit čáru tím, že zpracujete událost nátěru a pak ji vyplníte pomocí vlastnosti Graphics objektu PaintEventArgs.
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
ms.openlocfilehash: c8e92dc265c63413275561d0e2e3aa820eaec724
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621623"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a>Postupy: Kreslení čáry v rozhraní Windows Forms
Tento příklad nakreslí čáru na formuláři. Při kreslení na formuláři se obvykle zpracovává <xref:System.Windows.Forms.Control.Paint> událost formuláře a provádí vykreslování pomocí <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> vlastnosti <xref:System.Windows.Forms.PaintEventArgs> , jak je znázorněno v tomto příkladu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e` , což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="robust-programming"></a>Robustní programování  
 Vždy byste měli volat <xref:System.IDisposable.Dispose%2A> všechny objekty, které využívají systémové prostředky, jako například <xref:System.Drawing.Pen> objekty.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
