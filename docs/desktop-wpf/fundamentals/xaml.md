---
title: Přehled XAML
description: Zjistěte, jak je jazyk XAML strukturován a implementován systémem WPF (Windows Presentation Foundation) pro jazyk .NET Core.
author: thraka
ms.date: 08/08/2019
ms.author: adegeo
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
ms.openlocfilehash: b0a9357b623fbde08731a5b1ddb8fee3a93824c2
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "82071785"
---
# <a name="xaml-overview-in-wpf"></a>Přehled XAML v WPF

Tento článek popisuje funkce jazyka XAML a ukazuje, jak můžete použít XAML k zápisu windows presentation foundation (WPF) aplikace. Tento článek konkrétně popisuje XAML jako implementované WPF. XAML sám o sobě je větší koncept jazyka než WPF.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-xaml"></a>Co je XAML

XAML je deklarativní značkovací jazyk. Jak se použije na programovací model .NET Core, XAML zjednodušuje vytváření uživatelského rozhraní pro aplikaci .NET Core. Můžete vytvořit viditelné prvky uživatelského rozhraní v deklarativní masce XAML a potom oddělit definici uživatelského rozhraní od logiky za běhu pomocí souborů s kódem na pozadí, které jsou spojeny se značkami prostřednictvím částečných definic tříd. XAML přímo představuje konkretizovat objekty v určité sadě typů zálohování definovaných v sestavách. To je na rozdíl od většiny ostatních jazycích značek, které jsou obvykle interpretovaný jazyk bez takové přímé vazby na systém doprovodného typu. XAML umožňuje pracovní postup, kde samostatné strany mohou pracovat na uživatelském prostředí a logiku aplikace pomocí potenciálně různých nástrojů.

Při reprezentován jako text, XAML soubory `.xaml` jsou XML soubory, které obecně mají příponu. Soubory mohou být kódovány libovolným kódováním XML, ale kódování jako UTF-8 je typické.

Následující příklad ukazuje, jak můžete vytvořit tlačítko jako součást ui. Tento příklad je určen k vám chuť, jak XAML představuje běžné metafory programování uživatelského rozhraní (není kompletní vzorek).

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

## <a name="xaml-syntax-in-brief"></a>Syntaxe XAML ve zkratce

