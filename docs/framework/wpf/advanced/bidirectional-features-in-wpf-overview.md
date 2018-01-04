---
title: "Obousměrné funkce v přehledu WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b50d98d5f02a59a013d7577f0e312e6ffde35690
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="bidirectional-features-in-wpf-overview"></a>Obousměrné funkce v přehledu WPF
Na rozdíl od jiných vývoj platformy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má řadu funkcí, které podporují rychlý vývoj obousměrného obsahu, například smíšený zleva doprava a přímo na zbývajících dat ve stejném dokumentu. Ve stejnou dobu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvoří vynikající prostředí pro uživatele, kteří vyžadují obousměrné funkce, jako je arabština a hebrejština mluvení uživatele.  
  
 Následující části popisují mnoho funkcí obousměrného společně s příklady znázorňující způsob k dosažení nejlepšího zobrazení obousměrného obsahu. Většina ukázky používá [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], i když můžete snadno použít koncepty [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] nebo [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] kódu.  
  

  
<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 Základní vlastnosti, která definuje směr toku obsahu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace je <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Tuto vlastnost lze nastavit pro jednu ze dvou hodnot výčtu, <xref:System.Windows.FlowDirection.LeftToRight> nebo <xref:System.Windows.FlowDirection.RightToLeft>. Vlastnost je k dispozici všem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy, které dědí od <xref:System.Windows.FrameworkElement>.  
  
 Následující příklady nastavte směr toku <xref:System.Windows.Controls.TextBox> elementu.  
  
 **Směr toku zleva doprava**  
  
 [!code-xaml[LTRRTL#LTR](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Směr toku zprava doleva**  
  
 [!code-xaml[LTRRTL#RTL](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 Následující obrázek ukazuje, jak vykreslí předchozí kód.  
  
 **Obrázek, který znázorňuje FlowDirection**  
  
 ![Zarovnání TextBlock](../../../../docs/framework/wpf/advanced/media/lefttorightrighttoleft.PNG "LefttoRightRighttoLeft")  
  
 Prvek v rámci [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] stromu zdědí <xref:System.Windows.FrameworkElement.FlowDirection%2A> z jeho kontejneru. V následujícím příkladu <xref:System.Windows.Controls.TextBlock> je uvnitř <xref:System.Windows.Controls.Grid>, který se nachází v <xref:System.Windows.Window>. Nastavení <xref:System.Windows.FrameworkElement.FlowDirection%2A> pro <xref:System.Windows.Window> znamená pro jeho nastavení <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Controls.TextBlock> také.  
  
 Následující příklad ukazuje nastavení <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xaml[FlowDirection#FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 Nejvyšší úrovně <xref:System.Windows.Window> má <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>, takže všechny elementy, které jsou v něm obsažena také zdědit stejné <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Pro element k přepsání zadané <xref:System.Windows.FrameworkElement.FlowDirection%2A> se musí přidat změnu explicitní směr, jako je například druhý <xref:System.Windows.Controls.TextBlock> v předchozím příkladu, který se změní na <xref:System.Windows.FlowDirection.LeftToRight>. Pokud ne <xref:System.Windows.FrameworkElement.FlowDirection%2A> je definován výchozí <xref:System.Windows.FlowDirection.LeftToRight> platí.  
  
 Následující obrázek ukazuje výstup předchozí příklad.  
  
 **Obrázek, který znázorňuje explicitně přiřazené FlowDirection**  
  
 ![Obrázek směr toku](../../../../docs/framework/wpf/advanced/media/flowdir.PNG "FlowDir")  
  
<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Mnoho vývojové platformy jako [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)], [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] a Java poskytovat zvláštní podporu pro vývoj obousměrného obsahu. Jazyky značek jako [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] poskytnout obsahu zapisovače potřebné značky k zobrazení textu v požadovaném směru, například [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 štítek, "dir", která přebírá "rtl" nebo "ltr" jako hodnoty. Tato značka je podobná <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost, ale <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost funguje způsobem pokročilejší textový obsah rozložení a lze použít pro obsah než text.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Documents.FlowDocument> je všestranné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] element, který může hostovat kombinaci text, tabulky, obrázky a další prvky. Ukázky v následujících částech použijte tento element.  
  
 Přidávání textu k <xref:System.Windows.Documents.FlowDocument> lze provést více této jedním způsobem. Je jednoduchý způsob, jak to provést prostřednictvím <xref:System.Windows.Documents.Paragraph> tedy element na úrovni bloku použít k seskupení obsahu například textu. Přidat text do elementů na úrovni ukázky použití <xref:System.Windows.Documents.Span> a <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span>je vložené úrovni tok obsahu elementu používají k seskupování jiných vložených elementů, zatímco <xref:System.Windows.Documents.Run> je tok vložené úrovni obsahu určený element tak, aby obsahovala spustit neformátovaný text. A <xref:System.Windows.Documents.Span> může obsahovat více <xref:System.Windows.Documents.Run> elementy.  
  
 V prvním příkladu dokument obsahuje dokument, který má číslo sítě sdílet názvů; například `\\server1\folder\file.ext`. Máte-li tento odkaz sítě v dokumentu arabské nebo angličtina je vždy bude zobrazovat stejným způsobem. Následující obrázek zobrazuje odkaz v Arabský <xref:System.Windows.FlowDirection.RightToLeft> dokumentu.  
  
 **Obrázek, který znázorňuje použití Span Element**  
  
 ![Dokument s tokem zprava doleva](../../../../docs/framework/wpf/advanced/media/flowdocument.PNG "FlowDocument")  
  
 Vzhledem k tomu, že je text <xref:System.Windows.FlowDirection.RightToLeft>, všechny speciální znaky, jako například "\\", oddělte textu v práva k levé pořadí. Který výsledkem odkazu není zobrazen ve správném pořadí, proto problém vyřešit, text musí být vložený zachovat samostatné <xref:System.Windows.Documents.Run> toku <xref:System.Windows.FlowDirection.LeftToRight>. Místo nutnosti samostatné <xref:System.Windows.Documents.Run> pro každý jazyk, je lepší způsob, jak vyřešit problém pro vložení méně často používaných anglické text do větší arabské <xref:System.Windows.Documents.Span>.  
  
 To je znázorněný na následujícím obrázku.  
  
 **Obrázek, který znázorňuje použití spuštění elementu vložených v Span Element**  
  
 ![XamlPad – snímek obrazovky](../../../../docs/framework/wpf/advanced/media/runspan.PNG "RunSpan")  
  
 Následující příklad ukazuje, jak pomocí <xref:System.Windows.Documents.Run> a <xref:System.Windows.Documents.Span> prvky v dokumentech.  
  
 [!code-xaml[RunSpan#RunSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Span elementy  
 <xref:System.Windows.Documents.Span> Element funguje jako oddělovač hranice mezi texty s různými směry toku.  I <xref:System.Windows.Documents.Span> elementů pomocí stejné směr toku jsou považovány za jiný obousměrného obory, které znamená, které <xref:System.Windows.Documents.Span> prvky jsou uspořádány v kontejneru <xref:System.Windows.FlowDirection>, pouze obsah, v rámci <xref:System.Windows.Documents.Span> – element Následuje <xref:System.Windows.FlowDirection> z <xref:System.Windows.Documents.Span>.  
  
 Následující obrázek znázorňuje směr toku několik <xref:System.Windows.Controls.TextBlock> elementy.  
  
 **Obrázek, který znázorňuje FlowDirection v několika TextBlock elementy**  
  
 ![Text bloky s různými směry toku](../../../../docs/framework/wpf/advanced/media/span.PNG "rozpětí")  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Documents.Span> a <xref:System.Windows.Documents.Run> elementy nepřineslo výsledky ukazuje předchozí obrázek.  
  
 [!code-xaml[Span#Span](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 V <xref:System.Windows.Controls.TextBlock> elementy v ukázce <xref:System.Windows.Documents.Span> elementy jsou nastíněny podle <xref:System.Windows.FlowDirection> svých nadřazených složek, ale text v každém <xref:System.Windows.Documents.Span> element toky podle vlastní <xref:System.Windows.FlowDirection>. To se vztahuje na Latin a arabské – a dalších jazyků.  
  
### <a name="adding-xmllang"></a>Přidání XML: lang  
 Následující obrázek ukazuje další příklad, který používá čísla a aritmetických výrazech, například `"200.0+21.4=221.4"`. Všimněte si pouze <xref:System.Windows.FlowDirection> nastavena.  
  
 **Grafické, který zobrazí pouze FlowDirection pomocí čísla**  
  
 ![Čísla, která toku zprava doleva](../../../../docs/framework/wpf/advanced/media/langattribute.PNG "LangAttribute")  
  
 Uživatelé této aplikace bude možné Zklamaný výstup, i když <xref:System.Windows.FlowDirection> je správný, čísla, která nejsou ve tvaru, jako by měl být ve tvaru Arabic čísla.  
  
 Může zahrnovat elementů XAML [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] atribut (`xml:lang`), který definuje jazyk jednotlivých prvků. Také podporuje XAML [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] jazyk Princip které `xml:lang` hodnoty u nadřazené elementy ve stromové struktuře používají podřízené elementy. V předchozím příkladu protože jazyk nebyl definován pro <xref:System.Windows.Documents.Run> element ani žádnou její horní úrovni elementy, výchozí `xml:lang` byl použit, což je `en-US` pro jazyk XAML. Interní číslo tvarování algoritmus [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vybere čísla v jazyce, odpovídající – v tomto případě anglické. Chcete-li pro arabštinu čísla vykreslení správně `xml:lang` je třeba nastavit.  
  
 Následující obrázek ukazuje příklad s `xml:lang` přidat.  
  
 **Grafika, ukazuje použití atributu XML: lang**  
  
 ![Arabské číslice s tokem zprava doleva](../../../../docs/framework/wpf/advanced/media/langattribute2.PNG "LangAttribute2")  
  
 Následující příklad přidá `xml:lang` do aplikace.  
  
 [!code-xaml[LangAttribute#LangAttribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Mějte na paměti, mnoha jazycích mají různé `xml:lang` hodnoty v závislosti na cílové oblasti, například `"ar-SA"` a `"ar-EG"` představují dvě varianty Arabské. Předchozí příklady ilustrují, budete muset definovat jak `xml:lang` a <xref:System.Windows.FlowDirection> hodnoty.  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>FlowDirection s elementy bez textu  
 <xref:System.Windows.FlowDirection>definuje, ne jenom tok textu v textové elementu, ale také směr toku téměř každé jiné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementu. Následující grafické ukazuje <xref:System.Windows.Controls.ToolBar> , který používá vodorovných <xref:System.Windows.Media.LinearGradientBrush> k vykreslení jeho pozadí.  
  
 **Grafické, který zobrazí panel nástrojů s zleva doprava přechodu**  
  
 ![Přechod – snímek obrazovky](../../../../docs/framework/wpf/advanced/media/gradient.PNG "přechodu")  
  
 Po nastavení <xref:System.Windows.FlowDirection> k <xref:System.Windows.FlowDirection.RightToLeft>, nejen <xref:System.Windows.Controls.ToolBar> tlačítka jsou uspořádána zprava doleva, ale i <xref:System.Windows.Media.LinearGradientBrush> změněné zarovnání jeho posuny, které jsou předávány zprava doleva.  
  
 Následující obrázek ukazuje přibližování <xref:System.Windows.Media.LinearGradientBrush>.  
  
 **Obrázek, který ukazuje panel nástrojů se právo na levém přechodu**  
  
 ![Přechod s tokem zprava doleva](../../../../docs/framework/wpf/advanced/media/gradient2-wpf.PNG "Gradient2_WPF")  
  
 Následující příklad nevykresluje <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>. (K vykreslení ho zleva doprava, odeberte <xref:System.Windows.FlowDirection> atributu u <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[Gradient#Gradient](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>FlowDirection výjimky  
 Existuje několik případů kde <xref:System.Windows.FlowDirection> není chovat podle očekávání. Tato část obsahuje dva tyto výjimky.  
  
 **Obrázek**  
  
 <xref:System.Windows.Controls.Image> Reprezentuje ovládací prvek, který zobrazuje bitovou kopii. V [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] dá použít s <xref:System.Windows.Controls.Image.Source%2A> vlastnost, která definuje [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] z <xref:System.Windows.Controls.Image> k zobrazení.  
  
 Na rozdíl od jiných [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementů <xref:System.Windows.Controls.Image> nedědí <xref:System.Windows.FlowDirection> z kontejneru. Ale pokud <xref:System.Windows.FlowDirection> nastavena explicitně na <xref:System.Windows.FlowDirection.RightToLeft>, <xref:System.Windows.Controls.Image> se zobrazí vodorovně obráceně. Tato možnost je implementovaná jako pohodlné funkce pro vývojáře obousměrného obsahu; protože v některých případech vodorovně překlopení obrázku vytváří očekávaný výsledek.  
  
 Následující obrázek ukazuje přetočený <xref:System.Windows.Controls.Image>.  
  
 **Obrázek, který znázorňuje Přetočený obrázek**  
  
 ![XamlPad – snímek obrazovky](../../../../docs/framework/wpf/advanced/media/image.PNG "bitové kopie")  
  
 Následující příklad ukazuje, který <xref:System.Windows.Controls.Image> nepodaří dědění <xref:System.Windows.FlowDirection> z <xref:System.Windows.Controls.StackPanel> který ji obsahuje. **Poznámka:** musí mít soubor s názvem **ms_logo.jpg** na jednotce C:\ pro spuštění tohoto příkladu.  
  
 [!code-xaml[Image#Image](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Poznámka:** je zahrnuté v stažení souborů **ms_logo.jpg** souboru. Kód předpokládá, že se soubor .jpg mimo projektu, ale místo na jednotce C:\. Musíte zkopírovat .jpg z projektu souborů na jednotce C:\ nebo změnit kód a hledat v souboru v projektu. Chcete tuto změnu `Source="file://c:/ms_logo.jpg"` k `Source="ms_logo.jpg"`.  
  
 **Cesty**  
  
 Kromě <xref:System.Windows.Controls.Image>, je jiný zajímavé element <xref:System.Windows.Shapes.Path>. Cestu je objekt, který může kreslení řadu připojené čar a křivek. Se chová podobně jako způsobem <xref:System.Windows.Controls.Image> ohledně jeho <xref:System.Windows.FlowDirection>, třeba jeho <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> je vodorovné zrcadlením jeho <xref:System.Windows.FlowDirection.LeftToRight> jeden. Ale na rozdíl od <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> dědí jeho <xref:System.Windows.FlowDirection> z kontejneru a jeden není nutné explicitně zadat.  
  
 Následující příklad nakreslí jednoduchý šipku pomocí 3 řádky. Na první šipku dědí <xref:System.Windows.FlowDirection.RightToLeft> směr z toku <xref:System.Windows.Controls.StackPanel> tak, aby jeho počáteční a koncový bod se měří z kořenového adresáře na pravé straně. Na druhé šipku, která má explicitní <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> také spustí na pravé straně. Na třetí šipku však má svůj počáteční kořen na levé straně. Další informace o kreslení najdete <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.GeometryGroup>.  
  
 [!code-xaml[Paths#Paths](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 Následující obrázek ukazuje výstup předchozí příklad.  
  
 **Obrázek, který znázorňuje dvojice šipek, které jsou vykreslovány pomocí Element cesty byl**  
  
 ![Cesty](../../../../docs/framework/wpf/advanced/media/paths.PNG "cesty")  
  
 <xref:System.Windows.Controls.Image> a <xref:System.Windows.Shapes.Path> jsou dva příklady jak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] používá <xref:System.Windows.FlowDirection>. Vedle položky rozložení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementů v konkrétní směr v rámci kontejneru, <xref:System.Windows.FlowDirection> lze použít s prvky, jako <xref:System.Windows.Controls.InkPresenter> které vykreslí element ink na povrchu, <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Kdykoli budete potřebovat práva k levé chování pro váš obsah, který napodobuje nalevo pravém chování, nebo naopak, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje tuto funkci.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Číslo nahrazení  
 V minulosti [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] obsahoval podporované číslo nahrazení tím, že reprezentaci různých tvarů kulturního pro stejné číslic a zachovat přitom interní úložiště těchto číslic unified mezi různá národní prostředí pro čísla příkladu jsou uložené v jejich dobře známé hexadecimální hodnoty, 0x40, 0x41, ale zobrazených podle vybraný jazyk.  
  
 To je povoleno aplikací ke zpracování číselné hodnoty, aniž by bylo nutné je převést z jednoho jazyka do druhého, například může uživatel otevřít [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] tabulky v lokalizovaných arabské [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a zobrazit čísla ve tvaru v arabština, ale otevřete ho v Evropského verzi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a zobrazit Evropského reprezentace stejná čísla. Toto je také nezbytné pro další symboly, například oddělovačů čárkami a procento symbolů, protože se obvykle doprovázet čísla ve stejném dokumentu.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]pokračuje v stejné tradici a přidává další podporu pro tuto funkci, která umožňuje více uživatelům ovládat kdy a jak se používá nahrazení. Když tato funkce je určena pro žádný jazyk, je užitečné zejména v obousměrných obsahu kde shaping čísla pro konkrétní jazyk je obvykle výzvu pro vývojáře aplikací z důvodu různé jazykové verze, které aplikace může spustit na.  
  
 Vlastnost základní řízení jak číslo nahrazení funguje v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> vlastnost závislosti. <xref:System.Windows.Media.NumberSubstitution> Třída určuje, jak jsou čísla v textu, který se má zobrazit. Má tři veřejné vlastnosti, které definují chování. Následuje souhrn každé z vlastností.  
  
 **CultureSource:**  
  
 Tato vlastnost určuje, jakým způsobem je určován jazykovou verzi pro čísla. Mezi tři trvá <xref:System.Windows.Media.NumberCultureSource> hodnot výčtu.  
  
-   Přepsání: Číslo jazykové verze je, že z <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> vlastnost.  
  
-   Text: Číslo jazyková verze je jazyková verze spustit text. V kódu, by to byl `xml:lang`, nebo jeho alias `Language` vlastnost (<xref:System.Windows.FrameworkElement.Language%2A> nebo <xref:System.Windows.FrameworkContentElement.Language%2A>). Je také výchozí hodnoty pro třídy odvozené od <xref:System.Windows.FrameworkContentElement>. Tyto třídy zahrnují <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> a tak dále.  
  
-   Uživatel: Číslo jazykové verze je jazykové verze aktuálního vlákna. Tato vlastnost je výchozí pro všechny dílčí <xref:System.Windows.FrameworkElement> například <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> a <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride**:  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> Vlastnost se používá pouze v případě <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> je nastavena na <xref:System.Windows.Media.NumberCultureSource.Override> a v opačném případě je ignorováno. Určuje číslo jazykovou verzi. Hodnota `null`, použije se výchozí hodnota je interpretována jako en US.  
  
 **Nahrazení**:  
  
 Tato vlastnost určuje typ Číslo nahrazení k provedení. Jeden z následujících trvá <xref:System.Windows.Media.NumberSubstitutionMethod> hodnot výčtu.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>Metoda: nahrazení je určen na základě číslo jazykové verze <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> vlastnost. Toto nastavení je výchozí.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Pokud je číslo jazyková verze arabské nebo fársíjština jazykové verze, určuje, že číslice záviset na kontextu.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Čísla jsou vždy se vykresluje jako Evropského číslic.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Čísla jsou vykreslovány pomocí national číslic pro číslo jazykovou verzi, podle specifikace pro jazykovou verzi <xref:System.Globalization.CultureInfo.NumberFormat%2A>.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Čísla jsou vykreslovány pomocí tradičních číslic pro číslo jazykovou verzi. Pro většinu jazykových verzí, je to stejné jako <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. Ale <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> výsledkem Latin čísla pro některé Arabic kultury, že tato hodnota vede Arabic čísla pro všechny Arabic jazykové verze.  
  
 Co znamenají tyto hodnoty pro vývojář obousměrného obsahu? Ve většině případů vývojář může být nutné jenom k definování <xref:System.Windows.FlowDirection> a jazyk každý textovou [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementu, například `Language="ar-SA"` a <xref:System.Windows.Media.NumberSubstitution> logiku postará zobrazení čísla podle správné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Následující příklad ukazuje, jak pomocí Arabské a angličtina čísel ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace běžící v Arabic verzi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-xaml[Numbers#Numbers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 Následující obrázek znázorňuje výstup v předchozím příkladu, pokud používáte v Arabic verzi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 **Obrázek znázorňující Arabic a anglické čísla zobrazí**  
  
 ![Aplikaci XamlPad snímek obrazovky s čísly](../../../../docs/framework/wpf/advanced/media/numbers.PNG "čísla")  
  
 <xref:System.Windows.FlowDirection> Byl důležité v tomto případě, protože nastavení <xref:System.Windows.FlowDirection> k <xref:System.Windows.FlowDirection.LeftToRight> místo toho by mít poskytuje Evropského číslic. Následující části popisují, jak vám má jednotné zobrazení číslic v celém dokumentu. Pokud v tomto příkladu není spuštěný v systému Windows, Arabské, zobrazí se všechny číslice jako Evropského číslic.  
  
 **Definování pravidla nahrazení**  
  
 V reálné aplikaci může být nutné k nastavení jazyka prostřednictvím kódu programu. Například chcete nastavit `xml:lang` atribut, aby byla stejná jako používaný v systému [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], nebo může být změnit jazyk v závislosti na stavu aplikace.  
  
 Pokud chcete, aby se změny podle stavu aplikace, ujistěte se, použít další funkce poskytované službou [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Nastavte nejprve, součást aplikace `NumberSubstitution.CultureSource="Text"`. Použití tohoto nastavení je zajištěno, že nastavení nepocházejí ze [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro text elementy, které mají "User" jako výchozí, jako například <xref:System.Windows.Controls.TextBlock>.  
  
 Příklad:  
  
||  
|-|  
|`<TextBlock`<br /><br /> `Name="text1" NumberSubstitution.CultureSource="Text">`<br /><br /> `1234+5679=6913`<br /><br /> `</TextBlock>`|  
  
 Do odpovídajícího [!INCLUDE[TLA2#tla_lhcshrp](../../../../includes/tla2sharptla-lhcshrp-md.md)] kódu, nastavte `Language` vlastnost například `"ar-SA"`.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");`|  
  
 Pokud je nutné nastavit `Language` vlastnost, která má aktuální uživatel [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jazyk použít následující kód.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage(`<br /><br /> `System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);`|  
  
 <xref:System.Globalization.CultureInfo.CurrentCulture%2A>představuje aktuální jazykovou verzi používá aktuální vlákno v době běhu.  
  
 Váš koncový [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] příkladu by měla být podobně jako v následujícím příkladu.  
  
 [!code-xaml[Numbers2#Numbers2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 Váš koncový [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] by měla být podobný následujícímu příkladu.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 Následující obrázek ukazuje, jak okno vypadá pro buď programovací jazyk.  
  
 **Obrázek, který zobrazuje Arabic čísla**  
  
 ![Arabic čísla](../../../../docs/framework/wpf/advanced/media/numbers2.PNG "Numbers2")  
  
 **Pomocí vlastnosti nahrazení**  
  
 Způsob číslo nahrazení funguje v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] závisí na jazyce text elementu a jeho <xref:System.Windows.FlowDirection>. Pokud <xref:System.Windows.FlowDirection> zleva doprava, pak jsou vykreslovány Evropského číslic. Ale pokud mu předchází Arabic text nebo jazyk nastavená na "ar" a <xref:System.Windows.FlowDirection> je <xref:System.Windows.FlowDirection.RightToLeft>, místo toho vykreslení Arabic číslic.  
  
 V některých případech ale můžete vytvořit jednotné aplikaci, například Evropského čísla pro všechny uživatele. Nebo Arabic číslic v <xref:System.Windows.Documents.Table> buněk s konkrétním <xref:System.Windows.Style>. Jeden snadný způsob, jak provést používající <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> vlastnost.  
  
 V následujícím příkladu první <xref:System.Windows.Controls.TextBlock> nemá <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> vlastnost nastavena, aby algoritmus zobrazí Arabic číslic podle očekávání. Ale za sekundu <xref:System.Windows.Controls.TextBlock>, nahrazování nastavena na evropské přepsání výchozí nahrazování pro Arabic čísla a jsou zobrazeny Evropského číslic.  
  
 [!code-xaml[Numbers3#Numbers3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
