---
title: Úvod k ovládacím prvkům Čára a Tvar (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
ms.openlocfilehash: 3623c2363f39150fd4bb202ba61ebd51df383ca8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699919"
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>Úvod k ovládacím prvkům Čára a Tvar (Visual Studio)
Ovládací prvky jazyka Visual Basic Power Pack čára a tvar představují sadu tři grafické prvky, které vám umožní kreslení čar a obrazců ve formulářích a kontejnery. <xref:Microsoft.VisualBasic.PowerPacks.LineShape> Ovládacího prvku se používá k nakreslení vodorovné, svislé a diagonální řádky. <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> Ovládacího prvku se používá k nakreslení kruhů a elipsy a <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ovládací prvek se používá k vykreslení obdélníků a čtverce.  
  
## <a name="line-and-shape-controls"></a>Čára a Tvar – ovládací prvky  
 Ovládací prvky čára a tvar zapouzdřují mnoho metod grafiky, které jsou součástí <xref:System.Drawing> oboru názvů. To umožňuje kreslení čar a obrazců v jediném kroku bez nutnosti vytváření grafických objektů, pera a stopy. Složitý grafický techniky, jako je například přechodu výplně dosáhnete nastavením jenom některé vlastnosti.  
  
 I když je také možné kreslení čar a obrazců pomocí metod grafiky, má několik výhod pro ovládací prvky čára a tvar pomocí:  
  
-   Grafické metody lze volat pouze v době běhu. Ovládací prvky čára a tvar můžete přidat do formuláře v době návrhu. Díky tomu můžete zobrazit, jak vypadají a umístit je přesně; je možné také přidat za běhu.  
  
-   Line a Shape ovládací prvky jsou volitelné za běhu, poskytuje události, jako <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> a <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>. Výstupy grafické metody se nedá vybrat a neposkytuje události.  
  
-   Ovládací prvky čára a tvar poskytují <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> a <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> metody, které vám umožňují řídit pořadí vykreslování v době návrhu a za běhu. Pořadí vykreslování grafiky metody lze ovládat pouze změnou jejich pořadí spouštění v době běhu.  
  
-   Ovládací prvky čára a tvar jsou ovládací prvky bez oken; Tyto nemají žádné popisovače okna a proto použít míň systémových prostředků.  
  
### <a name="object-model"></a>Objektový Model  
 Ovládací prvky čára a tvar jsou odvozeny od základní <xref:Microsoft.VisualBasic.PowerPacks.Shape> třídu, která definuje své sdílené vlastnosti, metody a události.  
  
 Následující obrázek znázorňuje hierarchii objektů čára a tvar.  
  
 ![Diagram hierarchie objektů čára a tvar](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Hierarchie objektů čára a tvar  
  
 Odvozená <xref:Microsoft.VisualBasic.PowerPacks.LineShape> třída obsahuje vlastnosti, metody a události, které jsou jedinečné pro řádky. Odvozená <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> třída je základní třídou pro <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> a <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; obsahuje vlastnosti, metody a události, které jsou společné pro všechny obrazce. Můžete také provádět odvozování z <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> vytvořit vlastní `Shape` ovládacích prvků.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> a <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> třídy lze použít ke kreslení kružnic, elipsy, obdélníky a obdélníky zaoblené rohy.  
  
 Při přidání řádku nebo tvar ovládacího prvku na formulář nebo kontejner, skrytý <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> je vytvořen objekt. <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> Slouží jako plátno pro obrazce v rámci každého kontejneru ovládacího prvku; každý <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> má odpovídající <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> , která umožňuje iterovat přes ovládací prvky čára a tvar. Tvary můžete přesunout z jednoho kontejneru na jiný pomocí vyjímání a vkládání nebo pomocí přetažení. Při poslední tvar je odstraněn z kontejneru, <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> je také odebrána.  
  
> [!NOTE]
>  Ne všechny ovládací prvky kontejneru podporují ovládací prvky čára a tvar. Ovládací prvek řádku nebo tvar nelze umístit na <xref:System.Windows.Forms.TableLayoutPanel> nebo <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks>
- [Postupy: Kreslení čar pomocí ovládacího prvku LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
- [Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
- [Postupy: Povolení přecházení mezi tvary pomocí tabulátoru](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)
