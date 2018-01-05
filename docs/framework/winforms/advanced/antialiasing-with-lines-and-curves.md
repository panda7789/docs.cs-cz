---
title: "Vyhlazení u čar a křivek"
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
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8552f185a93b688555dbcfab3da9d28d9bfde6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="antialiasing-with-lines-and-curves"></a>Vyhlazení u čar a křivek
Při použití [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kreslení čáry, zadejte výchozí bod a koncový bod řádku, ale není nutné poskytovat žádné informace o jednotlivých pixelů na řádek. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]funguje ve spojení s software ovladače zobrazení k určení, které pixelů bude zapnuto zobrazíte řádek na konkrétní zobrazení zařízení.  
  
## <a name="aliasing"></a>Aliasy  
 Vezměte v úvahu rovnou red řádek, který přejde z bodu (4, 2) do bodu (16, 10). Předpokládejme souřadnicový systém má původ v levém horním rohu a zda Měrná jednotka služby pixelech. Také předpokládají, že osy x bodů vpravo a body osy y dolů. Následující obrázek znázorňuje zvětšeným zobrazením červené linií na barevné pozadí.  
  
 ![Řádek, žádné vyhlazení](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 Red pixelů použitý k vykreslení řádku jsou neprůhledné. V řádku nejsou žádné částečně transparentní pixelů. Tento typ řádku vykreslování nabízí řádek vícenásobná vzhled a řádek vypadal něco jako schodiště. Tato technika reprezentace čáry s schodiště nazývá aliasy; schodiště je alias teoretické řádku.  
  
## <a name="antialiasing"></a>Vyhlazení  
 Složitější technika pro vykreslování řádku, která využívá částečně transparentní pixelů společně s neprůhledností pixelů. Pixelů jsou nastaveny na čistý červený, nebo na některé blend red a barvu pozadí v závislosti na tom, jak zavřít jsou na řádek. Tento typ vykreslování se nazývá vyhlazení a výsledkem řádek, který zjistí lidské oko jako více smooth. Následující obrázek znázorňuje, jak jsou s na pozadí k vytvoření řádku s antialiased smíšení určité pixelů.  
  
 ![Vyhlazení řádek](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 Vyhlazení, označované taky jako vyhlazování, je použít také pro křivek. Následující obrázek znázorňuje zvětšeným zobrazením vyhlazenými třemi tečkami.  
  
 ![Křivky vyhlazení](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 Následující obrázek znázorňuje stejné elipsy v jeho skutečná velikost jednou bez vyhlazení a posléze s vyhlazení.  
  
 ![Příklad vyhlazení](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 Kreslení čar a křivek, které používají vyhlazení, vytvořte instanci <xref:System.Drawing.Graphics> a nastavit jeho <xref:System.Drawing.Graphics.SmoothingMode%2A> vlastnost <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> nebo <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>. Potom zavolejte jednu z metod vykreslování této stejné <xref:System.Drawing.Graphics> třídy.  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>  
 [Čáry, křivky a obrazce](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Postupy: Použití vyhlazení u textu](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
