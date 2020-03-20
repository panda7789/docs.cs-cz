---
title: XAML a vlastní třídy
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 4cd0ba7fa03d2578f4477c3ccf53188fbbea2dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186267"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>XAML a vlastní třídy pro WPF
XAML jako implementované v rámci CLR (COMMON Language runtime) podporuje možnost definovat vlastní třídu nebo strukturu v libovolném jazyce CLR (COMMON Language runtime) a pak přistupovat k této třídě pomocí značek XAML. Můžete použít směs [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]-defined typů a vlastní typy ve stejném souboru značek, obvykle mapováním vlastní typy předponu oboru názvů XAML. Toto téma popisuje požadavky, které musí splňovat vlastní třídy, aby byly použitelné jako element XAML.  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>
## <a name="custom-classes-in-applications-or-assemblies"></a>Vlastní třídy v aplikacích nebo sestaveních  
 Vlastní třídy, které se používají v XAML lze definovat dvěma různými způsoby: [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] v rámci kódu na pozadí nebo jiný kód, který vytváří primární aplikace, nebo jako třída v samostatném sestavení, jako je například spustitelný soubor nebo Knihovna DLL používá jako knihovna tříd. Každý z těchto přístupů má zvláštní výhody a nevýhody.  
  
- Výhodou vytvoření knihovny tříd je, že všechny tyto vlastní třídy mohou být sdíleny v mnoha různých možných aplikacích. Samostatná knihovna také usnadňuje správu verzí aplikací a zjednodušuje vytváření třídy, kde je zamýšlené použití třídy jako kořenový prvek na stránce XAML.  
  
- Výhodou definování vlastních tříd v aplikaci je, že tato technika je relativně zjednodušená a minimalizuje problémy s nasazením a testováním, ke kterým došlo při zavádění samostatných sestavení mimo spustitelný soubor hlavní aplikace.  
  
