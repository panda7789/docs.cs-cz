---
title: Přehled směrovaných událostí
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 896f3b852c00b9c7cd031710dbdaa00974428344
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="routed-events-overview"></a>Přehled směrovaných událostí
Toto téma popisuje koncept směrované události v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Téma definuje terminologie směrované události, popisuje, jak jsou směrované události směrován přes stromu elementů, shrnuje, jak zpracovávat směrované události a jak vytvořit vlastní směrované událostí zavádí.
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že máte základní znalosti o [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] a objektově orientované programování, a také koncepci jak vztahy mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky můžete conceptualized jako strom. Chcete-li v následujících příkladech v tomto tématu byste měli také porozumět [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a vědět, jak napsat velmi základní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nebo stránky. Další informace najdete v tématu [návod: Můj první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md) a [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="routing"></a>   
## <a name="what-is-a-routed-event"></a>Co je směrované události?  
 Si můžete představit o směrované události buď z hlediska funkčnosti nebo implementace. Obě definice budou zobrazeny zde, protože někteří uživatelé přehlednější, jednu nebo jiné definici.  
  
 Funkční definice: směrované události je typu události, který lze vyvolat obslužné rutiny na více naslouchací procesy ve stromu k elementu, nikoli jen na objekt, který vyvolá událost.  
  
 Definice implementace: je směrované události [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události, kterou je zajištěna instanci <xref:System.Windows.RoutedEvent> třídy a jejich zpracování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] událostí systému.  
  
 Typické [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace obsahuje mnoho prvků. Ať už vytvořené v kódu nebo deklarované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], tyto prvky existovat v relaci element stromu navzájem. Událost trasy, která mohou projít v jednom ze dvou směrů v závislosti na definici událostí, ale obecně trasy, která přenáší z source element a potom "bubliny" nahoru prostřednictvím stromu element dokud nedosáhne kořenu stromu elementu (obvykle na stránce nebo okno). Tento koncept probublávání může být snadno dokážete, pokud jste už pracovali s modelem objektu DHTML dříve.  
  
 Vezměte v úvahu následující stromu jednoduché element:  
  
 [!code-xaml[EventOvwSupport#GroupButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 Tento element stromu vytváří přibližně takto:  
  
 ![Ano, ne a stornovací tlačítka](../../../../docs/framework/wpf/advanced/media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")  
  
 V tomto zjednodušené element stromu, zdroj <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí je jedním z <xref:System.Windows.Controls.Button> prvky a podle toho, co <xref:System.Windows.Controls.Button> označeného je první prvek, který má možnost zpracování události. Ale pokud žádná obslužná rutina připojena k <xref:System.Windows.Controls.Button> funguje na události, pak událost je předána směrem nahoru k <xref:System.Windows.Controls.Button> nadřazené ve stromové struktuře element, který je <xref:System.Windows.Controls.StackPanel>. Případně bublinách událostí k <xref:System.Windows.Controls.Border>a pak kromě stránky kořen stromu element (není vidět).  
  
 Jinými slovy, události trasy pro tuto <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost:  
  
 Tlačítko--> StackPanel--> ohraničení-->...  
  
### <a name="top-level-scenarios-for-routed-events"></a>Nejvyšší úrovně scénáře pro směrované události  
 Následuje stručné souhrnné informace o scénářích opodstatněny koncept směrované události, a proto typické [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událost nebyla pro tyto scénáře:  
  
 **Řízení složení a zapouzdření:** různých ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mít bohaté modelu obsahu. Například můžete umístit obrázek uvnitř <xref:System.Windows.Controls.Button>, které efektivně rozšiřuje vizuálním stromu tlačítka. Přidání bitové kopie nesmí však přerušit testování podle chování, které způsobí, že tlačítko reagovat na <xref:System.Windows.Controls.Primitives.ButtonBase.Click> část jeho obsahu, i když uživatel klikne na pixelů, které jsou technicky součástí bitové kopie.  
  
 **Body přílohy singulární obslužná rutina:** v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], budete muset připojit obslužná rutina stejné vícekrát ke zpracování událostí, které mohou být vyvolány z více elementů. Směrované události vám umožní připojit tuto obslužnou rutinu jenom jednou, jako byl v předchozím příkladu a pomocí obslužná rutina logiky můžete určit, odkud událost pochází v případě potřeby. Například to může být obslužnou rutinu pro dříve uvedené [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-csharp[EventOvwSupport#GroupButtonCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
 [!code-vb[EventOvwSupport#GroupButtonCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]  
  
 **Třída zpracování:** směrován události povolit statický obslužná rutina, která je definována v třídě. Tato obslužná rutina třída má možnost zpracovat události předtím, než můžete všechny připojené instance obslužné rutiny.  
  
 **Odkazování na událost bez reflexe:** některé techniky kód a značky vyžadují způsob, jak identifikovat konkrétní události. Vytvoří směrované události <xref:System.Windows.RoutedEvent> pole jako identifikátor, který poskytuje postup identifikace robustní událostí, který nevyžaduje statickou nebo spuštění reflexe.  
  
### <a name="how-routed-events-are-implemented"></a>Jak jsou implementované směrované události  
 Je směrované události [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události, kterou je zajištěna instanci <xref:System.Windows.RoutedEvent> třídy a zaregistrovaného na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostí systému. <xref:System.Windows.RoutedEvent> Instance získané z registrace se obvykle uchovávají jako `public` `static` `readonly` pole členem třídy, která registruje a proto "vlastní" směrované události. Připojení k stejně jako s názvem [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událost (která se někdy říká "obálky" událostí) je dosáhnout přepsáním `add` a `remove` implementace pro [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událostí. Obvykle `add` a `remove` jsou ponechané jako implicitní výchozím nastavení, které používá syntaxi příslušné události specifické pro jazyk pro přidávání a odebírání obslužné rutiny této události. Směrované události připojení a základní mechanismus se koncepčně podobá jak vlastnost závislosti je [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnosti, které je založeno <xref:System.Windows.DependencyProperty> třídy a zaregistrovaného na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému.  
  
 Následující příklad ukazuje deklaraci pro vlastní `Tap` směrované události, včetně registrace a úniku <xref:System.Windows.RoutedEvent> identifikátor pole a `add` a `remove` implementace pro `Tap` [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událostí.  
  
 [!code-csharp[RoutedEventCustom#AddRemoveHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
 [!code-vb[RoutedEventCustom#AddRemoveHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]  
  
### <a name="routed-event-handlers-and-xaml"></a>Obslužné rutiny směrované události a XAML  
 K přidání obslužné rutiny k události pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], na element, který je naslouchací proces událost deklarovat název události jako atribut. Hodnota atributu je název metody implementované obslužné rutiny, které musí existovat v třídu souboru kódu na pozadí.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Syntaxe pro přidání standardní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obslužné rutiny událostí je stejný pro přidání obslužné rutiny směrované události, protože skutečně přidáváte obslužné rutiny na [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obálku událostí, který má implementace směrované události pod. Další informace o přidání obslužné rutiny událostí v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], najdete v části [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="routing_strategies"></a>   
## <a name="routing-strategies"></a>Strategie směrování  
 Směrovány události, použijte jednu z tři strategie směrování:  
  
-   **Šíření:** jsou vyvolány obslužné rutiny událostí ve zdroji událostí. Směrované události a směrování, aby následných nadřazené elementy, dokud nebude dosaženo kořen stromu elementu. Většina směrované události pomocí probublávání strategie směrování. Probublávání směrované události se obecně používají k hlášení vstupní nebo stavu změn z různých ovládací prvky nebo další prvky uživatelského rozhraní.  
  
-   **Přímé:** zdroj elementu samotného je zadána jen možnost vyvolání obslužné rutiny v odpovědi. Toto je obdobou "směrování", [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] používá pro události. Ale na rozdíl od standardní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událostí, přímé směrované události podporují zpracování třídy (třídy zpracování je vysvětleno v následující části) a mohou být využívána <xref:System.Windows.EventSetter> a <xref:System.Windows.EventTrigger>.  
  
-   **Tunelové propojení:** na začátku jsou vyvolány obslužné rutiny událostí v kořenu stromu elementu. Směrované události přenáší pak směrovat přes následných podřízených elementů na trase směrem uzel elementu, který je zdrojem směrované události (elementu, který vyvolá směrované události). Tunelové směrované události jsou často používá nebo zpracovávány jako součást skládání ovládacího prvku, tak, že události z části složené můžete úmyslně Potlačené nebo nahrazena události, které jsou specifické pro úplnou kontrolu. Vstupní události, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] často pocházet implementovaná jako dvojice tunelování šíření. Tunelové události jsou také někdy označovány jako události náhledu, z důvodu zásady vytváření názvů, který se používá pro dvojice.  
  
<a name="why_use"></a>   
## <a name="why-use-routed-events"></a>Proč použití směrované události?  
 Jako vývojář aplikací není vždy nutné vědět, nebo vás, že události, které jsou zpracování je implementovaný jako směrované události. Směrované události chovají specifickým, ale toto chování je z velké části neviditelná, pokud jsou zpracování události v elementu kde je vyvolána.  
  
 Kde stát výkonné směrované události je, pokud použijete kterýkoli z navrhovaných scénářů: definování běžné obslužné rutiny na společný kořen skládání vlastní ovládací prvek nebo definování třídě vlastního ovládacího prvku.  
  
 Moduly pro naslouchání směrované události a směrované události zdrojů není potřeba sdílet běžné události ve své hierarchii. Všechny <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> může být modul pro naslouchání událostí pro všechny směrované události. Proto můžete použít úplnou sadu směrované události, které jsou k dispozici v rámci pracovní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] nastavit jako koncepční "rozhraní" které různorodých prvky v aplikaci může výměnu informací o události. Tento koncept "rozhraní" směrované události je zvláště použitelné pro vstupní události.  
  
 Směrované události lze také komunikovat prostřednictvím stromu elementu vzhledem k tomu, že je pro každý prvek v postupu perpetuated data události pro událost. Jeden element v datech události něco změnit, a tato změna by být k dispozici na další prvek v postupu.  
  
 Než směrování aspekt existují dva další důvody této všechny zadané [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostí se může implementovat jako směrované události, namísto standardního [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] událostí. Pokud implementujete vlastní události, můžete také zvážit tyto zásady:  
  
-   Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stylů a ukázka funkce, jako <xref:System.Windows.EventSetter> a <xref:System.Windows.EventTrigger> vyžadují odkazované událost, která má být směrované události. Toto je scénář identifikátor událost, již bylo zmíněno dříve.  
  
-   Směrované události podporovat třídu mechanismu, které třídy můžete zadat statické metody, které mají možnost zpracování směrované událostí, než k nim měli přístup všechny registrované instance obslužné rutiny pro zpracování. Totiž velmi užitečná při návrhu řízení třídě můžete vynutit chování událostmi řízené třídy, které nelze potlačit omylem pomocí zpracování události v instanci.  
  
 Všechny aspekty výše popsané v samostatné části tohoto tématu.  
  
<a name="event_handing"></a>   
## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Přidání a implementace obslužné rutiny události pro směrované události  
 Přidání obslužné rutiny události v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jednoduše přidat název události k prvku jako atribut a nastavte hodnotu atributu jako název obslužné rutiny události, který implementuje odpovídající delegáta, jako v následujícím příkladu.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 `b1SetColor` je název implementovaná obslužná rutina, která obsahuje kód, který zpracovává <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí. `b1SetColor` musí mít stejný podpis jako <xref:System.Windows.RoutedEventHandler> delegáta, který je delegát obslužné rutiny události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí. První parametr všechny delegátů obslužných rutin směrované události určuje element, ke které je obslužná rutina přidána, a druhý parametr určuje data pro událost.  
  
[!code-csharp[EventOvwSupport#SimpleHandlerA](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]  
  
 <xref:System.Windows.RoutedEventHandler> je obslužná rutina delegát základní směrované události. Pro směrované události, které jsou specializované pro některé ovládací prvky nebo scénářů delegáty pro obslužné rutiny směrované události také může požadavky, aby odesílají data specializované události. Například v případě běžných vstupní může zpracovat <xref:System.Windows.UIElement.DragEnter> směrované události. Musí implementovat vaší obslužné rutiny <xref:System.Windows.DragEventHandler> delegovat. Pomocí nejvíce delegáta může zpracovat <xref:System.Windows.DragEventArgs> v obslužné rutiny a čtení <xref:System.Windows.DragEventArgs.Data%2A> vlastnosti, která obsahuje datové části schránky operace přetažení.  
  
 Kompletní příklad, jak přidat obslužné rutiny události pro element pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], najdete v části [zpracování události směrovány](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).  
  
 Přidání obslužné rutiny pro směrované události v aplikaci, která se vytvoří v kódu je jednoduchá. Obslužné rutiny směrované události můžete kdykoli přidat prostřednictvím Pomocná metoda <xref:System.Windows.UIElement.AddHandler%2A> (což je stejnou existující základní volání pro metodu `add`.) Však existující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] směrované události mají obvykle zálohování implementace `add` a `remove` logiky, která umožňují obslužné rutiny pro směrované události přidávaného syntaxí události pro specifický jazyk, který je intuitivnější syntaxe než Pomocná metoda. Toto je příklad použití metody pomocné rutiny:  
  
 [!code-csharp[EventOvwSupport#AddHandlerCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
 [!code-vb[EventOvwSupport#AddHandlerCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]  
  
 Další příklad ukazuje jazyka C# – operátor syntaxe (Visual Basic má mírně odlišné operátor syntaxi z důvodu jeho zpracování vyhodnocení):  
  
 [!code-csharp[EventOvwSupport#AddHandlerPlusEquals](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
 [!code-vb[EventOvwSupport#AddHandlerPlusEquals](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]  
  
 Příklad postup přidání obslužné rutiny událostí v kódu, naleznete v části [přidat kód obslužné rutiny události pomocí](../../../../docs/framework/wpf/advanced/how-to-add-an-event-handler-using-code.md).  
  
 Pokud používáte Visual Basic, můžete také použít `Handles` – klíčové slovo přidání obslužné rutiny jako součást deklarace obslužných rutin. Další informace najdete v tématu [Visual Basic a zpracování události WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
<a name="concept_handled"></a>   
### <a name="the-concept-of-handled"></a>Zpracovává konceptu  
 Všechny směrované události sdílet běžné události dat základní třídu, <xref:System.Windows.RoutedEventArgs>. <xref:System.Windows.RoutedEventArgs> definuje <xref:System.Windows.RoutedEventArgs.Handled%2A> vlastnosti, která nabývá logických hodnot. Účelem <xref:System.Windows.RoutedEventArgs.Handled%2A> vlastnost je umožnit žádné obslužné rutiny události na trase označit směrované události jako *zpracovává*, nastavením hodnotu <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true`. Po zpracovávaných obslužnou rutinu na jeden element společně trasy, data události sdílené údajně opakujte pro každý naslouchací proces na trase.  
  
 Hodnota <xref:System.Windows.RoutedEventArgs.Handled%2A> má vliv jak směrované události je hlášené nebo zpracovány při přenosu další na trase. Pokud <xref:System.Windows.RoutedEventArgs.Handled%2A> je `true` události data pro směrované události a pak obslužných rutin, které naslouchat této směrované události na další elementy jsou obecně už vyvolány u dané instance určitá událost. To platí, i pro obslužné rutiny připojena v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a pro obslužné rutiny přidali pomocí syntaxe přílohy obslužné rutiny události pro specifický jazyk, jako `+=` nebo `Handles`. U většiny běžných scénářů s obslužná rutina označíte událost jako ošetřena nastavením <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true` "zastaví" směrování pro trasu tunelu nebo probublávání trasy a také každé události, kterou provádí na místo v trasy třídy obslužnou rutinou.  
  
 Existuje však mechanismus "handledEventsToo", při němž naslouchací procesy dají spustit i přesto obslužné rutiny v reakci na směrované události kde <xref:System.Windows.RoutedEventArgs.Handled%2A> je `true` v datech události. Jinými slovy trasy událostí není skutečně zastavena označením dat události jako zpracování. Můžete použít pouze mechanismus handledEventsToo do kódu nebo <xref:System.Windows.EventSetter>:  
  
-   V kódu, místo použití syntaxe události pro specifický jazyk, který funguje pro obecné [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události, zavolejte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metoda <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> přidat vaší obslužné rutiny. Zadejte hodnotu `handledEventsToo` jako `true`.  
  
-   V <xref:System.Windows.EventSetter>, nastavte <xref:System.Windows.EventSetter.HandledEventsToo%2A> atributu na `true`.  
  
 Kromě chování, <xref:System.Windows.RoutedEventArgs.Handled%2A> stavu vytváří v směrované události, koncept <xref:System.Windows.RoutedEventArgs.Handled%2A> má důsledky, jak by měla návrhu aplikace a napsat kód obslužné rutiny událostí. Můžete conceptualize <xref:System.Windows.RoutedEventArgs.Handled%2A> jako jednoduchý protokol, který je zveřejněný prostřednictvím směrované události. Až můžete, ale koncepční návrh, jak přesně v tom, jak používáte tento protokol je hodnota <xref:System.Windows.RoutedEventArgs.Handled%2A> je určena pro použití vypadá takto:  
  
-   Pokud směrované události je označen jako zpracování, pak nemusí znovu zpracovávat další prvky této trase.  
  
-   Pokud směrované události není označena jako zpracovává, pak buď nechcete zaregistrovat obslužnou rutinu nebo obslužných rutin, které byly registrované pokusit nechcete pracovat s daty událostí a nastavte další naslouchací procesy, které byly dříve na trase rozhodli <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true`. (Nebo, samozřejmě je možné, že aktuální naslouchací proces prvního bodu v postupu). Obslužné rutiny na aktuální naslouchací proces Teď máte tři možné kurzy akce:  
  
    -   Provádět žádnou akci vůbec; událost zůstává neošetřená a události směruje na další naslouchací proces.  
  
    -   Spouštění kódu v reakci na událost, ale rozhodnout, že akci prováděnou nebyl dostatečně velké na to, pro vlastní označování událostí jako zpracování. Událost trasy pro další naslouchací proces.  
  
    -   Spouštění kódu v reakci na událost. Označte jako zpracování události data předaná obslužná rutina, protože akci prováděnou se považují za dostatečně velké na to, pro vlastní označení jako zpracování události. Událost stále tras pro další naslouchací proces, ale s <xref:System.Windows.RoutedEventArgs.Handled%2A> = `true` v jeho data událostí, takže jenom `handledEventsToo` naslouchací procesy mít příležitost vyvolat další obslužné rutiny.  
  
 Tento návrh koncepční je zesílené podle chování směrování, již bylo zmíněno dříve: je obtížnější (Ačkoli je to stále možné v kódu nebo styly) pro připojení obslužné rutiny pro směrované události, které jsou vyvolány i v případě, že předchozí obslužné rutiny na trase již nastaven <xref:System.Windows.RoutedEventArgs.Handled%2A>k `true`.  
  
 Další informace o <xref:System.Windows.RoutedEventArgs.Handled%2A>, třída zpracování směrované události a doporučení o tom, kdy je vhodné k označení směrované události jako <xref:System.Windows.RoutedEventArgs.Handled%2A>, najdete v části [označení směrované události jako Handled a třída zpracování](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 V aplikacích je celkem běžné právě zpracovávají probublávání směrované události na objektu, která je vyvolána a dělat starosti s vlastnostmi události směrování vůbec. Je však stále dobrým zvykem označit směrované události, jako v případě, že data, aby se zabránilo neočekávané vedlejší účinky jen v případě, že element, který je další nahoru k element má také pro tento stejný směrované události obslužná rutina zpracovává.  
  
<a name="class_handlers"></a>   
## <a name="class-handlers"></a>Obslužné rutiny – třída  
 Pokud definujete třídu odvozenou nějakým způsobem z <xref:System.Windows.DependencyObject>, můžete také definovat a připojte třída obslužnou rutinu pro směrované události, který je členem události deklarované nebo zděděná vaší třídy. Obslužné rutiny třídy jsou vyvolány před naslouchací proces obslužné rutiny všechny instance, které jsou připojeny k instanci této třídy, vždy, když směrované události dosáhne element instance v jeho trasu.  
  
 Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků mají vyplývajících třídu zpracování pro určité směrované události. To může poskytnout pasivního vzhled směrované události někdy není vyvolána, ale ve skutečnosti se třída zpracovává a směrované události mohou být stále potenciálně ošetřeny vaší instance obslužné rutiny, pokud použijete některé techniky. Virtuální metody, které lze použít k přepsání třída chování zpracování vystavit také mnoho základní třídy a ovládací prvky. Další informace jak o tom, jak obejít nežádoucí třída zpracování a k definování vlastní třídu zpracování v rámci vlastní třídy najdete v tématu [označení směrované události jako Handled a třída zpracování](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="attached_events"></a>   
## <a name="attached-events-in-wpf"></a>Přidružené události v grafickém subsystému WPF  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Jazyk také definuje speciální typ události volána *přidružená událost*. – Přidružená událost umožňuje přidat obslužnou rutinu události pro libovolný element. Element zpracování události není nutné definovat nebo nastavte dědičnost přidružená událost a ani objekt potenciálně vyvolá událost ani zpracování cílové instance musí definovat nebo jinak "vlastní" tuto událost jako člena třídy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vstupní systém hojně používá přidružené události. Však téměř všechny tyto přidružené události jsou předávány prostřednictvím základní elementy. Vstupních událostech se potom zobrazí jako ekvivalentní nepřipojené směrováním události, které jsou členy třídy base element. Například základní přidružená událost <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> může více snadno zpracovat všechny zadané <xref:System.Windows.UIElement> pomocí <xref:System.Windows.UIElement.MouseDown> na který <xref:System.Windows.UIElement> místo týkajících se syntaxí přidružená událost buď v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kódu.  
  
 Další informace o přidružené události v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v části [připojen přehled událostí](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>   
## <a name="qualified-event-names-in-xaml"></a>Názvy kvalifikovaný událostí v jazyce XAML  
 Další využití syntaxe, který vypadá takto: *typename*. *EventName* připojené syntaxe událostí, ale není přesněji řečeno využití připojené události je při připojení obslužné rutiny pro směrované události, které jsou vydané podřízené elementy. Obslužné rutiny se připojit k společným nadřazeným prvkem, využívat výhod směrování události, i když společným nadřazeným prvkem nemusí mít relevantní směrované události jako člena. Tento příklad zvažte znovu:  
  
 [!code-xaml[EventOvwSupport#GroupButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 Zde je naslouchací proces element nadřazené, kde se přidá obslužná rutina <xref:System.Windows.Controls.StackPanel>. Ale ho je přidání obslužné rutiny pro směrované události, která byla deklarována a bude aktivováno <xref:System.Windows.Controls.Button> – třída (<xref:System.Windows.Controls.Primitives.ButtonBase> ve skutečnosti, ale k dispozici pro <xref:System.Windows.Controls.Button> prostřednictvím dědičnosti). <xref:System.Windows.Controls.Button> "vlastní" události, ale systém směrované události povolí obslužné rutiny pro směrované události, které chcete připojit k žádné <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> instance naslouchací proces, který by jinak naslouchací procesy pro připojení [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] událostí. Výchozí obor názvů xmlns pro tyto názvy atributů kvalifikovaný událostí je obvykle výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] názvu oborů xmlns, ale můžete také zadat předponou obory názvů pro vlastní směrované události. Další informace o xmlns najdete v tématu [obory názvů jazyka XAML a Namespace mapování pro jazyk XAML WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="how_event_processing_works"></a>   
## <a name="wpf-input-events"></a>Vstupní události WPF  
 Časté provádění směrované události v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je platforma pro vstupní události. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tunelové propojení směrované události jsou názvy podle konvence předponou slovo "Náhled". Vstupní události často pocházet v párech, a s jedním se probublávání události a druhá je tunelové událostí. Například <xref:System.Windows.ContentElement.KeyDown> událostí a <xref:System.Windows.ContentElement.PreviewKeyDown> událost mít s dřívějším probublávání vstupní událost se stejným podpisem, a na kterou tunelové propojení vstupní události. V některých případech vstupních událostech mít pouze probublávání verze nebo možná jenom přímé směrované verze. Dokumentace směrované události témata křížovou podobné směrované události s další směrování strategie, pokud existují tyto směrované události a části na stránkách spravovaný odkaz vysvětlení směrování strategie každý směrované události.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vstupní události, které jsou v párech se implementují, aby akce jednoho uživatele ze vstupu, například stisknutí tlačítka myši, vyvolal obou směrované události, které odpovídá páru v pořadí. Nejprve tunelu událost se vyvolá a přenáší jeho trasu. Potom probublávání událost se vyvolá a přenáší jeho trasu. Dvě události oznámena sdílet stejné instance dat události, protože <xref:System.Windows.UIElement.RaiseEvent%2A> volání metody v implementující třídu, která vyvolává událost probublávání naslouchá data události z události tunelového propojení a opětovně ji používá v nové události vyvolané. Naslouchací procesy s obslužné rutiny pro tunelové událost mít první možnost označte směrované události zpracovává (třídu obslužné rutiny nejprve, pak instance obslužné rutiny). Pokud element společně tunelového propojení směrování označena směrované události jako zpracování, data již zpracovává události se odesílají na probublávání události a uplatněny typické obslužné rutiny pro ekvivalentní šíření vstupních událostech. Pro vzdálené vzhledy bude, jako kdyby nebyl zpracovávaný probublávání událost i vyvolá. Toto chování zpracování je užitečné pro ovládací prvek skládání, může místo všech vstupů do testu na základě vstupních událostech nebo na základě fokus vstupní událostí, které ohlášeny vaší poslední ovládací prvek, nikoli jeho složené částí. Poslední ovládacího prvku je blíž ke kořenu v skládání a tedy možnost Třída zpracovat událost tunelu nejprve a případně "nahradit" Tento směrované události ovládacího prvku konkrétní události, jako součást kód, který zálohuje ovládacího prvku Třída.  
  
 Jako obrázek, jak vstupní události zpracování funguje podívejte se na následující příklad vstupní událost. Na následujícím obrázku stromu `leaf element #2` je zdrojem i `PreviewMouseDown` a potom `MouseDown` událostí.  
  
 ![Diagram směrování událostí](../../../../docs/framework/wpf/advanced/media/wcsdkcoreinputevents.png "wcsdkCoreInputEvents")  
Vstupní událost šíření a tunelové propojení  
  
 Pořadí zpracování události je následující:  
  
1.  `PreviewMouseDown` (tunelu) na kořenový element.  
  
2.  `PreviewMouseDown` (tunelu) na zprostředkující prvek #1.  
  
3.  `PreviewMouseDown` (tunelu) na element source #. 2.  
  
4.  `MouseDown` (bublinový) na element source #. 2.  
  
5.  `MouseDown` (bublinový) na zprostředkující prvek #1.  
  
6.  `MouseDown` (bublinový) na kořenový element.  
  
 Obslužná rutina delegáta směrované události odkazuje na dva objekty: objekt, který vyvolá událost a objekt, kde byla vyvolána obslužná rutina. Objekt, kde byla vyvolána obslužná rutina je objekt hlášené `sender` parametr. Objekt, kde byla nejprve vyvolána událost je hlášen <xref:System.Windows.RoutedEventArgs.Source%2A> vlastnost v datech události. Směrované události stále můžete vyvolá a v takovém případě provádí stejný objekt `sender` a <xref:System.Windows.RoutedEventArgs.Source%2A> jsou identické (což je případ s kroky 3 a 4 události zpracování seznam příkladů).  
  
 Z důvodu tunelové propojení a šíření, nadřazené elementy přijímat vstupní události kde <xref:System.Windows.RoutedEventArgs.Source%2A> je jedním z jejich podřízené elementy. Pokud je důležité vědět, co je source element, můžete identifikovat source element díky přístupu k <xref:System.Windows.RoutedEventArgs.Source%2A> vlastnost.  
  
 Obvykle když je označen vstupní událost <xref:System.Windows.RoutedEventArgs.Handled%2A>, další nejsou vyvolat obslužné rutiny. Obvykle byste měli označit vstupních událostech jako zpracování co nejrychleji obslužná rutina je volána, která řeší vaše logické zpracování význam vstupní události specifické pro aplikaci.  
  
 Výjimka, která má toto obecných údajů o <xref:System.Windows.RoutedEventArgs.Handled%2A> stavu je, zadejte obslužné rutiny událostí, které jsou registrovány úmyslně Ignorovat <xref:System.Windows.RoutedEventArgs.Handled%2A> stav data události by stále vyvolat buď trase. Další informace najdete v tématu [události náhledu](../../../../docs/framework/wpf/advanced/preview-events.md) nebo [označení směrované události jako Handled a třída zpracování](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 Datový model sdílené událostí mezi tunelového propojení a probublávání události a sekvenční vyvolání první tunelového propojení potom šíření události, není konceptu, které obvykle platí pro všechny směrované události. Konkrétně je chování implementované jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vstupní zařízení rozhodnete vyvolávání a připojit páry vstupní událost. Implementace vstupní události je pokročilý scénář, ale můžete zvolit také postupujte podle tohoto modelu pro vstupní události.  
  
 Určité třídy zvolit třídu popisovač určité vstupní události, obvykle se záměrem opětovná definice určitá událost vstupu uživatele řízené znamená v rámci tohoto ovládacího prvku a vyvolání novou událost. Další informace najdete v tématu [označení směrované události jako Handled a třída zpracování](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 Další informace o vstup a způsob interakce vstup a události v typických aplikačních scénářů, najdete v části [vstupní přehled](../../../../docs/framework/wpf/advanced/input-overview.md).  
  
<a name="events_styles"></a>   
## <a name="eventsetters-and-eventtriggers"></a>EventSetters a EventTriggers  
 Styly, může obsahovat některé předem deklarovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zpracování syntaxe do kódu pomocí událostí <xref:System.Windows.EventSetter>. Při použití styl odkazované obslužná rutina se přidá do stylem instance. Je možné deklarovat <xref:System.Windows.EventSetter> pouze pro směrované události. Následuje příklad. Všimněte si, že `b1SetColor` metoda zde odkazuje je v souboru kódu na pozadí.  
  
 [!code-xaml[EventOvwSupport#XAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]  
  
 Výhoda získávají tady je, že styl není mohou obsahovat značnou část Další informace, které může použít pro žádné tlačítko v aplikaci, které mají <xref:System.Windows.EventSetter> být součástí této styl zvýší úroveň opakované použití kódu i na úrovni značek. Navíc <xref:System.Windows.EventSetter> abstrahuje metoda názvy pro obslužné rutiny jediný krok další obecné kód aplikace a stránky.  
  
 Jiné specializované syntaxi, která kombinuje směrované události a animace funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je <xref:System.Windows.EventTrigger>. Stejně jako u <xref:System.Windows.EventSetter>, mohou být použity pouze směrované události pro <xref:System.Windows.EventTrigger>. Obvykle <xref:System.Windows.EventTrigger> je deklarován jako součást stylu, ale <xref:System.Windows.EventTrigger> lze také deklarovat u elementů na úrovni stránky v rámci <xref:System.Windows.FrameworkElement.Triggers%2A> kolekce, nebo v <xref:System.Windows.Controls.ControlTemplate>. <xref:System.Windows.EventTrigger> Umožňuje určit <xref:System.Windows.Media.Animation.Storyboard> , spustí vždy, když směrované události dosáhne prvku v jeho trasu, který deklaruje <xref:System.Windows.EventTrigger> pro tuto událost. Výhodou <xref:System.Windows.EventTrigger> přes právě zpracování události a způsobuje tak, aby existující scénáře je, že <xref:System.Windows.EventTrigger> poskytuje lepší kontrolu nad scénáři a její chování. Další informace najdete v tématu [aktivační události použít k řízení scénáře po jeho spuštění](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
<a name="more_about"></a>   
## <a name="more-about-routed-events"></a>Další informace o směrované události  
 Toto téma popisuje především směrované události z perspektivy popisující se základními koncepty a nabízí pokyny o tom, a reagovat na směrované události, které jsou již k dispozici v různých základní elementy a ovládací prvky. Můžete však vytvořit vlastní směrované události na vaší třídě společně s všechny nezbytné podpory, jako jsou třídy dat specializované události a delegáti. Vlastník směrované události může být jakákoli třída, ale směrované události musí být aktivováno a zpracovává <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> odvozené třídy, aby byla užitečná. Další informace o vlastních událostí najdete v tématu [vytvořit vlastní směrované události](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.EventManager>  
 <xref:System.Windows.RoutedEvent>  
 <xref:System.Windows.RoutedEventArgs>  
 [Označení směrovaných událostí jako zpracovaných a zpracování tříd](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Přehled příkazů](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Stromy v subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [Slabé vzory událostí](../../../../docs/framework/wpf/advanced/weak-event-patterns.md)
