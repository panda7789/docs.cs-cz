---
title: B&#233;zier křivky v GDI +
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: ff4e9eb18610b70c88e057d3d44020321bbb9f4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107325"
---
# <a name="b233zier-splines-in-gdi"></a>B&#233;zier křivky v GDI +
Bézierovy křivky je křivka určené čtyři body: dva koncové body (p1 a p2) a dva kontrolních bodů (c1 a c2). Křivky začíná p1 a p2 končí. Křivka neprochází přes kontrolních bodů, ale kontrolní body fungují jako magnets stahování křivky v některých směrech a vliv na způsob, jakým zatáčkách křivky. Následující obrázek znázorňuje Bézierovy křivky spolu s jeho koncových bodů a kontrolní body.  
  
 ![Bezier Splines](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 Křivka začíná p1 a blíží c1 bodu ovládacího prvku. Tečný čáry na křivku P1 je linií z p1 c1. Tečný řádek na p2 koncový bod je linií z c2 p2.  
  
## <a name="drawing-bzier-splines"></a>Kreslení Bézierovy křivky  
 Na kreslení Bézierovy křivky, je třeba instance <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Pen>. Instance <xref:System.Drawing.Graphics> třída poskytuje <xref:System.Drawing.Graphics.DrawBezier%2A> metody a <xref:System.Drawing.Pen> uloží atributy, například šířku a barvu čáry použité k vykreslení křivky. <xref:System.Drawing.Pen> Je předán jako argumenty, které mají <xref:System.Drawing.Graphics.DrawBezier%2A> metody. Zbývající argumenty předané <xref:System.Drawing.Graphics.DrawBezier%2A> metody jsou koncové body a body ovládacího prvku. Následující příklad kreslení Bézierovy křivky s počáteční bod (0, 0), řídit body (40, 20) a (80, 150) a koncový bod (100, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#71](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 Následující obrázek znázorňuje křivku, kontrolní body a tečný dva řádky.  
  
 ![Bezier Splines](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 Bézierovy křivky byly původně vyvinutý Pierre Bézierovy pro programátory v automobilový průmysl. Se od té doby ukázaly být užitečné v mnoha typech engineeringových návrhu a se také používají k definování obrysy písma. Bézierovy křivky může přinést širokou škálu tvary, z nichž některé jsou zobrazené na následujícím obrázku.  
  
 ![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Sestavování a kreslení křivek](constructing-and-drawing-curves.md)
- [Postupy: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md)
- [Postupy: Vytvoření pera](how-to-create-a-pen.md)
