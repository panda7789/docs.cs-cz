---
title: Štětce a vyplněné obrazce v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 45ef0b5920e43300e047d363149ea10a7833477b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912233"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>Štětce a vyplněné obrazce v GDI+
Uzavřený tvar, jako je obdélník nebo elipsa, se skládá z obrysu a vnitřku. Obrys se vykreslí perem a vnitřek se vyplní štětcem. GDI+ poskytuje několik tříd štětců pro vyplňování vnitřních tvarů uzavřených obrazců: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>a <xref:System.Drawing.Drawing2D.PathGradientBrush>. Všechny tyto třídy dědí z <xref:System.Drawing.Brush> třídy. Následující obrázek znázorňuje obdélník vyplněný plným štětcem a elipsu vyplněnou tahem šrafování.  
  
 ![Vyplněné obrazce](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Plné štětce  
 Chcete-li vyplnit uzavřený tvar, potřebujete instanci <xref:System.Drawing.Graphics> třídy <xref:System.Drawing.Brush>a. Instance <xref:System.Drawing.Graphics> třídy poskytuje metody, <xref:System.Drawing.Graphics.FillRectangle%2A> jako jsou a <xref:System.Drawing.Graphics.FillEllipse%2A>, a také <xref:System.Drawing.Brush> atributy obchodů výplně, jako je barva a vzor. <xref:System.Drawing.Brush> Je předán jako jeden z argumentů metody Fill. Následující příklad kódu ukazuje, jak vyplnit elipsu plnou červenou barvou.  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
> V předchozím příkladu je štětec typu <xref:System.Drawing.SolidBrush>, který dědí z. <xref:System.Drawing.Brush>  
  
## <a name="hatch-brushes"></a>Šrafované štětce  
 Při naplňování tvaru pomocí šrafování štětce určíte barvu popředí, barvu pozadí a styl šrafování. Barva popředí je barva šrafování.  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 GDI+ poskytuje více než 50 stylů šrafování; tři styly zobrazené na následujícím obrázku jsou <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>a <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.  
  
 ![Vyplněné obrazce](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Štětce textury  
 Pomocí štětce textury můžete vyplnit tvar pomocí vzoru uloženého v bitmapě. Předpokládejme například, že následující obrázek je uložený v souboru na disku s `MyTexture.bmp`názvem.  
  
 ![Vyplněný tvar](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 Následující příklad kódu ukazuje, jak vyplnit elipsu opakováním obrázku uloženého v `MyTexture.bmp`.  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 Následující ilustrace znázorňuje Vyplněnou elipsu.  
  
 ![Vyplněný tvar](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Štětce přechodu  
 GDI+ nabízí dva druhy štětců přechodů: lineární a cesta. Můžete použít štětec lineárního přechodu k vyplnění obrazce barvou, která se postupně mění při pohybu mezi tvary vodorovně, svisle nebo úhlopříčně. Následující příklad kódu ukazuje, jak vyplnit elipsu vodorovným barevným štětcem, který se při přesunu od levého okraje elipsy do pravého okraje mění z modré na zelenou.  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 Následující ilustrace znázorňuje Vyplněnou elipsu.  
  
 ![Vyplněný tvar](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Štětec pro barevný přechod může být nakonfigurovaný tak, aby se změnila barva při přechodu od středu tvaru k okraji.  
  
 ![Vyplněný tvar](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Štětce přechodu cest jsou poměrně flexibilní. Štětec přechodu použitý k vyplnění trojúhelníku v následujícím obrázku se postupně mění od červeného na všech třech různých barvách na vrcholech.  
  
 ![Vyplněný tvar](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Postupy: Nakreslit vyplněný obdélník na formuláři Windows](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [Postupy: Nakreslit Vyplněnou elipsu na formuláři Windows](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
