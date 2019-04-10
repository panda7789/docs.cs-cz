---
title: Přehled vykreslovaných objektů
ms.date: 03/30/2017
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
ms.openlocfilehash: c065b06e7542913ae7fb495a0f69ff09dc4238b9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325511"
---
# <a name="drawing-objects-overview"></a>Přehled vykreslovaných objektů
Toto téma představuje <xref:System.Windows.Media.Drawing> objektů a popisuje, jak se dají použít k efektivní kreslení tvarů, rastrové obrázky, text a média. Použít <xref:System.Windows.Media.Drawing> objekty při vytváření klipart, Malování <xref:System.Windows.Media.DrawingBrush>, nebo použijte <xref:System.Windows.Media.Visual> objekty.  

<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Co je objekt kreslení?  
 A <xref:System.Windows.Media.Drawing> objektu popisuje viditelného obsahu, jako je tvar, rastrový obrázek, video nebo řádek textu. Různé druhy drawings popisují různé typy obsahu. Následuje seznam typy vykreslení objektů.  
  
-   <xref:System.Windows.Media.GeometryDrawing> – Nakreslí obrazec.  
  
-   <xref:System.Windows.Media.ImageDrawing> – Kreslení obrázku.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> – Kreslení textu.  
  
-   <xref:System.Windows.Media.VideoDrawing> – Přehraje zvuk nebo video soubor.  
  
-   <xref:System.Windows.Media.DrawingGroup> – Kreslení jiných kreslení. Pomocí vykreslení skupiny můžete kombinovat další drawings do jednoho kompozitní kresby.  
  
 <xref:System.Windows.Media.Drawing> objekty jsou univerzální; Existuje mnoho způsobů, můžete použít <xref:System.Windows.Media.Drawing> objektu.  
  
-   Můžete ho zobrazit jako bitovou kopii pomocí <xref:System.Windows.Media.DrawingImage> a <xref:System.Windows.Controls.Image> ovládacího prvku.  
  
-   Můžete ji použít <xref:System.Windows.Media.DrawingBrush> k vykreslení objektu, například <xref:System.Windows.Controls.Page.Background%2A> z <xref:System.Windows.Controls.Page>.  
  
-   Slouží k popisu vzhled <xref:System.Windows.Media.DrawingVisual>.  
  
