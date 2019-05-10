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
ms.openlocfilehash: 7712ed02d20d692842267464a645bfc93ca8fd73
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063896"
---
# <a name="routed-events-overview"></a>Přehled směrovaných událostí
Toto téma popisuje koncept směrovaných událostí v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Téma definuje terminologie směrovaných událostí, popisuje, jak směrované události jsou směrovány stromové struktuře prvků, shrnuje, jak zpracování směrované události a seznámíte s vytvořením vlastní směrované události.
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že máte základní znalosti o [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] a objektově orientované programování, jakož i koncept jak vztahy mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky můžete conceptualized jako strom. Pokud chcete postupovat podle příkladů v tomto tématu, měli byste také znát [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a vědět, jak psát velmi základní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací nebo stránek. Další informace najdete v tématu [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md) a [přehled XAML (WPF)](xaml-overview-wpf.md).  
  
<a name="routing"></a>   
## <a name="what-is-a-routed-event"></a>Co je směrované události?  
 Se dá chápat směrovaných událostí z hlediska funkčnosti nebo implementace. Obě definice jsou uvedeny zde, protože někteří uživatelé přehlednější, jeden nebo jiné definici.  
  
 Funkční definice: Směrované události je typ události, který může vyvolat obslužné rutiny na víc naslouchacích procesů ve stromu, nikoli jen na objekt, který vyvolal událost.  
  
 Implementace definice: Směrované události je [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událost, která je založená na instanci <xref:System.Windows.RoutedEvent> třídy a zpracovává [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systém událostí.  
  
 Typické [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace obsahuje mnoho prvků. Ať už vytvořené v kódu nebo deklarované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], tyto prvky existují ve vztahu k sobě navzájem k elementu stromu. Směrování událostí můžete projít v jednom ze dvou směrech v závislosti na definici události, ale obecně trasa přenáší ze zdrojového prvku a potom "bubliny" směrem nahoru přes strom prvku dokud nedosáhne kořen stromu – element (obvykle na stránce nebo okno). Pokud jste už dříve pracovali s objektovém modelu DHTML, může být tento koncept šíření známými.  
  
 Vezměte v úvahu následující jednoduchý prvek stromu:  
  
 [!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 Tento strom prvku produkuje přibližně takto:  
  
 ![Ano, ne a stornovací tlačítka](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")  
  
 V tomto zjednodušené prvek stromu, příčiny <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí je jedním z <xref:System.Windows.Controls.Button> elementy a podle toho, co <xref:System.Windows.Controls.Button> došlo ke kliknutí na je první prvek, který se má zpracovat události. Ale pokud žádná obslužná rutina připojena k <xref:System.Windows.Controls.Button> funguje na události a události je předána nahoru na <xref:System.Windows.Controls.Button> nadřazené ve stromové struktuře element, který je <xref:System.Windows.Controls.StackPanel>. Potenciálně, bubliny událostí, které budou <xref:System.Windows.Controls.Border>a pak mimo ně na stránce kořen stromem prvků (není vidět).  
  
 Jinými slovy, trasy události pro tento <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost:  
  
 Tlačítko--> StackPanel--> Border - >...  
  
### <a name="top-level-scenarios-for-routed-events"></a>Nejvyšší úrovně scénáře pro směrované události  
 Tady je stručný přehled scénáře, které opodstatněny koncept směrované události a proč typické [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událost nebyla pro těchto scénářů:  
  
 **Kompozice ovládacích prvků a zapouzdření:** Různé ovládací prvky v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mají bohaté obsahu modelu. Můžete například umístit obrázek uvnitř <xref:System.Windows.Controls.Button>, což účinně rozšiřuje vizuálního stromu tlačítka. Ale přidání bitové kopie nesmí přerušit spuštění testu chování, které způsobí, že tlačítko reagovat na <xref:System.Windows.Controls.Primitives.ButtonBase.Click> jeho obsahu, i když uživatel klikne na pixelech, které jsou technicky součástí bitové kopie.  
  
 **Body připojení singulární obslužné rutiny:** V [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], budete muset připojit více než jednou stejnou obslužnou rutinu pro zpracování událostí, které může být vyvolána z více prvků. Směrované události vám umožní připojit tuto obslužnou rutinu pouze jednou, jak je znázorněno v předchozím příkladu a použijte obslužnou rutinu logiku k určení, odkud událost pochází v případě potřeby. Například to může být obslužná rutina pro dříve zobrazených [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
 [!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]  
  
 **Zpracování tříd:** Směrování událostí povolení statické obslužné rutiny, která je definována třída. Tato obslužná rutina třída má zpracovat před všechny připojené instance obslužné rutiny události.  
  
 **Odkazování na událost bez reflexe:** Některé metody kódu a kódu vyžadují způsob, jak identifikovat konkrétní události. Směrované události vytvoří <xref:System.Windows.RoutedEvent> pole jako identifikátor, který poskytuje robustní události identifikace techniku, která nevyžaduje statickou nebo za běhu reflexe.  
  
### <a name="how-routed-events-are-implemented"></a>Jak se implementují směrovaných událostí  
 Směrované události je [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událost, která je založená na instanci <xref:System.Windows.RoutedEvent> třídy a zaregistrovaného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém událostí. <xref:System.Windows.RoutedEvent> Instance získané z registrace se obvykle uchovávají jako `public` `static` `readonly` pole člena třídy, která registruje a proto "vlastní" směrované události. Připojení k identicky pojmenovanou [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událost (což je někdy označovány jako "obálky" události) se provádí tak, že přepíšete `add` a `remove` implementace [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událostí. Obvykle `add` a `remove` jsou ponechané jako implicitní výchozí, používající syntaxi odpovídající události specifické pro jazyk pro přidávání a odebírání obslužných rutin tuto událost. Mechanismu směrované události zálohování a připojení se koncepčně podobá jak vlastnost závislosti je [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost, která je založená na <xref:System.Windows.DependencyProperty> třídy a zaregistrovaného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému.  
  
 Následující příklad ukazuje deklaraci pro vlastní `Tap` směrované události, včetně registrace a působení <xref:System.Windows.RoutedEvent> identifikátor pole a `add` a `remove` implementace pro `Tap` [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událostí.  
  
 [!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
 [!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]  
  
### <a name="routed-event-handlers-and-xaml"></a>Obslužné rutiny směrovaných událostí a XAML  
 Chcete-li přidat obslužnou rutinu události použití [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], deklaruje název události jako atribut na prvek, který je naslouchací proces událostí. Hodnota atributu je název metody implementované obslužná rutina, která musí existovat v dílčí třídě soubor kódu na pozadí.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Syntaxe pro přidání standardní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obslužné rutiny událostí je stejný pro přidání obslužné rutiny směrovaných událostí, protože jsou ve skutečnosti přidáním obslužných rutin k [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obálky událostí, který obsahuje implementaci směrované události pod. Další informace o přidání obslužné rutiny událostí v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], naleznete v tématu [přehled XAML (WPF)](xaml-overview-wpf.md).  
  
<a name="routing_strategies"></a>   
## <a name="routing-strategies"></a>Strategie směrování  
 Směrování událostí, použijte jednu z tři strategie směrování:  
  
- **Šíření:** Obslužné rutiny událostí u zdroje události jsou vyvolány. Směrované události následně přesměruje do po sobě jdoucích nadřazených prvků, dokud nebude dosaženo kořenový prvek stromu. Většina směrovaných událostí pomocí šíření strategie směrování. Šíření směrovaných událostí se obecně používají k hlášení změn vstupu nebo stav z různých ovládacích prvků nebo další prvky uživatelského rozhraní.  
  
- **S přímým přístupem:** Pouze zdroj elementu samotného je příležitost k vyvolání obslužných rutin v odpovědi. To je obdobou "směrování", který [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] používá pro události. Ale na rozdíl od standardní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události, směrovat směrovaných událostí podporu zpracování třídy (třídy zpracování je vysvětleno v následující části) a mohou být využívána <xref:System.Windows.EventSetter> a <xref:System.Windows.EventTrigger>.  
  
- **Tunelové propojení:** Na začátku jsou vyvolány obslužných rutin událostí v kořenovém elementu stromu. Směrované události přenáší potom směrovat přes po sobě následujících podřízených elementů na trase směrem k uzlu elementu, který je zdrojem směrovaných událostí (prvku, který vyvolal směrované události). Tunelového propojení směrované události jsou často použít nebo zpracovávány jako součást kompozice pro ovládací prvek tak, aby události z složené částí lze záměrně potlačeno nebo nahrazuje události, které jsou specifické pro úplnou kontrolu. Vstupní události podle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] často pocházejí implementovaná jako dvojice šíření a tunelové propojení. Události tunelového propojení se také někdy označovány jako události ve verzi Preview, z důvodu zásady vytváření názvů, který se používá pro dvojice.  
  
<a name="why_use"></a>   
## <a name="why-use-routed-events"></a>Proč použití směrovaných událostí?  
 Jako vývojář aplikace vždy nepotřebujete vědět, nebo pro vás, že události, kterou obsluhujete je implementovaný jako směrovaných událostí. Směrované události mají zvláštní chování, ale toto chování je z velké části nepostřehnutelné Pokud obsluhujete událost v elementu, kde je vyvolána.  
  
 Kde stát výkonné směrovaných událostí je, pokud použijete některou z navrhovaných scénářích: definování běžné obslužné rutiny na společný kořen skládání vlastní ovládací prvek nebo definuje vlastní třídu vlastního ovládacího prvku.  
  
 Naslouchacích procesů směrovaných událostí a směrovaných událostí zdrojů není potřeba sdílet společný událost ve své hierarchii. Žádné <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> může být naslouchací proces událostí pro všechny směrované události. Proto můžete použít úplnou sadu směrovaných událostí, které jsou k dispozici v rámci pracovní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] nastavit jako konceptuální "rozhraní" kterým různorodých prvky v aplikaci si mohou vyměňovat informace o události. Tento koncept "rozhraní" pro směrované události platí zejména pro vstupní události.  
  
 Směrované události lze také komunikovat přes strom prvku vzhledem k tomu, že se data události pro událost perpetuated na každý prvek v této trase. Jeden element něco v datech událostí může změnit, a tato změna by být k dispozici na další prvek v trase.  
  
 Než směrování aspekt existují dva další důvody tohoto každá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události může být implementovaný jako směrovaných událostí místo standardní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událostí. Při implementaci vlastních událostí, můžete také zvážit tyto zásady:  
  
- Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] styly a šablony funkce, jako <xref:System.Windows.EventSetter> a <xref:System.Windows.EventTrigger> vyžadují odkazované událostí jako směrovaných událostí. Jedná se o scénář identifikátor událost již bylo zmíněno dříve.  
  
- Směrované události podporovat třídu zpracování mechanismus, kterým třídy můžete zadat statické metody, které se mají zpracovat směrovaných událostí, než k nim mít přístup všechny registrované instance obslužné rutiny. To je velmi užitečné ovládacího prvku návrhu, protože vaše třída může vynutit chování třídy založený na událostech, které nelze potlačit omylem zpracování události v instanci.  
  
 Každý z výše uvedených aspekty jsou popsány v samostatných oddílech tohoto tématu.  
  
<a name="event_handing"></a>   
## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Přidání a implementace obslužné rutiny události pro směrovanou událost  
 Chcete-li přidat obslužnou rutinu události v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], stačí jednoduše přidat název události na prvek jako atribut a nastavit hodnotu atributu název obslužné rutiny události, která implementuje delegáta odpovídající jako v následujícím příkladu.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 `b1SetColor` je název implementovaného obslužná rutina, která obsahuje kód, který zpracovává <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí. `b1SetColor` musí mít stejný podpis jako <xref:System.Windows.RoutedEventHandler> delegáta, který je delegát obslužné rutiny události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí. Všechny obslužné rutiny delegátů směrované události první parametr určuje prvek, na který se přidá obslužnou rutinu události a druhý parametr určuje data pro událost.  
  
[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]  
  
 <xref:System.Windows.RoutedEventHandler> je delegát obslužné rutiny základní směrované události. Směrované události, které jsou specializované pro určité ovládací prvky nebo scénáře delegáty pro obslužné rutiny směrovaných událostí také může stát více specializovaný, tak, aby se můžou přenášet data specializované události. Například v běžném scénáři vstupní, může zpracovat <xref:System.Windows.UIElement.DragEnter> směrované události. Vaše obslužná rutina by měly implementovat <xref:System.Windows.DragEventHandler> delegovat. S použitím nejspecifičtější delegáta, může zpracovat <xref:System.Windows.DragEventArgs> v obslužné rutiny a čtení <xref:System.Windows.DragEventArgs.Data%2A> vlastnost, která obsahuje datovou část schránky operace přetažení.  
  
 Úplný příklad toho, jak přidat obslužnou rutinu události k prvku pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], naleznete v tématu [zpracování události směrovat](how-to-handle-a-routed-event.md).  
  
 Přidání rutiny pro směrovanou událost v aplikaci, která se vytvoří v kódu je jednoduché. Obslužné rutiny směrovaných událostí je vždy možné přidat prostřednictvím Pomocná metoda <xref:System.Windows.UIElement.AddHandler%2A> (což je stejnou metodu, která vyžaduje existující základní `add`.) Ale existující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] směrované události mají obvykle zálohování implementace `add` a `remove` logiku, která umožní obslužné rutiny pro směrované události přidávané syntaxí event specifické pro jazyk, což je mnohem intuitivnější syntaxe než Pomocná metoda. Následuje příklad použití metody pomocné rutiny:  
  
 [!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
 [!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]  
  
 Další příklad ukazuje C# syntaxe – operátor (Visual Basic má syntaxi operátor mírně odlišné z důvodu jeho zpracování přesměrování):  
  
 [!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
 [!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]  
  
 Příklad toho, jak přidat obslužnou rutinu události v kódu, naleznete v tématu [přidat kód pomocí obslužné rutiny události](how-to-add-an-event-handler-using-code.md).  
  
 Pokud používáte Visual Basic, můžete také použít `Handles` – klíčové slovo pro přidání obslužné rutiny jako součást deklarace obslužných rutin. Další informace najdete v tématu [jazyka Visual Basic a WPF zpracování událostí](visual-basic-and-wpf-event-handling.md).  
  
<a name="concept_handled"></a>   
### <a name="the-concept-of-handled"></a>Zpracovává konceptu  
 Všechny směrovaných událostí sdílet společný události data základní třídu, <xref:System.Windows.RoutedEventArgs>. <xref:System.Windows.RoutedEventArgs> definuje <xref:System.Windows.RoutedEventArgs.Handled%2A> vlastnost, která přebírá hodnotu typu Boolean. Účelem <xref:System.Windows.RoutedEventArgs.Handled%2A> vlastnost je chcete povolit všechny obslužné rutiny události na trase k označení směrovaných událostí jako *zpracovává*, tak, že nastavíte hodnotu <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true`. Po zpracování dat na jeden element na trase obslužnou rutinou, data událostí sdílené nahlašuje znovu každý naslouchací proces na trase.  
  
 Hodnota <xref:System.Windows.RoutedEventArgs.Handled%2A> ovlivní způsob, jakým je směrované události hlásí nebo zpracovány při jejich přenosu mimo na trase. Pokud <xref:System.Windows.RoutedEventArgs.Handled%2A> je `true` události data pro směrované události a obslužné rutiny, které naslouchají na další prvky tohoto směrované události jsou obvykle již volána pro tuto instanci určité události. To platí, i pro obslužné rutiny připojena v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a přidal syntaxe přílohy obslužné rutiny události specifické pro jazyk, jako obslužné rutiny `+=` nebo `Handles`. Pro nejběžnější scénáře obslužné rutiny označování událostí jako ošetřena nastavením <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true` "přestane" směrování pro trasu tunelového propojení nebo šíření trasy a také pro událost, která je zpracovávána v okamžiku v trase třídy obslužnou rutinou.  
  
 Existuje ale "handledEventsToo" mechanismus, kterým naslouchacích procesů se ještě může spustit obslužných rutin v reakci na směrovaných událostí kde <xref:System.Windows.RoutedEventArgs.Handled%2A> je `true` v datech události. Jinými slovy směrování událostí není skutečně zastavená označením data události, která je zpracována. Mechanismus handledEventsToo můžete použít pouze v kódu nebo <xref:System.Windows.EventSetter>:  
  
- V kódu namísto pomocí syntaxe události specifické pro jazyk, který funguje u obecných [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události, zavolejte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metoda <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> přidat obslužnou rutinu. Zadejte hodnotu `handledEventsToo` jako `true`.  
  
- V <xref:System.Windows.EventSetter>, nastavte <xref:System.Windows.EventSetter.HandledEventsToo%2A> atribut `true`.  
  
 Kromě chování, které <xref:System.Windows.RoutedEventArgs.Handled%2A> stavu vytvoří ve směrovaných událostí konceptu <xref:System.Windows.RoutedEventArgs.Handled%2A> má vliv jak by měl Navrhněte svou aplikaci a napsat kód pro obslužnou rutinu události. Můžete pohodlným <xref:System.Windows.RoutedEventArgs.Handled%2A> jako jednoduchý protokol, který je zveřejněný prostřednictvím směrovaných událostí. Přesně, jak používáte tento protokol je až vás, ale návrh koncepční informace o hodnotu <xref:System.Windows.RoutedEventArgs.Handled%2A> je určena pro použití vypadá takto:  
  
- Pokud směrované události označení jako zpracované, následně nemusí zpracovávat jinými prvky této trase.  
  
- Pokud směrované události není označen jako zpracované, pak jiných naslouchacích procesů, které byly dříve na trase zvolili buď nechcete zaregistrovat obslužnou rutinu nebo obslužné rutiny, které byly registrované zvolili nechcete pracovat s daty události a nastavte <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true`. (Nebo, je samozřejmě možné, že aktuální naslouchací proces je první bod v postupu). Obslužné rutiny na aktuální naslouchací proces teď mají tři možné kurzy akce:  
  
    - Neprovádět žádnou akci vůbec; událost zůstává neošetřená a události směruje do další naslouchacího procesu.  
  
    - Spouštění kódu v reakci na událost, ale rozhodnout, že provedená akce nebyla dostatečně velké na to, aby fungovala jako zpracované označení události. Směrování událostí k dalším naslouchací proces.  
  
    - Spouštění kódu v reakci na událost. Označení jako zpracované události data předaná do obslužné rutiny, protože byla provedená akce považovány za dostatečně velké na to, aby fungovala označení jako zpracované události. Událost stále směruje na další naslouchací proces, ale s <xref:System.Windows.RoutedEventArgs.Handled%2A> = `true` v jeho data událostí, takže pouze `handledEventsToo` naslouchacích procesů příležitost k vyvolání další obslužné rutiny.  
  
 Tento návrh koncepční je posíleno chování směrování již bylo zmíněno dříve: je obtížnější (i když pořád v kódu nebo styly) připojit obslužné rutiny pro směrované události, které jsou vyvolány i v případě, že předchozí obslužnou rutinou na trase již nastaven <xref:System.Windows.RoutedEventArgs.Handled%2A>k `true`.  
  
 Další informace o <xref:System.Windows.RoutedEventArgs.Handled%2A>, zpracování třídy směrovaných událostí a doporučení o tom, kdy je vhodné k označení směrovaných událostí jako <xref:System.Windows.RoutedEventArgs.Handled%2A>, naleznete v tématu [označení směrované události jako Handled a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).  
  
 V aplikacích je celkem běžné právě zpracování šíření směrované události u objektu, která ji vyvolala a nesmí být obeznámeni s vlastností Směrování události vůbec. Je však stále vhodné k označení směrovaných událostí jako zpracované v případě, že data, aby se zabránilo neočekávané vedlejší účinky jsou jen pro případ, element, který je další nahoru stromem prvků má také obslužná rutina připojená pro tento stejný směrované události.  
  
<a name="class_handlers"></a>   
## <a name="class-handlers"></a>Třída obslužné rutiny  
 Pokud definujete třídu, která je odvozena z nějakým způsobem <xref:System.Windows.DependencyObject>, můžete také definujte a připojte obslužné rutiny třídy pro směrovanou událost, která je členem vaší třídy deklarované nebo zděděné události. Obslužné rutiny třídy jsou vyvolány před obslužné instance naslouchacího procesu, které jsou připojené k instanci této třídy, pokaždé, když se dosáhne směrované události instance elementu v jeho trasu.  
  
 Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky mají vlastní zpracování třídy pro určité směrovaných událostí. To může přidělit vnějšího vzhledu směrované události někdy není vyvolána, ale ve skutečnosti se třída zpracovává a směrované události mohou být zpracovávány obslužnými instance stále potenciálně, pokud použijete některé techniky. Navíc mnoho základních tříd a ovládací prvky vystavit virtuální metody, které můžete použít k přepsání zpracování chování třídy. Další informace o tom, jak obejít nežádoucí třídy zpracování a o definování vlastní zpracování ve třídě vlastní třídy naleznete v tématu [označení směrované události jako Handled a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="attached_events"></a>   
## <a name="attached-events-in-wpf"></a>Připojené události ve WPF  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Jazyk také definuje speciální typ události, volá se, *přidružená událost*. Připojené události umožňuje přidat obslužnou rutinu pro konkrétní události na libovolný element. Element zpracování události nemusí definovat nebo dědí přidružená událost a objekt potenciálně vyvolání události ani cílové zpracování instance musí definovat nebo jinak "vlastní" tuto událost jako člen třídy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vstupní systém hojně používá přidružené události. Ale téměř všechny tyto připojené události se předávají prostřednictvím základní elementy. Vstupní události potom zobrazí jako ekvivalentní nepřipojené směrovaných událostí, které jsou členy třídy base element. Například základní přidružená událost <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> informace snadno půjde na každá <xref:System.Windows.UIElement> pomocí <xref:System.Windows.UIElement.MouseDown> zabývat <xref:System.Windows.UIElement> místo zabývajících se syntaxí přidružená událost buď v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kódu.  
  
 Další informace o přidružené události v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], naleznete v tématu [přehled připojených událostí](attached-events-overview.md).  
  
<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>   
## <a name="qualified-event-names-in-xaml"></a>Názvy kvalifikované událostí v XAML  
 Další využití syntaxe, která se podobá *typename*. *EventName* syntaxe událost pro připojené, ale není přesněji řečeno je využití přidružená událost po připojení obslužné rutiny pro směrované události, které jsou vyvolány podřízené elementy. Připojte obslužné rutiny na společným nadřazeným prvkem, abyste mohli využívat směrování událostí, i když společným nadřazeným prvkem nemusí mít odpovídající směrovaných událostí jako člen. V tomto příkladu zvažte znovu:  
  
 [!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 Tady je nadřazený element naslouchací proces ve kterém se přidá obslužnou rutinu <xref:System.Windows.Controls.StackPanel>. Ale to je přidání obslužné rutiny pro směrovanou událost, která byla deklarována a bude aktivováno <xref:System.Windows.Controls.Button> třídy (<xref:System.Windows.Controls.Primitives.ButtonBase> ve skutečnosti, ale k dispozici <xref:System.Windows.Controls.Button> prostřednictvím dědičnosti). <xref:System.Windows.Controls.Button> "vlastní" události, ale systém směrované události povolení obslužné rutiny pro směrované události, které chcete připojit k libovolnému <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> instance naslouchací proces, který jinak přiložit naslouchacích procesů pro [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] událostí. Výchozí obor názvů xmlns pro tyto názvy atributů kvalifikovaný událost je obvykle výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] xmlns oboru názvů, ale můžete také určit předponou obory názvů pro vlastní směrované události. Další informace o xmlns najdete v tématu [obory názvů XAML a mapování Namespace pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="how_event_processing_works"></a>   
## <a name="wpf-input-events"></a>Události vstupu WPF  
 Časté provádění směrovaných událostí v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platforma je pro vstupní události. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tunelové propojení směrovaných událostí názvy jsou, začínají předponou "Preview" podle konvence. Vstupní události často jsou dostupné v párech, a jednu událost šíření a druhá je tunelového propojení událost. Například <xref:System.Windows.ContentElement.KeyDown> událostí a <xref:System.Windows.ContentElement.PreviewKeyDown> události mají stejnou signaturu, s bývalé Probíhá šíření vstupní události a ten se tunelového propojení vstupní události. Vstupní události v některých případech pouze mají šíření verze nebo může být s přímým přístupem směrované verze. Dokumentace směrované události témata křížový odkaz podobně jako směrovaných událostí s alternativní strategie směrování pokud takové směrovaných událostí neexistuje, a části stránky pro spravované referenční materiály zjednodušili, strategie směrování směrovaných událostí.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vstupní události, které dostaneme v dvojice jsou implementované tak, aby jedna akce uživatele ze vstupu, jako je například stisknutí tlačítka myši, vyvolají pořadí obou směrovaných událostí, které odpovídá páru licencí. Nejprve tunelového propojení událost se vyvolá a jeho trasu se přenáší. Pak šíření událost se vyvolá a jeho trasu se přenáší. Dvě události doslova sdílejí stejné instance dat události, protože <xref:System.Windows.UIElement.RaiseEvent%2A> volání metody v implementující třídu, která vyvolává událost šíření naslouchá na data událostí z tunelového propojení událost a znovu ho použije v nové vyvolanou událost. Naslouchací procesy s obslužnými rutinami pro tunelového propojení událost mít první příležitosti k označení směrovaných událostí zpracovat (obslužné rutiny třídy nejprve pak instance obslužné rutiny). Pokud element trase tunelového propojení označení směrovaných událostí jako zpracované, data již zpracovává události se odesílají na pro šíření událostí a typické obslužnými rutinami připojenými ekvivalent šíření vstupní události nebudou vyvolány. Do vnějšího vzhledu metoda bude, jako kdyby nebyl zpracované šíření událost ještě vyvolá. Toto chování zpracování je užitečné pro ovládací prvek skládání, kdy chcete všechna spuštění testu na základě události vstupu nebo vstupní události na základě fokus má být hlášen konečné ovládacího prvku, spíše než její části složené. Poslední ovládací prvek je blíž ke kořenu v skládání a proto má možnost Třída zpracovat tunelového propojení událost první a pravděpodobně "nahradit" příslušné směrované události pomocí ovládacího prvku konkrétní události, jako součást kód, který zálohuje ovládacího prvku Třída.  
  
 Jako ukázku jak vstupní funguje pro zpracování událostí zvažte následující příklad vstupní události. Na následujícím obrázku stromu `leaf element #2` je zdrojem i `PreviewMouseDown` a pak `MouseDown` události:  
  
 ![Směrování událostí – diagram](./media/routed-events-overview/input-event-routing.png)  
  
 Pořadí zpracování události je následující:  
  
1. `PreviewMouseDown` (tunelu) na kořenový element.  
  
2. `PreviewMouseDown` (tunelu) zprostředkující elementu #1.  
  
3. `PreviewMouseDown` (tunelu) pro element source #2.  
  
4. `MouseDown` (bublinový) pro element source #2.  
  
5. `MouseDown` (bublinový) zprostředkující elementu #1.  
  
6. `MouseDown` (bublinový) na kořenový element.  
  
 Delegát obslužné rutiny směrované události obsahuje odkazy na dva objekty: objekt, který vyvolal událost a objekt, kde byla vyvolána obslužná rutina. Pokud byla vyvolána obslužná rutina je objekt hlášených `sender` parametru. Objekt, kde byla nejprve vyvolána událost je ohlášena <xref:System.Windows.RoutedEventArgs.Source%2A> vlastnost data události. Směrované události stále můžete vyvolána a zpracovat stejný objekt, v takovém případě `sender` a <xref:System.Windows.RoutedEventArgs.Source%2A> jsou identické (tomu se kroky 3 a 4, událostí zpracování seznam příkladů).  
  
 Z důvodu šíření a tunelové propojení nadřazených prvků přijímat události vstupu kde <xref:System.Windows.RoutedEventArgs.Source%2A> je jedním z jejich podřízených elementů. Pokud je důležité vědět, co je source element, můžete identifikovat source element díky přístupu <xref:System.Windows.RoutedEventArgs.Source%2A> vlastnost.  
  
 Obvykle Jakmile je označen vstupní události <xref:System.Windows.RoutedEventArgs.Handled%2A>, dále nejsou vyvolány obslužné rutiny. Obvykle byste měli označit vstupní události jako zpracované ihned poté, co je vyvolána obslužná rutina, které řeší vaše konkrétní aplikaci logické zpracování význam vstupní události.  
  
 Výjimkou z tohoto obecné prohlášení o <xref:System.Windows.RoutedEventArgs.Handled%2A> stav je danou vstupní obslužné rutiny událostí, které jsou registrované na záměrně Ignorovat <xref:System.Windows.RoutedEventArgs.Handled%2A> stavu data událostí by stále volat buď trase. Další informace najdete v tématu [události náhledu](preview-events.md) nebo [označení směrované události jako Handled a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).  
  
 Datový model sdílené událostí mezi událostmi tunelového propojení a šíření a sekvenční vyvolání první tunelového propojení potom šíření událostí, není konceptu, které obecně platí pro všechny směrovaných událostí. Konkrétně je chování implementované jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vstupní zařízení zvolte vyvolání a připojit páry vstupní události. Implementace vlastní události vstupu je pokročilý scénář, ale můžete také postupovat podle tohoto modelu pro vstupní události.  
  
 Určité třídy zvolte třídy – zpracování některých vstupní události, obvykle se záměrem, nově definují obor konkrétní vstupní události řízené uživatele znamená v rámci ovládacího prvku a vyvolání nové události. Další informace najdete v tématu [označení směrované události jako Handled a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md).  
  
 Další informace o vstupu a vstupu a události interakci v typických aplikačních scénářů, najdete v části [vstupní přehled](input-overview.md).  
  
<a name="events_styles"></a>   
## <a name="eventsetters-and-eventtriggers"></a>EventSetters a EventTriggers  
 Styly, může obsahovat některé předem deklarovat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zpracování syntaxe v kódu s použitím událostí <xref:System.Windows.EventSetter>. Když tento styl aplikován, přidá se do upravený instance odkazované obslužné rutiny. Je možné deklarovat <xref:System.Windows.EventSetter> pouze pro směrovanou událost. Následuje příklad. Všimněte si, že `b1SetColor` zde odkazovaná metoda je v souboru kódu na pozadí.  
  
 [!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]  
  
 Využívat získané zde je, že styl by mohla obsahovat spoustu dalších informací, které může použít jakékoli tlačítko ve vaší aplikaci, a <xref:System.Windows.EventSetter> být součástí tohoto stylu podporuje opakované využívání kódu i na úrovni kódu. Navíc <xref:System.Windows.EventSetter> abstrahuje názvy metod pro obslužné rutiny ještě o krok směrem od obecné kód aplikace a stránky.  
  
 Jiné speciální syntaxi, která kombinuje směrovaných událostí a animace funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je <xref:System.Windows.EventTrigger>. Stejně jako u <xref:System.Windows.EventSetter>, pouze směrovaných událostí mohou být použity pro <xref:System.Windows.EventTrigger>. Obvykle <xref:System.Windows.EventTrigger> je deklarován jako součást styl, ale <xref:System.Windows.EventTrigger> lze také deklarovat na úrovni stránky prvky jako součást <xref:System.Windows.FrameworkElement.Triggers%2A> kolekce, nebo v <xref:System.Windows.Controls.ControlTemplate>. <xref:System.Windows.EventTrigger> Umožňují zadat <xref:System.Windows.Media.Animation.Storyboard> , že se spustí pokaždé, když směrované události dosáhne elementu v jeho trasu, která deklaruje <xref:System.Windows.EventTrigger> pro tuto událost. Výhodou <xref:System.Windows.EventTrigger> přes právě zpracování událostí a způsobit tak, aby se začala existujícího scénáře je, že <xref:System.Windows.EventTrigger> poskytuje lepší kontrolu nad scénáři a její chování za běhu. Další informace najdete v tématu [použitím aktivačních procedur událostí pro řízení scénáře po jeho spuštění](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
<a name="more_about"></a>   
## <a name="more-about-routed-events"></a>Další informace o směrované události  
 Toto téma popisuje hlavně směrovaných událostí z hlediska popisující o základních konceptech a doprovodné materiály o tom, a reagovat na směrovaných událostí, které jsou už k dispozici v různých základních elementů a ovládacích prvků. Můžete však vytvořit vlastní směrované události na vaše vlastní třídy a všechny nezbytné podporu, jako je například datových tříd událostí specializované a delegáti. Vlastník směrované události může být libovolná třída, ale musí být směrované události vyvolané službou a zpracovány <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> odvozené třídy, aby byla užitečná. Další informace o vlastních událostech najdete v tématu [vytvoření vlastní události směrovat](how-to-create-a-custom-routed-event.md).  
  
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
