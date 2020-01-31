---
title: Přehled směrovaných událostí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached events [WPF]
- grouped button set [WPF]
- routed events [WPF]
- events [WPF], routed
- tunneling [WPF]
- events [WPF], attached
- routing strategies for events [WPF]
- button set [WPF], grouped
- bubbling [WPF]
ms.assetid: 1a2189ae-13b4-45b0-b12c-8de2e49c29d2
ms.openlocfilehash: f47eccac4e960bd6869da0da139803cd4e433393
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794293"
---
# <a name="routed-events-overview"></a>Přehled směrovaných událostí

Toto téma popisuje koncept směrovaných událostí v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Téma definuje terminologii směrované události. popisuje, jak jsou směrované směrované události směrovány prostřednictvím stromu prvků, shrnuje, jak zpracovávat směrované události a zavádí, jak vytvořit vlastní směrované události.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Požadavky

Toto téma předpokládá, že máte základní znalosti společného jazykového modulu runtime (CLR) a objektově orientovaného programování, a také koncept způsobu, jakým mohou být vztahy mezi prvky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koncepčně koncepční jako strom. Chcete-li postupovat podle příkladů v tomto tématu, měli byste také pochopit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a vědět, jak psát velmi základní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nebo stránky. Další informace najdete v tématu [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md) a [Přehled jazyka XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

<a name="routing"></a>

## <a name="what-is-a-routed-event"></a>Co je směrovaná událost?

Můžete si představit o směrovaných událostech buď z perspektivy funkčnosti nebo implementace. Obě definice jsou uvedené tady, protože někteří lidé hledají jednu nebo jinou definici užitečnější.

Definice funkce: nasměrovaná událost je typ události, která může vyvolat obslužné rutiny ve stromu elementu více posluchačů, nikoli jenom na objektu, který vyvolal událost.

Definice implementace: směrováná událost je událost modulu CLR, která je zajištěna instancí třídy <xref:System.Windows.RoutedEvent> a je zpracována [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]m systémem událostí.

Typická aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje mnoho prvků. Bez ohledu na to, zda jsou vytvořeny v kódu nebo deklarované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], tyto prvky existují v relaci stromu prvků navzájem. Trasa události může cestovat v jednom ze dvou směrů v závislosti na definici události, ale obecně se směruje ze zdrojového elementu a pak "bubliny" směrem nahoru přes strom elementů, dokud nedosáhne kořene stromu elementu (obvykle stránka nebo okno). Tento koncept probublávání může být obeznámený s tím, že jste předtím pracovali s modelem objektu DHTML.

Vezměte v úvahu následující jednoduchý strom elementů:

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

Tento strom elementu vytvoří něco podobného jako následující:

