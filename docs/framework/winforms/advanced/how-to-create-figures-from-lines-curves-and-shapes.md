---
title: 'Postupy: Vytváření obrázků z čar, křivek a obrazců'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
ms.openlocfilehash: c8cf7a7e08bed56fb704bba4e30ff369bc3fcf89
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643478"
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a>Postupy: Vytváření obrázků z čar, křivek a obrazců
Vytvoření elementu figure, sestavit <xref:System.Drawing.Drawing2D.GraphicsPath>a pak volat metody, jako například <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> a <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, chcete-li přidat primitivních elementů do cesty.  
  
## <a name="example"></a>Příklad  
 Následující příklady kódu vytvořte cesty, které se mají hodnoty:  
  
- První příklad vytváří cestu, která má jednoho elementu figure. Na obrázku se skládá z jedné oblouk. Oblouku má úhel oblouku – 180 stupňů, což je proti směru hodinových ručiček ve výchozím nastavení systém souřadnic.  
  
- V druhém příkladu vytvoří cestu, která má dvě číslice. První obrázek je oblouk, za nímž následuje řádku. Druhý obrázek je řádek, za nímž následuje křivku, za nímž následuje řádku. První obrázek je otevřená a druhý obrázek je zavřený.  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozích příkladech jsou určeny k použití pomocí Windows Forms a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [Sestavování a kreslení cest](constructing-and-drawing-paths.md)
- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
