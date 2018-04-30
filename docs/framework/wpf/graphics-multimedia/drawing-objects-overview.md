---
title: Přehled vykreslovaných objektů
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3672e4b1deacd8fb50a5318270854daae9c74761
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="drawing-objects-overview"></a>Přehled vykreslovaných objektů
Toto téma představuje <xref:System.Windows.Media.Drawing> objekty a popisuje, jak je použít k efektivní kreslení tvarů, rastrové obrázky, text a média. Použít <xref:System.Windows.Media.Drawing> objekty, když vytvoříte klip obrázky, Malování <xref:System.Windows.Media.DrawingBrush>, nebo použijte <xref:System.Windows.Media.Visual> objekty.  
  
 
  
<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Co je objekt kreslení?  
 A <xref:System.Windows.Media.Drawing> objekt popisuje viditelný obsah, například obrazce, rastrového obrázku, videa nebo na řádku textu. Různé typy výkresů popisují různé typy obsahu. Následuje seznam s různými typy kreslení objektů.  
  
-   <xref:System.Windows.Media.GeometryDrawing> – Kreslení obrazce.  
  
-   <xref:System.Windows.Media.ImageDrawing> – Nakreslí obrázek.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> – Nevykresluje text.  
  
-   <xref:System.Windows.Media.VideoDrawing> – Hraje soubor zvuku a videa.  
  
-   <xref:System.Windows.Media.DrawingGroup> – Nevykresluje kresby na další. Použijte skupinu kreslení kombinovat jiné kresby do jedné složené kreslení.  
  
 <xref:System.Windows.Media.Drawing> objekty jsou univerzální; Existuje mnoho způsobů, které můžete použít <xref:System.Windows.Media.Drawing> objektu.  
  
-   Můžete ji zobrazit jako bitovou kopii pomocí <xref:System.Windows.Media.DrawingImage> a <xref:System.Windows.Controls.Image> ovládacího prvku.  
  
-   Můžete použít se službou <xref:System.Windows.Media.DrawingBrush> k vyplnění objektu, například <xref:System.Windows.Controls.Page.Background%2A> z <xref:System.Windows.Controls.Page>.  
  
-   Můžete ji použít k popisu vzhled <xref:System.Windows.Media.DrawingVisual>.  
  
