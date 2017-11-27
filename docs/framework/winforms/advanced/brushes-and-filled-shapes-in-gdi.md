---
title: "Štětce a vyplněné obrazce v GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01d7359499c858ad7c4f1da2fa24f18e801bb324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>Štětce a vyplněné obrazce v GDI+
Uzavřený obrazec, jako je například obdélníku nebo elipsy, se skládá z přehledu a vnitřním. Obrys vykreslením pomocí pera a vnitřní je vyplněn štětce. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]poskytuje několik štětce třídy pro naplnění vnitřek uzavřené obrazce: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, a <xref:System.Drawing.Drawing2D.PathGradientBrush>. Všechny tyto třídy dědí <xref:System.Drawing.Brush> třídy. Následující obrázek znázorňuje obdélníku, naplní se plného štětce a elipsy plná štětce šrafování.  
  
 ![Vyplněné tvary](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Plného štětce  
 K vyplnění uzavřený obrazec, je třeba instanci <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Brush>. Instance <xref:System.Drawing.Graphics> třída poskytuje metody, jako například <xref:System.Drawing.Graphics.FillRectangle%2A> a <xref:System.Drawing.Graphics.FillEllipse%2A>a <xref:System.Drawing.Brush> uloží atributy výplně, jako je například barvy a vzorku. <xref:System.Drawing.Brush> Jako jednoho z argumentů předaný metodě výplně. Následující příklad kódu ukazuje, jak k vyplnění elipsy s plnou červenou barvu.  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  V předchozím příkladu stopy je typu <xref:System.Drawing.SolidBrush>, který dědí z <xref:System.Drawing.Brush>.  
  
## <a name="hatch-brushes"></a>Nesouvislých štětců  
 Po vyplnění obrazce štětcem šrafování, je třeba zadat barvu popředí, barva pozadí a styl šrafování. Barvu popředí je barva šrafování.  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]poskytuje více než 50 šrafování styly; tři styly vidět na následujícím obrázku jsou <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, a <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.  
  
 ![Vyplněné tvary](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Texturované štětce  
 Štětcem texture můžete vyplnění obrazce pomocí vzoru uložené v rastrový obrázek. Předpokládejme například, že na následujícím obrázku je uložený v souboru na disku s názvem `MyTexture.bmp`.  
  
 ![Vyplněné obrazce](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 Následující příklad kódu ukazuje, jak k vyplnění elipsy opakováním obrázek uložený v `MyTexture.bmp`.  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 Následující obrázek znázorňuje plné elipsy.  
  
 ![Vyplněné obrazce](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Štětce přechodu  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]nabízí dva typy štětce přechodu: lineární a cestu. Můžete lineární štětce přechodu k vyplnění obrazce s barvu, která změní postupně přesouvat mezi tvaru vodorovně, svisle nebo šikmo. Následující příklad kódu ukazuje, jak vyplníte elipsy vodorovné štětce přechodu, který změní z modré zelený, když jste odpojili od levého okraje se třemi tečkami na pravý okraj.  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 Následující obrázek znázorňuje plné elipsy.  
  
 ![Vyplněné obrazce](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Štětce přechodu cesty může být nakonfigurován pro změnit barvu, jako jste odpojili od středu tvaru směrem od okraje.  
  
 ![Vyplněné obrazce](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Štětce přechodu cesty jsou velmi flexibilní. Štětce přechodu použitou k vyplnění trojúhelníček následujícím změnám obrázek postupně z červené v Centru pro každé ze tří různých barev na vrcholy.  
  
 ![Vyplněné obrazce](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 [Čar, křivek a obrazců](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Postupy: Kreslení plného obdélníku ve formuláři Windows](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)  
 [Postupy: kreslení plné elipsy ve formuláři Windows](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
