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
ms.openlocfilehash: 8399a56fca87704e10456a4cf8109d7c80d4db45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964406"
---
# <a name="how-to-create-a-path-gradient"></a>Postupy: Vytvoření přechodu cesty
<xref:System.Drawing.Drawing2D.PathGradientBrush> Třída umožňuje přizpůsobit způsob, jakým se tvar naplní postupně měnícími se barvami. Můžete například zadat jednu barvu středu cesty a jinou barvu pro hranici cesty. Můžete také zadat samostatné barvy pro každý z několika bodů podél hranice cesty.  
  
> [!NOTE]
> V rozhraní GDI+ je cesta posloupnost čar a křivek udržovaných <xref:System.Drawing.Drawing2D.GraphicsPath> objektem. Další informace o cestách rozhraní GDI+ najdete v tématech [grafické cesty v rozhraní GDI+](graphics-paths-in-gdi.md) a sestavování [a kreslení cest](constructing-and-drawing-paths.md).  

Příklady v tomto článku jsou metody, které jsou volány z obslužné rutiny <xref:System.Windows.Forms.Control.Paint> události ovládacího prvku.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Vyplnění elipsy přechodem cesty  
  
- Následující příklad vyplní elipsu pomocí štětce přechodu cesty. Barva středu je nastavena na modrou a barva hranice je nastavena na hodnotu azurová. Následující ilustrace znázorňuje Vyplněnou elipsu.  
  
     ![Cesta přechodu vyplní elipsu.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Ve výchozím nastavení se štětec přechodu cesty nerozšiřuje mimo hranici cesty. Použijete-li barevný štětec cesty k vyplnění obrázku, který přesahuje hranici cesty, oblast obrazovky mimo cestu nebude vyplněna.  
  
     Následující ilustrace ukazuje, co se stane, pokud změníte <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> volání v následujícím kódu na: `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`  
  
     ![Cesta k barevnému přechodu je delší než hranice cesty.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     Předchozí příklad kódu je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.PaintEventHandler>parametr e, který je parametrem.  
  
### <a name="to-specify-points-on-the-boundary"></a>Určení bodů na hranici  
  
- Následující příklad sestaví štětec přechodu cest z cesty ve tvaru hvězdičky. Kód nastaví <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> vlastnost, která nastaví barvu na těžiště hvězdy na červenou. Potom kód nastaví <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> vlastnost tak, aby určovala různé barvy (uložené `colors` v poli) na jednotlivých místech v `points` poli. Konečný příkaz kódu vyplní cestu ve tvaru hvězdičky pomocí štětce přechodu cest.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- Následující příklad kreslí přechod cesty bez <xref:System.Drawing.Drawing2D.GraphicsPath> objektu v kódu. Konkrétní <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> konstruktor v příkladu obdrží pole bodů, ale <xref:System.Drawing.Drawing2D.GraphicsPath> nevyžaduje objekt. Všimněte si také, že <xref:System.Drawing.Drawing2D.PathGradientBrush> se používá k naplnění obdélníku, nikoli cesty. Obdélník je větší než uzavřená cesta použitá k definování štětce, takže některý z obdélníků není vykreslen štětcem. Následující ilustrace znázorňuje obdélník (tečkovaná čára) a část obdélníku vykreslenou štětcem přechodu cesty: 
  
     ![Přechodová část vybarvené štětcem přechodu cesty](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Přizpůsobení cesty přechodu  
  
- Jedním ze způsobů, jak přizpůsobit cestu k barevnému štětce <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> , je nastavit jeho vlastnost. Fokus škáluje zadání vnitřní cesty, která leží uvnitř hlavní cesty. Prostřední barva se zobrazí všude uvnitř této vnitřní cesty, nikoli jenom ve středovém bodě.  
  
     Následující příklad vytvoří štětec přechodu cesty na základě eliptické cesty. Kód nastaví barvu hranice na modrou, nastaví barevnou plochu na azurová a pak pomocí štětce přechodu cest vyplní eliptický cestu.  
  
     Dále kód nastaví škálu fokusu pro štětec přechodu cest. Škála fokusu x je nastavená na 0,3 a měřítko pro fokus y je nastavené na 0,8. Kód volá <xref:System.Drawing.Graphics.TranslateTransform%2A> metodu <xref:System.Drawing.Graphics> objektu tak <xref:System.Drawing.Graphics.FillPath%2A> , aby následné volání vyplnilo elipsu, která je umístěna napravo od první elipsy.  
  
     Chcete-li zobrazit efekt měřítka fokusu, Představte si malou elipsu, která sdílí své centrum s hlavní elipsou. Malá (vnitřní) elipsa je hlavní elipsa škálovaná (o středu) horizontálně podle faktoru 0,3 a svisle podle faktoru 0,8. Při přesunu z hranice vnější elipsy na hranici vnitřní elipsy se barvy změní postupně z modré na azurová. Při přesunu z hranice vnitřní elipsy do sdíleného centra zůstane barva barva azurová.  
  
     Následující obrázek ukazuje výstup následujícího kódu. Elipsa vlevo je azurová pouze v centrálním bodě. Elipsa na pravé straně je azurová všude uvnitř vnitřní cesty.  
  
 ![Efekt přechodu pro škálu fokusu](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Přizpůsobení pomocí interpolace  
  
- Dalším způsobem přizpůsobení cesty pro barevný štětec je určit pole barev interpolace a pole pozic interpolace.  
  
     Následující příklad vytvoří štětec přechodu cesty na základě trojúhelníku. Kód nastaví <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> vlastnost štětce přechodu cesty tak, aby určovala pole barev interpolace (tmavě zelená, azurová, modrá) a pole pozic interpolace (0, 0,25, 1). Při přesunu z hranice trojúhelníku na středový bod se barva barev postupně mění z tmavé zelené na azurová a pak od azurová až po modrou. Změna z tmavě zelené na azurová nastane v 25% vzdálenosti od tmavě zelená po modrou.  
  
     Následující ilustrace znázorňuje trojúhelník vyplněný štětcem přechodu na vlastní cestu.  
  
     ![Trojúhelník vyplněný štětcem přechodu na vlastní cestu.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Nastavení centrálního bodu  
  
- Ve výchozím nastavení se středový bod štětce přechodu cesty nachází na těžiště cesty použité k vytvoření štětce. Polohu centrálního bodu můžete změnit nastavením <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> vlastnosti <xref:System.Drawing.Drawing2D.PathGradientBrush> třídy.  
  
     Následující příklad vytvoří štětec přechodu cesty na základě elipsy. Střed elipsy je v (70, 35), ale středový bod štětce přechodu cesty je nastaven na (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Následující ilustrace znázorňuje Vyplněnou elipsu a středový bod štětce přechodu cesty:  
  
     ![Cesta přechodu s plným elipsou a středovým bodem](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Středový bod štětce přechodu cesty můžete nastavit na místo mimo cestu, která byla použita k vytvoření štětce. Následující příklad nahrazuje volání pro nastavení <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> vlastnosti v předchozím kódu.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Následující obrázek ukazuje výstup s touto změnou:  
  
     ![Cesta k barevnému přechodu se středovým bodem mimo cestu](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     Na předchozí ilustraci nejsou body na pravé straně elipsy čistě modré (i když jsou velmi blízko). Barvy v přechodu jsou umístěny, jako kdyby byla dosažena výplň bodu (145, 35), kde barva byla čistě modrá (0, 0, 255). Ale výplň nikdy nedosáhne (145, 35), protože barevný štětec přechodu cesty se maluje jenom uvnitř své cesty.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklady jsou určeny pro použití s model Windows Forms a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což <xref:System.Windows.Forms.Control.Paint> je parametr obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- [Použití štětce přechodu k vyplnění obrazců](using-a-gradient-brush-to-fill-shapes.md)
