---
title: "Úvod k ovládacím prvkům Čára a Tvar (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e691d57c6de640c83556937eeddedf89e79b6846
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>Úvod k ovládacím prvkům Čára a Tvar (Visual Studio)
Ovládací prvky jazyka Visual Basic Power Pack Line a Shape jsou sadu tři grafické ovládacích prvků, které vám umožní kreslení čar a obrazců ve formulářích a kontejnerech. <xref:Microsoft.VisualBasic.PowerPacks.LineShape> Řízení slouží k vykreslení vodorovné, svislé a diagonálních čáry. <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> Řízení slouží k vykreslení kružnice a elipsy a <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> řízení slouží k vykreslení obdélníků a čtverce.  
  
## <a name="line-and-shape-controls"></a>Čára a Tvar – ovládací prvky  
 Line a Shape – ovládací prvky pro zapouzdření řadu grafiky metody, které jsou součástí <xref:System.Drawing> oboru názvů. To umožňuje kreslení čar a tvarů bez nutnosti vytváření grafických objektů, pera a štětce v jediném kroku. Složité grafické technologie například přechodu výplně lze provést pouze pomocí nastavení některé vlastnosti.  
  
 I když je také možné kreslení čar a obrazců pomocí metod grafiky, má několik výhod pro používání ovládacích prvků, čára a tvar:  
  
-   Grafické metody lze volat pouze za běhu. Line a Shape – ovládací prvky můžete přidat do formuláře v době návrhu. Díky tomu můžete zobrazit, jak vypadají a umístit je přesně; také mohou být přidány za běhu.  
  
-   Line a Shape – ovládací prvky jsou volitelný za běhu, jako poskytují události <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> a <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>. Výstupy z grafických metod nelze vybrat a neposkytují události.  
  
-   Ovládací prvky Line a Shape poskytují <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> a <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> metody, které vám umožňují řídit pořadí vykreslování v době návrhu a v době běhu. Pořadí vykreslování grafických metody lze řídit jenom změnou jejich pořadí spouštění v době běhu.  
  
-   Line a Shape – ovládací prvky jsou bez oken ovládací prvky; Tyto nemají žádné popisovače okna a proto používat méně systémových prostředků.  
  
### <a name="object-model"></a>Objektový Model  
 Line a Shape ovládací prvky jsou odvozeny od základní <xref:Microsoft.VisualBasic.PowerPacks.Shape> třídu, která definuje jejich sdílené vlastnosti, metod a události.  
  
 Následující obrázek znázorňuje hierarchie objektů Line a Shape.  
  
 ![Diagram hierarchie objektů Line a Shape](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Line a Shape hierarchie objektů  
  
 Odvozené <xref:Microsoft.VisualBasic.PowerPacks.LineShape> třída obsahuje vlastnosti, metod a události, které jsou jedinečné pro řádky. Odvozené <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> třída je základní třídu pro <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> a <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; obsahuje vlastnosti, metod a události, které jsou společné pro všechny obrazce. Můžete také odvodit z <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> a vytvořte vlastní `Shape` ovládací prvky.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> a <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> třídy lze použít k vykreslení kružnice, elips, obdélníků a obdélníky s zaoblenými hranami.  
  
 Po přidání ovládacího prvku řádku nebo tvaru do formuláře nebo kontejner, skrytý <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> je vytvořen objekt. <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> Jednání jako plátno pro obrazce v rámci každé ovládacího prvku kontejneru; každá <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> má odpovídající <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> , můžete k iteraci v rámci Line a Shape – ovládací prvky. Obrazce můžete přesunout z jednoho kontejneru na jiný pomocí vyjímání a vkládání nebo přetahování a vkládání. Když je poslední obrazec odebrán z kontejneru, <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> je také odebrána.  
  
> [!NOTE]
>  Ne všechny ovládací prvky kontejneru podporovat Line a Shape – ovládací prvky. Nelze hostování ovládacího prvku řádku nebo tvaru na <xref:System.Windows.Forms.TableLayoutPanel> nebo <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks>  
 [Postupy: kreslení čar pomocí ovládacího prvku LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [Postupy: kreslení obrazců pomocí OvalShape a RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [Postupy: povolení přecházení mezi tvary pomocí tabulátoru](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)
