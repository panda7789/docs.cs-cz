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
ms.openlocfilehash: 3365c35e3e7b7fe5c0be48a65d7a14da0882c90e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186696"
---
# <a name="imaging-overview"></a>Přehled obrázků
Toto téma obsahuje úvod do součásti Microsoft Windows Presentation Foundation Imaging Component. WPF Imaging umožňuje vývojářům zobrazovat, transformovat a formátovat obrázky.  

## <a name="wpf-imaging-component"></a>Zobrazovací komponenta WPF  
 WPF Imaging poskytuje významná vylepšení v oblasti možností zpracování obrázků v systému Microsoft Windows. Funkce pro vytváření obrázků, například zobrazení bitmapy nebo použití bitmapy na společném ovládacím prvku, byly dříve závislé na knihovnách GDI (Microsoft Windows Graphics Device Interface) nebo Microsoft Windows GDI+. Tato rozhraní API poskytují základní funkce zobrazování, ale chybí funkce, jako je například podpora rozšiřitelnosti kodeku a podpora obrázků s vysokou věrností. WPF Imaging je navržen tak, aby překonal nedostatky GDI a GDI+ a poskytl novou sadu rozhraní API pro zobrazení a použití obrázků ve vašich aplikacích.  
  
 Existují dva způsoby přístupu k rozhraní WPF Imaging API, spravované součásti a nespravované součásti. Nespravovaná součást poskytuje následující funkce.  
  
- Model rozšiřitelnosti pro nové nebo proprietární obrazové formáty.  
  
- Vyšší výkon a zabezpečení na nativních formátů obrázků, včetně bitmapy (BMP), Joint Photographics Experts Group (JPEG), Portable Network Graphics (PNG), Tagged Image File Format (TIFF), Microsoft Windows Media Photo, Graphics Interchange Format (GIF), a ikonu (.ico).  
  
- Zachování obrazových dat s vysokou bitovou hloubkou až 8 bitů na kanál (32 bitů na pixel).  
  
- Nedestruktivní změna velikosti obrazu, oříznutí a otočení.  
  
- Zjednodušená správa barev.  
  
- Podpora pro in-file, proprietární metadata.  
  
- Spravovaná komponenta využívá nespravovanou infrastrukturu k zajištění [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]bezproblémové integrace bitových kopií s dalšími funkcemi WPF, jako je animace a grafika. Spravovaná komponenta také využívá model rozšiřitelnosti kodeku WPF (Windows Presentation Foundation) (Windows Presentation Foundation), který umožňuje automatické rozpoznávání nových formátů obrázků v aplikacích WPF.  
  
 Většina spravovaného rozhraní WPF Imaging API <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> se nachází v oboru názvů, i když v oboru názvů je uloženo několik důležitých typů, například <xref:System.Windows.Media.ImageBrush> a <xref:System.Windows.Media.ImageDrawing> je umístěno v oboru <xref:System.Windows.Media?displayProperty=nameWithType> názvů a <xref:System.Windows.Controls.Image> je umístěno v oboru <xref:System.Windows.Controls?displayProperty=nameWithType> názvů.  
  
 Toto téma obsahuje další informace o spravované součásti. Další informace o nespravovaném rozhraní API naleznete v dokumentaci [k nespravované součásti WPF Imaging Component.](/windows/desktop/wic/-wic-lh)  
  
