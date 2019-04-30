---
title: Cesty grafiky v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: c9a43065210f5ef0fffcae01cc7eb88349696b6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938134"
---
# <a name="graphics-paths-in-gdi"></a>Cesty grafiky v GDI+
Cesty jsou vytvořené kombinací řádků, obdélníky a jednoduché křivky. Pamatujete z [přehled vektorové grafiky](vector-graphics-overview.md) , že tyto základní stavební bloky ukázaly být zvláště užitečná pro vykreslování obrázků:  
  
- řádky  
  
- Obdélníků  
  
- Symbol tří teček  
  
- Oblouky  
  
- Mnohoúhelníky  
  
- Základní křivky vyhlazení  
  
- Bézierovy křivky  
  
 V rozhraní GDI + <xref:System.Drawing.Drawing2D.GraphicsPath> objektu umožňuje shromažďovat pořadí těchto stavebních bloků do jedné jednotky. S jedním zavoláním pak lze rozlišovat seřazených řádků, obdélníky, mnohoúhelníků a křivek <xref:System.Drawing.Graphics.DrawPath%2A> metodu <xref:System.Drawing.Graphics> třídy. Cesta vytvořené kombinací řádku, oblouk, Bézierovy křivky a křivky mohutnosti na následujícím obrázku.  
  
 ![Path](./media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>Pomocí cesty  
 <xref:System.Drawing.Drawing2D.GraphicsPath> Třída poskytuje následující metody pro vytváření pořadí položek, které chcete kreslit: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (pro základní křivky vyhlazení), a <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>. Každá z těchto metod je přetížena. To znamená jednotlivé metody podporují několik různých parametr seznamů. Například jeden varianta <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metoda obdrží čtyř celých čísel a další variantou <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metoda obdrží dvě <xref:System.Drawing.Point> objekty.  
  
 Metody pro přidání řádků, obdélníky a Bézierových křivek na cestu mají množném čísle doprovodná metody, které přidejte několik položek na cestu v jednom volání: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, a <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>. Navíc <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> a <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> metody mají metody doprovodné <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> a <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, přidá výsečového nebo uzavřené křivky do cesty.  
  
 K nakreslení cesty, je nutné <xref:System.Drawing.Graphics> objektu, <xref:System.Drawing.Pen> objektu a <xref:System.Drawing.Drawing2D.GraphicsPath> objektu. <xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.DrawPath%2A> metody a <xref:System.Drawing.Pen> ukládá atributy, například šířku a barvu čáry použité k vykreslení cestu. <xref:System.Drawing.Drawing2D.GraphicsPath> Ukládá posloupnost čar a křivek, které tvoří cestu. <xref:System.Drawing.Pen> Objektu a <xref:System.Drawing.Drawing2D.GraphicsPath> objektu jsou předány jako argumenty, které mají <xref:System.Drawing.Graphics.DrawPath%2A> metody. Následující příklad nakreslí cestu, která se skládá z řádku elipsu a Bézierovy křivky:  
  
 [!code-csharp[LinesCurvesAndShapes#101](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 Následující obrázek znázorňuje cestu.  
  
 ![Path](./media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 Kromě přidání řádků, obdélníky a křivek na cestu, můžete přidat cesty na cestu. Díky tomu můžete kombinovat existující cesty k vytvoření složitých cesty.  
  
 [!code-csharp[LinesCurvesAndShapes#102](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 Existují dvě další položky, můžete přidat do cesty: řetězce a koláče. Výsečový se část vnitřní elipsu. Následující příklad vytvoří cestu z oblouk, křivky mohutnosti, řetězce a výsečový:  
  
 [!code-csharp[LinesCurvesAndShapes#103](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 Následující obrázek znázorňuje cestu. Všimněte si, že cestu nemusí být připojená arc, základní křivka vyhlazení, řetězce a výsečový jsou oddělené.  
  
 ![Paths](./media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Postupy: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md)
- [Sestavování a kreslení cest](constructing-and-drawing-paths.md)