V následujících částech jsou vysvětleny základní formy syntaxe XAML a uvedeny krátké značky příklad. Tyto oddíly nejsou určeny k poskytování úplných informací o každém formuláři syntaxe, například jak jsou reprezentovány v systému typu zálohování. Další informace o specifikách syntaxe XAML naleznete [v části Syntaxe XAML v detailu](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

Velká část materiálu v příštích několika částech bude pro vás elementární, pokud máte předchozí znalost jazyka XML. To je důsledkem jednoho ze základních konstrukčních principů XAML. Jazyk XAML definuje vlastní koncepty, ale tyto koncepty fungují v rámci jazyka XML a formuláře značek.

### <a name="xaml-object-elements"></a>Prvky objektu XAML

Element objektu obvykle deklaruje instanci typu. Tento typ je definován v sestaveních odkazuje technologie, která používá XAML jako jazyk.

Syntaxe prvku objektu vždy začíná`<`otevírací úhlovou závorkou ( ). Následuje název typu, do kterého chcete vytvořit instanci. (Název může obsahovat předponu, koncept, který bude vysvětlen později.) Poté můžete volitelně deklarovat atributy prvku objektu. Chcete-li značku prvku objektu dokončit,`>`zakončete uzavírací úhlovou závorkou ( ). Místo toho můžete použít samouzavírací formulář, který nemá žádný obsah, vyplněním značky lomítkem a uzavíracím úhlovým držákem za sebou (`/>`). Podívejte se například znovu na dříve zobrazený úryvek značek.

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

Určuje dva objektové `<StackPanel>` prvky: (s obsahem a `<Button .../>` uzavírací značkou později) a (formulář pro samouzavírací formulář s několika atributy). Objektové `StackPanel` prvky a `Button` každý mapovat na název třídy, která je definována WPF a je součástí sestavení WPF. Když zadáte značku elementu objektu, vytvoříte instrukce pro zpracování XAML k vytvoření nové instance základního typu. Každá instance je vytvořena voláním konstruktoru bez parametrů základního typu při analýzě a načítání XAML.

### <a name="attribute-syntax-properties"></a>Syntaxe atributu (vlastnosti)

Vlastnosti objektu mohou být často vyjádřeny jako atributy prvku objektu. Syntaxe atributu pojmenuje vlastnost objektu, která je nastavena, následovanou operátorem přiřazení (=). Hodnota atributu je vždy zadána jako řetězec, který je obsažen v uvozovkách.

Syntaxe atributu je nejefektivnější syntaxe nastavení vlastností a je nejintuitivnější syntaxí, kterou lze použít pro vývojáře, kteří v minulosti používali značkovací jazyky. Například následující značky vytvoří tlačítko, které má červený text a modré `Content`pozadí kromě zobrazení textu určeného jako .

[!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]

### <a name="property-element-syntax"></a>Syntaxe prvku vlastnosti

Pro některé vlastnosti prvku objektu není syntaxe atributu možná, protože objekt nebo informace nezbytné k poskytnutí hodnoty vlastnosti nemohou být dostatečně vyjádřeny v rámci uvozovky a omezení řetězce syntaxe atributu. V těchto případech lze použít jinou syntaxi známou jako syntaxe prvku vlastnosti.

Syntaxe počáteční značky elementu vlastnosti je `<TypeName.PropertyName>`. Obecně je obsah této značky prvek objektu typu, který vlastnost bere jako jeho hodnotu. Po zadání obsahu je nutné zavřít element vlastnosti koncovou značkou. Syntaxe koncové značky `</TypeName.PropertyName>`je .

Pokud je syntaxe atributu možná, použití syntaxe atributu je obvykle pohodlnější a umožňuje kompaktnější značky, ale to je často jen otázkou stylu, nikoli technického omezení. Následující příklad ukazuje stejné vlastnosti, které jsou nastaveny jako v předchozím příkladu syntaxe `Button`atributu, ale tentokrát pomocí syntaxe elementu vlastnosti pro všechny vlastnosti .

[!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]

### <a name="collection-syntax"></a>Syntaxe kolekce

Jazyk XAML obsahuje některé optimalizace, které vytvářejí více čitelné značky. Jedním z takových optimalizace je, že pokud určitá vlastnost přebírá typ kolekce, pak položky, které deklarujete ve značkách jako podřízené prvky v rámci hodnoty této vlastnosti, se stanou součástí kolekce. V tomto případě kolekce podřízených prvků objektu je hodnota nastavena na vlastnost kolekce.

Následující příklad ukazuje syntaxi kolekce <xref:System.Windows.Media.GradientBrush.GradientStops%2A> pro nastavení hodnot vlastnosti.

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

XAML určuje funkci jazyka, kdy třída může přesně určit jednu ze svých vlastností jako vlastnost _obsahu_ XAML. Podřízené prvky tohoto prvku objektu se používají k nastavení hodnoty této vlastnosti content. Jinými slovy pro vlastnost content jedinečně můžete vynechat element vlastnosti při nastavování této vlastnosti v značek XAML a vytvořit více viditelné metafory nadřazený/podřízený ve značkách.

Určuje například <xref:System.Windows.Controls.Border> vlastnost _obsahu_ <xref:System.Windows.Controls.Decorator.Child%2A>souboru . Následující dva <xref:System.Windows.Controls.Border> prvky jsou zpracovány stejně. První z nich využívá syntaxi vlastnosti obsahu `Border.Child` a vynese prvek vlastnosti. Druhý ukazuje `Border.Child` explicitně.

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

Jako pravidlo jazyka XAML hodnota vlastnosti obsahu XAML musí být uvedeny zcela před nebo zcela po jakékoli jiné prvky vlastnosti na tento prvek objektu. Například následující značky nekompiluje.

```xaml
<Button>I am a
  <Button.Background>Blue</Button.Background>
  blue button</Button>
```

Další informace o specifikách syntaxe XAML naleznete [v části Syntaxe XAML v detailu](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

### <a name="text-content"></a>Textový obsah

Malý počet prvků XAML může přímo zpracovat text jako jejich obsah. Chcete-li to povolit, musí být splněn jeden z následujících případů:

- Třída musí deklarovat vlastnost content a vlastnost content musí být typu přiřaditelného řetězci (typ může být <xref:System.Object>). Například všechny <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ContentControl.Content%2A> použití jako jeho content <xref:System.Object>vlastnost a je typ , <xref:System.Windows.Controls.ContentControl> a <xref:System.Windows.Controls.Button>to `<Button>Hello</Button>`podporuje následující použití například : .

- Typ musí deklarovat převaděč typu, v takovém případě se textový obsah použije jako inicializační text pro tento převaděč typu. Například `<Brush>Blue</Brush>` převede hodnotu `Blue` obsahu na stopu. Tento případ je v praxi méně častý.

- Typ musí být známý jazyk XAML primitivní.

### <a name="content-properties-and-collection-syntax-combined"></a>Kombinované vlastnosti obsahu a syntaxe kolekce

Vezměme si tento příklad.

```xaml
<StackPanel>
  <Button>First Button</Button>
  <Button>Second Button</Button>
</StackPanel>
```

Zde je <xref:System.Windows.Controls.Button> každý podřízený <xref:System.Windows.Controls.StackPanel>prvek . Jedná se o zjednodušenou a intuitivní značku, která vyneche dvě značky ze dvou různých důvodů.

- **Vynecháno StackPanel.Children prvek vlastnost:** <xref:System.Windows.Controls.StackPanel> odvozuje od <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel>definuje <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> jako svou vlastnost obsahu XAML.

- **Vynecháno elementu objektu UIElementCollection:** Vlastnost <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> má typ <xref:System.Windows.Controls.UIElementCollection>, který <xref:System.Collections.IList>implementuje . Značka elementu kolekce může být vynechána na základě pravidel XAML <xref:System.Collections.IList>pro zpracování kolekcí, jako je například . (V tomto <xref:System.Windows.Controls.UIElementCollection> případě ve skutečnosti nelze vytvořit instanci, protože nezveřejňuje konstruktor <xref:System.Windows.Controls.UIElementCollection> bez parametrů, a proto je prvek objektu zobrazen komentovaný).

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

Syntaxe atributu lze také použít pro členy, které jsou události, nikoli vlastnosti. V tomto případě název atributu je název události. V wpf implementaci událostí pro XAML je hodnota atributu název obslužné rutiny, která implementuje delegáta této události. Například následující značky přiřadí obslužnou rutinu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události <xref:System.Windows.Controls.Button> vytvořené ve značkách:

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

Je více událostí a XAML v WPF, než jen tento příklad syntaxe atributu. Můžete se například divit, co `ClickHandler` zde odkazované představuje a jak je definován. To bude vysvětleno v nadcházející [události a XAML kód na pozadí](#events-and-xaml-code-behind) části tohoto článku.

## <a name="case-and-white-space-in-xaml"></a>Velká a prázdné místo v XAML

Obecně xaml rozlišuje malá a velká písmena. Pro účely řešení typů zálohování WPF XAML rozlišuje se stejnými pravidly, která clr rozlišuje malá a velká písmena. Prvky objektu, prvky vlastností a názvy atributů musí být určeny pomocí citlivého pouzdře při porovnání s názvem s podkladovým typem v sestavení nebo s členem typu. Klíčová slova jazyka XAML a primitiva jsou také rozlišována malá a velká písmena. Hodnoty nejsou vždy rozlišována malá a velká písmena. Rozlišování malých a velkých písmen pro hodnoty bude záviset na chování převaděče typu přidružené k vlastnosti, která přebírá hodnotu, nebo na typu hodnoty vlastnosti. Například vlastnosti, <xref:System.Boolean> které berou `true` typ `True` může trvat buď nebo jako ekvivalentní hodnoty, ale pouze proto, že nativní WPF XAML parser typ převodu pro řetězec <xref:System.Boolean> již umožňuje tyto jako ekvivalenty.

WPF XAML procesory a serializátory bude ignorovat nebo vynechat všechny nevýznamné prázdné znaky a normalizuje všechny významné prázdné místo. To je konzistentní s výchozí prázdné místo chování doporučení specifikace XAML. Toto chování je pouze důsledkem, pokud zadáte řetězce v rámci vlastností obsahu XAML. V nejjednodušších termínech XAML převede mezery, linefeed a tabulátorznaky do mezer a pak zachová jednu mezeru, pokud se nachází na obou koncích souvislého řetězce. Úplné vysvětlení zpracování prázdného místa XAML není zahrnuto v tomto článku. Další informace naleznete [v tématu Zpracování prázdného místa v XAML](../xaml-services/white-space-processing.md).

## <a name="markup-extensions"></a>Rozšíření značek

Rozšíření značek jsou koncept jazyka XAML. Při použití k zadání hodnoty syntaxe atributu`{` označují `}`složené závorky ( a ) použití rozšíření značek. Toto použití řídí zpracování XAML uniknout z obecné zpracování hodnoty atributů jako literál řetězec nebo řetězec konvertibilní hodnotu.

Nejběžnější značkovací rozšíření používaná v programování [`Binding`](../../framework/wpf/advanced/binding-markup-extension.md)aplikací WPF jsou , používá se [`StaticResource`](../../framework/wpf/advanced/staticresource-markup-extension.md) pro [`DynamicResource`](../../framework/wpf/advanced/dynamicresource-markup-extension.md)výrazy datové vazby a odkazy na prostředky a . Pomocí rozšíření značek můžete použít syntaxi atributu k zadání hodnot vlastností, i když tato vlastnost obecně nepodporuje syntaxi atributu. Rozšíření značek často používají zprostředkující typy výrazů k povolení funkcí, jako je například odložení hodnot nebo odkazování na jiné objekty, které jsou k dispozici pouze za běhu.

Například následující značky nastaví hodnotu vlastnosti <xref:System.Windows.FrameworkElement.Style%2A> pomocí syntaxe atributu. Vlastnost <xref:System.Windows.FrameworkElement.Style%2A> přebírá instanci <xref:System.Windows.Style> třídy, kterou ve výchozím nastavení nelze vytvořit pomocí řetězce syntaxe atributu. Ale v tomto případě atribut odkazuje na konkrétní `StaticResource`rozšíření značky . Při zpracování tohoto rozšíření značek vrátí odkaz na styl, který byl dříve vytvořena jako prostředek s klíčem ve slovníku prostředků.

[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]

Referenční seznam všech rozšíření značek pro XAML implementovaných konkrétně v WPF naleznete v [tématu WPF XAML Extensions](../../framework/wpf/advanced/wpf-xaml-extensions.md). Referenční seznam rozšíření značek, které jsou definovány system.xaml a jsou více široce dostupné pro implementace .NET Core XAML, naleznete v [tématu XAML Namespace (x:) Funkce jazyka](../xaml-services/namespace-language-features.md). Další informace o konceptech rozšíření značek naleznete v [tématu Markup Extensions and WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

## <a name="type-converters"></a>Převaděče typů

V části [Syntaxe XAML v kostce](#xaml-syntax-in-brief) bylo uvedeno, že hodnota atributu musí být možné nastavit řetězcem. Základní, nativní zpracování, jak jsou řetězce převedeny na jiné typy <xref:System.String> objektů nebo primitivní hodnoty je založena <xref:System.DateTime> na <xref:System.Uri>samotném typu, kromě nativní zpracování pro určité typy, jako je například nebo . Ale mnoho WPF typy nebo členy těchto typů rozšířit základní řetězec atribut zpracování chování takovým způsobem, že instance složitější typy objektů lze zadat jako řetězce a atributy.

Struktura <xref:System.Windows.Thickness> je příkladem typu, který má povolený převod typu pro použití XAML. <xref:System.Windows.Thickness>označuje měření v rámci vnořeného obdélníku a <xref:System.Windows.FrameworkElement.Margin%2A>používá se jako hodnota pro vlastnosti, jako je například . Umístěním převaděče <xref:System.Windows.Thickness>typu na , <xref:System.Windows.Thickness> všechny vlastnosti, které používají xAML, jsou snadněji zadat v XAML, protože mohou být zadány jako atributy. Následující příklad používá syntaxi převodu typu a <xref:System.Windows.FrameworkElement.Margin%2A>atributu k poskytnutí hodnoty pro :

[!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]

Předchozí příklad syntaxe atributu je ekvivalentní následujícímu podrobnému <xref:System.Windows.FrameworkElement.Margin%2A> příkladu syntaxe, kde <xref:System.Windows.Thickness> je místo toho nastavena syntaxe prvku vlastnosti obsahující prvek objektu. Čtyři klíčové vlastnosti <xref:System.Windows.Thickness> jsou nastaveny jako atributy na nové instanci:

[!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]

> [!NOTE]
> Existuje také omezený počet objektů, kde převod typu je jediný veřejný způsob, jak nastavit vlastnost na tento typ bez zahrnutí podtřídy, protože samotný typ nemá konstruktor bez parametrů. Příklad: <xref:System.Windows.Input.Cursor>.

Další informace o převodu typu naleznete v [tématech TypeConverters a XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md).

## <a name="xaml-root-elements-and-xaml-namespaces"></a>Kořenové prvky XAML a obory názvů XAML

Soubor XAML musí mít pouze jeden kořenový prvek, aby byl jak dobře formátovaný soubor XML, tak platný soubor XAML. Pro typické scénáře WPF použijete kořenový prvek, který má v modelu <xref:System.Windows.Window> aplikace <xref:System.Windows.Controls.Page> WPF <xref:System.Windows.ResourceDictionary> prominentní význam (například <xref:System.Windows.Application> nebo pro stránku, pro externí slovník nebo pro definici aplikace). Následující příklad ukazuje kořenový prvek typického souboru XAML pro stránku <xref:System.Windows.Controls.Page>WPF s kořenovým prvkem .

[!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]

Kořenový prvek také obsahuje `xmlns` `xmlns:x`atributy a . Tyto atributy označují procesoru XAML, který obory názvů XAML obsahují definice typů pro podpůrné typy, na které bude značka odkazovat jako na prvky. Atribut `xmlns` konkrétně označuje výchozí obor názvů XAML. Ve výchozím oboru názvů XAML lze zadat prvky objektu ve značkách bez předpony. Pro většinu scénářů aplikace WPF a pro téměř všechny příklady uvedené v oddílech WPF sady SDK je výchozí `http://schemas.microsoft.com/winfx/2006/xaml/presentation`obor názvů XAML mapován na obor názvů WPF . Atribut `xmlns:x` označuje další obor názvů XAML, který mapuje `http://schemas.microsoft.com/winfx/2006/xaml`obor názvů jazyka XAML .

Toto `xmlns` použití k definování oboru pro použití a mapování oboru názvů je konzistentní se specifikací XML 1.0. XAML namescopes se liší od xml namescopes pouze v tom, že XAML namescope také znamená něco o tom, jak namescope prvky jsou zálohovány typy, pokud jde o rozlišení typu a analýzy XAML.

Atributy `xmlns` jsou nezbytně nutné pouze pro kořenový prvek každého souboru XAML. `xmlns`definice se budou vztahovat na všechny potomek prvků kořenového prvku (toto `xmlns`chování je opět v souladu se specifikací XML 1.0 pro .) `xmlns` atributy jsou také povoleny na jiné prvky pod kořenem a by se vztahovaly na všechny potomek prvky definující prvek. Častou definici nebo předefinování oborů názvů XAML však může mít za následek styl značek XAML, který je obtížně čitelný.

WPF implementace jeho procesoru XAML zahrnuje infrastrukturu, která má povědomí o wpf jádra sestavení. Je známo, že jádrová sestavení WPF obsahují typy, které podporují mapování WPF na výchozí obor názvů XAML. To je povoleno prostřednictvím konfigurace, která je součástí souboru sestavení projektu a WPF sestavení a projektové systémy. Proto deklarování výchozí ho xaml `xmlns` obor názvů jako výchozí je vše, co je nezbytné pro odkaz na prvky XAML, které pocházejí ze sestavení WPF.

### <a name="the-x-prefix"></a>X: předpona

V předchozím příkladu kořenového `x:` prvku byla předpona použita `http://schemas.microsoft.com/winfx/2006/xaml`k mapování oboru názvů XAML , což je vyhrazený obor názvů XAML, který podporuje konstrukce jazyka XAML. Tato `x:` předpona se používá pro mapování tohoto oboru názvů XAML v šablonách pro projekty, v příkladech a v dokumentaci v této sadě SDK. Obor názvů XAML pro jazyk XAML obsahuje několik programovacích konstrukcí, které budete často používat v jazyce XAML. Následuje seznam nejběžnějších `x:` předpon programování konstrukce, které budete používat:

- [x:Key](../xaml-services/xkey-directive.md): Nastaví jedinečný klíč <xref:System.Windows.ResourceDictionary> pro každý prostředek v (nebo podobné slovníkové koncepty v jiných architekturách). `x:Key`bude pravděpodobně představovat 90 `x:` procent použití, které uvidíte v typické wpf app značky.

- [x:Class](../xaml-services/xclass-directive.md): Určuje obor názvů CLR a název třídy, která poskytuje kód na pozadí stránky XAML. Musíte mít takové třídy pro podporu kódu na pozadí na programovací `x:` model WPF, a proto téměř vždy vidět mapovány, i v případě, že neexistují žádné prostředky.

- [x:Name](../xaml-services/xname-directive.md): Určuje název objektu za běhu pro instanci, která existuje v kódu za běhu po zpracování prvku objektu. Obecně platí, že často budete používat WPF definované ekvivalentní vlastnost pro [x:Name](../xaml-services/xname-directive.md). Tyto vlastnosti mapovat konkrétně na vlastnost zálohování CLR a jsou proto vhodnější pro programování aplikací, kde často používáte kód run-time najít pojmenované prvky z inicializované XAML. Nejběžnější taková vlastnost <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>je . Stále můžete použít [x:Name,](../xaml-services/xname-directive.md) pokud ekvivalentní <xref:System.Windows.FrameworkElement.Name%2A> WPF úroveň architektury vlastnost není podporována v určitém typu. K tomu dochází v některých scénářích animace.

- [x:Static](../xaml-services/xstatic-markup-extension.md): Povolí odkaz, který vrací statickou hodnotu, která jinak není vlastností kompatibilní s XAML.

- [x:Type](../xaml-services/xtype-markup-extension.md): Vytvoří <xref:System.Type> odkaz na základě názvu typu. Používá se k určení atributů, <xref:System.Type> <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>které berou , například , i<xref:System.Type> když vlastnost má často nativní převod typu string-to-conversion takovým způsobem, že použití rozšíření značek [x:Type](../xaml-services/xtype-markup-extension.md) je volitelné.

Existují další programovací konstrukce `x:` v oboru názvů předpony/XAML, které nejsou tak běžné. Podrobnosti naleznete v [tématu XAML Namespace (x:) Funkce jazyka](../xaml-services/namespace-language-features.md).

## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Vlastní předpony a vlastní typy v XAML

Pro vlastní sestavení nebo pro sestavení mimo jádro WPF **PresentationCore**, **PresentationFramework** a **WindowsBase**můžete zadat `xmlns` sestavení jako součást vlastního mapování. Potom můžete odkazovat na typy z tohoto sestavení v XAML, tak dlouho, dokud tento typ je správně implementována pro podporu xAML použití, které se pokoušíte.

Následuje základní příklad fungování vlastních předpon ve značkách XAML. Předpona `custom` je definována ve značce kořenového prvku a mapována na konkrétní sestavení, které je zabaleno a k dispozici s aplikací. Toto sestavení `NumericUpDown`obsahuje typ , který je implementován pro podporu obecného použití XAML, stejně jako pomocí dědičnosti třídy, která umožňuje jeho vložení v tomto konkrétním bodě v modelu obsahu WPF XAML. Instance tohoto `NumericUpDown` ovládacího prvku je deklarována jako element objektu pomocí předpony tak, aby analyzátor XAML věděl, který obor názvů XAML obsahuje typ, a proto kde je záložní sestavení, které obsahuje definici typu.

```xaml
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

Další informace o vlastních typech v XAML naleznete v tématu [XAML a Custom Classes for WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).

Další informace o tom, jak spolu souvisejí obory názvů XML a obory názvů kódu v sestaveních, naleznete v [tématu XAML Namespaces a Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

## <a name="events-and-xaml-code-behind"></a>Události a kód XAML na pozadí

Většina wpf aplikací se skládá ze značek XAML i kódu na pozadí. V rámci projektu XAML je `.xaml` zapsán jako soubor a clr jazyk, jako je například Microsoft Visual Basic nebo C# se používá k zápisu souboru s kódem na pozadí. Pokud je soubor XAML zkompilován jako součást programovacích a aplikačních modelů WPF, umístění souboru kódu XAML pro soubor XAML je identifikováno zadáním oboru názvů a třídy jako `x:Class` atributu kořenového prvku XAML.

V příkladech zatím jste viděli několik tlačítek, ale žádné z těchto tlačítek neměl žádné logické chování s nimi spojené dosud. Primární mechanismus na úrovni aplikace pro přidání chování pro prvek objektu je použít existující událost třídy elementu a napsat konkrétní obslužnou rutinu pro tuto událost, která je vyvolána při vyvolání této události za běhu. Název události a název obslužné rutiny, která má být používána, jsou určeny ve značkách, zatímco kód, který implementuje obslužnou rutinu, je definován v kódu na pozadí.

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

[!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
[!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]

Všimněte si, že soubor s kódem na pozadí používá obor názvů `ExampleNamespace` CLR a deklaruje `ExamplePage` jako částečnou třídu v rámci tohoto oboru názvů. To paraleluje hodnotu `x:Class` atributu `ExampleNamespace`.`ExamplePage` který byl uveden v kořenovém adresáři značek. Kompilátor značek WPF vytvoří částečnou třídu pro jakýkoli kompilovaný soubor XAML odvozením třídy z typu kořenového prvku. Když zadáte kód za, který také definuje stejnou částečnou třídu, výsledný kód je kombinován v rámci stejného oboru názvů a třídy zkompilované aplikace.

Další informace o požadavcích na programování na pozadí kódu v WPF naleznete v [tématu Code-behind, Event Handler a Požadavky na částečnou třídu v WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md#code-behind-event-handler-and-partial-class-requirements-in-wpf).

Pokud nechcete vytvořit samostatný soubor s kódem na pozadí, můžete také zařadit kód do souboru XAML. Vázací kód je však méně univerzální technika, která má podstatná omezení. Další informace naleznete v [tématu Code-Behind a XAML v WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

### <a name="routed-events"></a>Směrované události

Konkrétní funkce události, která je zásadní pro WPF je směrované události. Směrované události umožňují prvek zpracovat událost, která byla vyvolána jiným prvkem, tak dlouho, dokud jsou prvky propojeny prostřednictvím vztahu stromu. Při zadávání zpracování událostí s atributem XAML lze směrovitou událost poslouchat a zpracovávat na libovolném prvku, včetně prvků, které neuvádějí tuto konkrétní událost v tabulce členů třídy. Toho lze dosáhnout kvalifikujícím atribut názvu události s názvem třídy vlastnící. Například `StackPanel` nadřazený `StackPanel`  /  `Button` v probíhajícím příkladu může zaregistrovat obslužnou rutinu pro událost tlačítka podřízeného <xref:System.Windows.Controls.Primitives.ButtonBase.Click> prvku zadáním atributu `Button.Click` na elementu objektu `StackPanel` s názvem obslužné rutiny jako hodnotou atributu. Další informace naleznete v tématu [Přehled směrovaných událostí](../../framework/wpf/advanced/routed-events-overview.md).

## <a name="xaml-named-elements"></a>Pojmenované prvky XAML

Ve výchozím nastavení instanci objektu, která je vytvořena v grafu objektu zpracováním elementu objektu XAML, nemá jedinečný identifikátor nebo odkaz na objekt. Naopak pokud voláte konstruktor v kódu, téměř vždy použijete výsledek konstruktoru k nastavení proměnné na vyrobenou instanci, takže můžete odkazovat na instanci později v kódu. Aby byl zajištěn standardizovaný přístup k objektům, které byly vytvořeny pomocí definice značek, xAML definuje [atribut x:Name](../xaml-services/xname-directive.md). Můžete nastavit hodnotu `x:Name` atributu na libovolný prvek objektu. Ve vašem kódu na pozadí, identifikátor, který zvolíte, je ekvivalentní proměnné instance, která odkazuje na vyrobenou instanci. Ve všech ohledech pojmenované prvky fungují, jako by byly instance objektu (název odkazuje na tuto instanci) a váš kód na pozadí můžete odkazovat na pojmenované prvky pro zpracování interakce run-time v rámci aplikace. Toto připojení mezi instancemi a proměnnými je dosaženo kompilátorem značek WPF XAML <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> a konkrétněji zahrnuje prvky a vzory, jako je například nebude podrobně popsáno v tomto článku.

WPF framework-level XAML <xref:System.Windows.FrameworkElement.Name%2A> elementy dědí vlastnost, která `x:Name` je ekvivalentní xaml definovaný atribut. Některé další třídy také poskytují `x:Name`ekvivalenty na úrovni vlastností pro , který je také obecně definován jako `Name` vlastnost. Obecně řečeno, pokud nemůžete `Name` najít vlastnost v tabulce členů pro vybraný `x:Name` prvek/typ, použijte místo. Hodnoty `x:Name` poskytnou identifikátor prvku XAML, který lze použít za běhu, a to buď určitými <xref:System.Windows.FrameworkElement.FindName%2A>subsystémy, nebo metodami nástrojů, jako je například .

Následující příklad <xref:System.Windows.FrameworkElement.Name%2A> nastaví <xref:System.Windows.Controls.StackPanel> na prvek. Potom obslužná <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.StackPanel> rutina <xref:System.Windows.Controls.StackPanel> v rámci, `buttonContainer` který <xref:System.Windows.FrameworkElement.Name%2A>odkazuje na odkaz prostřednictvím jeho instance, jak je nastaveno .

[!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]

[!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
[!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]

Stejně jako proměnná, název XAML pro instanci se řídí koncept oboru, takže názvy mohou být vynuceny jako jedinečné v rámci určitého oboru, který je předvídatelný. Primární značka, která definuje stránku označuje jeden jedinečný název xaml, přičemž hranice oboru názvů XAML je kořenovým prvkem této stránky. Jiné zdroje značek však mohou pracovat se stránkou za běhu, jako jsou styly nebo šablony v rámci stylů, a tyto zdroje značek mají často vlastní názvové obory XAML, které se nemusí nutně připojit k oboru názvů XAML na stránce. Další informace `x:Name` o oborech názvů A <xref:System.Windows.FrameworkElement.Name%2A>XAML naleznete v tématu , [x:Name Directive](../xaml-services/xname-directive.md)nebo [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

## <a name="attached-properties-and-attached-events"></a>Připojené vlastnosti a připojené události

XAML určuje funkci jazyka, která umožňuje určité vlastnosti nebo události, které mají být zadány na libovolný prvek, bez ohledu na to, zda vlastnost nebo událost existuje v definicích typu pro prvek, který je nastaven na. Verze vlastností této funkce se nazývá připojená vlastnost, verze událostí se nazývá připojená událost. Koncepčně si můžete představit připojené vlastnosti a připojené události jako globální členy, které lze nastavit na libovolné instanci elementu/objektu XAML. Tento prvek nebo třída nebo větší infrastruktura však musí podporovat úložiště podpůrných vlastností pro připojené hodnoty.

Připojené vlastnosti v XAML se obvykle používají pomocí syntaxe atributu. V syntaxi atributu určíte připojenou `ownerType.propertyName`vlastnost ve formuláři .

Povrchně se to podobá použití prvku vlastnosti, `ownerType` ale v tomto případě zadáte je vždy jiný typ než prvek objektu, kde je nastavena připojená vlastnost. `ownerType`je typ, který poskytuje přistupující metody, které jsou vyžadovány procesorem XAML, aby bylo možné získat nebo nastavit hodnotu připojené vlastnosti.

Nejběžnější scénář pro připojené vlastnosti je umožnit podřízené prvky hlásit hodnotu vlastnosti jejich nadřazený prvek.

Následující příklad ilustruje <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> připojenou vlastnost. Třída <xref:System.Windows.Controls.DockPanel> definuje přístupové objekty <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> pro a proto vlastní připojené vlastnosti. Třída <xref:System.Windows.Controls.DockPanel> také obsahuje logiku, která itevaluje jeho podřízené <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>prvky a konkrétně kontroluje každý prvek pro nastavenou hodnotu . Pokud je nalezena hodnota, tato hodnota se používá během rozložení umístit podřízené prvky. Použití <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> připojené vlastnosti a tato schopnost umístění je ve skutečnosti <xref:System.Windows.Controls.DockPanel> motivující scénář pro třídu.

[!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]

V WPF většina nebo všechny připojené vlastnosti jsou také implementovány jako vlastnosti závislostí. Další informace naleznete v [tématu Přehled připojených vlastností](../../framework/wpf/advanced/attached-properties-overview.md).

Připojené události používají `ownerType.eventName` podobnou formu syntaxe atributu. Stejně jako nepřipojené události, hodnota atributu pro připojené události v XAML určuje název metody obslužné rutiny, která je vyvolána při zpracování události na prvku. Připojené události použití v WPF XAML jsou méně časté. Další informace naleznete [v tématu Přehled připojených událostí](../../framework/wpf/advanced/attached-events-overview.md).

## <a name="base-types-and-xaml"></a>Základní typy a XAML

Základní WPF XAML a jeho XAML obor názvů je kolekce typů, které odpovídají CLR objekty kromě značkovací prvky pro XAML. Však ne všechny třídy lze mapovat na prvky. Abstraktní třídy, <xref:System.Windows.Controls.Primitives.ButtonBase>například , a některé neabstraktní základní třídy, se používají pro dědičnost v modelu objektů CLR. Základní třídy, včetně abstraktních, jsou pro vývoj XAML stále důležité, protože každý z konkrétních prvků XAML dědí členy z některé základní třídy v hierarchii. Často tyto členy zahrnují vlastnosti, které lze nastavit jako atributy na prvek nebo události, které mohou být zpracovány. <xref:System.Windows.FrameworkElement>je betonová základní třída uI WPF na úrovni rámce WPF. Při navrhování ui, budete používat různé tvar, panel, decorator nebo <xref:System.Windows.FrameworkElement>kontrolní třídy, které všechny odvozené z . Související základní třída <xref:System.Windows.FrameworkContentElement>, podporuje prvky orientované na dokumenty, které dobře fungují pro prezentaci <xref:System.Windows.FrameworkElement>rozložení toku, pomocí rozhraní API, která záměrně zrcadlí rozhraní API v . Kombinace atributů na úrovni prvku a objektového modelu CLR poskytuje sadu společných vlastností, které jsou nastaveny na většině konkrétních prvků XAML, bez ohledu na konkrétní prvek XAML a jeho základní typ.

## <a name="xaml-security"></a>Zabezpečení XAML

XAML je značkovací jazyk, který přímo představuje instanci a spuštění objektu. Proto prvky vytvořené v XAML mají stejnou schopnost pracovat se systémovými prostředky (přístup k síti, vznětlivé připojení k souboru, například) jako ekvivalentní generovaný kód. XAML načtený do plně důvěryhodné aplikace má stejný přístup k systémovým prostředkům jako hostitelská aplikace.

### <a name="code-access-security-cas-in-wpf"></a>Zabezpečení přístupu kódu (CAS) v WPF

**Tato část se vztahuje pouze na rozhraní .NET Framework. WPF pro .NET Core nepodporuje CAS. Další informace naleznete v [tématu Code Access Security differences](../migration/differences-from-net-framework.md#code-access-security).**

WPF pro rozhraní .NET Framework podporuje zabezpečení přístupu ke kódu (CAS). To znamená, že obsah WPF spuštěný v zóně Internet má snížená oprávnění k provádění. "Loose XAML" (stránky nekompilovanéxaml interpretovány v době načítání prohlížečem XAML) a XBAP jsou obvykle spuštěny v této internetové zóně a používají stejnou sadu oprávnění. XAML načtený do plně důvěryhodné aplikace má však stejný přístup k systémovým prostředkům jako hostitelská aplikace. Další informace naleznete v tématu [WPF Partial Trust Security](../../framework/wpf/wpf-partial-trust-security.md).

## <a name="loading-xaml-from-code"></a>Načítání XAML z kódu

XAML lze definovat všechny uživatelské ho uživatelského prohlášení, ale někdy je také vhodné definovat pouze část uživatelského uvisu v XAML. Tuto funkci lze použít k povolení částečného přizpůsobení, místního úložiště informací, použití xaml k poskytnutí obchodního objektu nebo různých možných scénářů. Klíčem k těmto scénářům <xref:System.Windows.Markup.XamlReader> je <xref:System.Windows.Markup.XamlReader.Load%2A> třída a její metoda. Vstup je soubor XAML a výstup je objekt, který představuje všechny run-time strom objektů, které byly vytvořeny z této značky. Potom můžete vložit objekt jako vlastnost jiného objektu, který již v aplikaci existuje. Pokud je vlastnost vhodnou vlastností v modelu obsahu, která má možnosti zobrazení a která upozorní spuštění motoru, že nový obsah byl přidán do aplikace, můžete snadno upravit obsah spuštěné aplikace načtením v XAML. Pro rozhraní .NET Framework je tato funkce obecně k dispozici pouze v plně důvěryhodných aplikacích z důvodu zřejmých důsledků zabezpečení načítání souborů do aplikací při jejich spuštění.

## <a name="see-also"></a>Viz také

- [Podrobná syntaxe XAML](../../framework/wpf/advanced/xaml-syntax-in-detail.md)
- [XAML a vlastní třídy pro WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Jazykové funkce kompatibility značek (mc:)](../xaml-services/namespace-language-features.md)
- [Rozšíření WPF XAML](../../framework/wpf/advanced/wpf-xaml-extensions.md)
- [Přehled základních elementů](../../framework/wpf/advanced/base-elements-overview.md)
- [Stromy v subsystému WPF](../../framework/wpf/advanced/trees-in-wpf.md)
