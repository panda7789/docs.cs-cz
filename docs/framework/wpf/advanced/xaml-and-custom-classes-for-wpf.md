---
title: XAML a vlastní třídy
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 8dab7310826357d7fbe434002298032b8722e5b5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744424"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>XAML a vlastní třídy pro WPF
XAML, jak je implementováno v architekturách modulu CLR (Common Language Runtime), podporuje možnost definovat vlastní třídu nebo strukturu v jakémkoli jazyce modulu CLR (Common Language Runtime) a pak k této třídě přistupovat pomocí kódu XAML. Můžete použít kombinaci [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]typů a vašich vlastních typů v rámci stejného souboru s označením, obvykle mapováním vlastních typů na předponu oboru názvů XAML. Toto téma popisuje požadavky, které musí vlastní třída splňovat, aby ji bylo možné použít jako prvek XAML.  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Vlastní třídy v aplikacích nebo sestaveních  
 Vlastní třídy, které jsou používány v jazyce XAML, lze definovat dvěma různými způsoby: v rámci kódu na pozadí nebo jiném kódu, který vytváří primární [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikaci, nebo jako třídu v samostatném sestavení, jako je například spustitelný soubor nebo knihovna DLL používané jako knihovna tříd. Každý z těchto přístupů má konkrétní výhody a nevýhody.  
  
- Výhodou vytvoření knihovny tříd je, že jakékoli takové vlastní třídy lze sdílet v mnoha různých možných aplikacích. Samostatná knihovna také usnadňuje řízení správy verzí aplikací a zjednodušuje vytváření třídy, kde je zamýšlené použití třídy jako kořenový element na stránce XAML.  
  
- Výhodou definování vlastních tříd v aplikaci je, že tato technika je poměrně odlehčená a minimalizuje problémy při nasazení a testování, ke kterým došlo při zavedení samostatných sestavení mimo hlavní spustitelný soubor aplikace.  
  
- Bez ohledu na to, zda jsou definovány ve stejném nebo jiném sestavení, musí být vlastní třídy mapovány mezi oborem názvů CLR a oborem názvů XML, aby je bylo možné použít v jazyce XAML jako prvky. Viz [obory názvů XAML a mapování oboru názvů pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>Požadavky na vlastní třídu jako element XAML  
 Aby bylo možné vytvořit instanci jako prvek objektu, musí vaše třída splňovat následující požadavky:  
  
- Vaše vlastní třída musí být veřejná a podporovat výchozí veřejný konstruktor (bez parametrů). (Poznámky týkající se struktur najdete v následující části.)  
  
- Vaše vlastní třída nesmí být vnořená třída. Vnořené třídy a "tečka" v obecné syntaxi použití CLR jsou v konfliktu s jinými funkcemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nebo XAML, jako jsou například připojené vlastnosti.  
  
 Kromě povolení syntaxe elementů objektu umožňuje definice objektu také syntaxi elementu Property pro jakékoli jiné veřejné vlastnosti, které tento objekt přebírají jako typ hodnoty. Důvodem je, že objekt se teď může vytvořit jako prvek objektu a může vyplnit hodnotu elementu vlastnosti takové vlastnosti.  
  
### <a name="structures"></a>Struktury  
 Struktury, které definujete jako vlastní typy, je vždy možné sestavit v jazyce XAML v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Důvodem je, že kompilátory CLR implicitně vytvoří konstruktor bez parametrů pro strukturu, která inicializuje všechny hodnoty vlastností na jejich výchozí hodnoty. V některých případech není vhodné výchozí chování konstrukce nebo použití prvků objektu pro strukturu. Důvodem může být to, že struktura má plnit hodnoty a funkce koncepčně jako sjednocení, kde uvedené hodnoty mohou mít vzájemně exkluzivní interpretaci, a proto žádnou z vlastností nelze nastavit. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] příklad takové struktury je <xref:System.Windows.GridLength>. Obecně by tyto struktury měly implementovat konvertor typu, aby hodnoty mohly být vyjádřeny ve formě atributu pomocí konvencí řetězců, které vytvářejí různé interpretace nebo režimy hodnot struktury. Struktura by měla také vystavovat podobné chování pro vytváření kódu prostřednictvím konstruktoru bez parametrů.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Požadavky na vlastnosti vlastní třídy jako atributů XAML  
 Vlastnosti musí odkazovat na typ podle hodnoty (například primitivní), nebo použít třídu pro typ, který má buď konstruktor bez parametrů, nebo vyhrazený konvertor typu, ke kterému má procesor XAML přístup. V implementaci CLR XAML, procesory XAML buď tyto převaděče najdou pomocí nativní podpory pro jazykové primitivy, nebo prostřednictvím aplikace <xref:System.ComponentModel.TypeConverterAttribute> do typu nebo členu v definicích zálohování typu.  
  
 Alternativně může vlastnost odkazovat na abstraktní typ třídy nebo na rozhraní. U abstraktních tříd nebo rozhraní je očekávána analýza XAML, že hodnota vlastnosti musí být vyplněna s praktickými instancemi třídy, které implementují rozhraní, nebo instancemi typů, které jsou odvozeny z abstraktní třídy.  
  
 Vlastnosti lze deklarovat u abstraktní třídy, ale lze je nastavit pouze v praktických třídách, které jsou odvozeny z abstraktní třídy. Je to proto, že při vytváření elementu Object pro třídu, která vůbec vyžaduje veřejný konstruktor bez parametrů pro třídu.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Syntaxe atributu s povolenou TypeConverter  
 Pokud zadáte vyhrazený typ konvertoru s atributem na úrovni třídy, použije se převod typu na syntaxi atributu pro jakoukoliv vlastnost, která vyžaduje vytvoření instance daného typu. Konvertor typu nepovoluje použití elementu Object typu; pouze přítomnost konstruktoru bez parametrů pro tento typ povoluje použití prvku objektu. Proto jsou vlastnosti, které jsou povoleny konvertoru typu, obecně řečeno nepoužitelné v syntaxi vlastnosti, pokud samotný typ také nepodporuje syntaxi elementu objektu. Výjimkou je, že můžete zadat syntaxi elementu vlastnosti, ale element Property obsahuje řetězec. Toto využití je skutečně v podstatě ekvivalentem použití syntaxe atributu a takové použití není běžné, pokud není potřeba pružnější zpracování prázdných míst v hodnotě atributu. Například Následuje příklad použití prvku vlastnosti, který přebírá řetězec a ekvivalent použití atributu:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Příklady vlastností, kde je povolena syntaxe atributu, ale syntaxe elementu vlastností, která obsahuje prvek objektu je zakázán prostřednictvím jazyka XAML, jsou různé vlastnosti, které přijímají <xref:System.Windows.Input.Cursor> typ. Třída <xref:System.Windows.Input.Cursor> má vyhrazený konvertor typu <xref:System.Windows.Input.CursorConverter>, ale nevystavuje konstruktor bez parametrů, takže vlastnost <xref:System.Windows.FrameworkElement.Cursor%2A> lze nastavit pouze prostřednictvím syntaxe atributu, i když skutečný typ <xref:System.Windows.Input.Cursor> je odkazový typ.  
  
### <a name="per-property-type-converters"></a>Převaděče typů per-Property  
 Alternativně může samotná vlastnost deklarovat konvertor typu na úrovni vlastnosti. To umožňuje "" zkrácenému jazyku ", který vytváří instance objektů typu vložené vlastnosti, zpracováním hodnot příchozích řetězců atributu jako vstupu pro operaci <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> na základě příslušného typu. Obvykle je to provedeno pro usnadnění přístupu, a ne jako jediný způsob, jak povolit nastavení vlastnosti v jazyce XAML. Je však také možné použít převaděče typů pro atributy, kde chcete použít existující typy CLR, které neposkytují konstruktor bez parametrů ani konvertor typu s atributy. Příklady z rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API jsou některé vlastnosti, které přebírají typ <xref:System.Globalization.CultureInfo>. V tomto případě [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používali existující typ <xref:System.Globalization.CultureInfo> Microsoft .NET Framework, aby lépe vyhovovaly scénářům kompatibility a migrace, které byly použity v dřívějších verzích rozhraní, ale typ <xref:System.Globalization.CultureInfo> nepodporoval potřebné konstruktory nebo převod typu na úrovni typu, aby jej bylo možné použít jako hodnotu vlastnosti XAML přímo.  
  
 Pokaždé, když vystavíte vlastnost, která má použití XAML, zejména pokud jste autorem ovládacího prvku, měli byste důrazně zvážit, zda tuto vlastnost obsahuje vlastnost závislosti. To platí zejména v případě, že použijete existující [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] implementaci procesoru XAML, protože můžete zvýšit výkon pomocí <xref:System.Windows.DependencyProperty>ho zálohování. Vlastnost závislosti vystaví funkce systému vlastností pro vaši vlastnost, které budou uživatelé chtít očekávat pro vlastnost přístupnou pomocí XAML. To zahrnuje funkce, jako je například animace, datová vazba a podpora stylu. Další informace najdete v tématu [vlastnosti vlastní závislosti](custom-dependency-properties.md) a [načítání XAML a vlastnosti závislostí](xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Zápis a označení konvertoru typu  
 Příležitostně budete muset napsat vlastní <xref:System.ComponentModel.TypeConverter> odvozenou třídu, která poskytuje převod typu pro typ vlastnosti. Pokyny, jak odvodit z a vytvořit konvertor typu, který může podporovat použití XAML a jak použít <xref:System.ComponentModel.TypeConverterAttribute>, naleznete v tématu [TypeConverters a XAML](typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Požadavky na syntaxi atributů obslužné rutiny událostí XAML u událostí vlastní třídy  
 Aby bylo možné použít jako událost CLR, musí být událost vystavena jako veřejná událost ve třídě, která podporuje konstruktor bez parametrů, nebo na abstraktní třídě, kde je k události možné přistupovat v odvozených třídách. Aby bylo možné používat pohodlný postup jako směrované události, měla by vaše událost CLR implementovat explicitní `add` a `remove` metody, které přidávají a odebírají obslužné rutiny pro signaturu události CLR a předávají tyto obslužné rutiny metodám <xref:System.Windows.UIElement.AddHandler%2A> a <xref:System.Windows.UIElement.RemoveHandler%2A>. Tyto metody přidávají nebo odebírají obslužné rutiny do úložiště obslužné rutiny směrované události v instanci, ke které je událost připojena.  
  
> [!NOTE]
> Je možné zaregistrovat obslužné rutiny přímo pro směrované události pomocí <xref:System.Windows.UIElement.AddHandler%2A>a záměrně nedefinovat událost modulu CLR, která zpřístupňuje směrovanou událost. Obecně se to nedoporučuje, protože událost nepovoluje syntaxi atributu XAML pro připojení obslužných rutin a výsledná třída nabízí méně transparentní zobrazení XAML pro tyto možnosti typu.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Zápis vlastností kolekce  
 Vlastnosti, které přijímají typ kolekce, mají syntaxi jazyka XAML, která umožňuje určit objekty, které jsou přidány do kolekce. Tato syntaxe má dvě významné funkce.  
  
- Objekt, který je objektem kolekce, nemusí být specifikován v syntaxi elementu Object. Přítomnost tohoto typu kolekce je implicitní pokaždé, když zadáte vlastnost v jazyce XAML, která přebírá typ kolekce.  
  
- Podřízené prvky vlastnosti Collection v kódu jsou zpracovávány tak, aby se staly členy kolekce. Obvykle je přístup kódu k členům kolekce prováděn prostřednictvím metod typu list/Dictionary, jako je například `Add`nebo prostřednictvím indexeru. Ale Syntaxe XAML nepodporuje metody nebo indexery (výjimka: XAML 2009 může podporovat metody, ale použití XAML 2009 omezuje možné použití WPF; viz [xaml 2009 jazykové funkce](../../../desktop-wpf/xaml-services/xaml-2009-language-features.md)). Kolekce jsou zjevně velice běžným požadavkem pro vytváření stromové struktury prvků a potřebujete nějaký způsob, jak tyto kolekce naplnit v deklarativních XAML. Proto podřízené prvky vlastnosti kolekce jsou zpracovány jejich přidáním do kolekce, která je hodnotou typu vlastnosti kolekce.  
  
 Implementace .NET Framework XAML Services, takže procesor WPF XAML používá následující definici pro to, co představuje vlastnost kolekce. Typ vlastnosti vlastnosti musí implementovat jednu z následujících možností:  
  
- Implementuje <xref:System.Collections.IList>.  
  
- Implementuje <xref:System.Collections.IDictionary> nebo obecný ekvivalent (<xref:System.Collections.Generic.IDictionary%602>).  
  
- Je odvozen z <xref:System.Array> (Další informace o polích v jazyce XAML naleznete v tématu [X:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md)).  
  
- Implementuje <xref:System.Windows.Markup.IAddChild> (rozhraní definované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Každý z těchto typů v modulu CLR má `Add` metodu, kterou používá procesor XAML k přidávání položek do základní kolekce při vytváření grafu objektů.  
  
> [!NOTE]
> Obecné `List` a rozhraní `Dictionary` (<xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IDictionary%602>) nejsou podporovány pro zjišťování kolekce procesorem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML. Můžete však použít třídu <xref:System.Collections.Generic.List%601> jako základní třídu, protože implementuje <xref:System.Collections.IList> přímo nebo <xref:System.Collections.Generic.Dictionary%602> jako základní třídu, protože implementuje <xref:System.Collections.IDictionary> přímo.  
  
 Pokud deklarujete vlastnost, která přebírá kolekci, buďte opatrní při inicializaci této hodnoty vlastnosti v nových instancích typu. Pokud vlastnost neimplementujete jako vlastnost závislosti, pak vlastnost používá pole pro zálohování, které volá konstruktor typu kolekce. Pokud je vlastnost závislá na vlastnosti, může být nutné inicializovat vlastnost kolekce jako součást výchozího konstruktoru typu. Důvodem je to, že vlastnost závislosti přebírá svou výchozí hodnotu z metadat a obvykle nechcete, aby byla počáteční hodnota vlastnosti kolekce statická, sdílená kolekce. Měla by existovat instance kolekce pro každý z nich obsahující instanci typu. Další informace najdete v tématu [vlastnosti vlastních závislostí](custom-dependency-properties.md).  
  
 Můžete implementovat vlastní typ kolekce pro vlastnost kolekce. Z důvodu implicitního zpracování vlastností kolekce není nutné, aby typ vlastní kolekce poskytoval konstruktor bez parametrů, aby jej bylo možné použít v jazyce XAML implicitně. Můžete však volitelně poskytnout konstruktor bez parametrů pro typ kolekce. To může být vhodný postup. Pokud nezadáte konstruktor bez parametrů, nelze kolekci explicitně deklarovat jako prvek objektu. Někteří autoři značek mohou chtít zobrazit explicitní kolekci jako druh značky. Konstruktor bez parametrů může také zjednodušit požadavky na inicializaci při vytváření nových objektů, které používají typ kolekce jako hodnotu vlastnosti.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>Deklarace vlastností obsahu XAML  
 Jazyk XAML definuje koncept vlastnosti [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu. Každá třída, která je použitelná v syntaxi objektu, může mít přesně jednu vlastnost obsahu XAML. Chcete-li deklarovat vlastnost, která má být vlastností obsahu XAML pro vaši třídu, použijte <xref:System.Windows.Markup.ContentPropertyAttribute> jako součást definice třídy. Zadejte název zamýšlené vlastnosti obsahu XAML jako <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> v atributu. Vlastnost je zadána jako řetězec podle názvu, nikoli jako konstrukce reflexe, jako je například <xref:System.Reflection.PropertyInfo>.  
  
 Můžete určit vlastnost kolekce jako vlastnost obsahu XAML. Výsledkem je použití této vlastnosti, kdy prvek objektu může mít jeden nebo více podřízených elementů, aniž by se musely přesáhnout prvky objektu kolekce nebo značky prvků vlastností. Tyto prvky se pak považují za hodnotu vlastnosti obsahu XAML a přidají se do instance back-Collection.  
  
 Některé existující vlastnosti obsahu XAML používají typ vlastnosti `Object`. To umožňuje vlastnost obsahu XAML, která může přijímat primitivní hodnoty, jako je například <xref:System.String>, a také přebírat hodnotu jediného referenčního objektu. Pokud budete postupovat podle tohoto modelu, je váš typ zodpovědný za určení typu a také pro zpracování možných typů. Typickým důvodem pro <xref:System.Object> typu obsahu je podpora jednoduchého způsobu přidání obsahu objektu jako řetězce (který přijímá výchozí úpravu prezentace) nebo pokročilým způsobům přidání obsahu objektu, který určuje nevýchozí nebo dodatečná data.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>Serializace XAML  
 V některých případech, například pokud jste autorem ovládacího prvku, můžete také zajistit, aby všechny reprezentace objektů, které lze vytvořit v jazyce XAML, mohla být také serializována zpět na ekvivalentní kód XAML. Požadavky na serializaci nejsou popsány v tomto tématu. Viz téma [Přehled vytváření](../controls/control-authoring-overview.md) a [strom elementů a serializace prvku](element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Přehled základních elementů](base-elements-overview.md)
- [Vlastnosti závislostí a načítání XAML](xaml-loading-and-dependency-properties.md)