<a name="_imageformats"></a>
## <a name="wpf-image-formats"></a>Formáty obrázků WPF  

 Kodek se používá k dekódování nebo kódování určitého formátu média. WPF Imaging obsahuje kodek pro formáty obrázků BMP, JPEG, PNG, TIFF, Windows Media Photo, GIF a ICON. Každý z těchto kodeků umožňuje aplikacím dekódovat a, s výjimkou ICON, kódovat své příslušné formáty obrázků.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>je důležitá třída používaná při dekódování a kódování obrazů. Jedná se o základní stavební blok kanálu WPF Imaging a představuje jednu konstantní sadu pixelů v určité velikosti a rozlišení. A <xref:System.Windows.Media.Imaging.BitmapSource> může být jednotlivý snímek obrazu s více snímky nebo může být <xref:System.Windows.Media.Imaging.BitmapSource>výsledkem transformace provedené na . Je nadřazenou částí mnoha primárních tříd <xref:System.Windows.Media.Imaging.BitmapFrame>používaných při zobrazování WPF, například .  
  
 A <xref:System.Windows.Media.Imaging.BitmapFrame> se používá k ukládání skutečných bitmapových dat ve formátu obrazu. Mnoho formátů obrázků podporuje <xref:System.Windows.Media.Imaging.BitmapFrame>pouze jeden , i když formáty jako GIF a TIFF podporují více snímků na obrázek. Rámce jsou používány dekodéry jako vstupní data a jsou předávány kodéry k vytvoření obrazových souborů.  
  
 Následující příklad ukazuje, <xref:System.Windows.Media.Imaging.BitmapFrame> jak je <xref:System.Windows.Media.Imaging.BitmapSource> vytvořen a a pak přidán do bitové kopie TIFF.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Dekódování formátu obrázku  
 Dekódování obrazu je překlad formátu obrazu do obrazových dat, které může systém použít. Obrazová data pak lze použít k zobrazení, zpracování nebo kódování do jiného formátu. Výběr dekodéru je založen na formátu obrazu. Výběr kodeku je automatický, pokud není zadán konkrétní dekodér. Příklady v části [Zobrazení obrázků v wpf](#_displayingimages) ukazují automatické dekódování. Vlastní formát dekodéry vyvinuté pomocí nespravovaných wpf imaging rozhraní a registrované v systému se automaticky účastní výběru dekodéru. To umožňuje automatické zobrazení vlastních formátů v aplikacích WPF.  
  
 Následující příklad ukazuje použití bitmapového dekodéru k dekódování obrazu ve formátu BMP.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Kódování formátu obrazu  
 Kódování obrazu je překlad obrazových dat do určitého formátu obrazu. Kódovaná obrazová data pak mohou být použita k vytvoření nových obrazových souborů. WPF Imaging poskytuje kodéry pro každý z výše popsaných obrazových formátů.  
  
 Následující příklad ukazuje použití kodéru k uložení nově vytvořeného bitmapového obrazu.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>
## <a name="displaying-images-in-wpf"></a>Zobrazení obrázků ve WPF  
 Existuje několik způsobů, jak zobrazit obrázek v aplikaci WPF (Windows Presentation Foundation). Obrázky lze zobrazit <xref:System.Windows.Controls.Image> pomocí ovládacího prvku, <xref:System.Windows.Media.ImageBrush>namalovat na <xref:System.Windows.Media.ImageDrawing>vizuál pomocí , nebo nakreslené pomocí .  
  
### <a name="using-the-image-control"></a>Použití ovládacího prvku obraz  
 <xref:System.Windows.Controls.Image>je prvek architektury a primární způsob zobrazení obrázků v aplikacích. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Image> , lze použít dvěma způsoby; syntaxe atributu nebo syntaxe vlastnosti. Následující příklad ukazuje, jak vykreslit obrázek o šířce 200 pixelů pomocí syntaxe atributu i syntaxe značky vlastnosti. Další informace o syntaxi atributů a syntaxi vlastností naleznete v [tématu Přehled vlastností závislostí](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Mnoho příkladů používá <xref:System.Windows.Media.Imaging.BitmapImage> objekt k odkazu na soubor obrázku. <xref:System.Windows.Media.Imaging.BitmapImage>je <xref:System.Windows.Media.Imaging.BitmapSource> specialita, která [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] je optimalizována pro načítání a <xref:System.Windows.Controls.Image.Source%2A> je <xref:System.Windows.Controls.Image> snadný způsob, jak zobrazit obrázky jako ovládacíprvek.  
  
 Následující příklad ukazuje, jak vykreslit obrázek 200 pixelů široký pomocí kódu.  
  
> [!NOTE]
> <xref:System.Windows.Media.Imaging.BitmapImage>implementuje <xref:System.ComponentModel.ISupportInitialize> rozhraní pro optimalizaci inicializace na více vlastností. Ke změnám vlastností může dojít pouze během inicializace objektu. Volání <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> signalizovat, že inicializace byla zahájena a <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> signál, že inicializace byla dokončena. Po inicializace jsou změny vlastností ignorovány.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Otáčení, převod a oříznutí obrazů  
 WPF umožňuje uživatelům transformovat obrázky <xref:System.Windows.Media.Imaging.BitmapImage> pomocí vlastností nebo pomocí dalších <xref:System.Windows.Media.Imaging.BitmapSource> objektů, jako <xref:System.Windows.Media.Imaging.CroppedBitmap> je například nebo <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Tyto transformace obrazu mohou změnit velikost nebo otočit obraz, změnit formát obrazových bodů obrazu nebo oříznout obraz.  
  
 Otočení obrazu se provádí <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> pomocí <xref:System.Windows.Media.Imaging.BitmapImage>vlastnosti . Rotace lze provést pouze v krocích po 90 stupních. V následujícím příkladu je obraz otočen o 90 stupňů.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Převod obrazu do jiného formátu obrazových bodů, <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>například ve stupních šedi, se provádí pomocí . V následujících příkladech je obrázek <xref:System.Windows.Media.PixelFormats.Gray4%2A>převeden na .  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Chcete-li obrázek <xref:System.Windows.UIElement.Clip%2A> oříznout, lze použít vlastnost <xref:System.Windows.Controls.Image> nebo <xref:System.Windows.Media.Imaging.CroppedBitmap> její použití. Obvykle, pokud chcete zobrazit pouze část obrázku, <xref:System.Windows.UIElement.Clip%2A> by měl být použit. Pokud potřebujete zakódovat a uložit oříznutý <xref:System.Windows.Media.Imaging.CroppedBitmap> obrázek, měl by být použit. V následujícím příkladu je obrázek oříznut pomocí <xref:System.Windows.Media.EllipseGeometry>vlastnosti Clip pomocí .  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Roztažení obrazů  
 Vlastnost <xref:System.Windows.Controls.Image.Stretch%2A> určuje, jak je obrázek roztažen tak, aby vyplnil svůj kontejner. Vlastnost <xref:System.Windows.Controls.Image.Stretch%2A> přijímá následující hodnoty definované výčtu: <xref:System.Windows.Media.Stretch>  
  
- <xref:System.Windows.Media.Stretch.None>: Obraz není roztažený, aby vyplnil výstupní oblast. Pokud je obraz větší než výstupní oblast, je obraz nakreslen do výstupní oblasti a ořízne to, co se nevejde.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Měřítko obrazu se přizpůsobí výstupní oblasti. Vzhledem k tomu, že se měřítko a šířka obrazu mění nezávisle, nemusí být zachován původní poměr stran obrazu. To znamená, že obraz může být pokřivený, aby bylo možné zcela vyplnit výstupní kontejner.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Měřítko obrazu se změní tak, aby se zcela vešel do výstupní oblasti. Poměr stran obrázku je zachován.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Měřítko obrazu se změní tak, aby zcela vyplnil výstupní oblast při zachování původního poměru stran obrazu.  
  
 Následující příklad použije každý z <xref:System.Windows.Media.Stretch> dostupných výčtů na <xref:System.Windows.Controls.Image>.  
  
 Následující obrázek znázorňuje výstup z příkladu <xref:System.Windows.Controls.Image.Stretch%2A> a ukazuje vliv různých nastavení při použití na obrázek.  
  
 ![Různá nastavení roztažení tilebrush](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Různá nastavení roztažení  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Malování obrazy  
 Obrázky lze také zobrazit v aplikaci <xref:System.Windows.Media.Brush>malováním pomocí . Stopy umožňují malovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] objekty s čímkoli od jednoduchých plných barev až po složité sady vzorků a obrazů. Chcete-li malovat obrazy, použijte . <xref:System.Windows.Media.ImageBrush> A <xref:System.Windows.Media.ImageBrush> je <xref:System.Windows.Media.TileBrush> typ, který definuje jeho obsah jako bitmapový obraz. Zobrazí <xref:System.Windows.Media.ImageBrush> jeden obrázek, který je <xref:System.Windows.Media.ImageBrush.ImageSource%2A> určen jeho vlastnost. Můžete určit, jak bude obraz roztažen, zarovnán a s kachlová, což vám umožní zabránit zkreslení a vytvářet vzorky a další efekty. Následující obrázek znázorňuje některé efekty, kterých lze dosáhnout pomocí <xref:System.Windows.Media.ImageBrush>aplikace .  
  
 ![Příklady výstupu ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Obrazové stopy mohou vyplňovat tvary, ovládací prvky, text a další  
  
 Následující příklad ukazuje, jak malovat pozadí tlačítka s obrazem <xref:System.Windows.Media.ImageBrush>pomocí .  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Další informace <xref:System.Windows.Media.ImageBrush> o obrazech a malování obrázků naleznete [v tématu Malování obrázky, kresby a vizuály](painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>
## <a name="image-metadata"></a>Metadata obrázku  
 Některé obrazové soubory obsahují metadata, která popisují obsah nebo charakteristiky souboru. Většina digitálních fotoaparátů například vytváří obrázky, které obsahují metadata o výrobě a modelu fotoaparátu použitého k zachycení obrazu. Každý formát obrázku zpracovává metadata jinak, ale WPF Imaging poskytuje jednotný způsob ukládání a načítání metadat pro každý podporovaný formát obrazu.  
  
 Přístup k metadatům je <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> poskytován prostřednictvím vlastnosti objektu. <xref:System.Windows.Media.Imaging.BitmapSource> <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>vrátí <xref:System.Windows.Media.Imaging.BitmapMetadata> objekt, který obsahuje všechna metadata obsažená v obraze. Tato data mohou být v jednom schématu metadat nebo v kombinaci různých schémat. WPF Imaging podporuje následující schémata metadat obrázků: Exchangeable image file (Exif), tEXt (PNG Textal Data), image file directory (IFD), International Press Telecommunications Council (IPTC) a Extensible Metadata Platform (XMP).  
  
 Za účelem zjednodušení procesu čtení <xref:System.Windows.Media.Imaging.BitmapMetadata> metadat poskytuje několik pojmenovaných vlastností, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>ke <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>kterým lze snadno přistupovat, například <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, , a . Mnoho z těchto pojmenovaných vlastností lze také použít k zápisu metadat. Další podporu pro čtení metadat poskytuje čtečka dotazů metadat. Metoda <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> se používá k načtení čtečky dotazů metadat poskytnutím dotazu řetězce, například *"/app1/exif/"*. V následujícím příkladu <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> se používá k získání textu uloženého v umístění *"/Text/Description".*  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Pro zápis metadat se používá zapisovač dotazu metadat. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>získá zapisovač dotazu a nastaví požadovanou hodnotu. V následujícím příkladu <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> se používá k zápisu textu uloženého v umístění *"/Text/Description".*  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>
## <a name="codec-extensibility"></a>Rozpustnost kodeku  
 Základním rysem WPF Imaging je model rozšiřitelnosti pro nové kodeky obrazu. Tato nespravovaná rozhraní umožňují vývojářům kodeků integrovat kodeky s WPF, takže nové formáty obrázků mohou být automaticky používány aplikacemi WPF.  
  
 Ukázku rozhraní API pro rozšiřitelnost naleznete v [ukázkovém kodeku Win32](https://go.microsoft.com/fwlink/?LinkID=160052). Tato ukázka ukazuje, jak vytvořit dekodér a kodér pro vlastní formát obrazu.  
  
> [!NOTE]
> Kodek musí být digitálně podepsán, aby jej systém rozpoznal.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Ukázkový kodek Win32](https://go.microsoft.com/fwlink/?LinkID=160052)
