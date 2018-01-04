---
title: "Postupy: Kreslení základních čar"
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
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64661bbdcb267e2f2ce33b8a8db2ab2aac9a86f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-cardinal-splines"></a>Postupy: Kreslení základních čar
Spojnice křivky je křivky, které procházejí danou sadu body bez problémů. Kreslení křivky mohutnosti, vytvořit <xref:System.Drawing.Graphics> objektu a předejte adresu v poli body <xref:System.Drawing.Graphics.DrawCurve%2A> metoda.  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a>Kreslení základních křivky ve tvaru zvonu  
  
-   Následující příklad nevykresluje mohutnosti křivkový se ve tvaru zvonu, které procházejí pět určené body. Následující obrázek znázorňuje křivku a pět bodů.  
  
     ![Křivkový základních](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a>Kreslení uzavřené křivky základních  
  
-   Použití <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metodu <xref:System.Drawing.Graphics> třída k vykreslení uzavřené křivky mohutnosti. V uzavřené křivky mohutnosti křivku pokračuje pomocí posledního bodu v poli a připojí s prvním bodem v poli. Následující příklad nevykresluje uzavřené křivku mohutnosti, která předá prostřednictvím šesti určené bodů. Následující obrázek znázorňuje uzavřené křivky společně s šest bodů.  
  
 ![Křivkový základních](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a>Změna ohybem základní křivky  
  
-   Změnit způsob křivky mohutnosti zatáčkách předáním pnutí argument <xref:System.Drawing.Graphics.DrawCurve%2A> metoda. Následující příklad nevykresluje tři základní křivky vyhlazení, které procházejí stejnou sadu body. Následující obrázek znázorňuje tři křivky spolu s příslušnými hodnotami pnutí. Všimněte si, že 0 po hodnotu napětí body jsou připojena linkami přímých.  
  
 ![Křivkový základních](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozích příkladech jsou navrženy pro používání s formuláři Windows a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Čáry, křivky a obrazce](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Sestavování a kreslení křivek](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
