---
title: Typografie v rozhraní WPF
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 0ba4e8ff639cdfbbec596da45a6e950fff921974
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740721"
---
# <a name="typography-in-wpf"></a>Typografie v rozhraní WPF
V tomto tématu se seznámíte s hlavními typografické funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Mezi tyto funkce patří Vylepšená kvalita a výkon vykreslování textu, podpora typografie OpenType, vylepšený mezinárodní text, Rozšířená podpora písem a nová textová rozhraní aplikací (API).  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Vylepšená kvalita a výkon textu  
 Text v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se vykresluje pomocí technologie Microsoft ClearType, která vylepšuje přehlednost a čitelnost textu. ClearType je softwarová technologie vyvinutá Microsoftem, která vylepšuje čitelnost textu v existujících LCDs (Liquid Crystal displeje), jako jsou obrazovky přenosné počítače, obrazovky Pocket PC a monitor plochých panelů. Technologie ClearType používá vykreslování v pixelech, které umožňuje zobrazení textu s větší věrnou přesností na jeho skutečný tvar zarovnáním znaků na zlomkové části pixelu. Další řešení zvyšuje ostrost drobných podrobností v zobrazení textu, což usnadňuje čtení dlouhých dob trvání. Dalším vylepšením technologie ClearType v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je použití antialiasů směru y, které vyhlazuje horní a dolní část podznaků v textových znacích. Další podrobnosti o funkcích technologie ClearType najdete v tématu [Přehled technologie ClearType](cleartype-overview.md).  
  
 ![Text pomocí technologie ClearType y-Direction anti-aliasing](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Text pomocí technologie ClearType y-Direction antialiasing  
  
 Celý kanál vykreslování textu může být hardwarově urychlený v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] za předpokladu, že váš počítač splňuje minimální požadovanou úroveň hardwaru. Vykreslování, které nelze provést pomocí hardwaru, se vrátí zpět do softwarového vykreslování. Hardwarová akcelerace má vliv na všechny fáze kanálu vykreslování textu – od uložení jednotlivých glyfů, skládání glyfů do glyfů, použití efektů pro aplikování algoritmu prolnutí ClearType na výsledný zobrazený výstup. Další informace o hardwarové akceleraci najdete v tématu [vrstvy vykreslování grafiky](graphics-rendering-tiers.md).  
  
 ![Diagram kanálu vykreslování textu](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Kromě toho animovaný text, ať už znakem nebo glyfem, plně využívá schopnost hardwaru grafiky povolenou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Výsledkem je plynulá animace textu.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Bohatá typografie  
 Formát písma OpenType je rozšířením formátu TrueType®. Formát písma OpenType byl vyvinut společně společností Microsoft a Adobe a poskytuje bohatou řadu pokročilých typografických funkcí. Objekt <xref:System.Windows.Documents.Typography> zpřístupňuje mnoho pokročilých funkcí písem OpenType, jako jsou stylistické alternativy a ozdobné znaky. Windows SDK poskytuje sadu ukázkových písem OpenType, která jsou navržená pomocí bohatých funkcí, jako jsou například písma Pericles a Pescadero. Další informace najdete v tématu [Ukázková sada písem OpenType](sample-opentype-font-pack.md).  
  
 Písmo OpenType Pericles obsahuje další glyfy, které představují stylistické alternativy standardní sady glyfů. Následující text zobrazuje stylistické alternativní glyfy.  
  
 ![Text používající stylistické alternativní glyfy písma OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "Text používající stylistické alternativní glyfy písma OpenType")  
  
 Ozdobné znaky jsou ozdobné glyfy, které používají výtvarné ozdoby, které jsou často spojeny s kaligraficky. Následující text zobrazuje standardní a ozdobné glyfy pro písmo Pescadero.  
  
 ![Text používající standardní a ozdobné glyfy OpenType](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "Text používající standardní a ozdobné glyfy OpenType")  
  
 Další informace o funkcích OpenType naleznete v tématu [funkce písem OpenType](opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>Vylepšená podpora pro mezinárodní text  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje vylepšenou podporu pro mezinárodní text tím, že poskytuje následující funkce:  
  
- Automatické rozestupy ve všech systémech pro psaní pomocí adaptivního měření.  
  
- Široká podpora pro mezinárodní text Další informace naleznete v tématu [globalizace pro WPF](globalization-for-wpf.md).  
  
- Dělení na základě jazyka, dělení a zarovnání řádků s asistencí  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>Rozšířená podpora písem  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje rozšířenou podporu písem tím, že poskytuje následující funkce:  
  
- Kódování Unicode pro veškerý text Chování písem a výběr už nevyžadují znakovou sadu (charset) nebo znakovou stránku.  
  
- Chování písem nezávislá na globálním nastavení, jako je například národní prostředí systému.  
  
- Samostatné typy <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch>a <xref:System.Windows.FontStyle> pro definování <xref:System.Windows.Media.FontFamily>. To poskytuje větší flexibilitu než v [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] programování, ve kterém se k definování rodiny písem používá logické kombinace kurzívy a tučného písma.  
  
- Směr zápisu (vodorovně versus svisle) zpracovává nezávisle na názvu písma.  
  
- Propojení písma a Fallback písma v přenositelném souboru XML pomocí technologie kompozitního písma. Složená písma umožňují konstrukci celé škály vícejazyčných písem. Složená písma také poskytují mechanismus, který brání zobrazení chybějících glyfů. Další informace naleznete v tématu poznámky ve třídě <xref:System.Windows.Media.FontFamily>.  
  
- Mezinárodní písma vytvořená ze složených písem pomocí skupiny písem s jedním jazykem. Tím se šetří náklady na prostředky při vývoji písem pro více jazyků.  
  
- Složená písma vložená v dokumentu, což zajišťuje přenositelnost dokumentu. Další informace naleznete v tématu poznámky ve třídě <xref:System.Windows.Media.FontFamily>.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Nová programovací rozhraní pro aplikace v textu (rozhraní API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje vývojářům několik textových rozhraní API pro použití při zahrnutí textu do svých aplikací. Tato rozhraní API se seskupují do tří kategorií:  
  
- **Rozložení a uživatelské rozhraní**. Běžné textové ovládací prvky grafického uživatelského rozhraní (GUI).  
  
- **Zjednodušené vykreslování textu**. Umožňuje kreslit text přímo do objektů.  
  
- **Rozšířené formátování textu**. Umožňuje implementovat vlastní textový modul.  
  
### <a name="layout-and-user-interface"></a>Rozložení a uživatelské rozhraní  
 Na nejvyšší úrovni funkčnosti obsahují rozhraní API pro text běžné [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ovládací prvky, jako jsou <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>a <xref:System.Windows.Controls.TextBox>. Tyto ovládací prvky poskytují základní prvky [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v rámci aplikace a nabízejí snadný způsob, jak prezentovat text a pracovat s ním. Ovládací prvky jako <xref:System.Windows.Controls.RichTextBox> a <xref:System.Windows.Controls.PasswordBox> umožňují pokročilejší nebo specializované zpracování textu. A třídy, jako jsou <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>a <xref:System.Windows.Documents.TextPointer> umožňují užitečnou manipulaci s textem. Tyto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládací prvky poskytují vlastnosti jako <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>a <xref:System.Windows.Controls.Control.FontStyle%2A>, které umožňují řídit písmo, které se používá k vykreslování textu.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Použití bitmapových efektů, transformací a textových efektů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje vytvořit vizuálně zajímavé používání textu pomocí funkcí, jako jsou rastrové efekty, transformace a textové efekty. Následující příklad ukazuje typický typ efektu Vržený stín aplikovaný na text.  
  
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
  
 Objekt <xref:System.Windows.Media.TextEffect> je pomocný objekt, který umožňuje považovat text za jednu nebo více skupin znaků v textovém řetězci. Následující příklad ukazuje otočení jednotlivého znaku. Každý znak je otočen nezávisle v intervalu 1 – sekund.  
  
 ![Snímek obrazovky rotujícího textu textového efektu](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>Používání dokumentů Flow  
 Kromě běžných [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ch ovládacích prvků nabízí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek rozložení textové prezentace – prvek <xref:System.Windows.Documents.FlowDocument>. Element <xref:System.Windows.Documents.FlowDocument> v kombinaci s <xref:System.Windows.Controls.DocumentViewer> prvkem poskytuje ovládací prvek pro velké objemy textu s různými požadavky na rozložení. Ovládací prvky rozložení poskytují přístup k pokročilým typografii prostřednictvím objektu <xref:System.Windows.Documents.Typography> a vlastností souvisejících s písmem jiných [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládacích prvků.  
  
 Následující příklad ukazuje textový obsah hostovaný ve <xref:System.Windows.Controls.FlowDocumentReader>, který poskytuje podporu vyhledávání, navigace, stránkování a škálování obsahu.  
  
 ![Snímek obrazovky, který zobrazuje písma OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Další informace najdete v tématu [dokumenty v WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Zjednodušené vykreslování textu  
 Text lze nakreslit přímo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů pomocí metody <xref:System.Windows.Media.DrawingContext.DrawText%2A> objektu <xref:System.Windows.Media.DrawingContext>. Chcete-li použít tuto metodu, vytvoříte objekt <xref:System.Windows.Media.FormattedText>. Tento objekt umožňuje nakreslit víceřádkový text, ve kterém je každý znak v textu možné formátovat individuálně. Funkce objektu <xref:System.Windows.Media.FormattedText> obsahuje většinu funkcí příznaků DrawText v rozhraní API systému Windows. Kromě toho objekt <xref:System.Windows.Media.FormattedText> obsahuje funkce, jako je například podpora tří teček, ve kterém se zobrazí tři tečky, když text překročí hranice. Následující příklad ukazuje text, který obsahuje několik formátů, včetně lineárního přechodu na druhý a třetí slova.  
  
 ![Text zobrazený pomocí objektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 Formátovaný text můžete převést na <xref:System.Windows.Media.Geometry> objekty, což vám umožní vytvořit další typy vizuálně zajímavého textu. Můžete například vytvořit objekt <xref:System.Windows.Media.Geometry> na základě obrysu textového řetězce.  
  
 ![Obrys textu s použitím štětce s lineárním přechodem](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Následující příklady ilustrují několik způsobů vytváření zajímavých vizuálních efektů úpravou tahu, výplně a zvýraznění převedeného textu.  
  
 ![Text s různými barvami pro výplň a tah](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Text s obrázkem štětce aplikovaný na tah](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Text s obrázkem štětce aplikovaný na tah a zvýraznění](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Další informace o objektu <xref:System.Windows.Media.FormattedText> najdete v tématu [Kreslení formátovaného textu](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Upřesněné formátování textu  
 Na nejrozšířenější úrovni textových rozhraní API nabízí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] možnost vytvářet vlastní rozložení textu pomocí objektu <xref:System.Windows.Media.TextFormatting.TextFormatter> a dalších typů v oboru názvů <xref:System.Windows.Media.TextFormatting>. <xref:System.Windows.Media.TextFormatting.TextFormatter> a přidružené třídy vám umožňují implementovat vlastní rozložení textu, které podporuje vaše vlastní definice formátů znaků, odstavcové styly, pravidla ukončování řádků a další funkce rozložení pro mezinárodní text. V některých případech je vhodné přepsat výchozí implementaci podpory [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho rozložení textu. Pokud jste ale vytvořili ovládací prvek pro úpravu textu nebo aplikaci, můžete vyžadovat odlišnou implementaci, než je výchozí implementace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Na rozdíl od tradičního textového rozhraní API <xref:System.Windows.Media.TextFormatting.TextFormatter> komunikuje s klientem rozložení textu prostřednictvím sady metod zpětného volání. Vyžaduje, aby klient poskytoval tyto metody v implementaci třídy <xref:System.Windows.Media.TextFormatting.TextSource>. Následující diagram znázorňuje interakci rozložení textu mezi klientskou aplikací a <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
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
- [Typografie Microsoftu](https://docs.microsoft.com/typography/)
