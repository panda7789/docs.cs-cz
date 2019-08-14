---
title: Typografie v rozhraní WPF
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 5f3560c899373b9835e2ead79590cf73777b2375
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972408"
---
# <a name="typography-in-wpf"></a>Typografie v rozhraní WPF
V tomto tématu se seznámíte s hlavními typografickou funkcí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nástroje. Mezi tyto funkce patří Vylepšená kvalita a výkon vykreslování textu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] , podpora typografie, vylepšený mezinárodní text, Rozšířená podpora písem a nová textová rozhraní aplikací (API).  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Vylepšená kvalita a výkon textu  
 Text v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je vykreslen pomocí technologie Microsoft ClearType, která vylepšuje přehlednost a čitelnost textu. ClearType je softwarová technologie vyvinutá [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] nástrojem, která vylepšuje čitelnost textu v existujících LCDS (Liquid Crystal displeje), jako jsou obrazovky přenosné počítače, obrazovky Pocket PC a monitorované ploché panely. Technologie ClearType používá vykreslování v pixelech, které umožňuje zobrazení textu s větší věrnou přesností na jeho skutečný tvar zarovnáním znaků na zlomkové části pixelu. Další řešení zvyšuje ostrost drobných podrobností v zobrazení textu, což usnadňuje čtení dlouhých dob trvání. Dalším vylepšením technologie ClearType [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v systému je antialiasing směru y, který vyhlazuje horní a dolní část neomezených křivek v textových znacích. Další podrobnosti o funkcích technologie ClearType najdete v tématu [Přehled technologie ClearType](cleartype-overview.md).  
  
 ![Text pomocí technologie ClearType y-Direction anti-aliasing](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Text pomocí technologie ClearType y-Direction antialiasing  
  
 Celý kanál vykreslování textu může být hardwarově urychlený, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Pokud počítač splňuje minimální požadovanou úroveň hardwaru. Vykreslování, které nelze provést pomocí hardwaru, se vrátí zpět do softwarového vykreslování. Hardwarová akcelerace má vliv na všechny fáze kanálu vykreslování textu – od uložení jednotlivých glyfů, skládání glyfů do glyfů, použití efektů pro aplikování algoritmu prolnutí ClearType na výsledný zobrazený výstup. Další informace o hardwarové akceleraci najdete v tématu [vrstvy vykreslování grafiky](graphics-rendering-tiers.md).  
  
 ![Diagram kanálu vykreslování textu](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Kromě toho animovaný text, bez ohledu na znak nebo glyf, plně využívá schopnost hardwaru grafiky, která je povolená [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nástrojem. Výsledkem je plynulá animace textu.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Bohatá typografie  
 Formát písma je rozšíření [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] formátu písma. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Formát písma byl vyvinut společně pomocí [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] a Adobe a poskytuje bohatou řadu pokročilých typografických funkcí. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Objekt zpřístupňuje mnoho pokročilých [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] funkcí písem, jako jsou stylistické alternativy a ozdobné znaky. <xref:System.Windows.Documents.Typography> Windows SDK poskytuje sadu ukázkových [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] písem, které jsou navrženy s bohatou funkcí, jako jsou například písma Pericles a Pescadero. Další informace najdete v tématu [Ukázková sada písem OpenType](sample-opentype-font-pack.md).  
  
 Písmo Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] obsahuje další glyfy, které představují stylistické alternativy standardní sady glyfů. Následující text zobrazuje stylistické alternativní glyfy.  
  
 ![Text používající stylistické alternativní glyfy písma OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "Text používající stylistické alternativní glyfy písma OpenType")  
  
 Ozdobné znaky jsou ozdobné glyfy, které používají výtvarné ozdoby, které jsou často spojeny s kaligraficky. Následující text zobrazuje standardní a ozdobné glyfy pro písmo Pescadero.  
  
 ![Text používající standardní a ozdobné glyfy OpenType](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "Text používající standardní a ozdobné glyfy OpenType")  
  
 Další informace o [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] funkcích najdete v tématu [funkce písem OpenType](opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>Vylepšená podpora pro mezinárodní text  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje vylepšenou podporu pro mezinárodní text tím, že poskytuje následující funkce:  
  
- Automatické rozestupy ve všech systémech pro psaní pomocí adaptivního měření.  
  
- Široká podpora pro mezinárodní text Další informace naleznete v tématu [globalizace pro WPF](globalization-for-wpf.md).  
  
- Dělení na základě jazyka, dělení a zarovnání řádků s asistencí  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>Rozšířená podpora písem  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje vylepšenou podporu písem tím, že poskytuje následující funkce:  
  
- Kódování Unicode pro veškerý text Chování písem a výběr už nevyžadují znakovou sadu (charset) nebo znakovou stránku.  
  
- Chování písem nezávislá na globálním nastavení, jako je například národní prostředí systému.  
  
- Samostatné <xref:System.Windows.FontWeight>typy <xref:System.Windows.FontStretch>, a<xref:System.Windows.FontStyle>pro definování .<xref:System.Windows.Media.FontFamily> To poskytuje větší flexibilitu než [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] při programování, při které se k definování rodiny písem používají logické kombinace kurzívy a tučného písma.  
  
- Směr zápisu (vodorovně versus svisle) zpracovává nezávisle na názvu písma.  
  
- Propojení písma a Fallback písma v přenosném [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] souboru pomocí technologie kompozitního písma. Složená písma umožňují konstrukci celé škály vícejazyčných písem. Složená písma také poskytují mechanismus, který brání zobrazení chybějících glyfů. Další informace naleznete v tématu poznámky ve <xref:System.Windows.Media.FontFamily> třídě.  
  
- Mezinárodní písma vytvořená ze složených písem pomocí skupiny písem s jedním jazykem. Tím se šetří náklady na prostředky při vývoji písem pro více jazyků.  
  
- Složená písma vložená v dokumentu, což zajišťuje přenositelnost dokumentu. Další informace naleznete v tématu poznámky ve <xref:System.Windows.Media.FontFamily> třídě.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Nová programovací rozhraní pro aplikace v textu (rozhraní API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje několik textových rozhraní API, které můžou vývojáři použít při zahrnutí textu do svých aplikací. Tato rozhraní API se seskupují do tří kategorií:  
  
- **Rozložení a uživatelské rozhraní**. Běžné textové ovládací prvky grafického uživatelského rozhraní (GUI).  
  
- **Zjednodušené vykreslování textu**. Umožňuje kreslit text přímo do objektů.  
  
- **Rozšířené formátování textu**. Umožňuje implementovat vlastní textový modul.  
  
### <a name="layout-and-user-interface"></a>Rozložení a uživatelské rozhraní  
 Na nejvyšší úrovni funkčnosti obsahují rozhraní API [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pro text běžné ovládací prvky <xref:System.Windows.Controls.Label>, jako jsou, <xref:System.Windows.Controls.TextBlock>a. <xref:System.Windows.Controls.TextBox> Tyto ovládací prvky poskytují základní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky v rámci aplikace a nabízejí snadný způsob, jak prezentovat text a pracovat s ním. Ovládací prvky, <xref:System.Windows.Controls.RichTextBox> jako <xref:System.Windows.Controls.PasswordBox> je a povolit pokročilejší nebo specializované zpracování textu. A třídy, jako <xref:System.Windows.Documents.TextRange>jsou <xref:System.Windows.Documents.TextSelection>, a <xref:System.Windows.Documents.TextPointer> umožňují užitečnou manipulaci s textem. Tyto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládací prvky poskytují vlastnosti <xref:System.Windows.Controls.Control.FontFamily%2A>, jako <xref:System.Windows.Controls.Control.FontSize%2A>jsou, <xref:System.Windows.Controls.Control.FontStyle%2A>a, které umožňují řídit písmo, které se používá k vykreslování textu.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Použití bitmapových efektů, transformací a textových efektů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umožňuje vytvořit vizuálně zajímavé používání textu pomocí funkcí, jako jsou rastrové efekty, transformace a textové efekty. Následující příklad ukazuje typický typ efektu Vržený stín aplikovaný na text.  
  
 ![Stín textu s měkkou &#61; 0,25](./media/typography-in-wpf/drop-shadow-text-effect.jpg) 
  
 Následující příklad ukazuje efekt Vržený stín a šum aplikovaný na text.  
  
 ![Stínování textu s hlukem](./media/typography-in-wpf/drop-shadow-noise-text.jpg) 
  
 Následující příklad ukazuje efekt vnější záře aplikovaný na text.  
  
 ![Stín textu s použitím OuterGlowBitmapEffect](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 Následující příklad ukazuje efekt rozostření aplikovaný na text.  
  
 ![Stín textu s použitím BlurBitmapEffect](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 Následující příklad ukazuje druhý řádek textu škálované o 150% podél osy x a třetí řádek textu se škáluje o 150% podél osy y.  
  
 ![Zvětšený text pomocí ScaleTransform](./media/typography-in-wpf/scaled-text-scaletransform.jpg) 
  
 Následující příklad ukazuje text zkosený podél osy x.  
  
 ![Text zkosený pomocí SkewTransform](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 <xref:System.Windows.Media.TextEffect> Objekt je pomocný objekt, který umožňuje považovat text za jednu nebo více skupin znaků v textovém řetězci. Následující příklad ukazuje otočení jednotlivého znaku. Každý znak je otočen nezávisle v intervalu 1 – sekund.  
  
 ![Snímek obrazovky rotujícího textu textového efektu](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>Používání dokumentů Flow  
 Kromě běžných [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků nabízí ovládací prvek rozložení <xref:System.Windows.Documents.FlowDocument> pro textové prezentace – element. Element ve spojení <xref:System.Windows.Controls.DocumentViewer> s elementem poskytuje ovládací prvek pro velké objemy textu s různými požadavky na rozložení. <xref:System.Windows.Documents.FlowDocument> Ovládací prvky rozložení poskytují přístup k pokročilým typografii <xref:System.Windows.Documents.Typography> prostřednictvím objektu a vlastností souvisejících s písmem [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jiných ovládacích prvků.  
  
 Následující příklad ukazuje textový obsah hostovaný v <xref:System.Windows.Controls.FlowDocumentReader>, který poskytuje podporu hledání, navigace, stránkování a škálování obsahu.  
  
 ![Snímek obrazovky, který zobrazuje písma OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Další informace najdete v tématu [dokumenty v WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Zjednodušené vykreslování textu  
 Můžete nakreslit text přímo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů <xref:System.Windows.Media.DrawingContext.DrawText%2A> pomocí metody <xref:System.Windows.Media.DrawingContext> objektu. Chcete-li použít tuto metodu, vytvoříte <xref:System.Windows.Media.FormattedText> objekt. Tento objekt umožňuje nakreslit víceřádkový text, ve kterém je každý znak v textu možné formátovat individuálně. Funkce <xref:System.Windows.Media.FormattedText> objektu obsahuje většinu funkcí příznaků DrawText v rozhraní API systému Windows. Kromě toho <xref:System.Windows.Media.FormattedText> objekt obsahuje funkce, jako je například podpora tří teček, ve kterém se zobrazí tři tečky, když text překročí hranice. Následující příklad ukazuje text, který obsahuje několik formátů, včetně lineárního přechodu na druhý a třetí slova.  
  
 ![Text zobrazený pomocí objektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 Formátovaný text můžete převést na <xref:System.Windows.Media.Geometry> objekty, což vám umožní vytvářet další typy vizuálně zajímavého textu. Můžete například vytvořit <xref:System.Windows.Media.Geometry> objekt na základě obrysu textového řetězce.  
  
 ![Obrys textu s použitím štětce s lineárním přechodem](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Následující příklady ilustrují několik způsobů vytváření zajímavých vizuálních efektů úpravou tahu, výplně a zvýraznění převedeného textu.  
  
 ![Text s různými barvami pro výplň a tah](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Text s obrázkem štětce aplikovaný na tah](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Text s obrázkem štětce aplikovaný na tah a zvýraznění](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Další informace o <xref:System.Windows.Media.FormattedText> objektu naleznete v tématu [Kreslení formátovaného textu](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Upřesněné formátování textu  
 Na nejpokročilejší úrovni textových rozhraní API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí možnost vytvářet vlastní rozložení textu <xref:System.Windows.Media.TextFormatting.TextFormatter> pomocí objektu <xref:System.Windows.Media.TextFormatting> a dalších typů v oboru názvů. Třídy <xref:System.Windows.Media.TextFormatting.TextFormatter> a přidružené umožňují implementovat vlastní rozložení textu, které podporuje vaše vlastní definice formátů znaků, odstavcové styly, pravidla ukončování řádků a další funkce rozložení pro mezinárodní text. V některých případech je vhodné přepsat výchozí implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podpory rozložení textu. Pokud jste však vytvořili ovládací prvek pro úpravu textu nebo aplikaci, můžete vyžadovat odlišnou implementaci, než je výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace.  
  
 Na <xref:System.Windows.Media.TextFormatting.TextFormatter> rozdíl od tradičního textového rozhraní API komunikuje s klientem rozložení textu prostřednictvím sady metod zpětného volání. Vyžaduje, aby klient poskytoval tyto metody v implementaci <xref:System.Windows.Media.TextFormatting.TextSource> třídy. Následující diagram znázorňuje interakci rozložení textu mezi klientskou aplikací a <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta rozložení textu a TextFormatter](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Další informace o vytváření vlastního rozložení textu najdete v tématu [Rozšířené formátování textu](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType – přehled](cleartype-overview.md)
- [Funkce písma OpenType](opentype-font-features.md)
- [Kreslení formátovaného textu](drawing-formatted-text.md)
- [Pokročilé formátování textu](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Microsoft Typography](https://docs.microsoft.com/typography/)
