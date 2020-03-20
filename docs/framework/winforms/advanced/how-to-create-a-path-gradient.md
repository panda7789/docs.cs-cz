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
ms.openlocfilehash: cf4dc558c008fb8adfc327a6a894a428e985df03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182636"
---
# <a name="how-to-create-a-path-gradient"></a>Postupy: Vytvoření přechodu cesty
Třída <xref:System.Drawing.Drawing2D.PathGradientBrush> umožňuje přizpůsobit způsob, jakým vyplníte tvar s postupně se měnícími barvami. Můžete například zadat jednu barvu pro střed cesty a jinou barvu pro hranici cesty. Můžete také určit samostatné barvy pro každý z několika bodů podél hranice cesty.  
  
> [!NOTE]
> V GDI+ je cesta posloupnost čar a <xref:System.Drawing.Drawing2D.GraphicsPath> křivek udržovaných objektem. Další informace o cestách GDI+ naleznete [v tématu Grafické cesty v GDI+](graphics-paths-in-gdi.md) a [Konstrukční a kreslicí cesty](constructing-and-drawing-paths.md).  

Příklady v tomto článku jsou metody, které <xref:System.Windows.Forms.Control.Paint> jsou volány z obslužné rutiny události ovládacího prvku.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Vyplnění elipsy přechodem cesty  
  
