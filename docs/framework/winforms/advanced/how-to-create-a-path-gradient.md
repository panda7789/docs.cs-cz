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
ms.openlocfilehash: a3a23d382e199b7ec70a8605041f7e464d1bffe0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529158"
---
# <a name="how-to-create-a-path-gradient"></a>Postupy: Vytvoření přechodu cesty
<xref:System.Drawing.Drawing2D.PathGradientBrush> Třída umožňuje přizpůsobit způsob vyplnění obrazce s postupně Změna barev. Můžete například zadat jeden barvu center cesty a jiné barvy hranice cesty. Můžete také zadat samostatnou barvy pro každý z několika bodů podél hranice cesty.  
  
> [!NOTE]
>  V [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], cesta je posloupnost čar a křivek udržované <xref:System.Drawing.Drawing2D.GraphicsPath> objektu. Další informace o [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] najdete v části cesty, [cesty grafiky v GDI +](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md) a [Constructing a kreslení cest](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md).  
  
### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Vyplníte elipsy přechodu cesty  
  
-   Následující příklad doplní elipsy s štětce přechodu cesty. Barva center je nastavena na hodnotu modrá a barva hranic je nastavena na hodnotu akvamarínová. Následující obrázek znázorňuje plné elipsy.  
  
     ![Cesty přechodu](../../../../docs/framework/winforms/advanced/media/pathgradient1.png "pathgradient1")  
  
     Ve výchozím nastavení neprodlužuje štětce přechodu cesty mimo hranice cesty. Pokud používáte štětce přechodu cesty k vyplnění obrázek, který se rozpíná za hranice cesty, nebude vyplněno oblasti obrazovky mimo cestu.  
  
     Následující obrázek znázorňuje, co se stane, když změníte <xref:System.Drawing.Graphics.FillEllipse%2A> volání v následující kód do `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`.  
  
     ![Cesty přechodu](../../../../docs/framework/winforms/advanced/media/pathgradient2.png "pathgradient2")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     V předchozím příkladu kódu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> e, což je parametr z <xref:System.Windows.Forms.PaintEventHandler>.  
  
### <a name="to-specify-points-on-the-boundary"></a>Určete body na hranici  
  
