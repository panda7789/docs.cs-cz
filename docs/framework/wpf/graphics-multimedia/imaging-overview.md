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
ms.openlocfilehash: a4151ff610c67ac762f0096c6a136f4475317782
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636637"
---
# <a name="imaging-overview"></a>Přehled obrázků
Toto téma poskytuje Úvod do komponenty Microsoft Windows Presentation Foundation Imaging. WPF Imaging umožňuje vývojářům zobrazovat, transformovat a formátovat obrázky.  

## <a name="wpf-imaging-component"></a>Komponenta WPF Imaging  
 Vytváření imagí WPF nabízí v systému Microsoft Windows významná vylepšení funkcí pro vytváření bitových kopií. Možnosti imagí, jako je zobrazení rastrového obrázku nebo použití obrázku na běžném ovládacím prvku, byly dřív závislé na knihovnách Microsoft Windows GDI (GDI) nebo Microsoft Windows GDI+. Tato rozhraní API poskytují základní funkce pro zpracování obrazu, ale chybí funkce, jako je podpora rozšiřitelnosti kodeku a podpora obrázků s vysokou kvalitou. Program WPF Imaging je navržený tak, aby překonal nedostatky GDI a GDI+ a poskytoval novou sadu rozhraní API pro zobrazení a používání imagí v rámci aplikací.  
  
 Existují dva způsoby, jak získat přístup k rozhraní WPF Imaging API, spravované komponentě a nespravované součásti. Nespravované komponenty poskytují následující funkce.  
  
- Model rozšiřitelnosti pro nové nebo speciální formáty obrázků.  
  
- Vylepšený výkon a zabezpečení v nativních formátech obrázků, včetně rastrového obrázku (BMP), společné funkce Windows Graphics Group (JPEG), Portable Network Graphics (PNG), formátu TIFF (Tagged Image File Format), Microsoft Windows Media Photo, GIF (Graphics Interchange Format), a ikona (. ico).  
  
- Uchovávání dat bitové kopie s vysokou bitovou hloubkou až na 8 bitů na kanál (32 bitů na pixel).  
  
- Nedestruktivní škálování obrazu, ořezávání a rotace.  
  
- Zjednodušená správa barev.  
  
- Podpora pro osobní metadata v souboru.  
  
