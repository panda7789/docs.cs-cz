---
title: Přehled vektorové grafiky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
ms.openlocfilehash: d424254839db6c403bafe779f475c0e344918a5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748421"
---
# <a name="vector-graphics-overview"></a>Přehled vektorové grafiky
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Nakreslí na systém souřadnic řádky, obdélníky a ostatním tvarům. Můžete si vybrat z celé řady souřadnicových systémů, ale výchozí souřadnicový systém má původ v levém horním rohu se osy x, přejdete na pravé straně a osy y směřující dolů. Je pixel je jednotka měření ve výchozím nastavení systém souřadnic.  
  
## <a name="the-building-blocks-of-gdi"></a>Stavební bloky rozhraní GDI +  
 ![Vector graphic](./media/aboutgdip02-art01.gif "AboutGdip02_Art01")  
  
 Monitorování počítače vytvoří její zobrazení v pravoúhlého pole tečky jako obrázek elementy nebo pixelech. Počet pixelů, které se zobrazí na obrazovce se liší od jedno monitorování na další a počet pixelů, které se zobrazí na jednotlivých monitorování obvykle dá do určité míry uživatelem.  
  
 ![Vector graphic](./media/aboutgdip02-art02.gif "AboutGdip02_Art02")  
  
 Při použití [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kreslení čáry, obdélníku či křivku, poskytují některé základní informace o položka, která má být vykreslen. Například můžete zadat jeden řádek tím, že poskytuje dva body a určíte tím, že poskytuje bod, výšku a šířku obdélníku. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funguje ve spojení s ovladač zobrazení k určení, které pixelech musí být nastavená zobrazit čáry, křivky nebo obdélník. Následující obrázek znázorňuje pixelů, které jsou zapnuté zobrazíte řádek z bodu (4, 2) pro bod (12, 8).  
  
 ![Vector graphic](./media/aboutgdip02-art03.gif "AboutGdip02_Art03")  
  
 V průběhu času určité základní stavební bloky ukázaly být zvláště užitečná pro vytváření dvojrozměrné obrázků. Tyto stavební bloky, které jsou podporovány produktem [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], jsou uvedeny v následujícím seznamu:  
  
- řádky  
  
- Obdélníků  
  
- Symbol tří teček  
  
- Oblouky  
  
- Mnohoúhelníky  
  
- Základní křivky vyhlazení  
  
- Bézierovy křivky  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a>Metody pro vykreslování s objektem grafiky  
 <xref:System.Drawing.Graphics> Třídy v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje následující metody pro vytvoření položky v předchozím seznamu: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (pro základní křivky vyhlazení), a <xref:System.Drawing.Graphics.DrawBezier%2A>. Každá z těchto metod je přetížena. To znamená jednotlivé metody podporují několik různých parametr seznamů. Například jeden varianta <xref:System.Drawing.Graphics.DrawLine%2A> metoda přijímá <xref:System.Drawing.Pen> objektu a čtyř celých čísel při další variantou <xref:System.Drawing.Graphics.DrawLine%2A> metoda přijímá <xref:System.Drawing.Pen> objektu a dva <xref:System.Drawing.Point> objekty.  
  
 Metody pro kreslení Bézierovy křivky, řádky a obdélníky mají množném čísle doprovodná metody, které nakreslit několik položek v jednom volání: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, a <xref:System.Drawing.Graphics.DrawBeziers%2A>. Navíc <xref:System.Drawing.Graphics.DrawCurve%2A> metoda má metodu doprovodné <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, že bod křivky koncový bod křivky propojíte s počáteční zavře.  
  
 Všechny metody vykreslení <xref:System.Drawing.Graphics> třídy práce ve spojení s <xref:System.Drawing.Pen> objektu. Chcete-li nakreslit nic, musíte vytvořit aspoň dva objekty: <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Pen> Ukládá atributy, jako je například šířku čáry a barvu položky, která má být vykreslen. <xref:System.Drawing.Pen> Objekt je předán jako jeden z argumentů metody vykreslení. Například jeden varianta <xref:System.Drawing.Graphics.DrawLine%2A> metoda přijímá <xref:System.Drawing.Pen> objektu a čtyř celých čísel, jak je znázorněno v následujícím příkladu, který kreslení obdélníku s šířku 100, výška 50 a levého horního rohu (20, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#11](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Postupy: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md)
