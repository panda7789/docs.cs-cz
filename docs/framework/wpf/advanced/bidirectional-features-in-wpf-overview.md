---
title: Obousměrné funkce v přehledu WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 2a599322ef955b9f702f8960f294f5d093ede74a
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834752"
---
# <a name="bidirectional-features-in-wpf-overview"></a>Obousměrné funkce v přehledu WPF

Na rozdíl od jakékoli jiné vývojové platformy @no__t – 0 obsahuje mnoho funkcí, které podporují rychlý vývoj obousměrného obsahu, například smíšenou levou a pravou a zprava doleva data ve stejném dokumentu. Ve stejnou dobu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvoří Skvělé prostředí pro uživatele, kteří vyžadují obousměrné funkce, jako jsou arabské a hebrejské speaking Users.

Následující části vysvětlují mnoho obousměrných funkcí společně s příklady ilustrující, jak dosáhnout nejlepšího zobrazení obousměrného obsahu. Většina ukázek používá [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], ale můžete snadno použít koncepty pro C# nebo Microsoft Visual Basic Code.

<a name="FlowDirection"></a>

## <a name="flowdirection"></a>FlowDirection

Základní vlastnost, která definuje směr toku obsahu v aplikaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], je <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Tato vlastnost může být nastavena na jednu ze dvou hodnot výčtu <xref:System.Windows.FlowDirection.LeftToRight> nebo <xref:System.Windows.FlowDirection.RightToLeft>. Vlastnost je k dispozici pro všechny prvky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], které dědí z <xref:System.Windows.FrameworkElement>.

Následující příklady nastaví směr toku prvku <xref:System.Windows.Controls.TextBox>.

**Směr toku zleva doprava**

[!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]

**Směr toku zprava doleva**

[!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]

Následující obrázek ukazuje, jak se vykreslí předchozí kód.

![Obrázek, který znázorňuje různé směry toku.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)

Element v rámci stromu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zdědí <xref:System.Windows.FrameworkElement.FlowDirection%2A> z jeho kontejneru. V následujícím příkladu je <xref:System.Windows.Controls.TextBlock> uvnitř <xref:System.Windows.Controls.Grid>, které se nachází v <xref:System.Windows.Window>. Nastavení <xref:System.Windows.FrameworkElement.FlowDirection%2A> pro <xref:System.Windows.Window> implikuje nastavení pro <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Controls.TextBlock>.

Následující příklad ukazuje nastavení <xref:System.Windows.FrameworkElement.FlowDirection%2A>.

[!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]

Nejvyšší úroveň <xref:System.Windows.Window> má <xref:System.Windows.FlowDirection.RightToLeft> @ no__t-2, takže všechny prvky, které jsou v ní obsažené, zdědí také stejné <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Aby element mohl přepsat zadaný <xref:System.Windows.FrameworkElement.FlowDirection%2A>, musí přidat explicitní změnu směru, například druhý <xref:System.Windows.Controls.TextBlock> v předchozím příkladu, který se změní na <xref:System.Windows.FlowDirection.LeftToRight>. Pokud není definována žádná <xref:System.Windows.FrameworkElement.FlowDirection%2A>, použije se výchozí <xref:System.Windows.FlowDirection.LeftToRight>.

Následující obrázek ukazuje výstup předchozího příkladu:

![Obrázek, který znázorňuje explicitní změnu směru toku.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)

<a name="FlowDocument"></a>

## <a name="flowdocument"></a>FlowDocument

Řada vývojových platforem, jako je HTML, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] a Java, nabízí speciální podporu pro vývoj obousměrného obsahu. Jazyky značek, jako je například HTML, poskytují zapisovači obsahu potřebné značky k zobrazení textu v libovolném požadovaném směru, například značka HTML 4,0, "dir", který přijímá "RTL" nebo "ltr" jako hodnoty. Tato značka je podobná vlastnosti <xref:System.Windows.FrameworkElement.FlowDirection%2A>, ale vlastnost <xref:System.Windows.FrameworkElement.FlowDirection%2A> funguje v pokročilejším způsobu rozložení textového obsahu a lze ji použít pro jiný obsah než text.

