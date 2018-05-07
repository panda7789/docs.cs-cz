---
title: Typografie v rozhraní WPF
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 45f74a4dd2164f332314ad79a18eab49efb520d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="typography-in-wpf"></a>Typografie v rozhraní WPF
Toto téma představuje hlavní typografických funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tyto funkce patří zlepšení kvality a výkon při vykreslování textu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] typografii podporu rozšířené mezinárodní text, rozšířenou podporu písma a nové aplikace programování text rozhraní (API).  
  

  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Zlepšení kvality a výkonu textu  
 Text v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je vykreslen pomocí [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)], což zlepšuje přehlednost a čitelnost textu. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] je technologie softwaru vyvinuté [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] která zlepšuje čitelnost textu na existující monitorů LCD (zobrazí se Crystal kapaliny), například přenosný počítač obrazovky, Pocket PC obrazovky a ploché monitory. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] používá vykreslování dílčí pixelů, což umožňuje text, který se zobrazí s větší věrnost na jeho true obrazec zarovnání znaky na zlomkové části pixelů. Navíc řešení zvyšuje ostrost jen nepatrnou podrobnosti zobrazení textu, výrazně usnadňují čtení přes dlouhé doby trvání. Jiné zkvalitňování [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je směru osy y vyhlazení, který vyhladí tolní počítače a dolním okraji bez podstruktury křivek v textových znaků. Další informace o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkce, najdete na [ClearType přehled](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 ![Text ClearType y&#45;směr anti&#45;aliasy](../../../../docs/framework/wpf/advanced/media/typographyinwpf02.gif "TypographyInWPF02")  
Text s ClearType směru osy y vyhlazení  
  
 Kanál vykreslování celý text může být accelerated hardwaru v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zadaný váš počítač splňuje minimální hardwarové požadavky. Vykreslení, který nelze provést pomocí hardwaru vrátí k vykreslování softwaru. Hardwarová akcelerace ovlivňuje všechny fáze kanálu vykreslování textu – ukládání jednotlivých glyfů skládání glyfů do glyfy spustí použití důsledky, použití [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] prolnutí algoritmus finální zobrazit výstup. Další informace o hardwarovou akceleraci najdete v tématu [vrstev vykreslování grafiky](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 ![Diagram kanálu vykreslování textu](../../../../docs/framework/wpf/advanced/media/typographyinwpf01.png "TypographyInWPF01")  
Diagram kanálu vykreslení textu  
  
 Kromě toho animovaný text pomocí znaku nebo glyf, plně využívá grafiky schopnost hardwaru ve povolené [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Výsledkem je hladké text animace.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Typografie formátováním  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Písma formát je rozšířením [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] formát písma. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Formát písma byla vyvinuta společně pomocí [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] a Adobe a poskytuje bohaté širokou typografických pokročilých funkcí. <xref:System.Windows.Documents.Typography> Objekt poskytuje řadu pokročilých funkcí [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] písem, například stylových alternativ a ozdobná písmena. [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] Poskytuje sadu ukázka [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] písma, která jsou navrženy s bohaté funkce, jako je Pericles a Pescadero písem. Další informace najdete v tématu [ukázkové sadě písem OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
 Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] písma obsahuje další glyfů, které poskytují stylových alternativ standardní sadu glyfů. Následující text zobrazí stylových alternativních glyfů.  
  
 ![Text s použitím stylových alternativních glyfů OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")  
Text s použitím stylových alternativních glyfů OpenType  
  
 Ozdobná písmena jsou dekorativní glyfů, které používají vypracovala dekoru často přidružené Kaligrafie. Následující text zobrazí standard a protažených glyfů v písmu Pescadero.  
  
 ![Text s použitím OpenType standard a protažených glyfů](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")  
Text s použitím OpenType standard a protažených glyfů  
  
 Další informace o [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] funkce, najdete na [funkce písem OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>Podpora rozšířené mezinárodní textu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje lepší mezinárodní text podporu tím, že poskytuje následující funkce:  
  
-   Automatické-mezery mezi řádky ve všech systémech zápis pomocí adaptivní měření.  
  
-   Široká podpora mezinárodní text. Další informace najdete v tématu [globalizace pro grafický subsystém WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md).  
  
-   Na základě jazyka řádku ukončování řádků, dělení a zarovnání do bloku.  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>Podpora rozšířené písma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje lepší písma podporu tím, že poskytuje následující funkce:  
  
-   Unicode veškerého textu. Chování písma a výběr už vyžadují charset nebo kódové stránky.  
  
-   Chování písma nezávisle na globální nastavení, jako je například národního prostředí.  
  
-   Samostatné <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch>, a <xref:System.Windows.FontStyle> typy pro definování <xref:System.Windows.Media.FontFamily>. To nabízí větší flexibilitu než [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] programování, ve které logická hodnota kombinace kurzíva a tučné slouží k určení v dané rodině písem.  
  
-   Zápis směr (vodorovných versus vertical) zpracovává nezávislé na název písma.  
  
-   Propojení a písmo záložní přenosném [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] souboru pomocí technologie složené písmo. Povolit složená písma pro tvorbu plný rozsah vícejazyčné písem. Složené písma také poskytují mechanismus, který zabraňuje zobrazování chybějící glyfů. Další informace najdete v části poznámky v <xref:System.Windows.Media.FontFamily> třídy.  
  
-   Mezinárodní písma z složená písma, použít skupinu písem v jednom jazyce. To umožňuje ušetřit na náklady prostředků při vývoji písem pro víc jazyků.  
  
-   Složené písem vložených v dokumentu, což zajišťuje přenositelnost dokumentu. Další informace najdete v části poznámky v <xref:System.Windows.Media.FontFamily> třídy.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Nový Text programování rozhraní API (Application)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje několik text [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] pro vývojáře pro použití při včetně textu ve svých aplikacích. Tyto [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] jsou seskupené do tří kategorií:  
  
-   **Rozložení a uživatelské rozhraní**. Ovládací prvky pro běžné text [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)].  
  
-   **Prosté vykreslování textu**. Umožňuje kreslení textu přímo na objekty.  
  
-   **Rozšířené formátování textu**. Umožňuje implementovat modul vlastní text.  
  
### <a name="layout-and-user-interface"></a>Rozložení a uživatelské rozhraní  
 Na nejvyšší úrovni funkčnosti, text [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] zadejte běžné [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ovládací prvky jako například <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.TextBox>. Tyto ovládací prvky poskytují základní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementů v rámci aplikace a nabídka snadný způsob, jak pracovat s textem a k dispozici. Ovládací prvky jako například <xref:System.Windows.Controls.RichTextBox> a <xref:System.Windows.Controls.PasswordBox> povolit více rozšířené nebo specializuje zpracování textu. A třídy, jako <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>, a <xref:System.Windows.Documents.TextPointer> povolit užitečné text manipulaci. Tyto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládací prvky, jako poskytují vlastnosti <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, a <xref:System.Windows.Controls.Control.FontStyle%2A>, které umožňují řídit písmo, které slouží k vykreslení text.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Pomocí rastrový obrázek důsledky, transformace a textové efekty  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umožňuje vytvořit vizuálně zajímavé používá textu používá funkce, například rastrový obrázek důsledky, transformace a efekty textu. Následující příklad ukazuje typický typ efekt stínu rozevírací použít na text.  
  
 ![Stín textu zobrazovat Softness &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")  
Text s stínu  
  
 Následující příklad ukazuje efekt stínu vyřaďte a šumu použít na text.  
  
 ![Stín textu zobrazovat s šumu](../../../../docs/framework/wpf/advanced/media/shadowtext04.jpg "ShadowText04")  
Text s stín a šumu  
  
 Následující příklad ukazuje efekt vnější záře použít na text.  
  
 ![Stín textu zobrazovat pomocí OuterGlowBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext05.jpg "ShadowText05")  
Text s efekt vnější záře  
  
 Následující příklad ukazuje efekt rozostření použít na text.  
  
 ![Stín textu zobrazovat pomocí BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")  
Text s efekt rozostření  
  
 Následující příklad ukazuje na druhém řádku textu škálovat 150 % podél osy x a ve třetím řádku textu škálovat 150 % podél osy y.  
  
 ![Text škálovat pomocí metody ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")  
Text s použitím metody ScaleTransform  
  
 Následující příklad ukazuje text nesouměrně rozdělí podél osy x.  
  
 ![Text nesouměrně rozdělí pomocí metody SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")  
Text s použitím SkewTransform  
  
 A <xref:System.Windows.Media.TextEffect> objekt je pomocný objekt, který umožňuje text považovat za jednu nebo více skupin znaků v textovém řetězci. Následující příklad ukazuje samostatný znak se otočen. Každý znak otočen nezávisle v intervalech 1 sekundu.  
  
 ![Snímek obrazovky textového efektu otáčení textu](../../../../docs/framework/wpf/advanced/media/texteffect01.jpg "TextEffect01")  
Příklad rotační vliv animace textu  
  
#### <a name="using-flow-documents"></a>Použití dokumentů toku  
 Kromě nejběžnější [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládací prvky, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí ovládací prvek rozložení pro text prezentace – <xref:System.Windows.Documents.FlowDocument> elementu. <xref:System.Windows.Documents.FlowDocument> Element společně s <xref:System.Windows.Controls.DocumentViewer> elementu, poskytuje ovládací prvek pro velké objemy textu s použitím různých rozložení požadavky. Rozložení ovládacích prvků poskytnout přístup k pokročilé typografii prostřednictvím <xref:System.Windows.Documents.Typography> objekt a vlastnosti související s písma jiné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládací prvky.  
  
 Následující příklad ukazuje, textového obsahu v hostované <xref:System.Windows.Controls.FlowDocumentReader>, který poskytuje vyhledávání, navigace, stránkování a obsah škálování podpory.  
  
 ![Příklad použití písem OpenType snímek obrazovky](../../../../docs/framework/wpf/advanced/media/typographyinwpf-03.png "TypographyInWPF_03")  
Text FlowDocumentReader s hostitelem  
  
 Další informace najdete v tématu [dokumenty v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Kreslení prostý Text  
 Můžete přímo na kreslení textu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty pomocí <xref:System.Windows.Media.DrawingContext.DrawText%2A> metodu <xref:System.Windows.Media.DrawingContext> objektu. Chcete-li použít tuto metodu, je vytvořit <xref:System.Windows.Media.FormattedText> objektu. Tento objekt umožňuje kreslení víceřádkový text, ve kterém lze jednotlivé znaky v textu jednotlivě formátovat. Funkce <xref:System.Windows.Media.FormattedText> objekt obsahuje mnoho funkcí příznaky DrawText v rozhraní API Win32. Kromě toho <xref:System.Windows.Media.FormattedText> objekt obsahuje funkce, jako je podpora třemi tečkami, ve kterém se třemi tečkami zobrazí, když text překračuje jeho hranice. Následující příklad ukazuje, text, který se má použít, včetně lineárního přechodu na druhý a třetí slova různých formátech.  
  
 ![Text zobrazený pomocí objektu FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
Pomocí objektu FormattedText zobrazovaného textu  
  
 Formátovaný text do můžete převést <xref:System.Windows.Media.Geometry> objekty, umožňuje vytvářet jiné typy zajímavé vizuální text. Například můžete vytvořit <xref:System.Windows.Media.Geometry> objektu podle obrys textového řetězce.  
  
 ![Osnova text použití štětce přechodu lineární](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Osnova text použití lineární štětce přechodu  
  
 Následující příklady ilustrují několik způsobů vytvoření zajímavé vizuální efekty úpravou tahu, výplň a zvýraznění převedený textu.  
  
 ![Text pomocí různých barev pro výplně a tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Příklad nastavení tahu a vyplňte pro různé barev  
  
 ![Text s štětce bitové kopie u tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Příklad štětce bitové kopie u tahu  
  
 ![Text s štětce bitové kopie u tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Příklad štětce obrázku použita pro tahu a zvýraznění  
  
 Další informace o <xref:System.Windows.Media.FormattedText> objektu, najdete v části [kreslení textu ve formátu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Upřesněné formátování textu  
 Nejvýše pokročilé úrovni text [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí možnost vytvářet vlastní text rozložení pomocí <xref:System.Windows.Media.TextFormatting.TextFormatter> objektu a dalších typů v <xref:System.Windows.Media.TextFormatting> oboru názvů. <xref:System.Windows.Media.TextFormatting.TextFormatter> a související třídy povolit můžete implementovat vlastní text rozložení, který podporuje vlastní definice znak formáty, styly odstavce řádek pravidla ukončování řádků, a další rozložení funkce mezinárodní textu. Existují jen několik případy, ve kterých by chcete přepsat výchozí implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podpora rozložení textu. Při vytváření aplikace nebo ovládací prvek pro úpravy textu, můžete však potřebovat jinou implementaci než výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace.  
  
 Na rozdíl od tradičních text [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], <xref:System.Windows.Media.TextFormatting.TextFormatter> komunikuje s klientem rozložení textu pomocí sady metody zpětného volání. Vyžaduje klienta k poskytování těchto metod v implementaci <xref:System.Windows.Media.TextFormatting.TextSource> třídy. Následující diagram znázorňuje interakci rozložení textu mezi klientská aplikace a <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta rozložení textu a objektu TextFormatter](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Interakce mezi aplikací a objektu TextFormatter  
  
 Další podrobnosti o vytvoření vlastní text rozložení najdete v tématu [Advanced formátování textu](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.FormattedText>  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>  
 [ClearType – přehled](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [Funkce písma OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Kreslení formátovaného textu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [Pokročilé formátování textu](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Typografie Microsoft](http://www.microsoft.com/typography/default.mspx)
