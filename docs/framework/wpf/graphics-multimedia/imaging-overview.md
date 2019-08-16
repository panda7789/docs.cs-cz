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
ms.openlocfilehash: 6d3dce5c8a34257f8509f239ece4bae3efa02b84
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545376"
---
# <a name="imaging-overview"></a>Přehled obrázků
Toto téma poskytuje Úvod do [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]umožňuje vývojářům zobrazovat, transformovat a formátovat obrázky.  

## <a name="wpf-imaging-component"></a>Komponenta WPF Imaging  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]poskytuje významná vylepšení funkcí [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]pro vytváření bitových kopií v nástroji. Možnosti imagí, jako je zobrazení rastrového obrázku nebo použití obrázku na běžném ovládacím prvku, byly dřív závislé na knihovnách Microsoft Windows GDI (GDI) nebo Microsoft Windows GDI+. Tato rozhraní API poskytují základní funkce pro zpracování obrazu, ale chybí funkce, jako je podpora rozšiřitelnosti kodeku a podpora obrázků s vysokou kvalitou. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]je navržený tak, aby překonal nedostatky GDI a GDI+ a poskytoval novou sadu rozhraní API pro zobrazení a používání imagí v rámci aplikací.  
  
 Existují dva způsoby, jak získat přístup [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] k rozhraní API, spravované komponentě a nespravované součásti. Nespravované komponenty poskytují následující funkce.  
  
- Model rozšiřitelnosti pro nové nebo speciální formáty obrázků.  
  
- Vylepšený výkon a zabezpečení v nativních formátech obrázků, včetně rastrového obrázku (BMP), společného fotografického skupiny (JPEG), přenosného [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)]síťového [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)]grafického objektu (PNG), formátu GIF (Graphics Interchange Format) a ikony (. ico).  
  
- Uchovávání dat bitové kopie s vysokou bitovou hloubkou až na 8 bitů na kanál (32 bitů na pixel).  
  
- Nedestruktivní škálování obrazu, ořezávání a rotace.  
  
- Zjednodušená správa barev.  
  
- Podpora pro osobní metadata v souboru.  
  