-   Slouží k vytvoření výčtu obsah <xref:System.Windows.Media.Visual>.  
  
 WPF obsahuje jiné typy objektů, které jsou schopny kreslení tvarů, rastrové obrázky, text a média. Například můžete použít také <xref:System.Windows.Shapes.Shape> objektů pro kreslení tvarů a <xref:System.Windows.Controls.MediaElement> ovládací prvek obsahuje jiný způsob, jak přidat video do vaší aplikace. Takže pokud byste měli použít <xref:System.Windows.Media.Drawing> objekty? Když jste vzdát úroveň funkce framework zlepší výkon, nebo pokud potřebujete <xref:System.Windows.Freezable> funkce. Protože <xref:System.Windows.Media.Drawing> objekty neobsahují podporu pro [rozložení](../advanced/layout.md)vstup a zaměřit, poskytují výhod vyššího výkonu upgradovaného, proto je ideální pro popis pozadími, klipart a pro kreslení nižší úrovně s <xref:System.Windows.Media.Visual> objekty.  
  
 Protože jde o typ <xref:System.Windows.Freezable> objektu, <xref:System.Windows.Media.Drawing> objekty získat několik speciální funkce, které zahrnují následující: mohou být deklarovány jako [prostředky](../advanced/xaml-resources.md), sdíleny mezi více objektů, jen pro čtení ke zlepšení výkon, klonování a provedli bezpečné pro vlákna. Další informace o různých funkcí poskytovaných službou <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Nakreslit obrazec  
 Chcete-li nakreslit obrazec, můžete použít <xref:System.Windows.Media.GeometryDrawing>. Geometrie kreslení <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> vlastnost popisuje obrazec nakreslit, jeho <xref:System.Windows.Media.GeometryDrawing.Brush%2A> vlastnost popisuje, jak by měl překreslit vnitřní část obrazce a jeho <xref:System.Windows.Media.GeometryDrawing.Pen%2A> vlastnost popisuje, jak má být vykreslena obrysu.  
  
 Následující příklad používá <xref:System.Windows.Media.GeometryDrawing> nakreslit obrazec. Tvar je popsán <xref:System.Windows.Media.GeometryGroup> a dva <xref:System.Windows.Media.EllipseGeometry> objekty. Vnitřní obrazce vymalováním s <xref:System.Windows.Media.LinearGradientBrush> a obrysu je vykreslen pomocí <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.  
  
 Tento příklad vytvoří následující <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing dvě symbol tří teček](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Kompletní příklad naleznete v tématu [vytvoření objektu GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 Další <xref:System.Windows.Media.Geometry> třídy, jako například <xref:System.Windows.Media.PathGeometry> vám umožní vytvářet složitější tvary tak, že vytvoříte křivky a oblouky. Další informace o <xref:System.Windows.Media.Geometry> objekty, najdete [přehled geometrie](geometry-overview.md).  
  
 Další informace o dalších způsobech pro kreslení tvarů, které nepoužívají <xref:System.Windows.Media.Drawing> objekty, najdete [tvary a základní kresby v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Vykreslení obrázku  
 Vykreslení obrázku, použijte <xref:System.Windows.Media.ImageDrawing>. <xref:System.Windows.Media.ImageDrawing> Objektu <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> vlastnost popisuje bitovou kopii k vykreslení a jeho <xref:System.Windows.Media.ImageDrawing.Rect%2A> vlastnost definuje oblast, ve kterém je vykreslen na obrázku.  
  
 Následující příklad nakreslí obrázek do obdélníku v bodu (75,75), který je 100 x 100 pixelů. Je vidět na následujícím obrázku <xref:System.Windows.Media.ImageDrawing> vytvořené v příkladu. Šedé ohraničení byl přidán do zobrazit hranice <xref:System.Windows.Media.ImageDrawing>.  
  
 ![100 × 100 ImageDrawing vykreslovat &#40;75,75&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100 x 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Další informace o imagích najdete v tématu [Imaging přehled](imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Přehrání média (jenom kód)  
  
> [!NOTE]
>  I když je možné deklarovat <xref:System.Windows.Media.VideoDrawing> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete načíst a přehrávání médií pomocí kódu. Přehrávání videa v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], použití <xref:System.Windows.Controls.MediaElement> místo.  
  
 Chcete-li přehrát zvuk nebo video soubor, je použít <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer>. Existují dva způsoby, jak načíst a přehrávání médií. První je použití <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> sami a druhý je způsob, jak vytvořit vlastní <xref:System.Windows.Media.MediaTimeline> pro použití s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Při distribuci média s aplikací, nelze použít mediální soubor jako projekt prostředků, stejně jako obrázek. V souboru projektu, musíte místo toho nastavte typ média na `Content` a nastavte `CopyToOutputDirectory` k `PreserveNewest` nebo `Always`.  
  
 Přehrávání médií bez nutnosti vytvářet vlastní <xref:System.Windows.Media.MediaTimeline>, proveďte následující kroky.  
  
1. Vytvoření <xref:System.Windows.Media.MediaPlayer> objektu.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Použití <xref:System.Windows.Media.MediaPlayer.Open%2A> metoda načíst do souboru média.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Vytvoření <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Zadejte velikost a umístění pro kreslení média tak, že nastavíte <xref:System.Windows.Media.VideoDrawing.Rect%2A> vlastnost <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Nastavte <xref:System.Windows.Media.VideoDrawing.Player%2A> vlastnost <xref:System.Windows.Media.VideoDrawing> s <xref:System.Windows.Media.MediaPlayer> jste vytvořili.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Použití <xref:System.Windows.Media.MediaPlayer.Play%2A> metodu <xref:System.Windows.Media.MediaPlayer> a spustit přehrávání média.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Následující příklad používá <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer> pro přehrání videa souboru jednou.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Chcete-li získat další časování ovládat média, použijte <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> objekty. <xref:System.Windows.Media.MediaTimeline> Umožňuje určit, zda by měla opakovat na video. Použití <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.VideoDrawing>, proveďte následující kroky:  
  
1. Deklarovat <xref:System.Windows.Media.MediaTimeline> a nastavte jeho chování časování.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Vytvoření <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.MediaTimeline>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Vytvoření <xref:System.Windows.Media.MediaPlayer> a použít <xref:System.Windows.Media.MediaClock> nastavit jeho <xref:System.Windows.Media.MediaPlayer.Clock%2A> vlastnost.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Vytvořit <xref:System.Windows.Media.VideoDrawing> a přiřaďte <xref:System.Windows.Media.MediaPlayer> k <xref:System.Windows.Media.VideoDrawing.Player%2A> vlastnost <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Následující příklad používá <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> opakovaného přehrávání videa.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Všimněte si, že při použití <xref:System.Windows.Media.MediaTimeline>, je použít interaktivní <xref:System.Windows.Media.Animation.ClockController> vrácená z <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnost <xref:System.Windows.Media.MediaClock> ovládací prvek přehrávání médií místo metody interaktivní <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Vykreslení textu  
 Vykreslení textu, použijte <xref:System.Windows.Media.GlyphRunDrawing> a <xref:System.Windows.Media.GlyphRun>. Následující příklad používá <xref:System.Windows.Media.GlyphRunDrawing> vykreslování textu "Hello World".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A <xref:System.Windows.Media.GlyphRun> je objekt nízké úrovně, určené pro použití s pevným formátem dokumentu prezentace a tisku scénáře. Jednodušší způsob vykreslení textu na obrazovce, je použít <xref:System.Windows.Controls.Label> nebo <xref:System.Windows.Controls.TextBlock>. Další informace o <xref:System.Windows.Media.GlyphRun>, najdete v článku [Úvod do objektu GlyphRun a elementu Glyph](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) Přehled.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Kompozitní kresby  
 A <xref:System.Windows.Media.DrawingGroup> umožňují kombinovat více drawings do jednoho kompozitní kresby. Pomocí <xref:System.Windows.Media.DrawingGroup>, tvary, obrázky a text můžete zkombinovat do jediného <xref:System.Windows.Media.Drawing> objektu.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingGroup> kombinace obou <xref:System.Windows.Media.GeometryDrawing> objekty a <xref:System.Windows.Media.ImageDrawing> objektu. Tento příklad vytvoří následující výstup.  
  
 ![DrawingGroup – s použitím kreslení více](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Kompozitní kresby  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A <xref:System.Windows.Media.DrawingGroup> taky umožňuje použít masky krytí, transformace, bitmapových efektů a dalších operací k jejímu obsahu. <xref:System.Windows.Media.DrawingGroup> operace se použijí v uvedeném pořadí: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>a potom <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Následující obrázek znázorňuje pořadí, ve kterém <xref:System.Windows.Media.DrawingGroup> operace jsou použity.  
  
 ![DrawingGroup – pořadí operací](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Pořadí operací DrawingGroup –  
  
 Následující tabulka popisuje vlastnosti můžete použít k manipulaci <xref:System.Windows.Media.DrawingGroup> obsah objektu.  
  
|Vlastnost|Popis|Obrázek|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Mění neprůhlednost vybrané části <xref:System.Windows.Media.DrawingGroup> obsah. Příklad najdete v tématu [jak: Řízení průhlednosti kresby](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![DrawingGroup – s masky krytí](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Rovnoměrně mění neprůhlednost <xref:System.Windows.Media.DrawingGroup> obsah. Pomocí této vlastnosti můžete provést <xref:System.Windows.Media.Drawing> průhledného nebo částečně. Příklad najdete v tématu [jak: Použití masky krytí na kresbu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![Objekty DrawingGroup s různým nastavením neprůhlednosti](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Platí <xref:System.Windows.Media.Effects.BitmapEffect> k <xref:System.Windows.Media.DrawingGroup> obsah. Příklad najdete v tématu [jak: Použití efekty BitmapEffect na kresbu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![DrawingGroup – s BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Klipy <xref:System.Windows.Media.DrawingGroup> obsah do oblasti popíšete pomocí <xref:System.Windows.Media.Geometry>. Příklad najdete v tématu [jak: Oříznout kresby](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![DrawingGroup – s definovanou oblastí oříznutí](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Připnutí pixelech nezávislých na zařízení na zařízení pixelů podél zadaná pravidla. Tato vlastnost je užitečná pro zajištění prudce vykreslení jemně podrobné grafiky na displeji nízkým rozlišením DPI. Příklad najdete v tématu [použití GuidelineSet na kresbu](how-to-apply-a-guidelineset-to-a-drawing.md).|![DrawingGroup – a nemusíte GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transformuje <xref:System.Windows.Media.DrawingGroup> obsah. Příklad najdete v tématu [jak: Použití transformace na kresbu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![DrawingGroup – otočit A](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Zobrazit kresby jako obrázek  
 K zobrazení <xref:System.Windows.Media.Drawing> s <xref:System.Windows.Controls.Image> řídit, použijte <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> ovládacího prvku <xref:System.Windows.Controls.Image.Source%2A> a nastavit <xref:System.Windows.Media.DrawingImage> objektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> vlastnost výkresu, které chcete zobrazit.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingImage> a <xref:System.Windows.Controls.Image> ovládací prvek pro zobrazení <xref:System.Windows.Media.GeometryDrawing>. Tento příklad vytvoří následující výstup.  
  
 ![GeometryDrawing dvě symbol tří teček](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Vykreslení objektu kresbou  
 A <xref:System.Windows.Media.DrawingBrush> k typu štětec, který jsou vykreslovány v oblasti kreslení objektu. Slouží k vykreslení téměř k jakémukoli grafický objekt kresbou. <xref:System.Windows.Media.Drawing> Vlastnost <xref:System.Windows.Media.DrawingBrush> popisuje jeho <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. K vykreslení <xref:System.Windows.Media.Drawing> s <xref:System.Windows.Media.DrawingBrush>, přidejte na štětec pomocí stopy <xref:System.Windows.Media.Drawing> vlastnost a použití štětce k vyplnění grafické objektů, jako je například ovládací prvek nebo panelu.  
  
 V následujících příkladech se používá <xref:System.Windows.Media.DrawingBrush> k vykreslení <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> pomocí vzoru vytvořené z <xref:System.Windows.Media.GeometryDrawing>. Tento příklad vytvoří následující výstup.  
  
 ![A vedle sebe DrawingBrush](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing použít s DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush> Třída poskytuje širokou škálu možností pro roztažení a dělení na bloky jeho obsah. Další informace o <xref:System.Windows.Media.DrawingBrush>, najdete v článku [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md) Přehled.  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Vykreslení výkresu vizuálním objektem  
 A <xref:System.Windows.Media.DrawingVisual> k typu vizuální objekty, které jsou navržené tak, aby vykreslení kresby. Práce přímo ve vizuální vrstvě je možnost pro vývojáře, kteří mají být sestaveny vysoce přizpůsobené grafickém prostředí a není popsané v tomto přehledu. Další informace najdete v tématu [použití objektů DrawingVisual](using-drawingvisual-objects.md) Přehled.  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext objekty  
 <xref:System.Windows.Media.DrawingContext> Třída umožňuje naplnit <xref:System.Windows.Media.Visual> nebo <xref:System.Windows.Media.Drawing> s vizuální obsah. Mnoho takových objektů grafiky nižší úrovně použít <xref:System.Windows.Media.DrawingContext> protože velmi efektivně popisuje grafického obsahu.  
  
 I když <xref:System.Windows.Media.DrawingContext> metody draw vypadat podobně jako na metody vykreslení <xref:System.Drawing.Graphics?displayProperty=nameWithType> typu, jsou ve skutečnosti velmi odlišné. <xref:System.Windows.Media.DrawingContext> se používá systém grafiky uchovanou režimu, zatímco <xref:System.Drawing.Graphics?displayProperty=nameWithType> typ se používá systémem grafiky přímý režim. Při použití <xref:System.Windows.Media.DrawingContext> objektu vykreslení příkazů, jsou ve skutečnosti ukládání sadu vykreslování pokynů (ale mechanismus přesně úložiště závisí na typu objektu, který poskytuje <xref:System.Windows.Media.DrawingContext>), který budete používat později grafiky systému; nejsou kreslení na obrazovku v reálném čase. Další informace o tom, jak funguje grafika systému Windows Presentation Foundation (WPF), najdete v článku [přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).  
  
 Jste nikdy přímo vytvořit instanci <xref:System.Windows.Media.DrawingContext>; můžete však získat výkresu kontext z určitých metod, například <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Výčet obsahu vizuálního objektu  
 Kromě jejich použití <xref:System.Windows.Media.Drawing> objekty také neposkytuje objektový model pro vytvoření výčtu obsah <xref:System.Windows.Media.Visual>.  
  
 V následujícím příkladu <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodu pro načtení <xref:System.Windows.Media.DrawingGroup> hodnotu <xref:System.Windows.Media.Visual> a výčet ho.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Kreslení pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled geometrie](geometry-overview.md)
- [Tvary a základní kresby v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
- [– postupy](drawings-how-to-topics.md)
