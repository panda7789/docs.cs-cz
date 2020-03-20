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
ms.openlocfilehash: 7a5d00eb2fb7c66e5e42d40893806e13717e1d2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186542"
---
# <a name="drawing-objects-overview"></a>Přehled vykreslovaných objektů
Toto téma <xref:System.Windows.Media.Drawing> představuje objekty a popisuje, jak je používat k efektivnímu kreslení tvarů, bitmap, textu a médií. Objekty používejte <xref:System.Windows.Media.Drawing> při vytváření klipartu, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Visual> malování pomocí nebo použití objektů.  

<a name="whatisadrawingsection"></a>
## <a name="what-is-a-drawing-object"></a>Co je kreslicí objekt?  
 Objekt <xref:System.Windows.Media.Drawing> popisuje viditelný obsah, například tvar, bitmapu, video nebo řádek textu. Různé typy výkresů popisují různé typy obsahu. Následuje seznam různých typů nakreslených objektů.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Nakreslí tvar.  
  
- <xref:System.Windows.Media.ImageDrawing>– Nakreslí obrázek.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Nakreslí text.  
  
- <xref:System.Windows.Media.VideoDrawing>– Přehraje zvukový soubor nebo video soubor.  
  
- <xref:System.Windows.Media.DrawingGroup>– Kreslí jiné výkresy. Pomocí skupiny výkresů můžete kombinovat další výkresy do jednoho složeného výkresu.  
  
 <xref:System.Windows.Media.Drawing>objekty jsou univerzální; existuje mnoho způsobů, jak <xref:System.Windows.Media.Drawing> můžete použít objekt.  
  
- Můžete jej zobrazit jako obrázek <xref:System.Windows.Media.DrawingImage> pomocí <xref:System.Windows.Controls.Image> ovládacího prvku a.  
  
- Můžete použít s <xref:System.Windows.Media.DrawingBrush> a malovat objekt, jako <xref:System.Windows.Controls.Page.Background%2A> je <xref:System.Windows.Controls.Page>například .  
  
- Můžete ji použít k popisu <xref:System.Windows.Media.DrawingVisual>vzhledu .  
  
