---
title: "Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53d91d10cc4735bbae521d17d05045cc7ea75fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a>Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape (Visual Studio)
Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> řízení k vykreslení kroužky nebo elips ve formuláři nebo kontejneru, v době návrhu i v době běhu. Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> řízení k vykreslení čtverce, obdélníku nebo obdélníků se zaoblenými hranami ve formuláři nebo kontejneru. Také můžete tento ovládací prvek pro kreslení tvarů v době návrhu i v době běhu.  
  
 Vzhled obrazce můžete přizpůsobit tak, že změníte šířku, barvu a styl ohraničení. Na pozadí obrazce je transparentní ve výchozím nastavení; můžete přizpůsobit na pozadí na plnou barvou, vzor, výplň přechodem (přechod z jedné barvy do jiného) nebo bitovou kopii.  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a>Kreslení jednoduchý obrazec v době návrhu  
  
1.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> nebo <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> řídit z **PowerPacks jazyka Visual Basic** karta (instalaci naleznete v tématu [ovládací prvky jazyka Visual Basic Power Pack](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) v **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.  
  
2.  Přetáhněte velikost a přesuňte velikost a umístění tvaru.  
  
     Můžete také upravit velikost a umístění tvaru změnou `Size` a `Position` vlastnosti v **vlastnosti** okno.  
  
     Chcete-li vytvořit obdélník se zaoblenými hranami, vyberte `CornerRadius` vlastnost v **vlastnosti** okno a nastavte ji na hodnotu, která je větší než 0.  
  
3.  V **vlastnosti** okno, Volitelně můžete nastavit další vlastnosti změnit vzhled tvaru.  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a>Kreslení obrazce jednoduché za běhu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz na**.  
  
2.  V **přidat odkaz na** dialogové okno, vyberte **Microsoft.VisualBasic.PowerPacks.VS**a potom klikněte na **OK**.  
  
3.  V **Editor kódu**, přidejte `Imports` nebo `using` příkaz v horní části modulu:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Přidejte následující kód v `Event` postup:  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a>Přizpůsobení tvarů  
 Pokud použijete výchozí nastavení <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> a <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ovládací prvky jsou zobrazeny s plnou černé ohraničení, které je jeden pixel široká a průhledné pozadí. Šířky, stylu a barvy ohraničení můžete změnit nastavením vlastnosti. Další vlastnosti umožňují změnit pozadí obrazce plnou barvou, vzor, přechod nebo bitovou kopii.  
  
 Než změníte na pozadí obrazce, byste měli vědět, jak několik vlastností komunikovat.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> Nastavení vlastnost nemá žádný vliv, pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> přepsání <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.  
  
-   Pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> vlastnost nastavena na hodnotu vzor, jako <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> nebo <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, vzoru se zobrazí v <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>. Zobrazí se na pozadí v <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, za předpokladu, že <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Aby bylo možné zobrazit výplň přechodem <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> musí být nastavena na <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> a <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> vlastnost musí být nastavena na hodnotu než <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.  
  
-   Nastavení <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> vlastnost pro bitovou kopii přepíše všechna ostatní nastavení pozadí.  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a>Kreslení kruh, který má vlastní ohraničení  
  
1.  Přetáhněte `OvalShape` řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.  
  
2.  V **vlastnosti** okno v `Size` vlastnost, nastavte `Height` a `Width` na stejné hodnoty.  
  
3.  Nastavte `BorderColor` vlastnost na požadovanou barvu.  
  
4.  Nastavte `BorderStyle` vlastnost na jakoukoli jinou hodnotu než `Solid`.  
  
5.  Nastavte `BorderWidth` na velikost, které chcete v pixelech.  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a>Kreslení kruh, který má plnou výplň  
  
1.  Přetáhněte `OvalShape` řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.  
  
2.  V **vlastnosti** okno v `Size` vlastnost, nastavte `Height` a `Width` na stejné hodnoty.  
  
3.  Nastavte `BackColor` vlastnost na požadovanou barvu.  
  
4.  Nastavte `BackStyle` vlastnost `Opaque`.  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a>Kreslení kruh, který má výplň vzorkem  
  
1.  Přetáhněte `OvalShape` řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.  
  
2.  V **vlastnosti** okno v `Size` vlastnost, nastavte `Height` a `Width` na stejné hodnoty.  
  
3.  Nastavte `BackColor` vlastnost na barvu, která chcete použít pro na pozadí.  
  
4.  Nastavte `BackStyle` vlastnost `Opaque`.  
  
5.  Nastavte `FillColor` vlastnost na barvu, která chcete použít pro vzoru.  
  
6.  Nastavte `FillStyle` vlastnost na jakoukoli jinou hodnotu než `Transparent` nebo `Solid`.  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a>Kreslení kruh, který má výplň přechodem  
  
1.  Přetáhněte `OvalShape` řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.  
  
2.  V **vlastnosti** okno v `Size` vlastnost, nastavte `Height` a `Width` na stejné hodnoty.  
  
3.  Nastavte `FillColor` vlastnost na barvu, která chcete použít pro počáteční barvu.  
  
4.  Nastavte `FillGradientColor` vlastnost na barvu, která chcete použít pro koncovou barvu.  
  
5.  Nastavte `FillGradientStyle` vlastnost na hodnotu jinou než `None`.  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a>Kreslení kruh, který je vyplněn bitovou kopii  
  
1.  Přetáhněte `OvalShape` řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.  
  
2.  V **vlastnosti** okno v `Size` vlastnost, nastavte `Height` a `Width` na stejné hodnoty.  
  
3.  Vyberte `BackgroundImage` vlastnost a klikněte na **třemi tečkami** tlačítko (...).  
  
4.  V **vyberte prostředek** dialogové okno, vyberte bitovou kopii k zobrazení. Pokud nejsou uvedeny žádné prostředky obrázků, klikněte na tlačítko **Import** a přejděte do umístění bitové kopie.  
  
5.  Klikněte na tlačítko **OK** vložit bitovou kopii.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [Úvod k čára a tvar – ovládací prvky](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [Postupy: kreslení čar pomocí ovládacího prvku LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