-   Následující příklad vytvoří štětce přechodu cesty z cesty ve tvaru hvězdičky. Nastaví kód <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> vlastnost, která nastavuje barvu v těžiště na červenou hvězdičkou. Potom nastaví kód <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> vlastnosti k určení různých barev (uložené v `colors` pole) v jednotlivých fázích `points` pole. Příkaz konečné kódu doplní cestu ve tvaru hvězdičky s štětce přechodu cesty.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   Následující příklad nevykresluje přechodu cesty bez <xref:System.Drawing.Drawing2D.GraphicsPath> objektu v kódu. Konkrétní <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> konstruktor v příkladu přijímá pole bodů, ale nevyžaduje <xref:System.Drawing.Drawing2D.GraphicsPath> objektu. Rovněž Pamatujte, že <xref:System.Drawing.Drawing2D.PathGradientBrush> se používá k vyplnění obdélníku, ne cesta. Rámeček je větší než uzavřené cesty použité k definovat štětec, takže některé rámečku není vykresluje podle stopy. Následující obrázek znázorňuje obdélníku (tečkovaná čára) a část rámeček vykresluje podle štětce přechodu cesty.  
  
     ![Přechodu](../../../../docs/framework/winforms/advanced/media/gradient4.png "gradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Chcete-li přizpůsobit přechodu cesty  
  
-   Je možné přizpůsobit štětce přechodu cesty k nastavení jeho <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> vlastnost. Fokus měřítka zadejte vnitřní cestu, který se nachází uvnitř hlavní cestu. Barva center se zobrazí everywhere uvnitř této vnitřní cesty a nikoli pouze v bodě center.  
  
     Následující příklad vytvoří štětce přechodu cesty na základě eliptické cesty. Kód nastaví barvu hranic na modrou, nastaví barvu center akvamarínová a pak použije štětce přechodu cesty k zadání eliptické cestu.  
  
     V dalším kroku kód nastaví fokus měřítka štětce přechodu cesty. Měřítko fokus x je nastaveno na 0,3 a měřítko fokus y je nastaveno na 0,8. Volání kódu <xref:System.Drawing.Graphics.TranslateTransform%2A> metodu <xref:System.Drawing.Graphics> objektu tak, aby následných volání <xref:System.Drawing.Graphics.FillPath%2A> doplní elipsy, která se nachází vpravo od první třemi tečkami.  
  
     Účinek měřítka fokus najdete Představte si malé elipsy, který sdílí jeho center hlavní třemi tečkami. Malé třemi tečkami (vnitřní) je hlavní elipsy škálovat (o jeho center) vodorovně faktorem 0,3 a svisle faktorem 0,8. Jak přesunout z hranice vnější elipsy na hranici vnitřní elipsy barvu změny postupně z modré akvamarínová. Když přesouváte z hranice vnitřní elipsy k centru sdílené aqua barva zůstanou.  
  
     Následující obrázek znázorňuje výstup následující kód. Se třemi tečkami na levé straně je akvamarínová pouze v bodě center. Se třemi tečkami na pravé straně je akvamarínová everywhere uvnitř vnitřní cesty.  
  
 ![Přechodu](../../../../docs/framework/winforms/advanced/media/focusscales1nogamma.png "focusscales1NoGamma")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Chcete-li přizpůsobit s interpolace  
  
-   Jiný způsob, jak přizpůsobit štětce přechodu cesty je zadání pole interpolace barvy a pole interpolace pozic.  
  
     Následující příklad vytvoří podle trojúhelník štětce přechodu cesty. Nastaví kód <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> vlastnost štětce přechodu cesty k určení pole barev interpolace (tmavý zelená, azurová, modrá) a pole interpolace pozice (0,25, 0, 1). Jak přesunout z hranice trojúhelníku středy barvu změní postupně z tmavý zelená do akvamarínová a pak z akvamarínová na modrou. Tato změna z tmavý zelená akvamarínová probíhá 25 procent vzdálenost od tmavý zelená na modrou.  
  
     Následující obrázek znázorňuje trojúhelníček vyplněnou štětce přechodu vlastní cesta.  
  
     ![Cesty přechodu](../../../../docs/framework/winforms/advanced/media/pathgradient4.png "pathgradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Chcete-li nastavit středový bod  
  
-   Ve výchozím nastavení je bod center štětce přechodu cesty na těžiště použitý k vytvoření stopy cesty. Můžete změnit umístění centrálního bodu nastavením <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> vlastnost <xref:System.Drawing.Drawing2D.PathGradientBrush> třídy.  
  
     Následující příklad vytvoří podle elipsy štětce přechodu cesty. Střed se třemi tečkami je na (70, 35), ale středový bod štětce přechodu cesty je nastaven na (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Následující obrázek znázorňuje plné elipsy a středový bod štětce přechodu cesty.  
  
     ![Cesty přechodu](../../../../docs/framework/winforms/advanced/media/pathgradient5.png "pathgradient5")  
  
-   Můžete nastavit středový bod štětce přechodu cestu do umístění mimo cestu, která byla použita k vytvoření stopy. Následující příklad nahrazuje volání nastavení <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> vlastnost v předchozí kód.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Následující obrázek znázorňuje výstup v této změně.  
  
     ![Cesty přechodu](../../../../docs/framework/winforms/advanced/media/pathgradient6.png "pathgradient6")  
  
     V předchozí ilustraci nejsou body na pravém elipsy čistý blue, (i když jsou velmi podobné). Barvy v přechodu jsou umístěny, jako kdyby výplně dosáhne stavu (145, 35), kde barvu by čistý blue (0, 0, 255). Ale výplně nikdy dosáhne (145, 35) protože štětce přechodu cesty vybarví pouze uvnitř cesty.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozích příkladech jsou navrženy pro používání s formuláři Windows a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Použití štětce přechodu k vyplnění obrazců](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
