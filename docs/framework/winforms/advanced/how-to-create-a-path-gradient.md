---
title: 'Postupy: Vytvoření přechodu cesty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: c37a42a5905e34a995efbd73d332b7ef8f90e51d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603241"
---
# <a name="how-to-create-a-path-gradient"></a>Postupy: Vytvoření přechodu cesty
<xref:System.Drawing.Drawing2D.PathGradientBrush> Třída umožňuje přizpůsobit způsob vyplnění obrazce pomocí postupně Změna barev. Například můžete určit jednu barvu pro System center cesty a jinou barvu dané hranice lze cesty. Můžete také zadat samostatnou barvy pro každý z několika bodů podél hranici cesty.  
  
> [!NOTE]
>  Cesty v GDI + je posloupnost čar a křivek udržuje <xref:System.Drawing.Drawing2D.GraphicsPath> objektu. Další informace o rozhraní GDI + cesty, naleznete v tématu [cesty grafiky v GDI +](graphics-paths-in-gdi.md) a [Constructing a kreslení cest](constructing-and-drawing-paths.md).  

V příkladech v tomto článku jsou metody, které se volají z ovládacího prvku <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Chcete-li vyplnit elipsu přechodu cesty  
  
- Následující příklad zkopíruje elipsu s štětce přechodu cesty. Barva center je nastavena na modrou a hranice barva je nastavena na akvamarínovou. Následující obrázek znázorňuje vyplněnou elipsu.  
  
     ![Cesta přechodu výplně elipsu.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Ve výchozím nastavení nerozšiřuje štětce přechodu cesty mimo hranice cesty. Pokud používáte štětce přechodu cesty tak, aby vyplnil obrázek, která se rozpíná za hranice cesty, nebude vyplnění oblasti obrazovky mimo cestu.  
  
     Následující obrázek znázorňuje, co se stane, když změníte <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> volání v následující kód, který `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`:  
  
     ![Cesta přechodu rozšířenou nad rámec hranic cesty.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     V předchozím příkladu kódu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> e, což je parametr z <xref:System.Windows.Forms.PaintEventHandler>.  
  
### <a name="to-specify-points-on-the-boundary"></a>K určení bodů na hranici  
  
- Následující příklad vytvoří štětce přechodu cesty z cesty ve tvaru hvězdy. Nastaví kód <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> vlastnost, která nastavuje barvu na těžiště červené hvězdy. Potom nastaví kód <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> vlastnosti a určit různé barvy (uložené v `colors` pole) v jednotlivých fázích `points` pole. Příkaz konečné kódu, který vyplní do cesty štětce přechodu cestu ve tvaru hvězdy.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- Následující příklad nakreslí přechodu cesty bez <xref:System.Drawing.Drawing2D.GraphicsPath> objekt v kódu. Konkrétní <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> konstruktor v příkladu přijímá pole bodů, ale nevyžaduje <xref:System.Drawing.Drawing2D.GraphicsPath> objektu. Všimněte si také, že <xref:System.Drawing.Drawing2D.PathGradientBrush> slouží k naplnění obdélníku, ne cestu. Obdélníku je větší než uzavřené cesty používá k definování štětce, takže některé obdélníku není kresleno stopy. Následující obrázek znázorňuje obdélník (tečkovaná čára) a část obdélník kresleno štětce přechodu cesty: 
  
     ![Část barevného přechodu kresleno štětce přechodu cesty.](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Chcete-li přizpůsobit přechodu cesty  
  
- Jednou z možností přizpůsobení štětce přechodu cesty je nastavit jeho <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> vlastnost. Nastaví fokus zadat vnitřní cestu, kterou najdete v hlavní cestě. V této cestě vnitřní, nikoli pouze v případě System center, zobrazí se barvě pro střední všude.  
  
     Následující příklad vytvoří štětce přechodu cestu na základě elipsy cesty. Kód nastaví barvu ohraničení na modrou, nastaví barvě pro Střední akvamarínová a poté použije štětce přechodu cesty tak, aby vyplnil elipsy cestu.  
  
     V dalším kroku kód nastaví fokus měřítka štětce přechodu cesty. Detailní škálovací x je nastavena na 0,3 a detailní škálovací y je nastavena na 0,8. Kód volá <xref:System.Drawing.Graphics.TranslateTransform%2A> metodu <xref:System.Drawing.Graphics> objektu tak, aby následné volání <xref:System.Drawing.Graphics.FillPath%2A> vyplní elipsy, která se nachází vpravo od první tři tečky.  
  
     A vidět její účinek nastaví fokus, imagine malé elipsy, která sdílí jeho střed s hlavním elipsy. Malá (vnitřní) elipsa je hlavní elipsa škálovat (o jeho center) horizontálně faktorem 0,3 a svisle faktorem 0,8. Při přesunu z hranice vnější elipsa na hranici vnitřní elipsy, barva se změní postupně z modré na akvamarínovou. Při přesunu z hranice vnitřního elipsy do sdílené center akvamarínový barva zůstane.  
  
     Následující obrázek znázorňuje výstup následující kód. Tři tečky na levé straně je aqua pouze v případě System center. Se třemi tečkami na pravé straně je aqua kdekoli uvnitř vnitřní cesty.  
  
 ![Efekt přechodu z nastaví fokus](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Chcete-li přizpůsobit pomocí interpolace  
  
- Jinou možností přizpůsobení štětce přechodu cesty je zadání pole interpolační barvy a pole interpolace pozic.  
  
     Následující příklad vytvoří štětce přechodu cesty, který je založen na trojúhelník. Nastaví kód <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> vlastnost štětce přechodu cesty k určení pole interpolační barvy (akvamarínová, tmavě zelená, modrá) a pole interpolace pozice (0, 0,25, 1). Při přesunu do středového bodu z hranice část trojúhelníku, barva se změní postupně z tmavě zelená na akvamarínovou a pak azurová modrá. Změna tmavě zelená aqua probíhá 25 procent vzdálenost od tmavě zelená na modrou.  
  
     Následující obrázek znázorňuje trojúhelník vyplněny štětce přechodu na vlastní cestu.  
  
     ![Trojúhelník vyplněny štětce přechodu na vlastní cestu.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Chcete-li nastavit středový bod  
  
- Ve výchozím nastavení je středového bodu štětce přechodu cesty na těžiště cesty použité k sestavení kompletních stopy. Můžete změnit umístění středový bod tak, že nastavíte <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> vlastnost <xref:System.Drawing.Drawing2D.PathGradientBrush> třídy.  
  
     Následující příklad vytvoří štětce přechodu cestu podle elipsu. Centrum se třemi tečkami je na (70, 35), ale středového bodu štětce přechodu cesty je nastaven na (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Následující obrázek znázorňuje vyplněnou elipsu a středového bodu štětce přechodu cesty:  
  
     ![Cesta přechodu vyplněnou elipsu a System center bodu.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Můžete nastavit středového bodu štětce přechodu cesty do umístění mimo cestu, která byla použita k sestavení kompletních stopy. Následující příklad nahradí volání nastavení <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> vlastnost v předchozím kódu.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Následující obrázek znázorňuje výstup s touto změnou:  
  
     ![Cesta přechodu středový bod mimo cestu.](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     V předchozí ilustraci nejsou body úplně vpravo se třemi tečkami čistě modrá, (i když jsou velmi podobné). Barev v gradientu jsou umístěny, jako kdyby výplně dosáhne stavu (145, 35), kde barva by být čistě modré (0, 0, 255). Ale výplně nikdy dosáhne (145, 35) vzhledem k tomu, že pouze uvnitř jeho cesty jsou vykreslovány štětce přechodu cesty.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklady jsou určeny k použití pomocí Windows Forms a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- [Použití štětce přechodu k vyplnění obrazců](using-a-gradient-brush-to-fill-shapes.md)