- Následující příklad vyplní elipsu stopou přechodu cesty. Středová barva je nastavena na modrou a hranice je nastavena na aqua. Následující obrázek znázorňuje vyplněnou elipsu.  
  
     ![Cesta přechodu vyplní elipsu.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Ve výchozím nastavení se stopa přechodu cesty nerozšiřuje mimo hranice cesty. Pokud použijete stopu přechodu cesty k vyplnění polymeje, která přesahuje hranice cesty, oblast obrazovky mimo cestu nebude vyplněna.  
  
     Následující obrázek znázorňuje, <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> co se stane, `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`pokud změníte volání v následujícím kódu na :  
  
     ![Cesta přechodu přesahová hranice cesty.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     Předchozí příklad kódu je určen pro použití s Windows <xref:System.Windows.Forms.PaintEventArgs> Forms a vyžaduje <xref:System.Windows.Forms.PaintEventHandler>e, což je parametr .  
  
### <a name="to-specify-points-on-the-boundary"></a>Určení bodů na hranici  
  
- Následující příklad vytvoří stopu přechodu cesty z cesty ve tvaru hvězdy. Kód nastaví <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> vlastnost, která nastaví barvu na středhvězdy na červenou. Pak kód nastaví <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> vlastnost určit různé barvy `colors` (uložené v poli) `points` v jednotlivých bodech v poli. Příkaz konečného kódu vyplní cestu ve tvaru hvězdy stopou přechodu cesty.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- Následující příklad nakreslí přechod <xref:System.Drawing.Drawing2D.GraphicsPath> cesty bez objektu v kódu. Konkrétní <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> konstruktor v příkladu obdrží pole bodů, ale <xref:System.Drawing.Drawing2D.GraphicsPath> nevyžaduje objekt. Všimněte si <xref:System.Drawing.Drawing2D.PathGradientBrush> také, že se používá k vyplnění obdélníku, nikoli cesty. Obdélník je větší než uzavřená cesta použitá k definování stopy, takže některé obdélník není malované stopou. Následující obrázek znázorňuje obdélník (tečkovaná čára) a část obdélníku namalovanou stopou přechodu cesty:
  
     ![Část přechodu vybarvená stopou přechodu cesty.](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Přizpůsobení přechodu cesty  
  
- Jedním ze způsobů, jak přizpůsobit stopu přechodu cesty, je nastavit její <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> vlastnost. Měřítko fokusu určuje vnitřní cestu, která leží uvnitř hlavní cesty. Středová barva se zobrazuje všude uvnitř této vnitřní cesty, nikoli pouze ve středovém bodě.  
  
     Následující příklad vytvoří stopu přechodu cesty založenou na eliptické cestě. Kód nastaví barvu hranice na modrou, nastaví středovou barvu na aqua a pak použije stopu přechodu cesty k vyplnění eliptické cesty.  
  
     Dále kód nastaví měřítko fokusu stopy přechodu cesty. Měřítko zaostření x je nastaveno na 0,3 a měřítko zaostření y je nastaveno na 0,8. Kód volá <xref:System.Drawing.Graphics.TranslateTransform%2A> metodu <xref:System.Drawing.Graphics> objektu tak, aby <xref:System.Drawing.Graphics.FillPath%2A> následné volání vyplní elipsu, která je napravo od první elipsy.  
  
     Chcete-li zobrazit efekt měřítko fokus, představte si malou elipsu, která sdílí jeho střed s hlavní elipsou. Malá (vnitřní) elipsa je hlavní elipsa měřítko (asi jeho středu) vodorovně o faktor 0,3 a svisle faktorem 0,8. Při přechodu z hranice vnější elipsy na hranici vnitřní elipsy se barva postupně mění z modré na aqua. Při přechodu z hranice vnitřní elipsy do sdíleného středu zůstane barva aqua.  
  
     Následující obrázek znázorňuje výstup následujícího kódu. Elipsa vlevo je aqua pouze ve středu. Elipsa vpravo je aqua všude uvnitř vnitřní cesty.  
  
 ![Přechodový efekt zaostřovacích měřítek](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Přizpůsobení pomocí interpolace  
  
- Dalším způsobem, jak přizpůsobit stopu přechodu cesty, je určit pole interpolačních barev a pole interpolačních pozic.  
  
     Následující příklad vytvoří stopu přechodu cesty založenou na trojúhelníku. Kód nastaví <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> vlastnost stopy přechodu cesty k určení pole interpolačních barev (tmavě zelená, aqua, modrá) a pole interpolačních pozic (0, 0,25, 1). Jak se pohybujete od hranice trojúhelníku ke středovému bodu, barva se postupně mění z tmavě zelené na aqua a pak z aqua na modrou. Změna z tmavě zelené na aqua se děje v 25 procentech vzdálenosti od tmavě zelené na modrou.  
  
     Následující obrázek znázorňuje trojúhelník vyplněný stopou přechodu vlastní cesty.  
  
     ![Trojúhelník vyplněný vlastní stopou přechodu cesty.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Nastavení středového bodu  
  
- Ve výchozím nastavení je středový bod stopy přechodu cesty v centru cesty použité k vytvoření stopy. Umístění středového bodu můžete změnit nastavením vlastnosti <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> třídy. <xref:System.Drawing.Drawing2D.PathGradientBrush>  
  
     Následující příklad vytvoří stopu přechodu cesty založenou na elipsy. Střed elipsy je (70, 35), ale středový bod stopy přechodu cesty je nastaven na (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Následující obrázek znázorňuje vyplněnou elipsu a středový bod stopy přechodu cesty:  
  
     ![Cesta přechodu s vyplněnou elipsou a středovým bodem.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Středový bod stopy přechodu cesty můžete nastavit na místo mimo cestu, která byla použita k vytvoření stopy. Následující příklad nahradí volání nastavit <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> vlastnost v předchozím kódu.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Následující obrázek znázorňuje výstup s touto změnou:  
  
     ![Cesta přechodu se středovým bodem mimo cestu.](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     Na předchozím obrázku body zcela vpravo elipsy nejsou čistě modré (i když jsou velmi blízko). Barvy v přechodu jsou umístěny, jako by výplň dosáhla bodu (145, 35), kde by barva byla čistě modrá (0, 0, 255). Výplň však nikdy nedosáhne (145, 35), protože štětec přechodu cesty maluje pouze uvnitř své cesty.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklady jsou určeny pro použití s <xref:System.Windows.Forms.PaintEventArgs> `e`windows forms a vyžadují <xref:System.Windows.Forms.Control.Paint> , což je parametr obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také

- [Použití štětce přechodu k vyplnění obrazců](using-a-gradient-brush-to-fill-shapes.md)