- Spravovaná komponenta využívá nespravovanou infrastrukturu k zajištění bezproblémové integrace imagí s dalšími funkcemi WPF, jako jsou [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], animace a grafika. Spravovaná komponenta také přináší výhody modelu rozšiřitelnosti kodeku pro Windows Presentation Foundation (WPF), která umožňuje automatické rozpoznávání nových formátů obrázků v aplikacích WPF.  
  
 Většina spravovaných rozhraní API pro Imaging pro WPF se nachází v oboru názvů <xref:System.Windows.Media.Imaging?displayProperty=nameWithType>, i když je v oboru názvů <xref:System.Windows.Media?displayProperty=nameWithType> několik důležitých typů, například <xref:System.Windows.Media.ImageBrush> a <xref:System.Windows.Media.ImageDrawing> nacházející se v oboru názvů <xref:System.Windows.Controls.Image>.  
  
 V tomto tématu najdete další informace o spravované komponentě. Další informace o nespravovaném rozhraní API najdete v dokumentaci ke [komponentě nespravovaného zpracování WPF](/windows/desktop/wic/-wic-lh) .  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>Formáty obrázků WPF  

 Kodek slouží k dekódování nebo kódování konkrétního formátu média. Obrázky WPF obsahují kodek pro formáty BMP, JPEG, PNG, TIFF, Windows Media Photo, GIF a ICON. Každý z těchto kodeků umožňuje aplikacím dekódovat a s výjimkou ikony zakódovat příslušné formáty obrázků.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> je důležitou třídou použitou při dekódování a kódování imagí. Je základním stavebním blokem kanálu pro zpracování obrazu WPF a představuje jednu konstantní sadu pixelů v určité velikosti a rozlišení. <xref:System.Windows.Media.Imaging.BitmapSource> může být individuální rámec obrázku s více snímky, nebo může být výsledkem transformace provedené na <xref:System.Windows.Media.Imaging.BitmapSource>. Je nadřazeným prvkem mnoha primárních tříd, které se používají v grafickém rozhraní WPF, jako je například <xref:System.Windows.Media.Imaging.BitmapFrame>.  
  
 <xref:System.Windows.Media.Imaging.BitmapFrame> slouží k uložení skutečných dat bitmapy formátu obrázku. Mnoho formátů obrázků podporuje pouze jeden <xref:System.Windows.Media.Imaging.BitmapFrame>, i když formáty jako GIF a TIFF podporují více snímků na obrázek. Tyto rámce jsou používány dekodéry jako vstupní data a jsou předávány kodérům pro vytváření souborů imagí.  
  
 Následující příklad ukazuje, jak je vytvořen <xref:System.Windows.Media.Imaging.BitmapFrame> z <xref:System.Windows.Media.Imaging.BitmapSource> a následně přidán do obrázku TIFF.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Dekódování formátu obrázku  
 Dekódování obrázku je převod formátu obrázku na data obrázku, který může být použit systémem. Data obrázku pak můžete použít k zobrazení, zpracování nebo kódování v jiném formátu. Výběr dekodéru je založen na formátu obrázku. Výběr kodeku je automatický, pokud se nezadá konkrétní dekodér. Příklady v části [zobrazení obrázků v](#_displayingimages) subsystému WPF ukazují automatické dekódování. Dekodéry vlastního formátu vyvinuté pomocí nespravovaných rozhraní WPF Imaging a zaregistrovaných v systému se automaticky účastní výběru dekodéru. To umožňuje, aby se vlastní formáty zobrazovaly automaticky v aplikacích WPF.  
  
 Následující příklad demonstruje použití dekodéru rastrového obrázku k dekódování obrázku formátu BMP.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Kódování formátu obrázku  
 Kódování obrázku je převod dat obrázku do konkrétního formátu obrázku. Data kódované image pak můžete použít k vytvoření nových souborů imagí. Program WPF Imaging poskytuje kodéry pro každý z formátů obrázků popsaných výše.  
  
 Následující příklad ukazuje použití kodéru k uložení nově vytvořeného rastrového obrázku.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>Zobrazení obrázků v subsystému WPF  
 Existuje několik způsobů, jak zobrazit obrázek v aplikaci Windows Presentation Foundation (WPF). Obrázky lze zobrazit pomocí ovládacího prvku <xref:System.Windows.Controls.Image>, vykresleného v vizuálu pomocí <xref:System.Windows.Media.ImageBrush>nebo vykresleného pomocí <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Použití ovládacího prvku obrázek  
 <xref:System.Windows.Controls.Image> je prvkem architektury a hlavním způsobem zobrazení obrázků v aplikacích. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]lze <xref:System.Windows.Controls.Image> použít dvěma způsoby; syntaxe atributu nebo syntaxe vlastnosti Následující příklad ukazuje, jak vykreslit obrázek 200 pixelů na šířku pomocí syntaxe atributů i syntaxe značek vlastností. Další informace o syntaxi atributů a syntaxi vlastností najdete v tématu [Přehled vlastností závislosti](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Mnohé z příkladů používají objekt <xref:System.Windows.Media.Imaging.BitmapImage> pro odkazování na soubor obrázku. <xref:System.Windows.Media.Imaging.BitmapImage> je specializované <xref:System.Windows.Media.Imaging.BitmapSource> optimalizované pro [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] načítání a je to snadný způsob, jak zobrazit obrázky jako <xref:System.Windows.Controls.Image.Source%2A> ovládacího prvku <xref:System.Windows.Controls.Image>.  
  
 Následující příklad ukazuje, jak vykreslit obrázek 200 pixelů v širším formátu pomocí kódu.  
  
> [!NOTE]
> <xref:System.Windows.Media.Imaging.BitmapImage> implementuje rozhraní <xref:System.ComponentModel.ISupportInitialize> k optimalizaci inicializace u více vlastností. Změny vlastností mohou nastat pouze při inicializaci objektu. Zavolejte <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> k signalizaci, že inicializace začala a <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> k signalizaci, že se inicializace dokončila. Po inicializaci jsou změny vlastností ignorovány.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Otáčení, převádění a ořezávání imagí  
 WPF umožňuje uživatelům transformovat obrázky pomocí vlastností <xref:System.Windows.Media.Imaging.BitmapImage> nebo pomocí dalších objektů <xref:System.Windows.Media.Imaging.BitmapSource>, jako je <xref:System.Windows.Media.Imaging.CroppedBitmap> nebo <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Tyto transformace obrázků mohou škálovat nebo otáčet obrázek, měnit formát pixelu obrázku nebo oříznout obrázek.  
  
 Otočení obrázku se provádí pomocí vlastnosti <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> <xref:System.Windows.Media.Imaging.BitmapImage>. Rotace se dají provádět jenom v přírůstcích po 90 stupních. V následujícím příkladu je obrázek otočen 90 stupňů.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Převod obrázku na jiný formát pixelu, například ve stupních šedi, se provádí pomocí <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. V následujících příkladech je obrázek převeden na <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Chcete-li oříznout obrázek, lze použít buď vlastnost <xref:System.Windows.UIElement.Clip%2A> <xref:System.Windows.Controls.Image> nebo <xref:System.Windows.Media.Imaging.CroppedBitmap>. Pokud chcete pouze zobrazit část obrázku, je třeba použít <xref:System.Windows.UIElement.Clip%2A>. Pokud potřebujete zakódovat a uložit oříznutou bitovou kopii, je třeba použít <xref:System.Windows.Media.Imaging.CroppedBitmap>. V následujícím příkladu je obrázek oříznut pomocí vlastnosti Clip pomocí <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Roztažení obrázků  
 Vlastnost <xref:System.Windows.Controls.Image.Stretch%2A> určuje, jak je obrázek roztažen tak, aby vyplnil jeho kontejner. Vlastnost <xref:System.Windows.Controls.Image.Stretch%2A> přijímá následující hodnoty definované <xref:System.Windows.Media.Stretch> výčtu:  
  
- <xref:System.Windows.Media.Stretch.None>: obrázek není roztažen tak, aby vyplnil výstupní oblast. Pokud je obrázek větší než výstupní oblast, obrázek se vykreslí do výstupní oblasti, na co se nevejde.  
  
- <xref:System.Windows.Media.Stretch.Fill>: obrázek se škáluje tak, aby odpovídal výstupní oblasti. Vzhledem k tomu, že se výška a šířka obrázku nezávisle škálují, nemusí být původní poměr stran obrázku zachovaný. To znamená, že obrázek může být pokřivení, aby bylo možné úplně vyplnit výstupní kontejner.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: obrázek se škáluje tak, aby se zcela vešel do výstupní oblasti. Poměr stran obrázku je zachován.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: obrázek se škáluje tak, že zcela vyplní výstupní oblast a přitom zachovává původní poměr stran obrázku.  
  
 Následující příklad aplikuje všechny dostupné výčty <xref:System.Windows.Media.Stretch> na <xref:System.Windows.Controls.Image>.  
  
 Následující obrázek ukazuje výstup z příkladu a demonstruje vliv různých nastavení <xref:System.Windows.Controls.Image.Stretch%2A> při použití na obrázek.  
  
 ![Různá nastavení funkce TileBrush Stretch](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Různá nastavení Stretch  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Malování s použitím obrázků  
 Obrázky lze také zobrazit v aplikaci vymalováním pomocí <xref:System.Windows.Media.Brush>. Štětce umožňují malovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] objekty s cokoli od jednoduchých, plných barev až po složité sady vzorů a imagí. K malování obrázků použijte <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.ImageBrush> je typ <xref:System.Windows.Media.TileBrush> definující jeho obsah jako rastrový obrázek. <xref:System.Windows.Media.ImageBrush> zobrazí jeden obrázek, který je určen vlastností <xref:System.Windows.Media.ImageBrush.ImageSource%2A>. Můžete ovládat, jak je obrázek roztažen, zarovnán a dlážděn, což vám umožní zabránit zkreslení a vydávat vzory a další efekty. Následující ilustrace znázorňuje některé efekty, které lze dosáhnout pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 ![Příklady výstupů ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Štětce obrázků mohou vyplnit tvary, ovládací prvky, text a další  
  
 Následující příklad ukazuje, jak malovat pozadí tlačítka s obrázkem pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Další informace o <xref:System.Windows.Media.ImageBrush> a malování obrázků najdete v tématu [malování pomocí obrázků, kreseb a vizuálů](painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Metadata image  
 Některé soubory obrázků obsahují metadata, která popisují obsah nebo vlastnosti souboru. Většina digitálních fotoaparátů například vytváří image obsahující metadata o typu a modelu kamery používané k zachycení bitové kopie. Každý formát obrázku zpracovává metadata jinak, ale zobrazovací aplikace WPF poskytuje jednotný způsob ukládání a načítání metadat pro každý podporovaný formát obrázku.  
  
 Přístup k metadatům poskytuje vlastnost <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> objektu <xref:System.Windows.Media.Imaging.BitmapSource>. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> vrátí objekt <xref:System.Windows.Media.Imaging.BitmapMetadata>, který obsahuje všechna metadata obsažená v obrázku. Tato data můžou být v jednom schématu metadat nebo v kombinaci různých schémat. WPF Imaging podporuje následující schémata metadat obrázku: soubor s možností nasazení obrazu (EXIF), tEXt (textová data PNG), adresář souboru obrázku (IFD), mezinárodní klávesová Rada (IPTC) a Extensible Metadata Platform (XMP).  
  
 Pro zjednodušení procesu čtení metadat <xref:System.Windows.Media.Imaging.BitmapMetadata> k dispozici několik pojmenovaných vlastností, které mohou být snadno dostupné, například <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>a <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. Mnohé z těchto pojmenovaných vlastností lze také použít k zápisu metadat. Další podpora pro čtení metadat je poskytována čtečkou dotazů metadat. Metoda <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> slouží k načtení čtečky dotazů metadat zadáním řetězcového dotazu, jako je například *"/app1/EXIF/"* . V následujícím příkladu <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> slouží k získání textu uloženého v umístění *"/text/Description"* .  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 K zápisu metadat se používá zapisovač dotazů metadat. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> získá zapisovač dotazů a nastaví požadovanou hodnotu. V následujícím příkladu se <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> použít k zápisu textu uloženého v umístění *"/text/Description"* .  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Rozšiřitelnost kodeku  
 Základní funkcí programu WPF Imaging je model rozšíření pro nové kodeky obrázků. Tato nespravovaná rozhraní umožňují vývojářům kodeků integrovat kodeky s WPF, takže nové formáty obrázků mohou být automaticky používány aplikacemi WPF.  
  
 Ukázku rozhraní API pro rozšiřitelnost najdete v [ukázkovém kodeku Win32](https://go.microsoft.com/fwlink/?LinkID=160052). Tato ukázka předvádí, jak vytvořit dekodér a kodér pro vlastní formát obrázku.  
  
> [!NOTE]
> Kodek musí být digitálně podepsaný pro systém, aby ho mohl rozpoznat.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Vzorový kodek Win32](https://go.microsoft.com/fwlink/?LinkID=160052)