- Můžete jej použít k výčetu obsahu <xref:System.Windows.Media.Visual>.  
  
 WPF poskytuje další typy objektů, které jsou schopné kreslit tvary, rastrové obrázky, text a média. Můžete například také <xref:System.Windows.Shapes.Shape> použít objekty k <xref:System.Windows.Controls.MediaElement> kreslení obrazců a ovládací prvek poskytuje další způsob přidání videa do aplikace. Takže kdy byste <xref:System.Windows.Media.Drawing> měli používat objekty? Když můžete obětovat funkce na úrovni architektury <xref:System.Windows.Freezable> získat výhody výkonu, nebo když potřebujete funkce. Vzhledem k tomu, <xref:System.Windows.Media.Drawing> že objekty postrádají podporu pro [rozvržení](../advanced/layout.md), vstup a fokus, poskytují výhody <xref:System.Windows.Media.Visual> výkonu, které je činí ideálními pro popis pozadí, klipartů a pro kreslení objektů na nízké úrovni.  
  
 Vzhledem k <xref:System.Windows.Freezable> tomu, <xref:System.Windows.Media.Drawing> že se jedná o objekt typu, objekty získají několik speciálních funkcí, které zahrnují následující: mohou být deklarovány jako [prostředky](../../../desktop-wpf/fundamentals/xaml-resources-define.md), sdíleny mezi více objekty, jen pro čtení za účelem zlepšení výkonu, klonovány a bezpečné pro přístup z více vláken. Další informace o různých funkcích <xref:System.Windows.Freezable> poskytovaných objekty naleznete v tématu [Přehled mrazivých objektů](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>
## <a name="draw-a-shape"></a>Kreslení tvaru  
 Chcete-li nakreslit tvar, použijte <xref:System.Windows.Media.GeometryDrawing>. <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Vlastnost výkresu geometrie popisuje tvar kreslení, <xref:System.Windows.Media.GeometryDrawing.Brush%2A> jeho vlastnost popisuje, jak by měl být <xref:System.Windows.Media.GeometryDrawing.Pen%2A> obrazec malován, a jeho vlastnost popisuje, jak by měl být nakreslen jeho obrys.  
  
 Následující příklad používá <xref:System.Windows.Media.GeometryDrawing> k nakreslení tvaru. Obrazec je popsán <xref:System.Windows.Media.GeometryGroup> a <xref:System.Windows.Media.EllipseGeometry> a a dva objekty. Interiér tvaru je natřen <xref:System.Windows.Media.LinearGradientBrush> a jeho obrys <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>je kreslen .  
  
 Tento příklad vytvoří <xref:System.Windows.Media.GeometryDrawing>následující .  
  
 ![GeometryKreslení dvou elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
A GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Úplný příklad naleznete v [tématu Vytvoření geometrieKreslení](how-to-create-a-geometrydrawing.md).  
  
 Jiné <xref:System.Windows.Media.Geometry> třídy, <xref:System.Windows.Media.PathGeometry> například umožňují vytvářet složitější tvary vytvářením křivek a oblouků. Další informace <xref:System.Windows.Media.Geometry> o objektech naleznete v přehledu [geometrie](geometry-overview.md).  
  
 Další informace o dalších způsobech kreslení <xref:System.Windows.Media.Drawing> obrazců, které nepoužívají objekty, naleznete [v tématu Obrazce a Základní výkres v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>
## <a name="draw-an-image"></a>Kreslení obrázku  
 Chcete-li nakreslit obrázek, použijte . <xref:System.Windows.Media.ImageDrawing> Vlastnost objektu popisuje obrázek kreslení a <xref:System.Windows.Media.ImageDrawing.Rect%2A> jeho vlastnost definuje oblast, kde je obrázek nakreslen. <xref:System.Windows.Media.ImageDrawing> <xref:System.Windows.Media.ImageDrawing.ImageSource%2A>  
  
 Následující příklad nakreslí obrázek do obdélníku umístěného na (75,75), který je 100 x 100 pixelů. Následující obrázek <xref:System.Windows.Media.ImageDrawing> znázorňuje vytvořený v příkladu. Bylo přidáno šedé ohraničení, které <xref:System.Windows.Media.ImageDrawing>zobrazuje hranice .  
  
 ![A 100 100 ImageDrawing nakreslené na &#40;75,75&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
A 100 na 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Další informace o obrázcích naleznete v tématu [Přehled snímků](imaging-overview.md).  
  
<a name="playmedia"></a>
## <a name="play-media-code-only"></a>Přehrát média (pouze kód)  
  
> [!NOTE]
> I když můžete <xref:System.Windows.Media.VideoDrawing> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]deklarovat in , můžete načíst a přehrávat pouze jeho média pomocí kódu. Chcete-li [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]přehrát <xref:System.Windows.Controls.MediaElement> video v , použijte místo toho.  
  
 Chcete-li přehrát zvukový soubor <xref:System.Windows.Media.VideoDrawing> nebo <xref:System.Windows.Media.MediaPlayer>videosoubor, použijte a a . Existují dva způsoby, jak načíst a přehrát média. První je použít <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> a a sami, a druhý způsob, jak je vytvořit svůj vlastní <xref:System.Windows.Media.MediaTimeline> pro použití s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
> Při distribuci médií s aplikací nelze použít mediální soubor jako zdroj projektu, stejně jako obrázek. V souboru projektu je nutné místo `Content` toho `CopyToOutputDirectory` nastavit `PreserveNewest` `Always`typ média a nastavit na nebo .  
  
 Chcete-li přehrávat <xref:System.Windows.Media.MediaTimeline>média bez vytvoření vlastního , proveďte následující kroky.  
  
1. Vytvořte <xref:System.Windows.Media.MediaPlayer> objekt.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Pomocí <xref:System.Windows.Media.MediaPlayer.Open%2A> této metody načtěte mediální soubor.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Vytvořte <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Určete velikost a umístění pro kreslení <xref:System.Windows.Media.VideoDrawing.Rect%2A> média <xref:System.Windows.Media.VideoDrawing>nastavením vlastnosti .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Nastavte <xref:System.Windows.Media.VideoDrawing.Player%2A> vlastnost <xref:System.Windows.Media.VideoDrawing> s vytvořeným. <xref:System.Windows.Media.MediaPlayer>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Použijte <xref:System.Windows.Media.MediaPlayer.Play%2A> metodu <xref:System.Windows.Media.MediaPlayer> a začněte přehrávat médium.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Následující příklad používá <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer> a přehrát video soubor jednou.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Chcete-li získat další časování <xref:System.Windows.Media.MediaTimeline> kontrolu <xref:System.Windows.Media.MediaPlayer> nad <xref:System.Windows.Media.VideoDrawing> médiem, použijte s a objekty. Umožňuje <xref:System.Windows.Media.MediaTimeline> určit, zda se má video opakovat. Chcete-li <xref:System.Windows.Media.MediaTimeline> použít <xref:System.Windows.Media.VideoDrawing>s , proveďte následující kroky:  
  
1. Deklarovat <xref:System.Windows.Media.MediaTimeline> a nastavit jeho načasování chování.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Vytvořte <xref:System.Windows.Media.MediaClock> a <xref:System.Windows.Media.MediaTimeline>z .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Vytvořte <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.MediaClock> použijte k <xref:System.Windows.Media.MediaPlayer.Clock%2A> nastavení jeho vlastnosti.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Vytvořte <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer> přiřaďte <xref:System.Windows.Media.VideoDrawing.Player%2A> <xref:System.Windows.Media.VideoDrawing>vlastnost .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 The following example uses a <xref:System.Windows.Media.MediaTimeline> with a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> to play a video repeatedly.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Všimněte si, že <xref:System.Windows.Media.MediaTimeline>při použití <xref:System.Windows.Media.Animation.ClockController> , použijete interaktivní vrácené z <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnosti <xref:System.Windows.Media.MediaClock> řídit <xref:System.Windows.Media.MediaPlayer>přehrávání médií namísto interaktivní metody .  
  
<a name="drawtext"></a>
## <a name="draw-text"></a>Kreslení textu  
 Chcete-li nakreslit <xref:System.Windows.Media.GlyphRunDrawing> text, <xref:System.Windows.Media.GlyphRun>použijte a a . Následující příklad používá <xref:System.Windows.Media.GlyphRunDrawing> k nakreslení textu "Hello World".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A <xref:System.Windows.Media.GlyphRun> je objekt nižší úrovně určený pro použití se scénáři prezentace a tisku dokumentu v pevném formátu. Jednodušší způsob kreslení textu na obrazovku je <xref:System.Windows.Controls.Label> použít <xref:System.Windows.Controls.TextBlock>nebo . Další informace <xref:System.Windows.Media.GlyphRun>o tématu naleznete v [přehledu Úvod k objektu Glyfů a elementu glyfů.](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md)  
  
<a name="compositedrawingssection"></a>
## <a name="composite-drawings"></a>Složené výkresy  
 A <xref:System.Windows.Media.DrawingGroup> umožňuje kombinovat více výkresů do jednoho složeného výkresu. Pomocí aplikace <xref:System.Windows.Media.DrawingGroup>můžete kombinovat tvary, obrázky a <xref:System.Windows.Media.Drawing> text do jednoho objektu.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingGroup> kombinovat <xref:System.Windows.Media.GeometryDrawing> dva objekty a objekt. <xref:System.Windows.Media.ImageDrawing> Tento příklad vytváří následující výstup.  
  
 ![Skupina výkresů s více výkresy](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Složený výkres  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A <xref:System.Windows.Media.DrawingGroup> také umožňuje použít masky krytí, transformace, bitmapové efekty a další operace na jeho obsah. <xref:System.Windows.Media.DrawingGroup>operace jsou použity v <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A> <xref:System.Windows.Media.DrawingGroup.Opacity%2A>následujícím <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>pořadí: , , , <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, a potom <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Následující obrázek znázorňuje <xref:System.Windows.Media.DrawingGroup> pořadí, ve kterém jsou operace použity.  
  
 ![Pořadí operací skupiny drawinggroup](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Pořadí operací DrawingGroup  
  
 Následující tabulka popisuje vlastnosti, které můžete <xref:System.Windows.Media.DrawingGroup> použít k manipulaci s obsahem objektu.  
  
|Vlastnost|Popis|Obrázek|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Změní krytí vybraných částí <xref:System.Windows.Media.DrawingGroup> obsahu. Příklad najdete v [tématu Jak: Řízení krytí výkresu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Skupina výkresů s maskou krytí](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Jednotně změní krytí <xref:System.Windows.Media.DrawingGroup> obsahu. Pomocí této vlastnosti <xref:System.Windows.Media.Drawing> můžete vytvořit průhlednou nebo částečně průhlednou vlastnost. Příklad najdete v [tématu Jak: Aplikování masky krytí na výkres](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![Skupiny výkresů s různými nastaveními krytí](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Aplikuje <xref:System.Windows.Media.Effects.BitmapEffect> a <xref:System.Windows.Media.DrawingGroup> na obsah. Příklad najdete v [tématu Jak: Aplikování bitmapového efektu na kresbu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![Skupina výkresů s efektem BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Klipy <xref:System.Windows.Media.DrawingGroup> obsah do oblasti, <xref:System.Windows.Media.Geometry>kterou popisujete pomocí . Příklad najdete v [tématu Jak: Oříznutí výkresu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![Skupina kreslení s definovanou oblastí klipu](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Přichytí pixely nezávislé na zařízení k pixelům zařízení podle zadaných pokynů. Tato vlastnost je užitečná pro zajištění, že jemně detailní grafiky vykreslují ostře na displejích s nízkým rozlišením DPI. Příklad najdete v [tématu Použití sady pokynů pro výkres](how-to-apply-a-guidelineset-to-a-drawing.md).|![Skupina výkresů se sadou guidelineSet a bez něj](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transformuje <xref:System.Windows.Media.DrawingGroup> obsah. Příklad najdete v [tématu Jak: Aplikování transformace na výkres](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![Otočená skupina výkresů](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>
## <a name="display-a-drawing-as-an-image"></a>Zobrazení výkresu jako obrázku  
 Chcete-li <xref:System.Windows.Media.Drawing> zobrazit <xref:System.Windows.Controls.Image> <xref:System.Windows.Media.DrawingImage> ovládací prvek, <xref:System.Windows.Controls.Image> použijte a <xref:System.Windows.Controls.Image.Source%2A> jako <xref:System.Windows.Media.DrawingImage> ovládací prvek <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> a nastavte vlastnost objektu na výkres, který chcete zobrazit.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingImage> a <xref:System.Windows.Controls.Image> ovládací prvek <xref:System.Windows.Media.GeometryDrawing>k zobrazení . Tento příklad vytváří následující výstup.  
  
 ![GeometryKreslení dvou elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Obrázek výkresu  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>
## <a name="paint-an-object-with-a-drawing"></a>Malování objektu výkresem  
 A <xref:System.Windows.Media.DrawingBrush> je typ stopy, která maluje oblast nakresleným objektem. Můžete ji použít k malování téměř libovolného grafického objektu s výkresem. Vlastnost <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingBrush> popisuje jeho <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. Chcete-li <xref:System.Windows.Media.Drawing> vykreslit a <xref:System.Windows.Media.DrawingBrush>, přidejte jej <xref:System.Windows.Media.Drawing> do stopy pomocí vlastnosti stopy a pomocí stopy namalujte grafický objekt, například ovládací prvek nebo panel.  
  
 Následující příklady používají <xref:System.Windows.Media.DrawingBrush> k <xref:System.Windows.Shapes.Shape.Fill%2A> malování <xref:System.Windows.Shapes.Rectangle> a se vzorkem <xref:System.Windows.Media.GeometryDrawing>vytvořeným z . Tento příklad vytváří následující výstup.  
  
 ![Kachlová kresbaBrush](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing používá s DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 Třída <xref:System.Windows.Media.DrawingBrush> poskytuje celou řadu možností pro roztažení a obklady jeho obsah. Další informace <xref:System.Windows.Media.DrawingBrush>o aplikaci naleznete v přehledu [Malování s obrázky, kresbami a vizuály.](painting-with-images-drawings-and-visuals.md)  
  
<a name="renderingwithvisualsection"></a>
## <a name="render-a-drawing-with-a-visual"></a>Vykreslení výkresu pomocí vizuálního  
 A <xref:System.Windows.Media.DrawingVisual> je typ vizuálního objektu určený k vykreslení výkresu. Práce přímo ve vizuální vrstvě je možnost pro vývojáře, kteří chtějí vytvořit vysoce přizpůsobené grafické prostředí a není popsánv tomto přehledu. Další informace naleznete [v tématu Using DrawingVisual Objects](using-drawingvisual-objects.md) overview.  
  
<a name="drawingcontextobjects"></a>
## <a name="drawingcontext-objects"></a>Objekty Kontextu kreslení  
 Třída <xref:System.Windows.Media.DrawingContext> umožňuje naplnit <xref:System.Windows.Media.Visual> vizuální <xref:System.Windows.Media.Drawing> obsah nebo s. Mnoho takových grafických objektů <xref:System.Windows.Media.DrawingContext> nižší úrovně používá, protože velmi efektivně popisuje grafický obsah.  
  
 Ačkoli <xref:System.Windows.Media.DrawingContext> metody kreslení se zdají být <xref:System.Drawing.Graphics?displayProperty=nameWithType> podobné metodám kreslení typu, jsou ve skutečnosti velmi odlišné. <xref:System.Windows.Media.DrawingContext>se používá s grafickým systémem se <xref:System.Drawing.Graphics?displayProperty=nameWithType> zachovaným režimem, zatímco typ se používá s grafickým systémem v okamžitém režimu. Při použití <xref:System.Windows.Media.DrawingContext> příkazy kreslení objektu, jsou ve skutečnosti ukládání sadu vykreslování pokyny (i když <xref:System.Windows.Media.DrawingContext>přesný mechanismus úložiště závisí na typu objektu, který poskytuje ), který bude později použit grafický systém; nekreslíte na obrazovku v reálném čase. Další informace o fungování grafického systému WPF (Windows Presentation Foundation) naleznete v přehledu [vykreslení grafiky WPF](wpf-graphics-rendering-overview.md).  
  
 Nikdy přímo konkretizovat <xref:System.Windows.Media.DrawingContext>; Kontext výkresu však můžete získat z určitých metod, například <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>
## <a name="enumerate-the-contents-of-a-visual"></a>Výčet obsahu vizuálního  
 Kromě jejich další použití, <xref:System.Windows.Media.Drawing> objekty také poskytují objektový model pro <xref:System.Windows.Media.Visual>výčet obsahu .  
  
 Následující příklad používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodu <xref:System.Windows.Media.DrawingGroup> k načtení hodnoty <xref:System.Windows.Media.Visual> a výčet.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled geometrie](geometry-overview.md)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
- [Témata s postupy](drawings-how-to-topics.md)
