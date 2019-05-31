---
title: Obousměrné funkce v přehledu WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: a3a991a841182438dca4ef0a4067d333180f4f60
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380184"
---
# <a name="bidirectional-features-in-wpf-overview"></a>Obousměrné funkce v přehledu WPF
Na rozdíl od jiných vývojovou platformu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje mnoho funkcí, které podporují rychlý vývoj obousměrné obsah, například smíšené zleva doprava a klikněte pravým tlačítkem myši na zbývající data ve stejném dokumentu. Ve stejnou dobu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvoří skvělé prostředí pro uživatele, kteří vyžadují obousměrné funkce, jako je arabština nebo hebrejština mluvený uživatelů.  
  
 Následující části popisují mnoho obousměrné funkce spolu s příklady znázorňující způsob k dosažení nejlepšího zobrazení obsahu obousměrné. Většina ukázek používá [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], i když můžete snadno použít koncepty C# nebo kódu jazyka Visual Basic.  

<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 Základní vlastnost, která definuje směr tok obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace je <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Tuto vlastnost lze nastavit na jednu ze dvou hodnot výčtu, <xref:System.Windows.FlowDirection.LeftToRight> nebo <xref:System.Windows.FlowDirection.RightToLeft>. Vlastnost je k dispozici všem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky, které dědí <xref:System.Windows.FrameworkElement>.  
  
 Následující příklady nastavují směr toku <xref:System.Windows.Controls.TextBox> elementu.  
  
 **Směr zleva doprava**  
  
 [!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Směr zprava doleva**  
  
 [!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 Následující obrázek ukazuje, jak předchozí kód vykreslí.  
    
 ![Obrázek, který ukazuje směry různých toku.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)  
  
 Prvek v rámci [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] stromu zdědí <xref:System.Windows.FrameworkElement.FlowDirection%2A> ze svého kontejneru. V následujícím příkladu <xref:System.Windows.Controls.TextBlock> se nachází uvnitř <xref:System.Windows.Controls.Grid>, který se nachází v <xref:System.Windows.Window>. Nastavení <xref:System.Windows.FrameworkElement.FlowDirection%2A> pro <xref:System.Windows.Window> zahrnuje nastavení pro <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Controls.TextBlock> také.  
  
 Následující příklad ukazuje nastavení <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 Na nejvyšší úrovni <xref:System.Windows.Window> má <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>, takže všechny prvky, které jsou v něm obsažena také dědí stejné <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Pro element, který má zadané přepsání <xref:System.Windows.FrameworkElement.FlowDirection%2A> ho musí přidat explicitní směr změnu, jako je například druhý <xref:System.Windows.Controls.TextBlock> v předchozím příkladem, kdy se změní na <xref:System.Windows.FlowDirection.LeftToRight>. Pokud ne <xref:System.Windows.FrameworkElement.FlowDirection%2A> je definován výchozí <xref:System.Windows.FlowDirection.LeftToRight> platí.  
  
 Následující obrázek znázorňuje výstup z předchozího příkladu:

 ![Obrázek, který znázorňuje směr změnu explicitní toku.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)  

<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Mnoho vývojových platformách, jako [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)], [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] a Java poskytuje zvláštní podporu pro vývoj obsahu obousměrné. Značkovacích jazycích, jako [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] poskytnout obsahu zapisovače potřebné značky k zobrazení textu v požadovaném směru, například [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 značky, "dir", který přijímá jako hodnoty "rtl" nebo "ltr". Tato značka je podobný <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastností, ale <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost funguje v pokročilejší způsob, jak rozložení textový obsah a je možné pro obsah než text.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Documents.FlowDocument> všestranný [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] element, který může hostovat kombinaci textu, tabulky, obrázky a další prvky. Ukázky v následujících částech použijte tento prvek.  
  
 Přidání text, který má <xref:System.Windows.Documents.FlowDocument> lze provést více této jedním způsobem. Je jednoduchý způsob, jak to provést prostřednictvím <xref:System.Windows.Documents.Paragraph> tedy blokových element sloužící k seskupení obsahu například podle textu. Chcete-li přidat text na úrovni vložení prvky pomocí ukázky <xref:System.Windows.Documents.Span> a <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span> je určena k seskupování další prvky vložené toku na úrovni vložení obsahu elementu při <xref:System.Windows.Documents.Run> je tok, který na úrovni vložení obsahu, měla by obsahovat spuštění neformátovaný textový prvek. A <xref:System.Windows.Documents.Span> může obsahovat více <xref:System.Windows.Documents.Run> elementy.  
  
 První příklad dokumentu obsahuje dokument, který má několik síťových sdílet názvy; například `\\server1\folder\file.ext`. Určuje, zda máte tento odkaz sítě v dokumentu arabština nebo angličtina je vždy bude zobrazovat stejným způsobem. Následující obrázek znázorňuje použití elementu značky Span a zobrazuje odkaz v Arabský <xref:System.Windows.FlowDirection.RightToLeft> dokumentu:

 ![Obrázek, který znázorňuje použití Span element. ](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")  
  
 Vzhledem k tomu, že text je <xref:System.Windows.FlowDirection.RightToLeft>, všechny speciální znaky, jako "\\", oddělení textu v právo na levém pořadí. Který vede odkaz, nejsou zobrazeny ve správném pořadí, proto k vyřešení problému, text musí být vložen pro zachování samostatné <xref:System.Windows.Documents.Run> toku <xref:System.Windows.FlowDirection.LeftToRight>. Namísto toho, aby samostatné <xref:System.Windows.Documents.Run> pro jednotlivé jazyky, lepší způsob, jak problém vyřešit, je vložit méně často používané anglický text do větší arabština <xref:System.Windows.Documents.Span>.  
  
 Následující obrázek ukazuje to pomocí elementu spuštění součástí Span element:

 ![Symbol, který ukazuje spuštění prvek vložit Span element.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)  
  
 Následující příklad ukazuje použití <xref:System.Windows.Documents.Run> a <xref:System.Windows.Documents.Span> prvky v dokumentech.  
  
 [!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Elementy rozpětí  
 <xref:System.Windows.Documents.Span> Element funguje jako oddělovač hranice mezi texty s různými směry toku.  I <xref:System.Windows.Documents.Span> elementy se stejným směr toku jsou považovány za obousměrné různých oborů, což znamená, <xref:System.Windows.Documents.Span> prvky jsou uspořádány v kontejneru <xref:System.Windows.FlowDirection>, pouze obsah v rámci <xref:System.Windows.Documents.Span> – element Následuje <xref:System.Windows.FlowDirection> z <xref:System.Windows.Documents.Span>.  
  
 Následující obrázek znázorňuje směr toku několik <xref:System.Windows.Controls.TextBlock> elementy.  
    
 ![Obrázek, který ukazuje textové bloky s různými směry toku.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)  
  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Documents.Span> a <xref:System.Windows.Documents.Run> prvků, které se výsledky, jak je znázorněno na předchozím obrázku.  
  
 [!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 V <xref:System.Windows.Controls.TextBlock> prvky v ukázce <xref:System.Windows.Documents.Span> prvky jsou podrobně popsány podle <xref:System.Windows.FlowDirection> svých nadřazených složek, ale text v každé <xref:System.Windows.Documents.Span> element toky podle vlastní <xref:System.Windows.FlowDirection>. To se vztahuje na Latin a arabština – nebo jakéhokoli jiného jazyka.  
  
### <a name="adding-xmllang"></a>Přidání XML: lang  
 Následující obrázek znázorňuje další příklad, který se používá jako čísla a aritmetických výrazech `"200.0+21.4=221.4"`. Všimněte si, že pouze <xref:System.Windows.FlowDirection> nastavena.  
    
 ![Obrázek, který se zobrazí pouze FlowDirection pomocí čísla.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)  
  
 Uživatelé tuto aplikaci bude možné zklamání výstup, i když <xref:System.Windows.FlowDirection> správná čísla nejsou upravená podle Arabské čísla by měla ve tvaru.  
  
 Můžete například XAML prvky [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] atribut (`xml:lang`), který definuje jazyk jednotlivých prvků. XAML podporuje také [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Princip jazyka kterým `xml:lang` hodnoty u nadřazené elementy ve stromové struktuře používají podřízené prvky. V předchozím příkladu protože jazyk nebyl definován pro <xref:System.Windows.Documents.Run> prvek nebo některý z jeho nejvyšší úrovně prvky, výchozí `xml:lang` bylo použito, což je `en-US` pro XAML. Interní číslo tvarování algoritmus [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vybere čísla v odpovídající jazyk – v tomto případě angličtina. Ujistěte se, arabština čísel vykreslení správně `xml:lang` musí být nastavena.  
  
 Následující obrázek znázorňuje příklad s `xml:lang` přidán.  
    
 ![Grafické, který znázorňuje Arabské čísla, která tok zprava doleva.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)  
  
 Následující příklad přidá `xml:lang` do aplikace.  
  
 [!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Mějte na paměti, že mnoho jazyky mají různé `xml:lang` hodnoty v závislosti na cílové oblasti, například `"ar-SA"` a `"ar-EG"` představují dvě varianty arabština. Předchozí příklady ukazují, že budete muset definovat jak `xml:lang` a <xref:System.Windows.FlowDirection> hodnoty.  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>FlowDirection s prvky  
 <xref:System.Windows.FlowDirection> Definuje nejen tok text v textové element, ale také směr toku téměř všechny ostatní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementu. Ukazuje následující grafické <xref:System.Windows.Controls.ToolBar> , která používá vodorovnou <xref:System.Windows.Media.LinearGradientBrush> Chcete-li nakreslit jeho pozadí s levou správné přechod.  

 ![Obrázek znázorňující, panel nástrojů s zleva doprava přechodu.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)  
  
 Po nastavení <xref:System.Windows.FlowDirection> k <xref:System.Windows.FlowDirection.RightToLeft>, nejen <xref:System.Windows.Controls.ToolBar> jsou tlačítka uspořádány zprava doleva, ale i <xref:System.Windows.Media.LinearGradientBrush> změněné zarovnání jeho posuny tok zprava doleva.  
  
 Následující obrázek ukazuje přibližování <xref:System.Windows.Media.LinearGradientBrush>.  
    
 ![Obrázek znázorňující, panel nástrojů s právo na levém přechodu.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)  
  
 Kreslení v následujícím příkladu <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>. (Nakreslete vlevo doprava, odeberte <xref:System.Windows.FlowDirection> atribut na <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>FlowDirection výjimky  
 Existuje několik případů kde <xref:System.Windows.FlowDirection> nechová podle očekávání. Tato část popisuje dva z těchto výjimek.  
  
 **Obrázek**  
  
 <xref:System.Windows.Controls.Image> Představuje ovládací prvek, který zobrazí obrázek. V [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] jde použít s <xref:System.Windows.Controls.Image.Source%2A> vlastnost, která definuje [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] z <xref:System.Windows.Controls.Image> k zobrazení.  
  
 Na rozdíl od jiných [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky, <xref:System.Windows.Controls.Image> nedědí <xref:System.Windows.FlowDirection> z kontejneru. Ale pokud <xref:System.Windows.FlowDirection> nastavený explicitně na <xref:System.Windows.FlowDirection.RightToLeft>, <xref:System.Windows.Controls.Image> zobrazený Vodorovně obráceně. To je implementováno jako praktické funkce pro vývojáře obousměrné obsahu; vzhledem k tomu, že v některých případech se vytvoří vodorovně překlopení obrázku požadovaný efekt.  
  
 Následující obrázek znázorňuje přetočený <xref:System.Windows.Controls.Image>.  
    
 ![Obrázek, který znázorňuje přetočený obrázek.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)  
  
 Následující příklad ukazuje, že <xref:System.Windows.Controls.Image> nepodaří dědit <xref:System.Windows.FlowDirection> z <xref:System.Windows.Controls.StackPanel> , který jej obsahuje. **Poznámka:** musí mít soubor s názvem **ms_logo.jpg** na vaše C:\ jednotky spuštění tohoto příkladu.  
  
 [!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Poznámka:** zahrnuté v souborech ke stažení je **ms_logo.jpg** souboru. Kód předpokládá, že je soubor .jpg ne uvnitř projektu, ale někam na jednotce C:\. Musíte zkopírovat .jpg ze souborů projektu na jednotce C:\ nebo změnou kódu vyhledejte soubor v projektu. Chcete-li provést tuto změnu `Source="file://c:/ms_logo.jpg"` k `Source="ms_logo.jpg"`.  
  
 **Cesty**  
  
 Kromě <xref:System.Windows.Controls.Image>, je jiný element zajímavé <xref:System.Windows.Shapes.Path>. Cesta je objekt, který lze nakreslit řadu připojené čar a křivek. Se chová způsobem, který je podobný <xref:System.Windows.Controls.Image> týkající se jeho <xref:System.Windows.FlowDirection>, třeba jeho <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> vodorovné odráží její <xref:System.Windows.FlowDirection.LeftToRight> jeden. Ale na rozdíl od <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> dědí její <xref:System.Windows.FlowDirection> z kontejneru a ten není potřeba explicitně zadat.  
  
 Následující příklad nakreslí jednoduchý šipku pomocí 3 řádky. Na první šipku dědí <xref:System.Windows.FlowDirection.RightToLeft> směr z toku <xref:System.Windows.Controls.StackPanel> tak, aby jeho počátečního a koncového bodu se měří z kořenového adresáře na pravé straně. Druhá šipka, který má explicitní <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> také začne na pravé straně. Třetí šipka má ale jeho výchozí kořenové složky na levé straně. Další informace o vykreslování viz <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.GeometryGroup>.  
  
 [!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 Následující obrázek znázorňuje výstup z předchozího příkladu s vykresleno pomocí šipky `Path` element:

 ![Grafické, které ukazují vykreslen Path element šipky.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)  
  
 <xref:System.Windows.Controls.Image> a <xref:System.Windows.Shapes.Path> jsou dva příklady o tom [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] používá <xref:System.Windows.FlowDirection>. Vedle vytváření rozložení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvků v konkrétní směr v rámci kontejneru, <xref:System.Windows.FlowDirection> lze použít s prvky, jako <xref:System.Windows.Controls.InkPresenter> které vykreslí rukopis na povrchu, <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Pokaždé, když potřebujete právo na levém chování pro obsah, který napodobuje zleva doprava chování, nebo naopak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje tuto funkci.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Číslo nahrazení  
 V minulosti [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] obsahoval podporované číslo nahrazení tím, že znázornění různých tvarů jazykové verze pro stejné číslic a zajistit přitom ochranu interní úložiště tyto číslice unified mezi různá národní prostředí pro příklady čísel jsou uloženy v jejich dobře známé šestnáctkových hodnot, 0x40, 0x41, ale zobrazeného podle vybraný jazyk.  
  
 To je povoleno aplikace ke zpracování číselných hodnot, aniž by bylo nutné je převést z jednoho jazyka do druhého, například může uživatel otevřít [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] tabulky v lokalizovaných arabština [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a zobrazit čísla ve tvaru v arabštině, ale jej otevřít v Evropská verzi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a podívejte se, Evropského reprezentace stejná čísla. To je také nutné pro další symboly, jako je oddělovací čárky a procento symbol, protože jsou obvykle připojeny čísla ve stejném dokumentu.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pokračuje v tradici stejné a přidává další podporu pro tuto funkci, která umožní další kontrola uživatele nad kdy a jak se používá nahrazení. Zatímco tato funkce je navržená pro libovolný jazyk, je to užitečné zejména v obousměrné obsahu, kde tvarování čísla linky pro konkrétní jazyk obvykle představuje výzvu pro vývojáře aplikací z důvodu různé jazykové verze, které v můžou spouštět aplikace.  
  
 Základní vlastnosti řízení jak číslo nahrazení funguje v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> vlastnost závislosti. <xref:System.Windows.Media.NumberSubstitution> Třída určuje, jak mají být zobrazeny čísla v textu. Má tři veřejné vlastnosti, které definují chování aplikace. Toto je souhrn všech vlastností.  
  
 **CultureSource:**  
  
 Tato vlastnost určuje, jak se určuje jazykovou verzi pro čísla. Bude mít jednu ze tří <xref:System.Windows.Media.NumberCultureSource> hodnot výčtu.  
  
- Přepsání: Číslo jazykovou verzi je <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> vlastnost.  
  
- Text: Číslo jazyková verze představuje jazykovou verzi textu spustit. Ve značce, to může být `xml:lang`, nebo její alias `Language` vlastnosti (<xref:System.Windows.FrameworkElement.Language%2A> nebo <xref:System.Windows.FrameworkContentElement.Language%2A>). Je také na výchozí hodnoty pro třídy odvozené od <xref:System.Windows.FrameworkContentElement>. Tyto třídy zahrnují <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> a tak dále.  
  
- Uživatel: Číslo jazykovou verzi je jazykové verze aktuálního vlákna. Tato vlastnost je výchozí nastavení pro všechny dílčí <xref:System.Windows.FrameworkElement> například <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> a <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride**:  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> Vlastnost se používá jenom v případě <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> je nastavena na <xref:System.Windows.Media.NumberCultureSource.Override> a v opačném případě se ignoruje. Určuje číslo jazykovou verzi. Hodnota `null`, výchozí hodnota je interpretován jako en US.  
  
 **Nahrazení**:  
  
 Tato vlastnost určuje typ čísla nahrazení provádět. Bude mít jednu z následujících <xref:System.Windows.Media.NumberSubstitutionMethod> hodnot výčtu:  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: Metoda nahrazení závisí na číslo jazykovou verzi <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> vlastnost. Toto nastavení je výchozí.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Pokud číslo jazykovou verzi je arabština nebo perština jazykové verze, určuje, že číslice závisí na kontextu.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Čísla jsou vždy vykresleny jako Evropské číslice.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Čísla jsou vykreslovány pomocí národní číslic čísla jazykové verze, jak jsou určené pro jazykovou verzi <xref:System.Globalization.CultureInfo.NumberFormat%2A>.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Čísla jsou vykreslovány pomocí tradiční číslic čísla jazykové verze. Pro většinu jazykové verze, to je stejný jako <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. Ale <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> výsledkem latinky číslic pro některé Arabské jazykové verze, že tato hodnota vede Arabské čísla linky pro všechny Arabské jazykové verze.  
  
 Co znamenají tyto hodnoty pro obousměrné obsahu pro vývojáře? Ve většině případů vývojář potřebovat pouze k definování <xref:System.Windows.FlowDirection> a jazyk každý textové [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvek, například `Language="ar-SA"` a <xref:System.Windows.Media.NumberSubstitution> logiky postará o zobrazování čísel podle správné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Následující příklad ukazuje použití arabština a angličtině čísla v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikaci spuštěnou na platformě arabské verzi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 Následující obrázek znázorňuje výstup v předchozím příkladu, pokud máte spuštěný v Arabská verzi systému Windows s čísly arabština a angličtině zobrazí:

 ![Obrázek znázorňující, arabština a angličtině čísla.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)  
  
 <xref:System.Windows.FlowDirection> Byl důležité v tomto případě, protože nastavení <xref:System.Windows.FlowDirection> k <xref:System.Windows.FlowDirection.LeftToRight> místo toho by jste obdrželi Evropské číslice. Následující části popisují, jak vám má jednotné zobrazení číslic v celém dokumentu. Pokud v tomto příkladu není spuštěna na Windows arabština, zobrazí všechny číslice jako Evropské číslice.  
  
 **Definování pravidla nahrazení**  
  
 V reálné aplikaci můžete potřebovat nastavit jazyk prostřednictvím kódu programu. Můžete třeba nastavit `xml:lang` atribut stejně jako jste použili v systému [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], nebo možná změnit jazyk v závislosti na stavu aplikace.  
  
 Pokud chcete provést změny podle stavu aplikace, ujistěte se, použití jiné funkce poskytované službou [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Nejprve nastavte součást aplikace `NumberSubstitution.CultureSource="Text"`. Použití tohoto nastavení zajišťuje, že nastavení nepochází z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro textové prvky, které mají "User" jako výchozí, jako například <xref:System.Windows.Controls.TextBlock>.  
  
Příklad:  

```xaml  
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

Do odpovídajícího C# kódu, nastavte `Language` vlastnosti, například `"ar-SA"`.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Pokud je nutné nastavit `Language` vlastnost jazyk uživatelského prostředí aktuálního uživatele použijte následující kód.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> představuje aktuální jazykovou verzi používané aktuální vlákno v době běhu.  
  
 Výsledná [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] příkladu by měl vypadat přibližně jako v následujícím příkladu.  
  
 [!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 Výsledná C# by měl být podobný následujícímu příkladu.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 Následující obrázek znázorňuje vypadá okno pro buď programovací jazyk zobrazení Arabské čísel:
     
 ![Obrázek zobrazující Arabské čísla.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)  
  
 **Pomocí vlastnosti nahrazení**  
  
 Funguje stejně, jako číslo nahrazení [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] závisí na jazyku text prvku a jeho <xref:System.Windows.FlowDirection>. Pokud <xref:System.Windows.FlowDirection> zleva doprava, pak jsou generovány Evropské číslice. Nicméně pokud mu předchází arabštině, nebo má jazyk nastavena na "ar" a <xref:System.Windows.FlowDirection> je <xref:System.Windows.FlowDirection.RightToLeft>, arabské číslic místo vykreslení.  
  
 V některých případech však můžete chtít vytvořit jednotný aplikaci, například Evropské číslice pro všechny uživatele. Nebo arabské číslic v <xref:System.Windows.Documents.Table> buňky s konkrétním <xref:System.Windows.Style>. Jeden snadný způsob, jak provést, která používá <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> vlastnost.  
  
 V následujícím příkladu první <xref:System.Windows.Controls.TextBlock> nemá <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> vlastnost nastavena, aby algoritmus zobrazoval Arabské číslic podle očekávání. Nicméně v druhém <xref:System.Windows.Controls.TextBlock>, nahrazení je nastavena na evropské přepisuje výchozí nahrazení Arabské čísel a Evropském číslic zobrazovaných.  
  
 [!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