- Spravovaná komponenta využívá nespravovanou infrastrukturu k zajištění bezproblémové integrace imagí s dalšími [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] funkcemi [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], jako je například animace a grafika. Spravovaná komponenta také přináší výhody modelu rozšiřitelnosti kodeku Windows Presentation Foundation (WPF), která umožňuje automatické rozpoznávání nových formátů obrázků v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacích.  
  
 Většina spravovaného [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] rozhraní API se nachází <xref:System.Windows.Media?displayProperty=nameWithType> <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.ImageDrawing> <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> v oboru názvů, i když několik důležitých typů, jako je například a je umístěn v oboru názvů <xref:System.Windows.Controls.Image> a je umístěno v <xref:System.Windows.Controls?displayProperty=nameWithType> hosting.  
  
 V tomto tématu najdete další informace o spravované komponentě. Další informace o nespravovaném rozhraní API najdete v dokumentaci ke komponentě nespravovaného [zpracování WPF](/windows/desktop/wic/-wic-lh) .  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>Formáty obrázků WPF  
 Kodek slouží k dekódování nebo kódování konkrétního formátu média. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]obsahuje kodek pro formáty obrázků BMP, JPEG, PNG [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)], [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)], GIF a Icon. Každý z těchto kodeků umožňuje aplikacím dekódovat a s výjimkou ikony zakódovat příslušné formáty obrázků.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>je důležitou třídou použitou při dekódování a kódování imagí. Je to základní stavební blok [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] kanálu a představuje jednu konstantní sadu pixelů v určité velikosti a rozlišení. Může to být individuální rámec obrázku s více snímky, nebo může být výsledkem transformace provedené <xref:System.Windows.Media.Imaging.BitmapSource>na. <xref:System.Windows.Media.Imaging.BitmapSource> Je nadřazeným prvkem mnoha primárních tříd používaných v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rámci imagí, jako je například. <xref:System.Windows.Media.Imaging.BitmapFrame>  
  
 <xref:System.Windows.Media.Imaging.BitmapFrame> Slouží k uložení skutečných dat bitmapy formátu obrázku. Mnoho formátů obrázků podporuje pouze jeden <xref:System.Windows.Media.Imaging.BitmapFrame>, i když formáty jako formát GIF a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] podporují více snímků na obrázek. Tyto rámce jsou používány dekodéry jako vstupní data a jsou předávány kodérům pro vytváření souborů imagí.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Media.Imaging.BitmapFrame> je vytvořen <xref:System.Windows.Media.Imaging.BitmapSource> z [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] a poté přidán do obrázku.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Dekódování formátu obrázku  
 Dekódování obrázku je převod formátu obrázku na data obrázku, který může být použit systémem. Data obrázku pak můžete použít k zobrazení, zpracování nebo kódování v jiném formátu. Výběr dekodéru je založen na formátu obrázku. Výběr kodeku je automatický, pokud se nezadá konkrétní dekodér. Příklady v části [zobrazení obrázků v](#_displayingimages) subsystému WPF ukazují automatické dekódování. Vlastní dekodéry formátu vyvinuté pomocí nespravovaných [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] rozhraní a zaregistrovaných v systému se automaticky účastní výběru dekodéru. To umožňuje, aby se vlastní formáty zobrazovaly [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automaticky v aplikacích.  
  
 Následující příklad demonstruje použití dekodéru rastrového obrázku k dekódování obrázku formátu BMP.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Kódování formátu obrázku  
 Kódování obrázku je převod dat obrázku do konkrétního formátu obrázku. Data kódované image pak můžete použít k vytvoření nových souborů imagí. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]poskytuje kodér pro každý z formátů obrázků popsaných výše.  
  
 Následující příklad ukazuje použití kodéru k uložení nově vytvořeného rastrového obrázku.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>Zobrazení obrázků v subsystému WPF  
 Existuje několik způsobů, jak zobrazit obrázek v aplikaci Windows Presentation Foundation (WPF). Obrázky lze zobrazit pomocí <xref:System.Windows.Controls.Image> ovládacího prvku, vykresleného v vizuálu <xref:System.Windows.Media.ImageBrush>pomocí nebo vykresleného pomocí <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Použití ovládacího prvku obrázek  
 <xref:System.Windows.Controls.Image>je prvkem architektury a hlavním způsobem zobrazení obrázků v aplikacích. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ,<xref:System.Windows.Controls.Image> lze použít dvěma způsoby, syntaxí atributu nebo vlastností. Následující příklad ukazuje, jak vykreslit obrázek 200 pixelů na šířku pomocí syntaxe atributů i syntaxe značek vlastností. Další informace o syntaxi atributů a syntaxi vlastností najdete v tématu [Přehled vlastností závislosti](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Mnohé z příkladů používají <xref:System.Windows.Media.Imaging.BitmapImage> objekt pro odkazování na soubor obrázku. <xref:System.Windows.Media.Imaging.BitmapImage>je specializovaný <xref:System.Windows.Media.Imaging.BitmapSource> , který je optimalizován pro [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] načítání a představuje snadný způsob zobrazení <xref:System.Windows.Controls.Image> obrázků jako <xref:System.Windows.Controls.Image.Source%2A> ovládacího prvku.  
  
 Následující příklad ukazuje, jak vykreslit obrázek 200 pixelů v širším formátu pomocí kódu.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage><xref:System.ComponentModel.ISupportInitialize> implementuje rozhraní pro optimalizaci inicializace u více vlastností. Změny vlastností mohou nastat pouze při inicializaci objektu. Volání <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> signalizace, že inicializace začala a <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> signalizuje, že inicializace byla dokončena. Po inicializaci jsou změny vlastností ignorovány.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Otáčení, převádění a ořezávání imagí  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]umožňuje uživatelům transformovat <xref:System.Windows.Media.Imaging.BitmapImage> obrázky pomocí vlastností nebo pomocí dalších <xref:System.Windows.Media.Imaging.BitmapSource> objektů, například <xref:System.Windows.Media.Imaging.CroppedBitmap> nebo <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Tyto transformace obrázků mohou škálovat nebo otáčet obrázek, měnit formát pixelu obrázku nebo oříznout obrázek.  
  
 Rotace obrázků se provádí pomocí <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> <xref:System.Windows.Media.Imaging.BitmapImage>vlastnosti. Rotace se dají provádět jenom v přírůstcích po 90 stupních. V následujícím příkladu je obrázek otočen 90 stupňů.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Převod obrázku na jiný formát pixelu, například ve stupních šedi, <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>se provádí pomocí. V následujících příkladech je obrázek převeden na <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Chcete-li oříznout obrázek, buď <xref:System.Windows.UIElement.Clip%2A> <xref:System.Windows.Controls.Image> vlastnost nebo <xref:System.Windows.Media.Imaging.CroppedBitmap> lze použít. Obvykle, pokud chcete pouze zobrazit část obrázku, <xref:System.Windows.UIElement.Clip%2A> je vhodné použít. Pokud potřebujete zakódovat a uložit oříznutý obraz, <xref:System.Windows.Media.Imaging.CroppedBitmap> měl by se použít. V následujícím příkladu je obrázek oříznut pomocí vlastnosti Clip pomocí <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Roztažení obrázků  
 <xref:System.Windows.Controls.Image.Stretch%2A> Vlastnost určuje, jak je obrázek roztažen tak, aby vyplnil jeho kontejner. Vlastnost přijímá následující hodnoty definované <xref:System.Windows.Media.Stretch> výčtem: <xref:System.Windows.Controls.Image.Stretch%2A>  
  
