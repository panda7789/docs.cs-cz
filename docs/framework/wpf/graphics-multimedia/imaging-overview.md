---
title: Přehled obrázků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- metadata [WPF], images
- displaying images [WPF]
- Imaging API [WPF]
- image metadata [WPF]
- converting images [WPF]
- encoding image formats [WPF]
- format decoding for images [WPF]
- painting with images [WPF]
- stretching images [WPF]
- images [WPF], about imaging
- format encoding for images [WPF]
- cropping images [WPF]
- decoding image formats [WPF]
- rotating images [WPF]
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
ms.openlocfilehash: 45214b5f0e6827c36f87a4d45592ff0989c9a877
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58133255"
---
# <a name="imaging-overview"></a>Přehled obrázků
Toto téma obsahuje úvod do [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] umožňuje vývojářům zobrazit, transformaci a formátu Image.  
  
  
<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>Součást zpracování obrázků WPF  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] poskytuje významná vylepšení imaging možnosti v rámci [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]. Byly dříve spolehlivé po Imaging možnosti, jako například zobrazení rastrový obrázek nebo pomocí image na běžný ovládací prvek [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] nebo [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] knihovny. Tyto [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] poskytuje základní funkce pro zpracování obrázků, ale chybějící funkce, jako je podpora kodek rozšíření a podporu image velmi přesné. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] slouží k překonání nedostatky z [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] a [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] a zadejte novou sadu [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] k zobrazení a používání imagí v rámci vašich aplikací.  
  
 Existují dva způsoby přístupu k [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], spravované a nespravované součásti. Nespravované součásti poskytuje následující funkce.  
  
-   Model rozšiřitelnosti pro nové nebo speciální obrázků ve formátu.  
  
-   Vylepšili jsme výkon a zabezpečení na nativních bitových kopií formátů, včetně [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)], [!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)], [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)], [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)], [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)], [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)]a ikony (ICO).  
  
-   Zachování dat vysoké bitové hloubky obrázků až 8 bitů na kanál (32 bitů na pixel).  
  
-   Škálování nedestruktivní image, oříznutí a otočení.  
  
-   Zjednodušená správa barev.  
  
-   Podpora metadat v souboru a specializované.  
  
