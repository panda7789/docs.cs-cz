---
title: "XAML a vlastní třídy pro WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da599afc94fba617d4df17c57679d8ee4bb05c61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-and-custom-classes-for-wpf"></a>XAML a vlastní třídy pro WPF
XAML, jak jsou implementované ve [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] rozhraní podporuje schopnost definovat vlastní třídu nebo strukturu v žádném [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] jazyka a poté přístup pomocí značek XAML. Můžete použít kombinaci [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]-definované typy a vaše vlastní typy v rámci stejného souboru značek, obvykle mapování vlastních typů na předponu oboru názvů jazyka XAML. Toto téma popisuje požadavky, které vlastní třídu, musí vyhovovat možné používat jako XAML element.  
  
 
  
<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Vlastní třídy v sestavení nebo aplikace  
 Ve dvou různých způsobů se dá definovat vlastní třídy, které se používají v jazyce XAML: v rámci modelu code-behind nebo jiný kód, který vytváří primární [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace, nebo jako třídu v samostatné sestavení, jako je například spustitelný soubor nebo knihovnu DLL používá jako knihovny tříd. Každá z těchto přístupů má konkrétní výhody a nevýhody.  
  
-   Výhodou vytvoření knihovny tříd je, že v mnoha různých možné aplikací lze sdílet takové vlastní třídy. Samostatné knihovny také usnadňuje správa verzí – potíže aplikací k řízení a zjednodušuje vytváření třídy, kde je třída zamýšlené použití jako kořenový element na stránce XAML.  
  
-   Výhodou definování vlastní třídy v aplikaci je, že tato metoda je relativně jednoduché a minimalizuje nasazení a testování problémů při zavádění samostatné sestavení nad rámec spustitelného souboru hlavní aplikace.  
  
-   Jestli definované v sestavení stejný nebo jiný, vlastní třídy musí být namapována mezi CLR obor názvů a obor názvů XML, aby bylo možné použít v jazyce XAML jako elementy. V tématu [obory názvů jazyka XAML a mapování Namespace pro jazyk XAML WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>Požadavky pro vlastní třídy jako XAML Element  
 Aby mohl být vytvořena instance jako element objekt třídě musí splňovat následující požadavky:  
  
-   Vaše vlastní třídy musí být veřejné a podporují výchozí veřejný konstruktor (bez parametrů). (Viz následující části poznámky týkající se struktury).  
  
-   Vaše vlastní třídy nesmí být vnořená třída. Vnořené třídy a "tečky" v jejich obecné použití syntaxe CLR konfliktu s jinými [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nebo XAML funkce jako je například přidružené vlastnosti.  
  
 Kromě povolení syntaxe element objektu, vaše definice objektu taky umožňuje vlastnost element syntaxe pro všechny veřejné vlastnosti, které provést tento objekt jako typ hodnoty. Je to proto, že objekt může být nyní vytvořena jako element objektu a můžete vyplnit hodnota vlastnosti element taková vlastnost.  
  
### <a name="structures"></a>Struktury  
 Struktury, které definujete, jako jsou vlastní typy se vždy můžou být vytvořená v jazyce XAML v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Důvodem je, že [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] kompilátory implicitně vytvořit výchozí konstruktor pro strukturu, která inicializuje všechny hodnoty vlastností pro jejich výchozí hodnoty. V některých případech není výchozí konstrukce chování nebo objekt elementu použití strukturu žádoucí. Může to být proto struktura slouží jako výplň hodnoty a funkce koncepčně jako union, kde hodnoty obsažené může mít vzájemně se vylučuje interpretace a proto žádný z jeho vlastnosti jsou nastavit. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je třeba tato struktura <xref:System.Windows.GridLength>. Obecně platí by měla implementovat tyto struktury tak, aby hodnoty mohou být vyjádřeny v podobě atribut, pomocí konvencí řetězce, které vytvořit různé interpretace nebo režimy hodnoty strukturu pro převaděče typů. Struktura by měl vystavit také podobné chování pro vytváření kódu prostřednictvím jiné než výchozí konstruktor.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Požadavky na vlastností vlastní třídy jako atributy XAML  
 Vlastnosti musí odkazovat na typ podle hodnoty (například primitivní), nebo pomocí třídy pro typ, který má výchozí konstruktor nebo převaděč vyhrazený typ, kterým může přistupovat na XAML procesor. K implementaci CLR XAML XAML procesory buď najít takové převaděče prostřednictvím nativní podpora pro primitiva jazyka, nebo aplikaci <xref:System.ComponentModel.TypeConverterAttribute> na typ nebo člen v zálohování definic typů  
  
 Alternativně může odkazovat na vlastnost typ abstraktní třídy nebo rozhraní. U abstraktní třídy nebo rozhraní očekávání pro analýzu XAML je, že hodnota vlastnosti musí být vyplněna s instancí praktické třídy, které implementují rozhraní nebo instance typy, které jsou odvozeny od abstraktní třídy.  
  
 Vlastnosti lze deklarovat na abstraktní třídu, ale lze nastavit pouze u praktické tříd, které jsou odvozeny od abstraktní třídy. Je to proto, že vytvoření objektu elementu pro třídu vůbec vyžaduje, aby veřejný výchozí konstruktor pro třídu.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>TypeConverter povoleno atribut syntaxe  
 Pokud zadáte konvertor vyhrazené, s atributy typu na úrovni třídy, umožňuje převod použité typu atributu syntaxe pro vlastnost, která vytvořit instanci typu. Převaděče typů neumožňuje použití elementu objektu typu; pouze přítomnost výchozí konstruktor pro tento typ umožňuje použití objektu elementu. Proto vlastnosti, které jsou povolené převaděče typů nejsou obecně použitelné v syntaxi vlastnost, pokud vlastní typ také podporuje syntaxi objekt elementu. Výjimkou je, že můžete zadat vlastnost element syntaxi, ale mít element vlastnosti obsahovat řetězec. Toto využití je skutečně v podstatě ekvivalentní použití syntaxe atribut a takové využití není běžné, pokud je třeba pro robustnější zpracování prázdných znaků hodnoty atributu. Například následující je použití elementu vlastnost, která přebírá řetězec a ekvivalentní atribut využití:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Příklady vlastností, kde atribut syntaxe je povoleno, ale vlastnost element syntaxi, která obsahuje element, objekt je zakázaná prostřednictvím XAML jsou různé vlastnosti, které provést <xref:System.Windows.Input.Cursor> typu. <xref:System.Windows.Input.Cursor> Třída má převodník vyhrazený typ <xref:System.Windows.Input.CursorConverter>, ale nevystavuje výchozí konstruktor, proto <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost lze nastavit pouze prostřednictvím syntaxe atribut i když skutečnou <xref:System.Windows.Input.Cursor> typ je typ odkazu.  
  
### <a name="per-property-type-converters"></a>Převaděče typů pro vlastnosti  
 Alternativně může samotné vlastnosti deklarovat převaděče typů na úrovni vlastnost. To umožňuje "mini jazyk" vytváří instance objektů typu vložený vlastnost zpracováním jako vstup pro příchozí řetězcové hodnoty atributu <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> operace založená na příslušného typu. Obvykle to slouží k poskytování přistupujícím objektem pohodlí a stejná jako jediný prostředek povolit nastavení vlastnosti v jazyce XAML. Je však také možné použít převaděčů typů pro atributy, ve které chcete použít existující [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] typy, které není zadat výchozí konstruktor nebo s atributy typ převaděče. Příklady z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraní API jsou některé vlastnosti, které provést <xref:System.Globalization.CultureInfo> typu. V takovém případě [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použít existující [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] <xref:System.Globalization.CultureInfo> typ lépe vyřešit kompatibilita a migrace scénáře, které byly používány v dřívějších verzích rozhraní, ale <xref:System.Globalization.CultureInfo> typ nepodporuje nezbytné konstruktory nebo úrovni převod typů možné používat jako hodnotu vlastnosti XAML přímo.  
  
 Vždy, když vystavit vlastnost, která má použití XAML, zejména v případě, že jsou ovládacího prvku Autor, doporučujeme raději zálohování tuto vlastnost s vlastnost závislosti. To je zvlášť hodnota true, pokud použijete existující [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] implementace XAML procesoru, protože může zlepšit výkon pomocí <xref:System.Windows.DependencyProperty> zálohování. Vlastnost závislosti zveřejní funkce vlastnost systému pro vaše vlastnost, která uživatelé budou pocházet očekávat u vlastnosti přístupné XAML. To zahrnuje funkce, jako je animace, vazby dat a podpora stylu. Další informace najdete v tématu [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) a [načítání XAML a vlastností závislostí](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Zápis a zapisujících převaděče typů  
 Čas od času musíte napsat vlastní <xref:System.ComponentModel.TypeConverter> odvozené třídy zajistit převod typu pro typ vašeho vlastnost. Pokyny, jak jsou odvozeny od a vytvořit převaděče typů, který podporuje použití XAML a jak se má použít <xref:System.ComponentModel.TypeConverterAttribute>, najdete v části [TypeConverters a XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Požadavky pro syntaxe atribut obslužné rutiny událostí XAML na události vlastní třídy  
 Chcete-li ji použít jako [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události, události musí být zveřejněné jako veřejná událost na třídu, která podporuje výchozí konstruktor nebo na abstraktní třídy, kde jsou přístupné události v odvozených třídách. Chcete-li použít pohodlně jako směrované události vaše [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události by měla implementovat explicitní `add` a `remove` metody, které přidávat a odebírat obslužné rutiny pro [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] podpisu události a předávat tyto obslužné rutiny na <xref:System.Windows.UIElement.AddHandler%2A>a <xref:System.Windows.UIElement.RemoveHandler%2A> metody. Tyto metody přidat nebo odebrat obslužné rutiny do úložiště směrované události obslužné rutiny na události je připojen k instanci.  
  
> [!NOTE]
>  Je možné registrovat obslužné rutiny přímo pro směrované události pomocí <xref:System.Windows.UIElement.AddHandler%2A>a úmyslně nedefinuje [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událost, která zveřejňuje směrované události. Toto se nedoporučuje obecně protože události neumožní syntaxe atributu XAML pro připojení obslužné rutiny a výsledná třída nabídne méně transparentní XAML zobrazení daný typ funkce.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Zápis vlastnosti kolekce  
 Vlastnosti, které typu kolekce mají XAML syntaxi, která umožňuje určit objekty, které jsou přidány do kolekce. Tato syntaxe má dvě upozorňují na důležité funkce.  
  
-   Objekt, který je objekt v kolekci nemusí být zadaný v elementu syntaxe objektu. Vždy, když zadáte vlastnosti v jazyce XAML, který přebírá typ kolekce je implicitní přítomnosti tohoto typu kolekce.  
  
-   Podřízené elementy vlastnost značek v kolekci se zpracovávají se stanou členy kolekce. Obvykle je kód přístup k členům kolekce se provádí prostřednictvím seznamu nebo slovník metody, jako `Add`, nebo prostřednictvím indexeru. Ale XAML syntaxe nepodporuje metody nebo indexery (výjimka: XAML 2009 může podporovat metody, ale pomocí jazyka XAML 2009 omezuje možné použití WPF; viz [funkce jazyka XAML 2009](../../../../docs/framework/xaml-services/xaml-2009-language-features.md)). Kolekce jsou samozřejmě velmi běžné požadavky pro vytváření stromu elementů a potřebujete některé způsob naplnění těchto kolekcí v deklarativní XAML. Vlastnost kolekce podřízených elementů proto jsou zpracovávány jejich přidáním do kolekce, která je hodnota typu vlastnosti kolekce.  
  
 Implementace rozhraní .NET Framework XAML Services a proto procesoru WPF XAML používá následující definici pro co se považuje za vlastnost kolekce. Vlastnost typ vlastnosti musí implementovat jednu z těchto možností:  
  
-   Implementuje <xref:System.Collections.IList>.  
  
-   Implementuje <xref:System.Collections.IDictionary> nebo jeho ekvivalent obecné (<xref:System.Collections.Generic.IDictionary%602>).  
  
-   Odvozená z <xref:System.Array> (Další informace o pole v jazyce XAML najdete v tématu [x: Array – rozšíření značek](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
-   Implementuje <xref:System.Windows.Markup.IAddChild> (rozhraní definované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Každý z těchto typů CLR má `Add` metodu, která se používá procesorem XAML k přidání položky ke kolekci základní při vytváření grafu objektu.  
  
> [!NOTE]
>  Obecná `List` a `Dictionary` rozhraní (<xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IDictionary%602>) nejsou podporovány pro zjišťování kolekce pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML procesoru. Můžete však použít <xref:System.Collections.Generic.List%601> třídy jako základní třída, protože implementuje <xref:System.Collections.IList> přímo, nebo <xref:System.Collections.Generic.Dictionary%602> jako základní třída, protože implementuje <xref:System.Collections.IDictionary> přímo.  
  
 Když je deklarovat vlastnost, která vezme kolekci, buďte opatrní o tom, jak je v nové instance typu inicializovat hodnota této vlastnosti. Pokud nejsou implementace vlastnost jako vlastnost závislosti, pak má vlastnost použít zálohování pole, která volá konstruktor typu kolekce je dostačující. Pokud je vaše vlastnost vlastnost závislosti, pak musíte k chybě při inicializaci vlastnost kolekce jako součást výchozí konstruktor typu. Je to proto, že vlastnost závislosti trvá jeho výchozí hodnotu z metadat a obvykle nechcete, aby počáteční hodnota vlastnost kolekce, která má být statické, sdílené kolekce. Měla by existovat instance kolekce na každý obsahující instanci typu. Další informace najdete v tématu [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
 Typ vlastní kolekce můžete implementovat pro vaši vlastnost kolekce. Z důvodu implicitní kolekce vlastnost zacházení typ vlastní kolekce nemusí poskytnout výchozí konstruktor, aby bylo možné použít v jazyce XAML implicitně. Je však můžete také zadat výchozí konstruktor pro typ kolekce. Může se jednat o smysl postup. Pokud vám poskytne výchozí konstruktor, nemůže explicitně deklarovat kolekce jako objekt elementu. Některé značek autoři mohou kterém má být explicitní kolekce jako řádu styl značek. Výchozí konstruktor taky můžete zjednodušit inicializace požadavky při vytváření nové objekty, které používají váš typ kolekce jako hodnotu vlastnosti.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>Deklarování vlastností obsahu XAML  
 Jazyk XAML definuje koncept [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu vlastnost. Každá třída, které lze použít v syntaxi objekt může mít právě jednu vlastnost obsahu XAML. Deklarovat vlastnost, která má být vlastnost obsahu XAML pro třídu, použít <xref:System.Windows.Markup.ContentPropertyAttribute> jako součást definice třídy. Zadejte název určený vlastnost XAML obsahu jako <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> v atributu. Vlastnost je zadán jako řetězec podle názvu, ne jako reflexe konstrukce, jako <xref:System.Reflection.PropertyInfo>.  
  
 Můžete zadat vlastnost kolekce, která má být vlastnost obsahu XAML. Výsledkem použití této vlastnosti, které object element může mít jeden nebo více podřízených prvků, bez jakýchkoli použité elementy z kolekce objekt nebo vlastnost element značky. Tyto prvky jsou pak považován za hodnotu pro vlastnost obsahu XAML a přidat do instance kolekce zálohování.  
  
 Některé vlastnosti existující XAML obsahu použijte vlastnost typ `Object`. To umožňuje obsahu, například hodnoty vlastnosti, která může trvat primitivní XAML <xref:System.String> i trvá hodnotu jeden odkaz na objekt. Pokud budete postupovat podle tohoto modelu, typu vašeho je zodpovědná za určení typu a také zpracování možných typů. Typické důvod <xref:System.Object> obsahu typ je pro podporu obou jednoduchý způsob přidávání obsahu objektu jako řetězec (který obdrží výchozí prezentace zpracování) nebo k pokročilé způsob přidání objektu obsah, který určuje jiné než výchozí prezentace nebo Další data.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>Serializace XAML  
 Pro určité scénáře, jako třeba když jsou autora ovládacího prvku, můžete také zajistit žádné reprezentace objektu, který se dá vytvořit instance v jazyce XAML lze také serializovat zpět na ekvivalentní kód XAML. Serializace požadavky nejsou popsané v tomto tématu. V tématu [řídit vytváření přehled](../../../../docs/framework/wpf/controls/control-authoring-overview.md) a [Element stromu a serializace](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Přehled vytváření ovládacích prvků](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Přehled základních elementů](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Vlastnosti závislostí a načítání XAML](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)
