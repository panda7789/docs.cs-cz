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
ms.openlocfilehash: 7093511906ca877af8285e5d7234cb5bc7e99a72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549721"
---
# <a name="xaml-overview-wpf"></a>Přehled XAML (WPF)
Toto téma popisuje funkce jazyka XAML a ukazuje, jak můžete použít XAML pro zápis [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace. Toto téma popisuje XAML konkrétně, jak je implementované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. XAML samotné je větší koncept jazyk než [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
  
  
<a name="what_is_xaml"></a>   
## <a name="what-is-xaml"></a>Co je XAML?  
 XAML je deklarativní jazyk. Jako použít pro programovací model rozhraní .NET Framework, XAML zjednodušuje vytváření [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro aplikace .NET Framework. Můžete vytvořit viditelné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy v deklarativní XAML a pak samostatné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] definice z logiky běhu pomocí kódu souborů, připojený k kód prostřednictvím definice třídu. XAML přímo představuje vytváření instancí objektů v konkrétní sadu zálohování typy definované v sestavení. To je rozdíl oproti většina jiných značek jazyky, které jsou obvykle interpretovaný jazyk bez přímé vazbě na systém typ zálohování. Umožňuje XAML pracovního postupu, kde můžete samostatné strany pracovat na [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a logiku aplikace, pomocí potenciálně různých nástrojů.  
  
 Při reprezentován jako text, jsou soubory XAML soubory XML, které mají obvykle `.xaml` rozšíření. Soubory mohou být zakódován žádné XML kódování, ale kódování v typických UTF-8.  
  
 Následující příklad ukazuje, jak je možné vytvořit tlačítko jako součást [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Tento příklad je určen pouze získáte příchuť o tom, jak představuje běžné XAML [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] programování metaphors (není ucelenou ukázku).  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## <a name="xaml-syntax-in-brief"></a>Syntaxe jazyka XAML v Brief  
 Následující části popisují základní formy syntaxe jazyka XAML a poskytněte příklad krátký kód. Tyto části nejsou určené k poskytnutí úplné informace o jednotlivých syntaxe formuláře, například jak jsou reprezentována v systému typ zálohování. Další informace o jaké jsou specifikace syntaxe jazyka XAML pro každou z formuláře syntaxe představenými v tomto tématu najdete v tématu [XAML syntaxe v podrobností](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Velká část informací v následujících částech několik bude základní pro vás, pokud máte předchozí znalost jazyka XML. Toto je důsledkem principů základní návrhu XAML.  Jazyk XAML definuje vlastní koncepty, ale tyto koncepty pracovat v rámci formuláře jazyk a značek XML.  
  
### <a name="xaml-object-elements"></a>Objekt elementů XAML  
 Element objekt obvykle deklaruje instanci typu. Tento typ je definována v sestavení, které poskytují základní typy pro technologie, která používá jako jazyk XAML.  
  
 Syntaxe objektu element vždy začíná úhel levou hranatou závorku (\<). Následuje název typu ve které chcete vytvořit instanci. (Název může obsahovat pravděpodobně předponu konceptu, které bude vysvětleno později.) Poté můžete volitelně deklarovat atributy na objekt elementu. Dokončete element značky object končit ukončovací lomená závorka (>). Místo toho můžete samouzavírací formulář, který nemá žádný obsah tak, že dokončení značky s lomítkem a ukončovací lomená závorka po sobě (/ >). Například podívejte se na fragmentu kódu dříve uvedené znovu:  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 Toto nastavení určuje dva elementy objektu: `<StackPanel>` (s obsah a koncovou značku později), a `<Button .../>` (samouzavírací formulář, s několika atributy). Elementy objektu `StackPanel` a `Button` každé mapování pro název třídy, který je definován [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení. Když zadáte značky elementu, můžete vytvořit instrukce pro jazyk XAML zpracování pro vytvoření nové instance. Každá instance se vytvoří při volání konstruktoru výchozí základní typ při analýze a načítání XAML.  
  
### <a name="attribute-syntax-properties"></a>Atribut syntaxe (Vlastnosti)  
 Vlastnosti objektu může být často vyjádřený jako atributy objektu elementu. Atributu syntaxe názvy vlastnost, která se nastavuje v atributu syntaxi, za nímž následuje operátor přiřazení (=). Hodnota atributu je vždy určen jako řetězec, který je obsažený v uvozovkách.  
  
 Atribut syntaxe je nejvíce zjednodušenou syntaxi nastavení vlastností a nejvíce intuitivní syntaxe pro vývojáře, kteří použili jazyky značek v minulosti. Například následující kód vytvoří tlačítko, které má červený text a modré pozadí kromě zobrazovaný text zadaný jako `Content`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### <a name="property-element-syntax"></a>Vlastnost Element syntaxe  
 Pro některé vlastnosti objektu elementu syntaxe atributu není možné, protože objekt nebo informace potřebné k zajištění hodnotu vlastnosti nelze vyjádřit adekvátní v rámci omezení řetězec atributu syntaxe a uvozovky. Pro tyto případy lze použít jinou syntaxi označuje jako vlastnost element syntaxe.  
  
 Tady je syntax u počáteční značky elementu vlastnost `<` *typeName*`.`*propertyName*`>`. Obsah této značky je obecně element objekt s typem, který vlastnost přijímá jako jeho hodnotu. Po zadání obsahu, je třeba nejprve zavřít element vlastnost s koncovou značku. Tady je syntax koncová značka `</` *typeName*`.`*propertyName*`>`.  
  
 Pokud syntaxe atribut je možné, pomocí syntaxe atribut je obvykle pohodlnější a umožňuje kompaktnější značek, ale který je často jenom řádu styl, není technická omezení. Následující příklad ukazuje stejné vlastnosti se nastavuje jako předchozí příklad syntaxe atribut, ale tentokrát pomocí syntaxe element vlastnost pro všechny vlastnosti `Button`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButtonPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### <a name="collection-syntax"></a>Syntaxe kolekce  
 Jazyk XAML obsahuje některé optimalizace, které vytváří více čitelná pro člověka značek. Jeden takový optimalizace je, že pokud určité vlastnosti trvá typu kolekce, pak položky, které je deklarovat ve značce jako podřízených elementů v rámci této vlastnosti hodnotu stát součástí kolekce. Kolekce podřízených elementů objekt v tomto případě je hodnota je nastavená na vlastnost kolekce.  
  
 Následující příklad ukazuje syntaxi kolekce pro nastavení hodnot <xref:System.Windows.Media.GradientBrush.GradientStops%2A> vlastnost:  
  
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
 XAML Určuje jazyk funkce, které třídy můžete určit právě jeden z jeho vlastnosti jako vlastnosti obsahu XAML. Podřízené elementy elementu tohoto objektu se používají k nastavit hodnotu této vlastnosti obsahu. Jinými slovy pro vlastnost obsahu jednoznačně, můžete vynechat element vlastnosti při nastavení této vlastnosti ve XAML značek a vytvořit více viditelných jedná nadřazených a podřízených ve značkách.  
  
 Například <xref:System.Windows.Controls.Border> určuje obsahu vlastnost <xref:System.Windows.Controls.Decorator.Child%2A>. Následující dva <xref:System.Windows.Controls.Border> prvky jsou považovány shodně. První z nich využívá syntaxi vlastnost obsahu a vynechá `Border.Child` element vlastnosti. Druhý zobrazí `Border.Child` explicitně.  
  
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
  
 Platí, jazyka XAML musí být hodnota vlastnosti obsahu XAML uvedeny zcela před nebo po další prvky vlastnost zcela na tento objekt elementu. Například následující kód nelze kompilovat:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Další informace o toto omezení na vlastnosti obsahu XAML najdete v části "Vlastnosti obsahu XAML" [XAML syntaxe v podrobností](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
### <a name="text-content"></a>Obsah textu  
 Malý počet elementů XAML přímo může zpracovat text jako jejich obsah. Chcete-li povolit, jednu z následujících případech musí být splněné:  
  
-   Třída musí deklarovat vlastnost obsahu a že vlastnost obsahu musí být typu přiřaditelný k řetězec (může být typ <xref:System.Object>). Například některé <xref:System.Windows.Controls.ContentControl> používá <xref:System.Windows.Controls.ContentControl.Content%2A> , protože jeho vlastnost obsahu a je typu <xref:System.Object>, a to podporuje následující využití na praktická <xref:System.Windows.Controls.ContentControl> například <xref:System.Windows.Controls.Button>: `<Button>Hello</Button>`.  
  
-   Typ musí deklarovat převaděče typu, ve kterém případ textového obsahu se používá jako text inicializace pro tento převaděč typů. Například `<Brush>Blue</Brush>`. Tento případ je méně častých v praxi.  
  
-   Typ musí být známé jazyk XAML primitivní.  
  
### <a name="content-properties-and-collection-syntax-combined"></a>Kolekce syntaxi kombinaci a vlastnosti obsahu  
 Vezměte v úvahu v tomto příkladu:  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 Zde každý <xref:System.Windows.Controls.Button> je podřízený prvek <xref:System.Windows.Controls.StackPanel>. Toto je zjednodušený a intuitivní značky, která vynechá dvě značky pro dva různé důvody.  
  
-   **Není zadán element vlastnosti StackPanel.Children:** <xref:System.Windows.Controls.StackPanel> je odvozena z <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel> definuje <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> jako jeho XAML obsahu vlastnost.  
  
-   **Není zadán element object UIElementCollection:** <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> vlastnost trvá typ <xref:System.Windows.Controls.UIElementCollection>, který implementuje <xref:System.Collections.IList>. Značky elementu kolekce lze vynechat, na základě pravidel XAML pro zpracování kolekcí, jako <xref:System.Collections.IList>. (V tomto případě <xref:System.Windows.Controls.UIElementCollection> ve skutečnosti nelze vytvořit instance, protože nevystavuje výchozí konstruktor, a proto <xref:System.Windows.Controls.UIElementCollection> object element se zobrazí komentovaný out).  
  
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
  
### <a name="attribute-syntax-events"></a>Atribut syntaxe (událostí)  
 Pro členy, kteří jsou události a nikoli vlastnosti se lze také atribut syntaxe. Název atributu je v tomto případě název události. Implementace WPF události pro jazyk XAML je hodnota atributu název obslužné rutiny, který implementuje tuto událost delegáta. Například následující kód přiřadí obslužnou rutinu pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události <xref:System.Windows.Controls.Button> vytvořené v značek:  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 Je na události a XAML v grafickém subsystému WPF víc než tento příklad syntaxe atributu. Například může zajímat, co `ClickHandler` zde odkazuje představuje a jak je definována. To se vysvětluje v nadcházející akce [události a kódu XAML](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#events_and_xaml_codebehind) části tohoto tématu.  
  
<a name="case_and_whitespace_in_xaml"></a>   
## <a name="case-and-whitespace-in-xaml"></a>Případ a prázdných znaků v jazyce XAML  
 XAML je obecně velká a malá písmena. Pro účely překladu typy zálohování je WPF XAML velká a malá písmena stejné pravidly, že modulu CLR je malá a velká písmena. Objekt prvky, vlastnost elementy a názvy atributů musí zadat pomocí citlivé malá a velká písmena při porovnání s názvem základní typ v sestavení nebo člena typu. Klíčová slova jazyka XAML a primitiv jsou také velká a malá písmena. Hodnoty nejsou vždy velká a malá písmena. Rozlišování velkých a malých písmen pro hodnoty bude záviset na typu chování převaděč přidružená vlastnost, která přebírá hodnotu nebo typ hodnoty vlastnosti. Například vlastnosti, které provést <xref:System.Boolean> typ může trvat buď `true` nebo `True` jako ekvivalentní hodnoty, ale pouze, protože nativní analyzátor WPF XAML konverze typu pro řetězec, který má <xref:System.Boolean> již umožňuje jako ekvivalenty.  
  
 WPF XAML procesory a serializátorů bude ignorovat nebo vyřadit všechny nonsignificant prázdný znak a bude normalizaci žádné významný mezerový znak. To je konzistentní s doporučeními výchozí prázdné chování specifikace XAML. Toto chování je obecně jenom z důsledkem při zadávání řetězce v rámci vlastnosti obsahu XAML. Jednoduše řečeno XAML převede místa, konce řádku a karta znaky mezery a pak uchovává jeden místo, pokud nalezen na libovolném konci souvislý řetězec. Úplné vysvětlení zpracování prázdných znaků XAML není zahrnutý v tomto tématu. Podrobnosti najdete v tématu [zpracování prázdných znaků v jazyce XAML](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozšíření značek  
 Rozšíření značek jsou koncept jazyka XAML. Pokud se použije k zadejte hodnotu atributu syntaxe a složené závorky (`{` a `}`) označuje použití rozšíření značek. Toto použití bude směrovat XAML zpracování k návratu z obecné způsob zpracování hodnot atributu jako řetězcový literál nebo hodnotu řetězce převoditelné.  
  
 Nejběžnější rozšíření značek, které jsou používány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování aplikací jsou [vazby](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)používané k výrazy vazby dat a odkazy na prostředek [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) a [DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Pomocí rozšíření značek můžete zadat hodnoty pro vlastnosti, i když tuto vlastnost nepodporuje syntaxi atributů obecně syntaxe atributu. Typy výrazů zprostředkující rozšíření značek často používají k povolení funkcí, jako je například odložit hodnoty nebo odkazy na další objekty, které se nacházejí pouze v době běhu.  
  
 Například následující kód nastaví hodnotu <xref:System.Windows.FrameworkElement.Style%2A> vlastnost pomocí syntaxe atribut. <xref:System.Windows.FrameworkElement.Style%2A> Vlastnost přijímá instanci <xref:System.Windows.Style> třídy, která ve výchozím nastavení nelze vytvořit instanci pomocí syntaxe řetězec atributu. V takovém případě atribut odkazuje na příponu konkrétní značek, ale [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Při zpracování této – rozšíření značek vrátí odkaz na styl, která byla dříve vytvořena instance jako prostředek s klíčem ve slovníku prostředků.  
  
 [!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]  
  
 Referenční seznam všech rozšíření značek pro jazyk XAML implementována konkrétně v grafickém subsystému WPF, najdete v části [WPF XAML rozšíření](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md). Seznam referenční rozšíření značek, které jsou definovány System.Xaml a jsou více široce dostupné pro implementace rozhraní .NET Framework XAML najdete v tématu [Namespace XAML (x:) Jazykové funkce](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md). Další informace o konceptech rozšíření značek najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Převaděče typů  
 V [XAML syntaxi Brief](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#xaml_syntax_in_brief) části bylo uvedeno, že musí být hodnota atributu může být nastavovat řetězce. Je na základě základní, nativní ošetření jak řetězce se převedou na další typy objektů nebo primitivní hodnoty <xref:System.String> zadejte sám sebe, kromě nativní zpracování pro určité typy, jako <xref:System.DateTime> nebo <xref:System.Uri>. Ale mnoho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy nebo členy z těchto typů rozšířit atribut základní řetězce zpracování chování tak, že instance složitější typy objektů lze zadat jako řetězce a atributy.  
  
 <xref:System.Windows.Thickness> Struktura je příkladem typ, který má povolené pro použití, XAML převod typů. <xref:System.Windows.Thickness> označuje měření v rámci vnořené obdélníku a slouží jako hodnota vlastnosti, jako <xref:System.Windows.FrameworkElement.Margin%2A>. Umístěním převaděče typů na <xref:System.Windows.Thickness>, všechny vlastnosti, které používají <xref:System.Windows.Thickness> se snadněji určit v jazyce XAML, protože může být zadán jako atributy. Následující příklad používá k zadání hodnoty pro typ převodu a atribut syntaxe <xref:System.Windows.FrameworkElement.Margin%2A>:  
  
 [!code-xaml[XAMLOvwSupport#MarginTCE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 Předchozí příklad atribut syntaxe je ekvivalentní pro následující podrobnější příklad syntaxe, kde <xref:System.Windows.FrameworkElement.Margin%2A> místo toho nastavit pomocí vlastnosti element syntaxe obsahující <xref:System.Windows.Thickness> object element. Čtyři klíče vlastnosti <xref:System.Windows.Thickness> jsou nastavené jako atributy v nové instanci:  
  
 [!code-xaml[XAMLOvwSupport#MarginVerbose](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  Existují také omezený počet objektů, kde převod typu je pouze veřejné způsob, jak nastavit vlastnost typu bez zásahu podtřídy, protože vlastní typ nemá výchozí konstruktor. Příkladem je <xref:System.Windows.Input.Cursor>.  
  
 Další informace o tom, jak převodu typu a jeho použití pro atribut je podporovaná syntaxe najdete v tématu [TypeConverters a XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## <a name="xaml-root-elements-and-xaml-namespaces"></a>Kořenové elementů XAML a obory názvů jazyka XAML  
 Soubor XAML musí mít jenom jeden kořenový element, aby byla obou ve správném formátu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] a platný soubor XAML. Pro typické scénáře WPF, můžete použít kořenový element, který má viditelného význam ve model aplikace WPF (například <xref:System.Windows.Window> nebo <xref:System.Windows.Controls.Page> pro stránku, <xref:System.Windows.ResourceDictionary> pro externí slovník, nebo <xref:System.Windows.Application> pro definici aplikace). Následující příklad ukazuje kořenový element typické souboru XAML pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránka s kořenový prvek <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[XAMLOvwSupport#RootOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xaml[XAMLOvwSupport#RootOnly2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 Kořenový element také obsahuje atributy `xmlns` a `xmlns:x`. Tyto atributy znamenat XAML procesor, který obory názvů jazyka XAML obsahovat definice typů pro zálohování typy, které kód bude odkazovat jako elementy. `xmlns` Atribut konkrétně určuje výchozí obor názvů jazyka XAML. V rámci oboru názvů jazyka XAML výchozí objekt elementy ve značkách lze bez předpony. Pro většinu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] scénáře aplikací a pro téměř všechny příklady v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] části [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], výchozí obor názvů jazyka XAML je namapována na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obor názvů [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]. `xmlns:x` Atribut uvádí další XAML názvů, který mapuje oboru názvů jazyka XAML [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)].  
  
 Toto použití `xmlns` k definování oboru pro využití a mapování namescope je v souladu s specifikace XML 1.0. XAML namescopes se liší od XML namescopes pouze v tomto XAML namescope také znamená něco jak namescope elementy jsou zajišťované typy při přechodu na typ překlad IP adres a analýza XAML.  
  
 Všimněte si, že `xmlns` atributy jsou jenom nezbytně nutná v kořenovém elementu každého souboru XAML. `xmlns` definice budou platit pro všechny následné elementy kořenového prvku (Toto chování je konzistentní s specifikace XML 1.0 pro znovu `xmlns`.) `xmlns` atributy jsou také povolená na další prvky pod kořenovým adresářem a by platí pro všechny následnickým elementům definující elementu. Ale často definice nebo předefinování obory názvů jazyka XAML může způsobit XAML styl značek, které je obtížné číst.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Infrastruktura, která obsahuje informace o základních sestavení WPF obsahuje implementaci jeho XAML procesoru. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Základních sestavení se ví, obsahovat typy, které podporují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapování oboru názvů jazyka XAML výchozí. Tato možnost je povolena prostřednictvím konfigurace, který je součástí vaší sestavení projektu soubor a WPF sestavení a projektu systémy. Proto deklarace oboru názvů jazyka XAML výchozí jako výchozí `xmlns` je všechno, co je nezbytné, aby odkazovat elementů XAML, které pocházejí z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení.  
  
### <a name="the-x-prefix"></a>Předpona x:  
 V předchozím příkladu kořenový element, předponu `x:` byl použit k mapování oboru názvů jazyka XAML [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)], který je vyhrazený oboru názvů jazyka XAML, který podporuje jazyk XAML vytvoří. To `x:` předpona se používá pro mapování tento obor názvů jazyka XAML v šablonách pro projekty, příklady a dokumentaci v rámci to [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Oboru názvů jazyka XAML pro jazyk XAML obsahovat několik programovací konstrukce, které budete používat velmi často ve vašem XAML. Následuje seznam nejobvyklejší `x:` předpony programovací konstrukce, které budete používat:  
  
-   [x: Key](../../../../docs/framework/xaml-services/x-key-directive.md): Nastaví jedinečný klíč pro každý zdroj v <xref:System.Windows.ResourceDictionary> (nebo podobné slovník koncepty v jiných rozhraní). `x:Key` pravděpodobně bude účet pro 90 % `x:` použití, zobrazí se v typické aplikaci WPF značek.  
  
-   [x: Class –](../../../../docs/framework/xaml-services/x-class-directive.md): Určuje [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obor názvů a třídy pro třídu, která poskytuje kódu stránky XAML. Třídy pro podporu kódu podle programovacího modelu WPF musí mít, a proto téměř vždy zobrazí `x:` namapované, i když nejsou žádné prostředky.  
  
-   [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md): Určuje název běhového objektu pro instanci, která existuje v běhu kódu po zpracování objektu elementu. Obecně platí, často použijete definované WPF ekvivalentní vlastnost pro [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md). Tyto vlastnosti namapovat konkrétně CLR, zálohování vlastnosti a jsou tedy pohodlnější pro programování aplikací, kde je často běhu kódu vyhledat pomocí pojmenovaného elementy z inicializovaného XAML. Nejběžnější tato vlastnost je <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>. Mohou přesto používat [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md) při ekvivalentní WPF úrovni framework <xref:System.Windows.FrameworkElement.Name%2A> vlastnost není podporována v konkrétní typ. K tomu dochází v některých scénářích animace.  
  
-   [x: Static](../../../../docs/framework/xaml-services/x-static-markup-extension.md): umožňuje odkaz, který vrátí statickou hodnotu, která není jinak vlastnost XAML kompatibilní.  
  
-   [x: Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md): vytvoří <xref:System.Type> odkaz založen na názvu typu. To slouží k určení atributy, které mají <xref:System.Type>, jako <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>, i když často vlastnost má nativní řetězec-na-<xref:System.Type> převod tak, který [x: Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md) využití rozšíření značek Volitelný parametr.  
  
 Existují další programovací konstrukce v `x:` oboru názvů předponu/jazyka XAML, které nejsou jako společné. Podrobnosti najdete v tématu [Namespace XAML (x:) Jazykové funkce](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Vlastní předpony a vlastních typů v jazyce XAML  
 Pro vlastní vlastní sestavení, nebo sestavení mimo základní WPF PresentationCore, PresentationFramework a WindowsBase, můžete zadat sestavení jako součást vlastní `xmlns` mapování. Pak můžete odkazovat typy z tohoto sestavení v XAML, tak dlouho, dokud tento typ je správně implementována pro podporu použití XAML, který se pokoušíte.  
  
 Následuje velmi základních příkladů jak vlastní pracovní předpony v XAML značek. Předpona `custom` je definované ve značce elementu kořenové a namapovat na konkrétní sestavení, která je dostupná s aplikací a zabalené. Toto sestavení obsahuje typ `NumericUpDown`, která je implementována pro podporu obecné použití XAML a také pomocí dědičnost třídy, která umožňuje jeho vložení v tomto okamžiku konkrétní modelu obsahu WPF XAML. Instanci tohoto objektu `NumericUpDown` ovládací prvek je deklarovaný jako objekt element, pomocí předponu, aby XAML analyzátor věděla, které XAML obor názvů obsahuje typ a proto kde je základní sestavení obsahující definici typu.  
  
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
  
 Další informace o vlastních typů v jazyce XAML najdete v tématu [XAML a vlastní třídy pro grafický subsystém WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
 Další informace o obory názvů XML a obory názvů kód základní sestavení jak souvisí, najdete v části [obory názvů jazyka XAML a Namespace mapování pro jazyk XAML WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="events_and_xaml_codebehind"></a>   
## <a name="events-and-xaml-code-behind"></a>Události a kódu XAML  
 Většina [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace se skládají z XAML značek a kódu. V projektu, je zapsán XAML jako `.xaml` souboru a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] jazyk, jako je například Microsoft Visual Basic a C# se používá k zápisu souboru kódu na pozadí. Jako součást WPF programovací a aplikace modely kompilaci kódu po souboru XAML umístění kódu XAML soubor pro soubor XAML je identifikována zadání oboru názvů a třídy jako `x:Class` atribut kořenového prvku XAML.  
  
 V příkladech, pokud jste viděli několik tlačítek, ale žádná z těchto tlačítek byl žádné logické chování ještě s nimi spojených. Primární mechanismus úrovni aplikace pro přidání chování pro daný objekt element je používat existující událost třídy elementu a k zápisu konkrétní obslužnou rutinu pro tuto událost, která je volána, když tuto událost se vyvolá v době běhu. Název události a název obslužné rutiny používat jsou určené v kód, zatímco kód, který implementuje vaší obslužné rutiny je definována v modelu code-behind.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 Všimněte si, že souboru kódu na pozadí používá obor názvů CLR `ExampleNamespace` a deklaruje `ExamplePage` jako částečné třídy v daném oboru názvů. To je paralelní `x:Class` hodnotu atributu `ExampleNamespace`.`ExamplePage` který zadaná v kořenu značek. WPF kód bude vytvořen konkrétní třídu pro všechny kompilované souboru XAML odvozením třídy od typ kořenového elementu. Když zadáte kódu, který definuje také stejnou třídu, je v rámci stejný obor názvů a třídy kompilované aplikace kombinaci výsledný kód.  
  
 Další informace o požadavcích pro programování kódu v grafickém subsystému WPF, najdete v části "kódu, obslužné rutiny události a požadavky na třídu" z [kódu a XAML v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
 Pokud nechcete vytvořit soubor samostatné kódu, můžete také vloženého kódu v souboru XAML. Vložený kód je však méně univerzální technika, který má významné omezení. Podrobnosti najdete v tématu [kódu a XAML v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
### <a name="routed-events"></a>Směrované události  
 Funkce určitá událost, která je nezbytné, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je směrované události. Směrované události povolit element zpracovat událost, která byla vyvolána podle různých prvku, tak dlouho, dokud elementy jsou propojeny pomocí vztahu stromu. Při zadávání zpracování s atributem XAML událostí, můžete směrované události naslouchali pro a zpracovává u libovolného elementu, včetně elementů, které neuvádějte danou událost v tabulce členy třídy. To se provádí kvalifikující události atribut name s vlastnícím název třídy. Například nadřazené `StackPanel` v probíhající `StackPanel`  /  `Button` příkladu by se mohl zaregistrovat obslužnou rutinu pro tlačítko podřízený element <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí zadáním atribut `Button.Click` na `StackPanel` element Object názvem vaší obslužné rutiny jako hodnota atributu. Další informace o způsobu směrovaný pracovní událostí najdete v tématu [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="x_name_and_xaml_named_elements"></a>   
## <a name="xaml-named-elements"></a>S názvem elementů XAML  
 Ve výchozím nastavení instance objektu, který je vytvořen v grafu objektů zpracováním element XAML objekt nemá jedinečný identifikátor nebo odkaz na objekt. Naproti tomu při volání konstruktoru v kódu, téměř vždy použijete výsledek konstruktor nastavte proměnnou na zkonstruovaná instance, tak, aby instance, můžete odkazovat později ve svém kódu. Chcete-li poskytovat standardizované přístup k objektům, vytvořené pomocí značek definice, XAML definuje [x: Name – atribut](../../../../docs/framework/xaml-services/x-name-directive.md). Můžete nastavit hodnotu `x:Name` atribut u libovolného elementu objektu. Ve vašem kódu je ekvivalentní proměnnou instance, který odkazuje na zkonstruovaná instance identifikátor, který zvolíte. Ve všech ohledech s názvem elementy funkce, jako kdyby byly instance objektů (název odkazuje na tato instance) a vašeho kódu odkazovat pojmenované elementy pro zpracování interakce běhu v aplikaci. Toto připojení mezi instancemi a proměnné provádí kompilátoru značek WPF XAML a více konkrétně zahrnují funkce a vzorů, jako <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> , nebude se podrobněji v tomto tématu.  
  
 Zdědit elementů XAML úrovni rozhraní WPF <xref:System.Windows.FrameworkElement.Name%2A> vlastnost, která je ekvivalentní XAML definované `x:Name` atribut. Některé jiné třídy taky zadat vlastnost úrovni ekvivalenty pro `x:Name`, který je také obecně definován jako `Name` vlastnost. Obecně platí, že pokud nemůžete najít `Name` v tabulce členy pro vaše vybraný element nebo typ, použijte vlastnost `x:Name` místo. `x:Name` Hodnoty bude poskytovat identifikátor elementu XAML, který lze použít v době běhu pomocí konkrétní subsystémy nebo pomocí pomocné metody, jako <xref:System.Windows.FrameworkElement.FindName%2A>.  
  
 Následující příklad sady <xref:System.Windows.FrameworkElement.Name%2A> na <xref:System.Windows.Controls.StackPanel> elementu. Potom obslužné rutiny na <xref:System.Windows.Controls.Button> v rámci které <xref:System.Windows.Controls.StackPanel> odkazy <xref:System.Windows.Controls.StackPanel> prostřednictvím odkaz na jeho instanci `buttonContainer` jako nastavte podle <xref:System.Windows.FrameworkElement.Name%2A>.  
  
 [!code-xaml[XAMLOvwSupport#NamedE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xaml[XAMLOvwSupport#NamedE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 Stejně jako proměnnou názvu XAML pro instance se řídí koncept oboru, tak, aby názvy je možné vynutit být jedinečný v rámci oboru, který je předvídatelný. Primární kód, který definuje stránky označuje jeden jedinečný XAML namescope k hranici namescope XAML se kořenový element této stránce. Ale jiných zdrojů značek mohou komunikovat s stránky v době běhu, jako je například styly nebo šablony v rámci styly, a těchto zdrojů, značek často mají své vlastní namescopes XAML, který se nutně nepřipojí s namescope XAML stránky. Další informace o `x:Name` a XAML namescopes najdete v části <xref:System.Windows.FrameworkElement.Name%2A>, [x: Name – direktiva](../../../../docs/framework/xaml-services/x-name-directive.md), nebo [WPF XAML Namescopes](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
<a name="attached_properties_and_attached_events"></a>   
## <a name="attached-properties-and-attached-events"></a>Přidružené vlastnosti a přidružené události  
 XAML Určuje jazyk funkce, která umožňuje určité vlastnosti nebo událostí, které je třeba zadat u libovolného elementu, bez ohledu na to, jestli existuje vlastnost nebo události v definicích typu pro element, který bude nastavena na. Vlastnosti verze této funkce je volána přidružená vlastnost, verze události se nazývá přidružená událost. Koncepčně si můžete představit přidružené vlastnosti a přidružené události jako globální členy, které lze nastavit na jakoukoli instanci XAML nebo objekt elementu. Ale element nebo třídy nebo větší infrastruktury musí podporovat zálohování úložiště vlastností pro připojené hodnoty.  
  
 Přidružené vlastnosti v jazyce XAML jsou obvykle používány prostřednictvím syntaxe atributu. V syntaxi atribut zadáte přidružená vlastnost ve formě *ownerType*. *propertyName*.  
  
 Na první pohled, to vypadá takto: použití elementu vlastnosti, ale v takovém případě *ownerType* zadáte, je vždy jiný atribut type než object element kde je právě připojená vlastnost nastavená. *ownerType* je typ, který poskytuje přistupující objekt metody, které jsou vyžadované procesor XAML za účelem získání nebo nastavení hodnoty vlastnosti připojené.  
  
 Nejběžnější scénáře pro přidružené vlastnosti je umožnit podřízené elementy informuje hodnotu vlastnosti o jejich nadřazeného elementu.  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> přidružená vlastnost. <xref:System.Windows.Controls.DockPanel> Třída definuje přistupující objekty pro <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> a proto je vlastníkem připojená vlastnost. <xref:System.Windows.Controls.DockPanel> Třída také obsahuje logiku, která iteruje její podřízené elementy a konkrétně zkontroluje každý prvek pro hodnotu sady <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Pokud je nalezen hodnotu, tato hodnota se používá během rozložení na pozici podřízené elementy. Použití <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> přidružená vlastnost a tato umísťovací funkce je ve skutečnosti motivačních scénář pro <xref:System.Windows.Controls.DockPanel> třídy.  
  
 [!code-xaml[XAMLOvwSupport#DockAP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], většině nebo všem přidružené vlastnosti jsou implementované také jako vlastnosti závislosti. Podrobnosti najdete v tématu [připojen přehled vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
 Použít přidružené události podobné *ownerType*. *eventName* formu atributu syntaxe. Stejně jako nepřipojené události určuje hodnota atributu přidružená událost v jazyce XAML název metody obslužné rutiny, která je volána, když se zpracovává událost v elementu. Použití přidružená událost v jazyce XAML WPF je méně běžné. Další informace najdete v tématu [připojen přehled událostí](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
<a name="base_classes_and_xaml"></a>   
## <a name="base-types-and-xaml"></a>Základní typy a XAML  
 Základní WPF XAML a jeho oboru názvů jazyka XAML je kolekci typů, které odpovídají [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty kromě prvky značek pro jazyk XAML. Ne všechny třídy však lze mapovat na elementy. Abstraktní třídy, jako například <xref:System.Windows.Controls.Primitives.ButtonBase>, a používají se pro dědičnosti v určitých neabstraktní základní třídy [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty modelu. Základní třídy, včetně těch abstraktní, jsou pro vývoj XAML stále důležité, protože každý z konkrétní elementů XAML dědí členy ze základní třídy, které se v hierarchii. Tito členové často patří vlastnosti, které lze nastavit jako atributy v elementu nebo událostí, které mohou být zpracovány. <xref:System.Windows.FrameworkElement> je konkrétní základní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] třídu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na úrovni framework WPF. Při navrhování [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], budete používat různé tvaru, panel, dekoratéra nebo – třídy ovládacích prvků, které všechna odvozena od <xref:System.Windows.FrameworkElement>. Související základní třídu, <xref:System.Windows.FrameworkContentElement>, podporuje dokumentu zaměřené na konkrétní prvky, které fungovat i pro prezentaci rozložení toku pomocí [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] který úmyslně zrcadlení [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] v <xref:System.Windows.FrameworkElement>. Kombinace atributů na úrovni elementu a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektový model poskytuje sadu společných vlastností, které jsou nastavit na nejvíce konkrétní elementů XAML, bez ohledu na konkrétní element jazyka XAML a jeho zdrojovým typem.  
  
<a name="xaml_security"></a>   
## <a name="xaml-security"></a>XAML – zabezpečení  
 XAML je jazyk kódu, který přímo představuje vytvoření instance objektu a spouštění. Proto prvků vytvořených v jazyce XAML mít stejné možnost využívat systémové prostředky (přístup do sítě, soubor systému vstupně-výstupní operace, například) jako ekvivalentní, vygeneruje kód neobsahuje.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] zabezpečení framework [!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)]. To znamená, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah spuštěný v zóně internet omezila oprávnění provádění. "Ke ztrátě XAML" (stránky noncompiled XAML interpretovat při načítání, prohlížeč XAML) a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] jsou obvykle spustit v této zóně internet a použít stejnou sadu oprávnění.  XAML načíst ve plně důvěryhodný pro aplikaci však má stejný přístup k systémovým prostředkům, stejně jako hostitelskou aplikaci. Další informace najdete v tématu [WPF částečné důvěryhodnosti zabezpečení](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="loading_xaml_from_code"></a>   
## <a name="loading-xaml-from-code"></a>Načítání z kódu jazyka XAML  
 XAML lze použít k definování všechny rozhraní, ale je někdy také vhodné definují právě části uživatelského rozhraní v jazyce XAML. Tato funkce může za účelem částečné přizpůsobení místního úložiště informací, které poskytují objekt obchodní nebo celou řadu možných scénářích pomocí XAML. Tyto scénáře je <xref:System.Windows.Markup.XamlReader> třídy a jeho <xref:System.Windows.Markup.XamlReader.Load%2A> metoda. Vstup je soubor XAML a výstup je objekt, který reprezentuje všechny stromu běhu objektů, který byl vytvořen z těchto značek. Potom můžete vložit objekt, který má být vlastnost jiného objektu, který již existuje v aplikaci. Pokud je vlastnost příslušné vlastnosti v modelu obsahu, který má možnosti případné zobrazení a který oznámí modul provádění že byl přidán nový obsah do aplikace, můžete velmi snadno upravit obsah spuštěné aplikace podle načítání v jazyce XAML. Všimněte si, že tato funkce je obecně k dispozici pouze ve plně důvěryhodné aplikace, z důvodu zřejmé bezpečnostních důsledcích načtení souborů do aplikací při spuštění.  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>Co je další  
 Toto téma obsahuje základní informace o XAML syntaxe principy a terminologií, která se vztahuje na WPF. Další informace o podmínky použít se zde najdete v tématu [XAML syntaxe v podrobností](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Pokud jste to ještě neudělali, zkuste praktická cvičení v kurzu tématu [návod: Můj první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md). Při vytvoření značek zaměřená na aplikace, které jsou popsané v kurzu, bude výkonu pomohli posílit řadu konceptů popsaných v tomto tématu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá model konkrétní aplikace, který je založen na <xref:System.Windows.Application> třídy. Podrobnosti najdete v tématu [přehled správy aplikací](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
 [Vytvoření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md) získáte další informace o tom, jak vytvářet aplikace inkluzivní XAML z příkazového řádku a s [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
 [Přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) poskytuje další informace o univerzálnost vlastností v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a zavádí koncepci vlastností závislostí.  
  
## <a name="see-also"></a>Viz také  
 [Podrobná syntaxe XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [XAML a vlastní třídy pro WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Jazykové funkce oboru názvů jazyka XAML (x:)](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [Rozšíření WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [Přehled základních elementů](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Stromy v subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
