---
title: Přehled vykreslovaných objektů
description: Seznamte se s objekty a Naučte se je používat k efektivnímu kreslení tvarů, rastrových obrázků, textu a multimédií v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
ms.openlocfilehash: f00a59cd6e799e57f238c5f9b72ecc48e8445475
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853834"
---
# <a name="drawing-objects-overview"></a>Přehled vykreslovaných objektů
Toto téma představuje <xref:System.Windows.Media.Drawing> objekty a popisuje, jak je použít k efektivnímu kreslení tvarů, rastrových obrázků, textu a multimédií. Objekty můžete použít <xref:System.Windows.Media.Drawing> při vytváření klipartů, Malování s <xref:System.Windows.Media.DrawingBrush> nebo k používání <xref:System.Windows.Media.Visual> objektů.  

<a name="whatisadrawingsection"></a>
## <a name="what-is-a-drawing-object"></a>Co je nakreslený objekt?  
 <xref:System.Windows.Media.Drawing>Objekt popisuje viditelný obsah, jako je například tvar, rastrový obrázek, video nebo řádek textu. Různé typy kreseb popisují různé typy obsahu. Následuje seznam různých typů nakreslených objektů.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Nakreslí obrazec.  
  
- <xref:System.Windows.Media.ImageDrawing>– Nakreslí obrázek.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Kreslí text.  
  
- <xref:System.Windows.Media.VideoDrawing>– Přehraje zvukový soubor nebo videosoubor.  
  
- <xref:System.Windows.Media.DrawingGroup>– Kreslí další výkresy. K kombinování dalších kreseb do jednoho složené kresby použijte skupinu pro kreslení.  
  
 <xref:System.Windows.Media.Drawing>objekty jsou univerzální; Existuje mnoho způsobů, jak můžete objekt použít <xref:System.Windows.Media.Drawing> .  
  
- Můžete ji zobrazit jako obrázek pomocí <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> ovládacího prvku a.  
  
- Můžete ji použít s objektem <xref:System.Windows.Media.DrawingBrush> k vykreslení objektu, jako je například <xref:System.Windows.Controls.Page.Background%2A> z <xref:System.Windows.Controls.Page> .  
  
- Můžete ji použít k popisu vzhledu <xref:System.Windows.Media.DrawingVisual> .  
  
