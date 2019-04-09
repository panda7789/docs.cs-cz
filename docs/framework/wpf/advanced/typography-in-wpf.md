---
title: Typografie v rozhraní WPF
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 0fba0b8814597f58018c4c5feba85082ef035e1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111407"
---
# <a name="typography-in-wpf"></a>Typografie v rozhraní WPF
Toto téma popisuje hlavní funkce typografickém [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tyto funkce patří vylepšení kvality a výkonu při vykreslování textu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Typografie support, rozšířené mezinárodní text, vylepšená podpora písma a rozhraní (API) nové application programming text.  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Zlepšení kvality a výkonu textu  
 Text v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je vykreslen pomocí [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)], která vylepšuje přehlednost a čitelnost textu. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] je software technologie vyvinutá společností [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] , který zlepšuje čitelnost textu na existující monitorů LCD (zobrazí se Liquid Crystal), například Notebook obrazovky, obrazovky v prostředí Pocket PC a monitorování plochý. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] používá vykreslování dílčí pixel, což umožní text zobrazený větší věrně k jeho skutečný tvar znaky zarovnání v jiné části sekundového údaje o jeden pixel. Další řešení zvyšuje ostrost malý podrobnosti zobrazení textu, tím se velmi zjednoduší si přečíst dlouhé doby trvání. Další vylepšení [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je směru osy y vyhlazení, který vyhladí tolní počítače a DNA bez podstruktury křivky v textové znaky. Podrobné informace o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkce, najdete v článku [ClearType – přehled](cleartype-overview.md).  
  
 ![Text s ClearType směru osy y vyhlazení](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Text s ClearType směru osy y vyhlazení  
  
 Kanál vykreslení celý text může být hardwarově urychlené v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] předpokladu, že váš počítač splňuje minimální hardwarové požadavky. Vykreslování, které nelze provést pomocí hardwaru vrátí k softwarové vykreslování. Hardwarovou akceleraci ovlivňuje všechny fáze kanálu vykreslování textu – ukládání jednotlivých glyfy skládání glyfy do šifer, použití efektů, k použití [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] prolnutí algoritmů a poslední zobrazený výstup. Další informace o hardwarovou akceleraci, naleznete v tématu [vrstvy vykreslování grafiky](graphics-rendering-tiers.md).  
  
 ![Diagram kanálu vykreslování textu](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Kromě toho animovaný text podle znaku nebo glyf plně využívá grafiky schopnost hardwaru, kterou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Výsledkem je hladké textové animace.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Bohaté Typografie  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Formát písma je rozšířením [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] formát písma. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Formát písma byla vyvinuta společně za [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] a Adobe a poskytuje bohaté zjistila typografickém pokročilých funkcí. <xref:System.Windows.Documents.Typography> Zpřístupňuje řadu pokročilých funkcí [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] písma, jako je například stylových alternativ a ozdobná písmena. [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] Poskytuje sadu ukázkových [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] písma, které jsou určeny pomocí bohatých funkcí, jako například Pericles a Pescadero písma. Další informace najdete v tématu [Ukázková sada písem OpenType](sample-opentype-font-pack.md).  
  
 Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] písmo obsahuje další glyfy, které poskytují stylových alternativ na standardní sadu glyphs. Zobrazí se následující text stylistické alternativních glyfů.  
  
 ![Textu s použitím stylových alternativních glyfů OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "textu s použitím stylových alternativních glyfů OpenType")  
  
 Ozdobná písmena jsou dekorativní glyfy, které používají propracované dekoru často přidružený Kaligrafie. Následující text zobrazí standardní a swash glyfy Pescadero písma.  
  
 ![Textu použitím piktogramů standard a swash OpenType](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "textu použitím piktogramů standard a swash OpenType")  
  
 Podrobné informace o [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] funkce, najdete v článku [funkce písma OpenType](opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>Podpora rozšířené mezinárodní Text  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje lepší mezinárodní text podporu tím, že poskytuje následující funkce:  
  
-   Automatické-řádkování ve všech systémech zápis pomocí adaptivního měření.  
  
-   Rozsáhlá podpora pro mezinárodní text. Další informace najdete v tématu [globalizace pro WPF](globalization-for-wpf.md).  
  
-   Řádek s asistencí jazykové slov, dělení a zarovnání.  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>Podpora rozšířené písma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje vylepšené písma podporu tím, že poskytuje následující funkce:  
  
-   Kódování Unicode pro veškerý text. Chování písma a výběr už vyžadují znaková sada nebo znakovou stránku.  
  
-   Písmo chování nezávisle na globální nastavení, jako je například národního prostředí.  
  
-   Samostatné <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch>, a <xref:System.Windows.FontStyle> typy pro definování <xref:System.Windows.Media.FontFamily>. To poskytuje větší flexibilitu než [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] programování, ve které datový typ Boolean kombinací tučné písmo a kurzíva se používají k definování rodinu písem.  
  
-   Zápis směr (vodorovně a svisle) zpracovává nezávisle na název písma.  
  
-   Propojování písma a zpětné volání v přenosný [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] soubor, pomocí technologie složený font. Složená písma povolit pro tvorbu plný rozsah vícejazyčné písma. Složená písma taky mělo poskytovat mechanismus, který zabraňuje zobrazování chybějící glyphs. Další informace najdete v části poznámky v <xref:System.Windows.Media.FontFamily> třídy.  
  
-   Mezinárodní písma od složená písma pomocí skupiny písem v jednom jazyce. Toto uloží na nákladech na prostředky při vývoji písma pro různé jazyky.  
  
-   Složená písma vložené v dokumentu, a tím zajištění přenositelnosti dokumentu. Další informace najdete v části poznámky v <xref:System.Windows.Media.FontFamily> třídy.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Nový Text aplikační programovací rozhraní (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje několik text [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] vývojáři mohou použít při vkládání textu ve svých aplikacích. Tyto [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] jsou seskupené do tří kategorií:  
  
-   **Rozložení a uživatelské rozhraní**. Pro ovládací prvky společný text [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)].  
  
-   **Zjednodušené vykreslování textu**. Umožňuje nakreslit text přímo k objektům.  
  
-   **Pokročilé formátování textu**. Umožňuje implementovat modul s vlastním textem.  
  
### <a name="layout-and-user-interface"></a>Rozložení a uživatelského rozhraní  
 Na nejvyšší úrovni funkčnosti, text [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] poskytují běžné [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ovládací prvky jako například <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.TextBox>. Tyto ovládací prvky poskytují základní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementů v rámci aplikace a nabídku snadný způsob, jak zobrazit a pracovat s textem. Ovládací prvky jako například <xref:System.Windows.Controls.RichTextBox> a <xref:System.Windows.Controls.PasswordBox> povolit více advanced nebo specializovaných zpracování textu. A třídy jako <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>, a <xref:System.Windows.Documents.TextPointer> povolit manipulaci s textem užitečné. Tyto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládací prvky, jako poskytují vlastnosti <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, a <xref:System.Windows.Controls.Control.FontStyle%2A>, které vám umožňují řídit písma, která se použije k vykreslení textu.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Pomocí bitmapových efektů, transformace a textových efektů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] můžete vytvořit vizuálně zajímavé používá textu používá funkce, jako je například bitmapových efektů, transformace a textových efektů. Následující příklad ukazuje typické typu efektem stínu použitý pro text.  
  
 ![Stín Softness &#61; 0,25](./media/typography-in-wpf/drop-shadow-text-effect.jpg) 
  
 Následující příklad ukazuje efektem stínu a šumu použitý pro text.  
  
 ![Stín textu s šumu](./media/typography-in-wpf/drop-shadow-noise-text.jpg) 
  
 Následující příklad ukazuje efekt vnější záře použitý pro text.  
  
 ![Stín textu pomocí OuterGlowBitmapEffect](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 Následující příklad ukazuje efekt rozostření použitý pro text.  
  
 ![Pomocí BlurBitmapEffect Stín textu](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 Následující příklad ukazuje, druhý řádek textu měřítkem řídit 150 % podél osy x a třetí řádek textu měřítkem řídit 150 % podél osy y.  
  
 ![Škálování, použití ScaleTransform – text](./media/typography-in-wpf/scaled-text-scaletransform.jpg) 
  
 Následující příklad ukazuje text zkosený podél osy x.  
  
 ![Text zkosený pomocí SkewTransform](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 A <xref:System.Windows.Media.TextEffect> objekt je objekt pomocné rutiny, která umožňuje zpracovávat text jako jeden nebo více skupin znaků v textovém řetězci. Následující příklad ukazuje jednotlivý znak se otočí. Každý znak v intervalech 1 sekundu otočena nezávisle na sobě.  
  
 ![Snímek obrazovky efekt textu otáčení textu](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>Použití toku dokumentů  
 Kromě společné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládací prvky, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí rozložení ovládacího prvku pro textové prezentaci – <xref:System.Windows.Documents.FlowDocument> elementu. <xref:System.Windows.Documents.FlowDocument> Element ve spojení s <xref:System.Windows.Controls.DocumentViewer> element, obsahuje ovládací prvek pro velkého množství textu s použitím různých požadavkům na rozložení. Rozložení ovládacích prvků poskytují přístup k rozšířené Typografie prostřednictvím <xref:System.Windows.Documents.Typography> objektu a vlastnosti související se písmo jiných [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládacích prvků.  
  
 Následující příklad ukazuje, textového obsahu konání <xref:System.Windows.Controls.FlowDocumentReader>, poskytující vyhledávání, navigace, stránkování a obsah škálování podpory.  
  
 ![Snímek obrazovky zobrazující písem OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Další informace najdete v tématu [dokumenty v platformě WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Kreslení jednoduchý Text  
 Text lze nakreslit přímo na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů pomocí <xref:System.Windows.Media.DrawingContext.DrawText%2A> metodu <xref:System.Windows.Media.DrawingContext> objektu. Chcete-li použít tuto metodu, vytvoříte <xref:System.Windows.Media.FormattedText> objektu. Tento objekt umožňuje nakreslit více řádky textu, ve kterém každý znak v textu jednotlivě naformátovaná. Funkce <xref:System.Windows.Media.FormattedText> objekt obsahuje většinu funkcí příznaky DrawText v rozhraní Windows API. Kromě toho <xref:System.Windows.Media.FormattedText> objekt obsahuje funkce, jako je například podpora tlačítko se třemi tečkami, ve kterém se třemi tečkami zobrazí, když text překročí jeho hranice. Následující příklad ukazuje, text, který má několik formátování, včetně lineárního přechodu na druhý a třetí slova.  
  
 ![Text zobrazený pomocí objektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 Můžete převést formátovaný text do <xref:System.Windows.Media.Geometry> objekty, které umožňuje vytvoření jiných typů vizuálně zajímavou text. Například můžete vytvořit <xref:System.Windows.Media.Geometry> objektu podle obrysu textového řetězce.  
  
 ![Text osnovy pomocí štětec lineárního přechodu](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Následující příklady znázorňují několik možností, jak vytvářet zajímavé vizuální efekty úpravou stroke, výplň a zvýraznit text převedený.  
  
 ![Text mají různé barvy výplně a tahu](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Text použitý pro stroke obrázkový štětec](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Text s použita k obtažení a zvýraznit obrázkový štětec](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Další informace o <xref:System.Windows.Media.FormattedText> objektu, najdete v článku [kreslení textu ve formátu](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Upřesněné formátování textu  
 Nanejvýš pokročilé úrovni členství textu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí možnost vytvořit vlastní text rozložení pomocí <xref:System.Windows.Media.TextFormatting.TextFormatter> objektu a další typy v <xref:System.Windows.Media.TextFormatting> oboru názvů. <xref:System.Windows.Media.TextFormatting.TextFormatter> a přidružených tříd povolit další rozložení funkcí pro mezinárodní text a můžete implementovat vlastní text rozložení, který podporuje vlastní definice formátování, styly odstavec pravidel ukončování řádků. Velmi málo případech, ve kterých chcete přepsat výchozí implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podpora rozložení textu. Ale při vytváření ovládacího prvku nebo aplikace pro úpravy textu, můžete vyžadovat jinou implementaci než výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace.  
  
 Na rozdíl od tradičních text [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], <xref:System.Windows.Media.TextFormatting.TextFormatter> komunikuje přes sadu metod zpětného volání klienta rozložení textu. Vyžaduje od klienta tyto metody v implementaci <xref:System.Windows.Media.TextFormatting.TextSource> třídy. Následující diagram znázorňuje interakci rozložení textu mezi klientskou aplikací a <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta rozložení textu a objektu TextFormatter](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Další informace o vytváření rozložení vlastního textu, naleznete v tématu [pokročilé formátování textu](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType – přehled](cleartype-overview.md)
- [Funkce písma OpenType](opentype-font-features.md)
- [Kreslení formátovaného textu](drawing-formatted-text.md)
- [Upřesněné formátování textu](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Microsoft Typography](https://docs.microsoft.com/typography/)