- <xref:System.Windows.Media.Stretch.None>: Obrázek není roztažen tak, aby vyplnil výstupní oblast. Pokud je obrázek větší než výstupní oblast, obrázek se vykreslí do výstupní oblasti, na co se nevejde.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Obrázek se škáluje tak, aby odpovídal výstupní oblasti. Vzhledem k tomu, že se výška a šířka obrázku nezávisle škálují, nemusí být původní poměr stran obrázku zachovaný. To znamená, že obrázek může být pokřivení, aby bylo možné úplně vyplnit výstupní kontejner.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Obrázek se škáluje tak, aby se zcela vešel do výstupní oblasti. Poměr stran obrázku je zachován.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Obrázek se škáluje tak, že zcela vyplní výstupní oblast a přitom zachovává původní poměr stran obrázku.  
  
 Následující příklad aplikuje všechny dostupné <xref:System.Windows.Media.Stretch> výčty <xref:System.Windows.Controls.Image>na.  
  
 Následující obrázek ukazuje výstup z příkladu a ukazuje, jak má vliv na různá <xref:System.Windows.Controls.Image.Stretch%2A> nastavení při použití na obrázek.  
  
 ![Různá nastavení funkce TileBrush Stretch](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Různá nastavení Stretch  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Malování s použitím obrázků  
 Obrázky lze také zobrazit v aplikaci vymalováním pomocí <xref:System.Windows.Media.Brush>. Štětce umožňují malovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] objekty s cokoli od jednoduchých, plných barev až po složité sady vzorů a imagí. K malování obrázků použijte <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.ImageBrush> Je<xref:System.Windows.Media.TileBrush> typ, který definuje jeho obsah jako rastrový obrázek. Zobrazí jeden obrázek, který je určen <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastností. <xref:System.Windows.Media.ImageBrush> Můžete ovládat, jak je obrázek roztažen, zarovnán a dlážděn, což vám umožní zabránit zkreslení a vydávat vzory a další efekty. Následující ilustrace znázorňuje některé efekty, které lze dosáhnout pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 ![Příklady výstupů ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Štětce obrázků mohou vyplnit tvary, ovládací prvky, text a další  
  
 Následující příklad ukazuje, jak malovat pozadí tlačítka s obrázkem pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Další informace o <xref:System.Windows.Media.ImageBrush> obrázcích a malování obrázků najdete v tématu [malování obrázků, kreseb a vizuálů](painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Metadata image  
 Některé soubory obrázků obsahují metadata, která popisují obsah nebo vlastnosti souboru. Většina digitálních fotoaparátů například vytváří image obsahující metadata o typu a modelu kamery používané k zachycení bitové kopie. Každý formát obrázku zpracovává metadata jinak, [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] ale poskytuje jednotný způsob ukládání a načítání metadat pro každý podporovaný formát obrázku.  
  
 Přístup k metadatům se poskytuje prostřednictvím <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> vlastnosti <xref:System.Windows.Media.Imaging.BitmapSource> objektu. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A><xref:System.Windows.Media.Imaging.BitmapMetadata> vrátí objekt, který obsahuje všechna metadata obsažená v obrázku. Tato data můžou být v jednom schématu metadat nebo v kombinaci různých schémat. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]podporuje následující schémata metadat obrázků: Soubor s daty (EXIF), tEXt (PNG tEXt), adresář souboru obrázku (IFD), Mezinárodní rada pro každou klávesovou zkratku (IPTC) [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)]a.  
  
 Aby bylo možné zjednodušit proces čtení <xref:System.Windows.Media.Imaging.BitmapMetadata> metadat, poskytuje několik pojmenovaných vlastností, které mohou být snadno dostupné, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A> <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>například, <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>a. Mnohé z těchto pojmenovaných vlastností lze také použít k zápisu metadat. Další podpora pro čtení metadat je poskytována čtečkou dotazů metadat. Metoda se používá k načtení čtečky dotazů metadat zadáním řetězcového dotazu, jako je například *"/app1/EXIF/".* <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> V následujícím příkladu <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> se používá k získání textu uloženého v umístění *"/text/Description"* .  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 K zápisu metadat se používá zapisovač dotazů metadat. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>Získá zapisovač dotazů a nastaví požadovanou hodnotu. V následujícím příkladu <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> se používá k zápisu textu uloženého v umístění *"/text/Description"* .  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Rozšiřitelnost kodeku  
 Základní funkcí [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] nástroje je model rozšíření pro nové kodeky obrázků. Tato nespravovaná rozhraní umožňují vývojářům kodeků [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integrovat kodeky, takže nové formáty obrázků [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mohou být automaticky používány aplikacemi.  
  
 Ukázku rozhraní API pro rozšiřitelnost najdete v ukázkovém [kodeku Win32](https://go.microsoft.com/fwlink/?LinkID=160052). Tato ukázka předvádí, jak vytvořit dekodér a kodér pro vlastní formát obrázku.  
  
> [!NOTE]
>  Kodek musí být digitálně podepsaný pro systém, aby ho mohl rozpoznat.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Vzorový kodek Win32](https://go.microsoft.com/fwlink/?LinkID=160052)
