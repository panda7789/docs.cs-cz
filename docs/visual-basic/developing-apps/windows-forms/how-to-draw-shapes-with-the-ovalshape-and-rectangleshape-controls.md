---
title: 'Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
ms.openlocfilehash: fe937236332591f6065e618c49ca5cf2c54b987c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701219"
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a>Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape (Visual Studio)
Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ovládací prvek nakreslit kruhy nebo elipsy ve formuláři nebo kontejneru, v době návrhu i době běhu. Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ovládací prvek nakreslit čtverce, obdélníku nebo obdélníky zaoblené rohy ve formuláři nebo kontejneru. Tento ovládací prvek lze také použít pro kreslení tvarů v době návrhu i době běhu.  
  
 Můžete přizpůsobit vzhled tvaru tak, že změníte šířku, barvu a styl ohraničení. Pozadí obrazec je transparentní ve výchozím nastavení; můžete přizpůsobit zobrazení plnou barvu, vzor, přechodovou výplní (přechod z jedné barvy k jinému) nebo obrázek na pozadí.  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a>Chcete-li nakreslit jednoduchý obrazec v době návrhu  
  
1.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> nebo <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ovládacího prvku **sady Visual Basic PowerPack** kartu (instalaci najdete v tématu [ovládací prvky jazyka Visual Basic Power Pack](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) v **nástrojů** do ovládacího prvku formulář nebo kontejneru.  
  
2.  Přetažením úchytů a přesunout obslužné rutiny na velikost a umístění obrazce.  
  
     Můžete také změnit velikost a umístění obrazce tak, že změníte `Size` a `Position` vlastnosti **vlastnosti** okna.  
  
     Chcete-li vytvořit obdélník zaoblené rohy, vyberte `CornerRadius` vlastnost v **vlastnosti** okno a nastavte ho na hodnotu, která je větší než 0.  
  
3.  V **vlastnosti** okna, Volitelně můžete nastavit další vlastnosti ke změně vzhledu tvar.  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a>Chcete-li nakreslit jednoduchý obrazec za běhu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz**.  
  
2.  V **přidat odkaz** dialogu **Microsoft.VisualBasic.PowerPacks.VS**a potom klikněte na tlačítko **OK**.  
  
3.  V **Editor kódu**, přidejte `Imports` nebo `using` příkazu v horní části modulu:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Přidejte následující kód `Event` postup:  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a>Přizpůsobení obrazce  
 Pokud použijete výchozí nastavení <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> a <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ovládací prvky jsou zobrazeny s plnou černým ohraničením, které je jeden pixel široké a průhledné pozadí. Šířky, stylu a barvy ohraničení můžete změnit nastavením vlastnosti. Další vlastnosti umožňují změnit na pozadí obrazce plnou barvu, vzor, přechod nebo image.  
  
 Než změníte na pozadí tvaru, byste měli znát několik vlastností interakci.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> Nastavení vlastnost nemá žádný vliv, pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> přepsání <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.  
  
-   Pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> je nastavena na hodnotu vzor jako <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> nebo <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, vzor se zobrazí v <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>. Zobrazí se na pozadí v <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>za předpokladu, že <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Aby bylo možné zobrazit přechodovou výplní <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> musí být vlastnost nastavena na <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> a <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> vlastnost musí být nastavena na hodnotu jiné než <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.  
  
-   Nastavení <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> vlastností pro bitovou kopii přepíše všechna ostatní nastavení na pozadí.  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a>Chcete-li nakreslit kruh, který má vlastní ohraničení  
  
1.  Přetáhněte `OvalShape` ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.  
  
2.  V **vlastnosti** okno v `Size` , nastavit `Height` a `Width` na stejné hodnoty.  
  
3.  Nastavte `BorderColor` vlastnost na požadovanou barvu.  
  
4.  Nastavte `BorderStyle` vlastnost na libovolnou hodnotu jinou než `Solid`.  
  
5.  Nastavte `BorderWidth` velikosti, který chcete v pixelech.  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a>Chcete-li nakreslit kruh, který má plné barvy  
  
1.  Přetáhněte `OvalShape` ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.  
  
2.  V **vlastnosti** okno v `Size` , nastavit `Height` a `Width` na stejné hodnoty.  
  
3.  Nastavte `BackColor` vlastnost na požadovanou barvu.  
  
4.  Nastavte `BackStyle` vlastnost `Opaque`.  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a>Chcete-li nakreslit kruh, který má výplň vzorkem  
  
1.  Přetáhněte `OvalShape` ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.  
  
2.  V **vlastnosti** okno v `Size` , nastavit `Height` a `Width` na stejné hodnoty.  
  
3.  Nastavte `BackColor` vlastnost na požadovanou barvu má pozadí.  
  
4.  Nastavte `BackStyle` vlastnost `Opaque`.  
  
5.  Nastavte `FillColor` nastavte barvu, která chcete použít pro vzorek.  
  
6.  Nastavte `FillStyle` vlastnost na libovolnou hodnotu jinou než `Transparent` nebo `Solid`.  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a>Chcete-li nakreslit kruh, který má přechodovou výplní  
  
1.  Přetáhněte `OvalShape` ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.  
  
2.  V **vlastnosti** okno v `Size` , nastavit `Height` a `Width` na stejné hodnoty.  
  
3.  Nastavte `FillColor` nastavte barvu, která chcete použít pro počáteční barvu.  
  
4.  Nastavte `FillGradientColor` nastavte barvu, která chcete použít pro koncovou barvu.  
  
5.  Nastavte `FillGradientStyle` vlastnost na hodnotu jinou než `None`.  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a>Chcete-li nakreslit kruh, který je vyplněna bitovou kopii  
  
1.  Přetáhněte `OvalShape` ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.  
  
2.  V **vlastnosti** okno v `Size` , nastavit `Height` a `Width` na stejné hodnoty.  
  
3.  Vyberte `BackgroundImage` vlastnosti a kliknutím **tlačítko se třemi tečkami** tlačítko (...).  
  
4.  V **vybrat prostředek** dialogové okno, vyberte obrázek, který se zobrazí. Pokud nejsou uvedeny žádné prostředky bitové kopie, klikněte na tlačítko **Import** a přejděte do umístění obrázku.  
  
5.  Klikněte na tlačítko **OK** vložit obrázek.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>
- <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>
- [Úvod k ovládacím prvkům Čára a Tvar](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [Postupy: Kreslení čar pomocí ovládacího prvku LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
