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
ms.openlocfilehash: 162f13c994db70cf3b474b7109b8baf62f28e960
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imaging-overview"></a>Přehled obrázků
Toto téma obsahuje úvod do [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] umožňuje uživatelům zobrazit, transformace a formátování bitové kopie.  
  
  
<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>Součást zpracování obrázků WPF  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] poskytuje významná vylepšení imaging možnosti v rámci [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]. Byly dříve závisí na Imaging možnosti, například zobrazení rastrový obrázek nebo pomocí bitovou kopii na běžného ovládacího prvku [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] nebo [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] knihovny. Tyto [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] poskytnout základní funkce pro zpracování obrázků, ale chybí funkce, jako je podpora pro rozšiřitelnost kodeků a podpora přesnější zobrazení obrázků. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] slouží k překonání nedostatků z [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] a [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] a zadejte novou sadu [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] zobrazení a použití bitové kopie v rámci vaší aplikace.  
  
 Existují dva způsoby pro přístup [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], spravovaná a nespravovaná součásti. Nespravované součást poskytuje následující funkce.  
  
-   Model rozšiřitelnosti pro nové nebo vlastní image formáty.  
  
-   Vylepšení výkonu a zabezpečení v nativních bitových kopií formátech, včetně [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)], [!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)], [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)], [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)], [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)], [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)]a ikona ().  
  
-   Uchovávání dat vysoké image hloubka až 8 bitů na kanál (32 bitů na pixel).  
  
-   Změna velikosti nedestruktivní bitové kopie, oříznutí a otočení.  
  
-   Zjednodušená správa barev.  
  
-   Podpora pro metadata v souboru, vlastní.  
  
