---
title: "B &#233; zier křivky v GDI +"
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
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cc06a81c879e6ebd50c4eb6a70590c28cc43f6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="b233zier-splines-in-gdi"></a>B &#233; zier křivky v GDI +
Bézierovy křivky je křivka určeného čtyři body: dva koncové body (p1 a p2) a dva kontrolních bodů (c1 a c2). Křivku začíná na p1 a p2 končí. Křivku nepředává prostřednictvím kontrolní body, ale kontrolní body fungovat jako magnets, stahování křivku v určitých pokynů a ovlivňování způsob, jakým zatáčkách křivku. Následující obrázek znázorňuje Bézierovy křivky spolu s jeho koncových bodů a kontrolní body.  
  
 ![Bézierovy křivky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 Křivku začíná p1 a blíží c1 bodu ovládacího prvku. Tečný čáry na křivku P1 je řádku vykreslovány z p1 c1. Tečný řádek v p2 koncový bod je řádku vykreslovány z c2 p2.  
  
## <a name="drawing-bzier-splines"></a>Kreslení Bézierovy křivky  
 Kreslení Bézierovy křivky, je třeba instanci <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Pen>. Instance <xref:System.Drawing.Graphics> třída poskytuje <xref:System.Drawing.Graphics.DrawBezier%2A> metody a <xref:System.Drawing.Pen> ukládá atributy, jako například šířku a barvu čáry použité k vykreslení křivku. <xref:System.Drawing.Pen> Se předá jako jeden z argumenty, které mají <xref:System.Drawing.Graphics.DrawBezier%2A> metoda. Zbývající argumenty předaný <xref:System.Drawing.Graphics.DrawBezier%2A> metoda jsou koncové body a kontrolní body. Následující příklad nevykresluje Bézierovy křivky s výchozí bod (0, 0), řídit body (40, 20) a (80, 150) a koncový bod (100, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 Následující obrázek znázorňuje křivku, kontrolní body a tečný dva řádky.  
  
 ![Bézierovy křivky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 Bézierovy křivky byly původně vyvinuté Pierre Bézierovy návrh v automobilu odvětví. Tyto ukázaly od jako užitečné v mnoha typech počítačový návrhu a také slouží k určení jsou podrobněji popsány dále písem. Bézierovy křivky přispět širokou škálu tvarů, z nichž některé jsou uvedeny na následujícím obrázku.  
  
 ![Cesty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Čáry, křivky a obrazce](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Sestavování a kreslení křivek](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)  
 [Postupy: Vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Postupy: Vytvoření pera](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
