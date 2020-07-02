---
title: 'Postupy: Kreslení plného obdélníku v rozhraní Windows Form'
description: Naučte se programově nakreslit plný obdélník na formuláři Windows. Přečtěte si také informace o kompilování kódu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621636"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a>Postupy: Kreslení plného obdélníku v rozhraní Windows Form
Tento příklad nakreslí vyplněný obdélník na formuláři.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tuto metodu nelze volat v <xref:System.Windows.Forms.Form.Load> obslužné rutině události. Nakreslený obsah nebude překreslen v případě, že dojde ke změně velikosti formuláře nebo jeho skrytí jiným formulářem. Chcete-li obsah automaticky překreslit, měli byste přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metodu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Vždy byste měli volat <xref:System.IDisposable.Dispose%2A> všechny objekty, které využívají systémové prostředky, například <xref:System.Drawing.Brush> a <xref:System.Drawing.Graphics> objekty.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
- [Štětce a vyplněné obrazce v GDI+](brushes-and-filled-shapes-in-gdi.md)
