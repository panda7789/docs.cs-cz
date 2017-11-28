---
title: "TileBrush – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f759a56233e8cf2b1c1d39862706be518fefe43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="tilebrush-overview"></a>TileBrush – přehled
<xref:System.Windows.Media.TileBrush>objekty poskytují s značnou část řídit způsob vykreslení oblast obsahující bitovou kopii, <xref:System.Windows.Media.Drawing>, nebo <xref:System.Windows.Media.Visual>. Toto téma popisuje postup použití <xref:System.Windows.Media.TileBrush> funkce, které chcete získat lepší kontrolu nad postupy <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, nebo <xref:System.Windows.Media.VisualBrush> vybarví oblast.  
  
  
<a name="prerequisite"></a>   
## <a name="prerequisites"></a>Požadavky  
 Zjistit, v tomto tématu, je vhodné pochopit, jak využívat základní funkce, které <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, nebo <xref:System.Windows.Media.VisualBrush> třídy. Úvod do těchto typů, najdete v článku [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>   
## <a name="painting-an-area-with-tiles"></a>Vykreslování oblast s dlaždice  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, jsou <xref:System.Windows.Media.VisualBrush> jsou typy <xref:System.Windows.Media.TileBrush> objekty. Dlaždice štětce nabízejí značnou část ovládat, jak je pomocí bitové kopie, kreslení nebo visual vykresluje oblast. Například místo právě vykreslování oblast s jedné roztažené image, můžete malovat oblast s řadou dlaždice obrázků, které vytvářejí se vzorem.  
  
 Vykreslování oblast štětcem dlaždice zahrnuje tři komponenty: obsahu, základní dlaždice a oblasti výstup.  
  
 ![Součásti TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Součástí TileBrush se jedna dlaždice  
  
 ![Součástí Objekt TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Součástí TileBrush se vlastnosti TileMode objektu dlaždice  
  
 Výstup oblast je oblast se vykresluje jako <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> nebo <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>. Tento oddíl popisuje další dvě součásti <xref:System.Windows.Media.TileBrush>.  
  
<a name="brushcontent"></a>   
## <a name="brush-content"></a>Obsah štětce  
 Existují tři různé typy <xref:System.Windows.Media.TileBrush> a každý vybarví s jiným typem obsahu.  
  
-   Pokud je štětce <xref:System.Windows.Media.ImageBrush>, tento obsah je obrázek, který <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost určuje obsah <xref:System.Windows.Media.ImageBrush>.  
  
-   Pokud je stopy <xref:System.Windows.Media.DrawingBrush>, tento obsah je výkresu. <xref:System.Windows.Media.DrawingBrush.Drawing%2A> Vlastnost určuje obsah <xref:System.Windows.Media.DrawingBrush>.  
  
-   Pokud je stopy <xref:System.Windows.Media.VisualBrush>, tento obsah je vizuál. <xref:System.Windows.Media.VisualBrush.Visual%2A> Vlastnost určuje obsah <xref:System.Windows.Media.VisualBrush>.  
  
 Můžete zadat umístění a rozměry <xref:System.Windows.Media.TileBrush> obsahu pomocí <xref:System.Windows.Media.TileBrush.Viewbox%2A> vlastnost, i když je běžné ponechte <xref:System.Windows.Media.TileBrush.Viewbox%2A> nastavit na výchozí hodnotu. Ve výchozím nastavení <xref:System.Windows.Media.TileBrush.Viewbox%2A> nakonfigurovaný tak, aby zcela obsahovat stopy obsah. Další informace o konfiguraci <xref:System.Windows.Controls.Viewbox>, najdete v článku <xref:System.Windows.Controls.Viewbox> stránku vlastností.  
  
<a name="thebasetile"></a>   
## <a name="the-base-tile"></a>Základní dlaždice  
 A <xref:System.Windows.Media.TileBrush> projekty jeho obsah do základní dlaždice. <xref:System.Windows.Media.TileBrush.Stretch%2A> Ovládací prvky vlastnost jak <xref:System.Windows.Media.TileBrush> obsah je roztažen tak, aby vyplnění základní dlaždice. <xref:System.Windows.Media.TileBrush.Stretch%2A> Vlastnost přijímá následující hodnoty, které jsou definované <xref:System.Windows.Media.Stretch> výčtu:  
  
-   <xref:System.Windows.Media.Stretch.None>Obsah: štětce není roztažená k vyplnění dlaždici.  
  
-   <xref:System.Windows.Media.Stretch.Fill>Obsah: štětce přizpůsobí dlaždici. Protože k obsahu výška a šířka jsou nezávisle škálovat, nemusí být zachována původní poměr stran obsahu. To znamená může obsah štětce pokřivení úplně naplnit dlaždici výstup.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>Obsah: štětce je škálovat tak, aby odpovídal zcela v dlaždici. Poměr stran k obsahu je zachovaná.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>Obsah: štětce je škálovat tak, že úplně vyplní oblasti výstupu při zachování původní poměr stran k obsahu.  
  
 Následující obrázek ukazuje různými <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavení.  
  
 ![Různá nastavení TileBrush Stretch](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 V následujícím příkladu, obsah <xref:System.Windows.Media.ImageBrush> je nastaven tak, aby ji není roztáhnou tak, aby vyplnil celou oblast výstup.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Ve výchozím nastavení <xref:System.Windows.Media.TileBrush> vygeneruje jednu dlaždici (základní dlaždice) a roztahovány tuto dlaždici úplně vyplnil celou oblast výstup. Velikost a umístění základní dlaždice můžete změnit nastavením <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnosti.  
  
<a name="basetilesize"></a>   
### <a name="base-tile-size"></a>Velikost základní dlaždice  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Vlastnost určuje velikost a umístění dlaždici základní a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnost určuje, zda <xref:System.Windows.Media.TileBrush.Viewport%2A> je zadán pomocí souřadnic absolutní nebo relativní. Pokud jsou relativní souřadnice, jsou relativní vzhledem k velikosti oblasti výstup. Představuje bodu (0,0) levém horním rohu výstupní oblasti a (1,1) představuje dolní pravému hornímu rohu oblasti výstup. Chcete-li určit, že <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost používá absolutní souřadnice, nastavte <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnost <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
 Následující obrázek ukazuje rozdíl ve výstupu mezi <xref:System.Windows.Media.TileBrush> s relativní a absolutní <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>. Všimněte si, že na každém obrázcích vedle sebe vzor; Další část popisuje, jak zadat vzor dlaždice.  
  
 ![Absolutní a relativní jednotky zobrazení](../../../../docs/framework/wpf/graphics-multimedia/media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 V následujícím příkladu je image použít k vytvoření dlaždice, který má šířka a výška 50 %. Základní dlaždice se nachází v (0,0) výstupní oblasti.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 Další příklad nastaví dlaždicích <xref:System.Windows.Media.ImageBrush> na 25 podle 25 zařízení nezávislé pixelů. Protože <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> jsou absolutní, <xref:System.Windows.Media.ImageBrush> dlaždice jsou vždy 25 podle 25 pixelů, bez ohledu na velikost oblasti se vykresluje.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### <a name="tiling-behavior"></a>Chování vedle sebe  
 A <xref:System.Windows.Media.TileBrush> při jeho základní dlaždice zcela nevyplní oblasti výstupu a režim dlaždice jiných potom vytvoří vedle sebe vzor <xref:System.Windows.Media.TileMode.None> je zadán. Pokud dlaždice štětce dlaždice zcela nevyplní oblasti výstup jeho <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost určuje, jestli dlaždici základní by měl být duplicitní k vyplnění oblasti výstup, a pokud ano, jak základní dlaždice musí být duplicitní. <xref:System.Windows.Media.TileBrush.TileMode%2A> Vlastnost přijímá následující hodnoty, které jsou definované <xref:System.Windows.Media.TileMode> výčtu:  
  
-   <xref:System.Windows.Media.TileMode.None>: Pouze základní dlaždice se nevykreslí.  
  
-   <xref:System.Windows.Media.TileMode.Tile>: Vykreslením základní dlaždice a zbývající oblast se vyplní opakováním dlaždici základní tak, aby byla přiléhající k levý okraj na další a pravé hrany jeden dlaždice podobně pro dolní a horní.  
  
-   <xref:System.Windows.Media.TileMode.FlipX>: Stejná jako <xref:System.Windows.Media.TileMode.Tile>, ale jsou alternativní sloupce dlaždic Vodorovně obráceně.  
  
-   <xref:System.Windows.Media.TileMode.FlipY>: Stejná jako <xref:System.Windows.Media.TileMode.Tile>, ale jsou alternativní řádky dlaždic Svisle obráceně.  
  
-   <xref:System.Windows.Media.TileMode.FlipXY>: Kombinace <xref:System.Windows.Media.TileMode.FlipX> a <xref:System.Windows.Media.TileMode.FlipY>.  
  
 Následující obrázek ukazuje dlaždice různé režimy.  
  
 ![Různá nastavení vlastnosti TileMode objektu TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 V následujícím příkladu je obrázku použita k vyplnění obdélníku, která je 100 pixelů na šířku a výšku 100 pixelů. Nastavením stopy <xref:System.Windows.Media.TileBrush.Viewport%2A> byla nastavena na 0,0,0.25,0.25, základní dlaždice stopy přišla za 1/4 výstupní oblasti. Stopy <xref:System.Windows.Media.TileBrush.TileMode%2A> je nastaven na <xref:System.Windows.Media.TileMode.FlipXY>. tak, že vyplní rámeček s řádky dlaždic.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [Malování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Postupy: témata](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [Zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Objekt ImageBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [Ukázka VisualBrush](http://go.microsoft.com/fwlink/?LinkID=160049)
