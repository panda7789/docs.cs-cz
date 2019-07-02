---
title: Vyhlazení u čar a křivek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
ms.openlocfilehash: 871c5cb3cd9356f677633acb04fe82021a9787c5
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506148"
---
# <a name="antialiasing-with-lines-and-curves"></a>Vyhlazení u čar a křivek
Když použijete GDI + nakreslení čáry, zadáte počáteční bod a koncový bod řádku, ale nemáte zadejte informace o jednotlivých pixelech na řádku. Rozhraní GDI + funguje ve spojení s ovladač zobrazení k určení, které pixelů zapne k zobrazení řádku v konkrétní zobrazení zařízení.  
  
## <a name="aliasing"></a>Vyhlazení  
 Vezměte v úvahu přímo červená čára, která přejde z bodu (4, 2) na bod (16, 10). Předpokládejme souřadnicový systém má původu v levém horním rohu a zda je jednotka měření je pixel. Taky se předpokládá, že osa x odkazuje na pravé straně a osy y body dolů. Následující obrázek znázorňuje zvětšeným zobrazením červené čáry vykreslen na barevné pozadí.  
  
 ![Řádek, bez antialiasingu](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 Červené pixelů použitý k vykreslení čáry jsou neprůhledné. V řádku nejsou žádné pixelech částečně transparentní. Tento typ čáry vykreslování poskytuje řádku vícenásobná vzhled a řádek vypadal něco jako schodiště. Tato technika reprezentovat čáry s schodiště se nazývá aliasing, schodiště je alias pro teoretické řádek.  
  
## <a name="antialiasing"></a>Vyhlazení  
 Složitější techniku pro vykreslení čáry zahrnuje použití částečně transparentní pixelů spolu s neprůhledné pixelů. Obrazové body jsou nastaveny na čistě červenou nebo některé blendu červené a barva pozadí v závislosti na tom, jak blízko se na řádek. Tento typ vykreslování se nazývá vyhlazení a výsledkem řádek, který zjistí z pohledu uživatele jako více hladký průběh. Následující obrázek znázorňuje, jak jsou prolnuty určité pixelů na pozadí a k vytvoření řádku antialiased.  
  
 ![Vyhlazení řádku](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 Vyhlazení, také nazývané vyhlazování, můžete použít také pro křivky. Následující obrázek znázorňuje zvětšeným zobrazením vyhlazenými elipsy.  
  
 ![Antialiasing Curves](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 Následující obrázek znázorňuje stejné elipsy ve skutečné velikosti, bez vyhlazení a posléze s vyhlazení.  
  
 ![Antialiasing example](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 Kreslení čar a křivek, které používají vyhlazení, vytvoření instance <xref:System.Drawing.Graphics> třídy a nastavit jeho <xref:System.Drawing.Graphics.SmoothingMode%2A> vlastnost <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> nebo <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>. Pak volání jedné z metod výkresu, který stejné <xref:System.Drawing.Graphics> třídy.  
  
 [!code-csharp[LinesCurvesAndShapes#81](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Postupy: Použití vyhlazení s textem](how-to-use-antialiasing-with-text.md)
