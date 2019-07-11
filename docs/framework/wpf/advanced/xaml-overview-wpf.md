---
title: Přehled XAML (WPF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interfaces [XAML]
- classes [XAML]
- root element [XAML]
- XAML [WPF], about XAML
- base classes [XAML]
- routed events [WPF]
- code-behind files [WPF], XAML
- collection properties [XAML]
- events [XAML]
- property element [XAML]
- content models [XAML]
- Extensible Application Markup Language (see XAML)
- attribute syntax [XAML]
ms.assetid: a80db4cd-dd0f-479f-a45f-3740017c22e4
ms.openlocfilehash: e0d277eb039c1fb1668f292d83ab9e7dbe4be70e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762320"
---
# <a name="xaml-overview-wpf"></a>Přehled XAML (WPF)
Toto téma popisuje funkce jazyka XAML a ukazuje, jak můžete použít XAML pro zápis [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací. Toto téma popisuje XAML konkrétně, jak je implementované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. XAML samotného je větší než konceptu jazyka [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="what_is_xaml"></a>   
## <a name="what-is-xaml"></a>Co je XAML?  
 XAML je deklarativní značkovací jazyk. Jak použít pro programovací model rozhraní .NET Framework, XAML zjednodušuje vytváření [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro aplikace rozhraní .NET Framework. Můžete vytvořit viditelné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky v deklarativní značce XAML a poté samostatné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] definice od logiky běhu pomocí souborů použití modelu code-behind, připojeny ke značce prostřednictvím definicí částečné třídy. XAML přímo představuje instance objektů v konkrétní sadu zálohování typy definované v sestavení. To je rozdíl oproti většina ostatních značek jazyků, které jsou obvykle interpretovaný jazyk bez přímé stejného systému typ základní. XAML umožňuje pracovní místo, kde může pracovat samostatný strany na [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a logika aplikace, pomocí potenciálně různých nástrojů.  
  
 Při reprezentovaná jako text, jsou soubory XAML soubory XML, které mají obvykle `.xaml` rozšíření. Soubory mohou být kódovány libovolný XML kódování, ale kódování v typických UTF-8.  
  
 Následující příklad ukazuje, jak je možné vytvořit tlačítko v rámci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Tento příklad je určen pouze vám charakter jak XAML představuje běžné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] programování metaphors (není kompletní ukázky).  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## <a name="xaml-syntax-in-brief"></a>Syntaxe XAML přehled  
 Následující části popisují základní formy syntaxe XAML a poskytují příklad krátký kód. Tyto oddíly nejsou určená k zajištění kompletní informace o jednotlivých forma syntaxe, například jak jsou reprezentovány v základní systém typů. Další informace o specifika syntaxe XAML pro všechny formy syntaxe představenými v tomto tématu najdete v tématu [syntaxe XAML v podrobnosti o](xaml-syntax-in-detail.md).  
  
 Velká část v následujících částech se základní, pokud máte předchozí znalost jazyka XML. Toto je důsledkem některého z základní principy návrhu z XAML.  Jazyk XAML definuje koncepty vlastní, ale tyto koncepty pracovat v rámci formuláře jazyka a kód XML.  
  
### <a name="xaml-object-elements"></a>Elementů objektu XAML  
 Prvek objektu obvykle deklaruje instanci typu. Tento typ je definován v sestavení, které poskytují základní typy pro technologie, která používá XAML jako jazyk.  
  
 Syntaxe elementu objektu vždy začíná otevírací ostrou závorkou (\<). Následuje název typu, ve kterém chcete vytvořit instanci. (Název může obsahovat pravděpodobně předponu, která budou vysvětlena dále koncept.) Potom je volitelně možné deklarovat atributy elementu objektu. K dokončení značky elementu objektu, končit ukončovací lomená závorka (>). Místo toho můžete použít samouzavírací formulář, který nemá žádný obsah tak, že dokončovací značka s lomítkem a ukončovací lomená závorka v daný okamžik (/ >). Například podívejte se na dříve zobrazených fragment znovu:  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 Určuje objekt dva elementy: `<StackPanel>` (s obsahem a koncovou značku později) a `<Button .../>` (samouzavírací formuláře, s několika atributů). Elementů objektu `StackPanel` a `Button` každé mapování k názvu třídy, která je definována [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení. Při zadávání značka elementu objektu vytvoříte instrukce pro zpracování pro vytvoření nové instance XAML. Každá instance je vytvořen zavoláním výchozí konstruktor třídy základní typ při analýze a načítají XAML.  
  
### <a name="attribute-syntax-properties"></a>Syntaxe atributu (Vlastnosti)  
 Vlastnosti objektu může často vyjádřena jako atributy elementu objektu. Syntaxe atributu názvy vlastnost, která je nastavena v syntaxi atributu, za nímž následuje operátor přiřazení (=). Hodnota atributu je vždy určena jako řetězec, který je obsažený v uvozovkách.  
  
 Syntaxe atributu je nejvíce zjednodušenou syntaxi nastavení vlastností a nejintuitivnější syntaxi pro vývojáře, kteří použili v minulosti značkovacích jazycích. Například následující kód vytvoří tlačítko, které má červený text a modré pozadí kromě zobrazovaný text zadaný jako `Content`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### <a name="property-element-syntax"></a>Syntax prvku vlastnosti  
 Pro některé vlastnosti prvku objektu syntaxe atributu není možné, protože objekt nebo informace nezbytné k zajištění hodnotu nelze vyjádřit adekvátní v rámci uvozovky a řetězec omezení syntaxe atributu. Pro tyto případy je možné odlišnou syntaxi označuje jako syntax prvku vlastnosti.  
  
 Syntaxe pro počáteční značky elementu vlastnosti je `<` *typeName*`.`*propertyName*`>`. Obecně platí že obsah dané klíčové slovo je element objektu typu, který má vlastnost jako hodnotu. Po určení obsahu, je nutné zavřít vlastnost element s koncovou značku. Syntaxe pro koncovou značku `</` *typeName*`.`*propertyName*`>`.  
  
 Pokud syntaxe atributu je možné, pomocí syntaxe atributu je obvykle pohodlnější a umožňuje kompaktnějším značky, ale, který stačí často stylu, technických omezení. Následující příklad ukazuje stejné vlastnosti nastavena jako v předchozím příkladu syntaxe atributu, ale tentokrát s použitím syntax prvku vlastnosti pro všechny vlastnosti `Button`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### <a name="collection-syntax"></a>Syntaxe kolekce  
 Jazyk XAML obsahuje některé optimalizace, které vyvolávají více čitelný značek. Jeden takový optimalizace je, že pokud používá určité vlastnosti typu kolekce položek, které se v kódu deklarujete jako podřízené prvky v rámci této vlastnosti hodnotu stanou součástí kolekce a. Kolekce podřízených elementů objektu v tomto případě je hodnota nastavena na vlastnost kolekce.  
  
 Následující příklad ukazuje syntaxi kolekcí pro nastavení hodnoty <xref:System.Windows.Media.GradientBrush.GradientStops%2A> vlastnost:  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->  
    <GradientStop Offset="0.0" Color="Red" />  
    <GradientStop Offset="1.0" Color="Blue" />  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
### <a name="xaml-content-properties"></a>Vlastnosti obsahu XAML  
 XAML určuje funkci jazyka, které třídu určit právě jeden z jeho vlastností tak, aby vlastnost obsahu XAML. Podřízené prvky tohoto prvku objektu slouží k nastavení hodnoty této vlastnosti obsahu. Jinými slovy pro vlastnost ContentProperty jednoznačně, můžete vynechat prvek vlastnosti při nastavování vlastnosti ve značce XAML a vytvoření viditelnější metafora nadřazené a podřízené v kódu.  
  
 Například <xref:System.Windows.Controls.Border> určuje vlastnost obsahu <xref:System.Windows.Controls.Decorator.Child%2A>. Následující dva <xref:System.Windows.Controls.Border> prvky jsou zpracovávána stejně jako. První z nich využívá syntaxi vlastnost obsahu a vynechá `Border.Child` element vlastnosti. Druhý zobrazí `Border.Child` explicitně.  
  
```xaml  
<Border>  
  <TextBox Width="300"/>  
</Border>  
<!--explicit equivalent-->  
<Border>  
  <Border.Child>  
    <TextBox Width="300"/>  
  </Border.Child>  
</Border>  
```  
  
 Jako pravidlo jazyka XAML hodnota vlastnosti XAML obsahu se musí předávat zcela před nebo po další prvky vlastnost zcela na tento prvek objektu. Například následující kód nezkompiluje:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Další informace o toto omezení na vlastnosti obsahu XAML, viz část "XAML obsah vlastnosti" [syntaxe XAML v podrobnosti o](xaml-syntax-in-detail.md).  
  
### <a name="text-content"></a>Textový obsah  
 Malý počet elementů XAML může zpracovat text přímo jako obsah. Chcete-li povolit, jeden z následujících případech musí být splněné:  
  
- Třída musí deklarovat vlastnost obsahu, a tuto vlastnost obsahu musí být přiřaditelný k řetězec typu (typ může být <xref:System.Object>). Například některé <xref:System.Windows.Controls.ContentControl> používá <xref:System.Windows.Controls.ContentControl.Content%2A> jako jeho vlastnost obsahu a to je typ <xref:System.Object>, a tento atribut podporuje následující použití na praktických <xref:System.Windows.Controls.ContentControl> například <xref:System.Windows.Controls.Button>: `<Button>Hello</Button>`.  
  
- Typ musí deklarovat konvertor typu, ve kterém případ textového obsahu se používá jako text inicializace pro tento konvertor typu. Například, `<Brush>Blue</Brush>`. Tento případ je méně častý v praxi.  
  
- Typ musí být primitivní známý jazyk XAML.  
  
### <a name="content-properties-and-collection-syntax-combined"></a>Kombinované syntaxe obsahu vlastnosti a kolekce  
 Podívejte se například:  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 Tady každý <xref:System.Windows.Controls.Button> je podřízený prvek <xref:System.Windows.Controls.StackPanel>. Toto je zjednodušený a intuitivní značky, která vynechává dvě značky dvou různých důvodů.  
  
- **Element vlastnosti vynechaný StackPanel.Children:** <xref:System.Windows.Controls.StackPanel> je odvozena z <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel> definuje <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> Vlastnost ContentProperty jako jeho XAML.  
  
- **Element object vynechaný UIElementCollection:** <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> Vlastnost přijímá typ <xref:System.Windows.Controls.UIElementCollection>, která implementuje <xref:System.Collections.IList>. Značky elementu kolekce lze vynechat, na základě pravidel XAML pro zpracování kolekcí, jako <xref:System.Collections.IList>. (V tomto případě <xref:System.Windows.Controls.UIElementCollection> ve skutečnosti nejde vytvořit, protože nezveřejňuje výchozí konstruktor, a to je důvod, proč <xref:System.Windows.Controls.UIElementCollection> prvek objektu se zobrazí komentářem out).  
  
```xaml  
<StackPanel>  
  <StackPanel.Children>  
    <!--<UIElementCollection>-->  
    <Button>First Button</Button>  
    <Button>Second Button</Button>  
    <!--</UIElementCollection>-->  
  </StackPanel.Children>  
</StackPanel>  
```  
  
### <a name="attribute-syntax-events"></a>Syntaxe atributu (události)  
 Syntaxe atributu slouží také pro členy, které jsou události, nikoli vlastnosti. V takovém případě atributu name je název události. V implementaci WPF události pro XAML představuje hodnotu atributu název obslužné rutiny, která implementuje delegáta tuto událost. Například následující kód přiřadí obslužné rutiny pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události <xref:System.Windows.Controls.Button> vytvořené v kódu:  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 Existuje více událostí a XAML v subsystému WPF než jenom tento příklad syntaxe atributu. Například může zajímat, co `ClickHandler` odkazujete představuje, jak je definována. To se vysvětluje v nadcházející [události a XAML použití modelu Code-Behind](xaml-overview-wpf.md#events_and_xaml_codebehind) části tohoto tématu.  
  
<a name="case_and_white space_in_xaml"></a>   
## <a name="case-and-white-space-in-xaml"></a>Případ a prázdných znaků v XAML  
 XAML je obecně malá a velká písmena. Pro účely řešení základní typy WPF XAML je velká a malá písmena stejnými pravidly, modul CLR je velká a malá písmena. Elementů objektu, elementy vlastnosti a názvy atributů musí zadat pomocí citlivé malých a velkých písmen při porovnání podle názvu na základní typ v sestavení nebo na člen typu. Klíčová slova jazyka XAML a primitivních elementů jsou také malá a velká písmena. Hodnoty nejsou vždy velká a malá písmena. Rozlišování velikosti písmen pro hodnoty bude záviset na typu konvertoru chování asociovaných s vlastnost, která přebírá hodnotu, nebo typ hodnoty vlastnosti. Například vlastnosti, které provést <xref:System.Boolean> typu můžete provést buď `true` nebo `True` jako ekvivalentní hodnoty, ale pouze, protože převod řetězce na typ analyzátor nativní WPF XAML <xref:System.Boolean> již povoluje jako ekvivalenty.  
  
 WPF XAML procesory a serializátorů bude ignorovat nebo vyřaďte všechny nonsignificant prázdné znaky a bude normalizovat všechny významné prázdné znaky. To je konzistentní s doporučeními výchozí chování mezer – specifikace XAML. Toto chování je obecná pouze z důsledkem při zadávání řetězců v rámci vlastnosti obsahu XAML. Jednoduše řečeno XAML převede znaky, znak odřádkování a kartu znaky mezery a pak najít zachová jednu mezeru, pokud na jednom konci souvislý řetězec. Úplné vysvětlení zpracování prázdných XAML není uvedené v tomto tématu. Podrobnosti najdete v tématu [v XAML je zpracování mezerových znaků](../../xaml-services/whitespace-processing-in-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozšíření značek  
 Rozšíření značek jsou konceptu jazyka XAML. Pokud se použije k poskytnutí hodnoty atributu syntaxe, složené závorky (`{` a `}`) označuje použití rozšíření značky. Toto použití bude směrovat XAML zpracování návrat z obecné zacházení hodnoty atributů jako řetězcový literál nebo hodnotu řetězce převoditelné.  
  
 Nejčastěji používané přípony označení používané [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování aplikací jsou [vazby](binding-markup-extension.md), která se používá pro výrazy vázání dat a odkazy na prostředky [StaticResource](staticresource-markup-extension.md) a [DynamicResource](dynamicresource-markup-extension.md). Pomocí rozšíření značek, slouží k poskytnutí hodnot pro vlastnosti i v případě, že tuto vlastnost nepodporuje syntaxi atributů obecně syntaxe atributu. Typy výrazů zprostředkující – rozšíření značek často používají k povolení funkcí, jako je například odložené hodnoty nebo odkazovat na jiné objekty, které existují pouze v době běhu.  
  
 Například následující kód nastaví hodnotu vlastnosti <xref:System.Windows.FrameworkElement.Style%2A> vlastnost pomocí syntaxe atributu. <xref:System.Windows.FrameworkElement.Style%2A> Vlastnost přebírá instanci <xref:System.Windows.Style> třídu, která ve výchozím nastavení nelze vytvořit instanci řetězcem syntaxe atributu. Ale v takovém případě atribut odkazuje na konkrétní příponě [StaticResource](staticresource-markup-extension.md). Při zpracování tohoto rozšíření značek, vrátí odkaz na styl, který byl dříve vytvořen jako prostředek s klíčem ve slovníku prostředků.  
  
 [!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]  
  
 Referenční seznam všechna rozšíření značek pro XAML implementována konkrétně v subsystému WPF, naleznete v tématu [rozšíření WPF XAML](wpf-xaml-extensions.md). Seznam rozšíření značek, které jsou definovány v oboru názvů System.Xaml a jsou anestezii pro implementace rozhraní .NET Framework XAML, naleznete v tématu [Namespace XAML (x:) Funkce jazyka](../../xaml-services/xaml-namespace-x-language-features.md). Další informace o konceptech rozšíření značek, naleznete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Převaděče typů  
 V [syntaxe XAML přehled](xaml-overview-wpf.md#xaml_syntax_in_brief) oddílu bylo uvedeno, že hodnota atributu musí být možné nastavit řetězcem. Je na základě základní, nativní zpracování řetězce, jak jsou převedeny do jiných typů objektů nebo primitivní hodnoty <xref:System.String> samotného typu, kromě nativní zpracování pro určité typy, jako <xref:System.DateTime> nebo <xref:System.Uri>. Ale mnoho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy nebo členy z těchto typů rozšíření atribut základní řetězce zpracování chování tak, že instance složitější typy objektů lze zadat jako řetězce a atributy.  
  
 <xref:System.Windows.Thickness> Struktura je příkladem typem, který má povolené pro použití XAML převodu typu. <xref:System.Windows.Thickness> Určuje měření v rámci vnořených obdélníku a slouží jako hodnotu vlastnosti, jako <xref:System.Windows.FrameworkElement.Margin%2A>. Umístěním konvertor typu na <xref:System.Windows.Thickness>, všechny vlastnosti, které používají <xref:System.Windows.Thickness> snadněji zadat v XAML, protože mohou být určeny jako atributy. Následující příklad používá k zadání hodnoty pro typ převodu a atribut syntaxe <xref:System.Windows.FrameworkElement.Margin%2A>:  
  
 [!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 Předchozí příklad syntaxe atributu je ekvivalentní následujícímu podrobnější příklad syntaxe, kde <xref:System.Windows.FrameworkElement.Margin%2A> místo toho nastavit pomocí obsahující syntaxe elementu vlastnosti <xref:System.Windows.Thickness> elementu objektu. Čtyři klíčové vlastnosti z <xref:System.Windows.Thickness> jsou nastavené jako atributy v nové instanci:  
  
 [!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  Existují také omezený počet objektů, kde je jediný veřejný způsob, jak nastavit vlastnost pro daný typ bez zásahu podtřídu, protože samotný datový typ nemá výchozí konstruktor převodu typu. Příklad: <xref:System.Windows.Input.Cursor>.  
  
 Další informace o způsobu převodu typu a jeho použití pro atribut syntaxe podporovaná, najdete v článku [TypeConverters a XAML](typeconverters-and-xaml.md).  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## <a name="xaml-root-elements-and-xaml-namespaces"></a>Kořenových elementů XAML a obory názvů XAML  
 Soubor XAML musí mít pouze jeden kořenový element, aby bylo možné oba ve správném formátu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] souboru a platný soubor XAML. Pro typické scénáře WPF je použít kořenový element, který má viditelného význam v modelu aplikace WPF (například <xref:System.Windows.Window> nebo <xref:System.Windows.Controls.Page> pro stránku, <xref:System.Windows.ResourceDictionary> pro externí slovník, nebo <xref:System.Windows.Application> pro definice aplikace). Následující příklad ukazuje typické souboru XAML pro kořenový element [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránka s kořenovým elementem <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 Kořenový element taky obsahuje atributy `xmlns` a `xmlns:x`. Tyto atributy skutečnost XAML procesor, což XAML obory názvů obsahují definice typu pro zálohování typy, které se odkazují značky jako prvky. `xmlns` Atribut konkrétně označuje výchozí obor názvů XAML. V rámci výchozí obor názvů XAML lze zadat objekt elementy v kódu bez předpony. Pro většinu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikačních scénářů a pro téměř všechny uvedené příklady [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oddíly [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], výchozí obor názvů XAML je namapována na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obor názvů [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]. `xmlns:x` Atribut označuje další názvů XAML, který mapuje oboru názvů jazyka XAML [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)].  
  
 Toto použití `xmlns` k definování rozsahu pro využití a mapování obor namescope je konzistentní s specifikace XML 1.0. Obory názvů XAML se liší od obory názvů XML pouze v tom, že obor namescope XAML také znamená něco o jak obor namescope prvky se zálohují na typy při rozhodování o typu řešení a analýzu XAML.  
  
 Všimněte si, `xmlns` atributy jsou jenom nezbytně nutná v kořenovém elementu každého souboru XAML. `xmlns` definice má platit pro všechny následovnické elementy kořenového elementu (Toto chování je konzistentní s specifikace XML 1.0 znovu `xmlns`.) `xmlns` atributy jsou také povolené u další prvky pod kořenovým adresářem a platit na všechny následovnické elementy definující elementu. Ale časté definice nebo opětovná definice oborů názvů XAML může způsobit styl značky XAML, který je obtížné číst.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Provádění jeho procesoru XAML obsahuje infrastrukturu, která má povědomí o WPF sestavení core. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Se ví, že základní sestavení obsahují typy, které podporují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapování na výchozí obor názvů XAML. To zajišťuje konfiguraci, která je součástí vašeho sestavení projektu soubor a WPF sestavení a systémy projektů. Proto deklarace výchozí obor názvů XAML jako výchozí `xmlns` je vše, co je nezbytné, aby se odkazy na prvky XAML, které pocházejí z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení.  
  
### <a name="the-x-prefix"></a>Předpona x:  
 V předchozím příkladu kořenový element, předpona `x:` byl použit k mapování oboru názvů XAML [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)], což je vyhrazený obor názvů XAML, který podporuje jazyk XAML vytvoří. To `x:` předpona se používá pro tento obor názvů XAML v šablonách projektů, příklady a dokumentaci v rámci tohoto mapování [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Obor názvů XAML pro jazyk XAML obsahuje několik programovací konstrukce, které se často používají ve vaší XAML. Tady je seznam nejčastěji používaných `x:` předpony programovací konstrukce, které budete používat:  
  
- [x: Key](../../xaml-services/x-key-directive.md): Nastaví jedinečný klíč pro každý zdroj v <xref:System.Windows.ResourceDictionary> (nebo podobné slovníku koncepty v jiných rozhraní). `x:Key` pravděpodobně bude účet 90 % `x:` použití, zobrazí se v typické aplikaci WPF kódu.  
  
- [x: Class](../../xaml-services/x-class-directive.md): Určuje, [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obor názvů a název třídy pro třídu, která poskytuje kódu na pozadí stránky XAML. Musí mít třídu pro podporu modelu code-behind na programovací model WPF, a proto se téměř vždy zobrazí `x:` mapována, i když nejsou žádné prostředky.  
  
- [x: Name](../../xaml-services/x-name-directive.md): Určuje název run-time objekt instance, která existuje v kódu v době spuštění po zpracování elementu objektu. Obecně platí, často použijete WPF definován odpovídající vlastnost pro [x: Name](../../xaml-services/x-name-directive.md). Tyto vlastnosti mapování speciálně pro CLR zálohování vlastnost a jsou proto vhodnější pro programování aplikací, kde často používáte kódu v době běhu k nalezení pojmenované elementy ve inicializované XAML. Tato vlastnost je nejběžnější <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>. Mohou přesto používat [x: Name](../../xaml-services/x-name-directive.md) při ekvivalentní WPF úrovni framework <xref:System.Windows.FrameworkElement.Name%2A> vlastnost není podporována v určitého typu. K tomu dochází v některých scénářích animace.  
  
- [x: Static](../../xaml-services/x-static-markup-extension.md): Umožňuje odkaz, který vrací hodnotu statické, jinak není kompatibilní s XAML vlastností.  
  
- [x:Type](../../xaml-services/x-type-markup-extension.md): Vytvoří <xref:System.Type> odkaz založen na názvu typu. To je možné určit atributy, které mají <xref:System.Type>, jako <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>, i když často vlastnost má nativní řetězec – k –<xref:System.Type> převod takovým způsobem, který [x: Type](../../xaml-services/x-type-markup-extension.md) se použití rozšíření značky volitelné.  
  
 Existují další programovací konstrukce v `x:` názvů předponu/XAML, který nejsou jako běžné. Podrobnosti najdete v tématu [Namespace XAML (x:) Funkce jazyka](../../xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Vlastní typy v XAML a vlastní předpony  
 Vlastní sestavení nebo sestavení mimo jádro WPF PresentationCore, PresentationFramework a WindowsBase, můžete zadat sestavení jako součást vlastní `xmlns` mapování. Tak dlouho, dokud tento typ je správná implementace pro podporu použití XAML, který se pokoušíte, můžete pak referenční typy v tomto sestavení ve vaší XAML.  
  
 Následuje příklad velmi základní jak vlastní pracovní předpony v kódu XAML. Předpona, která `custom` je definována v tagu kořenového prvku a namapované na konkrétní sestavení, které je zabalená a k dispozici v aplikaci. Toto sestavení obsahuje typ `NumericUpDown`, která je implementována pro podporu obecné použití XAML a jak používat dědičnost tříd, který umožňuje jeho vložení v tomto konkrétním okamžiku model obsahu WPF XAML. Instanci tohoto objektu `NumericUpDown` ovládací prvek je deklarován jako element objektu, tak, aby analyzátoru XAML ví, které XAML pomocí předponu oboru názvů obsahuje typ a proto pokud je sestavení zálohování, který obsahuje definici typu.  
  
```  
<Page  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
    xmlns:custom="clr-namespace:NumericUpDownCustomControl;assembly=CustomLibrary"  
    >  
  <StackPanel Name="LayoutRoot">  
    <custom:NumericUpDown Name="numericCtrl1" Width="100" Height="60"/>  
...  
  </StackPanel>  
</Page>  
```  
  
 Další informace o vlastních typů v XAML najdete v tématu [XAML a vlastní třídy pro WPF](xaml-and-custom-classes-for-wpf.md).  
  
 Další informace o obory názvů XML a obory názvů pomocného kódu v sestaveních, jak souvisí, najdete v části [obory názvů XAML a mapování Namespace pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="events_and_xaml_codebehind"></a>   
## <a name="events-and-xaml-code-behind"></a>Události a kódu XAML  
 Většina [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace skládají z kódu XAML a kódu. V rámci projektu, XAML je zapsán jako `.xaml` souboru a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] jazyka, jako je Microsoft Visual Basic nebo C# se používá k zápisu do souboru kódu na pozadí. Při kompilaci modely programování a aplikace WPF v rámci kódu je soubor XAML, umístění kódu XAML soubor pro soubor XAML je identifikován zadání oboru názvů a třídy jako `x:Class` atribut kořenového prvku XAML.  
  
 V příkladech zatím jste viděli několik tlačítek, ale žádná z těchto tlačítek měli všechny logické chování asociovaných s nimi ještě. Primární mechanismus úrovni aplikace pro přidání chování pro prvek objektu je používat existující událost třídy prvek a zapisovat obslužná rutina specifická pro tuto událost, která je volána, když tuto událost je aktivována v době běhu. Název události a název obslužné rutiny použití jsou uvedeny v kódu, zatímco kód, který implementuje vaše obslužná rutina je definován v modelu code-behind.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 Všimněte si, že soubor kódu na pozadí používá obor názvů CLR `ExampleNamespace` a deklaruje `ExamplePage` jako částečné třídy v daném oboru názvů. To je paralelní `x:Class` hodnotu atributu `ExampleNamespace`.`ExamplePage` který byl součástí kořenové značky. Kompilátor kód WPF vytvoří částečnou třídu pro všechny kompilovaný soubor XAML, odvozením třídy od typ kořenového elementu. Když zadáte kód na pozadí, který definuje také stejné částečné třídy, je výsledný kód kombinovat v rámci stejného oboru názvů a třídy zkompilované aplikace.  
  
 Další informace o požadavcích pro použití modelu code-behind programování v subsystému WPF, najdete v části "použití modelu Code-behind, obslužné rutiny události a požadavky na částečné třídy" [použití modelu Code-Behind a XAML v subsystému WPF](code-behind-and-xaml-in-wpf.md).  
  
 Pokud nechcete vytvořit soubor samostatné kódu, můžete také vloženého kódu v souboru XAML. Vložený kód je však méně univerzální technika, která má podstatné omezení. Podrobnosti najdete v tématu [použití modelu Code-Behind a XAML v subsystému WPF](code-behind-and-xaml-in-wpf.md).  
  
### <a name="routed-events"></a>Směrované události  
 Funkce konkrétní událost, která je nezbytné k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je směrované události. Směrování událostí povolit prvek, který chcete zpracovat událost, která byla vygenerována jiný element, za předpokladu, prvky jsou propojeny pomocí vztahu stromu. Při zadávání XAML atributu zpracování událostí, můžete směrované události naslouchali u a zpracování na libovolný element, včetně prvků, které danou událost v tabulce členů třídy do seznam úkolů. Toho lze dosáhnout kvalifikující události atribut name vlastnící názvu třídy. Například nadřazené `StackPanel` v probíhající `StackPanel`  /  `Button` příkladu by se mohl zaregistrovat obslužnou rutinu pro tlačítko podřízený element <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události zadáním atributu `Button.Click` na `StackPanel` element Object, názvem vaší obslužné rutiny jako hodnota atributu. Další informace o jak směrované události práce, naleznete v tématu [směrovat Přehled událostí](routed-events-overview.md).  
  
<a name="x_name_and_xaml_named_elements"></a>   
## <a name="xaml-named-elements"></a>S názvem prvky XAML  
 Ve výchozím nastavení instanci objektu, který je vytvořen v grafu objektů pomocí zpracování elementu objektu XAML nemá jedinečný identifikátor nebo odkaz na objekt. Naproti tomu při volání konstruktoru v kódu, je téměř vždy měli používat výsledek konstruktoru k nastavení proměnné na konstruovaný instanci tak, aby později ve svém kódu můžete odkazovat na instanci. Aby bylo možné poskytovat standardizovaný přístup k objektům, které byly vytvořeny pomocí definice značek XAML definuje [x: Name – atribut](../../xaml-services/x-name-directive.md). Můžete nastavit hodnotu `x:Name` atribut u libovolného elementu objektu. Do vašeho kódu na pozadí je ekvivalentní proměnnou instance, který odkazuje na konstruovaný instance identifikátoru, který zvolíte. Ve všech ohledech s názvem elementy funkce, jako kdyby byly instance objektů (název odkazuje na tuto instanci) a vaše použití modelu code-behind odkazovat pojmenované elementy pro zpracování běhu interakce v rámci aplikace. Toto připojení mezi instancemi a proměnné se provádí kompilátorem značky XAML WPF a více konkrétně zahrnuje funkce a vzorů, jako <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> , které nebudou popsány podrobně v tomto tématu.  
  
 Dědit elementy XAML úrovni rozhraní WPF <xref:System.Windows.FrameworkElement.Name%2A> vlastnost, která je ekvivalentní k XAML definované `x:Name` atribut. Určité třídy také poskytují ekvivalenty úroveň vlastnosti `x:Name`, který je obvykle také definován jako `Name` vlastnost. Obecně vzato Pokud nemůžete najít `Name` v tabulce členů pro váš zvolený element/typ, použijte vlastnost `x:Name` místo. `x:Name` Hodnoty poskytne identifikátor pro prvek XAML, který lze použít v době běhu, určité subsystémy nebo pomocné metody, jako <xref:System.Windows.FrameworkElement.FindName%2A>.  
  
 Následující příklad nastaví <xref:System.Windows.FrameworkElement.Name%2A> na <xref:System.Windows.Controls.StackPanel> elementu. Potom obslužné rutiny na <xref:System.Windows.Controls.Button> , které <xref:System.Windows.Controls.StackPanel> odkazy <xref:System.Windows.Controls.StackPanel> prostřednictvím odkazu na instanci `buttonContainer` jako nastavte podle <xref:System.Windows.FrameworkElement.Name%2A>.  
  
 [!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 Stejně jako proměnnou je název XAML pro instanci řídí koncept oboru, tak, aby názvy je možné vynutit být jedinečný v rámci oboru, který předvídatelné. Primární kód, který definuje stránku označuje jeden jedinečný namescope XAML s hranici namescope XAML se kořenový element této stránce. Však jiných zdrojů značek můžete pracovat se stránkou v době běhu, jako je například stylů a šablon v rámci stylů, a tyto zdroje značek často mají své vlastní obory názvů XAML, která se nepřipojují nutně s XAML namescope stránky. Další informace o `x:Name` a obory názvů XAML, naleznete v tématu <xref:System.Windows.FrameworkElement.Name%2A>, [x: Name – direktiva](../../xaml-services/x-name-directive.md), nebo [obory názvů WPF XAML](wpf-xaml-namescopes.md).  
  
<a name="attached_properties_and_attached_events"></a>   
## <a name="attached-properties-and-attached-events"></a>Připojené vlastnosti a přidružené události  
 XAML Určuje jazyk funkce, která umožňuje určité vlastnosti nebo události, které mají zadaný u libovolného elementu, bez ohledu na to, zda existuje vlastnost nebo událost v definicích typu pro element, který se nastavuje na. Vlastnosti verze této funkce se nazývá připojené vlastnosti, události verze se nazývá přidružená událost. Koncepčně si můžete představit připojené vlastnosti a připojené události jako globální členy, které lze nastavit na libovolnou instanci elementu/objektu XAML. Však element/třídy nebo větší infrastruktury musí podporovat záložní úložiště vlastností pro připojené hodnoty.  
  
 Připojené vlastnosti v XAML se obvykle používají prostřednictvím syntaxe atributu. V syntaxi atributu, určíte připojené vlastnosti ve formě *ownerType*. *Vlastnost propertyName*.  
  
 Na první pohled, to se podobá použití elementu vlastnosti, ale v tomto případě *ownerType* zadáte, je vždy jiný atribut type než element objektu ve kterém se nastavuje připojená vlastnost. *ownerType* je typ, který poskytuje přístupové metody, které jsou vyžadované XAML procesoru, aby bylo možné získat nebo nastavit hodnotu přidružené vlastnosti.  
  
 Nejběžnější scénář pro připojené vlastnosti je umožnit podřízené prvky informuje hodnotu vlastnosti svého nadřazeného elementu.  
  
 Následující příklad ukazuje, <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> přidružená vlastnost. <xref:System.Windows.Controls.DockPanel> Třída definuje přístupové objekty pro <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> a proto je vlastníkem připojená vlastnost. <xref:System.Windows.Controls.DockPanel> Třída také obsahuje logiku, která iteruje jeho podřízené prvky a konkrétně zkontroluje každý prvek pro nastavte hodnotu identifikátoru <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Pokud hodnotu nenajde, tato hodnota umožňuje během rozložení umístění podřízených elementů. Použití <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> připojené vlastnosti a tato umístění funkce je ve skutečnosti motivačním scénář <xref:System.Windows.Controls.DockPanel> třídy.  
  
 [!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], většinu nebo všechny připojené vlastnosti jsou také implementovány jako vlastnosti závislosti. Podrobnosti najdete v tématu [přehled připojených vlastností](attached-properties-overview.md).  
  
 Připojené události použijte podobný *ownerType*. *eventName* forma syntaxe atributu. Hodnota atributu přidružená událost v XAML stejně jako události nepřipojené Určuje název obslužné metody, která je volána, když událost zpracovává u elementu. Připojené události ve WPF XAML je méně častý. Další informace najdete v tématu [přehled připojených událostí](attached-events-overview.md).  
  
<a name="base_classes_and_xaml"></a>   
## <a name="base-types-and-xaml"></a>Základní typy a XAML  
 Základní WPF XAML a její obor názvů XAML je kolekce typů, které odpovídají [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektů včetně elementy značek pro XAML. Ale ne všechny třídy lze mapovat na elementy. Abstraktní třídy, jako například <xref:System.Windows.Controls.Primitives.ButtonBase>, a používají se pro dědičnosti v určité neabstraktní základní třídy [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty modelu. Základní třídy, včetně těch abstraktní, jsou stále potřeba vývoje XAML, protože jednotlivých konkrétních prvků XAML dědí členy z některé základní třídy v hierarchii. Často tyto členy obsahují vlastnosti, které můžete nastavit jako atributy elementu nebo události, které mohou být zpracovány. <xref:System.Windows.FrameworkElement> je konkrétní základní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] třídu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na úrovni rozhraní WPF. Při navrhování [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], budete používat různé tvar, panely, dekoratér nebo třídy ovládacích prvků, které všechny odvozené z <xref:System.Windows.FrameworkElement>. Související základní třídu, <xref:System.Windows.FrameworkContentElement>, podporuje dokumentově orientované prvky, které fungují dobře pro prezentaci rozložení tok pomocí [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] , která záměrně zrcadlit [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] v <xref:System.Windows.FrameworkElement>. Kombinace atributů na úrovni prvku a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektový model poskytuje sadu společných vlastností, které jsou nastavitelná při čekání na nejvíce konkrétní prvky XAML, bez ohledu na konkrétní elementu XAML a jeho nadřízeného typu.  
  
<a name="xaml_security"></a>   
## <a name="xaml-security"></a>Zabezpečení XAML  
 XAML je značkovací jazyk, který představuje přímo vytváření instancí objektu a spuštění. Proto prvků vytvořených v XAML se stejnou moct pracovat s prostředky systému (třeba síťový přístup, v/v souborů systému) jako ekvivalentní, vygeneruje kód provádí.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje rozhraní .NET Framework 4 zabezpečení [!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)]. To znamená, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah spuštěný v zóně internet má omezená oprávnění k provádění. "Volný XAML" (stránek XAML noncompiled interpretuje v okamžiku načtení pomocí prohlížeče XAML) a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] jsou obvykle spouštěny v této zóně internet a používá stejnou sadu oprávnění.  XAML načteno do plně důvěryhodné aplikaci v ale má stejný přístup k systémovým prostředkům stejně jako hostitelské aplikace. Další informace najdete v tématu [částečné zabezpečení důvěryhodnosti WPF](../wpf-partial-trust-security.md).  
  
<a name="loading_xaml_from_code"></a>   
## <a name="loading-xaml-from-code"></a>Načítání z kódu XAML  
 XAML lze použít k definování všech uživatelského rozhraní, ale je někdy také vhodné definovat pouze část uživatelského rozhraní v XAML. Tato funkce se používal k povolení částečné přizpůsobení, informace, pomocí XAML, které poskytují obchodní objekt nebo širokou škálu možných scénářů místního úložiště. Klíčem k scénářů je <xref:System.Windows.Markup.XamlReader> třídy a jeho <xref:System.Windows.Markup.XamlReader.Load%2A> metoda. Soubor XAML je vstup a výstup je objekt, který představuje všechny za běhu strom objektů, který byl vytvořen z těchto značek. Potom můžete vložit objekt, který má být vlastnost jiného objektu, který již existuje v aplikaci. Pokud je vlastnost odpovídající vlastnost v modelu obsahu, který má konečnou zobrazení možnosti a, která upozorní prováděcího modulu, aby se přidal nový obsah do aplikace, můžete upravit obsah běžící aplikaci velmi snadno podle načítání v XAML. Všimněte si, že tato funkce je obecně k dispozici pouze v plně důvěryhodné aplikace, z důvodu ze zřejmých bezpečnostních důsledcích načítání souborů do aplikace za běhu.  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>Co se chystá  
 Toto téma obsahuje základní informace o konceptech syntaxe XAML a terminologii, protože se vztahuje k použití WPF. Další informace o termíny používané zde najdete v tématu [syntaxe XAML v podrobnosti o](xaml-syntax-in-detail.md).  
  
 Pokud jste to ještě neudělali, zkuste praktická cvičení v tématu výukového [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Při vytváření zaměřené na kód aplikace je popsáno v kurzu výkonu vám pomůže posílit mnoho popsaných konceptů popsaných v tomto tématu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá model konkrétní aplikaci, která je založena na <xref:System.Windows.Application> třídy. Podrobnosti najdete v tématu [přehled správy aplikací](../app-development/application-management-overview.md).  
  
 [Sestavení aplikace WPF](../app-development/building-a-wpf-application-wpf.md) poskytuje další podrobnosti o tom, jak vytvářet aplikace XAML (včetně) z příkazového řádku a s [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
 [Přehled vlastností závislosti](dependency-properties-overview.md) obsahuje bližší informace o všestrannost vlastností v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a zavádí koncepci vlastnosti závislosti.  
  
## <a name="see-also"></a>Viz také:

- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
- [XAML a vlastní třídy pro WPF](xaml-and-custom-classes-for-wpf.md)
- [Namespace XAML (x:) Jazykové funkce](../../xaml-services/xaml-namespace-x-language-features.md)
- [Rozšíření WPF XAML](wpf-xaml-extensions.md)
- [Přehled základních elementů](base-elements-overview.md)
- [Stromy v subsystému WPF](trees-in-wpf.md)
