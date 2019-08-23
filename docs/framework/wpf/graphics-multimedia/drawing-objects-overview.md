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
ms.openlocfilehash: d739865a692fa5ef448eba91369015580e5eda97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916317"
---
# <a name="drawing-objects-overview"></a>Přehled vykreslovaných objektů
Toto téma představuje <xref:System.Windows.Media.Drawing> objekty a popisuje, jak je použít k efektivnímu kreslení tvarů, rastrových obrázků, textu a multimédií. Objekty <xref:System.Windows.Media.Drawing> můžete použít při vytváření klipartů, malování <xref:System.Windows.Media.DrawingBrush>s nebo k používání <xref:System.Windows.Media.Visual> objektů.  

<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Co je nakreslený objekt?  
 <xref:System.Windows.Media.Drawing> Objekt popisuje viditelný obsah, jako je například tvar, rastrový obrázek, video nebo řádek textu. Různé typy kreseb popisují různé typy obsahu. Následuje seznam různých typů nakreslených objektů.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Nakreslí obrazec.  
  
- <xref:System.Windows.Media.ImageDrawing>– Nakreslí obrázek.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Kreslí text.  
  
- <xref:System.Windows.Media.VideoDrawing>– Přehraje zvukový soubor nebo videosoubor.  
  
- <xref:System.Windows.Media.DrawingGroup>– Kreslí další výkresy. K kombinování dalších kreseb do jednoho složené kresby použijte skupinu pro kreslení.  
  
 <xref:System.Windows.Media.Drawing>objekty jsou univerzální; Existuje mnoho způsobů, jak můžete <xref:System.Windows.Media.Drawing> objekt použít.  
  
- Můžete ji zobrazit jako obrázek pomocí <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> ovládacího prvku a.  
  
- Můžete ji použít s <xref:System.Windows.Media.DrawingBrush> objektem k vykreslení objektu, jako je <xref:System.Windows.Controls.Page.Background%2A> například z <xref:System.Windows.Controls.Page>.  
  
- Můžete ji použít k popisu vzhledu <xref:System.Windows.Media.DrawingVisual>.  
  
