---
title: "Základní křivky v GDI+"
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
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ad417ee61026f6573f19e70409511e0b28e4d78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cardinal-splines-in-gdi"></a>Základní křivky v GDI+
Spojnice křivky je pořadí jednotlivých křivek připojený k formuláři větší křivky. Pole bodů a parametr pnutí je určena křivky. Spojnice křivky plynule projdou každý bod v poli; neexistují žádné sharp rozích a žádné náhlému změny v těsnost křivku. Následující obrázek znázorňuje sadu body a křivky mohutnosti, které procházejí každý bod v sadě.  
  
 ![Křivkový základních](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>Fyzické a matematickém křivky vyhlazení  
 Fyzické křivkový je dynamické dřeva nebo jiného materiálu flexibilní. Před nástupem matematickém křivky Designer použít fyzické křivky kreslení křivek. Návrhář by umístit křivky na papír a ukotvení na danou sadu body. Návrhář může potom vytvořit křivka kreslení podél křivky pomocí pera nebo tužky. Danou sadu bodů může yield celou řadu křivek, v závislosti na vlastnosti fyzické křivkový. Křivkový s vysokou odolností vůči ohybu například byste mohli vytvořit různé křivky než velmi flexibilní křivkový.  
  
 Vzorce pro matematické křivky jsou založené na vlastnosti flexibilní tyče tak křivek vyprodukované matematickém křivky jsou podobná křivek jednou vydaných společností fyzické křivky. Stejně jako fyzický křivky různých pnutí vytvoří různé křivek prostřednictvím danou sadu body, vygeneruje matematickém křivky vyhlazení s různými hodnotami pro parametr pnutí různých křivek prostřednictvím danou sadu body. Následující obrázek znázorňuje čtyři základní křivky vyhlazení prošla stejnou sadu body. Pro každý křivkový se zobrazuje hodnotu napětí. Pnutí 0 odpovídá nekonečné fyzické pnutí vynucení křivku provést nejkratší způsob (přímky) mezi body. Žádné fyzické pnutí povolení křivkový provést cestu alespoň celkový ohybem odpovídá pnutí 1. S hodnotami pnutí větší než 1 křivku chová jako komprimovaný pružiny, instaluje do použít delší cestu.  
  
 ![Základní křivky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 Čtyři křivky v předchozí ilustraci sdílet stejnou tečný řádku na počáteční bod. Tangens je řádku čerpají z výchozí bod pro další bod podél křivku. Sdílené tangens na koncový bod, je na řádku čerpají z koncový bod předchozího bodu na křivku.  
  
 Kreslení křivky mohutnosti, je třeba instanci <xref:System.Drawing.Graphics> třída, <xref:System.Drawing.Pen>a pole <xref:System.Drawing.Point> objekty instanci <xref:System.Drawing.Graphics> třída poskytuje <xref:System.Drawing.Graphics.DrawCurve%2A> metodu, která nevykresluje křivky, a <xref:System.Drawing.Pen> uloží atributy křivkový, jako je například šířka čáry a barvy. Pole <xref:System.Drawing.Point> objekty ukládá body, které budou předány křivku. Následující příklad kódu ukazuje, jak k vykreslení křivky mohutnosti, které procházejí body v `myPointArray`. Třetí parametr není hodnotu napětí.  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Viz také  
 [Čar, křivek a obrazců](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Sestavování a kreslení křivek](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
