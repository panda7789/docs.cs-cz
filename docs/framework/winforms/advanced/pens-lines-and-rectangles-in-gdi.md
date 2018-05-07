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
ms.openlocfilehash: 86cc51006361d5628dc12999588520e28e62f166
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>Pera, čáry a obdélníky v GDI+
Kreslení čar pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] musíte vytvořit <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Graphics> Objekt poskytuje metody, které skutečně provést výkresu a <xref:System.Drawing.Pen> objekt ukládá atributy, jako například řádku barvu, šířku a styl.  
  
## <a name="drawing-a-line"></a>Kreslení čáry  
 Chcete-li kreslení čáry, volejte <xref:System.Drawing.Graphics.DrawLine%2A> metodu <xref:System.Drawing.Graphics> objektu. <xref:System.Drawing.Pen> Objekt je předán jako jeden z argumenty, které mají <xref:System.Drawing.Graphics.DrawLine%2A> metoda. Následující příklad nakreslí čáru z bodu (4, 2) do bodu (12, 6):  
  
 [!code-csharp[LinesCurvesAndShapes#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> je přetížené metodu <xref:System.Drawing.Graphics> třídy, takže je můžete zadat s argumenty několika způsoby. Například můžete vytvořit dvě <xref:System.Drawing.Point> objekty a předejte jí <xref:System.Drawing.Point> objekty jako argumenty, které mají <xref:System.Drawing.Graphics.DrawLine%2A> metoda:  
  
 [!code-csharp[LinesCurvesAndShapes#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>Vytváření pera  
 Určité atributy můžete zadat, když vytvoříte <xref:System.Drawing.Pen> objektu. Například jeden `Pen` konstruktor vám umožňuje určit barva a šířka. Následující příklad nakreslí blue šířky 2 z (0, 0) na (60, 30):  
  
 [!code-csharp[LinesCurvesAndShapes#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>Přerušované čáry a čar  
 <xref:System.Drawing.Pen> Objekt také zpřístupní vlastnosti, jako například <xref:System.Drawing.Pen.DashStyle%2A>, že vám pomůže určit funkce řádku. Následující příklad nevykresluje na přerušovanou čáru z (100, 50) na (300, 80):  
  
 [!code-csharp[LinesCurvesAndShapes#44](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 Můžete použít vlastnosti <xref:System.Drawing.Pen> objekt, který chcete nastavit mnoho další atributy čáry. <xref:System.Drawing.Pen.StartCap%2A> a <xref:System.Drawing.Pen.EndCap%2A> vlastnosti určit vzhled konců řádku; skončení se ploché, čtvercový, zaokrouhlené, trojúhelníkovou, nebo vlastní tvaru. <xref:System.Drawing.Pen.LineJoin%2A> Vlastnost umožňuje určit, jestli mají být připojené řádky ostrého (spojená s sharp rozích), zkosené, zaokrouhlí nebo oříznut. Následující obrázek znázorňuje řádky s různými styly zakončení a připojení.  
  
 ![Řádky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>Kreslení v obdélníku  
 Kreslení obdélníků se [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je podobná kreslení čar. Kreslení obdélníku, musíte <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Graphics> Objekt poskytuje <xref:System.Drawing.Graphics.DrawRectangle%2A> metody a <xref:System.Drawing.Pen> ukládá atributy, jako například barvu a šířku objektu. <xref:System.Drawing.Pen> Objekt je předán jako jeden z argumenty, které mají <xref:System.Drawing.Graphics.DrawRectangle%2A> metoda. Následující příklad nevykresluje obdélníku s jeho levého horního rohu na (100, 50), 80 šířka a výška 40:  
  
 [!code-csharp[LinesCurvesAndShapes#45](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> je přetížené metodu <xref:System.Drawing.Graphics> třídy, takže je můžete zadat s argumenty několika způsoby. Například můžete vytvořit <xref:System.Drawing.Rectangle> objektu a předat <xref:System.Drawing.Rectangle> do objektu <xref:System.Drawing.Graphics.DrawRectangle%2A> metoda jako argument:  
  
 [!code-csharp[LinesCurvesAndShapes#46](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 A <xref:System.Drawing.Rectangle> objekt má metody a vlastnosti pro manipulaci s a shromažďování informací o rámeček. Například <xref:System.Drawing.Rectangle.Inflate%2A> a <xref:System.Drawing.Rectangle.Offset%2A> metody změnit velikost a umístění rámečku. <xref:System.Drawing.Rectangle.IntersectsWith%2A> Metoda oznamuje, zda rámeček protíná jiné zadané obdélníku a <xref:System.Drawing.Rectangle.Contains%2A> metoda oznamuje, zda je k danému bodu uvnitř rámeček.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Rectangle?displayProperty=nameWithType>  
 [Postupy: Vytvoření pera](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [Postupy: Kreslení čáry ve formuláři Windows](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)  
 [Postupy: Kreslení obrazce s obrysem](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
