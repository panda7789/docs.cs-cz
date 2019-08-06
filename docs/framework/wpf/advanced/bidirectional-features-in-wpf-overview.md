---
title: Obousměrné funkce v přehledu WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: d2b35a50d9d09bffd69ae8b8217d6e778ce66ea0
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796401"
---
# <a name="bidirectional-features-in-wpf-overview"></a>Obousměrné funkce v přehledu WPF
Na rozdíl od jakékoli jiné vývojové platformy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje mnoho funkcí, které podporují rychlý vývoj obousměrného obsahu, například smíšenou levou a pravou a zprava doleva data ve stejném dokumentu. Ve stejnou chvíli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvoří Skvělé prostředí pro uživatele, kteří vyžadují obousměrné funkce, jako jsou arabské a hebrejské speaking Users.  
  
 Následující části vysvětlují mnoho obousměrných funkcí společně s příklady ilustrující, jak dosáhnout nejlepšího zobrazení obousměrného obsahu. Většina ukázek používá [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], i když můžete snadno použít koncepty nástroje C# nebo kód Microsoft Visual Basic.  

<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 Základní vlastnost definující směr toku obsahu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci je. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Tato vlastnost může být nastavena na jednu ze dvou hodnot <xref:System.Windows.FlowDirection.LeftToRight> výčtu nebo. <xref:System.Windows.FlowDirection.RightToLeft> Vlastnost je k dispozici pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] všechny prvky, které <xref:System.Windows.FrameworkElement>dědí z.  
  
 Následující příklady nastaví směr <xref:System.Windows.Controls.TextBox> toku prvku.  
  
 **Směr toku zleva doprava**  
  
 [!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Směr toku zprava doleva**  
  
 [!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 Následující obrázek ukazuje, jak se vykreslí předchozí kód.  
    
 ![Obrázek, který znázorňuje různé směry toku.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)  
  
 Element v rámci [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] stromu <xref:System.Windows.FrameworkElement.FlowDirection%2A> zdědí z jeho kontejneru. V následujícím příkladu <xref:System.Windows.Controls.TextBlock> je <xref:System.Windows.Controls.Grid>uvnitř a, který se nachází v <xref:System.Windows.Window>. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Nastavení proparametr<xref:System.Windows.Controls.Grid> implikujes pro a <xref:System.Windows.Controls.TextBlock> také. <xref:System.Windows.Window>  
  
 Následující příklad ukazuje nastavení <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 <xref:System.Windows.Window> Nejvyšší úroveň má, takže <xref:System.Windows.FlowDirection.RightToLeft>všechny prvky obsažené v ní také dědí stejný <xref:System.Windows.FrameworkElement.FlowDirection%2A>objekt <xref:System.Windows.FlowDirection>. Pro prvek, který má přepsat specifikovanou <xref:System.Windows.FrameworkElement.FlowDirection%2A> , musí přidat explicitní změnu směru, jako je například druhý <xref:System.Windows.Controls.TextBlock> v předchozím příkladu, který se <xref:System.Windows.FlowDirection.LeftToRight>změní na. Pokud není definován, použije se výchozí <xref:System.Windows.FlowDirection.LeftToRight>hodnota. <xref:System.Windows.FrameworkElement.FlowDirection%2A>  
  
 Následující obrázek ukazuje výstup předchozího příkladu:

 ![Obrázek, který znázorňuje explicitní změnu směru toku.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)  

<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Řada vývojových platforem, jako jsou [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] HTML a Java, nabízí speciální podporu pro vývoj obousměrného obsahu. Jazyky značek, jako je například HTML, poskytují zapisovači obsahu potřebné značky k zobrazení textu v libovolném požadovaném směru, například značka HTML 4,0, "dir", který přijímá "RTL" nebo "ltr" jako hodnoty. Tato značka je podobná <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnosti, <xref:System.Windows.FrameworkElement.FlowDirection%2A> ale vlastnost pracuje s pokročilejším způsobem rozložení textového obsahu a lze ji použít pro jiný obsah než text.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]je univerzální prvek[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který může hostovat kombinaci textu, tabulek, obrázků a dalších prvků. <xref:System.Windows.Documents.FlowDocument> Ukázky v následujících částech používají tento prvek.  
  
 Přidání textu do <xref:System.Windows.Documents.FlowDocument> může být provedeno tím, že je jedním způsobem. Jediným způsobem, jak to provést, je prostřednictvím <xref:System.Windows.Documents.Paragraph> prvku, který je prvkem na úrovni bloku, který slouží k seskupení obsahu, jako je například text. Chcete-li přidat text do prvků na úrovni vložené pomocí <xref:System.Windows.Documents.Span> vzorků <xref:System.Windows.Documents.Run>a. <xref:System.Windows.Documents.Span>je element obsahu toku na úrovni vloženého objektu, který se používá pro seskupení dalších vložených <xref:System.Windows.Documents.Run> prvků, zatímco je element obsahu toku na úrovni vloženého objektu, který je určen pro spuštění neformátovaného textu. Může obsahovat více <xref:System.Windows.Documents.Run>elementů. <xref:System.Windows.Documents.Span>  
  
 Příklad prvního dokumentu obsahuje dokument, který má několik názvů síťových sdílených složek; například `\\server1\folder\file.ext`. Bez ohledu na to, jestli máte tento odkaz na síť v dokumentu arabštiny nebo angličtiny, je vždycky vhodné ho zobrazovat stejným způsobem. Následující obrázek znázorňuje použití prvku span a ukazuje odkaz v dokumentu arabštiny <xref:System.Windows.FlowDirection.RightToLeft> :

 ![Obrázek, který znázorňuje použití prvku span.](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")  
  
 Vzhledem k tomu, <xref:System.Windows.FlowDirection.RightToLeft>že text je, všechny speciální znaky, například\\"", oddělte text vpravo k levému pořadí. To znamená, že odkaz není zobrazen ve správném pořadí, proto je nutné tento problém vyřešit tak, aby se zachovalo samostatné <xref:System.Windows.Documents.Run> <xref:System.Windows.FlowDirection.LeftToRight>toky. Místo toho, aby se <xref:System.Windows.Documents.Run> pro každý jazyk používala samostatná, je vhodnější tento problém vyřešit tak, že do větší arabského <xref:System.Windows.Documents.Span>textu vložíte méně často používaný anglický text.  
  
 Následující obrázek znázorňuje to pomocí elementu Run vloženého v elementu span:

 ![Obrázek, který znázorňuje element Run vložený v elementu span.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)  
  
 Následující příklad ukazuje použití <xref:System.Windows.Documents.Run> elementů a <xref:System.Windows.Documents.Span> v dokumentech.  
  
 [!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Span – elementy  
 <xref:System.Windows.Documents.Span> Prvek funguje jako oddělovač hranice mezi textem s různými směry toku.  I <xref:System.Windows.Documents.Span> prvky se stejným směrem toku jsou považovány za mají různé obousměrné obory <xref:System.Windows.FlowDirection>, <xref:System.Windows.Documents.Span> což znamená, že prvky jsou uspořádány v kontejneru, pouze obsah <xref:System.Windows.Documents.Span> v rámci elementu. <xref:System.Windows.FlowDirection> následuje<xref:System.Windows.Documents.Span>po.  
  
 Následující obrázek znázorňuje směr toku několika <xref:System.Windows.Controls.TextBlock> prvků.  
    
 ![Obrázek, který znázorňuje textové bloky s různými směry toku.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Documents.Span> prvky a <xref:System.Windows.Documents.Run> k vytvoření výsledků zobrazených v předchozím obrázku.  
  
 [!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection> <xref:System.Windows.Documents.Span> V prvcích v ukázce <xref:System.Windows.Documents.Span> jsou prvky rozloženy podle jejich nadřazených prvků, ale text v rámci každého prvku toků pracuje podle vlastního typu. <xref:System.Windows.Controls.TextBlock> To platí pro Latinská a arabské jazyky – případně pro jiný jazyk.  
  
### <a name="adding-xmllang"></a>Přidání XML: lang  
 Následující obrázek ukazuje jiný příklad, který používá čísla a aritmetické výrazy, například `"200.0+21.4=221.4"`. Všimněte si, že <xref:System.Windows.FlowDirection> je nastavena pouze sada.  
    
 ![Obrázek, který zobrazuje čísla pouze pomocí FlowDirection.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)  
  
 Uživatelé této aplikace budou Disappointed výstupem, i když <xref:System.Windows.FlowDirection> je Opravná, i když je třeba, aby čísla nebyla ve tvaru arabského čísla.  
  
 Prvky XAML mohou zahrnovat [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] atribut (`xml:lang`), který definuje jazyk každého prvku. XAML také podporuje `xml:lang` princip [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jazyka, který umožňuje, aby hodnoty použité pro nadřazené prvky ve stromu byly používány podřízenými prvky. V předchozím příkladu, protože jazyk nebyl definován pro <xref:System.Windows.Documents.Run> element nebo žádný z jeho elementů nejvyšší úrovně, byla použita výchozí hodnota `xml:lang` , která je určena `en-US` pro jazyk XAML. Algoritmus interního čísla tvarování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vybere čísla v odpovídajícím jazyku, v tomto případě v angličtině. Aby bylo možné správně vykreslit arabské `xml:lang` číslice, je třeba nastavit jejich správné nastavení.  
  
 Následující obrázek znázorňuje příklad s `xml:lang` přidáním.  
    
 ![Obrázek, který znázorňuje arabské čísla, která se směrují zprava doleva.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)  
  
 Následující příklad přidá `xml:lang` do aplikace.  
  
 [!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Počítejte s tím, že mnoho jazyků `xml:lang` má různé hodnoty v závislosti na cílové oblasti, `"ar-SA"` například a `"ar-EG"` představuje dvě varianty arabštiny. Předchozí příklady ilustrují, že je nutné definovat `xml:lang` hodnoty a. <xref:System.Windows.FlowDirection>  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>FlowDirection s prvky, které nejsou textové  
 <xref:System.Windows.FlowDirection>definuje nejen to, jak text toky v textovém elementu, ale také směr toku téměř všech ostatních [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvků. Následující obrázek ukazuje <xref:System.Windows.Controls.ToolBar> , který používá vodorovný <xref:System.Windows.Media.LinearGradientBrush> k nakreslení pozadí s levým a pravým přechodem.  

 ![Obrázek, který zobrazuje panel nástrojů s levým a pravým přechodem.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)  
  
 Po nastavení <xref:System.Windows.FlowDirection> na <xref:System.Windows.FlowDirection.RightToLeft>, nejen <xref:System.Windows.Controls.ToolBar> tlačítka jsou uspořádána zprava doleva, ale i v případě, že <xref:System.Windows.Media.LinearGradientBrush> se jejich posuny přemění na tok zprava doleva.  
  
 Následující obrázek znázorňuje nové zarovnání <xref:System.Windows.Media.LinearGradientBrush>.  
    
 ![Obrázek, který zobrazuje panel nástrojů se směrem k levému barevnému přechodu.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)  
  
 Následující příklad kreslí <xref:System.Windows.FlowDirection.RightToLeft>. <xref:System.Windows.Controls.ToolBar> (Chcete-li ji nakreslit vlevo, odeberte <xref:System.Windows.FlowDirection> atribut <xref:System.Windows.Controls.ToolBar>v.  
  
 [!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>Výjimky FlowDirection  
 V některých případech <xref:System.Windows.FlowDirection> se nechová podle očekávání. Tato část se zabývá dvěma výjimkami.  
  
 **Obrázek**  
  
 <xref:System.Windows.Controls.Image> Představuje ovládací prvek, který zobrazuje obrázek. V [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] takovém případě lze použít <xref:System.Windows.Controls.Image.Source%2A> s vlastností <xref:System.Windows.Controls.Image> , která definuje [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] vlastnost, která má být zobrazena.  
  
 Na <xref:System.Windows.Controls.Image> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rozdílodjinýchprvkůnedědízkontejneru.<xref:System.Windows.FlowDirection> Pokud <xref:System.Windows.FlowDirection> je však nastavena explicitně na <xref:System.Windows.FlowDirection.RightToLeft>hodnotu, <xref:System.Windows.Controls.Image> je zobrazena překlopení vodorovně. To je implementováno jako pohodlnější funkce pro vývojáře obousměrného obsahu. vzhledem k tomu, že v některých případech je vodorovný překlopení obrázku požadovaným efektem.  
  
 Následující obrázek ukazuje překlopení <xref:System.Windows.Controls.Image>.  
    
 ![Obrázek, který ilustruje převrácenou bitovou kopii.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)  
  
 Následující příklad ukazuje, že <xref:System.Windows.Controls.Image> <xref:System.Windows.FlowDirection> nedědí z rozhraní <xref:System.Windows.Controls.StackPanel> , které ho obsahuje. **Poznámka:** V C:\ musíte mít soubor s názvem **ms_logo. jpg.** jednotku pro spuštění tohoto příkladu.  
  
 [!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Poznámka:** Součástí souborů ke stažení je soubor **ms_logo. jpg** . Kód předpokládá, že soubor. jpg není v projektu, ale někde na C:\ disky. Je nutné zkopírovat soubor. jpg ze souborů projektu do C:\ disk nebo změňte kód tak, aby byl soubor v projektu hledán. Chcete-li provést `Source="file://c:/ms_logo.jpg"` tuto `Source="ms_logo.jpg"`změnu na.  
  
 **Ruky**  
  
 Kromě <xref:System.Windows.Controls.Image>jiného zajímavého prvku je <xref:System.Windows.Shapes.Path>. Cesta je objekt, který může nakreslit řadu propojených čar a křivek. Se chová způsobem <xref:System.Windows.FlowDirection>, který se podobá tomu <xref:System.Windows.Controls.Image> , že se týká. například <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> je to horizontální zrcadlení jeho <xref:System.Windows.FlowDirection.LeftToRight> . Nicméně na rozdíl <xref:System.Windows.Controls.Image>od, <xref:System.Windows.Shapes.Path> dědí <xref:System.Windows.FlowDirection> z kontejneru a druhý jej nepotřebuje explicitně zadat.  
  
 V následujícím příkladu je nakreslena Jednoduchá šipka pomocí 3 čáry. První šipka zdědí <xref:System.Windows.FlowDirection.RightToLeft> směr toku <xref:System.Windows.Controls.StackPanel> od, takže počáteční a koncový bod se měří od kořene na pravé straně. Druhá šipka, která má explicitní <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> , začíná také na pravé straně. Třetí šipka ale má svůj počáteční kořen na levé straně. Další informace o kreslení naleznete v <xref:System.Windows.Media.LineGeometry> tématu <xref:System.Windows.Media.GeometryGroup>a.  
  
 [!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 Následující obrázek znázorňuje výstup předchozího příkladu se šipkami nakreslenými pomocí `Path` elementu:

 ![Obrázek, který znázorňuje šipky vykreslené pomocí elementu Path.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)  
  
 A jsou dva příklady použití .<xref:System.Windows.FlowDirection> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Image> <xref:System.Windows.Shapes.Path> Vedle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rozložení prvků v určitém směru v rámci <xref:System.Windows.FlowDirection> kontejneru lze použít s prvky, jako je například <xref:System.Windows.Controls.InkPresenter> vykreslí rukopis na povrchu, <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Kdykoli budete potřebovat právo k levému chování obsahu, který napodobuje chování zleva doprava nebo naopak, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje tuto schopnost.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Nahrazování čísel  
 Historicky se [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] zavedlo substituce čísel tím, že umožňuje reprezentace různých kulturních tvarů pro stejné číslice a přitom zachovat interní úložiště těchto číslic v různých národních prostředích, jako jsou například čísla uložená v jejich dobře známé hexadecimální hodnoty, 0x40, 0x41, ale zobrazeny podle vybraného jazyka.  
  
 To umožňuje aplikacím zpracovávat číselné hodnoty, aniž by je museli převést z jednoho jazyka na jiný, například uživatel může otevřít [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] tabulku v lokalizované arabštině [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a zobrazit čísla v arabštině, ale otevřít ji v Evropská verze [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] nástroje a viz Evropské vyjádření stejných čísel. To je také nutné pro jiné symboly, jako jsou oddělovače čárky a symbol procenta, protože obvykle doprovázejí čísla ve stejném dokumentu.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]pokračuje v rámci stejné tradice a přidá další podporu pro tuto funkci, která umožňuje větší kontrolu nad tím, kdy a jak se použije náhrada. I když je tato funkce navržena pro libovolný jazyk, je zvláště užitečná v obousměrném obsahu, kde tvarování číslic pro určitý jazyk je obvykle výzvou pro vývojáře aplikací z důvodu různých kultur, na kterých může aplikace běžet.  
  
 Základní vlastnost řídící, jak nahrazování čísel funguje v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] rámci, <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> je vlastnost závislosti. <xref:System.Windows.Media.NumberSubstitution> Třída určuje, jak se mají zobrazovat čísla v textu. Má tři veřejné vlastnosti, které definují jeho chování. Následuje souhrn každé z vlastností.  
  
 **CultureSource:**  
  
 Tato vlastnost určuje, jak je určena jazyková verze pro čísla. Přebírá jednu ze tří <xref:System.Windows.Media.NumberCultureSource> hodnot výčtu.  
  
- Prioritu Jazyková verze Number je <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> vlastnost.  
  
- Text: Číslo jazykové verze je jazyková verze běhu textu. V označení by to `xml:lang`byla nebo jeho vlastnost aliasu `Language` (<xref:System.Windows.FrameworkElement.Language%2A> nebo <xref:System.Windows.FrameworkContentElement.Language%2A>). Také je výchozím nastavením pro třídy, které jsou odvozeny <xref:System.Windows.FrameworkContentElement>z. Takové třídy zahrnují <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType> <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, atakdále.<xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>  
  
- Uživatelský Číslo jazykové verze je jazyková verze aktuálního vlákna. Tato vlastnost je výchozím nastavením pro všechny podtřídy <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> jako jsou a <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride**:  
  
 Vlastnost se používá pouze v případě, <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> že je vlastnost nastavena <xref:System.Windows.Media.NumberCultureSource.Override> na hodnotu a je ignorována v opačném případě. <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> Určuje číselnou verzi. Hodnota `null`, výchozí hodnota, je interpretována jako en-US.  
  
 **Nahrazení**:  
  
 Tato vlastnost určuje typ nahrazování čísla, který má být proveden. Používá jednu z následujících <xref:System.Windows.Media.NumberSubstitutionMethod> hodnot výčtu:  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: Substituční metoda je určena na základě <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> vlastnosti číselné jazykové verze. Toto nastavení je výchozí.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Pokud je jazyková verze číselná nebo Perština, určuje, že číslice závisí na kontextu.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Číslice se vždycky vykreslují jako Evropské číslice.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Čísla se vykreslují pomocí národních číslic pro číslo jazykové verze, jak je určeno v jazykové <xref:System.Globalization.CultureInfo.NumberFormat%2A>verzi.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Čísla se vykreslují pomocí tradičních číslic pro jazykovou verzi. Pro většinu jazykových verzí je to stejné jako <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. Výsledkem ale <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> jsou číslice latinky pro některé Arabské jazykové verze, zatímco tato hodnota má za následek arabské číslice pro všechny Arabské jazykové verze.  
  
 Co tyto hodnoty znamenají pro vývojáře s obousměrným obsahem? Ve většině případů může vývojář potřebovat definovat <xref:System.Windows.FlowDirection> a jazyk každého textového [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvku <xref:System.Windows.Media.NumberSubstitution> , například `Language="ar-SA"` a logika se postará o zobrazení čísel podle správné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]hodnoty. Následující příklad ukazuje použití arabských a anglické číslice v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikaci běžící v arabštině verze systému. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]  
  
 [!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 Následující obrázek ukazuje výstup předchozí ukázky, pokud používáte arabskou verzi Windows s zobrazenými arabskými a anglickými čísly:

 ![Obrázek zobrazující arabské a anglické číslo.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)  
  
 V <xref:System.Windows.FlowDirection> tomto případě bylo důležité, protože <xref:System.Windows.FlowDirection> nastavení na <xref:System.Windows.FlowDirection.LeftToRight> místo toho způsobilo, že by byly získány Evropské číslice. Následující části popisují, jak mít v celém dokumentu jednotný displej číslic. Pokud tento příklad není v arabštině Windows spuštěný, všechny číslice se zobrazí jako Evropské číslice.  
  
 **Definování pravidel nahrazení**  
  
 V reálné aplikaci může být potřeba nastavit jazyk programově. Například chcete nastavit `xml:lang` atribut tak, aby byl stejný jako ten [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], který používá systém, nebo možná změnit jazyk v závislosti na stavu aplikace.  
  
 Pokud chcete provádět změny v závislosti na stavu aplikace, využijte jiné funkce, které [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje.  
  
 Nejprve nastavte komponentu `NumberSubstitution.CultureSource="Text"`aplikace. Pomocí tohoto nastavení je zajištěno, že nastavení nepochází z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvků textu, které mají jako výchozí hodnotu "uživatel", <xref:System.Windows.Controls.TextBlock>například.  
  
Příklad:  

```xaml  
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

V příslušném C# kódu nastavte `Language` vlastnost například na `"ar-SA"`.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Pokud potřebujete nastavit `Language` vlastnost na jazyk uživatelského rozhraní aktuálního uživatele, použijte následující kód.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>představuje aktuální jazykovou verzi použitou aktuálním vláknem v době běhu.  
  
 Konečný [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] příklad by měl být podobný následujícímu příkladu.  
  
 [!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 Konečný C# příklad by měl být podobný následujícímu.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 Následující obrázek ukazuje, jak okno vypadá v programovacím jazyce a zobrazuje arabské číslice:
     
 ![Obrázek, který zobrazuje arabské číslice.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)  
  
 **Použití vlastnosti Substitution**  
  
 Způsob nahrazení čísel funguje v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] závislosti na jazyku textového prvku a jeho <xref:System.Windows.FlowDirection>typu. <xref:System.Windows.FlowDirection> Pokud je zleva doprava, vykreslí se Evropské číslice. Pokud je však před ním uveden arabský text nebo má jazyk nastavený na ar <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection.RightToLeft>, jsou místo toho vykreslovány arabské číslice.  
  
 V některých případech ale možná budete chtít vytvořit sjednocenou aplikaci, například Evropské číslice pro všechny uživatele. Nebo arabské číslice v <xref:System.Windows.Documents.Table> buňkách s určitou <xref:System.Windows.Style>příponou. Jedním jednoduchým způsobem, jak to udělat, <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> je použití vlastnosti.  
  
 V následujícím příkladu nemá první <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> vlastnost nastavenou, takže algoritmus zobrazuje arabské číslice podle očekávání. V druhé <xref:System.Windows.Controls.TextBlock>je ale náhrada nastavená na evropské přepsání výchozí náhrady pro arabské číslice a zobrazí se Evropské číslice.  
  
 [!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