-   Spravované součásti využívá nespravované infrastruktury k poskytování obrázků bezproblémovou integraci s jinými [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] funkce, jako [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], animace a obrázky. Spravované součásti také výhody z Windows Presentation Foundation (WPF) pro zpracování obrázků kodeků rozšiřitelnost modelu umožňující automatické rozpoznávání nové formáty obrázků v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace.  
  
 Většina spravovaný [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] jsou umístěny ve <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> obor názvů, i když některé důležité typy, jako například <xref:System.Windows.Media.ImageBrush> a <xref:System.Windows.Media.ImageDrawing> jsou umístěny ve <xref:System.Windows.Media?displayProperty=nameWithType> obor názvů a <xref:System.Windows.Controls.Image> se nachází v <xref:System.Windows.Controls?displayProperty=nameWithType> oboru názvů.  
  
 Toto téma obsahuje další informace o spravované součásti. Další informace o nespravovanou [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] najdete v článku [nespravované WPF Imaging součást](https://msdn.microsoft.com/library/ee719902.aspx) dokumentaci.  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>Formáty obrázků WPF  
 Kodek slouží k dekódování nebo kódování formátu konkrétní média. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] zahrnuje kodeků pro [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)], [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)], [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)], [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)], [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)], [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]a ikona bitové kopie formátů. Každý z těchto kodeky umožňují aplikacím dekódovat a s výjimkou ikonu, kódovat jejich formáty příslušného obrázku.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> je důležité třída použít v dekódování a kódování bitových kopií. Je základním stavebním blokem [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] kanálu a představuje jediné konstantní sady pixelů na velikost a řešení. A <xref:System.Windows.Media.Imaging.BitmapSource> může být jednotlivý snímek více obrázku rámečku, nebo může být výsledkem transformace provést na <xref:System.Windows.Media.Imaging.BitmapSource>. Jedná o nadřazený mnoha primární třídy používané v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vytvořením bitové kopie, jako <xref:System.Windows.Media.Imaging.BitmapFrame>.  
  
 A <xref:System.Windows.Media.Imaging.BitmapFrame> se používá k ukládání skutečná data bitmapy z formátu bitové kopie. Mnoho formátů obrázku podporují pouze jeden <xref:System.Windows.Media.Imaging.BitmapFrame>, i když formátů, jako [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] podporují několik snímků za bitové kopie. Rámce používají dekodérů jako vstupní data a jsou předávány kodéry pro vytvoření bitové kopie souborů.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Media.Imaging.BitmapFrame> je vytvořený z <xref:System.Windows.Media.Imaging.BitmapSource> a pak přidá do [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] bitové kopie.  
  
 [!code-csharp[BitmapFrameExample#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Dekódování formát obrázku  
 Dekódování bitové kopie je překlad formátu bitové kopie do bitové kopie dat, která lze použít v systému. Data obrázku pak slouží k zobrazení, proces, nebo zakódujte ho do jiného formátu. Výběr dekodér je založena na formát obrázku. Výběr kodeků je automatické uvedeno konkrétní decoder. Příklady v [zobrazení obrázků v grafickém subsystému WPF](#_displayingimages) části ukazují, automatické dekódování. Vlastní formát dekodérů vyvinuté pomocí nespravovanou [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] rozhraní a zaregistrovaného na systém automaticky účastnit decoder výběr. To umožňuje vlastní formáty, který se má automaticky v zobrazit [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace.  
  
 Následující příklad ukazuje použití rastrový obrázek decoder dekódování [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] formát obrázku.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Bitovou kopii formátu kódování  
 Kódování bitové kopie je překlad bitovou kopii dat do formátu konkrétní image. Data kódovaného obrázku pak slouží k vytvoření nové soubory bitové kopie. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] poskytuje kodéry pro každý formát obrázku popsané výše.  
  
 Následující příklad ukazuje použití kodér uložte nově vytvořený rastrového obrázku.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>Zobrazení obrázků v grafickém subsystému WPF  
 Chcete-li zobrazit obrázek v aplikaci Windows Presentation Foundation (WPF) několika způsoby. Bitové kopie lze zobrazit pomocí <xref:System.Windows.Controls.Image> řízení, vykresluje na visual pomocí <xref:System.Windows.Media.ImageBrush>, nebo vykreslovány pomocí <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Použití ovládacího prvku obrázek  
 <xref:System.Windows.Controls.Image> je framework element a primární způsob zobrazení obrázků v aplikacích. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Controls.Image> mohou být používány dva způsoby, jak; atribut syntaxe nebo vlastnost syntaxe. Následující příklad ukazuje, jak Vykreslit obrázek 200 pixelů pomocí syntaxe atribut a syntaxe značek vlastnost. Další informace o syntaxi atributů a vlastnost syntaxi najdete v části [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Mnoho příkladů použití <xref:System.Windows.Media.Imaging.BitmapImage> objekt, který má odkazovat na soubor obrázku. <xref:System.Windows.Media.Imaging.BitmapImage> je speciální <xref:System.Windows.Media.Imaging.BitmapSource> která je optimalizovaná pro [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] načítání a je snadný způsob, jak zobrazit obrázky, jako <xref:System.Windows.Controls.Image.Source%2A> z <xref:System.Windows.Controls.Image> ovládacího prvku.  
  
 Následující příklad ukazuje, jak Vykreslit obrázek 200 pixelů pomocí kódu.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> implementuje <xref:System.ComponentModel.ISupportInitialize> rozhraní k optimalizaci inicializace na víc vlastností. Změny vlastností může dojít pouze během inicializace objektu. Volání <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> signál, že inicializace zahájení a <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> signál, že inicializace byla dokončena. Jakmile inicializován, změny vlastností se ignorují.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Otáčení, převod a oříznutí obrázků  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje uživatelům transformace bitové kopie pomocí vlastnosti <xref:System.Windows.Media.Imaging.BitmapImage> nebo pomocí dalších <xref:System.Windows.Media.Imaging.BitmapSource> objekty, jako <xref:System.Windows.Media.Imaging.CroppedBitmap> nebo <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Tyto bitové kopie transformace můžete škálovat nebo otočit bitovou kopii, změnit Pixelový formát obrázku nebo oříznutí obrázku.  
  
 Otočení bitové kopie se provádí pomocí <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapImage>. Otočení lze provést pouze v přírůstcích 90 stupňů. V následujícím příkladu bitová kopie je otočený o 90 stupňů.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Převod obrázku různých Pixelový formát, například ve stupních šedi se provádí pomocí <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. V následujících příkladech je obrázek převedeno na <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Oříznutí obrázku, buď <xref:System.Windows.UIElement.Clip%2A> vlastnost <xref:System.Windows.Controls.Image> nebo <xref:System.Windows.Media.Imaging.CroppedBitmap> lze použít. Obvykle, pokud jste právě chcete zobrazit část obrázku, <xref:System.Windows.UIElement.Clip%2A> by měl být použit. Pokud potřebujete ke kódování a uložit oříznutý obrázek <xref:System.Windows.Media.Imaging.CroppedBitmap> by měl být použit. V následujícím příkladu je oříznutý obrázek pomocí klip vlastnost <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Roztažení obrázků  
 <xref:System.Windows.Controls.Image.Stretch%2A> Vlastnost určuje, jak obrázek je roztažen tak, aby vyplnění jejímu kontejneru. <xref:System.Windows.Controls.Image.Stretch%2A> Vlastnost přijímá následující hodnoty, které jsou definované <xref:System.Windows.Media.Stretch> výčtu:  
  
-   <xref:System.Windows.Media.Stretch.None>: Bitové kopie není roztažen tak, aby vyplnil celou oblast výstup. Pokud je větší než oblasti výstup bitovou kopii, bitovou kopii vykreslením do oblasti výstup výstřižek co nevejde.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: Bitovou kopii se přizpůsobí oblasti výstup. Protože image výška a šířka jsou škálovat nezávisle, nemusí být zachována původní poměr stran obrázku. Aby bylo možné dokončit vyplňování kontejneru výstup může to znamená, pokřivení bitovou kopii.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: Velikost obrázku je změněna tak, aby odpovídal zcela v oblasti výstup. Poměr stran obrázku je zachován.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: Velikost obrázku je změněna tak, že úplně vyplní oblasti výstupu při zachování původní poměr stran obrázku.  
  
 V následujícím příkladu platí všechny dostupné <xref:System.Windows.Media.Stretch> výčty k <xref:System.Windows.Controls.Image>.  
  
 Následující obrázek zobrazuje výstup z příkladu a předvádí vlivu jiné <xref:System.Windows.Controls.Image.Stretch%2A> mít nastavení, kdy použít na obrázek.  
  
 ![Různá nastavení TileBrush Stretch](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Různá nastavení stretch  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Malování s obrázky  
 Bitové kopie lze také zobrazit v aplikaci Malování <xref:System.Windows.Media.Brush>. Štětce umožňují malovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] objekty s vše od jednoduchých, plné barvy pro komplexní skupiny vzory a bitové kopie. Chcete-li malovat s obrázky, použijte <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.ImageBrush> Je typ <xref:System.Windows.Media.TileBrush> , který definuje jeho obsah jako rastrový obrázek. <xref:System.Windows.Media.ImageBrush> Zobrazí jeden obrázek, který je určený jeho <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost. Můžete ovládat, jak obrázek je roztažen tak, zarovnaný a vedle sebe, umožňuje zabránit narušení a vytvořit vzory a apod. Následující obrázek znázorňuje některé účinky, které lze dosáhnout pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 ![Objekt ImageBrush výstup příklady](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Štětce bitové kopie můžete vyplnit tvarů, ovládací prvky, text a další  
  
 Následující příklad ukazuje, jak k vyplnění pozadí tlačítko s k pomocí bitové kopie <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-xaml[UsingImageBrush#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Další informace o <xref:System.Windows.Media.ImageBrush> a zobrazit obrázky Malování [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Image Metadata  
 Některé soubory, image obsahovat metadata, která popisuje obsah nebo vlastnosti souboru. Většina digitální fotoaparáty můžete například vytvořit Image, které obsahují metadata o značku a model fotoaparátu používá k zachycení bitové kopie. Každý formát obrázku zpracovává metadata jiným způsobem, ale [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] poskytuje uniform způsob ukládání a načítání metadat pro každý podporovaný bitovou kopii formátu.  
  
 Přístup k metadatům je zajišťováno prostřednictvím <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapSource> objektu. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> Vrátí <xref:System.Windows.Media.Imaging.BitmapMetadata> objekt, který zahrnuje všechny metadat obsažených bitovou kopii. Tato data mohou být v jedno schéma metadata nebo jejich kombinaci různých schémat. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] podporuje následující schémata metadata image: [!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)], tEXt (PNG textových dat), [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)], [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)], a [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)].  
  
 Aby bylo možné zjednodušit proces načítání metadat, <xref:System.Windows.Media.Imaging.BitmapMetadata> poskytuje několik s názvem vlastnosti, které jsou snadno přístupné, jako <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>, a <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. Mnoho z těchto vlastností s názvem také slouží k zápisu metadat. Další podpora pro čtení metadat poskytuje metadata dotazu čtečky. <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> Metoda se používá k načtení metadat dotazu čtečka čipových karet tím, že poskytuje řetězec dotazu, jako *"/ app1/exif /"*. V následujícím příkladu <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> slouží k získání text uložený ve *"/ Text/popis"* umístění.  
  
 [!code-cpp[BitmapMetadata#GetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Zápis metadata, se používá zapisovač dotazu metadat. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> Získá zapisovač dotazu a nastaví požadovanou hodnotu. V následujícím příkladu <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> se používá k zápisu text uložený ve *"/ Text/popis"* umístění.  
  
 [!code-cpp[BitmapMetadata#SetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Rozšiřitelnost kodeků  
 Základní funkce [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] je model rozšiřitelnosti pro nové obrazové kodeky. Tato nespravované rozhraní umožňuje vývojářům kodeků integrovat kodeky s [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] proto formáty novou bitovou kopii můžete použít automaticky [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace.  
  
 Pro ukázku rozšiřitelnosti [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], najdete v článku [Win32 ukázka kodeků](http://go.microsoft.com/fwlink/?LinkID=160052). Tento příklad znázorňuje způsob vytvoření decoder a kodéru pro formát vlastní image.  
  
> [!NOTE]
>  Kodek musí být digitálně podepsané pro systém ho rozpoznat.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Imaging.BitmapSource>  
 <xref:System.Windows.Media.Imaging.BitmapImage>  
 <xref:System.Windows.Controls.Image>  
 <xref:System.Windows.Media.Imaging.BitmapMetadata>  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Ukázka kodeků Win32](http://go.microsoft.com/fwlink/?LinkID=160052)