-   Spravovaná komponenta využívá nespravované infrastruktura, která poskytuje bezproblémovou integraci imagí s jinými [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] funkce, jako [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], animace a grafiky. Spravované součásti taky další výhody z Windows Presentation Foundation (WPF) pro zpracování obrázků kodek model rozšiřitelnosti umožňující automatické rozpoznávání nové formátů obrázku v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací.  
  
 Většina spravovanou [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] jsou umístěny v <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> obor názvů, i když některé důležité typy, jako <xref:System.Windows.Media.ImageBrush> a <xref:System.Windows.Media.ImageDrawing> jsou umístěny v <xref:System.Windows.Media?displayProperty=nameWithType> obor názvů a <xref:System.Windows.Controls.Image> se nachází v <xref:System.Windows.Controls?displayProperty=nameWithType> oboru názvů.  
  
 Toto téma obsahuje další informace o spravované součásti. Další informace o nespravovanou [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] najdete v článku [nespravované součásti Imaging Component WPF](/windows/desktop/wic/-wic-lh) dokumentaci.  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>WPF formátů obrázku  
 Kodek slouží k dekódování nebo kódování formátu konkrétního média. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] zahrnuje kodek pro [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)], [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)], [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)], [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)], [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)], [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]a ikonu formátů obrázku. Každá z těchto kodeky umožňují aplikacím dekódovat a s výjimkou ikonu kódování formátů jejich odpovídajících obrázku.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> je důležité třídy používané kódování a dekódování obrázků. Je základním stavebním blokem [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] kanálu a představuje jediné konstantní sady pixelů na velikost a řešení. A <xref:System.Windows.Media.Imaging.BitmapSource> může být jednotlivý snímek více bitové kopie snímků nebo může být výsledek transformace provedla <xref:System.Windows.Media.Imaging.BitmapSource>. Je nadřazeného člena řadu primární třídy používané v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vytvořením bitové kopie jako <xref:System.Windows.Media.Imaging.BitmapFrame>.  
  
 A <xref:System.Windows.Media.Imaging.BitmapFrame> se používá k ukládání dat skutečné rastrového obrázku z formátu image. Mnoho formátů obrázku podporují jenom jeden <xref:System.Windows.Media.Imaging.BitmapFrame>, i když formáty, jako [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] podporovat více snímků za bitové kopie. Snímky jsou používány dekodérů jako vstupní data a jsou předány kodérů pro vytvoření bitové kopie souborů.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Media.Imaging.BitmapFrame> je vytvořený z <xref:System.Windows.Media.Imaging.BitmapSource> a pak přidá do [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] bitové kopie.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Dekódování formátu obrázku  
 Dekódování obrázku je převod formátu obrázku data bitové kopie, která lze použít v systému. Obrazová data pak slouží k zobrazení, proces, nebo do jiného formátu kódování. Výběr dekodér je založen na formát obrázku. Kodek výběr je automatické uvedeno konkrétní dekodéru. Příklady v [zobrazování obrázků v subsystému WPF](#_displayingimages) části ukazují automatické dekódování. Vlastní formát dekodérů vyvinuté pomocí nespravovanou [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] rozhraní a registrovaný v systému automaticky účastnit dekodér výběru. To umožňuje vlastní formáty, který se má zobrazit automaticky v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací.  
  
 Následující příklad ukazuje použití dekodér rastrový obrázek pro dekódování [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] formát obrázku.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Kódování formátu Image  
 Kódování obrázků je překladu dat obrázků do formátu konkrétní image. Kódovaný obrazová data lze potom vytvořit nové bitové kopie. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] poskytuje kodérů pro každou z formátů obrázku je popsáno výše.  
  
 Následující příklad ukazuje použití kodéru uložte nově vytvořený rastrový obrázek.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>Zobrazení obrázků v subsystému WPF  
 Existuje několik způsobů, jak zobrazit obrázek v aplikaci Windows Presentation Foundation (WPF). Image je možné zobrazit pomocí <xref:System.Windows.Controls.Image> ovládacího prvku, vykreslení na vizuál pomocí <xref:System.Windows.Media.ImageBrush>, nebo vykresleno pomocí <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Použití ovládacího prvku obrázek  
 <xref:System.Windows.Controls.Image> je element rozhraní framework a hlavní způsob, jak zobrazit obrázky v aplikacích. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Controls.Image> lze použít v dva způsoby, jak; syntaxe atributu nebo syntaxe vlastnosti. Následující příklad ukazuje způsob, aby se vykreslil obraz 200 pixelů pomocí syntaxe atributu a vlastnost syntaxe značek. Další informace o syntaxi atributů a vlastnost syntaxe, naleznete v tématu [přehled vlastností závislosti](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Mnoho příkladů použití <xref:System.Windows.Media.Imaging.BitmapImage> objektu, který chcete odkazovat na soubor obrázku. <xref:System.Windows.Media.Imaging.BitmapImage> je specializovaný <xref:System.Windows.Media.Imaging.BitmapSource> , který je optimalizovaný pro [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] načítání a je snadný způsob, jak zobrazit obrázky jako <xref:System.Windows.Controls.Image.Source%2A> ze <xref:System.Windows.Controls.Image> ovládacího prvku.  
  
 Následující příklad ukazuje, jak Vykreslit obrázek 200 pixelů pomocí kódu.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> implementuje <xref:System.ComponentModel.ISupportInitialize> rozhraní optimalizovat inicializací na více vlastností. Změny vlastností může dojít pouze během inicializace objektu. Volání <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> který signalizuje, že byl zahájen, že inicializace a <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> signál, že inicializace byla dokončena. Po inicializaci změny vlastností se ignorují.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Otočení, převádění a oříznutí obrázků  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje uživatelům transformace imagí pomocí vlastnosti <xref:System.Windows.Media.Imaging.BitmapImage> nebo pomocí dalších <xref:System.Windows.Media.Imaging.BitmapSource> objekty, jako <xref:System.Windows.Media.Imaging.CroppedBitmap> nebo <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Tyto image transformace můžete škálovat otočení obrázku, změnit formát pixelu obrázku nebo oříznutí obrázku.  
  
 Otočení obrázku se provádí pomocí <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapImage>. Otočení lze provést pouze v přírůstcích o 90 stupňů. V následujícím příkladu je obrázek otočenou o 90 stupňů.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Převod obrázku různých žádnému pixelovému formátu tak, jak se provádí ve stupních šedi pomocí <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. V následujících příkladech bitovou kopii je převedena na <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Pokud chcete provést oříznutí obrázku, buď <xref:System.Windows.UIElement.Clip%2A> vlastnost <xref:System.Windows.Controls.Image> nebo <xref:System.Windows.Media.Imaging.CroppedBitmap> lze použít. Obvykle využijete, pokud chcete zobrazit část obrázku <xref:System.Windows.UIElement.Clip%2A> by měla sloužit. Pokud potřebujete kódovat a ukládat oříznutý obrázek <xref:System.Windows.Media.Imaging.CroppedBitmap> by měla sloužit. V následujícím příkladu je oříznutý image pomocí příkazu Vlastnosti galerie <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Roztažení obrázků  
 <xref:System.Windows.Controls.Image.Stretch%2A> Vlastnost určuje, jak je obrázek roztažený tak, aby vyplnil svého kontejneru. <xref:System.Windows.Controls.Image.Stretch%2A> Vlastnost přijímá následující hodnoty, které jsou definované <xref:System.Windows.Media.Stretch> výčtu:  
  
-   <xref:System.Windows.Media.Stretch.None>: Obrázek není roztažená tak, aby vyplnil výstupní oblasti. Pokud je větší než výstupní oblast bitovou kopii, bitovou kopii linie výstupní oblasti oříznutí, co se nevejde.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: Na obrázku se přizpůsobí výstupní oblasti. Protože jsou nezávisle image výšku a šířku, nemusí být zachovaná původní poměr stran obrázku. To znamená může být pokřivení bitovou kopii pro úplně naplnění výstupní kontejner.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: Na obrázku je škálovat tak, aby zcela v rámci výstupní oblasti. Poměr stran obrázku je zachován.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: Na obrázku je škálovat tak, že zcela vyplní výstupní oblasti současně v něm zachovat původní poměr stran obrázku.  
  
 Následující příklad používá všechny dostupné <xref:System.Windows.Media.Stretch> výčty do <xref:System.Windows.Controls.Image>.  
  
 Na následujícím obrázku zobrazuje výstup z příkladu a ukazuje rozdíly ovlivňují <xref:System.Windows.Controls.Image.Stretch%2A> mít nastavení, kdy použít u obrázku.  
  
 ![Různá nastavení TileBrush Stretch](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Různá nastavení stretch  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Malování s použitím obrázků  
 Image můžete také zobrazit v aplikaci můžete Malování <xref:System.Windows.Media.Brush>. Štětce umožňují vykreslení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] objekty se vše od jednoduchých, plné barvy pro komplexní sady vzorce a Image. Malování pomocí obrázků, použijte <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.ImageBrush> k typu <xref:System.Windows.Media.TileBrush> jeho obsah, který definuje jako rastrový obrázek. <xref:System.Windows.Media.ImageBrush> Zobrazí jedné image, která je určená jeho <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost. Můžete určit, jak je roztažená bitovou kopii, zarovnané a vedle sebe, umožňuje nedošlo ke zkreslení a vytvářet modely a další efekty. Následující obrázek znázorňuje některé efekty, které lze nastavit pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 ![ImageBrush output examples](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Štětce Image můžete přejít k vyplnění obrazců, ovládacích prvků, textu a další  
  
 Následující příklad ukazuje, jak se má Vymalovat pozadí tlačítka pomocí image pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Další informace o <xref:System.Windows.Media.ImageBrush> a podívejte se, vykreslování obrazů [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Metadata obrázků  
 Některé soubory obrázku obsahují metadata, která popisuje vlastnosti souboru nebo obsah. Například většina digitální fotoaparáty vytvořit Image, které obsahují metadata o značku a model fotoaparátu/kamery, používá k zachycení bitové kopie. Každý formát obrázku zpracovává metadat jinak, ale [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] poskytuje jednotným způsobem ukládání a načítání metadat pro všechny formáty podporované image.  
  
 Přístup k metadatům je poskytována prostřednictvím <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapSource> objektu. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> Vrátí <xref:System.Windows.Media.Imaging.BitmapMetadata> objekt, který zahrnuje všechny metadat obsažených imagí. Tato data mohou být v jedné metadata schématu nebo kombinaci různých režimů. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] podporuje následující schémata metadata obrázků: [!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)], tEXt (PNG textová Data), [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)], [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)], a [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)].  
  
 Aby bylo možné zjednodušit proces načítání metadat, <xref:System.Windows.Media.Imaging.BitmapMetadata> poskytuje několik pojmenované vlastnosti, které mohou být snadno přístupné, jako <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>, a <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. Mnohé z těchto pojmenované vlastnosti také umožňuje zápis metadat. Čtečka metadat pro dotaz poskytuje další podporu pro čtení metadat. <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> Metoda se používá k načtení čtečku metadat dotazu zadáním řetězce dotazu *"/ app1/exif /"*. V následujícím příkladu <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> slouží k získání uložených v textu *"/ Text/popis"* umístění.  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Zápis metadat se používá zapisovač dotazů metadat. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> Získá zapisovač dotazů a nastaví požadovanou hodnotu. V následujícím příkladu <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> se používá k vypsání textu v uložených *"/ Text/popis"* umístění.  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Kodek rozšiřitelnosti  
 Základní funkce [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] je model rozšiřitelnosti kodeky nový obrázek. Tato nespravovaná rozhraní povolit kodek vývojářům integrovat kodeky [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tak může automaticky využívat nové image formáty [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací.  
  
 Pro ukázku rozšiřitelnosti [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], najdete v článku [Win32 ukázka kodek](https://go.microsoft.com/fwlink/?LinkID=160052). Tento příklad ukazuje, jak vytvořit dekodér a kodér formátu vlastní image.  
  
> [!NOTE]
>  Kodek musí být digitálně podepsané, systém ho.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Ukázka kodek Win32](https://go.microsoft.com/fwlink/?LinkID=160052)