-   Můžete ji provést výčet obsahu <xref:System.Windows.Media.Visual>.  
  
 WPF obsahuje jiné typy objektů, které podporují kreslení tvarů, rastrové obrázky, text a média. Například můžete také použít <xref:System.Windows.Shapes.Shape> objektů pro kreslení tvarů a <xref:System.Windows.Controls.MediaElement> řízení poskytuje jiný způsob, jak přidat video do vaší aplikace. Proto když mám použít <xref:System.Windows.Media.Drawing> objekty? Pokud můžete vzdát úrovně funkce framework získat výhody výkonu nebo pokud potřebujete <xref:System.Windows.Freezable> funkce. Protože <xref:System.Windows.Media.Drawing> objekty neobsahují podporu pro [rozložení](../../../../docs/framework/wpf/advanced/layout.md), zadejte a zaměřit, poskytují výkon výhody, díky kterým ideální pro popisující pozadí, klip obrázky a nízké úrovně kreslení s <xref:System.Windows.Media.Visual> objekty.  
  
 Protože jsou typu <xref:System.Windows.Freezable> objekt, <xref:System.Windows.Media.Drawing> objekty získat několik speciální funkce, které zahrnují následující: můžete být deklarována jako [prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md), sdílené mezi více objektů, jen pro čtení ke zlepšení výkon, klonovat a provedené bezpečné pro přístup z více vláken. Další informace o různých funkcí poskytovaných <xref:System.Windows.Freezable> objekty, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Kreslení obrazce  
 Kreslení obrazce, můžete použít <xref:System.Windows.Media.GeometryDrawing>. Geometrie výkresu <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> vlastnost popisuje tvar, který má nakreslit, jeho <xref:System.Windows.Media.GeometryDrawing.Brush%2A> vlastnost popisuje, jak by měla být vykresluje vnitřního tvaru a jeho <xref:System.Windows.Media.GeometryDrawing.Pen%2A> vlastnost popisuje, jak mají být vykresleny jeho outline.  
  
 Následující příklad používá <xref:System.Windows.Media.GeometryDrawing> kreslení obrazce. Tvar, který je popsán <xref:System.Windows.Media.GeometryGroup> a dvě <xref:System.Windows.Media.EllipseGeometry> objekty. Vykreslení vnitřního tvaru s <xref:System.Windows.Media.LinearGradientBrush> a jeho obrys vykreslením s <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.  
  
 Tento příklad vytvoří následující <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![Objekt GeometryDrawing sestávající ze dvou výpustky](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Objekt GeometryDrawing sestávající  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Úplný příklad najdete v tématu [vytvořit objekt GeometryDrawing sestávající](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-geometrydrawing.md).  
  
 Další <xref:System.Windows.Media.Geometry> třídy, jako například <xref:System.Windows.Media.PathGeometry> vám umožní vytvořit složitější tvary vytvořením křivek a oblouky. Další informace o <xref:System.Windows.Media.Geometry> objekty, najdete [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 Další informace o jiných způsobech kreslení obrazců, které nepoužívají <xref:System.Windows.Media.Drawing> objekty, najdete v části [tvarů a základní kreslení v přehledu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Kreslení obrázku  
 Kreslení obrázku, můžete použít <xref:System.Windows.Media.ImageDrawing>. <xref:System.Windows.Media.ImageDrawing> Objektu <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> vlastnost popisuje bitovou kopii k vykreslení a jeho <xref:System.Windows.Media.ImageDrawing.Rect%2A> vlastnost definuje oblasti, kde se vykreslují bitovou kopii.  
  
 Následující příklad nevykresluje bitovou kopii do obdélníku umístěný v bodu (75,75) tedy 100 x 100 pixelů. Následující obrázek ukazuje <xref:System.Windows.Media.ImageDrawing> vytvořené v příkladu. Šedé ohraničení byla přidána do zobrazit hranice <xref:System.Windows.Media.ImageDrawing>.  
  
 ![100 × 100 ImageDrawing vykreslovat &#40;75,75&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
ImageDrawing 100 x 100  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Další informace o bitových kopiích naleznete v tématu [Imaging přehled](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Přehrání média (pouze kód)  
  
> [!NOTE]
>  I když můžou deklarovat <xref:System.Windows.Media.VideoDrawing> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], je možné provádět pouze načíst- and -play jeho médium pomocí kódu. Přehrávání videa v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], používat <xref:System.Windows.Controls.MediaElement> místo.  
  
 Pro přehrání souboru zvuku a videa, můžete použít <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer>. Existují dva způsoby, jak načíst- and -play média. První je použití <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> sami a druhý je způsob, jak vytvořit vlastní <xref:System.Windows.Media.MediaTimeline> pro použití s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Při distribuci média s vaší aplikací, nelze použít soubor média jako prostředek projektu jako obrázek. V souboru projektu, musíte místo toho nastavit typ média na `Content` a nastavte `CopyToOutputDirectory` k `PreserveNewest` nebo `Always`.  
  
 Přehrávání média bez vytvoření vlastní <xref:System.Windows.Media.MediaTimeline>, proveďte následující kroky.  
  
1.  Vytvoření <xref:System.Windows.Media.MediaPlayer> objektu.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2.  Použití <xref:System.Windows.Media.MediaPlayer.Open%2A> metoda načíst soubor média.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3.  Vytvoření <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4.  Zadejte velikost a umístění k vykreslení média nastavením <xref:System.Windows.Media.VideoDrawing.Rect%2A> vlastnost <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5.  Nastavte <xref:System.Windows.Media.VideoDrawing.Player%2A> vlastnost <xref:System.Windows.Media.VideoDrawing> s <xref:System.Windows.Media.MediaPlayer> jste vytvořili.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6.  Použití <xref:System.Windows.Media.MediaPlayer.Play%2A> metodu <xref:System.Windows.Media.MediaPlayer> a spustit přehrávání média.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Následující příklad používá <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer> pro přehrání souboru videa jednou.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Chcete-li získat další časování kontrolu nad média, použijte <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> objekty. <xref:System.Windows.Media.MediaTimeline> Umožňuje určit, zda by měl opakovat videa. Použít <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.VideoDrawing>, proveďte následující kroky:  
  
1.  Deklarovat <xref:System.Windows.Media.MediaTimeline> a nastavte své chování časování.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2.  Vytvoření <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.MediaTimeline>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3.  Vytvoření <xref:System.Windows.Media.MediaPlayer> a použít <xref:System.Windows.Media.MediaClock> k nastavení jeho <xref:System.Windows.Media.MediaPlayer.Clock%2A> vlastnost.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4.  Vytvoření <xref:System.Windows.Media.VideoDrawing> a přiřaďte <xref:System.Windows.Media.MediaPlayer> k <xref:System.Windows.Media.VideoDrawing.Player%2A> vlastnost <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Následující příklad používá <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> opakovaného přehrávání videa.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Všimněte si, že při použití <xref:System.Windows.Media.MediaTimeline>, je použít interaktivní <xref:System.Windows.Media.Animation.ClockController> vrácená z <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnost <xref:System.Windows.Media.MediaClock> řízení přehrávání médií místo interaktivní metody <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Kreslení textu  
 Chcete-li kreslení textu, použijte <xref:System.Windows.Media.GlyphRunDrawing> a <xref:System.Windows.Media.GlyphRun>. Následující příklad používá <xref:System.Windows.Media.GlyphRunDrawing> vykreslování textu "Hello World".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A <xref:System.Windows.Media.GlyphRun> je objekt nízké úrovně určený k použití s prezentace-formátovat dokument a tisku scénáře. Kreslení textu na obrazovce jednodušší způsob je použít <xref:System.Windows.Controls.Label> nebo <xref:System.Windows.Controls.TextBlock>. Další informace o <xref:System.Windows.Media.GlyphRun>, najdete v článku [Úvod do objektu GlyphRun a glyfů Element](../../../../docs/framework/wpf/advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) Přehled.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Složené kresby  
 A <xref:System.Windows.Media.DrawingGroup> umožňuje kombinovat více výkresů do jedné složené kreslení. Pomocí <xref:System.Windows.Media.DrawingGroup>, můžete kombinovat tvary, obrázky a text do jednoho <xref:System.Windows.Media.Drawing> objektu.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingGroup> kombinace obou <xref:System.Windows.Media.GeometryDrawing> objekty a <xref:System.Windows.Media.ImageDrawing> objektu. Tento příklad vytvoří následující výstup.  
  
 ![Objekt DrawingGroup s více výkresů](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
Složené kreslení  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A <xref:System.Windows.Media.DrawingGroup> taky umožňuje použít masky krytí, transformací, důsledky rastrového obrázku a dalších operací k jejímu obsahu. <xref:System.Windows.Media.DrawingGroup> operace se použijí v uvedeném pořadí: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>a potom <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Následující příklad uvádí pořadí, ve kterém <xref:System.Windows.Media.DrawingGroup> operace se použijí.  
  
 ![Pořadí operací objektu DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Pořadí operací DrawingGroup  
  
 Následující tabulka popisuje vlastnosti, které můžete použít k manipulaci <xref:System.Windows.Media.DrawingGroup> obsah objektu.  
  
|Vlastnost|Popis|Obrázek|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Mění krytí vybraných částí <xref:System.Windows.Media.DrawingGroup> obsah. Příklad, naleznete v části [postupy: řízení krytí výkresu](http://msdn.microsoft.com/library/68580652-7d32-4d27-93cc-a5148cf4d5ee).|![Objekt DrawingGroup s masky krytí](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Jednotná změní krytí <xref:System.Windows.Media.DrawingGroup> obsah. Chcete-li tuto vlastnost používat <xref:System.Windows.Media.Drawing> průhledných nebo částečně transparentní. Příklad, naleznete v části [postupy: použití masky krytí do výkresu](http://msdn.microsoft.com/library/d77b420b-9be2-479c-a45e-82f4da30eb9f).|![Objekty DrawingGroup s různým nastavením neprůhlednosti](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Se vztahuje <xref:System.Windows.Media.Effects.BitmapEffect> k <xref:System.Windows.Media.DrawingGroup> obsah. Příklad, naleznete v části [postupy: použití BitmapEffect do výkresu](http://msdn.microsoft.com/library/c5b1de83-8d09-47fb-96db-5f174471f4b5).|![DrawingGroup s BlurBitmapEffect](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Klipů <xref:System.Windows.Media.DrawingGroup> obsah do oblasti můžete popsat pomocí <xref:System.Windows.Media.Geometry>. Příklad, naleznete v části [postupy: oříznutí kreslení](http://msdn.microsoft.com/library/1f7d8a2c-c3c2-42cb-a542-e6796f9fb058) .|![DrawingGroup s definovanou oblastí oříznutí](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Připnutí pixelů zařízení nezávislé na zařízení pixelů podél zadaná pravidla. Tato vlastnost je užitečná pro zajištění prudce vykreslení jemně podrobné grafiky na nízkou hodnotou DPI zobrazí. Příklad, naleznete v části [použít vlastností GuidelineSet do výkresu](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-a-guidelineset-to-a-drawing.md).|![Objekt DrawingGroup s i bez vlastností GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transformuje <xref:System.Windows.Media.DrawingGroup> obsah. Příklad, naleznete v části [postupy: použití transformace na výkres](http://msdn.microsoft.com/library/0d525f2b-682d-4d67-9660-cf46929fbabd).|![A otáčet DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Zobrazení kreslení jako obrázek  
 K zobrazení <xref:System.Windows.Media.Drawing> s <xref:System.Windows.Controls.Image> řídit, použijte <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> ovládacího prvku <xref:System.Windows.Controls.Image.Source%2A> a nastavte <xref:System.Windows.Media.DrawingImage> objektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> vlastnost kreslení chcete zobrazit.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingImage> a <xref:System.Windows.Controls.Image> ovládacího prvku pro zobrazení <xref:System.Windows.Media.GeometryDrawing>. Tento příklad vytvoří následující výstup.  
  
 ![Objekt GeometryDrawing sestávající ze dvou výpustky](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Malování objektů s výkresu  
 A <xref:System.Windows.Media.DrawingBrush> je typ štětce, který vybarví oblast s objektu. Můžete ji použít k vyplnění téměř jakýmkoli grafického objektu s výkresu. <xref:System.Windows.Media.Drawing> Vlastnost <xref:System.Windows.Media.DrawingBrush> popisuje jeho <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. K vykreslení <xref:System.Windows.Media.Drawing> s <xref:System.Windows.Media.DrawingBrush>, přidejte ji do štětce pomocí štětce <xref:System.Windows.Media.Drawing> vlastnost a použití štětce k vyplnění grafického objektu, například ovládacího prvku nebo panelu.  
  
 Následující příklady používá <xref:System.Windows.Media.DrawingBrush> k vyplnění <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> pomocí vzoru vytvořené z <xref:System.Windows.Media.GeometryDrawing>. Tento příklad vytvoří následující výstup.  
  
 ![A na dlaždicích DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
Objekt GeometryDrawing sestávající použít s DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush> Třída poskytuje celou řadu možností pro roztažení a dlaždice jeho obsah. Další informace o <xref:System.Windows.Media.DrawingBrush>, najdete v článku [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md) Přehled.  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Vykreslení výkresu s vizuál  
 A <xref:System.Windows.Media.DrawingVisual> je typ určený k vykreslení výkresu vizuální objekt. Práce přímo ve vrstvě visual je možnost pro vývojáře, kteří chtějí vytvořit vysoce přizpůsobenou grafickém prostředí a není popsané v tomto přehledu. Další informace najdete v tématu [pomocí objekty DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md) Přehled.  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext objekty  
 <xref:System.Windows.Media.DrawingContext> Třída umožňuje naplnit <xref:System.Windows.Media.Visual> nebo <xref:System.Windows.Media.Drawing> s visual obsahem. Mnoho tyto objekty grafiky nižší úrovně použít <xref:System.Windows.Media.DrawingContext> protože velmi efektivně popisuje grafického obsahu.  
  
 I když <xref:System.Windows.Media.DrawingContext> metody kreslení zobrazí podobná metody kreslení <xref:System.Drawing.Graphics?displayProperty=nameWithType> typu, jsou ve skutečnosti odlišné. <xref:System.Windows.Media.DrawingContext> se používá systém grafiky udržených režimu, při <xref:System.Drawing.Graphics?displayProperty=nameWithType> typ se používá systém grafiky přímý režim. Při použití <xref:System.Windows.Media.DrawingContext> objektu kreslení příkazy, jsou ve skutečnosti ukládání sada pokynů vykreslování (i když tento mechanismus přesný úložiště závisí na typu objektu, který poskytuje <xref:System.Windows.Media.DrawingContext>), budou používat později grafiky systému; nejsou kreslení na obrazovku v reálném čase. Další informace o tom, jak funguje v systému Windows Presentation Foundation (WPF) grafiky, najdete v článku [vykreslování přehled grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 Nikdy přímo instance <xref:System.Windows.Media.DrawingContext>; můžete, ale získat kreslení kontext z některé metody, jako <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Výčet obsahu vizuálu  
 Kromě jejich použití <xref:System.Windows.Media.Drawing> objekty také poskytují objektový model pro vytvoření výčtu obsah <xref:System.Windows.Media.Visual>.  
  
 Následující příklad používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metoda pro načtení <xref:System.Windows.Media.DrawingGroup> hodnotu <xref:System.Windows.Media.Visual> a výčet ho.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Přehled objektů Shape a základního kreslení ve WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/drawings-how-to-topics.md)
