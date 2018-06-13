---
title: 'Postupy: Vytvoření lineárního přechodu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: 9eeedf1ef92bdf6e5e2724eeca5060765b0778f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522457"
---
# <a name="how-to-create-a-linear-gradient"></a>Postupy: Vytvoření lineárního přechodu
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje vodorovné, svislé a diagonálních lineární přechody. Ve výchozím nastavení změní barvu v lineárního přechodu jednotně. Lineárního přechodu však můžete přizpůsobit tak, že změní barvu způsobem neuniformní.  
  
 Následující příklad doplní řádku, třemi tečkami a obdélníku štětcem vodorovné lineárního přechodu.  
  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Konstruktor přijímá čtyři argumenty: dva body a dvě barvy. První bod (0, 10) je přidružen první barvy (červená) a druhý bod (200, 10) souvisí s druhou barvu (modrá). Jak by jste očekávali, řádku čerpají z (0, 10) na (200, 10) se změní z červené na modrou postupně.  
  
 10s v bodech (50, 10) a (200, 10) nejsou důležité. Důležité je, že dva body mají stejné souřadnice druhý – řádek jejich připojením je vodorovné. Se třemi tečkami a rámeček také změnit postupně z červené na modrou jako souřadnici vodorovné přejde od 0 do 200.  
  
 Následující obrázek znázorňuje řádek se třemi tečkami a rámeček. Všimněte si, že barvy opakuje jako souřadnici vodorovné zvýší nad 200.  
  
 ![Lineárního přechodu](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>Chcete-li použít vodorovné lineární přechody  
  
-   Předejte modře neprůhledného červené a neprůhledného jako třetí a čtvrtý argument, v uvedeném pořadí.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 V předchozím příkladu komponenty barvu změnit lineárně jako přesunout z vodorovné souřadnice 0 vodorovné souřadnice 200. Například bod, jehož první souřadnice je uprostřed mezi 0 a 200 bude mít blue komponenty, která je uprostřed mezi 0 a 255.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Umožňuje upravit způsob, jakým barvu, která se liší od jeden okraj přechodu na druhý. Předpokládejme, že chcete vytvořit štětce přechodu, který změní z černé na červený podle následující tabulky.  
  
|Vodorovné souřadnice|RGB součásti|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 Upozorňujeme, že komponentu red se poloviční intenzitou jenom 20 procent způsob 200 od 0 po vodorovné souřadnice.  
  
 Následující příklad nastavuje <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> vlastnost <xref:System.Drawing.Drawing2D.LinearGradientBrush> objekt, který chcete přidružit tři relativní intenzity tři relativní umístění. Jako v předchozí tabulce je spojeno s relativní pozici 0,2 relativní intenzitou 0,5. Kód doplní elipsy a obdélníku s štětce přechodu.  
  
 Následující obrázek znázorňuje výsledné elipsy a obdélník.  
  
 ![Lineárního přechodu](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")  
  
### <a name="to-customize-linear-gradients"></a>Chcete-li přizpůsobit lineární přechody  
  
-   Předejte červeně neprůhledného černé a neprůhledného jako třetí a čtvrtý argument, v uvedeném pořadí.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 Přechody v předchozích ukázkách byly vodorovné; To znamená barva změní postupně jako přesunout společně žádné vodorovném řádku. Můžete také definovat přechody vertikální a diagonálních přechody.  
  
 Následující příklad předá body (0, 0) a (200, 100) <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> konstruktor. Je přidružen modrou barvu (0, 0), a je přidružen zelenou barvu (200, 100). Řádek (s pera šířka 10) a elipsy jsou vyplněny lineární štětce přechodu.  
  
 Následující obrázek znázorňuje řádku a se třemi tečkami. Všimněte si, že barvu v změny elipsy postupně jako přesunout společně žádné řádku, je paralelní na řádek prošla (0, 0) a (200, 100).  
  
 ![Lineárního přechodu](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>Chcete-li vytvořit diagonálních lineární přechody  
  
-   Předejte zeleně neprůhledného modré a neprůhledného jako třetí a čtvrtý argument, v uvedeném pořadí.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Viz také  
 [Použití štětce přechodu k vyplnění obrazců](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
