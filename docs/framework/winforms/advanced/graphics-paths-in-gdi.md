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
ms.openlocfilehash: 66d30b949fbfe8190b9e2ae2ea7896ac36bf0bac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523885"
---
# <a name="graphics-paths-in-gdi"></a>Cesty grafiky v GDI+
Cesty se vytvoří kombinací řádků, obdélníků a jednoduchý křivek. Odvolat z [přehled vektorové grafiky](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) , následující základní stavební bloky ukázaly jako nejvhodnější pro vykreslování obrázků:  
  
-   řádky  
  
-   Obdélníků  
  
-   Symbol tří teček  
  
-   Oblouky  
  
-   Mnohoúhelníky  
  
-   Základní křivky vyhlazení  
  
-   Bézierovy křivky  
  
 V rozhraní GDI + <xref:System.Drawing.Drawing2D.GraphicsPath> objekt umožňuje shromažďovat posloupnost tyto stavební bloky do jedné jednotky. Celé řady čar, obdélníků, mnohoúhelníky a křivek pak lze rozlišovat pomocí jednoho volání <xref:System.Drawing.Graphics.DrawPath%2A> metodu <xref:System.Drawing.Graphics> třídy. Následující obrázek znázorňuje cestu vytvořit kombinací řádek, oblouk, Bézierovy křivky a křivky mohutnosti.  
  
 ![Cesta](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>Pomocí cesty  
 <xref:System.Drawing.Drawing2D.GraphicsPath> Třída poskytuje následující metody pro vytvoření posloupnost položek, které se mají vykreslovat: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (pro základní křivky vyhlazení), a <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>. Každá z těchto metod je přetížena; To znamená jednotlivé metody podporují několik různých parametr seznamy. Například jeden varianta <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metoda přijímá čtyři celá čísla a další varianta <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metoda obdrží dvě <xref:System.Drawing.Point> objekty.  
  
 Metody pro přidání řádků, obdélníků a Bézierových křivek na cestu, mají množném čísle doprovodné metody, které přidejte několik položek do cesty v jediném volání: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, a <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>. Navíc <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> a <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> metody mají metody Průvodce vyhledáváním, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> a <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, přidá výsečového nebo uzavřené křivky k cestě.  
  
 Kreslení cestu, musíte <xref:System.Drawing.Graphics> objekt, <xref:System.Drawing.Pen> objekt a <xref:System.Drawing.Drawing2D.GraphicsPath> objektu. <xref:System.Drawing.Graphics> Objekt poskytuje <xref:System.Drawing.Graphics.DrawPath%2A> metody a <xref:System.Drawing.Pen> objekt ukládá atributy, jako například šířku a barvu čáry použité k vykreslení cestu. <xref:System.Drawing.Drawing2D.GraphicsPath> Objekt ukládá řady čar a křivek, které tvoří cestu. <xref:System.Drawing.Pen> Objektu a <xref:System.Drawing.Drawing2D.GraphicsPath> objekt jsou předány jako argumenty, které mají <xref:System.Drawing.Graphics.DrawPath%2A> metoda. Následující příklad nevykresluje cestu, která se skládá z řádku, třemi tečkami a Bézierovy křivky:  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 Následující obrázek ukazuje cestu.  
  
 ![Cesta](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 Kromě přidání čar, obdélníků a křivek na cestu, můžete přidat cesty na cestu. To umožňuje zkombinovat existující cesty k vytvoření složitých cesty.  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 Existují dva další položky, které můžete přidat do cesty: řetězce a koláče. Výsečový je část vnitřek elipsy. Následující příklad vytvoří cestu z oblouk, křivky mohutnosti, řetězec a výsečový:  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 Následující obrázek ukazuje cestu. Všimněte si, že cestu nemusí být připojen; oblouk, křivky mohutnosti, string a kruhový jsou oddělené.  
  
 ![Cesty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [Čáry, křivky a obrazce](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Postupy: Vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Sestavování a kreslení cest](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
