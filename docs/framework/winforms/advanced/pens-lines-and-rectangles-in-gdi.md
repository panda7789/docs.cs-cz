---
title: Pera, čáry a obdélníky v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 84752773c0b56d9684dc31620d463d4ddccf9dad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078223"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>Pera, čáry a obdélníky v GDI+
Kreslení čar pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je potřeba vytvořit <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Graphics> Objekt, který poskytuje metody, které se dělají kreslení, a <xref:System.Drawing.Pen> ukládá atributy, jako je barva čáry, šířku a stylu.  
  
## <a name="drawing-a-line"></a>Vykreslení čáry  
 Chcete-li nakreslit čáru, zavolejte <xref:System.Drawing.Graphics.DrawLine%2A> metodu <xref:System.Drawing.Graphics> objektu. <xref:System.Drawing.Pen> Objekt je předán jako argumenty, které mají <xref:System.Drawing.Graphics.DrawLine%2A> metody. Následující příklad nakreslí čáru z bodu (4, 2) pro bod (12, 6):  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> je přetížená metoda <xref:System.Drawing.Graphics> třídy, takže je můžete zadat s argumenty několika způsoby. Například můžete vytvořit dvě <xref:System.Drawing.Point> objekty a předejte jí <xref:System.Drawing.Point> objekty jako argumenty, které mají <xref:System.Drawing.Graphics.DrawLine%2A> metoda:  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>Vytváření pera  
 Určité atributy můžete zadat při vytváření <xref:System.Drawing.Pen> objektu. Například jeden `Pen` konstruktor umožňuje zadat barvu a šířku. Následující příklad nakreslí modrá čára šířky 2 z (0, 0) na (60, 30):  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>Přerušované čáry a zakončení  
 <xref:System.Drawing.Pen> Objekt také zpřístupní vlastnosti, jako například <xref:System.Drawing.Pen.DashStyle%2A>, že můžete použít k určení funkce na řádku. Následující příklad kreslení na přerušovanou čáru z (100, 50) na (300, 80):  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 Můžete použít vlastnosti <xref:System.Drawing.Pen> nastavíte mnoho další atributy čáry. <xref:System.Drawing.Pen.StartCap%2A> a <xref:System.Drawing.Pen.EndCap%2A> vlastnosti určují vzhled konce řádku; konců lze použít bez stromové struktury, čtvereček, zakulacený, trojúhelníkové, nebo vlastní obrazce. <xref:System.Drawing.Pen.LineJoin%2A> Vlastnost umožňuje určit, zda spojené čáry jsou zkosené (připojené k doméně se sharp rohy), sený, zaokrouhleno nebo oříznut. Následující obrázek znázorňuje řádky s různými styly zakončení a spojení.  
  
 ![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>Vykreslení obdélníku  
 Kreslení obdélníků pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je nějak nakreslení čáry. Chcete-li nakreslit obdélník, je nutné <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.DrawRectangle%2A> metody a <xref:System.Drawing.Pen> ukládá atributy, jako je například šířku čáry a barvu. <xref:System.Drawing.Pen> Objekt je předán jako argumenty, které mají <xref:System.Drawing.Graphics.DrawRectangle%2A> metody. Kreslení obdélníku s jeho levého horního rohu v následujícím příkladu (100, 50), 80 šířku a výšku 40:  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> je přetížená metoda <xref:System.Drawing.Graphics> třídy, takže je můžete zadat s argumenty několika způsoby. Například můžete vytvořit <xref:System.Drawing.Rectangle> objektu a předejte <xref:System.Drawing.Rectangle> objektu <xref:System.Drawing.Graphics.DrawRectangle%2A> metody jako argument:  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 A <xref:System.Drawing.Rectangle> objekt má metody a vlastnosti zpracování a shromažďují se informace o obdélníku. Například <xref:System.Drawing.Rectangle.Inflate%2A> a <xref:System.Drawing.Rectangle.Offset%2A> metody měnit velikost a umístění obdélníku. <xref:System.Drawing.Rectangle.IntersectsWith%2A> Metoda zjistíte, zda obdélník protíná jiné zadané obdélníku a <xref:System.Drawing.Rectangle.Contains%2A> metoda zjistíte, jestli je daný bod v obdélníku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [Postupy: Vytvoření pera](how-to-create-a-pen.md)
- [Postupy: Nakreslit čáru na formuláři Windows](how-to-draw-a-line-on-a-windows-form.md)
- [Postupy: Kreslení obrazce s obrysem](how-to-draw-an-outlined-shape.md)
