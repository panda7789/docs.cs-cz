---
title: TileBrush – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
ms.openlocfilehash: 99bcc8695206030a381d71df2dda495867d3e9c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187099"
---
# <a name="tilebrush-overview"></a>TileBrush – přehled
<xref:System.Windows.Media.TileBrush>Objekty poskytují velkou kontrolu nad tím, jak je <xref:System.Windows.Media.Drawing>oblast <xref:System.Windows.Media.Visual>namalována obrazem , nebo . Toto téma popisuje <xref:System.Windows.Media.TileBrush> použití funkcí k získání <xref:System.Windows.Media.ImageBrush>větší <xref:System.Windows.Media.DrawingBrush>kontroly nad tím, jak oblast , nebo <xref:System.Windows.Media.VisualBrush> maluje.  

<a name="prerequisite"></a>
## <a name="prerequisites"></a>Požadavky  
 Chcete-li porozumět tomuto tématu, je užitečné pochopit, <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>jak <xref:System.Windows.Media.VisualBrush> používat základní funkce , nebo třídy. Úvod k těmto typům naleznete v tématu [Malování s obrázky, kresby a vizuály](painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>
## <a name="painting-an-area-with-tiles"></a>Malování plochy dlaždicemi  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush> jsou <xref:System.Windows.Media.TileBrush> typy objektů. Štětce dlaždic poskytují velkou kontrolu nad tím, jak je oblast namalována obrázkem, výkresem nebo vizuálem. Například místo pouhého malování oblasti jedním roztaženým obrazem můžete malovat oblast řadou dlaždic obrazu, které vytvářejí vzorek.  
  
 Malování oblasti štětcem dlaždic zahrnuje tři součásti: obsah, základní dlaždici a výstupní oblast.  
  
 ![Komponenty TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Součásti TileBrush s jednou dlaždicí  
  
 ![Součásti dlaždicové dlaždiceBrush](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Součásti TileBrush s TileMode dlaždice  
  
 Výstupní oblast je plocha, která je <xref:System.Windows.Shapes.Shape.Fill%2A> malována, například a <xref:System.Windows.Shapes.Ellipse> nebo <xref:System.Windows.Controls.Control.Background%2A> of . <xref:System.Windows.Controls.Button> V následujících částech jsou popsány <xref:System.Windows.Media.TileBrush>další dvě součásti .  
  
<a name="brushcontent"></a>
## <a name="brush-content"></a>Obsah stopy  
 Existují tři různé <xref:System.Windows.Media.TileBrush> typy a každý barvy s jiným typem obsahu.  
  
- Pokud je stopa <xref:System.Windows.Media.ImageBrush>, tento obsah <xref:System.Windows.Media.ImageBrush.ImageSource%2A> je obrázek Vlastnost <xref:System.Windows.Media.ImageBrush>určuje obsah .  
  
- Pokud je stopa <xref:System.Windows.Media.DrawingBrush>, tento obsah je výkres. Vlastnost <xref:System.Windows.Media.DrawingBrush.Drawing%2A> určuje obsah <xref:System.Windows.Media.DrawingBrush>.  
  
- Pokud je stopa <xref:System.Windows.Media.VisualBrush>, tento obsah je vizuál. Vlastnost <xref:System.Windows.Media.VisualBrush.Visual%2A> určuje obsah <xref:System.Windows.Media.VisualBrush>.  
  
 Můžete určit umístění a rozměry <xref:System.Windows.Media.TileBrush> obsahu <xref:System.Windows.Media.TileBrush.Viewbox%2A> pomocí vlastnosti, i když <xref:System.Windows.Media.TileBrush.Viewbox%2A> je běžné ponechat sadu na jeho výchozí hodnotu. Ve výchozím <xref:System.Windows.Media.TileBrush.Viewbox%2A> nastavení je nakonfigurován tak, aby zcela obsahoval obsah stopy. Další informace o konfiguraci aplikace naleznete na <xref:System.Windows.Controls.Viewbox>stránce vlastností. <xref:System.Windows.Controls.Viewbox>  
  
<a name="thebasetile"></a>
## <a name="the-base-tile"></a>Základní dlaždice  
 A <xref:System.Windows.Media.TileBrush> promítá jeho obsah na základní dlaždici. Vlastnost <xref:System.Windows.Media.TileBrush.Stretch%2A> určuje, <xref:System.Windows.Media.TileBrush> jak je obsah roztažen tak, aby vyplnil základní dlaždici. Vlastnost <xref:System.Windows.Media.TileBrush.Stretch%2A> přijímá následující hodnoty definované výčtu: <xref:System.Windows.Media.Stretch>  
  
- <xref:System.Windows.Media.Stretch.None>: Obsah stopy není napnutý, aby vyplnil dlaždici.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Velikost obsahu stopy se změní tak, aby se vešel do dlaždice. Vzhledem k tomu, že se velikost výšky a šířky obsahu mění nezávisle, nemusí být zachován původní poměr stran obsahu. To znamená, že obsah stopy může být pokřivený, aby bylo možné zcela vyplnit výstupní dlaždici.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Velikost obsahu stopy se změní tak, aby se zcela vešel do dlaždice. Poměr stran obsahu je zachován.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Velikost obsahu stopy se změní tak, aby zcela vyplnil výstupní oblast při zachování původního poměru stran obsahu.  
  
 Následující obrázek znázorňuje různá <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavení.  
  
 ![Různá nastavení roztažení tilebrush](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 V následujícím příkladu je <xref:System.Windows.Media.ImageBrush> obsah a nastaven tak, aby se neroztáhl tak, aby vyplnil výstupní oblast.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Ve výchozím <xref:System.Windows.Media.TileBrush> nastavení generuje jedna dlaždice (základní dlaždice) a roztáhne tuto dlaždici tak, aby zcela vyplnila výstupní oblast. Velikost a umístění základní dlaždice můžete změnit <xref:System.Windows.Media.TileBrush.Viewport%2A> nastavením vlastností a. <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>  
  
<a name="basetilesize"></a>
### <a name="base-tile-size"></a>Základní velikost dlaždice  
 Vlastnost <xref:System.Windows.Media.TileBrush.Viewport%2A> určuje velikost a umístění základní dlaždice a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnost určuje, <xref:System.Windows.Media.TileBrush.Viewport%2A> zda je zadán pomocí absolutní nebo relativní souřadnice. Pokud jsou souřadnice relativní, jsou relativní vzhledem k velikosti výstupní oblasti. Bod (0,0) představuje levý horní roh výstupní oblasti a (1,1) představuje pravý dolní roh výstupní oblasti. Chcete-li <xref:System.Windows.Media.TileBrush.Viewport%2A> určit, že vlastnost používá <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> absolutní <xref:System.Windows.Media.BrushMappingMode.Absolute>souřadnice, nastavte vlastnost na .  
  
 Následující obrázek znázorňuje rozdíl <xref:System.Windows.Media.TileBrush> ve výstupu <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>mezi a s relativní versus absolutní . Všimněte si, že ilustrace každý zobrazit kachlová vzoru; v další části je popsáno, jak určit vzorek dlaždice.  
  
 ![Absolutní a relativní výřezové jednotky](./media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 V následujícím příkladu se obrázek používá k vytvoření dlaždice, která má šířku a výšku 50 %. Základní dlaždice je umístěna na (0,0) výstupní oblasti.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 Další příklad nastaví dlaždice <xref:System.Windows.Media.ImageBrush> na 25 x 25 pixelů nezávislých na zařízení. Vzhledem <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> k tomu, že jsou absolutní, <xref:System.Windows.Media.ImageBrush> dlaždice jsou vždy 25 x 25 pixelů, bez ohledu na velikost oblasti, která je malovaná.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>
### <a name="tiling-behavior"></a>Chování dlaždic  
 A <xref:System.Windows.Media.TileBrush> vytvoří dlaždicový vzor, když jeho základní dlaždice není zcela vyplnit výstupní <xref:System.Windows.Media.TileMode.None> oblast a dlažba režim jiný pak je určen. Pokud dlaždice štětce dlaždic dlaždice zcela nevyplňuje výstupní oblast, její <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost určuje, zda má být základní dlaždice duplikována, aby vyplnila výstupní oblast, a pokud ano, jak by měla být základní dlaždice duplikována. Vlastnost <xref:System.Windows.Media.TileBrush.TileMode%2A> přijímá následující hodnoty definované výčtu: <xref:System.Windows.Media.TileMode>  
  
- <xref:System.Windows.Media.TileMode.None>: Je nakreslena pouze základní dlaždice.  
  
- <xref:System.Windows.Media.TileMode.Tile>: Základní dlaždice je nakreslena a zbývající plocha je vyplněna opakováním základní dlaždice tak, aby pravý okraj jedné dlaždice sousedí s levým okrajem dalšího a podobně pro dolní a horní.  
  
- <xref:System.Windows.Media.TileMode.FlipX>: Stejné <xref:System.Windows.Media.TileMode.Tile>jako , ale alternativní sloupce dlaždic jsou převráceny vodorovně.  
  
- <xref:System.Windows.Media.TileMode.FlipY>: Stejné <xref:System.Windows.Media.TileMode.Tile>jako , ale alternativní řádky dlaždic jsou převráceny svisle.  
  
- <xref:System.Windows.Media.TileMode.FlipXY>: Kombinace <xref:System.Windows.Media.TileMode.FlipX> a <xref:System.Windows.Media.TileMode.FlipY>.  
  
 Následující obrázek znázorňuje různé režimy dlaždic.  
  
 ![Různá nastavení TileBrush TileMode](./media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 V následujícím příkladu se obraz používá k malování obdélníku, který je 100 pixelů široký a 100 pixelů vysoký. Nastavením stopy <xref:System.Windows.Media.TileBrush.Viewport%2A> byla nastavena na 0,0,0,25,0,25, základní dlaždice stopy je provedena jako 1/4 výstupní oblasti. Štětec <xref:System.Windows.Media.TileBrush.TileMode%2A> je nastaven <xref:System.Windows.Media.TileMode.FlipXY>na . tak, aby vyplnil obdélník s řádky dlaždic.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Témata s postupy](brushes-how-to-topics.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
- [Ukázka imagebrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [Ukázka visualbrushu](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
