---
title: "Přehled vektorové grafiky"
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
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7bb3247f531a0dac83657e118fb53ebaf708ec9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="vector-graphics-overview"></a>Přehled vektorové grafiky
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Kreslení čar, obdélníků a ostatním tvarům na souřadnicový systém. Můžete vybrat z různých souřadnicových systémů, ale výchozí souřadnicový systém má původ v levém horním rohu s osou x tvořenou hodnotami odkazující na ose y míří dolů a doprava. Ve výchozím nastavení souřadnicový systém Měrná jednotka je pixelech.  
  
## <a name="the-building-blocks-of-gdi"></a>Stavební bloky rozhraní GDI +  
 ![Vektorová grafika](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.gif "AboutGdip02_Art01")  
  
 Monitorování počítače vytvoří jeho zobrazení na obdélníkový pole teček označovaný jako obrázek elementy nebo pixelů. Počet pixelů, které se zobrazují na obrazovce se liší z jednoho monitoru na další a počet pixelů, která se zobrazují na jednotlivých monitorování lze nakonfigurovat obvykle do určité míry uživatelem.  
  
 ![Vektorová grafika](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.gif "AboutGdip02_Art02")  
  
 Při použití [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kreslení čáry, obdélníku nebo křivky, zadáte určité klíčové informace o položce, které se mají vykreslovat. Například můžete zadat řádek tím, že poskytuje dva body a zadáte obdélníku tím, že poskytuje bod, výšku a šířku. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]funguje ve spojení s software ovladače zobrazení k určení, které pixelech musí být zapnutý zobrazíte řádku, obdélníku nebo křivky. Následující obrázek znázorňuje pixelů, které jsou zapnuté pro zobrazení průběhu z bodu (4, 2) do bodu (12, 8).  
  
 ![Vektorová grafika](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.gif "AboutGdip02_Art03")  
  
 V průběhu času určité základní stavební bloky ukázaly jako velmi užitečné k vytváření dvourozměrná obrázků. Tyto stavební bloky, které jsou podporovány produktem [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], jsou uvedeny v následujícím seznamu:  
  
-   řádky  
  
-   Obdélníků  
  
-   Symbol tří teček  
  
-   Oblouky  
  
-   Mnohoúhelníky  
  
-   Základní křivky vyhlazení  
  
-   Bézierovy křivky  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a>Metody pro vykreslování s objektem grafiky  
 <xref:System.Drawing.Graphics> Třídy v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje následující metody pro vykreslení položky v předchozím seznamu: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (pro základní křivky vyhlazení), a <xref:System.Drawing.Graphics.DrawBezier%2A>. Každá z těchto metod je přetížena; To znamená jednotlivé metody podporují několik různých parametr seznamy. Například jeden varianta <xref:System.Drawing.Graphics.DrawLine%2A> metoda přijímá <xref:System.Drawing.Pen> objekt a čtyři celá čísla, při jiné varianta <xref:System.Drawing.Graphics.DrawLine%2A> metoda přijímá <xref:System.Drawing.Pen> objektu a dvě <xref:System.Drawing.Point> objekty.  
  
 Metody pro kreslení čar, obdélníků a Bézierovy křivky mají množném čísle doprovodné metody, které kreslení několik položek v jediném volání: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, a <xref:System.Drawing.Graphics.DrawBeziers%2A>. Také <xref:System.Drawing.Graphics.DrawCurve%2A> metoda obsahuje metodu doprovodné <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, že bodu křivky propojíte počáteční koncovému bodu křivky zavře.  
  
 Všechny metody kreslení z <xref:System.Drawing.Graphics> třídy pracovní ve spojení s <xref:System.Drawing.Pen> objektu. Kreslení nic, musíte vytvořit aspoň dva objekty: <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Pen> Ukládá atributy, jako například barvu položky, které se mají vykreslovat a šířku objektu. <xref:System.Drawing.Pen> Objekt je předán jako jednoho z argumentů kreslení metodě. Například jeden varianta <xref:System.Drawing.Graphics.DrawLine%2A> metoda obdrží <xref:System.Drawing.Pen> objekt a čtyři celá čísla, jak je znázorněno v následujícím příkladu, který vykreslí s šířky 100, výška 50 a levého horního rohu obdélníku (20, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Čar, křivek a obrazců](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Postupy: vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