V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je <xref:System.Windows.Documents.FlowDocument> Univerzální prvek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], který může hostovat kombinaci textu, tabulek, obrázků a dalších prvků. Ukázky v následujících částech používají tento prvek.

Přidání textu do <xref:System.Windows.Documents.FlowDocument> může být provedeno tímto způsobem. Jediným způsobem, jak to provést, je prostřednictvím <xref:System.Windows.Documents.Paragraph>, což je element na úrovni bloku, který se používá k seskupení obsahu, jako je například text. Chcete-li přidat text do prvků na úrovni inline, použijí se v ukázkách <xref:System.Windows.Documents.Span> a <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span> je element obsahu toku na úrovni inline, který se používá pro seskupení dalších vložených prvků, zatímco <xref:System.Windows.Documents.Run> je element obsahu toku na úrovni inline, který je určen pro spuštění neformátovaného textu. @No__t-0 může obsahovat více prvků <xref:System.Windows.Documents.Run>.

Příklad prvního dokumentu obsahuje dokument, který má několik názvů síťových sdílených složek; například `\\server1\folder\file.ext`. Bez ohledu na to, jestli máte tento odkaz na síť v dokumentu arabštiny nebo angličtiny, je vždycky vhodné ho zobrazovat stejným způsobem. Následující obrázek znázorňuje použití prvku span a ukazuje odkaz v dokumentu arabského <xref:System.Windows.FlowDirection.RightToLeft>:

![Obrázek, který znázorňuje použití prvku span.](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")

Vzhledem k tomu, že je text <xref:System.Windows.FlowDirection.RightToLeft>, všechny speciální znaky, například "\\", oddělte text vpravo k levému pořadí. To znamená, že se odkaz ve správném pořadí nezobrazuje, takže problém vyřešíte tak, že zachováte samostatné <xref:System.Windows.Documents.Run> Flow <xref:System.Windows.FlowDirection.LeftToRight>. Namísto samostatného <xref:System.Windows.Documents.Run> pro každý jazyk, lepší způsob, jak problém vyřešit, je vložení méně často používaného anglického textu do větší arabské <xref:System.Windows.Documents.Span>.

Následující obrázek znázorňuje to pomocí elementu Run vloženého v elementu span:

![Obrázek, který znázorňuje element Run vložený v elementu span.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)

Následující příklad ukazuje použití <xref:System.Windows.Documents.Run> a <xref:System.Windows.Documents.Span> prvků v dokumentech.

[!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]

<a name="SpanElements"></a>

## <a name="span-elements"></a>Span – elementy

Prvek <xref:System.Windows.Documents.Span> funguje jako oddělovač hranice mezi textem s různými směry toku.  I <xref:System.Windows.Documents.Span> prvků se stejným směrem toku se považují za různé obousměrné obory, což znamená, že prvky <xref:System.Windows.Documents.Span> jsou seřazené v @no__t kontejneru-2, pouze obsah v rámci elementu <xref:System.Windows.Documents.Span> se řídí <xref:System.Windows.FlowDirection> @no__. t-5.

Následující obrázek znázorňuje směr toku několika <xref:System.Windows.Controls.TextBlock> prvků.

![Obrázek, který znázorňuje textové bloky s různými směry toku.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)

Následující příklad ukazuje, jak použít prvky <xref:System.Windows.Documents.Span> a <xref:System.Windows.Documents.Run> k vytvoření výsledků zobrazených na předchozím obrázku.

[!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]

V prvcích <xref:System.Windows.Controls.TextBlock> v ukázce jsou prvky <xref:System.Windows.Documents.Span> rozloženy podle <xref:System.Windows.FlowDirection> jejich nadřazených prvků, ale text v každém prvku <xref:System.Windows.Documents.Span> se vede podle vlastního <xref:System.Windows.FlowDirection>. To platí pro Latinská a arabské jazyky – případně pro jiný jazyk.

### <a name="adding-xmllang"></a>Přidání XML: lang

Následující obrázek ukazuje jiný příklad, který používá čísla a aritmetické výrazy, například `"200.0+21.4=221.4"`. Všimněte si, že je nastavená jenom hodnota <xref:System.Windows.FlowDirection>.

![Obrázek, který zobrazuje čísla pouze pomocí FlowDirection.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)

Uživatelé této aplikace budou Disappointed ve výstupu, i když <xref:System.Windows.FlowDirection> opravíte, že čísla se netvarují, protože by měla být ve tvaru arabského čísla.

Prvky XAML mohou zahrnovat atribut [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] (`xml:lang`), který definuje jazyk každého prvku. XAML také podporuje princip jazyka [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], při kterém jsou použity hodnoty `xml:lang` pro nadřazené elementy ve stromu, které jsou používány podřízenými prvky. Vzhledem k tomu, že v předchozím příkladu nebyl definován jazyk pro element <xref:System.Windows.Documents.Run> nebo žádné z jeho prvků nejvyšší úrovně, byl použit výchozí `xml:lang`, což je `en-US` pro jazyk XAML. Algoritmus interního čísla pro tvarování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vybere čísla v odpovídajícím jazyku – v tomto případě v angličtině. Aby se arabské číslice správně vykreslily `xml:lang`, je potřeba nastavit.

Následující obrázek znázorňuje příklad s přidaným `xml:lang`.

![Obrázek, který znázorňuje arabské čísla, která se směrují zprava doleva.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)

Následující příklad přidá do aplikace `xml:lang`.

[!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]

Uvědomte si, že mnoho jazyků má různé hodnoty `xml:lang` v závislosti na cílové oblasti, například `"ar-SA"` a `"ar-EG"` představuje dvě varianty arabštiny. Předchozí příklady ilustrují, že je potřeba definovat hodnoty `xml:lang` i <xref:System.Windows.FlowDirection>.

<a name="FlowDirectionNontext"></a>

## <a name="flowdirection-with-non-text-elements"></a>FlowDirection s prvky, které nejsou textové

<xref:System.Windows.FlowDirection> definuje nejen to, jak text natéká v textovém elementu, ale také směr toku téměř každého druhého prvku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Následující obrázek ukazuje <xref:System.Windows.Controls.ToolBar>, který používá vodorovnou <xref:System.Windows.Media.LinearGradientBrush> k nakreslení jeho pozadí s levou a pravou stupnicí.

![Obrázek, který zobrazuje panel nástrojů s levým a pravým přechodem.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)

Po nastavení <xref:System.Windows.FlowDirection> na hodnotu <xref:System.Windows.FlowDirection.RightToLeft> jsou uspořádána pouze tlačítka <xref:System.Windows.Controls.ToolBar> zprava doleva, ale i <xref:System.Windows.Media.LinearGradientBrush> změní zarovnání posunu na tok zprava doleva.

Následující obrázek znázorňuje nové zarovnání <xref:System.Windows.Media.LinearGradientBrush>.

![Obrázek, který zobrazuje panel nástrojů se směrem k levému barevnému přechodu.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)

Následující příklad nakreslí <xref:System.Windows.FlowDirection.RightToLeft> @ no__t-1. (Chcete-li ji nakreslit vlevo, odeberte atribut <xref:System.Windows.FlowDirection> v <xref:System.Windows.Controls.ToolBar>.

[!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]

<a name="FlowDirectionExceptions"></a>

### <a name="flowdirection-exceptions"></a>Výjimky FlowDirection

V některých případech se <xref:System.Windows.FlowDirection> nechová podle očekávání. Tato část se zabývá dvěma výjimkami.

**Obrázek**

@No__t-0 představuje ovládací prvek, který zobrazuje obrázek. V [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] lze použít s vlastností <xref:System.Windows.Controls.Image.Source%2A> definující [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] <xref:System.Windows.Controls.Image> k zobrazení.

Na rozdíl od jiných prvků [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nedědí <xref:System.Windows.Controls.Image> <xref:System.Windows.FlowDirection> z kontejneru. Pokud je však <xref:System.Windows.FlowDirection> nastavené explicitně na <xref:System.Windows.FlowDirection.RightToLeft>, zobrazí se <xref:System.Windows.Controls.Image> převráceno vodorovně. To je implementováno jako pohodlnější funkce pro vývojáře obousměrného obsahu. vzhledem k tomu, že v některých případech je vodorovný překlopení obrázku požadovaným efektem.

Následující obrázek ukazuje převrácenou <xref:System.Windows.Controls.Image>.

![Obrázek, který ilustruje převrácenou bitovou kopii.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)

Následující příklad ukazuje, že <xref:System.Windows.Controls.Image> nedědí <xref:System.Windows.FlowDirection> z <xref:System.Windows.Controls.StackPanel>, který jej obsahuje.

> [!NOTE]
> V C:\ musíte mít soubor s názvem **ms_logo. jpg.** jednotku pro spuštění tohoto příkladu.

[!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]

> [!NOTE]
> Součástí souborů ke stažení je soubor **ms_logo. jpg** . Kód předpokládá, že soubor. jpg není v projektu, ale někde na C:\ disky. Je nutné zkopírovat soubor. jpg ze souborů projektu do C:\ disk nebo změňte kód tak, aby byl soubor v projektu hledán. Chcete-li provést tuto změnu `Source="file://c:/ms_logo.jpg"` na `Source="ms_logo.jpg"`.

**Ruky**

Kromě <xref:System.Windows.Controls.Image> je další zajímavý prvek <xref:System.Windows.Shapes.Path>. Cesta je objekt, který může nakreslit řadu propojených čar a křivek. Chová se způsobem podobným <xref:System.Windows.Controls.Image> týkající se jeho <xref:System.Windows.FlowDirection>; například <xref:System.Windows.FlowDirection.RightToLeft> @ no__t-3 je vodorovným zrcadlem <xref:System.Windows.FlowDirection.LeftToRight> 1. Na rozdíl od <xref:System.Windows.Controls.Image> <xref:System.Windows.Shapes.Path> ale dědí své <xref:System.Windows.FlowDirection> z kontejneru a druhý ho nepotřebuje explicitně zadat.

V následujícím příkladu je nakreslena Jednoduchá šipka pomocí 3 čáry. První šipka zdědí směr toku <xref:System.Windows.FlowDirection.RightToLeft> od <xref:System.Windows.Controls.StackPanel>, takže počáteční a koncový bod se měří od kořene na pravé straně. Druhá šipka, která má explicitní <xref:System.Windows.FlowDirection.RightToLeft> @ no__t-1, začíná také na pravé straně. Třetí šipka ale má svůj počáteční kořen na levé straně. Další informace o kreslení naleznete <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.GeometryGroup>.

[!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]

Následující obrázek znázorňuje výstup předchozího příkladu se šipkami nakreslenými pomocí elementu `Path`:

![Obrázek, který znázorňuje šipky vykreslené pomocí elementu Path.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)

@No__t-0 a <xref:System.Windows.Shapes.Path> jsou dva příklady, jak @no__t 2 používá <xref:System.Windows.FlowDirection>. Vedle rozvržení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvků v určitém směru v rámci kontejneru lze použít <xref:System.Windows.FlowDirection> s prvky, jako je například <xref:System.Windows.Controls.InkPresenter>, které vykreslují rukopis na povrchu, <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.RadialGradientBrush>. Kdykoli budete potřebovat právo k levému chování obsahu, který napodobuje chování zleva doprava, nebo naopak, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] tuto schopnost poskytuje.

<a name="NumberSubstitution"></a>

## <a name="number-substitution"></a>Nahrazování čísel

V minulosti systém Windows podporuje substituci čísel tím, že umožňuje znázornění různých kulturních tvarů pro stejné číslice a přitom zachovat interní úložiště těchto číslic v různých národních prostředích, jako jsou například čísla uložená v jejich dobře známé hexadecimální hodnoty, 0x40, 0x41, ale zobrazené v závislosti na vybraném jazyce.

To umožňuje aplikacím zpracovávat číselné hodnoty, aniž by je museli převádět z jednoho jazyka na jiný. uživatel například může otevřít tabulku [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] v lokalizovaných arabských oknech a zobrazit čísla ve formátu arabštiny, ale otevřít ji v Evropském verze systému Windows a viz Evropské vyjádření stejných čísel. To je také nutné pro jiné symboly, jako jsou oddělovače čárky a symbol procenta, protože obvykle doprovázejí čísla ve stejném dokumentu.

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pokračuje ve stejné tradici a přidá další podporu pro tuto funkci, která umožňuje větší kontrolu nad tím, kdy a jak se použije náhrada. I když je tato funkce navržena pro libovolný jazyk, je zvláště užitečná v obousměrném obsahu, kde tvarování číslic pro určitý jazyk je obvykle výzvou pro vývojáře aplikací z důvodu různých kultur, na kterých může aplikace běžet.

Základní vlastnost určující, jak nahrazování čísel funguje v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je vlastnost závislosti <xref:System.Windows.Media.NumberSubstitution.Substitution%2A>. Třída <xref:System.Windows.Media.NumberSubstitution> určuje, jak se mají zobrazovat čísla v textu. Má tři veřejné vlastnosti, které definují jeho chování. Následuje souhrn každé z těchto vlastností:

**CultureSource:**

Tato vlastnost určuje, jak je určena jazyková verze pro čísla. Používá jednu ze tří @no__t 0 hodnot výčtu.

- Override: Number culture je hodnota vlastnosti <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>.

- Text: číslo jazykové verze je jazyková verze běhu textu. V označení by to bylo `xml:lang` nebo jeho alias `Language` vlastnost (<xref:System.Windows.FrameworkElement.Language%2A> nebo <xref:System.Windows.FrameworkContentElement.Language%2A>). Také je výchozím nastavením pro třídy odvozené od <xref:System.Windows.FrameworkContentElement>. Mezi takové třídy patří <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> a tak dále.

- User: Number culture je jazyková verze aktuálního vlákna. Tato vlastnost je výchozím nastavením pro všechny podtřídy <xref:System.Windows.FrameworkElement>, například <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> a <xref:System.Windows.Controls.TextBlock>.

**CultureOverride**:

Vlastnost <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> se používá pouze v případě, že vlastnost <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> je nastavena na hodnotu <xref:System.Windows.Media.NumberCultureSource.Override> a je ignorována jinak. Určuje číselnou verzi. Hodnota `null`, výchozí hodnota, je interpretována jako en-US.

**Nahrazení**:

Tato vlastnost určuje typ nahrazování čísla, který má být proveden. Přebírá jednu z následujících hodnot výčtu <xref:System.Windows.Media.NumberSubstitutionMethod>:

- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: metoda Substitution je určena na základě vlastnosti <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> jazykové verze. Toto nastavení je výchozí.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Pokud je jazyková verze v arabštině nebo perské jazykové verzi, určuje, že číslice závisí na kontextu.

- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: čísla se vždycky vykreslují jako Evropská čísla.

- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: čísla se vykreslují pomocí národních číslic pro jazykovou verzi, jak určuje <xref:System.Globalization.CultureInfo.NumberFormat%2A> jazykové verze.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: čísla se vykreslují pomocí tradičních číslic pro jazykovou verzi. U většiny kultur je tato hodnota stejná jako <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. Nicméně <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> má za následek číslici v latince pro některé Arabské jazykové verze, zatímco tato hodnota má za následek arabské číslice pro všechny Arabské jazykové verze.

Co tyto hodnoty znamenají pro vývojáře s obousměrným obsahem? Ve většině případů může vývojář potřebovat definovat <xref:System.Windows.FlowDirection> a jazyk každého textového prvku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], například `Language="ar-SA"` a logika <xref:System.Windows.Media.NumberSubstitution> se postará o zobrazení čísel podle správného [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Následující příklad ukazuje použití arabských a anglické číslice v aplikaci [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] spuštěné v arabštině verze systému Windows.

[!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]

Následující obrázek ukazuje výstup předchozí ukázky, pokud používáte arabskou verzi Windows s zobrazenými arabskými a anglickými čísly:

![Obrázek zobrazující arabské a anglické číslo.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)

@No__t-0 byl v tomto případě důležité, protože nastavení <xref:System.Windows.FlowDirection> na <xref:System.Windows.FlowDirection.LeftToRight> by znamenalo, že se použily Evropské číslice. Následující části popisují, jak mít v celém dokumentu jednotný displej číslic. Pokud tento příklad není v arabštině Windows spuštěný, všechny číslice se zobrazí jako Evropské číslice.

**Definování pravidel nahrazení**

V reálné aplikaci může být potřeba nastavit jazyk programově. Například chcete nastavit atribut `xml:lang` tak, aby byl stejný jako ten, který používá [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] systému, nebo možná změnit jazyk v závislosti na stavu aplikace.

Pokud chcete provádět změny v závislosti na stavu aplikace, využijte jiné funkce, které poskytuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].

Nejprve nastavte `NumberSubstitution.CultureSource="Text"` součásti aplikace. Pomocí tohoto nastavení je zajištěno, že nastavení nepochází z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro textové prvky, které mají jako výchozí hodnotu "uživatel", například <xref:System.Windows.Controls.TextBlock>.

Příklad:

```xaml
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

V příslušném C# kódu nastavte vlastnost `Language`, například na `"ar-SA"`.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Pokud potřebujete nastavit vlastnost `Language` na jazyk uživatelského rozhraní aktuálního uživatele, použijte následující kód.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> představuje aktuální jazykovou verzi použitou aktuálním vláknem v době běhu.

Konečný příklad [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] by měl být podobný následujícímu příkladu.

[!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]

Konečný C# příklad by měl být podobný následujícímu.

[!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]

Následující obrázek ukazuje, jak okno vypadá v programovacím jazyce a zobrazuje arabské číslice:

![Obrázek, který zobrazuje arabské číslice.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)

**Použití vlastnosti Substitution**

Způsob nahrazení čísel funguje v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] závisí na jazyku prvku text a na jeho <xref:System.Windows.FlowDirection>. Pokud je <xref:System.Windows.FlowDirection> ponecháno vpravo, vykreslí se Evropské číslice. Pokud je však před ním uveden arabský text nebo má jazyk nastavený na ar a <xref:System.Windows.FlowDirection> je <xref:System.Windows.FlowDirection.RightToLeft>, místo toho se vykreslují arabské číslice.

V některých případech ale možná budete chtít vytvořit sjednocenou aplikaci, například Evropské číslice pro všechny uživatele. Nebo arabské číslice v <xref:System.Windows.Documents.Table> buňkách s konkrétní <xref:System.Windows.Style>. Jedním jednoduchým způsobem, jak to udělat, je použití vlastnosti <xref:System.Windows.Media.NumberSubstitution.Substitution%2A>.

V následujícím příkladu nemá první <xref:System.Windows.Controls.TextBlock> nastavenou vlastnost <xref:System.Windows.Media.NumberSubstitution.Substitution%2A>, takže algoritmus zobrazuje arabské číslice podle očekávání. V druhém <xref:System.Windows.Controls.TextBlock> ale náhrada je nastavená na Evropskou přepisující výchozí substituci pro arabské číslice a zobrazí se Evropské číslice.

[!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