![Tlačítka Ano, ne a Storno](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")

V tomto zjednodušeném stromu prvků je zdrojem <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události jeden z <xref:System.Windows.Controls.Button> prvků a na základě toho, na kterém <xref:System.Windows.Controls.Button> byl kliknuto, je prvním prvkem, který má příležitost tuto událost zpracovat. Pokud ale žádná obslužná rutina není připojená k <xref:System.Windows.Controls.Button> v události funguje, pak se událost doplní směrem nahoru k <xref:System.Windows.Controls.Button> nadřazenému prvku stromu elementu, který je <xref:System.Windows.Controls.StackPanel>. Může se stát, že bubliny událostí budou <xref:System.Windows.Controls.Border>a potom mimo kořenový adresář stránky stromu elementu (nezobrazuje se).

Jinými slovy, trasa události pro tuto událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>:

Tlačítko--> StackPanel--> Border-->...

### <a name="top-level-scenarios-for-routed-events"></a>Scénáře nejvyšší úrovně pro směrované události

Následuje stručný souhrn scénářů, které motivují koncept směrované události a proč nebyla typická událost CLR pro tyto scénáře Dostačující:

**Složení a zapouzdření ovládacích prvků:** Různé ovládací prvky v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mají bohatý model obsahu. Například můžete umístit obrázek do <xref:System.Windows.Controls.Button>, který efektivně rozšiřuje vizuální strom tlačítka. Přidaný obrázek však nesmí přerušit chování testování přístupů, které způsobí, že tlačítko reaguje na <xref:System.Windows.Controls.Primitives.ButtonBase.Click> jeho obsahu, a to i v případě, že uživatel klikne na pixely, které jsou technicky součástí obrázku.

**Body příloh obslužných rutin jednotného** přiložených: V model Windows Forms bylo nutné několikrát připojit stejný popisovač pro zpracování událostí, které by mohly být vyvolány z více prvků. Směrované události umožňují připojit tuto obslužnou rutinu pouze jednou, jak je uvedeno v předchozím příkladu, a použít logiku obslužných rutin k určení, kde událost pochází v případě potřeby. Může to být například obslužná rutina pro dříve zobrazená [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:

[!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
[!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]

**Zpracování tříd:** Směrované události umožňují statickou obslužnou rutinu, která je definována třídou. Tato obslužná rutina třídy má příležitost zpracovat událost předtím, než mohou obslužné rutiny připojené instance.

**Odkazování na událost bez reflexe:** Některé techniky kódu a značek vyžadují způsob, jak identifikovat konkrétní událost. Nasměrovaná událost vytvoří pole <xref:System.Windows.RoutedEvent> jako identifikátor, který poskytuje robustní techniku identifikace události, která nevyžaduje statické nebo běhové odrazy.

### <a name="how-routed-events-are-implemented"></a>Jak jsou implementovány směrované události

Směrovaná událost je událost modulu CLR, která je zajištěna instancí třídy <xref:System.Windows.RoutedEvent> a zaregistrována v systému událostí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Instance <xref:System.Windows.RoutedEvent> získaná z registrace je obvykle uchována jako `public` členu pole `static` `readonly` třídy, která registruje a tedy "vlastní" směrované události. Připojení k identicky pojmenované události CLR (která je někdy označována jako "Obálka") je dosaženo přepsáním `add` a `remove` implementaci pro událost CLR. Obvykle `add` a `remove` jsou ponechány jako implicitní výchozí použití příslušné syntaxe události konkrétního jazyka pro přidávání a odebírání obslužných rutin této události. Směrování směrovaného a spojovacího mechanismu události je koncepčně podobné, jako vlastnost závislosti je vlastnost CLR, která je založená na třídě <xref:System.Windows.DependencyProperty> a zaregistrovaná v systému vlastností [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Následující příklad ukazuje deklaraci vlastní `Tap` směrované události, včetně registrace a vystavení pole identifikátoru <xref:System.Windows.RoutedEvent> a `add` a `remove` implementace pro událost `Tap` CLR.

[!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
[!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]

### <a name="routed-event-handlers-and-xaml"></a>Směrované obslužné rutiny událostí a XAML

Chcete-li přidat obslužnou rutinu pro událost pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], deklarujete název události jako atribut prvku, který je naslouchací proces události. Hodnota atributu je název vaší implementované metody obslužné rutiny, která musí existovat v částečné třídě souboru s kódem na pozadí.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

Syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro přidání standardních obslužných rutin událostí CLR je stejná pro přidání obslužných rutin směrovaného události, protože opravdu přidáváte obslužné rutiny do obálky události CLR, která má nasměrovanou implementaci události pod. Další informace o přidávání obslužných rutin událostí v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]naleznete v tématu [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

<a name="routing_strategies"></a>

## <a name="routing-strategies"></a>Strategie směrování

Směrované události používají jednu ze tří strategií směrování:

- **Probublávání:** Jsou vyvolány obslužné rutiny události ve zdroji události. Směrované událost pak směruje na po sobě jdoucí nadřazené prvky, dokud se nedostane do kořenového adresáře stromu elementu. Většina směrovaných událostí používá ke probublávání strategii směrování. Probublávání směrované události se obecně používají k hlášení vstupních nebo stavových změn z různých ovládacích prvků nebo jiných prvků uživatelského rozhraní.

- **Přímý odkaz:** Možnost vyvolat obslužné rutiny v reakci je dána pouze samotnému elementu source. To je obdobou "směrování", které model Windows Forms používá pro události. Nicméně na rozdíl od standardní události CLR, přímé směrované události podporují zpracování tříd (zpracování tříd je vysvětleno v nadcházející části) a lze je použít <xref:System.Windows.EventSetter> a <xref:System.Windows.EventTrigger>.

- **Tunelové propojení:** Zpočátku jsou vyvolány obslužné rutiny události v kořenovém adresáři stromu elementu. Směrovaná událost pak směrují trasu prostřednictvím po sobě jdoucích podřízených prvků podél trasy směrem k elementu uzlu, který je směrovaného zdroje událostí (prvek, který vyvolal směrovanou událost). Tunelové směrované události jsou často používány nebo zpracovávány jako součást skládání pro ovládací prvek, takže události ze složených částí mohou být záměrně potlačeny nebo nahrazeny událostmi, které jsou specifické pro úplný ovládací prvek. Vstupní události, které jsou k dispozici v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], se často implementují jako dvojice tunelování/probublávání. Události tunelování se také někdy označují jako události ve verzi Preview, protože se používají konvence pojmenování, která se používá pro páry.

<a name="why_use"></a>

## <a name="why-use-routed-events"></a>Proč používat směrované události?

Jako vývojář aplikace nemusíte vždycky znát ani se starat, že událost, kterou zpracováváte, je implementována jako směrovaná událost. Směrované události mají zvláštní chování, ale toto chování je převážně neviditelné, Pokud zpracováváte událost na prvku, kde je vyvolána.

Místo toho, aby směrované události byly výkonné, je použití některého z navrhovaných scénářů: definování běžných obslužných rutin na společném kořenovém adresáři, skládání vlastního ovládacího prvku nebo definování vlastní třídy ovládacího prvku.

Směrované naslouchací procesy událostí a směrované zdroje událostí nepotřebují sdílení společné události ve své hierarchii. Každý <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> může být naslouchací proces události pro všechny směrované události. Proto můžete použít úplnou sadu směrovaných událostí dostupných v rámci pracovní sady rozhraní API jako koncepční "rozhraní", aby různorodé prvky aplikace mohly vyměňovat informace o událostech. Tento koncept rozhraní pro směrované události je zvlášť použitelný pro události vstupu.

Směrované události lze také použít ke komunikaci mezi stromem elementu, protože data události pro událost jsou perpetuated ke každému prvku v trase. Jeden prvek může změnit něco v datech události a tato změna by byla k dispozici pro další prvek v trase.

Kromě aspektu směrování existují dva další důvody, proč může být jakákoli daná [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událost implementována jako směrované událost namísto standardní události CLR. Pokud implementujete vlastní události, můžete také zvážit tyto principy:

- Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce stylů a šablonování, jako je například <xref:System.Windows.EventSetter> a <xref:System.Windows.EventTrigger>, vyžadují směrované události na odkazovanou událost. Toto je výše zmíněný scénář identifikátoru události.

- Směrované události podporují mechanismus zpracování tříd, kdy třída může určovat statické metody, které mají příležitost zpracovat směrované události před tím, než k nim budou mít přístup všechny obslužné rutiny registrované instance. To je velmi užitečné v návrhu ovládacích prvků, protože vaše třída může vymáhat chování třídy řízené událostmi, které nelze omylem potlačit pomocí zpracování události v instanci.

Každé z výše uvedených doporučení je popsáno v samostatné části tohoto tématu.

<a name="event_handing"></a>

## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Přidání a implementace obslužné rutiny události pro směrovanou událost

Chcete-li přidat obslužnou rutinu události v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jednoduše přidáte název události do prvku jako atribut a nastavíte hodnotu atributu jako název obslužné rutiny události, která implementuje příslušný delegát, jak je uvedeno v následujícím příkladu.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

`b1SetColor` je název implementované obslužné rutiny, která obsahuje kód, který zpracovává událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>. `b1SetColor` musí mít stejnou signaturu jako <xref:System.Windows.RoutedEventHandler> delegát, což je delegát obslužné rutiny události pro událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>. První parametr všech delegátů směrované obslužné rutiny události Určuje prvek, ke kterému je přidána obslužná rutina události, a druhý parametr určuje data pro událost.

[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]

<xref:System.Windows.RoutedEventHandler> je základní delegát obslužné rutiny události. Pro směrované události, které jsou specializované pro určité ovládací prvky nebo scénáře, mohou být Delegáti použití pro směrované obslužné rutiny událostí také lépe specializované, aby mohli přenášet specializované údaje o událostech. Například v běžném vstupním scénáři můžete zpracovat událost směrované <xref:System.Windows.UIElement.DragEnter>. Obslužná rutina by měla implementovat delegáta <xref:System.Windows.DragEventHandler>. Pomocí nejvíce specifického delegáta můžete zpracovat <xref:System.Windows.DragEventArgs> v obslužné rutině a číst vlastnost <xref:System.Windows.DragEventArgs.Data%2A>, která obsahuje datovou část schránky operace přetažení.

Úplný příklad, jak přidat obslužnou rutinu události k elementu pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], najdete v tématu [zpracování směrované události](how-to-handle-a-routed-event.md).

Přidání obslužné rutiny pro směrovanou událost v aplikaci, která je vytvořena v kódu, je jednoduché. Směrované obslužné rutiny událostí lze vždy přidat prostřednictvím pomocné metody <xref:System.Windows.UIElement.AddHandler%2A> (což je stejná metoda, jakou stávající volání `add`.) Stávající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] směrované události však obvykle mají záložní implementace `add` a `remove` logiku, která umožňuje obslužné rutiny pro směrované události přidat syntaxí události specifické pro jazyk, což je intuitivnější syntaxe, než je pomocná metoda. Následuje příklad použití pomocné metody:

[!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
[!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]

Následující příklad ukazuje syntaxi C# operátoru (Visual Basic má mírně odlišnou syntaxi operátora z důvodu manipulace s odkazem):

[!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
[!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]

Příklad, jak přidat obslužnou rutinu události v kódu, naleznete v tématu [Přidání obslužné rutiny události pomocí kódu](how-to-add-an-event-handler-using-code.md).

Pokud používáte Visual Basic, můžete také použít klíčové slovo `Handles` pro přidání obslužných rutin jako součást deklarací obslužných rutin. Další informace naleznete v tématu [Visual Basic a zpracování událostí WPF](visual-basic-and-wpf-event-handling.md).

<a name="concept_handled"></a>

### <a name="the-concept-of-handled"></a>Koncept zpracování

Všechny směrované události sdílejí základní třídu dat události <xref:System.Windows.RoutedEventArgs>. <xref:System.Windows.RoutedEventArgs> definuje vlastnost <xref:System.Windows.RoutedEventArgs.Handled%2A>, která přijímá logickou hodnotu. Účelem vlastnosti <xref:System.Windows.RoutedEventArgs.Handled%2A> je povolení jakékoli obslužné rutiny události podél trasy k označení směrované události jako *zpracovaného*nastavením hodnoty <xref:System.Windows.RoutedEventArgs.Handled%2A> na `true`. Po zpracování obslužnou rutinou v jednom elementu v cestě se data sdílené události znovu nahlásí každému posluchači v trase.

Hodnota <xref:System.Windows.RoutedEventArgs.Handled%2A> má vliv na to, jak je nahlášena nebo zpracována směrované událost při jejich následném přenosu podél trasy. Pokud je <xref:System.Windows.RoutedEventArgs.Handled%2A> `true` v datech události pro směrovanou událost, pak obslužné rutiny, které naslouchají této události směrované na jiné prvky, nejsou obvykle vyvolány pro danou instanci události. To platí pro obslužné rutiny připojené v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a pro obslužné rutiny přidané syntaxmi příloh obslužných rutin událostí, jako jsou `+=` nebo `Handles`. U většiny běžných scénářů obslužných rutin se označením události jako zpracovávané nastaví <xref:System.Windows.RoutedEventArgs.Handled%2A> na `true` bude "Stop" směrování buď trasy tunelového propojení, nebo trasy k probublávání, a také pro všechny události, které jsou zpracovávány v určitém bodě trasy obslužnou rutinou třídy.

Nicméně existuje mechanismus "handledEventsToo", který naslouchací procesy stále můžou spouštět obslužné rutiny v reakci na směrované události, kde <xref:System.Windows.RoutedEventArgs.Handled%2A> `true` v datech události. Jinými slovy, trasa události není skutečně zastavena označením dat události jako zpracovávaných. Mechanismus handledEventsToo můžete použít pouze v kódu nebo v <xref:System.Windows.EventSetter>:

- V kódu namísto použití syntaxe události specifické pro jazyk, která funguje pro obecné události CLR, zavolejte metodu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> k přidání vaší obslužné rutiny. Zadejte hodnotu `handledEventsToo` jako `true`.

- V <xref:System.Windows.EventSetter>nastavte atribut <xref:System.Windows.EventSetter.HandledEventsToo%2A> na hodnotu `true`.

Kromě chování, které <xref:System.Windows.RoutedEventArgs.Handled%2A> stav vytváří ve směrovaných událostech, koncept <xref:System.Windows.RoutedEventArgs.Handled%2A> má vliv na to, jak byste měli navrhnout aplikaci a napsat kód obslužné rutiny události. Můžete conceptualize <xref:System.Windows.RoutedEventArgs.Handled%2A> jako jednoduchý protokol, který je vystavený směrovanými událostmi. Přesně to, jak tento protokol používáte, je až vám, ale koncepční návrh, jak má být hodnota <xref:System.Windows.RoutedEventArgs.Handled%2A> určená k použití, je následující:

- Pokud je směrováná událost označena jako zpracovaná, nemusí být zpracována dalšími prvky v této trase.

- Pokud směrované událost není označena jako zpracovaná, pak jiné naslouchací procesy, které byly dříve v trase, zvolily buď Neregistrovat obslužnou rutinu, nebo obslužné rutiny, které byly zaregistrovány, nepracují s daty události a nastaveny <xref:System.Windows.RoutedEventArgs.Handled%2A> na `true`. (Nebo je samozřejmě možné, že aktuální naslouchací proces je prvním bodem v trase.) Obslužné rutiny aktuálního naslouchacího procesu teď mají tři možné kurzy k akci:

  - Neprovádět žádnou akci. událost zůstává neošetřená a událost se směruje do dalšího naslouchacího procesu.

  - Spusťte kód jako odpověď na událost, ale zajistěte, aby akce, která byla provedena, nebyla dostatečně podstatná, aby bylo možné označit událost jako zpracovanou. Událost směruje do dalšího naslouchacího procesu.

  - Spustí kód jako odpověď na událost. Označte událost jako zpracovanou v datech události předaných obslužné rutině, protože provedena akce byla dostatečně podstatná, aby bylo možné označit, že se označení považuje za zpracovanou. Událost dál směruje na další naslouchací proces, ale s <xref:System.Windows.RoutedEventArgs.Handled%2A>=`true` v datech události, takže `handledEventsToo` posluchačů mají možnost vyvolat další obslužné rutiny.

Tento koncepční návrh je posílen výše zmíněným chováním směrování: je obtížnější (přestože je stále možné v kódu nebo stylů) připojit obslužné rutiny pro směrované události, které jsou vyvolány i v případě, že předchozí obslužná rutina v trase již nastavila <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true`.

Další informace o <xref:System.Windows.RoutedEventArgs.Handled%2A>, zpracování tříd směrovaných událostí a doporučeních, kdy je vhodné označit směrovanou událost jako <xref:System.Windows.RoutedEventArgs.Handled%2A>, naleznete v tématu [Označení směrovaných událostí jako zpracovaných a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).

V aplikacích je poměrně běžné zpracovávat pouze probublávání směrované události na objekt, který ji vyvolal, a nemusíte přitom zabývat charakteristikami směrování událostí. Přesto je však vhodné označit směrovanou událost jako zpracovanou v datech události, aby nedocházelo k neočekávaným vedlejším účinkům pouze v případě, že je k této stejné směrované události přidružena obslužná rutina.

<a name="class_handlers"></a>

## <a name="class-handlers"></a>Obslužné rutiny tříd

Pokud definujete třídu, která je odvozena nějakým způsobem z <xref:System.Windows.DependencyObject>, můžete také definovat a připojit obslužnou rutinu třídy pro směrovanou událost, která je deklarována nebo zděděná členem události vaší třídy. Obslužné rutiny třídy jsou vyvolány před všemi obslužnými rutinami naslouchacího procesu instance, které jsou připojeny k instanci této třídy, pokaždé, když směrované událost dosáhne instance elementu v cestě.

Některé ovládací prvky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mají podstatu zpracování tříd pro určité směrované události. To může vést k vnějšímu vzhledu, že směrované událost není nikdy vyvolána, ale ve skutečnosti se jedná o zpracování tříd a směrované událost může být zpracována vašimi obslužnými rutinami instance, pokud používáte určité techniky. Mnoho základních tříd a ovládacích prvků navíc zveřejňuje virtuální metody, které lze použít k přepsání chování zpracování třídy. Další informace o tom, jak obejít nepožadovanou manipulaci s třídou a definovat vlastní zpracování třídy ve vlastní třídě, naleznete v tématu [Označení směrovaných událostí jako zpracovaných a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).

<a name="attached_events"></a>

## <a name="attached-events-in-wpf"></a>Připojené události v subsystému WPF

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jazyk definuje také zvláštní typ události označovaný jako *připojená událost*. Připojená událost umožňuje přidat obslužnou rutinu pro konkrétní událost do libovolného elementu. Element, který zpracovává událost, nedefinuje ani nedědí připojenou událost, a ani objekt, který potenciálně nevyvolává událost, ani instance zpracování cíle musí definovat nebo jinak vlastnit tuto událost jako člena třídy.

Vstupní systém [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá rozsáhlou připojenou událost. Téměř všechny tyto připojené události jsou však předávány prostřednictvím základních prvků. Vstupní události se pak zobrazí jako ekvivalentní nepřipojené směrované události, které jsou členy třídy základního elementu. Například základní připojené události <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> lze snáze zpracovat na všech daných <xref:System.Windows.UIElement> pomocí <xref:System.Windows.UIElement.MouseDown> na daném <xref:System.Windows.UIElement>, nikoli v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kódu.

Další informace o připojených událostech v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]najdete v tématu [Přehled připojených událostí](attached-events-overview.md).

<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>

## <a name="qualified-event-names-in-xaml"></a>Kvalifikované názvy událostí v jazyce XAML

Jiné použití syntaxe, které se podobá *TypeName*. *EventName* připojená syntaxe události, ale není výhradně mluvit o využití připojené události je při připojování obslužných rutin pro směrované události, které jsou vyvolány podřízenými prvky. Obslužné rutiny připojíte ke společné nadřazené položce, abyste mohli využít výhod směrování událostí, i když společný nadřazený objekt nemusí mít příslušnou směrovanou událost jako člen. Zvažte tento příklad znovu:

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

Zde je posluchač nadřazeného elementu, kde je obslužná rutina přidána, <xref:System.Windows.Controls.StackPanel>. Přidává však obslužnou rutinu pro směrovanou událost, která byla deklarována a bude vyvolána třídou <xref:System.Windows.Controls.Button> (<xref:System.Windows.Controls.Primitives.ButtonBase> skutečně, ale je k dispozici <xref:System.Windows.Controls.Button> prostřednictvím dědičnosti). <xref:System.Windows.Controls.Button> "vlastní" událost, ale směrovaný systém událostí umožňuje, aby byly obslužné rutiny pro všechny směrované události připojeny k jakémukoli <xref:System.Windows.UIElement> nebo posluchači instance <xref:System.Windows.ContentElement>, který by jinak mohl připojit naslouchací procesy pro událost modulu CLR (Common Language Runtime). Výchozím oborem názvů xmlns pro tyto kvalifikované názvy atributů události je obvykle výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obor názvů xmlns, ale můžete také zadat předem fixní obory názvů pro vlastní směrované události. Další informace o xmlns naleznete v tématu [obory názvů XAML a mapování oboru názvů pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

<a name="how_event_processing_works"></a>

## <a name="wpf-input-events"></a>Události vstupu WPF

Jedna častá aplikace směrovaných událostí v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platformy je určena pro vstupní události. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tunelování názvů směrovaných událostí je předponou "Preview" podle konvence. Události vstupu často přicházejí ve dvojicích, přičemž jedna se jedná o událost probublávání a druhá je událost tunelování. Například událost <xref:System.Windows.ContentElement.KeyDown> a událost <xref:System.Windows.ContentElement.PreviewKeyDown> mají stejný podpis, přičemž původní je probublávání vstupní událost a druhá je vstupní událost tunelového propojení. V některých případech mají vstupní události pouze šíření verze, nebo možná pouze přímo směrované verze. V dokumentaci směrované témata událostí křížově odkazují na podobné směrované události s alternativními strategiemi směrování, pokud takové směrované události existují a že oddíly na spravovaných odkazech objasňují strategii směrování u každé směrované události.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vstupní události, které jsou součástí dvojic, jsou implementovány, aby jedna akce uživatele ze vstupu, například stisknutí tlačítka myši, vyvolala obě směrované události dvojice v sekvenci. Nejprve se vygeneruje událost tunelování a dojde k přenosu své trasy. Pak dojde k vyvolání události probublávání a k přenosu trasy. Dvě události doslova sdílejí stejnou instanci dat události, protože volání metody <xref:System.Windows.UIElement.RaiseEvent%2A> v implementované třídě, která vyvolává událost probublávání pro data události z události tunelování a znovu ji používá v nově vyvolané události. Naslouchací procesy s obslužnými rutinami pro událost tunelování mají první možnost označit zpracovávané směrované události (nejprve obslužné rutiny třídy a potom obslužné rutiny instance). Pokud prvek podél tunelového propojení označil směrovanou událost jako zpracovanou, jsou již zpracovaná data události odesílána pro událost probublávání a typické obslužné rutiny připojené k ekvivalentním vstupním událostem šíření nebudou vyvolány. K vnějším vzhledům bude jako v případě, že událost zpracovaného probublávání není ještě vyvolána. Toto chování při zpracování je užitečné pro skládání ovládacích prvků, kde můžete chtít, aby byly všechny vstupní události na základě testu a vstupní události na základě fokusu hlášeny konečným ovládacím prvkem, nikoli s jeho složenými částmi. Konečný element ovládacího prvku je bližší ke kořenu v skládání. proto má možnost nejprve zpracovat událost tunelového propojení a případně "nahradit", který směroval událost s větším ovládacím prvkem, jako součást kódu, který vrací ovládací prvek. Deník.

Jako příklad fungování zpracování událostí vstupu je třeba vzít v úvahu následující příklad události Input. Následující obrázek stromu `leaf element #2` je zdrojem `PreviewMouseDown` a pak `MouseDown` událost:

![Diagram směrování událostí](./media/routed-events-overview/input-event-routing.png)

Pořadí zpracování událostí je následující:

1. `PreviewMouseDown` (tunel) na kořenovém elementu.

2. `PreviewMouseDown` (tunelové propojení) na zprostředkujícím prvku #1.

3. `PreviewMouseDown` (tunel) na zdrojovém elementu #2.

4. `MouseDown` (bublinové) na zdrojovém prvku #2.

5. `MouseDown` (bublinové) na #1 mezilehlého prvku.

6. `MouseDown` (bublinové) na kořenovém elementu.

Delegát směrované obslužné rutiny události poskytuje odkazy na dva objekty: objekt, který vyvolal událost a objekt, kde byla obslužná rutina vyvolána. Objekt, kde byla obslužná rutina vyvolána, je objekt, který je hlášen parametrem `sender`. Objekt, ve kterém byla událost poprvé vyvolána, je hlášen vlastností <xref:System.Windows.RoutedEventArgs.Source%2A> v datech události. Směrovaná událost může být stále vyvolána a zpracována stejným objektem. v takovém případě `sender` a <xref:System.Windows.RoutedEventArgs.Source%2A> jsou identické (Jedná se o případ s kroky 3 a 4 v seznamu příkladů zpracování událostí).

Z důvodu tunelového propojení a probublávání jsou v nadřazených prvcích vstupní události, kde <xref:System.Windows.RoutedEventArgs.Source%2A> je jedním z jejich podřízených prvků. Pokud je důležité znát, co je zdrojový element, můžete identifikovat zdrojový element přístupem k vlastnosti <xref:System.Windows.RoutedEventArgs.Source%2A>.

Jakmile je vstupní událost označena <xref:System.Windows.RoutedEventArgs.Handled%2A>, další obslužné rutiny nejsou vyvolány. Obvykle je vhodné označit vstupní události jako zpracované, jakmile je vyvolána obslužná rutina, která řeší logické zpracování významu konkrétní události specifické pro danou aplikaci.

Výjimka z tohoto obecného příkazu o stavu <xref:System.Windows.RoutedEventArgs.Handled%2A> je, že vstupní obslužné rutiny událostí, které jsou zaregistrovány k úmyslnému ignorování <xref:System.Windows.RoutedEventArgs.Handled%2A> stavu dat události, by se pořád vyvolaly podél obou tras. Další informace naleznete v tématech [Náhled událostí](preview-events.md) nebo [Označení směrovaných událostí jako zpracovaných a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).

Sdílený datový model události mezi událostmi tunelového propojení a probublávání a sekvenčním vyzvednutím prvního tunelového propojení pak není koncept, který je obecně pravdivý pro všechny směrované události. Toto chování je implementováno konkrétně tím, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vstupní zařízení zvolí, aby vyvolala a připojila páry vstupních událostí. Implementace vlastních událostí vstupu je pokročilý scénář, ale můžete se rozhodnout, že tento model budete sledovat i pro vlastní vstupní události.

Určité třídy, které zpracovávají třídy, zpracovávají určité události, obvykle s záměrem předefinování toho, co konkrétní uživatelem řízená událost znamená v rámci tohoto ovládacího prvku a vyvolání nové události. Další informace naleznete v tématu [Označení směrovaných událostí jako zpracovaných a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).

Další informace o vstupu a způsobu interakce vstupu a událostí v typických aplikačních scénářích najdete v tématu [Přehled vstupu](input-overview.md).

<a name="events_styles"></a>

## <a name="eventsetters-and-eventtriggers"></a>EventSetters a EventTriggers

V části styly můžete zahrnout některé předem deklarované [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe zpracování událostí do značek pomocí <xref:System.Windows.EventSetter>. Při použití stylu je odkazovaná obslužná rutina přidána do instance s Style. <xref:System.Windows.EventSetter> lze deklarovat pouze pro směrovanou událost. Například: Všimněte si, že `b1SetColor` metoda, na kterou se odkazuje, je v souboru kódu na pozadí.

[!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]

Zde získaná výhoda spočívá v tom, že styl bude pravděpodobně obsahovat skvělé informace o dalších informacích, které by mohly být použity na jakékoli tlačítko v aplikaci a které <xref:System.Windows.EventSetter> být součástí tohoto stylu, propagují opětovné použití kódu i na úrovni značek. Kromě toho <xref:System.Windows.EventSetter> abstraktní názvy metod pro obslužné rutiny postupně od obecné aplikace a značky stránky.

Další specializovanou syntaxí, která kombinuje směrované funkce události a animace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je <xref:System.Windows.EventTrigger>. Stejně jako u <xref:System.Windows.EventSetter>se pro <xref:System.Windows.EventTrigger>můžou použít jenom směrované události. <xref:System.Windows.EventTrigger> je obvykle deklarován jako součást stylu, ale <xref:System.Windows.EventTrigger> lze také deklarovat na prvky na úrovni stránky jako součást kolekce <xref:System.Windows.FrameworkElement.Triggers%2A> nebo v <xref:System.Windows.Controls.ControlTemplate>. <xref:System.Windows.EventTrigger> umožňuje zadat <xref:System.Windows.Media.Animation.Storyboard>, která se spustí pokaždé, když směrované událost dosáhne prvku v cestě, který deklaruje <xref:System.Windows.EventTrigger> pro danou událost. Výhoda <xref:System.Windows.EventTrigger> přes pouze zpracování události a způsobila, že její spuštění v existujícím scénáři je, že <xref:System.Windows.EventTrigger> zajišťuje lepší kontrolu nad scénářem a jeho chování za běhu. Další informace najdete v tématu [použití triggerů událostí k řízení scénáře po jeho spuštění](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

<a name="more_about"></a>

## <a name="more-about-routed-events"></a>Další informace o směrovaných událostech

Toto téma popisuje hlavně směrované události z perspektivy popisující základní koncepty a nabízí pokyny k tomu, jak a kdy reagovat na směrované události, které jsou již přítomny v různých základních prvcích a ovládacích prvcích. Můžete však vytvořit vlastní směrovanou událost na vlastní třídě spolu se všemi nezbytnými podporami, jako jsou například specializované třídy dat události a Delegáti. Vlastníkem směrované události může být libovolná třída, ale směrované události musí být vyvolány a zpracovávány <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> odvozených třídách, aby byly užitečné. Další informace o vlastních událostech najdete v tématu [Vytvoření vlastní směrované události](how-to-create-a-custom-routed-event.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.EventManager>
- <xref:System.Windows.RoutedEvent>
- <xref:System.Windows.RoutedEventArgs>
- [Označení směrovaných událostí jako zpracovaných a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md)
- [Přehled vstupu](input-overview.md)
- [Přehled příkazů](commanding-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Stromy v subsystému WPF](trees-in-wpf.md)
- [Slabé vzory událostí](weak-event-patterns.md)