- Můžete ji použít k zobrazení výčtu obsahu <xref:System.Windows.Media.Visual> .  
  
 WPF poskytuje další typy objektů, které jsou schopné kreslit tvary, rastry, text a multimédia. Můžete například použít <xref:System.Windows.Shapes.Shape> objekty k vykreslování tvarů a <xref:System.Windows.Controls.MediaElement> ovládací prvek poskytuje další způsob, jak přidat video do aplikace. Takže když byste měli použít <xref:System.Windows.Media.Drawing> objekty? Když můžete využít funkce na úrovni rozhraní, abyste získali výhody výkonu nebo potřebujete <xref:System.Windows.Freezable> funkce. Vzhledem k tomu, že objekty neobsahují <xref:System.Windows.Media.Drawing> podporu pro [rozložení](../advanced/layout.md), vstup a zaměření, poskytují výkonnostní výhody, které jsou ideální pro popis pozadí, klipartu a pro vykreslování na nižší úrovni s <xref:System.Windows.Media.Visual> objekty.  
  
 Vzhledem k tomu, že se jedná o <xref:System.Windows.Freezable> objekt typu, <xref:System.Windows.Media.Drawing> objekty získají několik speciálních funkcí, které zahrnují následující: mohou být deklarovány jako [prostředky](../../../desktop-wpf/fundamentals/xaml-resources-define.md), sdílené mezi více objekty, pro zlepšení výkonu, klonování a provádění bezpečnosti vláken. Další informace o různých funkcích poskytovaných <xref:System.Windows.Freezable> objekty najdete v [přehledu objektů Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>
## <a name="draw-a-shape"></a>Nakreslit obrazec  
 Chcete-li nakreslit tvar, použijte <xref:System.Windows.Media.GeometryDrawing> . Vlastnost kreslení geometrie <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> popisuje tvar, který se má vykreslit, jeho <xref:System.Windows.Media.GeometryDrawing.Brush%2A> vlastnost popisuje, jak by měl být vnitřní prvek vykreslen a jeho <xref:System.Windows.Media.GeometryDrawing.Pen%2A> vlastnost popisuje, jak má být vykreslen jeho obrys.  
  
 Následující příklad používá <xref:System.Windows.Media.GeometryDrawing> k nakreslení tvaru. Tvar je popsán pomocí <xref:System.Windows.Media.GeometryGroup> a a dvou <xref:System.Windows.Media.EllipseGeometry> objektů. Vnitřek obrazce se <xref:System.Windows.Media.LinearGradientBrush> vykreslí pomocí a jeho obrys se vykreslí pomocí <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen> .  
  
 Tento příklad vytvoří následující <xref:System.Windows.Media.GeometryDrawing> .  
  
 ![GeometryDrawing dvou elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Úplný příklad najdete v tématu [Vytvoření GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 Jiné <xref:System.Windows.Media.Geometry> třídy, jako <xref:System.Windows.Media.PathGeometry> je například umožnění vytváření složitějších tvarů vytvořením křivek a oblouků. Další informace o <xref:System.Windows.Media.Geometry> objektech naleznete v tématu [geometrie Overview](geometry-overview.md).  
  
 Další informace o dalších způsobech kreslení tvarů, které nepoužívají <xref:System.Windows.Media.Drawing> objekty, naleznete v tématu [Shapes and Basic DRAWING in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>
## <a name="draw-an-image"></a>Nakreslit obrázek  
 Chcete-li nakreslit obrázek, použijte <xref:System.Windows.Media.ImageDrawing> . <xref:System.Windows.Media.ImageDrawing> <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> Vlastnost objektu popisuje vykreslení obrázku a jeho <xref:System.Windows.Media.ImageDrawing.Rect%2A> vlastnost definuje oblast, kde je obrázek vykreslen.  
  
 Následující příklad kreslí obrázek do obdélníku umístěného na pozici (75, 75), který je 100 100 pixelů. Následující ilustrace znázorňuje vytvoření v <xref:System.Windows.Media.ImageDrawing> příkladu. Bylo přidáno šedé ohraničení, které zobrazí hranice <xref:System.Windows.Media.ImageDrawing> .  
  
 ![A 100 100 ImageDrawing vytažené na &#40;75, 75&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
A 100 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Další informace o obrázcích najdete v tématu [Přehled imagí](imaging-overview.md).  
  
<a name="playmedia"></a>
## <a name="play-media-code-only"></a>Přehrát médium (jenom kód)  
  
> [!NOTE]
> I když můžete deklarovat <xref:System.Windows.Media.VideoDrawing> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , můžete načíst a přehrát pouze své médium pomocí kódu. K přehrání videa v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] použijte <xref:System.Windows.Controls.MediaElement> místo něj.  
  
 Pro přehrání zvukového souboru nebo videosouboru použijte <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer> . Existují dva způsoby, jak načítat a přehrávat média. První je použít <xref:System.Windows.Media.MediaPlayer> a sám <xref:System.Windows.Media.VideoDrawing> sebe a druhý způsob, jak vytvořit vlastní <xref:System.Windows.Media.MediaTimeline> pro použití s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> .  
  
> [!NOTE]
> Při distribuci médií do aplikace nemůžete použít mediální soubor jako prostředek projektu, jako by to byl obrázek. V souboru projektu je nutné místo toho nastavit typ média na hodnotu `Content` `CopyToOutputDirectory` `PreserveNewest` nebo `Always` .  
  
 Pokud chcete přehrávat multimédia bez vytváření vlastních <xref:System.Windows.Media.MediaTimeline> , proveďte následující kroky.  
  
1. Vytvořte <xref:System.Windows.Media.MediaPlayer> objekt.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Použijte <xref:System.Windows.Media.MediaPlayer.Open%2A> metodu pro načtení mediálního souboru.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Vytvořte <xref:System.Windows.Media.VideoDrawing> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Určete velikost a umístění pro vykreslování média nastavením <xref:System.Windows.Media.VideoDrawing.Rect%2A> vlastnosti <xref:System.Windows.Media.VideoDrawing> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Nastavte <xref:System.Windows.Media.VideoDrawing.Player%2A> vlastnost <xref:System.Windows.Media.VideoDrawing> pomocí, <xref:System.Windows.Media.MediaPlayer> kterou jste vytvořili.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Použijte <xref:System.Windows.Media.MediaPlayer.Play%2A> metodu <xref:System.Windows.Media.MediaPlayer> pro začátek přehrávání média.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Následující příklad používá <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> k přehrání videosouboru soubor a.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Chcete-li získat další ovládací prvek časování pro médium, použijte <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing> objekty a. <xref:System.Windows.Media.MediaTimeline>Umožňuje určit, zda se má video opakovat. Chcete-li použít <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.VideoDrawing> , proveďte následující kroky:  
  
1. Deklarujte <xref:System.Windows.Media.MediaTimeline> a nastavte jeho chování časování.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Vytvořte <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.MediaTimeline> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Vytvořte <xref:System.Windows.Media.MediaPlayer> a použijte <xref:System.Windows.Media.MediaClock> k nastavení jeho <xref:System.Windows.Media.MediaPlayer.Clock%2A> Vlastnosti.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Vytvořte <xref:System.Windows.Media.VideoDrawing> a přiřaďte <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing.Player%2A> vlastnost k <xref:System.Windows.Media.VideoDrawing> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Následující příklad používá <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> a a <xref:System.Windows.Media.VideoDrawing> k opakovanému přehrání videa.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Všimněte si, že když použijete <xref:System.Windows.Media.MediaTimeline> , použijete interaktivní <xref:System.Windows.Media.Animation.ClockController> vrácenou z <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnosti <xref:System.Windows.Media.MediaClock> ovládacího prvku k řízení přehrávání média namísto interaktivních metod <xref:System.Windows.Media.MediaPlayer> .  
  
<a name="drawtext"></a>
## <a name="draw-text"></a>Nakreslit text  
 Chcete-li nakreslit text, použijte <xref:System.Windows.Media.GlyphRunDrawing> a <xref:System.Windows.Media.GlyphRun> . Následující příklad používá <xref:System.Windows.Media.GlyphRunDrawing> k nakreslení textu "Hello World".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 <xref:System.Windows.Media.GlyphRun>Je objekt nižší úrovně určený pro použití s pevným formátem pro prezentace a tisk dokumentů. Jednodušší způsob, jak nakreslit text na obrazovku, je použít <xref:System.Windows.Controls.Label> nebo <xref:System.Windows.Controls.TextBlock> . Další informace o naleznete v <xref:System.Windows.Media.GlyphRun> tématu [Úvod do prvku GlyphRun Object a glyfy](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) .  
  
<a name="compositedrawingssection"></a>
## <a name="composite-drawings"></a>Složené kresby  
 <xref:System.Windows.Media.DrawingGroup>Umožňuje zkombinovat více kreseb do jediného složeného vykreslování. Pomocí <xref:System.Windows.Media.DrawingGroup> můžete kombinovat tvary, obrázky a text do jednoho <xref:System.Windows.Media.Drawing> objektu.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingGroup> ke kombinování dvou <xref:System.Windows.Media.GeometryDrawing> objektů a <xref:System.Windows.Media.ImageDrawing> objektů. Tento příklad vytvoří následující výstup.  
  
 ![Sestavování s více výkresy](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Složený výkres  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <xref:System.Windows.Media.DrawingGroup>Umožňuje také použít pro obsah masky neprůhlednosti, transformace, rastrové efekty a další operace. <xref:System.Windows.Media.DrawingGroup>operace jsou aplikovány v následujícím pořadí: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A> , <xref:System.Windows.Media.DrawingGroup.Opacity%2A> , <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> , <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> , <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> a poté <xref:System.Windows.Media.DrawingGroup.Transform%2A> .  
  
 Následující ilustrace znázorňuje pořadí, ve kterém <xref:System.Windows.Media.DrawingGroup> jsou operace aplikovány.  
  
 ![Pořadí vykreslování operací](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Pořadí operací vykreslování  
  
 Následující tabulka popisuje vlastnosti, které lze použít k manipulaci s <xref:System.Windows.Media.DrawingGroup> obsahem objektu.  
  
|Vlastnost|Popis|Obrázek|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Změní krytí vybraných částí <xref:System.Windows.Media.DrawingGroup> obsahu. Příklad naleznete v tématu [How to: Control neprůhlednost kresby](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Kresba s maskou neprůhlednosti](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Stejnoměrně změní neprůhlednost <xref:System.Windows.Media.DrawingGroup> obsahu. Tato vlastnost slouží k zajištění <xref:System.Windows.Media.Drawing> transparentního nebo částečně transparentního. Příklad naleznete v tématu [How to: použití masky neprůhlednosti pro kreslení](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![DrawingGroups s různými nastaveními neprůhlednosti](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Použije se <xref:System.Windows.Media.Effects.BitmapEffect> na <xref:System.Windows.Media.DrawingGroup> obsah. Příklad naleznete v tématu [How to: Apply BitmapEffect to a Drawing](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![Drawings s BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Ořízne <xref:System.Windows.Media.DrawingGroup> obsah do oblasti, kterou popisujete pomocí <xref:System.Windows.Media.Geometry> . Příklad naleznete v tématu [How to: Clip a Drawing](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![Drawing s definovanou oblastí oříznutí](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Přitahuje v pixelech nezávislé zařízení na pixely podél zadaných pokynů. Tato vlastnost je užitečná pro zajištění, že jemně detailní vykreslování grafiky na displejích s nízkou hodnotou DPI je ostře. Příklad najdete v tématu [použití GuidelineSet k vykreslování](how-to-apply-a-guidelineset-to-a-drawing.md).|![Sestavování s GuidelineSet a bez něj](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transformuje <xref:System.Windows.Media.DrawingGroup> obsah. Příklad naleznete v tématu [How to: použít transformaci na vykreslení](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![Otočená kresba](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>
## <a name="display-a-drawing-as-an-image"></a>Zobrazení kresby jako obrázku  
 Chcete-li zobrazit <xref:System.Windows.Media.Drawing> <xref:System.Windows.Controls.Image> ovládací prvek, použijte <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> ovládací prvek <xref:System.Windows.Controls.Image.Source%2A> a nastavte <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> vlastnost objektu na vykreslení, které chcete zobrazit.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingImage> a <xref:System.Windows.Controls.Image> ovládací prvek pro zobrazení <xref:System.Windows.Media.GeometryDrawing> . Tento příklad vytvoří následující výstup.  
  
 ![GeometryDrawing dvou elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>
## <a name="paint-an-object-with-a-drawing"></a>Malování objektu kresbou  
 A <xref:System.Windows.Media.DrawingBrush> je typ štětce, který vykreslí oblast s nakresleným objektem. Můžete ji použít k malování všech grafických objektů do kresby. <xref:System.Windows.Media.Drawing>Vlastnost <xref:System.Windows.Media.DrawingBrush> obsahuje popis <xref:System.Windows.Media.DrawingBrush.Drawing%2A> . Chcete-li objekt vykreslit pomocí <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingBrush> , přidejte jej do štětce pomocí vlastnosti štětce <xref:System.Windows.Media.Drawing> a pomocí štětce malujte grafický objekt, jako je například ovládací prvek nebo panel.  
  
 V následujících příkladech se používá <xref:System.Windows.Media.DrawingBrush> k vykreslení <xref:System.Windows.Shapes.Shape.Fill%2A> sady <xref:System.Windows.Shapes.Rectangle> se vzorem vytvořeným z <xref:System.Windows.Media.GeometryDrawing> . Tento příklad vytvoří následující výstup.  
  
 ![Dlaždicový prostředek DrawingBrush](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing se používá s prostředek DrawingBrush.  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush>Třída poskytuje celou řadu možností pro roztažení a skládání obsahu. Další informace o najdete v <xref:System.Windows.Media.DrawingBrush> tématu Přehled [malování pomocí obrázků, kreseb a vizuálů](painting-with-images-drawings-and-visuals.md) .  
  
<a name="renderingwithvisualsection"></a>
## <a name="render-a-drawing-with-a-visual"></a>Vykreslení kresby pomocí vizuálu  
 A <xref:System.Windows.Media.DrawingVisual> je typ vizuálního objektu navržený pro vykreslení kresby. Práce přímo ve vizuální vrstvě je možností pro vývojáře, kteří chtějí vytvořit vysoce přizpůsobené grafické prostředí a nejsou popsány v tomto přehledu. Další informace naleznete v tématu [using DrawingVisual Objects](using-drawingvisual-objects.md) Overview.  
  
<a name="drawingcontextobjects"></a>
## <a name="drawingcontext-objects"></a>Objekty DrawingContext  
 <xref:System.Windows.Media.DrawingContext>Třída umožňuje naplnit <xref:System.Windows.Media.Visual> <xref:System.Windows.Media.Drawing> vizuální obsah a. Mnoho takových grafických objektů na nižší úrovni používá, <xref:System.Windows.Media.DrawingContext> protože velmi efektivně popisuje grafický obsah.  
  
 I když se <xref:System.Windows.Media.DrawingContext> metody kreslení zobrazují podobně jako metody vykreslování <xref:System.Drawing.Graphics?displayProperty=nameWithType> typu, jsou ve skutečnosti velmi odlišné. <xref:System.Windows.Media.DrawingContext>se používá s grafickým systémem v zachované práci, zatímco tento <xref:System.Drawing.Graphics?displayProperty=nameWithType> typ se používá v systému grafického režimu s přímým režimem. Použijete-li <xref:System.Windows.Media.DrawingContext> příkazy pro vykreslení objektu, ukládáte ve skutečnosti sadu instrukcí pro vykreslování (přestože přesný mechanismus úložiště závisí na typu objektu, který dodává <xref:System.Windows.Media.DrawingContext> ), který bude později použit v grafickém systému. nebudete kreslit na obrazovku v reálném čase. Další informace o tom, jak funguje grafický systém Windows Presentation Foundation (WPF), naleznete v tématu [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).  
  
 Nikdy přímo nevytvoříte instanci a. <xref:System.Windows.Media.DrawingContext> můžete ale získat kontext vykreslování z určitých metod, například <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType> .  
  
<a name="enumeratevisualcontents"></a>
## <a name="enumerate-the-contents-of-a-visual"></a>Zobrazení výčtu obsahu vizuálu  
 Kromě jiných použití <xref:System.Windows.Media.Drawing> objekty poskytují také objektový model pro vytváření výčtu obsahu <xref:System.Windows.Media.Visual> .  
  
 Následující příklad používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodu k načtení <xref:System.Windows.Media.DrawingGroup> hodnoty <xref:System.Windows.Media.Visual> a k jejímu vytvoření.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Kreslení pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled geometrie](geometry-overview.md)
- [Tvary a základní kresby v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
- [– postupy](drawings-how-to-topics.md)
