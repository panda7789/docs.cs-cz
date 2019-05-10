---
title: XAML a vlastní třídy pro WPF
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 2f59e7479c856de9b00592d570ca89d2539b0ec4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662239"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>XAML a vlastní třídy pro WPF
Jak je implementován v XAML [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] architektur podporuje schopnost definovat vlastní třídy nebo struktury v libovolném [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] jazyk a pak přístupu, které třídy pomocí kódu XAML. Můžete použít kombinaci [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]-definované typy a vlastních typů ve stejném souboru kódu, obvykle na předponu oboru názvů XAML mapování vlastních typů. Toto téma popisuje požadavky, které má být použitelná jako prvek XAML musí splňovat vlastní třídy.  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Vlastní třídy v aplikacích nebo sestavení  
 Dvě různé možnosti, jak lze definovat vlastní třídy, které se používají v XAML: v rámci modelu code-behind nebo jiný kód, který vytvoří primární [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace, nebo jako třída v samostatné sestavení, jako je spustitelný soubor nebo knihovnu DLL používá jako knihovny tříd. Každá z těchto přístupů má určité výhody a nevýhody.  
  
- Výhodou vytvoření knihovny tříd je, že všechny vlastní třídy mohou být sdíleny napříč mnoha různým aplikacím je to možné. Samostatné knihovny také snazší správa verzí – potíže aplikací ovládacího prvku a zjednodušuje vytváření třídy, kde je využití určené třídy jako kořenový element na stránce XAML.  
  
- Výhodou definování vlastní třídy v aplikaci je, že tato metoda je relativně jednoduché a minimalizuje nasazení a testování problémů při zavedení samostatné sestavení mimo hlavní spustitelný soubor aplikace.  
  
- Zda definované ve stejném nebo jiném sestavení, je potřeba namapovat mezi názvový prostor CLR a obor názvů XML jinak se nedá použít v XAML jako prvky vlastní třídy. Zobrazit [obory názvů XAML a mapování Namespace pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>Požadavky pro vlastní třídy jako prvek XAML  
 Aby bylo možné vytvořit instanci jako element objektu, vaše třída musí splňovat následující požadavky:  
  
- Vlastní třída musí být veřejný a podporují výchozí veřejný konstruktor (bez parametrů). (Viz následující části pro poznámky týkající se struktury).  
  
- Vlastní třída nesmí být vnořená třída. Vnořené třídy a "tečky" v jejich obecné použití syntaxe CLR v konfliktu s jinými [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a/nebo XAML funkce, jako jsou připojené vlastnosti.  
  
 Kromě povolení syntaxe elementu objektu, vaše definice objektu taky umožňuje syntax prvku vlastnosti pro všechny veřejné vlastnosti, které získat tento objekt jako typ hodnoty. Je to proto teď může být vytvořen jako element objektu a můžete přejít k vyplnění hodnota vlastnosti element z těchto vlastností objektu.  
  
### <a name="structures"></a>Struktury  
 Struktury, které můžete definovat vlastní typy jsou vždy možné zkonstruovat v XAML v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Je to proto, [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] kompilátory implicitně vytvořit výchozí konstruktor pro struktury, která inicializuje všechny hodnoty vlastností, které jejich výchozích hodnotách. V některých případech není žádoucí výchozí konstrukci chování a/nebo objekt elementu použití pro strukturu. To může být, protože struktura je určené k vyplnění hodnot a funkce koncepčně jako sjednocení, kde hodnoty obsažené pravděpodobně vzájemně se vylučující interpretace a proto žádná z její vlastnosti jsou nastavitelná při čekání. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] příklad takové struktury je <xref:System.Windows.GridLength>. Obecně platí struktur by měly implementovat konvertor typu tak, aby hodnot lze vyjádřit do formuláře atributů, pomocí řetězce vytváření názvů, které vytvářejí různé interpretace nebo režimy hodnot strukturu. Struktury by měly vystavit také podobné chování pro tvorbu kódu prostřednictvím jiného než výchozího konstruktoru.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Požadavky pro vlastností vlastní třídy jako atributy XAML  
 Vlastnosti musí odkazovat na typ podle hodnoty (jako je například primitivní), nebo použít třídu pro typ, který má výchozí konstruktor nebo vyhrazený typ převaděče s přístupem k procesoru XAML. V implementaci CLR XAML XAML procesory buď najít takový převaděče prostřednictvím nativní podporu pro jazykové primitivy, nebo použití <xref:System.ComponentModel.TypeConverterAttribute> na typ nebo člen v zálohování definice typu  
  
 Alternativně může odkazovat na vlastnost typu abstraktní třídy nebo rozhraní. Pro abstraktní třídy nebo rozhraní očekávání ohledně analýza XAML je, že musí být hodnota vlastnosti naplněna instance praktické třídy, které implementují rozhraní nebo instance typů, které jsou odvozeny od abstraktní třídy.  
  
 Vlastnosti mohou být deklarovány u abstraktní třídy, ale lze nastavit pouze na praktické třídy, které jsou odvozeny od abstraktní třídy. Je to proto, že vytvoření objektu elementu pro třídu vůbec vyžaduje veřejný výchozí konstruktor třídy.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Povolené syntaxe atributu TypeConverter  
 Pokud zadáte konvertor typu vyhrazené, s atributy na úrovni třídy, použitých převodů umožňuje syntaxe atributu jakákoli vlastnost, která je potřeba vytvořit instanci tohoto typu. Konvertor typu není povoleno použití elementu objektu typu; pouze přítomnost výchozího konstruktoru pro daný typ umožňuje použití elementu objektu. Proto vlastnosti, které jsou povolené konvertor typu nejsou obecně použitelné v syntaxi vlastnosti, pokud typ, samotný také podporuje syntaxi elementu objektu. Výjimkou je, že můžete zadat syntax prvku vlastnosti, ale mít element vlastnosti obsahuje řetězec. Tohle využívání je ve skutečnosti v podstatě ekvivalentní použití syntaxe atributu a takové použití není běžné, pokud je potřeba pro více robustní zpracování prázdných hodnotu atributu. Například následující je použití elementu vlastnosti, která přebírá řetězec a ekvivalentní použití atributu:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Příkladem vlastnosti, kde syntaxe atributu je povoleno, ale syntax prvku vlastnosti, které obsahuje prvek objektu je zakázané prostřednictvím XAML jsou různé vlastnosti, které provést <xref:System.Windows.Input.Cursor> typu. <xref:System.Windows.Input.Cursor> Třída má vyhrazené konvertor <xref:System.Windows.Input.CursorConverter>, ale nezpřístupňuje výchozí konstruktor, proto <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost lze nastavit pouze pomocí syntaxe atributu i když samotný <xref:System.Windows.Input.Cursor> typ je typ odkazu.  
  
### <a name="per-property-type-converters"></a>Převaděče typů na vlastnost  
 Můžete také deklarovat samotné vlastnosti konvertor typu na úrovni vlastnost. To umožňuje "zkrácené jazyk", který vytváří instance objektů typu inline vlastnost podle jako vstup pro zpracování příchozích řetězcové hodnoty atributu <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> operace podle příslušného typu. Obvykle se to provádí poskytnout přístupový objekt usnadnění práce, a ne jako jediný prostředek povolit nastavení vlastnosti v XAML. Je však také možné použít převaděče typů pro atributy, ve které chcete použít existující [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] typy, které nezadávejte výchozí konstruktor nebo konvertor s atributy typu. Příklady z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraní API jsou určité vlastnosti, které provést <xref:System.Globalization.CultureInfo> typu. V takovém případě [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použít existující rozhraní Microsoft .NET Framework <xref:System.Globalization.CultureInfo> typ lépe situacích kompatibilita a migrace, které byly použity v předchozích verzích rozhraní, ale <xref:System.Globalization.CultureInfo> typ nepodporuje potřebné konstruktory nebo převod typu na úrovni typu na možné přímo použít jako hodnotu vlastnosti XAML.  
  
 Pokaždé, když zveřejníte vlastnost, která má využití XAML, zejména v případě, že se ovládací prvek Autor, doporučujeme raději zálohování tuto vlastnost s vlastností závislostí. To platí zejména v Pokud použijete existující [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] implementace editoru XAML, protože výkon lze zvýšit pomocí <xref:System.Windows.DependencyProperty> zálohování. Vlastnosti závislosti zpřístupní vlastnosti funkce systému pro vaše vlastnost, která uživateli přijde očekávat dostupné vlastnosti XAML. To zahrnuje funkce, jako je animace, podporu styl a datové vazby. Další informace najdete v tématu [vlastní vlastnosti závislosti](custom-dependency-properties.md) a [vlastnosti závislostí a načítání XAML](xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Psaní a zapisujících konvertor typu  
 Čas od času musíte napsat vlastní <xref:System.ComponentModel.TypeConverter> odvozené třídy poskytují převod typu pro váš typ vlastnosti. Pokyny, jak jsou odvozeny z a vytvořit převaděč typu, který podporuje použití XAML a tom, jak používat <xref:System.ComponentModel.TypeConverterAttribute>, naleznete v tématu [TypeConverters a XAML](typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Požadavky pro syntaxe atributu obslužné rutiny události XAML na události vlastní třídy  
 Chcete-li možné použít jako [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události, události musí být vystavené jako veřejná událost, která podporuje výchozí konstruktor třídy, nebo na abstraktní třídu, kde k události je přístupná v odvozených třídách. Aby bylo možné použít pohodlně jako směrovaných událostí, vaše [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události by měly implementovat explicitní `add` a `remove` metody, které přidávat a odebírat obslužné rutiny pro [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] podpisu události a předávat tyto obslužné rutiny pro <xref:System.Windows.UIElement.AddHandler%2A>a <xref:System.Windows.UIElement.RemoveHandler%2A> metody. Tyto metody přidat nebo odebrat obslužné rutiny obslužná rutina úložiště směrované události v instanci, která událost je připojen k.  
  
> [!NOTE]
>  Je možné registrovat obslužné rutiny přímo pro směrované události pomocí <xref:System.Windows.UIElement.AddHandler%2A>a záměrně nemá definován [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událost, která zveřejňuje směrované události. Toto nastavení nedoporučujeme obecně vzhledem k tomu, že události neumožní syntaxe XAML atributu pro připojení obslužné rutiny a výsledné třídy nabídne méně transparentní XAML zobrazení tohoto typu funkce.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Zápis vlastnosti kolekce  
 Vlastnosti, které zpracují typ kolekce mají syntaxe XAML, který umožňuje určit objekty, které jsou přidány do kolekce. Tato syntaxe má dvě důležité funkce.  
  
- Objekt, který je objekt kolekce není nutné zadat v syntaxi elementu objektu. Pokaždé, když zadáte vlastnosti XAML, která přebírá typ kolekce je implicitní přítomnosti tohoto typu kolekce.  
  
- Podřízené prvky prvku vlastnost kolekce, ve značkách jsou zpracovány do stanou členy kolekce. Obvykle kód přístup k členům kolekce se provádí prostřednictvím metody seznamu/slovníku jako `Add`, nebo prostřednictvím indexeru. Ale syntaxe XAML nepodporuje metody nebo indexery (výjimka: XAML 2009 může podporovat metody, ale pomocí XAML 2009 omezuje možná použití WPF; Zobrazit [funkce jazyka XAML 2009](../../xaml-services/xaml-2009-language-features.md)). Kolekce jsou samozřejmě velmi běžné požadavky pro vytváření stromové struktuře prvků a potřebujete způsob, jak naplnit těchto kolekcí v deklarativní XAML. Proto se zpracovávají podřízené prvky prvku vlastnost kolekce jejich přidáním do kolekce, která je typ hodnoty vlastnosti kolekce.  
  
 Implementace rozhraní .NET Framework XAML Services a proto procesor WPF XAML používá následující definici pro co se považuje za vlastnost kolekce. Vlastnost typ vlastnosti musí implementovat jedno z následujících akcí:  
  
- Implementuje <xref:System.Collections.IList>.  
  
- Implementuje <xref:System.Collections.IDictionary> nebo jeho obecný ekvivalent (<xref:System.Collections.Generic.IDictionary%602>).  
  
- Je odvozen od <xref:System.Array> (Další informace o polích v XAML najdete v tématu [x: Array – rozšíření značek](../../xaml-services/x-array-markup-extension.md).)  
  
- Implementuje <xref:System.Windows.Markup.IAddChild> (rozhraní určené [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Každý z těchto typů v prostředí CLR má `Add` metodu, která používá procesor XAML pro přidání položek do zdrojové kolekce při vytváření grafu objektů.  
  
> [!NOTE]
>  Obecné `List` a `Dictionary` rozhraní (<xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IDictionary%602>) nejsou podporovány pro detekci kolekce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML procesoru. Můžete však použít <xref:System.Collections.Generic.List%601> třídy jako základní třídu, protože implementuje <xref:System.Collections.IList> přímo, nebo <xref:System.Collections.Generic.Dictionary%602> jako základní třídu, protože implementuje <xref:System.Collections.IDictionary> přímo.  
  
 Při deklaraci vlastnosti, která vezme kolekci buďte opatrní jak hodnota této vlastnosti se inicializuje nové instance daného typu. Pokud nejsou implementace vlastnost jako vlastnost závislosti, pak vlastnost, použijte pomocné pole, která volá konstruktor typu kolekce je odpovídající. Pokud je vaše vlastnost vlastnost závislosti, budete muset inicializovat vlastnost kolekce jako součást výchozí konstruktor typu. Je to proto, že vlastnost závislosti má výchozí hodnotu z metadat a obvykle nechcete, aby počáteční hodnota vlastnosti kolekce statické, sdílené kolekce. Měla by existovat instance kolekce za každou obsahující instanci typu. Další informace najdete v tématu [vlastní vlastnosti závislosti](custom-dependency-properties.md).  
  
 Vlastní typ kolekce můžete implementovat pro vaši vlastnost kolekce. Z důvodu zpracování implicitní kolekce vlastností typ vlastní kolekce není nutné zadat výchozí konstruktor, aby se implicitně použije v XAML. Ale můžete volitelně zadat výchozí konstruktor pro typ kolekce. To může být vhodné praxe. Pokud nezadáte konstruktor default, nelze explicitně deklarovat kolekci jako element objektu. Některé autoři značky pravděpodobně chtít zobrazit explicitní kolekce jako otázkou styl značek. Výchozí konstruktor může také zjednodušit požadavky inicializace při vytváření nových objektů, které používají váš typ kolekce jako hodnotu vlastnosti.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>Deklarace vlastnosti obsahu XAML  
 Jazyk XAML definuje konceptu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Vlastnost ContentProperty. Každá třída, která je možné použít v syntaxi objekt může mít přesně jednu vlastnost obsahu XAML. Chcete-li deklarovat vlastnost, která má být vlastnost content XAML pro třídu, použijte <xref:System.Windows.Markup.ContentPropertyAttribute> jako součást definice třídy. Zadejte název odpovídající vlastnost obsahu XAML jako <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> v atributu. Vlastnost je určen jako řetězec podle názvu, ne jako reflexe konstrukce, jako <xref:System.Reflection.PropertyInfo>.  
  
 Můžete zadat vlastnost kolekce vlastností obsahu XAML. Výsledkem je využití pro tuto vlastnost, kterým object element může mít jeden nebo více podřízených elementů, bez jakýchkoli požadovanými elementy z kolekce objekt nebo vlastnost elementu značky. Tyto prvky jsou pak považován za hodnotu pro vlastnost ContentProperty XAML a přidat do instance kolekce zálohování.  
  
 Některé existující vlastnosti obsahu XAML, použijte vlastnost typu `Object`. Díky tomu XAML obsahu, vlastnost, která může trvat primitivní hodnoty jako <xref:System.String> a také převzetí hodnotu jedním odkazem na objekt. Pokud budete postupovat podle tohoto modelu, váš typ zodpovídá za určení typu, stejně jako zpracování možných typů. Typické důvod <xref:System.Object> obsahu typu je pro podporu obou jednoduchý způsob přidávání obsahu objektu jako řetězec (který obdrží ošetření prezentace výchozí) nebo rozšířené znamená, že přidání objektu obsah, který určuje jiné než výchozí prezentace nebo Další data.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>Serializace XAML  
 Pro určité scénáře, jako třeba když se ovládací prvek Autor, můžete chtít také zajistit, že všechny reprezentaci objektu, který se dá vytvořit instance v XAML lze také serializovat zpět na odpovídající kód XAML. Serializace požadavky nejsou popsané v tomto tématu. Zobrazit [řídit vytvoření přehledu](../controls/control-authoring-overview.md) a [strom prvku a serializace](element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Přehled základních elementů](base-elements-overview.md)
- [Vlastnosti závislostí a načítání XAML](xaml-loading-and-dependency-properties.md)
