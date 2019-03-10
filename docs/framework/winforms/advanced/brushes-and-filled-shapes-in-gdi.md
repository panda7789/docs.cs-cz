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
ms.openlocfilehash: fc6d6857e912ba14fca382eb49373655004534d5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720940"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>Štětce a vyplněné obrazce v GDI+
Zavřeného tvaru, jako je například obdélník nebo elipsy, se skládá z přehledu a vnitřním. Přehled je vykreslen pomocí pera a vnitřní je vyplněna štětce. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje několik tříd štětce k vyplnění vnitřek uzavřené obrazce: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, a <xref:System.Drawing.Drawing2D.PathGradientBrush>. Všechny tyto třídy dědí <xref:System.Drawing.Brush> třídy. Následující obrázek znázorňuje obdélník vyplněny plného štětce a elipsa se štětce šrafování.  
  
 ![Vyplněné tvary](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Plné štětců  
 K vyplnění zavřeného tvaru, je třeba instance <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Brush>. Instance <xref:System.Drawing.Graphics> třída poskytuje metody, jako například <xref:System.Drawing.Graphics.FillRectangle%2A> a <xref:System.Drawing.Graphics.FillEllipse%2A>a <xref:System.Drawing.Brush> uloží atributy výplň, jako je barva a vzor. <xref:System.Drawing.Brush> Je předán jako jeden z argumentů metody fill. Následující příklad kódu ukazuje, jak vyplnit elipsu s plnou červenou barvu.  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  V předchozím příkladu je štětec typu <xref:System.Drawing.SolidBrush>, který dědí z <xref:System.Drawing.Brush>.  
  
## <a name="hatch-brushes"></a>Nesouvislých štětců  
 Po vyplnění obrazce pomocí nesouvislého štětce, určíte barvu popředí, pozadí barvu a styl šrafování. Barva popředí je barva šrafování.  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje více než 50 šrafování styly; tři styly je znázorněno na následujícím obrázku jsou <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, a <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.  
  
 ![Vyplněné tvary](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Texturované štětce  
 Štětcem textury můžete vyplnění obrazce pomocí vzoru uložené v rastrový obrázek. Předpokládejme například, že na následujícím obrázku je uložen v souboru na disku s názvem `MyTexture.bmp`.  
  
 ![Vyplněné obrazce](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 Následující příklad kódu ukazuje, jak vyplnit elipsu opakováním obrázek uložený v `MyTexture.bmp`.  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 Následující obrázek znázorňuje vyplněnou elipsu.  
  
 ![Vyplněné obrazce](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Štětce přechodu  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje dva druhy štětce přechodu: lineární a cestu. Štětec lineárního přechodu můžete použít k vyplnění obrazce pomocí barev, která se mění postupně při přesunu napříč tvar vodorovně, svisle, nebo šikmo. Následující příklad kódu ukazuje, jak vyplnit elipsu vodorovné štětce přechodu, který změní z blue green při přesunu z levého okraje na tři tečky na pravý okraj.  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 Následující obrázek znázorňuje vyplněnou elipsu.  
  
 ![Vyplněné obrazce](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Chcete-li změnit barvu při přesunu z centra obrazec na hraničních zařízeních je možné nakonfigurovat štětce přechodu cesty.  
  
 ![Vyplněné obrazce](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Štětce přechodu cesty jsou velmi flexibilní. Štětec přechodu použitou k vyplnění trojúhelník následující změny obrázek postupně od červené uprostřed každé tři různé barvy u vrcholů.  
  
 ![Vyplněné obrazce](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Postupy: Kreslení plného obdélníku ve formuláři Windows](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [Postupy: Kreslení plné elipsy ve formuláři Windows](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
