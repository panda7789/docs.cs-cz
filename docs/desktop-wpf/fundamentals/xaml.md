---
title: Přehled XAML
description: Přečtěte si, jak je jazyk XAML strukturovaný a implementovaný pomocí Windows Presentation Foundation (WPF) pro .NET Core.
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
# <a name="xaml-overview-in-wpf"></a>Přehled XAML v subsystému WPF

Tento článek popisuje funkce jazyka XAML a ukazuje, jak lze použít XAML k psaní Windows Presentation Foundationch aplikací (WPF). Tento článek konkrétně popisuje XAML, jak je implementováno v jazyce WPF. Samotný XAML je větší jazyk konceptu než WPF.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-xaml"></a>Co je XAML

XAML je deklarativní jazyk značení. V programovacím modelu .NET Core jazyk XAML zjednodušuje vytváření uživatelského rozhraní pro aplikaci .NET Core. Můžete vytvořit viditelné prvky uživatelského rozhraní v deklarativním kódu XAML a potom oddělit definici uživatelského rozhraní od běhové logiky pomocí souborů kódu na pozadí, které jsou připojeny ke značkám prostřednictvím definic dílčí třídy. XAML přímo představuje instanci objektů v konkrétní sadě typů zálohování definovaných v sestaveních. To se na rozdíl od většiny ostatních jazyků značek, což je obvykle interpretovaný jazyk bez přímé propojení na systém back-Type. XAML umožňuje pracovní postup, ve kterém můžou samostatné strany pracovat na uživatelském rozhraní a logice aplikace, a to pomocí potenciálně různých nástrojů.

V případě, že jsou reprezentovány jako text, soubory XAML jsou `.xaml` soubory XML, které mají obvykle příponu. Soubory mohou být kódovány jakýmkoli kódováním XML, ale kódování jako UTF-8 je typické.

Následující příklad ukazuje, jakým způsobem můžete vytvořit tlačítko jako součást uživatelského rozhraní. Tento příklad je určen k poskytnutí charakteru, jak XAML představuje společné programování uživatelského rozhraní metaphors (není to kompletní ukázka).

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

## <a name="xaml-syntax-in-brief"></a>Stručná syntaxe jazyka XAML

