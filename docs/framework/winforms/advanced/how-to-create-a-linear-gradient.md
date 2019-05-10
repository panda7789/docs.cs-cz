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
ms.openlocfilehash: 953a1944073a8cb5b19ef072e2a523baec3a5605
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650007"
---
# <a name="how-to-create-a-linear-gradient"></a>Postupy: Vytvoření lineárního přechodu
Rozhraní GDI + poskytuje vodorovné, svislé a diagonální lineárními přechody. Ve výchozím nastavení změní barvu v lineárním přechodem jednotně. Lineární přechod však můžete přizpůsobit tak, aby se barva mění, nerovnoměrné způsobem.  

> [!NOTE]
> V příkladech v tomto článku jsou metody, které se volají z ovládacího prvku <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  

Následující příklad zkopíruje řádku elipsu a obdélníku s vodorovné štětec lineárního přechodu.  
  
<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Konstruktoru přijímá čtyři argumenty: dva body a dvěma barvami. První bod (0, 10) souvisí s první barvy (červená), a druhý bod (200, 10) souvisí s druhou barvou (modrá). Dle očekávání, řádku z (0, 10) na (200, 10) změní z red blue postupně.  
  
 10s v bodech (0, 10) a (200, 10) nejsou důležité. Důležité je, že dva body mají stejné souřadnice druhý – řádek je propojí je vodorovný. Elipsy a obdélníku také změnit postupně z red blue jako bod se souřadnicemi vodorovné přejde od 0 do 200.  
  
 Následující obrázek znázorňuje řádku, na tři tečky a obdélníku. Všimněte si, že barva přechodu opakuje jako bod se souřadnicemi vodorovné zvýší nad 200.  
  
 ![Linear Gradient](./media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>Určený horizontální lineárními přechody  
  
- Předejte modře neprůhledné červené a neprůhledné jako třetí a čtvrtý argument, v uvedeném pořadí.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 V předchozím příkladu složky barvy změnit lineárně při přesunu z vodorovné souřadnice 0 vodorovné souřadnice 200. Bod, jehož první souřadnice je uprostřed mezi 0 a 200 bude mít například komponentu modrý uprostřed mezi 0 a 255.  
  
 Rozhraní GDI + umožňuje upravit způsob, jakým barvu se liší od jednomu z okrajů přechod na druhý. Předpokládejme, že chcete vytvořit štětce přechodu od černé se změní na červený podle následující tabulky.  
  
|Vodorovné souřadnice|Součásti RGB|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 Upozorňujeme, že červené poloviční intenzitou při vodorovné bod se souřadnicemi je pouze 20 procent způsob od 0 do 200.  
  
 Následující příklad nastaví <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> vlastnost pro přidružení k tři relativní pozice tři relativní míry. Stejně jako v předchozí tabulce je přidružen k relativní pozice 0.2 relativní intenzita 0,5. Kód vyplní elipsu a obdélníku s štětce přechodu.  
  
 Následující obrázek znázorňuje výsledný tři tečky a obdélník.  
  
 ![Linear Gradient](./media/cslineargradient2.png "cslineargradient2")  

### <a name="to-customize-linear-gradients"></a>Chcete-li přizpůsobit lineárními přechody  
  
- Předejte červeně neprůhledný černý a neprůhledné jako třetí a čtvrtý argument, v uvedeném pořadí.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 Přechody v předchozích příkladech byly vodorovné; To znamená barva se změní postupně při přesunu podél jakékoli vodorovnou čáru. Můžete také definovat svislé barevné přechody a Úhlopříčný přechody.  
  
 Následující příklad předá body (0, 0) a (200, 100) <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> konstruktoru. Modrá barva je přidružené k (0, 0), a je asociována zelenou barvu (200, 100). Řádek (s 10 Šířka pera) a elipsa jsou vyplněny hodnotou štětec lineárního přechodu.  
  
 Následující obrázek znázorňuje řádku a na tři tečky. Všimněte si, že barvu v elipsa změny postupně při přesunu podél žádný řádek, který je paralelní řádku procházející (0, 0) a (200, 100).  
  
 ![Linear Gradient](./media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>Chcete-li vytvořit Úhlopříčný lineárními přechody  
  
- Předejte zeleně neprůhledné modré a neprůhledné jako třetí a čtvrtý argument, v uvedeném pořadí.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Viz také:

- [Použití štětce přechodu k vyplnění obrazců](using-a-gradient-brush-to-fill-shapes.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
