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
ms.openlocfilehash: e590732419396660221aa781e3c333311b6e88b4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505136"
---
# <a name="tilebrush-overview"></a>TileBrush – přehled
<xref:System.Windows.Media.TileBrush> objekty poskytují vám s velkou kontrolu nad jak Vymalování oblasti s obrázkem, <xref:System.Windows.Media.Drawing>, nebo <xref:System.Windows.Media.Visual>. Toto téma popisuje způsob použití <xref:System.Windows.Media.TileBrush> funkce, které chcete získat větší kontrolu nad jak <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, nebo <xref:System.Windows.Media.VisualBrush> jsou vykreslovány oblasti.  
  
  
<a name="prerequisite"></a>   
## <a name="prerequisites"></a>Požadavky  
 Informace o tom v tomto tématu, je vhodné pochopit, jak používat základní funkce <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, nebo <xref:System.Windows.Media.VisualBrush> třídy. Úvod do těchto typů, najdete v článku [Malování pomocí obrázků, kreseb a vizuálních](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>   
## <a name="painting-an-area-with-tiles"></a>Malování s dlaždicemi, které oblasti  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, jsou <xref:System.Windows.Media.VisualBrush> typů <xref:System.Windows.Media.TileBrush> objekty. Dlaždice štětce poskytnout vám s velkou kontrolu nad jak se oblast vybarvené obrázek, kreslení nebo vizuál. Například namísto pouze Malování imagi roztažené jeden v oblasti, můžete vykreslení oblasti řadu dlaždic bitové kopie, které společně tvoří masku.  
  
 V oblasti dlaždicového štětce vykreslování zahrnuje tři komponenty: obsah, že je základní dlaždice a výstupní oblasti.  
  
 ![TileBrush – komponenty](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Součásti s jednu dlaždici TileBrush  
  
 ![Součástí Objekt TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Součástí TileBrush pomocí vlastnosti TileMode objektu dlaždice  
  
 Výstupní oblasti je v oblasti se překreslit, jako <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> nebo <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>. Tento oddíl popisuje další dvě součásti <xref:System.Windows.Media.TileBrush>.  
  
<a name="brushcontent"></a>   
## <a name="brush-content"></a>Obsah štětce  
 Existují tři různé typy <xref:System.Windows.Media.TileBrush> a každý Vymaluje s jiným typem obsahu.  
  
-   Pokud je štětec <xref:System.Windows.Media.ImageBrush>, tento obsah je obrázek <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost určuje obsah značek <xref:System.Windows.Media.ImageBrush>.  
  
-   Pokud je štětce <xref:System.Windows.Media.DrawingBrush>, tento obsah je kresbu. <xref:System.Windows.Media.DrawingBrush.Drawing%2A> Vlastnost určuje obsah značek <xref:System.Windows.Media.DrawingBrush>.  
  
-   Pokud je štětce <xref:System.Windows.Media.VisualBrush>, tento obsah je vizuál. <xref:System.Windows.Media.VisualBrush.Visual%2A> Vlastnost určuje obsah <xref:System.Windows.Media.VisualBrush>.  
  
 Můžete zadat umístění a velikosti <xref:System.Windows.Media.TileBrush> obsahu pomocí <xref:System.Windows.Media.TileBrush.Viewbox%2A> vlastnost, i když je běžné ponechte <xref:System.Windows.Media.TileBrush.Viewbox%2A> nastavit na výchozí hodnotu. Ve výchozím nastavení <xref:System.Windows.Media.TileBrush.Viewbox%2A> konfigurován tak, aby zcela obsah na stopu. Další informace o konfiguraci <xref:System.Windows.Controls.Viewbox>, najdete v článku <xref:System.Windows.Controls.Viewbox> stránku vlastností.  
  
<a name="thebasetile"></a>   
## <a name="the-base-tile"></a>Základní dlaždice  
 A <xref:System.Windows.Media.TileBrush> projekty její obsah do základní dlaždice. <xref:System.Windows.Media.TileBrush.Stretch%2A> Ovládací prvky vlastnosti jak <xref:System.Windows.Media.TileBrush> je roztažený obsah tak, aby vyplnil základní dlaždice. <xref:System.Windows.Media.TileBrush.Stretch%2A> Vlastnost přijímá následující hodnoty, které jsou definované <xref:System.Windows.Media.Stretch> výčtu:  
  
-   <xref:System.Windows.Media.Stretch.None>Obsah: štětce není roztažená tak, aby vyplnil dlaždice.  
  
-   <xref:System.Windows.Media.Stretch.Fill>Přizpůsobit na dlaždici se mění velikost obsahu: štětce. Protože jsou nezávisle výšku a šířku obsah, nemusí být zachovaná původní poměr stran obsahu. To znamená může obsah na stopu pokřivení pro úplně naplnění dlaždice výstup.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>Tak, aby zcela v rámci dlaždice, se mění velikost obsahu: štětce. Poměr stran obsahu se zachovají.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>Tak, že zcela vyplní výstupní oblasti při zachování původního poměru stran obrázku obsah, se mění velikost obsahu: štětce.  
  
 Následující obrázek ukazuje různé <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavení.  
  
 ![Různá nastavení TileBrush Stretch](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 V následujícím příkladu, obsah <xref:System.Windows.Media.ImageBrush> je nastavit tak, že není roztáhnout tak, aby vyplnil výstupní oblasti.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Ve výchozím nastavení <xref:System.Windows.Media.TileBrush> vygeneruje jednu dlaždici (základní dlaždice) a roztáhne, aby tuto dlaždici pro úplně naplnění výstupní oblasti. Můžete změnit velikost a umístění základní dlaždice tak, že nastavíte <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnosti.  
  
<a name="basetilesize"></a>   
### <a name="base-tile-size"></a>Velikost základní dlaždice  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Vlastnost určuje velikost a umístění základní dlaždice a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnost určuje, zda <xref:System.Windows.Media.TileBrush.Viewport%2A> používá absolutní nebo relativní souřadnice. Pokud jsou relativní souřadnice, jsou relativní vzhledem k velikosti výstupní oblasti. Představuje bod (0,0) levého horního rohu výstupní oblasti a (1,1) představuje dolní pravému hornímu rohu výstupní oblasti. Určit, že <xref:System.Windows.Media.TileBrush.Viewport%2A> absolutní souřadnice používá vlastnost, nastavte <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnost <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
 Následující ilustrace ukazuje rozdíl ve výstupu mezi <xref:System.Windows.Media.TileBrush> s relativní a absolutní <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>. Všimněte si, že na každé obrázcích je vedle sebe vzor; Další část popisuje, jak zadat vzor dlaždice.  
  
 ![Absolutní a relativní zobrazení jednotky](../../../../docs/framework/wpf/graphics-multimedia/media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 V následujícím příkladu se používá image vytvořit dlaždici, která má šířku a výšku 50 %. Základní dlaždice se nachází na (0,0) výstupní oblasti.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 Následující příklad nastaví dlaždicích <xref:System.Windows.Media.ImageBrush> do 25 25 zařízeních nezávislých na pixelech. Protože <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> jsou absolutní, <xref:System.Windows.Media.ImageBrush> dlaždice jsou vždy 25 25 pixelů, bez ohledu na velikost oblasti se překreslit.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### <a name="tiling-behavior"></a>Chování dělení do bloků  
 A <xref:System.Windows.Media.TileBrush> při jeho základní dlaždice nevyplní zcela výstupní oblasti a režim dělení do bloků další pak vytvoří vedle sebe vzor <xref:System.Windows.Media.TileMode.None> je zadán. Když dlaždici dlaždicového štětce zcela nevyplní výstupní oblasti jeho <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost určuje, zda by měl být duplicitní základní dlaždice tak, aby vyplnil výstupní oblasti, a pokud ano, jak základní dlaždice by měl být duplicitní. <xref:System.Windows.Media.TileBrush.TileMode%2A> Vlastnost přijímá následující hodnoty, které jsou definované <xref:System.Windows.Media.TileMode> výčtu:  
  
-   <xref:System.Windows.Media.TileMode.None>: Pouze základní dlaždice se vykreslí.  
  
-   <xref:System.Windows.Media.TileMode.Tile>: Vykreslení základní dlaždice a zbývající oblast se vyplní opakováním základní dlaždice tak, že je vedle levého okraje na další a pravým okrajem jednu dlaždici podobně pro dolní a horní části.  
  
-   <xref:System.Windows.Media.TileMode.FlipX>: Stejná jako <xref:System.Windows.Media.TileMode.Tile>, ale jsou alternativní sloupce dlaždic Vodorovně obráceně.  
  
-   <xref:System.Windows.Media.TileMode.FlipY>: Stejná jako <xref:System.Windows.Media.TileMode.Tile>, ale jsou střídavé řádky dlaždice Svisle obráceně.  
  
-   <xref:System.Windows.Media.TileMode.FlipXY>: Kombinace <xref:System.Windows.Media.TileMode.FlipX> a <xref:System.Windows.Media.TileMode.FlipY>.  
  
 Následující obrázek ukazuje dělení do bloků různé režimy.  
  
 ![Různá nastavení vlastnosti TileMode objektu TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 V následujícím příkladu se používá bitovou kopii k vykreslení obdélníku, který je 100 pixelů na šířku a 100 pixelů na výšku. Tím, že nastavíte na stopu <xref:System.Windows.Media.TileBrush.Viewport%2A> byla nastavena do 0,0,0.25,0.25, se provádí na stopu je základní dlaždice bude 1/4 výstupní oblasti. Nástroj štětec <xref:System.Windows.Media.TileBrush.TileMode%2A> je nastavena na <xref:System.Windows.Media.TileMode.FlipXY>. tak, že vyplní obdélníku s řádky dlaždic.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Ukázka ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005)  
 [Ukázka VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049)