- Bez ohledu na to, zda jsou definovány ve stejném nebo jiném sestavení, vlastní třídy musí být mapovány mezi oborem názvů CLR a oborem názvů XML, aby mohly být použity v Jazyce XAML jako prvky. Viz [XAML Obory názvů a Mapování oboru názvů pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>Požadavky na vlastní třídu jako element XAML  
 Aby bylo možné vytvořit instanci jako prvek objektu, musí vaše třída splňovat následující požadavky:  
  
- Vlastní třída musí být veřejná a podporovat výchozí (bezparametrový) veřejný konstruktor. (Poznámky týkající se struktur naleznete v následující části.)  
  
- Vlastní třída nesmí být vnořená třída. Vnořené třídy a "tečka" v jejich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obecné syntaxi použití CLR interferují s jinými nebo Funkce XAML, jako jsou připojené vlastnosti.  
  
 Kromě povolení syntaxe prvku objektu umožňuje definice objektu také syntaxi prvku vlastnosti pro všechny ostatní veřejné vlastnosti, které berou tento objekt jako typ hodnoty. Důvodem je, že objekt může být nyní vytvořena jako element objektu a může vyplnit hodnotu prvku vlastnosti takové vlastnosti.  
  
### <a name="structures"></a>Struktury  
 Struktury, které definujete jako vlastní typy, lze vždy vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v xaml v . Důvodem je, že kompilátory CLR implicitně vytvořit konstruktor bez parametrů pro strukturu, která inicializuje všechny hodnoty vlastností na jejich výchozí hodnoty. V některých případech není žádoucí výchozí chování konstrukce nebo použití prvku objektu pro strukturu. Důvodem může být, že struktura je určena k vyplnění hodnoty a funkce koncepčně jako unie, kde obsažené hodnoty mohou mít vzájemně se vylučující interpretace a proto žádné z jeho vlastností jsou taelné. Příkladem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] takové struktury je <xref:System.Windows.GridLength>. Obecně tyto struktury by měly implementovat převaděč typu tak, aby hodnoty mohou být vyjádřeny ve formě atributu pomocí konvence řetězce, které vytvářejí různé interpretace nebo režimy hodnoty struktury. Struktura by měla také vystavit podobné chování pro konstrukci kódu prostřednictvím konstruktoru bez parametrů.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Požadavky na vlastnosti vlastní třídy jako atributy XAML  
 Vlastnosti musí odkazovat na typ podle hodnoty (například primitivní) nebo použít třídu pro typ, který má buď konstruktor bez parametrů, nebo vyhrazený převaděč typu, ke kterému má procesor XAML přístup. V implementaci CLR XAML procesory XAML buď najít tyto převaděče prostřednictvím <xref:System.ComponentModel.TypeConverterAttribute> nativní podporu pro jazykové primitivy, nebo prostřednictvím použití typu nebo člena v definicích typu zálohování  
  
 Alternativně vlastnost může odkazovat na typ abstraktní třídy nebo rozhraní. Pro abstraktní třídy nebo rozhraní, očekávání pro analýzu XAML je, že hodnota vlastnosti musí být vyplněna instancemi praktických tříd, které implementují rozhraní, nebo instance typů, které jsou odvozeny z abstraktní třídy.  
  
 Vlastnosti lze deklarovat na abstraktní třídy, ale lze nastavit pouze na praktické třídy, které jsou odvozeny z abstraktní třídy. Důvodem je, že vytvoření elementu objektu pro třídu vůbec vyžaduje veřejný konstruktor bez parametrů ve třídě.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Syntaxe atributu s povoleným převaděčem  
 Pokud zadáte vyhrazený, přiřazený převaděč typu na úrovni třídy, použitý převod typu povolí syntaxi atributu pro všechny vlastnosti, které je třeba vytvořit instanci tohoto typu. Převaděč typu neumožňuje použití prvku objektu typu; pouze přítomnost konstruktoru bez parametrů pro tento typ umožňuje použití prvku objektu. Proto vlastnosti, které jsou povoleny převaděč typu jsou obecně nelze použitelné v syntaxi vlastnosti, pokud samotný typ také podporuje syntaxi elementu objektu. Výjimkou je, že můžete zadat syntaxi prvku vlastnosti, ale prvek vlastnosti obsahuje řetězec. Toto použití je skutečně v podstatě ekvivalentní použití syntaxe atributu a takové použití není běžné, pokud není potřeba robustnější zpracování prázdnémísto hodnoty atributu. Například následující je použití prvku vlastnosti, který přebírá řetězec a ekvivalent použití atributu:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Příklady vlastností, kde je povolena syntaxe atributu, ale syntaxe prvku vlastnosti, <xref:System.Windows.Input.Cursor> která obsahuje prvek objektu, je zakázána prostřednictvím xaml jsou různé vlastnosti, které berou typ. Třída <xref:System.Windows.Input.Cursor> má převaděč <xref:System.Windows.Input.CursorConverter>vyhrazeného typu , ale nezveřejňuje <xref:System.Windows.FrameworkElement.Cursor%2A> konstruktor bez parametrů, takže vlastnost <xref:System.Windows.Input.Cursor> lze nastavit pouze pomocí syntaxe atributu, i když skutečný typ je typ odkazu.  
  