Následující části vysvětlují základní formy syntaxe jazyka XAML a poskytují krátký příklad označení. Tyto části nejsou určeny k poskytování úplných informací o jednotlivých formulářích syntaxe, například o tom, jak jsou reprezentovány v systému typů zálohování. Další informace o konkrétních syntaxech syntaxe jazyka XAML naleznete v tématu [syntaxe jazyka XAML podrobněji](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

Většina materiálu v následujících částech bude základní pro vás, pokud jste dříve obeznámeni s jazykem XML. Toto je důsledek jednoho ze základních principů návrhu jazyka XAML. Jazyk XAML definuje koncepty vlastní, ale tyto koncepty fungují v jazyce XML a formuláři s označením.

### <a name="xaml-object-elements"></a>Elementy objektu XAML

Prvek objektu obvykle deklaruje instanci typu. Tento typ je definován v sestaveních, na které odkazuje technologie, která používá XAML jako jazyk.

Syntaxe elementu objektu vždy začíná levou lomenou závorkou (`<`). Následuje název typu, ve kterém chcete vytvořit instanci. (Název může obsahovat předponu, koncept, který bude vysvětlen později.) Potom můžete volitelně deklarovat atributy elementu Object. Chcete-li dokončit značku prvku objektu, ukončete pravou ostrou závorku`>`(). Místo toho můžete použít samoobslužný formulář, který nemá žádný obsah, doplněním značky s lomítkem a pravou ostrou závorkou v úspěchu (`/>`). Podívejte se například na dříve zobrazený fragment kódu znovu.

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

To určuje dva prvky objektu: `<StackPanel>` (s obsahem a koncovou značku později) a `<Button .../>` (formulář pro samoobslužné zavírání s několika atributy). Prvky `StackPanel` objektu a `Button` každé mapování na název třídy, která je definována WPF a je součástí sestavení WPF. Když zadáte značku prvku objektu, vytvoříte instrukci pro zpracování XAML pro vytvoření nové instance základního typu. Každá instance je vytvořena voláním konstruktoru bez parametrů základního typu při analýze a načítání XAML.

### <a name="attribute-syntax-properties"></a>Syntaxe atributu (vlastnosti)

Vlastnosti objektu lze často vyjádřit jako atributy elementu Object. Syntaxe atributu vyjmenovává vlastnost objektu, která je právě nastavena, následovaná operátorem přiřazení (=). Hodnota atributu je vždy zadána jako řetězec, který je obsažen v uvozovkách.

Syntaxe atributu je nejefektivnější syntaxe nastavení vlastností a je nejpohodlnější syntaxe, která se používá pro vývojáře, kteří používali jazyky značek v minulosti. Například následující kód vytvoří tlačítko, které má červený text a modré pozadí vedle zobrazení textu zadaného jako `Content`.

[!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]

### <a name="property-element-syntax"></a>Syntaxe elementu vlastnosti

U některých vlastností elementu Object není syntaxe atributu možná, protože objekt nebo informace, které jsou nezbytné k poskytnutí hodnoty vlastnosti, nelze přiměřeně vyjádřit v rámci značky uvozovek a omezením řetězce syntaxe atributu. V těchto případech lze použít jinou syntaxi známou jako syntaxe prvku vlastnosti.

Syntaxe pro počáteční značku elementu vlastnosti je `<TypeName.PropertyName>`. Obecně platí, že obsah této značky je prvek objektu typu, který vlastnost přebírá jako hodnotu. Po zadání obsahu je nutné zavřít element Property s koncovou značkou. Syntaxe pro koncovou značku je `</TypeName.PropertyName>`.

Pokud je možné syntaxi atributu, použití syntaxe atributu je obvykle pohodlnější a umožňuje více kompaktních značek, ale to je často pouze druh stylu, nikoli technické omezení. Následující příklad ukazuje stejné vlastnosti jako v předchozím příkladu syntaxe atributu, ale tentokrát pomocí syntaxe elementu Property pro všechny vlastnosti `Button`.

[!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]

### <a name="collection-syntax"></a>Syntaxe kolekce

Jazyk XAML obsahuje několik optimalizací, které poskytují uživatelsky čitelné značky. Taková optimalizace je taková, že pokud konkrétní vlastnost přebírá typ kolekce, pak položky, které deklarujete jako podřízené prvky v rámci této hodnoty této vlastnosti, se stanou součástí kolekce. V tomto případě kolekce podřízených prvků objektu je hodnota nastavená na vlastnost kolekce.

Následující příklad ukazuje syntaxi kolekce pro nastavení hodnot <xref:System.Windows.Media.GradientBrush.GradientStops%2A> vlastnosti.

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

XAML Určuje funkci jazyka, kde třída může určit přesně jednu z vlastností, která má být vlastností _obsahu_ XAML. Podřízené prvky tohoto prvku objektu slouží k nastavení hodnoty této vlastnosti obsahu. Jinými slovy, pro vlastnost obsahu lze jedinečně vynechat element Property při nastavení této vlastnosti v kódu XAML a vytvořit viditelné nadřazené/podřízené metafora ve značce.

Například <xref:System.Windows.Controls.Border> určuje vlastnost _obsahu_ pro <xref:System.Windows.Controls.Decorator.Child%2A>. Následující dva <xref:System.Windows.Controls.Border> prvky jsou zpracovány identicky. První z nich využívá syntaxi vlastnosti obsahu a vynechává prvek `Border.Child` vlastnosti. Druhá z nich se `Border.Child` zobrazí explicitně.

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

Jako pravidlo jazyka XAML musí být hodnota vlastnosti obsahu XAML předána zcela před nebo zcela po všech ostatních prvcích vlastností na daném objektovém prvku. Například následující kód není zkompilován.

```xaml
<Button>I am a
  <Button.Background>Blue</Button.Background>
  blue button</Button>
```

Další informace o konkrétních syntaxech syntaxe jazyka XAML naleznete v tématu [syntaxe jazyka XAML podrobněji](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

### <a name="text-content"></a>Textový obsah

Malý počet prvků XAML může přímo zpracovat text jako svůj obsah. Pokud to chcete povolit, musí mít jeden z následujících případů hodnotu true:

- Třída musí deklarovat vlastnost obsahu a tato vlastnost obsahu musí být typu, který lze přiřadit k řetězci (typ může být <xref:System.Object>). <xref:System.Windows.Controls.ContentControl> Například jakékoli použití <xref:System.Windows.Controls.ContentControl.Content%2A> jako jeho vlastnost obsahu a je typu <xref:System.Object>a to podporuje následující použití na, <xref:System.Windows.Controls.ContentControl> například <xref:System.Windows.Controls.Button>:. `<Button>Hello</Button>`

- Typ musí deklarovat konvertor typu. v takovém případě je textový obsah použit jako inicializační text pro tento konvertor typu. Například `<Brush>Blue</Brush>` převede hodnotu obsahu `Blue` do štětce. Tento případ je v praxi méně běžný.

- Typ musí být známý primitivní jazyk XAML.

### <a name="content-properties-and-collection-syntax-combined"></a>Kombinované vlastnosti obsahu a syntaxe kolekce

Vezměte v úvahu tento příklad.

```xaml
<StackPanel>
  <Button>First Button</Button>
  <Button>Second Button</Button>
</StackPanel>
```

Tady je každý <xref:System.Windows.Controls.Button> podřízený prvek <xref:System.Windows.Controls.StackPanel>. Toto je zjednodušený a intuitivní kód, který vynechává dvě značky ze dvou různých důvodů.

- **Vynechaný element vlastnosti StackPanel. Children:** <xref:System.Windows.Controls.StackPanel> je odvozený <xref:System.Windows.Controls.Panel>od. <xref:System.Windows.Controls.Panel>definuje <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> jako vlastnost obsahu XAML.

- **Vynechán prvek objektu UIElementCollection:** <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> Vlastnost přebírá typ <xref:System.Windows.Controls.UIElementCollection>, který implementuje <xref:System.Collections.IList>. Značku prvku kolekce lze vynechat na základě pravidel jazyka XAML pro zpracování kolekcí, jako je <xref:System.Collections.IList>například. (V tomto případě nemůžete vytvořit instanci, <xref:System.Windows.Controls.UIElementCollection> protože nezveřejňuje konstruktor bez parametrů, což je důvod, proč je prvek <xref:System.Windows.Controls.UIElementCollection> objektu zobrazen jako komentář).

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

Syntaxi atributů lze také použít pro členy, kteří jsou události, nikoli vlastnosti. V tomto případě je názvem atributu název události. V implementaci WPF událostí pro XAML je hodnota atributu název obslužné rutiny, která implementuje delegáta události. Například následující kód přiřadí obslužnou rutinu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události pro událost <xref:System.Windows.Controls.Button> vytvořenou v kódu:

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

V subsystému WPF existuje více událostí a XAML než pouze tento příklad syntaxe atributu. Například můžete mít na `ClickHandler` něco, co tady je znázorněno a jak je definováno. To bude vysvětleno v nadcházejících [událostech a](#events-and-xaml-code-behind) v tomto článku v části s kódem na pozadí.

## <a name="case-and-white-space-in-xaml"></a>Velikosti písmen a mezer v jazyce XAML

Obecně platí, že XAML rozlišuje velká a malá písmena. Pro účely překladu typů zálohování WPF XAML rozlišuje velká a malá písmena se stejnými pravidly, jako je u CLR velká a malá písmena. Prvky objektu, prvky vlastností a názvy atributů musí být zadány pomocí citlivých malých a velkých písmen v porovnání s názvem k základnímu typu v sestavení nebo pro člena typu. V jazyce XAML a primitivních klíčích jsou rozlišována velká a malá písmena. V hodnotách nejsou rozlišována malá a velká písmena. Rozlišování velkých a malých písmen pro hodnoty závisí na chování převaděče typů přidružené k vlastnosti, která přebírá hodnotu, nebo na typ hodnoty vlastnosti. <xref:System.Boolean> Například vlastnosti, které přebírají typ, mohou přijímat buď `true` `True` ekvivalentní hodnoty, ale pouze proto, že NATIVNÍ převod typu analyzátoru WPF XAML pro řetězec na <xref:System.Boolean> již je povoluje jako ekvivalenty.

Procesory a serializace WPF XAML budou ignorovat nebo odstranit všechny nevýznamné prázdné znaky a budou normalizovat jakékoli významné prázdné znaky. To je konzistentní s výchozími doporučeními pro chování prázdných míst specifikace jazyka XAML. Toto chování je pouze v případě, že zadáte řetězce v rámci vlastností obsahu XAML. V nejjednodušším smyslu XAML převede znaky mezer, odřádkování a tabulátoru na mezery a pak zachová jeden prostor, pokud se najde na konci souvislého řetězce. Úplné vysvětlení zpracování prázdných míst v jazyce XAML není zahrnuto v tomto článku. Další informace naleznete v tématu [prázdné místo zpracování v jazyce XAML](../xaml-services/white-space-processing.md).

## <a name="markup-extensions"></a>Rozšíření značek

Rozšíření značek jsou koncept jazyka XAML. Při použití k poskytnutí hodnoty syntaxe atributu, složené závorky (`{` a `}`) označují použití rozšíření značek. Toto využití směruje zpracování XAML za účelem sekvence z obecného zpracování hodnot atributů jako řetězcového literálu nebo hodnoty převoditelné z řetězce.

Nejběžnější přípony značek používané v programování aplikací WPF jsou [`Binding`](../../framework/wpf/advanced/binding-markup-extension.md)používány pro výrazy datových vazeb a odkazy [`StaticResource`](../../framework/wpf/advanced/staticresource-markup-extension.md) na prostředky a. [`DynamicResource`](../../framework/wpf/advanced/dynamicresource-markup-extension.md) Pomocí rozšíření značek můžete použít syntaxi atributu k poskytnutí hodnot pro vlastnosti, i když tato vlastnost obecně nepodporuje syntaxi atributu. Rozšíření značek často používají typy mezilehlého výrazu k povolení funkcí, jako je například odložení hodnot nebo odkazování na jiné objekty, které jsou přítomny pouze v době běhu.

Například následující kód nastaví hodnotu <xref:System.Windows.FrameworkElement.Style%2A> vlastnosti pomocí syntaxe atributu. <xref:System.Windows.FrameworkElement.Style%2A> Vlastnost přebírá instanci <xref:System.Windows.Style> třídy, ve které se ve výchozím nastavení nedala vytvořit instance řetězcem syntaxe atributu. Ale v tomto případě atribut odkazuje na konkrétní rozšíření značek, `StaticResource`. Při zpracování tohoto rozšíření značek vrátí odkaz na styl, který byl dříve vytvořen jako prostředek s klíčem ve slovníku prostředků.

[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]

Odkaz na seznam všech rozšíření značek pro jazyk XAML implementovaný konkrétně v technologii WPF naleznete v tématu [rozšíření WPF XAML](../../framework/wpf/advanced/wpf-xaml-extensions.md). Pro odkazový seznam rozšíření značek, která jsou definována v System. XAML a jsou širší pro implementaci .NET Core XAML, naleznete v tématu [obor názvů XAML (x:). Jazykové funkce](../xaml-services/namespace-language-features.md). Další informace o konceptech rozšíření značek naleznete v tématu [rozšíření značek a WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

## <a name="type-converters"></a>Převaděče typů

V [syntaxi jazyka XAML v krátkém](#xaml-syntax-in-brief) oddílu bylo uvedeno, že hodnota atributu musí být schopna nastavit řetězec. Základní, nativní zpracování způsobu převodu řetězců do jiných typů objektů nebo primitivních hodnot je založen na <xref:System.String> typu samotném, a to i na nativní zpracování pro určité typy, jako je <xref:System.DateTime> například <xref:System.Uri>nebo. Ale mnoho typů WPF nebo členů těchto typů rozšiřuje základní chování při zpracování atributů řetězců takovým způsobem, že instance složitějších typů objektů mohou být zadány jako řetězce a atributy.

<xref:System.Windows.Thickness> Struktura je příkladem typu, který má povolen převod typu pro použití v jazyce XAML. <xref:System.Windows.Thickness>označuje měření v rámci vnořeného obdélníku a používá se jako hodnota pro vlastnosti, <xref:System.Windows.FrameworkElement.Margin%2A>jako je například. Umístěním převaděče typu na <xref:System.Windows.Thickness>, všechny vlastnosti, které používají <xref:System.Windows.Thickness> , je snazší zadat v jazyce XAML, protože mohou být zadány jako atributy. Následující příklad používá převod typu a syntaxi atributu k poskytnutí hodnoty pro <xref:System.Windows.FrameworkElement.Margin%2A>:

[!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]

Příklad syntaxe předchozího atributu je ekvivalentní následujícímu příkladu syntaxe verbose, kde <xref:System.Windows.FrameworkElement.Margin%2A> je místo toho nastaveno prostřednictvím syntaxe elementu Property obsahující prvek <xref:System.Windows.Thickness> Object. Čtyři klíčové vlastnosti pro <xref:System.Windows.Thickness> jsou nastaveny jako atributy nové instance:

[!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]

> [!NOTE]
> Existuje také omezený počet objektů, kde je převod typu jediným veřejným způsobem, jak nastavit vlastnost na tento typ bez použití podtřídy, protože samotný typ nemá konstruktor bez parametrů. Příklad: <xref:System.Windows.Input.Cursor>.

Další informace o převodu typů naleznete v tématu [TypeConverters a XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md).

## <a name="xaml-root-elements-and-xaml-namespaces"></a>Kořenové elementy XAML a obory názvů XAML

Soubor XAML musí mít pouze jeden kořenový element, aby mohl být ve správném formátu XML a platný soubor XAML. V typických scénářích WPF použijete kořenový prvek, který má výrazný význam v modelu aplikace WPF ( <xref:System.Windows.Window> například nebo <xref:System.Windows.Controls.Page> pro stránku, <xref:System.Windows.ResourceDictionary> pro externí slovník nebo <xref:System.Windows.Application> pro definici aplikace). Následující příklad ukazuje kořenový prvek typického souboru XAML pro stránku WPF s kořenovým elementem <xref:System.Windows.Controls.Page>.

[!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]

Kořenový element obsahuje také atributy `xmlns` a. `xmlns:x` Tyto atributy označují procesor XAML, který obsahuje obory názvů XAML definice typu pro typy back-Types, které budou odkazovat jako prvky. `xmlns` Atribut konkrétně určuje výchozí obor názvů XAML. V rámci výchozího oboru názvů XAML lze prvky objektu v kódu zadat bez předpony. Pro většinu scénářů aplikace WPF a pro téměř všechny příklady uvedené v oddílech WPF sady SDK je výchozí obor názvů jazyka XAML mapován na obor názvů `http://schemas.microsoft.com/winfx/2006/xaml/presentation`WPF. `xmlns:x` Atribut označuje další obor názvů XAML, který mapuje obor názvů `http://schemas.microsoft.com/winfx/2006/xaml`jazyka XAML.

Toto použití `xmlns` pro definování oboru pro použití a mapování namescope je konzistentní se specifikací XML 1,0. Obory názvů WPF XAML se liší od XML obory názvů WPF pouze v tom, že XAML namescope také znamená něco o tom, jak jsou prvky namescope zálohovány typy, pokud je k dispozici pro rozlišení typu a při analýze XAML.

`xmlns` Atributy jsou pouze naprosto nezbytné v kořenovém elementu každého souboru XAML. `xmlns`definice budou použity pro všechny následníky kořenového prvku (Toto chování je znovu konzistentní se specifikací XML 1,0 pro `xmlns`.) `xmlns` atributy jsou povoleny také na jiných prvcích pod kořenem a platí pro všechny následníky definující element. Časté definice nebo předefinování oborů názvů XAML ale mohou mít za následek, že je obtížné číst styl kódu XAML.

Implementace WPF svého procesoru v jazyce XAML zahrnuje infrastrukturu, která obsahuje povědomí o základních sestaveních WPF. Základní sestavení WPF jsou známá, aby obsahovala typy, které podporují mapování WPF na výchozí obor názvů XAML. Tato možnost je povolena prostřednictvím konfigurace, která je součástí souboru sestavení projektu a systémů sestavení a projektů WPF. Proto deklarace výchozího oboru názvů XAML jako výchozí `xmlns` je vše, co je nezbytné pro odkazování na prvky XAML, které pocházejí ze sestavení WPF.

### <a name="the-x-prefix"></a>X: prefix

V předchozím příkladu kořenového elementu se předpona `x:` použila k mapování oboru názvů `http://schemas.microsoft.com/winfx/2006/xaml`XAML, což je vyhrazený obor názvů XAML, který podporuje konstrukce jazyka XAML. Tato `x:` předpona se používá pro mapování tohoto oboru názvů XAML v šablonách projektů, v příkladech a v dokumentaci v rámci této sady SDK. Obor názvů XAML pro jazyk XAML obsahuje několik programovacích konstrukcí, které budou často používány v jazyce XAML. Následuje seznam nejběžnějších `x:` programovacích konstrukcí, které budete používat:

- [x:Key –](../xaml-services/xkey-directive.md): nastavuje jedinečný klíč pro každý prostředek v rámci <xref:System.Windows.ResourceDictionary> (nebo v podobných konceptech slovníku v jiných rozhraních). `x:Key`budou pravděpodobně účtovány v 90 procentech `x:` využití, která se zobrazí v typickém kódu aplikace WPF.

- [x:Class](../xaml-services/xclass-directive.md): Určuje obor názvů a název třídy CLR pro třídu, která poskytuje kód na pozadí stránky XAML. Je nutné, aby taková třída podporovala kód na základě programovacího modelu WPF, a proto téměř vždy vidíte `x:` namapované, i když nejsou k dispozici žádné prostředky.

- [x:Name](../xaml-services/xname-directive.md): Určuje název objektu modulu runtime pro instanci, která existuje v běhovém kódu po zpracování elementu Object. Obecně platí, že často použijete ekvivalentní vlastnost pro [x:Name](../xaml-services/xname-directive.md), která je definována pro WPF. Tyto vlastnosti jsou mapovány konkrétně na vlastnost zálohování CLR a jsou proto pohodlnější pro programování aplikací, kde často používáte běhový kód k nalezení pojmenovaných prvků z inicializovaného kódu XAML. Nejběžnější taková vlastnost je <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>. Můžete i nadále používat [x:Name](../xaml-services/xname-directive.md) , pokud není ekvivalentní vlastnost na úrovni <xref:System.Windows.FrameworkElement.Name%2A> architektury WPF na daném typu podporována. K tomu dochází v některých scénářích animace.

- [x:static](../xaml-services/xstatic-markup-extension.md): povolí odkaz, který vrací statickou hodnotu, která není jinak vlastností kompatibilní s jazykem XAML.

- [x:Type](../xaml-services/xtype-markup-extension.md): vytvoří <xref:System.Type> odkaz na základě názvu typu. Tato možnost slouží k určení atributů, které <xref:System.Type>přebírají, <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>například, přestože často vlastnost má nativní<xref:System.Type> převod řetězce na převod takovým způsobem, že použití rozšíření značek [x:Type](../xaml-services/xtype-markup-extension.md) je volitelné.

Existují další programovací konstrukce v oboru názvů `x:` prefix/XAML, které nejsou tak běžné. Podrobnosti najdete v tématu [obor názvů XAML (x:). Jazykové funkce](../xaml-services/namespace-language-features.md).

## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Vlastní předpony a vlastní typy v jazyce XAML

Pro vlastní sestavení nebo pro sestavení mimo rozhraní WPF Core of **PresentationCore**, **PresentationFramework** a **WindowsBase**můžete zadat sestavení jako součást vlastního `xmlns` mapování. Pak můžete odkazovat na typy z tohoto sestavení v jazyce XAML, pokud je tento typ správně implementován pro podporu použití jazyka XAML, které zkoušíte.

Následuje základní příklad, jak vlastní předpony fungují v kódu XAML. Předpona `custom` je definována ve značce kořenového prvku a namapována na konkrétní sestavení, které je zabaleno a k dispozici v aplikaci. Toto sestavení obsahuje typ `NumericUpDown`, který je implementován pro podporu obecného použití jazyka XAML, a také použití dědičnosti třídy, která umožňuje jeho vložení na tento konkrétní bod v modelu obsahu WPF XAML. Instance tohoto `NumericUpDown` ovládacího prvku je deklarována jako element Object s použitím předpony tak, aby analyzátor XAML věděl, který obor názvů XAML obsahuje typ, a proto, kde záložní sestavení obsahuje definici typu.

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

Další informace o vlastních typech v jazyce XAML naleznete v tématu [XAML a vlastní třídy pro WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).

Další informace o tom, jak se v sestavení vztahují obory názvů XML a obory názvů kódu, naleznete v tématu [obory názvů XAML a mapování oboru názvů pro WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

## <a name="events-and-xaml-code-behind"></a>Události a kód XAML – na pozadí

Většina aplikací WPF se skládá z kódu XAML i kódu na pozadí. V rámci projektu je kód XAML napsán jako `.xaml` soubor a jazyk CLR, jako je například Microsoft Visual Basic nebo C#, je použit k zápisu souboru kódu na pozadí. Je-li soubor XAML kód kompilován jako součást programovacích a aplikačních modelů WPF, umístění souboru kódu XAML pro soubor XAML je identifikováno zadáním oboru názvů a třídy jako `x:Class` atributu kořenového prvku XAML.

V uvedených příkladech jste viděli několik tlačítek, ale žádná z těchto tlačítek neměla k nim přidruženo žádné logické chování. Primární mechanismus na úrovni aplikace pro přidání chování pro prvek objektu je použít existující událost třídy elementu a zapsat konkrétní obslužnou rutinu pro tuto událost, která je vyvolána, když je událost vyvolána za běhu. Název události a název obslužné rutiny, které se mají použít, jsou uvedeny v označení, zatímco kód, který implementuje vaši obslužnou rutinu, je definován v kódu na pozadí.

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

[!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
[!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]

Všimněte si, že soubor s kódem na pozadí používá obor `ExampleNamespace` názvů CLR a `ExamplePage` deklaruje jako částečnou třídu v rámci tohoto oboru názvů. Tím se `x:Class` paralelně hodnota atributu `ExampleNamespace`.`ExamplePage` který byl zadán v kořenovém adresáři značek. Kompilátor značek WPF vytvoří částečnou třídu pro všechny kompilované soubory XAML odvozením třídy z typu kořenového prvku. Pokud zadáte kód na pozadí, který také definuje stejnou částečnou třídu, výsledný kód je sloučen do stejného oboru názvů a třídy kompilované aplikace.

Další informace o požadavcích programování kódu na pozadí v technologii WPF naleznete v tématu [Code-na, obslužná rutina události a požadavky na částečnou třídu v](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md#code-behind-event-handler-and-partial-class-requirements-in-wpf)subsystému WPF.

Pokud nechcete vytvořit samostatný soubor kódu na pozadí, můžete také vložit kód do souboru XAML. Vložený kód je však méně univerzální technikou, která má významná omezení. Další informace naleznete v tématu [Code-na a XAML v](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)subsystému WPF.

### <a name="routed-events"></a>Směrované události

Konkrétní funkce události, která je základem pro WPF, je směrná událost. Směrované události umožňují elementu zpracovávat události, které byly vyvolány jiným prvkem, pokud jsou prvky propojeny pomocí relace stromu. Při zadávání zpracování událostí pomocí atributu XAML lze směrovat směrované události pro libovolný element, včetně prvků, které neuvádějí tuto konkrétní událost v tabulce členů třídy. To je dosaženo zařazením atributu název události s názvem vlastnící třídy. Například `StackPanel` nadřazená položka v pokračujícím `StackPanel`  /  `Button` příkladu by mohla zaregistrovat obslužnou <xref:System.Windows.Controls.Primitives.ButtonBase.Click> rutinu pro událost tlačítka podřízeného elementu zadáním atributu `Button.Click` u prvku `StackPanel` objektu s názvem obslužné rutiny jako hodnotou atributu. Další informace najdete v tématu [Přehled směrovaných událostí](../../framework/wpf/advanced/routed-events-overview.md).

## <a name="xaml-named-elements"></a>Pojmenované elementy XAML

Ve výchozím nastavení instance objektu, která je vytvořena v grafu objektů zpracováním elementu objektu XAML, nemá jedinečný identifikátor nebo odkaz na objekt. Naproti tomu, pokud voláte konstruktor v kódu, skoro vždy použijete výsledek konstruktoru pro nastavení proměnné na vytvořenou instanci, takže můžete odkazovat na instanci později v kódu. Za účelem zajištění standardizovaného přístupu k objektům, které byly vytvořeny pomocí definice kódu, XAML definuje [atribut x:Name](../xaml-services/xname-directive.md). Můžete nastavit hodnotu `x:Name` atributu u libovolného elementu Object. V kódu na pozadí se identifikátor, který zvolíte, odpovídá proměnné instance, která odkazuje na vytvořenou instanci. Ve všech ohledech se funkce pojmenované prvky, jako by šlo o instance objektů (název odkazuje na tuto instanci), a váš kód na pozadí může odkazovat na pojmenované prvky pro zpracování interakcí za běhu v rámci aplikace. Toto připojení mezi instancemi a proměnnými je provedeno kompilátorem kódu XAML WPF a konkrétně zahrnuje funkce a vzory, jako například <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> , které nebudou podrobněji popsány v tomto článku.

Prvky XAML na úrovni architektury WPF dědí <xref:System.Windows.FrameworkElement.Name%2A> vlastnost, která je ekvivalentní atributu definovanému `x:Name` XAML. Některé jiné třídy také poskytují ekvivalenty na úrovni vlastnosti pro `x:Name`, což je také obecně definováno jako `Name` vlastnost. Obecně řečeno, pokud nemůžete najít `Name` vlastnost v tabulce Members pro zvolený element/typ, použijte `x:Name` místo toho. `x:Name` Hodnoty budou poskytovat identifikátor prvku jazyka XAML, který lze použít v době běhu, a to buď pomocí specifických subsystémů, nebo pomocí pomocných metod, jako <xref:System.Windows.FrameworkElement.FindName%2A>je.

Následující příklad nastaví <xref:System.Windows.FrameworkElement.Name%2A> u <xref:System.Windows.Controls.StackPanel> prvku. Pak <xref:System.Windows.Controls.Button> obslužná rutina v rámci, která <xref:System.Windows.Controls.StackPanel> odkazuje na <xref:System.Windows.Controls.StackPanel> odkaz `buttonContainer` prostřednictvím své instance, je nastavena <xref:System.Windows.FrameworkElement.Name%2A>pomocí.

[!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]

[!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
[!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]

Podobně jako u proměnné se název XAML pro instanci řídí konceptem oboru, aby bylo možné názvy vynutily, aby byly jedinečné v rámci určitého oboru, který je předvídatelný. Primární kód, který definuje stránku, označuje jednu jedinečnou namescope XAML s hranicí namescope XAML, která je kořenovým prvkem této stránky. Nicméně jiné zdroje značek mohou pracovat se stránkou v době běhu, jako jsou styly nebo šablony v rámci stylů, a tyto zdroje značek často mají vlastní obory názvů WPF XAML, které nemusí být nutně připojeny k namescopeu stránky XAML. Další informace o `x:Name` a XAML obory názvů WPF naleznete v tématu <xref:System.Windows.FrameworkElement.Name%2A>, [direktive x:Name](../xaml-services/xname-directive.md)nebo [WPF XAML obory názvů WPF](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

## <a name="attached-properties-and-attached-events"></a>Připojené vlastnosti a připojené události

XAML Určuje funkci jazyka, která umožňuje určit určité vlastnosti nebo události v jakémkoli elementu bez ohledu na to, zda vlastnost nebo událost existují v definicích typu prvku, na kterém je nastavena. Verze vlastností této funkce se nazývá připojená vlastnost, verze události se nazývá připojená událost. V konceptuální části si můžete představit připojené vlastnosti a připojené události jako globální členy, které lze nastavit u libovolné instance elementu nebo objektu XAML. Nicméně tento element nebo třída nebo větší infrastruktura musí podporovat úložiště vlastností pro připojené hodnoty.

Připojené vlastnosti v jazyce XAML se obvykle používají prostřednictvím syntaxe atributu. V syntaxi atributu zadáte připojenou vlastnost ve formuláři `ownerType.propertyName`.

`ownerType` Po navýšení se to podobá použití prvku vlastnosti, ale v tomto případě je vždy jiný typ než prvek objektu, kde je nastavena připojená vlastnost. `ownerType`je typ, který poskytuje přístupové metody, které jsou vyžadovány procesorem XAML, aby bylo možné získat nebo nastavit hodnotu připojené vlastnosti.

Nejběžnějším scénářem pro připojené vlastnosti je povolení podřízených prvků pro hlášení hodnoty vlastnosti do jejich nadřazeného prvku.

Následující příklad znázorňuje <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> připojenou vlastnost. <xref:System.Windows.Controls.DockPanel> Třída definuje přistupující objekty pro <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> a proto vlastní připojenou vlastnost. <xref:System.Windows.Controls.DockPanel> Třída také obsahuje logiku, která prochází své podřízené prvky a konkrétně kontroluje každý prvek pro sadu hodnoty <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Pokud je nalezena hodnota, tato hodnota se používá během rozložení k umístění podřízených elementů. Použití <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> připojené vlastnosti a tato schopnost umístění je ve skutečnosti scénář motivace pro <xref:System.Windows.Controls.DockPanel> třídu.

[!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]

Ve WPF je většina nebo všechny připojené vlastnosti implementovány také jako vlastnosti závislosti. Další informace najdete v tématu [Přehled připojených vlastností](../../framework/wpf/advanced/attached-properties-overview.md).

Připojené události používají podobný `ownerType.eventName` tvar syntaxe atributu. Stejně jako nepřipojené události určuje hodnota atributu připojené události v jazyce XAML název metody obslužné rutiny, která je vyvolána při zpracování události na elementu. Připojená používání událostí v jazyce WPF XAML jsou méně společná. Další informace najdete v tématu [Přehled připojených událostí](../../framework/wpf/advanced/attached-events-overview.md).

## <a name="base-types-and-xaml"></a>Základní typy a XAML

Základní WPF XAML a jeho obor názvů XAML je kolekce typů, které odpovídají objektům CLR, kromě prvků značek pro XAML. Ne všechny třídy však mohou být mapovány na prvky. Abstraktní třídy, jako <xref:System.Windows.Controls.Primitives.ButtonBase>jsou a určité neabstraktní základní třídy, jsou používány pro dědění v modelu objektů CLR. Základní třídy, včetně abstraktních, jsou stále důležité pro vývoj v jazyce XAML, protože každý z konkrétních prvků XAML dědí členy z některé základní třídy ve své hierarchii. Tyto členy často obsahují vlastnosti, které lze nastavit jako atributy prvku nebo události, které lze zpracovat. <xref:System.Windows.FrameworkElement>je konkrétní základní třídou uživatelského rozhraní WPF na úrovni architektury WPF. Při navrhování uživatelského rozhraní použijete různé třídy Shape, panel, dekoratér nebo Control, které jsou odvozeny z <xref:System.Windows.FrameworkElement>. Související základní třída <xref:System.Windows.FrameworkContentElement>, podporuje prvky orientované na dokument, které dobře fungují pro prezentaci plovoucího rozložení, používají rozhraní API, která záměrně zrcadlí rozhraní API <xref:System.Windows.FrameworkElement>v nástroji. Kombinace atributů na úrovni prvku a objektového modelu CLR poskytuje sadu společných vlastností, které lze nastavit pro většinu betonových prvků XAML, bez ohledu na konkrétní prvek XAML a jeho nadřízený typ.

## <a name="xaml-security"></a>Zabezpečení XAML

XAML je jazyk značek, který přímo představuje instanci objektu a provádění. Proto prvky vytvořené v jazyce XAML mají stejnou schopnost pracovat se systémovými prostředky (například přístup k síti, vstupně-výstupní operace systému souborů) jako ekvivalentní generovaný kód. XAML načtený v plně důvěryhodné aplikaci má stejný přístup k systémovým prostředkům, jako hostující aplikace.

### <a name="code-access-security-cas-in-wpf"></a>Zabezpečení přístupu kódu (CAS) v subsystému WPF

**Tato část se týká jenom .NET Framework. WPF pro .NET Core nepodporuje CAS. Další informace najdete v tématu [rozdíly v zabezpečení přístupu ke kódu](../migration/differences-from-net-framework.md#code-access-security).**

WPF pro .NET Framework podporuje zabezpečení přístupu kódu (CAS). To znamená, že obsah WPF běžící v zóně Internet má omezená oprávnění ke spuštění. "Volné XAML" (stránky nekompilovaného XAML interpretované v době načtení prohlížečem XAML) a XBAP jsou obvykle spouštěny v této zóně Internetu a používají stejnou sadu oprávnění. Nicméně XAML načtený v plně důvěryhodné aplikaci má stejný přístup k systémovým prostředkům, jako hostující aplikace. Další informace najdete v tématu [zabezpečení částečné důvěryhodnosti WPF](../../framework/wpf/wpf-partial-trust-security.md).

## <a name="loading-xaml-from-code"></a>Načítání XAML z kódu

XAML lze použít k definování celého uživatelského rozhraní, ale je někdy také vhodné definovat pouze část uživatelského rozhraní v jazyce XAML. Tato funkce se dá použít k povolení částečného přizpůsobení, místního úložiště informací, použití XAML k poskytnutí podnikového objektu nebo nejrůznějších možných scénářů. Klíčem k těmto scénářům je <xref:System.Windows.Markup.XamlReader> třída a její <xref:System.Windows.Markup.XamlReader.Load%2A> metoda. Vstup je soubor XAML a výstup je objekt, který reprezentuje všechny běhové stromové struktury objektů, které byly vytvořeny z tohoto kódu. Pak můžete objekt vložit jako vlastnost jiného objektu, který již v aplikaci existuje. Pokud je vlastnost vhodnou vlastností v modelu obsahu, která má příslušně zobrazené možnosti zobrazení a upozorní prováděcí modul, že se do aplikace přidal nový obsah, můžete snadno upravovat obsah běžící aplikace načtením v jazyce XAML. Pro .NET Framework je tato funkce všeobecně dostupná jenom v aplikacích s plnou důvěryhodností, protože se jedná o zjevné důsledky zabezpečení při načítání souborů do aplikací při jejich spuštění.

## <a name="see-also"></a>Viz také

- [Podrobná syntaxe XAML](../../framework/wpf/advanced/xaml-syntax-in-detail.md)
- [XAML a vlastní třídy pro WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Jazykové funkce kompatibility značek (mc:)](../xaml-services/namespace-language-features.md)
- [Rozšíření WPF XAML](../../framework/wpf/advanced/wpf-xaml-extensions.md)
- [Přehled základních elementů](../../framework/wpf/advanced/base-elements-overview.md)
- [Stromy v subsystému WPF](../../framework/wpf/advanced/trees-in-wpf.md)