- Můžete ji použít k zobrazení výčtu obsahu <xref:System.Windows.Media.Visual>.  
  
 WPF poskytuje další typy objektů, které jsou schopné kreslit tvary, rastry, text a multimédia. Můžete například použít <xref:System.Windows.Shapes.Shape> objekty k vykreslování tvarů <xref:System.Windows.Controls.MediaElement> a ovládací prvek poskytuje další způsob, jak přidat video do aplikace. Takže když byste měli použít <xref:System.Windows.Media.Drawing> objekty? Když můžete využít funkce na úrovni rozhraní, abyste získali výhody výkonu nebo potřebujete <xref:System.Windows.Freezable> funkce. Vzhledem <xref:System.Windows.Media.Drawing> k tomu, že objekty neobsahují podporu pro [rozložení](../advanced/layout.md), vstup a zaměření, poskytují výkonnostní výhody, které jsou ideální pro popis pozadí, klipartu a pro vykreslování na <xref:System.Windows.Media.Visual> nižší úrovni s objekty.  
  
 Vzhledem k tomu, že <xref:System.Windows.Freezable> se jedná <xref:System.Windows.Media.Drawing> o objekt typu, objekty získají několik speciálních funkcí, které zahrnují následující: mohou být deklarovány jako [prostředky](../advanced/xaml-resources.md), sdílené mezi více objekty, které jsou určeny jen pro čtení pro zlepšení výkonu, klonování a bylo zabezpečeno pro přístup z více vláken. Další informace o různých funkcích poskytovaných <xref:System.Windows.Freezable> objekty najdete v [přehledu objektů Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Nakreslit obrazec  
 Chcete-li nakreslit tvar, použijte <xref:System.Windows.Media.GeometryDrawing>. <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Vlastnost kreslení geometrie popisuje tvar, který se má vykreslit, <xref:System.Windows.Media.GeometryDrawing.Brush%2A> jeho vlastnost popisuje, jak by měl být vnitřní prvek vykreslen a jeho <xref:System.Windows.Media.GeometryDrawing.Pen%2A> vlastnost popisuje, jak má být vykreslen jeho obrys.  
  
 Následující příklad používá <xref:System.Windows.Media.GeometryDrawing> k nakreslení tvaru. Tvar je popsán pomocí <xref:System.Windows.Media.GeometryGroup> a a dvou <xref:System.Windows.Media.EllipseGeometry> objektů. Vnitřek obrazce se vykreslí pomocí <xref:System.Windows.Media.LinearGradientBrush> a jeho obrys se vykreslí <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>pomocí.  
  
 Tento příklad vytvoří následující <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing dvou elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Úplný příklad najdete v tématu [Vytvoření GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 Jiné <xref:System.Windows.Media.Geometry> třídy, <xref:System.Windows.Media.PathGeometry> jako je například umožnění vytváření složitějších tvarů vytvořením křivek a oblouků. Další informace o <xref:System.Windows.Media.Geometry> objektech naleznete v tématu [geometrie Overview](geometry-overview.md).  
  
 Další informace o dalších způsobech kreslení tvarů, které nepoužívají <xref:System.Windows.Media.Drawing> objekty, naleznete v tématu [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Nakreslit obrázek  
 Chcete-li nakreslit obrázek, použijte <xref:System.Windows.Media.ImageDrawing>. Vlastnost objektu popisuje vykreslení obrázku a jeho <xref:System.Windows.Media.ImageDrawing.Rect%2A> vlastnost definuje oblast, kde je obrázek vykreslen. <xref:System.Windows.Media.ImageDrawing> <xref:System.Windows.Media.ImageDrawing.ImageSource%2A>  
  
 Následující příklad kreslí obrázek do obdélníku umístěného na pozici (75, 75), který je 100 100 pixelů. Následující ilustrace znázorňuje <xref:System.Windows.Media.ImageDrawing> vytvoření v příkladu. Bylo přidáno šedé ohraničení, které zobrazí hranice <xref:System.Windows.Media.ImageDrawing>.  
  
 ![A 100 100 ImageDrawing vykreslí se &#40;75&#41; ] . 75 (./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
A 100 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Další informace o obrázcích najdete v tématu [Přehled imagí](imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Přehrát médium (jenom kód)  
  
> [!NOTE]
> I když můžete deklarovat <xref:System.Windows.Media.VideoDrawing> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete načíst a přehrát pouze své médium pomocí kódu. K přehrání videa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]v <xref:System.Windows.Controls.MediaElement> použijte místo něj.  
  
 Pro přehrání zvukového souboru nebo videosouboru použijte <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>a. Existují dva způsoby, jak načítat a přehrávat média. <xref:System.Windows.Media.MediaPlayer> První je použít <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.MediaTimeline> a sám sebe a druhý způsob, jak vytvořit vlastní pro použití s a. <xref:System.Windows.Media.VideoDrawing>  
  
> [!NOTE]
> Při distribuci médií do aplikace nemůžete použít mediální soubor jako prostředek projektu, jako by to byl obrázek. V souboru projektu je nutné místo toho `Content` nastavit typ média na `CopyToOutputDirectory` `PreserveNewest` hodnotu nebo `Always`.  
  
 Pokud chcete přehrávat multimédia bez vytváření vlastních <xref:System.Windows.Media.MediaTimeline>, proveďte následující kroky.  
  
1. <xref:System.Windows.Media.MediaPlayer> Vytvořte objekt.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. <xref:System.Windows.Media.MediaPlayer.Open%2A> Použijte metodu pro načtení mediálního souboru.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Vytvoření <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Určete velikost a umístění pro vykreslování média <xref:System.Windows.Media.VideoDrawing.Rect%2A> nastavením vlastnosti. <xref:System.Windows.Media.VideoDrawing>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. <xref:System.Windows.Media.VideoDrawing.Player%2A> Nastavte vlastnost <xref:System.Windows.Media.VideoDrawing> pomocí ,kteroujstevytvořili.<xref:System.Windows.Media.MediaPlayer>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. <xref:System.Windows.Media.MediaPlayer.Play%2A> Použijte metodu <xref:System.Windows.Media.MediaPlayer> pro začátek přehrávání média.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Následující příklad používá <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> k přehrání videosouboru soubor a.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Chcete-li získat další ovládací prvek časování pro médium, <xref:System.Windows.Media.MediaTimeline> použijte <xref:System.Windows.Media.MediaPlayer> s objekty <xref:System.Windows.Media.VideoDrawing> a. <xref:System.Windows.Media.MediaTimeline> Umožňuje určit, zda se má video opakovat. Chcete-li <xref:System.Windows.Media.MediaTimeline> použít <xref:System.Windows.Media.VideoDrawing>s, proveďte následující kroky:  
  
1. Deklarujte <xref:System.Windows.Media.MediaTimeline> a nastavte jeho chování časování.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. <xref:System.Windows.Media.MediaClock> Vytvořte<xref:System.Windows.Media.MediaTimeline>z.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Vytvořte a použijte k nastavení jeho <xref:System.Windows.Media.MediaPlayer.Clock%2A> vlastnosti. <xref:System.Windows.Media.MediaClock> <xref:System.Windows.Media.MediaPlayer>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Vytvořte a přiřaďte <xref:System.Windows.Media.VideoDrawing.Player%2A> vlastnost <xref:System.Windows.Media.MediaPlayer> k .<xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.VideoDrawing>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Následující příklad používá <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> s a a <xref:System.Windows.Media.VideoDrawing> k opakovanému přehrání videa.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Všimněte si, že když použijete <xref:System.Windows.Media.MediaTimeline>, použijete interaktivní <xref:System.Windows.Media.Animation.ClockController> vrácenou <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnosti ovládacího prvku k řízení přehrávání média namísto interaktivních metod <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Nakreslit text  
 Chcete-li nakreslit text, <xref:System.Windows.Media.GlyphRunDrawing> použijte <xref:System.Windows.Media.GlyphRun>a. Následující příklad používá <xref:System.Windows.Media.GlyphRunDrawing> k nakreslení textu "Hello World".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 <xref:System.Windows.Media.GlyphRun> Je objekt nižší úrovně určený pro použití s pevným formátem pro prezentace a tisk dokumentů. Jednodušší způsob, jak nakreslit text na obrazovku, je použít <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock>nebo. Další informace o <xref:System.Windows.Media.GlyphRun>naleznete v tématu [Úvod do prvku GlyphRun Object a glyfy](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) .  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Složené kresby  
 <xref:System.Windows.Media.DrawingGroup> Umožňuje zkombinovat více kreseb do jediného složeného vykreslování. Pomocí <xref:System.Windows.Media.DrawingGroup>můžete kombinovat tvary, obrázky a text do jednoho <xref:System.Windows.Media.Drawing> objektu.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingGroup> ke kombinování dvou <xref:System.Windows.Media.GeometryDrawing> objektů a <xref:System.Windows.Media.ImageDrawing> objektů. Tento příklad vytvoří následující výstup.  
  
 ![Sestavování s více výkresy](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Složený výkres  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Umožňuje <xref:System.Windows.Media.DrawingGroup> také použít pro obsah masky neprůhlednosti, transformace, rastrové efekty a další operace. <xref:System.Windows.Media.DrawingGroup>operace jsou aplikovány v následujícím pořadí: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>a poté <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Následující ilustrace znázorňuje pořadí, ve kterém <xref:System.Windows.Media.DrawingGroup> jsou operace aplikovány.  
  
 ![Pořadí vykreslování operací](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Pořadí operací vykreslování  
  
 Následující tabulka popisuje vlastnosti, které lze použít k manipulaci s <xref:System.Windows.Media.DrawingGroup> obsahem objektu.  
  
|Vlastnost|Popis|Obrázek|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Změní krytí vybraných částí <xref:System.Windows.Media.DrawingGroup> obsahu. Příklad naleznete v tématu [How to: Ovládat průhlednost kresby](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Kresba s maskou] neprůhlednosti (./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Stejnoměrně změní neprůhlednost <xref:System.Windows.Media.DrawingGroup> obsahu. Tato vlastnost slouží k zajištění <xref:System.Windows.Media.Drawing> transparentního nebo částečně transparentního. Příklad naleznete v tématu [How to: Aplikujte na kresbu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90))masku neprůhlednosti.|![DrawingGroups s různými nastaveními] neprůhlednosti (./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Použije se <xref:System.Windows.Media.Effects.BitmapEffect> na obsah <xref:System.Windows.Media.DrawingGroup> . Příklad naleznete v tématu [How to: Použijte BitmapEffect pro kreslení](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![Drawings s BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Ořízne <xref:System.Windows.Media.Geometry>obsah do oblasti, kterou popisujete pomocí. <xref:System.Windows.Media.DrawingGroup> Příklad naleznete v tématu [How to: Vytvořte výstřižek kresby](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![Drawing s definovanou oblastí oříznutí](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Přitahuje v pixelech nezávislé zařízení na pixely podél zadaných pokynů. Tato vlastnost je užitečná pro zajištění, že jemně detailní vykreslování grafiky na displejích s nízkou hodnotou DPI je ostře. Příklad najdete v tématu [použití GuidelineSet k vykreslování](how-to-apply-a-guidelineset-to-a-drawing.md).|![Sestavování s GuidelineSet a bez něj](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transformuje <xref:System.Windows.Media.DrawingGroup> obsah. Příklad naleznete v tématu [How to: Použijte transformaci na vykreslení](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![Otočená kresba](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Zobrazení kresby jako obrázku  
 Chcete-li <xref:System.Windows.Media.Drawing> zobrazit <xref:System.Windows.Controls.Image> ovládací <xref:System.Windows.Controls.Image.Source%2A> prvek <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Media.DrawingImage> , použijte <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> jako <xref:System.Windows.Controls.Image> ovládací prvek a nastavte vlastnost objektu na vykreslení, které chcete zobrazit.  
  
 Následující příklad používá <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> a ovládací prvek pro zobrazení <xref:System.Windows.Media.GeometryDrawing>. Tento příklad vytvoří následující výstup.  
  
 ![GeometryDrawing dvou elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Malování objektu kresbou  
 A <xref:System.Windows.Media.DrawingBrush> je typ štětce, který vykreslí oblast s nakresleným objektem. Můžete ji použít k malování všech grafických objektů do kresby. <xref:System.Windows.Media.Drawing> Vlastnost obsahuje<xref:System.Windows.Media.DrawingBrush> popis .<xref:System.Windows.Media.DrawingBrush.Drawing%2A> Chcete-li <xref:System.Windows.Media.Drawing> objekt vykreslit <xref:System.Windows.Media.DrawingBrush>pomocí, přidejte jej do <xref:System.Windows.Media.Drawing> štětce pomocí vlastnosti štětce a pomocí štětce malujte grafický objekt, jako je například ovládací prvek nebo panel.  
  
 V následujících příkladech se <xref:System.Windows.Media.DrawingBrush> používá k <xref:System.Windows.Shapes.Shape.Fill%2A> vykreslení sady <xref:System.Windows.Shapes.Rectangle> se vzorem vytvořeným z <xref:System.Windows.Media.GeometryDrawing>. Tento příklad vytvoří následující výstup.  
  
 ![Dlaždicový prostředek DrawingBrush](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing se používá s prostředek DrawingBrush.  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush> Třída poskytuje celou řadu možností pro roztažení a skládání obsahu. Další informace o <xref:System.Windows.Media.DrawingBrush>najdete v tématu Přehled [malování pomocí obrázků, kreseb a vizuálů](painting-with-images-drawings-and-visuals.md) .  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Vykreslení kresby pomocí vizuálu  
 A <xref:System.Windows.Media.DrawingVisual> je typ vizuálního objektu navržený pro vykreslení kresby. Práce přímo ve vizuální vrstvě je možností pro vývojáře, kteří chtějí vytvořit vysoce přizpůsobené grafické prostředí a nejsou popsány v tomto přehledu. Další informace naleznete v tématu [using DrawingVisual Objects](using-drawingvisual-objects.md) Overview.  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>Objekty DrawingContext  
 Třída umožňuje naplnit <xref:System.Windows.Media.Drawing>vizuálníobsaha. <xref:System.Windows.Media.Visual> <xref:System.Windows.Media.DrawingContext> Mnoho takových grafických objektů na nižší úrovni používá, <xref:System.Windows.Media.DrawingContext> protože velmi efektivně popisuje grafický obsah.  
  
 I když se metody <xref:System.Drawing.Graphics?displayProperty=nameWithType> Kreslenízobrazujípodobnějakometodyvykreslovánítypu,jsouveskutečnostivelmiodlišné.<xref:System.Windows.Media.DrawingContext> <xref:System.Windows.Media.DrawingContext>se používá s grafickým systémem v zachované práci, <xref:System.Drawing.Graphics?displayProperty=nameWithType> zatímco tento typ se používá v systému grafického režimu s přímým režimem. Použijete <xref:System.Windows.Media.DrawingContext> -li příkazy pro vykreslení objektu, ukládáte ve skutečnosti sadu instrukcí pro vykreslování (přestože přesný mechanismus úložiště závisí na typu objektu, který <xref:System.Windows.Media.DrawingContext>poskytuje), který bude později použit v grafickém systému. nekreslí na obrazovku v reálném čase. Další informace o tom, jak funguje grafický systém Windows Presentation Foundation (WPF), naleznete v tématu [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).  
  
 Nikdy přímo nevytvoříte instanci <xref:System.Windows.Media.DrawingContext>a. můžete ale získat kontext vykreslování z určitých metod, <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> například a <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Zobrazení výčtu obsahu vizuálu  
 Kromě jiných použití <xref:System.Windows.Media.Drawing> objekty poskytují také objektový model pro vytváření výčtu obsahu <xref:System.Windows.Media.Visual>.  
  
 Následující příklad používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodu k <xref:System.Windows.Media.DrawingGroup> načtení hodnoty <xref:System.Windows.Media.Visual> a k jejímu vytvoření.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled geometrie](geometry-overview.md)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
- [Témata s postupy](drawings-how-to-topics.md)