### <a name="per-property-type-converters"></a>Převaděče typu pro vlastnosti  
 Alternativně samotná vlastnost může deklarovat převaděč typu na úrovni vlastnosti. To umožňuje "mini jazyk", který inkasuje objekty typu vlastnosti vložené, zpracováním příchozí <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> řetězcové hodnoty atributu jako vstup pro operaci na základě příslušného typu. Obvykle se to provádí poskytnout pohodlí přistupujícího objektu, a nikoli jako jediný prostředek k povolení nastavení vlastnosti v XAML. Je však také možné použít převaděče typů pro atributy, kde chcete použít existující typy CLR, které neposkytují konstruktor bez parametrů nebo převodník přiřazeného typu. Příklady z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraní API jsou <xref:System.Globalization.CultureInfo> určité vlastnosti, které berou typ. V tomto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] případě používá existující microsoft <xref:System.Globalization.CultureInfo> .NET Framework typ lépe řešit kompatibilitu a migrace scénáře, <xref:System.Globalization.CultureInfo> které byly použity v dřívějších verzích rozhraní, ale typ nepodporoval nezbytné konstruktory nebo typ typu převodu typu, které mají být použitelné jako hodnota vlastnosti XAML přímo.  
  
 Kdykoli zpřístupníte vlastnost, která má použití XAML, zejména pokud jste autor ovládacího prvku, měli byste důrazně zvážit podporu této vlastnosti s vlastností závislosti. To platí zejména v případě, že používáte existující [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] implementaci procesoru XAML, protože můžete zlepšit výkon pomocí <xref:System.Windows.DependencyProperty> podpory. Vlastnost závislosti zpřístupní funkce systému vlastností pro vaši vlastnost, kterou uživatelé očekávají pro vlastnost přístupnou k XAML. To zahrnuje funkce, jako je animace, datové vazby a podpora stylu. Další informace naleznete [v tématu Vlastní vlastnosti závislostí](custom-dependency-properties.md) a [Vlastnosti načítání a závislostí XAML](xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Psaní a přiřazení převaděče typů  
 Občas budete muset napsat vlastní <xref:System.ComponentModel.TypeConverter> odvozené třídy poskytnout převod typu pro typ vaší vlastnosti. Pokyny k odvození a vytvoření převaděče typů, který podporuje použití XAML a jak použít <xref:System.ComponentModel.TypeConverterAttribute>, naleznete v [tématu TypeConverters a XAML](typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Požadavky na syntaxi atributu obslužné rutiny události XAML na událostech vlastní třídy  
 Aby byla událost použitelná jako událost CLR, musí být událost vystavena jako veřejná událost ve třídě, která podporuje konstruktor bez parametrů, nebo na abstraktní třídě, kde je událost přístupná na odvozené třídy. Chcete-li pohodlně použít jako směrované události, vaše clr `add` `remove` událost by měla implementovat explicitní a metody, které přidávají <xref:System.Windows.UIElement.AddHandler%2A> a <xref:System.Windows.UIElement.RemoveHandler%2A> odeberou obslužné rutiny pro podpis události CLR a předávají tyto obslužné rutiny metodám a. Tyto metody přidávají nebo odeberou obslužné rutiny do úložiště obslužné rutiny směrované události v instanci, ke které je událost připojena.  
  
> [!NOTE]
> Je možné zaregistrovat obslužné <xref:System.Windows.UIElement.AddHandler%2A>rutiny přímo pro směrované události pomocí a záměrně není definovat událost CLR, která zveřejňuje směrované události. To se obecně nedoporučuje, protože událost nepovolí syntaxi atributu XAML pro připojení obslužných rutin a výsledná třída nabídne méně transparentní zobrazení XAML schopností tohoto typu.  
  
<a name="Collection_Properties"></a>
## <a name="writing-collection-properties"></a>Zápis vlastností kolekce  
 Vlastnosti, které mají typ kolekce mají syntaxi XAML, která umožňuje určit objekty, které jsou přidány do kolekce. Tato syntaxe má dvě pozoruhodné funkce.  
  
- Objekt, který je objekt kolekce nemusí být zadán v syntaxi prvku objektu. Přítomnost tohoto typu kolekce je implicitní vždy, když zadáte vlastnost v XAML, která přebírá typ kolekce.  
  
- Podřízené prvky vlastnosti kolekce v přirážce jsou zpracovány, aby se staly členy kolekce. Přístup kódu k členům kolekce se obvykle provádí prostřednictvím list/dictionary metody, jako `Add`je například , nebo prostřednictvím indexeru. Syntaxe XAML však nepodporuje metody nebo indexery (výjimka: XAML 2009 může podporovat metody, ale použití XAML 2009 omezuje možné wpf použití; viz [XAML 2009 Jazykové funkce](../../../desktop-wpf/xaml-services/xaml-2009-language-features.md)). Kolekce jsou samozřejmě velmi běžný požadavek pro vytváření stromu prvků a potřebujete nějaký způsob, jak naplnit tyto kolekce v deklarativní XAML. Proto podřízené prvky vlastnosti kolekce jsou zpracovány jejich přidáním do kolekce, která je hodnota typu vlastnosti kolekce.  
  
 Implementace služby .NET Framework XAML Services a tedy wpf xaml procesor používá následující definici pro co představuje vlastnost kolekce. Typ vlastnosti musí implementovat jednu z následujících možností:  
  
- Implementuje <xref:System.Collections.IList>.  
  
- Nářadí <xref:System.Collections.IDictionary> nebo generický<xref:System.Collections.Generic.IDictionary%602>ekvivalent ( ).  
  
- Odpochází <xref:System.Array> z (další informace o polích v XAML naleznete v tématu [x:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).)  
  
- Implementuje <xref:System.Windows.Markup.IAddChild> (rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]definované).  
  
 Každý z těchto typů v `Add` CLR má metodu, která se používá procesorxaml přidat položky do základní kolekce při vytváření grafu objektu.  
  
> [!NOTE]
> Obecné `List` a `Dictionary` rozhraní<xref:System.Collections.Generic.IList%601> ( <xref:System.Collections.Generic.IDictionary%602>a ) nejsou podporovány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro zjišťování kolekce procesorem XAML. Třídu <xref:System.Collections.Generic.List%601> však můžete použít jako základní třídu, protože implementuje <xref:System.Collections.IList> přímo nebo <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.IDictionary> jako základní třídu, protože implementuje přímo.  
  
 Při deklarování vlastnost, která přebírá kolekce, buďte opatrní, jak je tato hodnota vlastnosti inicializována v nových instancích typu. Pokud neimplementujete vlastnost jako vlastnost závislosti, pak s vlastnost použít záložní pole, které volá konstruktor typu kolekce je adekvátní. Pokud vaše vlastnost je vlastnost závislosti, pak budete muset inicializovat vlastnost kolekce jako součást výchozího konstruktoru typu. Důvodem je, že vlastnost závislosti přebírá výchozí hodnotu z metadat a obvykle nechcete, aby počáteční hodnota vlastnosti kolekce byla statickou sdílenou kolekcí. Měla by existovat instance kolekce pro každou instanci obsahující typ. Další informace naleznete [v tématu Vlastní vlastnosti závislostí](custom-dependency-properties.md).  
  
 Můžete implementovat vlastní typ kolekce pro vlastnost kolekce. Z důvodu implicitní zpracování vlastnosti kolekce vlastní typ kolekce nemusí poskytnout konstruktor bez parametrů, aby mohl být použit v XAML implicitně. Volitelně však můžete zadat konstruktor bez parametrů pro typ kolekce. To může být užitečná praxe. Pokud nezadáte konstruktor bez parametrů, nelze explicitně deklarovat kolekci jako element objektu. Někteří autoři značek mohou dát přednost zobrazení explicitní kolekce jako záležitost stylu značek. Konstruktor bez parametrů může také zjednodušit požadavky na inicializaci při vytváření nových objektů, které používají typ kolekce jako hodnotu vlastnosti.  
  
<a name="XAMLCONtent"></a>
## <a name="declaring-xaml-content-properties"></a>Deklarování vlastností obsahu XAML  
 Jazyk XAML definuje koncept vlastnosti [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu. Každá třída, která je použitelná v syntaxi objektu, může mít přesně jednu vlastnost obsahu XAML. Chcete-li deklarovat vlastnost jako vlastnost obsahu XAML pro vaši třídu, použijte <xref:System.Windows.Markup.ContentPropertyAttribute> jako součást definice třídy. Zadejte název zamýšlené vlastnosti obsahu XAML jako <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> v atributu. Vlastnost je určena jako řetězec podle názvu, nikoli <xref:System.Reflection.PropertyInfo>jako konstrukce odrazu, například .  
  
 Můžete zadat vlastnost kolekce jako vlastnost obsahu XAML. To má za následek použití pro tuto vlastnost, kdy element objektu může mít jeden nebo více podřízených prvků, bez jakýchkoli zasahujících prvků objektu kolekce nebo tagů elementu vlastností. Tyto prvky jsou pak považovány za hodnotu pro vlastnost obsahu XAML a přidány do instance kolekce zálohování.  
  
 Některé existující vlastnosti obsahu XAML `Object`používají typ vlastnosti . To umožňuje vlastnost obsahu XAML, která může <xref:System.String> trvat primitivní hodnoty, jako je například a stejně jako převzetí hodnoty objektu s jedním odkazem. Pokud budete postupovat podle tohoto modelu, váš typ je zodpovědný za určení typu, stejně jako zpracování možných typů. Typickým důvodem <xref:System.Object> pro typ obsahu je podpora jak jednoduchý způsob přidání obsahu objektu jako řetězec (který obdrží výchozí zpracování prezentace), nebo pokročilý způsob přidávání obsahu objektu, který určuje nevýchozí prezentaci nebo další data.  
  
<a name="Serializing"></a>
## <a name="serializing-xaml"></a>Serializace XAML  
 Pro určité scénáře, například pokud jste autor ovládacího prvku, můžete také chtít ujistit, že všechny reprezentace objektu, které lze vytvořit v XAML lze také serializovat zpět na ekvivalentní xaml značky. Požadavky na serializaci nejsou popsány v tomto tématu. Viz [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md) a strom [elementů a serializace](element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Přehled základních elementů](base-elements-overview.md)
- [Vlastnosti závislostí a načítání XAML](xaml-loading-and-dependency-properties.md)
