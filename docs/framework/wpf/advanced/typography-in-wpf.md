---
title: Typografie
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 501a4221c99d405484a2fb908641d27d1f38f266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187354"
---
# <a name="typography-in-wpf"></a>Typografie v rozhraní WPF
Toto téma představuje hlavní typografické rysy aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Mezi tyto funkce patří lepší kvalita a výkon vykreslování textu, podpora typografie OpenType, vylepšený mezinárodní text, vylepšená podpora písem a nová rozhraní API pro programování textových aplikací.  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>
## <a name="improved-quality-and-performance-of-text"></a>Zlepšená kvalita a výkon textu  
 Text [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v aplikaci je vykreslen pomocí programu Microsoft ClearType, což zvyšuje srozumitelnost a čitelnost textu. ClearType je softwarová technologie vyvinutá společností Microsoft, která zlepšuje čitelnost textu na stávajících LCD (displeje z tekutých krystalů), jako jsou obrazovky notebooků, obrazovky kapesních počítačů a ploché monitory. ClearType používá vykreslování sub-pixel, které umožňuje text, který má být zobrazen s větší věrností jeho skutečného tvaru zarovnáním znaků na zlomkové části obrazového bodu. Dodatečné rozlišení zvyšuje ostrost drobných detailů v textovém displeji, takže je mnohem snazší číst po dlouhou dobu. Dalším vylepšením funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ClearType je vyhlazení směru y, které vyhlazuje vrcholy a dna mělkých křivek v textových znacích. Další podrobnosti o funkcích ClearType najdete v tématu [Přehled jazyka ClearType](cleartype-overview.md).  
  
 ![Text s vyhlazením ve směru y Příkazu ClearType](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Text s vyhlazením ve směru y příkazu ClearType  
  
 Celý kanál vykreslování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] textu může být hardwarově akcelerován za předpokladu, že váš počítač splňuje minimální požadovanou úroveň hardwaru. Vykreslování, které nelze provést pomocí hardwaru, se vrátí zpět do softwarového vykreslování. Hardwarová akcelerace ovlivňuje všechny fáze kanálu vykreslování textu – od ukládání jednotlivých glyfů, skládání glyfů do běhů glyfů, aplikování efektů až po aplikování algoritmu prolnutí ClearType na konečný zobrazený výstup. Další informace o hardwarové akceleraci naleznete v [tématu Úrovně vykreslování grafiky](graphics-rendering-tiers.md).  
  
 ![Diagram kanálu vykreslení textu](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Animovaný text, ať už znaknebo glyf, navíc plně využívá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]výhod grafických hardwarových funkcí povolených aplikací . Výsledkem je plynulá animace textu.  
  
<a name="Rich_Typography"></a>
## <a name="rich-typography"></a>Bohatá typografie  
 Formát písma OpenType je příponou formátu písma TrueType®. Formát písma OpenType byl vyvinut společně společnostmi Microsoft a Adobe a poskytuje bohatý sortiment pokročilých typografických funkcí. Objekt <xref:System.Windows.Documents.Typography> zpřístupňuje mnoho pokročilých funkcí písem OpenType, jako jsou stylistické alternativy a svítidla. Sada Windows SDK poskytuje sadu ukázkových písem OpenType, které jsou navrženy s bohatými funkcemi, jako jsou písma Pericles a Pescadero. Další informace naleznete [v tématu Ukázka sady OpenType Font Pack](sample-opentype-font-pack.md).  
  
 Písmo Pericles OpenType obsahuje další glyfy, které poskytují stylistické alternativy ke standardní sadě glyfů. Následující text zobrazuje stylistické alternativní glyfy.  
  
 ![Text pomocí alternativních glyfů stylistické opentype](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "Text pomocí alternativních glyfů stylistické opentype")  
  
 Ozdobné výmysly jsou ozdobné glyfy, které používají propracované ornamenty často spojené s kaligrafií. Následující text zobrazuje standardní a vymývací glyfy pro písmo Pescadero.  
  
 ![Text pomocí standardu OpenType a glyfů s mycími barvami](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "Text pomocí standardu OpenType a glyfů s mycími barvami")  
  
 Další podrobnosti o funkcích OpenType najdete [v tématu Funkce písma OpenType](opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>
## <a name="enhanced-international-text-support"></a>Vylepšená mezinárodní textová podpora  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje rozšířenou mezinárodní textovou podporu tím, že poskytuje následující funkce:  
  
- Automatické řádkování ve všech systémech zápisu pomocí adaptivního měření.  
  
- Široká podpora mezinárodního textu. Další informace naleznete v [tématu Globalizace pro WPF](globalization-for-wpf.md).  
  
- Jazykově vedené dělení čar, dělení slov a zarovnání.  
  
<a name="Enhanced_Font_Support"></a>
## <a name="enhanced-font-support"></a>Vylepšená podpora písem  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Poskytuje rozšířenou podporu písem tím, že poskytuje následující funkce:  
  
- Unicode pro veškerý text. Chování písma a výběr již nevyžadují znakovou sadu nebo znakovou stránku.  
  
- Chování písma nezávisle na globálním nastavení, jako je například národní prostředí systému.  
  
- Samostatné <xref:System.Windows.FontWeight> <xref:System.Windows.FontStretch>a <xref:System.Windows.FontStyle> typy pro definování <xref:System.Windows.Media.FontFamily>. To poskytuje větší flexibilitu než v programování Win32, ve kterém logické kombinace kurzívy a tučné ho se používají k definování rodiny písem.  
  
- Směr zápisu (vodorovný versus svislý) zpracovánnezávisle na názvu písma.  
  
- Propojení písem a záložní písmo v přenosném souboru XML pomocí technologie kompozitních písem. Složená písma umožňují konstrukci vícejazyčných písem v plném rozsahu. Složená písma také poskytují mechanismus, který zabraňuje zobrazení chybějících glyfů. Další informace naleznete v poznámkách ve <xref:System.Windows.Media.FontFamily> třídě.  
  
- Mezinárodní písma vytvořená z kompozitních písem pomocí skupiny jednojazyčných písem. To šetří náklady na prostředky při vývoji písem pro více jazyků.  
  
- Složená písma vložená do dokumentu, čímž poskytují přenositelnost dokumentu. Další informace naleznete v poznámkách ve <xref:System.Windows.Media.FontFamily> třídě.  
  
<a name="New_Text_APIs"></a>
## <a name="new-text-application-programming-interfaces-apis"></a>Nová rozhraní pro programování textových aplikací (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje několik textových rozhraní API pro vývojáře, které mají vývojáři používat při zahrnutí textu do svých aplikací. Tato api jsou seskupeny do tří kategorií:  
  
- **Rozložení a uživatelské rozhraní**. Běžné textové ovládací prvky pro grafické uživatelské rozhraní (GUI).  
  
- **Zjednodušené kreslení textu**. Umožňuje kreslit text přímo k objektům.  
  
- **Rozšířené formátování textu**. Umožňuje implementovat vlastní textový modul.  
  
### <a name="layout-and-user-interface"></a>Rozložení a uživatelské rozhraní  
 Na nejvyšší úrovni funkčnosti poskytují textová [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] rozhraní API <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock>běžné <xref:System.Windows.Controls.TextBox>ovládací prvky, například , a . Tyto ovládací prvky poskytují základní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky v rámci aplikace a nabízejí snadný způsob prezentace a interakce s textem. Ovládací prvky, jako <xref:System.Windows.Controls.RichTextBox> je například a <xref:System.Windows.Controls.PasswordBox> povolit pokročilejší nebo specializované zpracování textu. A třídy, jako <xref:System.Windows.Documents.TextRange>je například , <xref:System.Windows.Documents.TextSelection>a <xref:System.Windows.Documents.TextPointer> umožňují užitečnou manipulaci s textem. Tyto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládací prvky <xref:System.Windows.Controls.Control.FontFamily%2A> <xref:System.Windows.Controls.Control.FontSize%2A>poskytují <xref:System.Windows.Controls.Control.FontStyle%2A>vlastnosti, jako jsou například , a , které umožňují řídit písmo, které se používá k vykreslení textu.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Použití bitmapových efektů, transformací a textových efektů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umožňuje vytvářet vizuálně zajímavé použití textu pomocí funkcí, jako jsou bitmapové efekty, transformace a textové efekty. Následující příklad ukazuje typický typ efektu vrženého stínu aplikovaného na text.  
  
 ![Textový stín s &#61; měkkosti 0,25](./media/typography-in-wpf/drop-shadow-text-effect.jpg)
  
 Následující příklad ukazuje efekt vrženého stínu a šum aplikovaný na text.  
  
 ![Textový stín s šumem](./media/typography-in-wpf/drop-shadow-noise-text.jpg)
  
 Následující příklad ukazuje vnější efekt záře aplikovaný na text.  
  
 ![Stín textu pomocí efektu OuterGlowBitmapEffect](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 Následující příklad ukazuje efekt rozostření aplikovaný na text.  
  
 ![Textový stín pomocí efektu BlurBitmapEffect](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 Následující příklad ukazuje druhý řádek textu se 150 % podél osy x a třetí řádek textu o 150 % podél osy y.  
  
 ![Velikost textu s měřítkem pomocí scaletransform](./media/typography-in-wpf/scaled-text-scaletransform.jpg)
  
 Následující příklad ukazuje text zkosený podél osy x.  
  
 ![Text zkosený pomocí skewtransformu](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 Objekt <xref:System.Windows.Media.TextEffect> je pomocný objekt, který umožňuje považovat text za jednu nebo více skupin znaků v textovém řetězci. Následující příklad ukazuje jednotlivý znak, který se otáčí. Každý znak je otočen nezávisle v intervalech 1 sekundy.  
  
 ![Snímek obrazovky s rotujícím textem textového efektu](./media/typography-in-wpf/rotating-text-effect.jpg)
  
#### <a name="using-flow-documents"></a>Použití dokumentů toku  
 Kromě běžných [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládacích [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvků nabízí ovládací prvek <xref:System.Windows.Documents.FlowDocument> rozložení pro textovou prezentaci – prvek. Prvek <xref:System.Windows.Documents.FlowDocument> ve spojení s <xref:System.Windows.Controls.DocumentViewer> elementem poskytuje ovládací prvek pro velké množství textu s různými požadavky na rozložení. Ovládací prvky rozložení poskytují přístup <xref:System.Windows.Documents.Typography> k rozšířené typografii prostřednictvím objektu a vlastností souvisejících s písmem jiných ovládacích [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvků.  
  
 Následující příklad ukazuje textový obsah <xref:System.Windows.Controls.FlowDocumentReader>hostovaný v , který poskytuje podporu pro vyhledávání, navigaci, stránkování a škálování obsahu.  
  
 ![Snímek obrazovky, který zobrazuje písma OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Další informace naleznete [v tématu Dokumenty v wpf](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Zjednodušené kreslení textu  
 Text můžete kreslit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přímo k <xref:System.Windows.Media.DrawingContext.DrawText%2A> objektům <xref:System.Windows.Media.DrawingContext> pomocí metody objektu. Chcete-li použít tuto <xref:System.Windows.Media.FormattedText> metodu, vytvořte objekt. Tento objekt umožňuje nakreslit víceřádkový text, ve kterém může být každý znak v textu individuálně formátován. Funkce objektu <xref:System.Windows.Media.FormattedText> obsahuje většinu funkcí DrawText příznaky v rozhraní API systému Windows. Kromě toho <xref:System.Windows.Media.FormattedText> objekt obsahuje funkce, jako je například podpora tři tečky, ve kterém se zobrazí tři tečky, když text překročí jeho hranice. Následující příklad ukazuje text, který má několik formátů, včetně lineárního přechodu na druhé a třetí slovo.  
  
 ![Text zobrazený pomocí objektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)
  
 Formátovaný text můžete <xref:System.Windows.Media.Geometry> převést na objekty, což vám umožní vytvářet další typy vizuálně zajímavého textu. Můžete například vytvořit <xref:System.Windows.Media.Geometry> objekt založený na obrysu textového řetězce.  
  
 ![Obrys textu pomocí stopy lineárního přechodu](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Následující příklady ilustrují několik způsobů vytváření zajímavých vizuálních efektů úpravou tahu, výplně a zvýraznění převedeného textu.  
  
 ![Text s různými barvami pro výplň a tah](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Text s obrazovou stopou aplikovanou na tah](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Text s obrazovou stopou aplikovanou na tah a zvýraznění](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Další informace o <xref:System.Windows.Media.FormattedText> objektu naleznete v [tématu Drawing Formatted Text](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Upřesněné formátování textu  
 Na nejpokročilejší úrovni textových rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API nabízí možnost vytvořit vlastní rozložení <xref:System.Windows.Media.TextFormatting.TextFormatter> textu pomocí objektu <xref:System.Windows.Media.TextFormatting> a dalších typů v oboru názvů. A <xref:System.Windows.Media.TextFormatting.TextFormatter> přidružené třídy umožňují implementovat vlastní rozložení textu, které podporuje vlastní definici formátů znaků, odstavcových stylů, pravidel rozdělení řádků a dalších funkcí rozložení pro mezinárodní text. Existuje velmi málo případů, ve kterých byste chtěli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přepsat výchozí implementaci podpory rozložení textu. Pokud jste však vytvářeli ovládací prvek pro úpravy textu nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci, může vyžadovat jinou implementaci než výchozí implementace.  
  
 Na rozdíl od tradičního textového <xref:System.Windows.Media.TextFormatting.TextFormatter> rozhraní API interaguje s klientem rozložení textu prostřednictvím sady metod zpětného volání. Vyžaduje, aby klient poskytnout tyto metody <xref:System.Windows.Media.TextFormatting.TextSource> v implementaci třídy. Následující diagram znázorňuje interakci rozložení textu <xref:System.Windows.Media.TextFormatting.TextFormatter>mezi klientskou aplikací a aplikací .  
  
 ![Diagram klienta rozložení textu a textformatter](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Další podrobnosti o vytváření vlastního rozložení textu naleznete v [tématu Rozšířené formátování textu](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType – přehled](cleartype-overview.md)
- [Funkce písma OpenType](opentype-font-features.md)
- [Kreslení formátovaného textu](drawing-formatted-text.md)
- [Upřesněné formátování textu](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Typografie microsoftu](https://docs.microsoft.com/typography/)
