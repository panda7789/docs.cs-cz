---
title: Základní křivky v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
ms.openlocfilehash: 4588f6f606f0f479aeae1d143f23175ec4be32a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779117"
---
# <a name="cardinal-splines-in-gdi"></a>Základní křivky v GDI+
Křivky mohutnosti je posloupnost jednotlivých křivky připojené k formuláři větší křivky. Pole bodů a napětí parametr je zadaný křivky. Křivky mohutnosti plynule prochází každý bod v poli; neexistují žádné sharp rohů a žádné náhlé změny v těsnost křivky. Následující obrázek znázorňuje sadu body a vyhlazení prochází každý bod v sadě.  
  
 ![Cardinal Spline](./media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>Fyzická a matematické křivek  
 Fyzické křivky je dynamického zajišťování wood nebo jiného materiálu flexibilní. Před nástupem matematické křivek návrháři použili fyzické křivky kreslení křivek. Návrhář by umístit na papír křivky a ukotvení na danou sadu body. Návrhář může potom vytvořit křivky kreslení podél křivky perem nebo tužky. Daný sady bodů může přinést řadu křivky v závislosti na vlastnosti fyzické křivky. Křivkový s vysokou odolností vůči ohyb například byste mohli vytvořit různé křivky než velmi flexibilní křivky.  
  
 Křivky matematické vzorce jsou založené na vlastnosti flexibilní tyče křivky vytvářených matematické křivky jsou podobné křivky jednou vydaných společností fyzickou křivky. Stejně jako fyzické křivky různých napětí vytvoří jiné křivky prostřednictvím daný sady bodů, vytvoří matematické křivky s různými hodnotami pro parametr napětí různých křivky prostřednictvím daný sady bodů. Následující obrázek znázorňuje čtyři základní křivky vyhlazení stejnou sadu body prošla. Napětí se zobrazí pro každou křivky. Napětí 0 odpovídá nekonečné fyzické napětí vynucení křivky provést nejkratší způsob (rovné čáry) mezi body. Žádné fyzické napětí povolení křivka procházel nejméně celkový ohyb odpovídá napětí 1. S hodnotami napětí větší než 1 křivka se chová jako komprimovaný spring nahrány do použít delší cestu.  
  
 ![Základní křivky](./media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 Čtyři křivky v předchozí ilustraci sdílí stejnou tečný linku počátečního bodu. Tangens je linií od počátečního bodu na další bod podél křivky. Obdobně sdílené tangens na koncový bod je řádek je cílem vykreslování z koncového bodu na předchozí bod křivky.  
  
 K nakreslení křivky mohutnosti, je třeba instance <xref:System.Drawing.Graphics> třídy, <xref:System.Drawing.Pen>a celou řadu <xref:System.Drawing.Point> objekty instance <xref:System.Drawing.Graphics> třída poskytuje <xref:System.Drawing.Graphics.DrawCurve%2A> metodu, která vykreslí křivky a <xref:System.Drawing.Pen> uloží atributy křivky, například šířku čáry a barvu. Pole <xref:System.Drawing.Point> objekty ukládá body, které budou předány křivky. Následující příklad kódu ukazuje, jak nakreslení křivky mohutnosti, který prochází body v `myPointArray`. Třetí parametr je napětí.  
  
 [!code-csharp[LinesCurvesAndShapes#31](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Viz také:

- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Sestavování a kreslení křivek](constructing-and-drawing-curves.md)
