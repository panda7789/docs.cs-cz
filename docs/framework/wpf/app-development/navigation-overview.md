---
title: Přehled navigace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loose XAML files [WPF]
- windows [WPF]
- Start page [WPF]
- HTML files [WPF]
- structured navigation [WPF]
- fragment navigation [WPF]
- URIs (Uniform Resource Identifiers)
- custom objects [WPF]
- Uniform Resource Identifiers (URIs)
- pages [WPF]
- frames [WPF]
- navigation hosts [WPF]
- journals [WPF]
- lifetimes [WPF]
- retaining content state [WPF]
- content state [WPF]
- programmatic navigation [WPF]
- hyperlinks [WPF]
ms.assetid: 86ad2143-606a-4e34-bf7e-51a2594248b8
ms.openlocfilehash: 8afda2a314bd04e91c6686fb254a1bd9e773913d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636286"
---
# <a name="navigation-overview"></a>Přehled navigace

Windows Presentation Foundation (WPF) podporuje navigaci ve stylu prohlížeče, které lze použít ve dvou typech aplikací: samostatné aplikace a aplikace prohlížeče XAML (XBAP). Pro zabalení obsahu pro navigaci WPF poskytuje třídu <xref:System.Windows.Controls.Page>. Můžete přecházet z jednoho <xref:System.Windows.Controls.Page> na další deklarativně, pomocí <xref:System.Windows.Documents.Hyperlink>nebo programově pomocí <xref:System.Windows.Navigation.NavigationService>. WPF používá deník k zapamatování stránek, které byly přecházení z a na přechod na ně.

<xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>a Journal tvoří základní podporu pro navigaci nabízenou WPF. Tento přehled podrobněji prozkoumá tyto funkce před tím, než pokrývá rozšířenou podporu navigace, která zahrnuje navigaci na volné [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubory, soubory HTML a objekty.

> [!NOTE]
> V tomto tématu pojem "prohlížeč" odkazuje pouze na prohlížeče, které mohou hostovat aplikace WPF, které aktuálně obsahují aplikace Microsoft Internet Explorer a Firefox. V případě, že konkrétní funkce WPF jsou podporovány pouze konkrétním prohlížečem, je na verzi prohlížeče odkazováno.

## <a name="navigation-in-wpf-applications"></a>Navigace v aplikacích WPF

Toto téma poskytuje přehled klíčových navigačních funkcí v subsystému WPF. Tyto možnosti jsou k dispozici pro samostatné aplikace i pro XBAP, i když toto téma prezentuje v kontextu aplikace XBAP.

> [!NOTE]
> V tomto tématu se nezabývá sestavování a nasazování aplikací XBAP. Další informace o aplikaci XBAP naleznete v tématu [Přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).

Tato část vysvětluje a ukazuje následující aspekty navigace:

- [Implementace stránky](#CreatingAXAMLPage)

- [Konfigurace úvodní stránky](#Configuring_a_Start_Page)

- [Konfigurace názvu, šířky a výšky hostitelského okna](#ConfiguringAXAMLPage)

- [Navigace hypertextovými odkazy](#NavigatingBetweenXAMLPages)

- [Navigace v fragmentu](#FragmentNavigation)

- [Navigační služba](#NavigationService)

- [Programová navigace pomocí navigační služby](#Programmatic_Navigation_with_the_Navigation_Service)

- [Doba života navigace](#Navigation_Lifetime)

- [Zapamatování navigace pomocí deníku](#NavigationHistory)

- [Životnost stránky a deník](#PageLifetime)

- [Zachování stavu obsahu s historií navigace](#RetainingContentStateWithNavigationHistory)

- [Soubory cookie](#Cookies)

- [Strukturovaná navigace](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a>Implementace stránky

V jazyce WPF můžete přejít na několik typů obsahu, které zahrnují .NET Framework objekty, vlastní objekty, hodnoty výčtu, uživatelské ovládací prvky, soubory [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a soubory HTML. Ale zjistíte, že nejběžnější a pohodlný způsob balení obsahu je pomocí <xref:System.Windows.Controls.Page>. Kromě toho <xref:System.Windows.Controls.Page> implementuje funkce specifické pro navigaci, aby vylepšily jejich vzhled a zjednodušila vývoj.

Pomocí <xref:System.Windows.Controls.Page>lze deklarativně implementovat stránku naviguje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu pomocí značek jako následující.

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

<xref:System.Windows.Controls.Page>, která je implementována v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky, má `Page` jako svůj kořenový prvek a vyžaduje deklaraci oboru názvů WPF XML. Element `Page` obsahuje obsah, na který chcete přejít a zobrazit. Obsah můžete přidat nastavením prvku vlastnosti `Page.Content`, jak je znázorněno v následujícím kódu.

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content` může obsahovat pouze jeden podřízený element; v předchozím příkladu je obsahem jeden řetězec "Hello, Page!" V praxi obvykle použijete ovládací prvek rozložení jako podřízený element (viz [rozložení](../advanced/layout.md)), který bude obsahovat a vytvořit obsah.

Podřízené prvky `Page` prvku jsou považovány za obsah <xref:System.Windows.Controls.Page> a v důsledku toho nemusíte používat explicitní deklaraci `Page.Content`. Následující kód je deklarativní ekvivalent předchozí ukázky.

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

V tomto případě se `Page.Content` automaticky nastaví s podřízenými prvky elementu `Page`. Další informace najdete v tématu [model obsahu WPF](../controls/wpf-content-model.md).

<xref:System.Windows.Controls.Page> pouze s označením je užitečné pro zobrazení obsahu. <xref:System.Windows.Controls.Page> však může také zobrazit ovládací prvky, které umožňují uživatelům interakci se stránkou, a může reagovat na interakci s uživatelem, a to zpracováním událostí a voláním logiky aplikace. Interaktivní <xref:System.Windows.Controls.Page> jsou implementovány pomocí kombinace značek a kódu na pozadí, jak je znázorněno v následujícím příkladu.

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

Chcete-li, aby soubor značek a soubor s kódem na pozadí pracovaly společně, je vyžadována následující konfigurace:

- V kódu `Page` element musí zahrnovat atribut `x:Class`. Když je aplikace sestavena, existence `x:Class` v souboru označení způsobí, že nástroj Microsoft Build Engine (MSBuild) vytvoří třídu `partial`, která je odvozena z <xref:System.Windows.Controls.Page> a má název, který je určen atributem `x:Class`. To vyžaduje přidání deklarace oboru názvů XML pro schéma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`). Vygenerovaná `partial` třída implementuje `InitializeComponent`, která je volána k registraci událostí a nastavení vlastností, které jsou implementovány v označení.

- V kódu na pozadí třída musí být `partial` třídy se stejným názvem, který je určen atributem `x:Class` v kódu a musí odvozovat z <xref:System.Windows.Controls.Page>. To umožňuje, aby soubor s kódem na pozadí byl přidružen k třídě `partial`, která je generována pro soubor označení při sestavení aplikace (viz [Vytvoření aplikace WPF](building-a-wpf-application-wpf.md)).

- V kódu na pozadí třída <xref:System.Windows.Controls.Page> musí implementovat konstruktor, který volá metodu `InitializeComponent`. `InitializeComponent` je implementováno pomocí `partial` třídy vygenerované v souboru značek k registraci událostí a nastavování vlastností, které jsou definovány v kódu.

> [!NOTE]
> Když do projektu přidáte novou <xref:System.Windows.Controls.Page> pomocí sady Visual Studio, <xref:System.Windows.Controls.Page> je implementováno pomocí kódu a kódu na pozadí a obsahuje nezbytnou konfiguraci pro vytvoření přidružení mezi značkami a soubory kódu na pozadí, jak je popsáno zde.

Jakmile budete mít <xref:System.Windows.Controls.Page>, můžete na něj přejít. Chcete-li určit první <xref:System.Windows.Controls.Page>, na kterou aplikace přejde, je nutné nakonfigurovat počáteční <xref:System.Windows.Controls.Page>.

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>Konfigurace úvodní stránky

XBAP vyžadují, aby se v prohlížeči hostoval určitý objem aplikační infrastruktury. V WPF je třída <xref:System.Windows.Application> součástí definice aplikace, která vytváří požadovanou aplikační infrastrukturu (viz [Přehled správy aplikací](application-management-overview.md)).

Definice aplikace je obvykle implementována pomocí značek i kódu na pozadí se souborem označení, který je nakonfigurován jako`ApplicationDefinition` položka MSBuild. Následuje definice aplikace pro XBAP.

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

XBAP může použít definici své aplikace k určení počátečního <xref:System.Windows.Controls.Page>, což je <xref:System.Windows.Controls.Page>, který se automaticky načte při spuštění XBAP. Provedete to tak, že nastavíte vlastnost <xref:System.Windows.Application.StartupUri%2A> s identifikátorem URI (Uniform Resource Identifier) pro požadovanou <xref:System.Windows.Controls.Page>.

> [!NOTE]
> Ve většině případů je <xref:System.Windows.Controls.Page> buď kompilována, nebo nasazena s aplikací. V těchto případech identifikátor URI, který identifikuje <xref:System.Windows.Controls.Page>, je identifikátor URI balíčku, což je identifikátor URI, který odpovídá schématu *balíčku* . Identifikátory URI Pack jsou podrobněji popsány v tématu [identifikátory URI balíčku v](pack-uris-in-wpf.md)subsystému WPF. Můžete také přejít k obsahu pomocí schématu http, které je popsáno níže.

Můžete nastavit <xref:System.Windows.Application.StartupUri%2A> deklarativně v kódu, jak je znázorněno v následujícím příkladu.

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

V tomto příkladu je atribut `StartupUri` nastaven s identifikátorem URI relativního balíčku, který identifikuje stránku Web. XAML. Po spuštění aplikace XBAP je Domovská stránka. XAML automaticky přesměrována do a zobrazena. To je znázorněno na následujícím obrázku, který ukazuje XBAP spouštěné z webového serveru.

![Stránka XBAP](./media/navigation-overview/xbap-launched-from-a-web-server.png "Zobrazuje se XBAP spouštěná z webového serveru.")

> [!NOTE]
> Další informace týkající se vývoje a nasazení aplikace XBAP naleznete v tématu [Přehled aplikací WPF XAML browser](wpf-xaml-browser-applications-overview.md) a [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>Konfigurace názvu, šířky a výšky hostitelského okna

Jedna věc, kterou jste si poznamenali od předchozího obrázku, je, že název prohlížeče i panelu karet je identifikátor URI pro XBAP. Kromě toho není název ani atraktivní ani informativní. Z tohoto důvodu <xref:System.Windows.Controls.Page> nabízí způsob, jak změnit název nastavením vlastnosti <xref:System.Windows.Controls.Page.WindowTitle%2A>. Kromě toho můžete nakonfigurovat šířku a výšku okna prohlížeče nastavením <xref:System.Windows.Controls.Page.WindowWidth%2A> a <xref:System.Windows.Controls.Page.WindowHeight%2A>v uvedeném pořadí.

<xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>a <xref:System.Windows.Controls.Page.WindowHeight%2A> lze nastavit deklarativně v kódu, jak je znázorněno v následujícím příkladu.

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

Výsledek je znázorněn na následujícím obrázku.

![Název, Výška a šířka okna](./media/navigation-overview/window-title-width-height.png "Zobrazí se název okna, Výška a šířka, které můžete konfigurovat.")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>Navigace hypertextovými odkazy

Typický XBAP zahrnuje několik stránek. Nejjednodušší způsob, jak přejít z jedné stránky na druhou, je použít <xref:System.Windows.Documents.Hyperlink>. Můžete deklarativně přidat <xref:System.Windows.Documents.Hyperlink> do <xref:System.Windows.Controls.Page> pomocí elementu `Hyperlink`, který je zobrazen v následujícím kódu.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

Element `Hyperlink` vyžaduje následující:

- Identifikátor URI balíčku <xref:System.Windows.Controls.Page>, na který se má přejít, jak je určeno atributem `NavigateUri`

- Obsah, na který může uživatel kliknout pro zahájení navigace, jako je text a obrázky (pro obsah, který prvek `Hyperlink` může obsahovat, najdete v tématu <xref:System.Windows.Documents.Hyperlink>).

Následující obrázek ukazuje XBAP s <xref:System.Windows.Controls.Page>, která má <xref:System.Windows.Documents.Hyperlink>.

![Stránka s hypertextovým odkazem](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "To ukazuje XBAP se stránkou s hypertextovým odkazem.")

Jak byste to očekávali, kliknutím na <xref:System.Windows.Documents.Hyperlink> způsobí, že XBAP přejde na <xref:System.Windows.Controls.Page>, který je identifikovaný atributem `NavigateUri`. Kromě toho XBAP přidá položku pro předchozí <xref:System.Windows.Controls.Page> v seznamu poslední stránky v aplikaci Internet Explorer. To je znázorněno na následujícím obrázku.

![Tlačítka zpět a přeposílání](./media/navigation-overview/back-and-forward-navigation.png "Přejděte pomocí tlačítek zpět a vpřed.")

Stejně jako podpora navigace z jednoho <xref:System.Windows.Controls.Page> do druhé <xref:System.Windows.Documents.Hyperlink> podporuje také navigaci fragmentem.

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>Navigace v fragmentu

*Rozdělení fragmentu* je navigace k fragmentu obsahu v aktuálním <xref:System.Windows.Controls.Page> nebo jiném <xref:System.Windows.Controls.Page>. V WPF je fragmentem obsahu obsah obsažený v pojmenovaném elementu. Pojmenovaný element je element, který má nastaven atribut `Name`. Následující kód ukazuje pojmenovaný `TextBlock` element, který obsahuje fragment obsahu.

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

Aby <xref:System.Windows.Documents.Hyperlink> mohl přejít na fragment obsahu, musí atribut `NavigateUri` zahrnovat následující:

- Identifikátor URI <xref:System.Windows.Controls.Page> s fragmentem obsahu, na který se má přejít

- Znak "#".

- Název prvku na <xref:System.Windows.Controls.Page>, který obsahuje fragment obsahu.

Identifikátor URI fragmentu má následující formát.

*PageURI* `#` *ElementName*

V následujícím příkladu vidíte příklad `Hyperlink`, který je nakonfigurován tak, aby přešel na fragment obsahu.

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> Tato část popisuje výchozí implementaci navigace mezi fragmenty v subsystému WPF. WPF také umožňuje implementovat vlastní navigační schéma fragmentů, které v rámci součásti vyžaduje zpracování události <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType>.

> [!IMPORTANT]
> Můžete přejít na fragmenty na volných stránkách [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory s `Page` jako kořenový element) pouze v případě, že stránky lze procházet prostřednictvím protokolu HTTP.
>
> Nicméně volné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka může přejít na vlastní fragmenty.

<a name="NavigationService"></a>

### <a name="navigation-service"></a>Navigační služba

I když <xref:System.Windows.Documents.Hyperlink> umožňuje uživateli iniciovat navigaci na konkrétní <xref:System.Windows.Controls.Page>, práce s umístěním a stažením stránky provádí třída <xref:System.Windows.Navigation.NavigationService>. V podstatě <xref:System.Windows.Navigation.NavigationService> poskytuje možnost zpracování žádosti o navigaci jménem kódu klienta, jako je například <xref:System.Windows.Documents.Hyperlink>. Kromě toho <xref:System.Windows.Navigation.NavigationService> implementuje podporu vyšší úrovně pro sledování a vliv na navigační požadavek.

Když kliknete na <xref:System.Windows.Documents.Hyperlink>, WPF volá <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> k vyhledání a stažení <xref:System.Windows.Controls.Page> v zadaném identifikátoru URI packu. Stažený <xref:System.Windows.Controls.Page> je převedena na strom objektů, jejichž kořenový objekt je instancí stažené <xref:System.Windows.Controls.Page>. Odkaz na objekt root <xref:System.Windows.Controls.Page> je uložen ve vlastnosti <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType>. Identifikátor URI balíčku pro obsah, na který byl přesměrován, je uložen ve vlastnosti <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>, zatímco <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> ukládá identifikátor URI balíčku pro poslední stránku, na kterou byl přesměrován.

> [!NOTE]
> Je možné, že aplikace WPF má více než jednu aktuálně aktivní <xref:System.Windows.Navigation.NavigationService>. Další informace naleznete v části [hostitelé navigace](#Navigation_Hosts) dále v tomto tématu.

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>Programová navigace pomocí navigační služby

Nemusíte znát <xref:System.Windows.Navigation.NavigationService>, pokud se navigace implementuje deklarativně v kódu pomocí <xref:System.Windows.Documents.Hyperlink>, protože <xref:System.Windows.Documents.Hyperlink> používá <xref:System.Windows.Navigation.NavigationService> vaším jménem. To znamená, že pokud je přímý nebo nepřímý nadřazený objekt <xref:System.Windows.Documents.Hyperlink> navigační hostitel (viz téma [hostitelé navigace](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> bude moci vyhledat a použít navigační službu navigačního hostitele ke zpracování žádosti o navigaci.

Existují však situace, kdy je nutné použít <xref:System.Windows.Navigation.NavigationService> přímo, včetně následujících:

- Když potřebujete vytvořit instanci <xref:System.Windows.Controls.Page> pomocí konstruktoru bez parametrů.

- Když potřebujete nastavit vlastnosti <xref:System.Windows.Controls.Page> před přechodem na něj.

- Pokud <xref:System.Windows.Controls.Page>, na který je třeba přejít, lze určit pouze v době běhu.

V těchto situacích je nutné napsat kód pro programové iniciování navigace voláním metody <xref:System.Windows.Navigation.NavigationService.Navigate%2A> objektu <xref:System.Windows.Navigation.NavigationService>. Který vyžaduje získání odkazu na <xref:System.Windows.Navigation.NavigationService>.

#### <a name="getting-a-reference-to-the-navigationservice"></a>Získání odkazu na StopLoading

Z důvodů popsaných v části [Navigace hostitelé](#Navigation_Hosts) může aplikace WPF mít více než jeden <xref:System.Windows.Navigation.NavigationService>. To znamená, že váš kód potřebuje způsob, jak najít <xref:System.Windows.Navigation.NavigationService>, což je obvykle <xref:System.Windows.Navigation.NavigationService>, který přešel na aktuální <xref:System.Windows.Controls.Page>. Odkaz na <xref:System.Windows.Navigation.NavigationService> lze získat voláním metody <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> `static`. Chcete-li získat <xref:System.Windows.Navigation.NavigationService>, které přešly na konkrétní <xref:System.Windows.Controls.Page>, předáte odkaz na <xref:System.Windows.Controls.Page> jako argument metody <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A>. Následující kód ukazuje, jak získat <xref:System.Windows.Navigation.NavigationService> pro aktuální <xref:System.Windows.Controls.Page>.

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

Jako zástupce pro hledání <xref:System.Windows.Navigation.NavigationService> pro <xref:System.Windows.Controls.Page><xref:System.Windows.Controls.Page> implementuje vlastnost <xref:System.Windows.Controls.Page.NavigationService%2A>. To je ukázáno v následujícím příkladu.

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> <xref:System.Windows.Controls.Page> může získat odkaz na <xref:System.Windows.Navigation.NavigationService> pouze v případě, že <xref:System.Windows.Controls.Page> vyvolá událost <xref:System.Windows.FrameworkElement.Loaded>.

#### <a name="programmatic-navigation-to-a-page-object"></a>Programová navigace na objekt Page

Následující příklad ukazuje, jak použít <xref:System.Windows.Navigation.NavigationService> k programovému přechodu na <xref:System.Windows.Controls.Page>. Programová navigace je povinná, protože <xref:System.Windows.Controls.Page>, na kterou se přechází, se dá vytvořit jenom pomocí jednoho konstruktoru bez parametrů. <xref:System.Windows.Controls.Page> s konstruktorem bez parametrů je uveden v následujícím kódu a kódu.

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

<xref:System.Windows.Controls.Page>, který naviguje k <xref:System.Windows.Controls.Page> s konstruktorem bez parametrů, je uveden v následujícím kódu a kódu.

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

Při kliknutí na <xref:System.Windows.Documents.Hyperlink> na tomto <xref:System.Windows.Controls.Page> se spustí navigace vytvořením instance <xref:System.Windows.Controls.Page> k přechodu na použití neparametrového konstruktoru bez parametrů a volání metody <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> přijímá odkaz na objekt, na který <xref:System.Windows.Navigation.NavigationService> naviguje, místo identifikátoru URI balíčku.

#### <a name="programmatic-navigation-with-a-pack-uri"></a>Programová navigace pomocí identifikátoru URI balíčku

Pokud potřebujete identifikátor URI balíčku vytvořit programově (Pokud je možné pouze určit identifikátor URI balíčku za běhu, například), můžete použít metodu <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>. To je ukázáno v následujícím příkladu.

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>Aktualizace aktuální stránky

<xref:System.Windows.Controls.Page> se nestáhne, pokud má stejný identifikátor URI balíčku jako identifikátor URI balíčku, který je uložený ve vlastnosti <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>. Pro vynucení opětovného stažení aktuální stránky v WPF můžete zavolat metodu <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType>, jak je znázorněno v následujícím příkladu.

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>Doba života navigace

Existuje mnoho způsobů, jak spustit navigaci, jak jste viděli. Při zahájení navigace a v průběhu navigace můžete sledovat a ovlivňovat navigaci pomocí následujících událostí, které jsou implementovány <xref:System.Windows.Navigation.NavigationService>:

- <xref:System.Windows.Navigation.NavigationService.Navigating>. Vyvolá se v případě, že je požadována nová navigace. Dá se použít k zrušení navigace.

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Probíhá pravidelně během stahování, aby se poskytly informace o průběhu navigace.

- <xref:System.Windows.Navigation.NavigationService.Navigated>. Vyvolá se při umístění a stažení stránky.

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Nastane, pokud se zastaví navigace (voláním <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), nebo když se požaduje nová navigace, zatímco probíhá aktuální navigace.

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. Vyvolá se v případě, že dojde k vyvolání chyby při přechodu na požadovaný obsah.

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Nastane, pokud se obsah, na který se přechází, načte a analyzuje a začala vykreslování.

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Vyvolá se v případě, že dojde k zahájení navigace na fragment obsahu.

  - Ihned, pokud je požadovaný fragment v aktuálním obsahu.

  - Po načtení zdrojového obsahu, pokud je požadovaný fragment v jiném obsahu.

Navigační události jsou vyvolány v pořadí, které je znázorněno na následujícím obrázku.

![Graf toku navigace na stránce](./media/navigation-overview/order-of-navigation-events.png "Diagram toku události navigace stránky")

Obecně platí, <xref:System.Windows.Controls.Page> o těchto událostech obavy. Je pravděpodobnější, že s nimi má aplikace obavy a z tohoto důvodu tyto události jsou také vyvolány <xref:System.Windows.Application> třídy:

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

Pokaždé, když <xref:System.Windows.Navigation.NavigationService> vyvolá událost, třída <xref:System.Windows.Application> vyvolá odpovídající událost. <xref:System.Windows.Controls.Frame> a <xref:System.Windows.Navigation.NavigationWindow> nabízejí stejné události pro detekci navigace v příslušných oborech.

V některých případech může být <xref:System.Windows.Controls.Page> zajímat tyto události. <xref:System.Windows.Controls.Page> například může zpracovat událost <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> a určit, zda se má zrušit navigace mimo sebe. To je ukázáno v následujícím příkladu.

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

Pokud zaregistrujete obslužnou rutinu s událostí navigace z <xref:System.Windows.Controls.Page>, jak je uvedeno v předchozím příkladu, je také nutné zrušit registraci obslužné rutiny události. Pokud ne, může docházet k vedlejším účinkům v souvislosti s tím, jak se navigace WPF pamatuje <xref:System.Windows.Controls.Page> navigaci pomocí deníku.

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>Zapamatování navigace pomocí deníku

WPF používá ke zapamatování stránek, na které jste přešli, dva zásobníky: zásobník back-stack a předávací zásobník. Když přejdete z aktuálního <xref:System.Windows.Controls.Page> k novému <xref:System.Windows.Controls.Page> nebo přejdete na stávající <xref:System.Windows.Controls.Page>, aktuální <xref:System.Windows.Controls.Page> se přidá do *zásobníku back*-and. Když přejdete z aktuálního <xref:System.Windows.Controls.Page> zpátky na předchozí <xref:System.Windows.Controls.Page>, do *předávacího zásobníku*se přidá aktuální <xref:System.Windows.Controls.Page>. Sada back-Stack, předávací zásobník a funkce pro jejich správu se souhrnně označují jako deník. Každá položka v zásobníku back-stack a předávací zásobník je instancí třídy <xref:System.Windows.Navigation.JournalEntry> a je označována jako *Položka deníku*.

#### <a name="navigating-the-journal-from-internet-explorer"></a>Navigace v deníku z aplikace Internet Explorer

V koncepčních případech deník funguje stejným způsobem jako tlačítka **zpět** a **předávat** v aplikaci Internet Explorer. Zobrazují se na následujícím obrázku.

![Tlačítka zpět a přeposílání](./media/navigation-overview/back-and-forward-navigation.png "Přejděte pomocí tlačítek zpět a vpřed.")

Pro XBAP, které jsou hostovány aplikací Internet Explorer, WPF integruje deník do navigačních [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikace Internet Explorer. To umožňuje uživatelům navigovat stránky v XBAP pomocí tlačítek **zpět**, **vpřed**a **poslední stránky** v aplikaci Internet Explorer.

> [!IMPORTANT]
> Pokud uživatel přejde v aplikaci Internet Explorer směrem od a zpět do aplikace XBAP, budou v deníku uchovány pouze položky deníku pro stránky, které nejsou udržovány v aktivním stavu. Diskuzi o tom, jak udržovat stránky aktivní, najdete v části [životnost stránky a deník](#PageLifetime) dále v tomto tématu.

Ve výchozím nastavení je text pro každý <xref:System.Windows.Controls.Page>, který se zobrazí v seznamu **poslední stránky** v aplikaci Internet Explorer, identifikátor URI pro <xref:System.Windows.Controls.Page>. V mnoha případech to není pro uživatele obzvláště smysluplné. Naštěstí můžete změnit text pomocí jedné z následujících možností:

1. Hodnota atributu připojené `JournalEntry.Name`.

2. Hodnota atributu `Page.Title`.

3. Hodnota atributu `Page.WindowTitle` a identifikátor URI pro aktuální <xref:System.Windows.Controls.Page>.

4. Identifikátor URI pro aktuální <xref:System.Windows.Controls.Page>. (Výchozí)

Pořadí, ve kterém jsou možnosti uvedené, odpovídá pořadí priority pro hledání textu. Například pokud je nastavena `JournalEntry.Name`, ostatní hodnoty jsou ignorovány.

Následující příklad používá atribut `Page.Title` ke změně textu, který se zobrazí pro položku deníku.

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>Navigace v deníku pomocí WPF

I když uživatel může přejít do deníku pomocí stránek **zpět**, **vpřed**a **nedávno** v aplikaci Internet Explorer, můžete také procházet deník pomocí deklarativních i programových mechanismů poskytovaných WPF. Jedním z důvodů, jak to provést, je poskytnout na stránkách vlastní navigační uživatelská rozhraní.

Podporu navigace v deníku lze deklarativně přidat pomocí navigačních příkazů, které jsou zpřístupněny <xref:System.Windows.Input.NavigationCommands>. Následující příklad ukazuje, jak použít navigační příkaz `BrowseBack`.

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

Deník můžete programově procházet pomocí jednoho z následujících členů třídy <xref:System.Windows.Navigation.NavigationService>:

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

Deník je také možné manipulovat programově, jak je popsáno v části [zachování stavu obsahu s historií navigace](#RetainingContentStateWithNavigationHistory) dále v tomto tématu.

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>Životnost stránky a deník

Zvažte použití aplikace XBAP s několika stránkami, které obsahují bohatou obsah, včetně grafiky, animací a médií. Nároky na paměť pro stránky, jako jsou ty, můžou být poměrně velké, zejména pokud se používají video a zvuková média. Vzhledem k tím, že stránky "remembers", na které byly přesměrovány, může aplikace XBAP rychle spotřebovat velkou a znatelné množství paměti.

Z tohoto důvodu je výchozí chování deníku ukládat <xref:System.Windows.Controls.Page> metadata v jednotlivých položkách deníku, nikoli odkaz na objekt <xref:System.Windows.Controls.Page>. Při přechodu na položku deníku na se k vytvoření nové instance zadaného <xref:System.Windows.Controls.Page>používá metadata <xref:System.Windows.Controls.Page>. V důsledku toho má každý <xref:System.Windows.Controls.Page>, který je navigací, dobu života, která je znázorněna na následujícím obrázku.

![Doba života stránky](./media/navigation-overview/navigated-page-lifetime.png "To ukazuje dobu života při přechodu stránky.")

I když použití výchozího chování při zakládání do deníku může ušetřit při využití paměti, může se snížit výkon vykreslování na stránce; opětovné vytvoření instance <xref:System.Windows.Controls.Page> může být náročné na čas, zejména v případě, že má hodně obsahu. Pokud potřebujete zachovat <xref:System.Windows.Controls.Page> instanci v deníku, můžete k tomu vykreslit dvěma způsoby. Nejprve můžete programově přejít na objekt <xref:System.Windows.Controls.Page> voláním metody <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>.

Za druhé můžete určit, že se má WPF v deníku uchovávat instance <xref:System.Windows.Controls.Page> nastavením vlastnosti <xref:System.Windows.Controls.Page.KeepAlive%2A> na `true` (výchozí hodnota je `false`). Jak je znázorněno v následujícím příkladu, lze nastavit <xref:System.Windows.Controls.Page.KeepAlive%2A> deklarativně v kódu.

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

Doba života <xref:System.Windows.Controls.Page>, která je udržována v provozu, je trochu odlišná od z nich. Při prvním <xref:System.Windows.Controls.Page>, která je udržována v aktivním stavu, se přechází na, je vytvořena instance stejně jako <xref:System.Windows.Controls.Page>, která není udržována jako aktivní. Vzhledem k tomu, že je instance <xref:System.Windows.Controls.Page> uchována v deníku, není nikdy vytvořena její instance, dokud zůstane v deníku. V důsledku toho, pokud <xref:System.Windows.Controls.Page> má inicializační logiku, která musí být volána pokaždé, když je <xref:System.Windows.Controls.Page> přesměrován na, měli byste jej přesunout z konstruktoru do obslužné rutiny pro událost <xref:System.Windows.FrameworkElement.Loaded>. Jak je znázorněno na následujícím obrázku, <xref:System.Windows.FrameworkElement.Loaded> a <xref:System.Windows.FrameworkElement.Unloaded> události jsou stále vyvolány pokaždé, když je <xref:System.Windows.Controls.Page> přecházení do a v uvedeném pořadí.

![Když jsou vyvolány načtené a uvolněné události](./media/navigation-overview/loaded-and-unloaded-events.png "Načtené a uvolněné události jsou vyvolány při přechodu na stránku do a z.")

Pokud <xref:System.Windows.Controls.Page> nezůstane aktivní, neměli byste provádět žádnou z následujících akcí:

- Uložte na něj odkaz nebo jeho část.

- Zaregistrujte obslužné rutiny událostí s událostmi, které nejsou implementovány.

Jedním z těchto kroků je vytvoření odkazů, které vynutí, aby se <xref:System.Windows.Controls.Page> zachovala v paměti, i když byla odebrána z deníku.

Obecně platí, že byste měli upřednostňovat výchozí <xref:System.Windows.Controls.Page> chování při neudržení <xref:System.Windows.Controls.Page> Alive. Nicméně má dopad na stav, který je popsán v následující části.

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>Zachování stavu obsahu s historií navigace

Pokud se <xref:System.Windows.Controls.Page> neudržuje aktivní a obsahuje ovládací prvky, které shromažďují data od uživatele, co se stane s daty, pokud uživatel přejde pryč z a zpět do <xref:System.Windows.Controls.Page>? V perspektivě uživatelského prostředí by měl uživatel očekávat, že uvidí data, která jste předtím zadali. Bohužel, protože je vytvořena nová instance <xref:System.Windows.Controls.Page> s každou navigací, jsou ovládací prvky, které shromáždily data, znovu vytvořeny instance a data jsou ztracena.

Naštěstí deník poskytuje podporu pro zapamatování dat napříč <xref:System.Windows.Controls.Page>mi navigacemi, včetně dat ovládacího prvku. Konkrétně záznam deníku pro každý <xref:System.Windows.Controls.Page> funguje jako dočasný kontejner pro přidružený stav <xref:System.Windows.Controls.Page>. Následující kroky popisují, jak se tato podpora používá, když <xref:System.Windows.Controls.Page> prochází:

1. Do deníku se přidá položka pro aktuální <xref:System.Windows.Controls.Page>.

2. Stav <xref:System.Windows.Controls.Page> je uložen s položkou deníku pro tuto stránku, která je přidána do zásobníku back.

3. Nový <xref:System.Windows.Controls.Page> přechází na.

Když se stránka <xref:System.Windows.Controls.Page> přejde zpět na, pomocí deníku se provede následující kroky:

1. Je vytvořena instance <xref:System.Windows.Controls.Page> (horní položka deníku v zásobníku back-Stack).

2. <xref:System.Windows.Controls.Page> se aktualizuje se stavem, který byl uložen s položkou deníku pro <xref:System.Windows.Controls.Page>.

3. <xref:System.Windows.Controls.Page> se přechází zpět na.

WPF automaticky používá tuto podporu, když jsou v <xref:System.Windows.Controls.Page>použity následující ovládací prvky:

- <xref:System.Windows.Controls.CheckBox>

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.Expander>

- <xref:System.Windows.Controls.Frame>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListBoxItem>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.ProgressBar>

- <xref:System.Windows.Controls.RadioButton>

- <xref:System.Windows.Controls.Slider>

- <xref:System.Windows.Controls.TabControl>

- <xref:System.Windows.Controls.TabItem>

- <xref:System.Windows.Controls.TextBox>

Pokud <xref:System.Windows.Controls.Page> používá tyto ovládací prvky, data zadaná do těchto ovládacích prvků se pamatují napříč <xref:System.Windows.Controls.Page>mi navigacemi, jak je znázorněno na základě **oblíbené barvy**<xref:System.Windows.Controls.ListBox> na následujícím obrázku.

![Stránka s ovládacími prvky, které zapamatují stav](./media/navigation-overview/data-remembered-across-page-navigations.png "Zadaná data jsou zapamatovatná napříč navigacemi stránky.")

Pokud <xref:System.Windows.Controls.Page> má jiné ovládací prvky než ty v předchozím seznamu nebo pokud je stav uložený ve vlastních objektech, musíte napsat kód, který způsobí, že deník bude pamatovat stav napříč <xref:System.Windows.Controls.Page>mi navigacemi.

Pokud potřebujete pamatovat malé části stavu napříč <xref:System.Windows.Controls.Page>mi navigacemi, můžete použít vlastnosti závislosti (viz <xref:System.Windows.DependencyProperty>), které jsou nakonfigurované s příznakem <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> metadata.

Pokud stav, který vaše <xref:System.Windows.Controls.Page> potřebuje pamatovat napříč navigacemi, zahrnuje více částí dat, může být méně náročná na kódování kódu pro zapouzdření stavu v jediné třídě a implementaci <xref:System.Windows.Navigation.IProvideCustomContentState>ho rozhraní.

Pokud potřebujete procházet různými stavy jednoho <xref:System.Windows.Controls.Page>, aniž byste museli přecházet ze <xref:System.Windows.Controls.Page> samotného, můžete použít <xref:System.Windows.Navigation.IProvideCustomContentState> a <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.

<a name="Cookies"></a>

### <a name="cookies"></a>Cookies

Další způsob, jakým aplikace WPF můžou ukládat data, je pomocí souborů cookie, které se vytvářejí, aktualizují a odstraňují pomocí <xref:System.Windows.Application.SetCookie%2A> a <xref:System.Windows.Application.GetCookie%2A>ch metod. Soubory cookie, které lze vytvořit v subsystému WPF, jsou stejné soubory cookie, které používají jiné typy webových aplikací; soubory cookie jsou libovolné části dat, které aplikace ukládá v klientských počítačích v rámci nebo napříč relacemi aplikací. Data souborů cookie obvykle přebírají formu dvojice název/hodnota v následujícím formátu.

*Název* `=` *hodnota*

Když jsou data předána <xref:System.Windows.Application.SetCookie%2A>společně s <xref:System.Uri> umístění, pro které má být soubor cookie nastaven, je soubor cookie vytvořen v paměti a je k dispozici pouze po dobu trvání aktuální relace aplikace. Tento typ souboru cookie je označován jako *soubor cookie relace*.

Chcete-li uložit soubor cookie mezi relacemi aplikace, je nutné do souboru cookie přidat datum vypršení platnosti v následujícím formátu.

*Název* `=` *hodnota* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

Soubor cookie s datem vypršení platnosti je uložen ve složce dočasných internetových souborů instalace systému Windows, dokud nevyprší platnost souboru cookie. Takový soubor cookie je známý jako *trvalý soubor cookie* , protože trvá napříč relacemi aplikací.

Můžete načíst relaci a trvalé soubory cookie voláním metody <xref:System.Windows.Application.GetCookie%2A> a předáním <xref:System.Uri> místa, kde byl soubor cookie nastaven pomocí metody <xref:System.Windows.Application.SetCookie%2A>.

Níže jsou uvedeny některé způsoby, jak jsou soubory cookie podporovány v subsystému WPF:

- Samostatné aplikace a XBAP pro WPF můžou vytvářet a spravovat soubory cookie.

- Soubory cookie, které jsou vytvořeny v XBAP, lze použít z prohlížeče.

- Aplikace XBAP ze stejné domény mohou vytvářet a sdílet soubory cookie.

- Aplikace XBAP a stránky HTML ze stejné domény mohou vytvářet a sdílet soubory cookie.

- Soubory cookie jsou odesílány při použití aplikací XBAP a volné stránky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] webové požadavky.

- Přístup k souborům cookie mají pouze aplikace XBAP a XBAP na nejvyšší úrovni hostované na IFRAME.

- Podpora souborů cookie v WPF je stejná pro všechny podporované prohlížeče.

- V aplikaci Internet Explorer jsou zásady P3P, které se týkají souborů cookie, respektovány v rámci WPF, zejména pokud jde o první stranu a XBAP jiných výrobců.

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>Strukturovaná navigace

Pokud potřebujete předat data z jednoho <xref:System.Windows.Controls.Page> do druhé, můžete předat data jako argumenty konstruktoru nebez parametrů <xref:System.Windows.Controls.Page>. Všimněte si, že pokud použijete tento postup, musíte ponechat <xref:System.Windows.Controls.Page> Alive; Pokud ne, WPF při příštím přechodu na <xref:System.Windows.Controls.Page>znovu vytvoří instanci <xref:System.Windows.Controls.Page> pomocí konstruktoru bez parametrů.

Případně může <xref:System.Windows.Controls.Page> implementovat vlastnosti, které jsou nastaveny s daty, která je třeba předat. Když ale <xref:System.Windows.Controls.Page> potřebuje předat data zpět do <xref:System.Windows.Controls.Page>, která se na něj přešla, stane se něco obtížné. Problémem je, že navigace nezpůsobí nativní podporu mechanismů pro zajištění, že <xref:System.Windows.Controls.Page> se vrátí do po přechodu na. Navigace v podstatě nepodporuje sémantiku volání a vracení. Chcete-li tento problém vyřešit, WPF poskytuje třídu <xref:System.Windows.Navigation.PageFunction%601>, kterou můžete použít k zajištění, že <xref:System.Windows.Controls.Page> se vrátí předvídatelným a strukturovaným způsobem. Další informace najdete v tématu [Přehled strukturované navigace](structured-navigation-overview.md).

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>Třída objektu NavigationWindow

K tomuto okamžiku jste viděli škálu navigačních služeb, které nejpravděpodobněji použijete k vytváření aplikací s naviguje obsahem. Tyto služby byly popsány v kontextu programu XBAP, i když nejsou omezeny na aplikace XBAP. Moderní operační systémy a aplikace Windows využívají možnosti prohlížeče moderních uživatelů k začlenění navigace ve stylu prohlížeče do samostatných aplikací. Mezi běžné příklady patří:

- **Tezaurus Word**: navigace mezi možnostmi Wordu

- **Průzkumník souborů**: navigace v souborech a složkách

- **Průvodci**: rozdělení složitého úkolu na více stránek, mezi kterými lze přejít. Příkladem je Průvodce součástmi systému Windows, který zpracovává přidávání a odebírání funkcí systému Windows.

Chcete-li zahrnout navigaci ve stylu prohlížeče do samostatných aplikací, můžete použít třídu <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> je odvozena z <xref:System.Windows.Window> a rozšiřuje ji se stejnou podporou navigace, kterou aplikace XBAP nabízí. <xref:System.Windows.Navigation.NavigationWindow> můžete použít buď jako hlavní okno samostatné aplikace, nebo jako sekundární okno, jako je například dialogové okno.

Chcete-li implementovat <xref:System.Windows.Navigation.NavigationWindow>, stejně jako u většiny tříd nejvyšší úrovně v subsystému WPF (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>a tak dále), použijte kombinaci značek a kódu na pozadí. To je ukázáno v následujícím příkladu.

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

Tento kód vytvoří <xref:System.Windows.Navigation.NavigationWindow>, který automaticky přejde na <xref:System.Windows.Controls.Page> (Domovská stránka. XAML) při otevření <xref:System.Windows.Navigation.NavigationWindow>. Pokud je <xref:System.Windows.Navigation.NavigationWindow> hlavním oknem aplikace, můžete jej spustit pomocí atributu `StartupUri`. Zobrazuje se v následujícím kódu.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

Následující obrázek ukazuje <xref:System.Windows.Navigation.NavigationWindow> hlavním oknem samostatné aplikace.

![Hlavní okno](./media/navigation-overview/navigation-window-as-main-window.png "Navigační okno jako hlavní okno")

Z obrázku vidíte, že <xref:System.Windows.Navigation.NavigationWindow> má název, a to i v případě, že nebyl nastaven v kódu implementace <xref:System.Windows.Navigation.NavigationWindow> z předchozího příkladu. Místo toho je název nastaven pomocí vlastnosti <xref:System.Windows.Controls.Page.WindowTitle%2A>, která je zobrazena v následujícím kódu.

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

Nastavení vlastností <xref:System.Windows.Controls.Page.WindowWidth%2A> a <xref:System.Windows.Controls.Page.WindowHeight%2A> ovlivní také <xref:System.Windows.Navigation.NavigationWindow>.

Obvykle implementujete vlastní <xref:System.Windows.Navigation.NavigationWindow>, pokud potřebujete přizpůsobit jeho chování nebo jeho vzhled. Pokud ani to neuděláte, můžete použít zástupce. Pokud zadáte identifikátor URI balíčku <xref:System.Windows.Controls.Page> jako <xref:System.Windows.Application.StartupUri%2A> v samostatné aplikaci, <xref:System.Windows.Application> automaticky vytvoří <xref:System.Windows.Navigation.NavigationWindow> pro hostování <xref:System.Windows.Controls.Page>. Následující kód ukazuje, jak to povolit.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

Pokud chcete, aby sekundární okno aplikace, jako je například dialogové okno, bylo <xref:System.Windows.Navigation.NavigationWindow>, můžete k jeho otevření použít kód v následujícím příkladu.

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

Výsledek je znázorněn na následujícím obrázku.

![Dialogové okno](./media/navigation-overview/navigation-window-as-dialog-box.png "Navigační okno jako dialogové okno")

Jak vidíte, <xref:System.Windows.Navigation.NavigationWindow> zobrazuje tlačítka pro **zpět** a **vpřed** ve stylu aplikace Internet Explorer, která uživatelům umožňují procházet deník. Tato tlačítka poskytují stejné uživatelské prostředí, jak je znázorněno na následujícím obrázku.

![Tlačítka zpět a přeposílání v objektu NavigationWindow](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "Tlačítka zpět a přeposílání v navigačním okně")

Pokud vaše stránky poskytují podporu a uživatelské rozhraní pro navigaci v deníku, můžete skrýt tlačítka **zpět** a **přeslat** zobrazená pomocí <xref:System.Windows.Navigation.NavigationWindow> nastavením hodnoty vlastnosti <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> na `false`.

Alternativně můžete použít podporu přizpůsobení v WPF pro nahrazení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.NavigationWindow> sebe sama.

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Třída Frame

Prohlížeč i <xref:System.Windows.Navigation.NavigationWindow> jsou systémy Windows, které hostují obsah naviguje. V některých případech mají aplikace obsah, který není nutné hostovat do celého okna. Místo toho se takový obsah bude hostovat v jiném obsahu. Obsah naviguje můžete vložit do dalšího obsahu pomocí třídy <xref:System.Windows.Controls.Frame>. <xref:System.Windows.Controls.Frame> poskytuje stejnou podporu jako <xref:System.Windows.Navigation.NavigationWindow> a XBAP.

Následující příklad ukazuje, jak přidat <xref:System.Windows.Controls.Frame> do <xref:System.Windows.Controls.Page> deklarativně pomocí elementu `Frame`.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

Tento kód nastaví atribut `Source` `Frame` elementu s identifikátorem URI balíčku pro <xref:System.Windows.Controls.Page>, na který <xref:System.Windows.Controls.Frame> počáteční přejít. Následující obrázek ukazuje XBAP s <xref:System.Windows.Controls.Page>em, který má <xref:System.Windows.Controls.Frame>, který přešel mezi několika stránkami.

![Rámec, který přešel mezi několika stránkami](./media/navigation-overview/frame-navigation-between-multiple-pages.png "Tím se zobrazí navigace mezi několika stránkami.")

Nemusíte používat <xref:System.Windows.Controls.Frame> v obsahu <xref:System.Windows.Controls.Page>. Také je běžné hostovat <xref:System.Windows.Controls.Frame> v rámci obsahu <xref:System.Windows.Window>.

Ve výchozím nastavení <xref:System.Windows.Controls.Frame> používá pouze vlastní deník při absenci jiného deníku. Pokud je <xref:System.Windows.Controls.Frame> součástí obsahu, který je hostován v rámci <xref:System.Windows.Navigation.NavigationWindow> nebo XBAP, <xref:System.Windows.Controls.Frame> používá deník, který patří <xref:System.Windows.Navigation.NavigationWindow> nebo XBAP. V některých případech ale může být potřeba, aby <xref:System.Windows.Controls.Frame> odpovědnost za svůj vlastní deník. Jedním z důvodů je povolit navigaci v deníku na stránkách hostovaných <xref:System.Windows.Controls.Frame>. To je znázorněno na následujícím obrázku.

![Diagram rámečku a stránky](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "Tím se zobrazí navigace v deníku na stránkách hostovaných snímkem.")

V takovém případě můžete <xref:System.Windows.Controls.Frame> nakonfigurovat, aby používaly vlastní deník, nastavením vlastnosti <xref:System.Windows.Controls.Frame.JournalOwnership%2A> <xref:System.Windows.Controls.Frame> na <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. Zobrazuje se v následujícím kódu.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

Následující obrázek znázorňuje účinek přechodu v rámci <xref:System.Windows.Controls.Frame>, který používá vlastní deník.

![Rámec, který používá vlastní deník](./media/navigation-overview/frame-uses-its-own-journal.png "To ukazuje účinek přechodu v rámci rámce, který používá vlastní deník.")

Všimněte si, že položky deníku jsou zobrazeny [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] navigace v <xref:System.Windows.Controls.Frame>a nikoli aplikací Internet Explorer.

> [!NOTE]
> Pokud je <xref:System.Windows.Controls.Frame> součástí obsahu, který je hostován v <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> používá vlastní deník a následně zobrazuje vlastní navigační [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].

Pokud uživatelské prostředí vyžaduje, aby <xref:System.Windows.Controls.Frame> poskytoval vlastní deník, aniž by se zobrazila [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]navigace, můžete skrýt navigační [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nastavením <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> na <xref:System.Windows.Visibility.Hidden>. Zobrazuje se v následujícím kódu.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>Hostitelé navigace

<xref:System.Windows.Controls.Frame> a <xref:System.Windows.Navigation.NavigationWindow> jsou třídy, které jsou známé jako hostitelé navigace. *Navigační hostitel* je třída, která může přejít na obsah a zobrazit ho. K tomu každý navigační hostitel používá vlastní <xref:System.Windows.Navigation.NavigationService> a deník. Základní konstrukce pro navigační hostitele je znázorněna na následujícím obrázku.

![Navigátorové diagramy](./media/navigation-overview/navigation-host-construction.png "Základní konstrukce pro navigačního hostitele")

V podstatě to umožňuje <xref:System.Windows.Navigation.NavigationWindow> a <xref:System.Windows.Controls.Frame> poskytnout stejnou podporu navigace, kterou XBAP poskytuje při hostování v prohlížeči.

Kromě použití <xref:System.Windows.Navigation.NavigationService> a deníku, hostitelé navigace implementují stejné členy, které <xref:System.Windows.Navigation.NavigationService> implementuje. To je znázorněno na následujícím obrázku.

![Deník v rámečku a v objektu NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "Navigační okno a rámec")

To vám umožní naprogramovat podporu navigace přímo proti nim. Můžete to vzít v úvahu, pokud potřebujete zadat vlastní navigační [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro <xref:System.Windows.Controls.Frame>, která je hostována v <xref:System.Windows.Window>. Oba typy navíc implementují další členy související s navigací, včetně `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) a `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), což vám umožní vytvořit výčet položek deníku v zásobníku back-stack a vpřed v uvedeném pořadí.

Jak bylo zmíněno dříve, více než jeden deník může existovat v rámci aplikace. Následující obrázek uvádí příklad, kdy k tomu může dojít.

![Několik deníků v rámci jedné aplikace](./media/navigation-overview/multiple-journals-in-one-application.png "Toto je příklad více než jednoho deníku v aplikaci.")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>Přechod na obsah jiný než XAML stránky

V tomto tématu se <xref:System.Windows.Controls.Page> a sada XBAP používaly k předvedení různých možností navigace WPF. <xref:System.Windows.Controls.Page>, který je zkompilován do aplikace, však není jediným typem obsahu, na který lze přejít, a pak není jediným způsobem, jak určit obsah, zabalit aplikaci XBAP.

Jak ukazuje Tato část, můžete také přejít na volné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, soubory HTML a objekty.

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>Navigace do volných souborů XAML

Volně [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je soubor s následujícími charakteristikami:

- Obsahuje pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (to znamená žádný kód).

- Má odpovídající deklaraci oboru názvů.

- Má příponu názvu souboru. XAML.

Zvažte například následující obsah, který je uložen jako volně [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor Person. XAML.

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

Když dvakrát kliknete na soubor, otevře se prohlížeč a přejde na něj a zobrazí se jeho obsah. To je znázorněno na následujícím obrázku.

![Zobrazení obsahu v souboru Person. XAML](./media/navigation-overview/contents-of-person-xaml-file.png "Zobrazuje obsah souboru Person. XAML.")

Můžete zobrazit volný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor z následujících možností:

- Web na místním počítači, v intranetu nebo na internetu.

- Sdílená složka UNC (Universal Naming Convention).

- Místní disk.

Do oblíbených položek v prohlížeči se dá přidat volný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor, nebo se může jednat o domovskou stránku prohlížeče.

> [!NOTE]
> Další informace o publikování a spouštění volných stránek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] najdete v tématu [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).

Jedním z omezení z hlediska volného [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je, že je možné pouze hostovat obsah, který je bezpečný pro spuštění v částečném vztahu důvěryhodnosti. `Window` například nemůže být kořenovým prvkem volného [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru. Další informace najdete v tématu [zabezpečení částečné důvěryhodnosti WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>Navigace do souborů HTML pomocí rámce

Jak byste mohli očekávat, můžete také přejít na HTML. Jednoduše potřebujete zadat identifikátor URI, který používá schéma HTTP. Například následující [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ukazuje <xref:System.Windows.Controls.Frame>, který naviguje na stránku HTML.

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

Navigace na HTML vyžaduje zvláštní oprávnění. Například nemůžete přejít z aplikace XBAP, která je spuštěna v izolovaném prostoru zabezpečení zóny Internet Zone. Další informace najdete v tématu [zabezpečení částečné důvěryhodnosti WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Navigace do souborů HTML pomocí ovládacího prvku WebBrowser

<xref:System.Windows.Controls.WebBrowser> ovládací prvek podporuje hostování dokumentů HTML, navigaci a spolupráci pomocí skriptů a spravovaného kódu. Podrobné informace o ovládacím prvku <xref:System.Windows.Controls.WebBrowser> naleznete v tématu <xref:System.Windows.Controls.WebBrowser>.

Stejně jako <xref:System.Windows.Controls.Frame>, přechod na HTML pomocí <xref:System.Windows.Controls.WebBrowser> vyžaduje zvláštní oprávnění. Například z aplikace s částečným vztahem důvěryhodnosti můžete přejít pouze k HTML, které je umístěno na webu původu. Další informace najdete v tématu [zabezpečení částečné důvěryhodnosti WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>Navigace na vlastní objekty

Pokud máte data, která jsou uložena jako vlastní objekty, jedním ze způsobů, jak tato data zobrazit, je vytvoření <xref:System.Windows.Controls.Page> s obsahem, který je svázán s těmito objekty (viz [Přehled datové vazby](../../../desktop-wpf/data/data-binding-overview.md)). Pokud nepotřebujete pro zobrazení objektů režii vytváření celé stránky, můžete místo toho přejít přímo na ně.

Zvažte `Person` třídu, která je implementována v následujícím kódu.

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

Chcete-li na něj přejít, zavolejte metodu <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType>, jak je znázorněno v následujícím kódu.

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

Výsledek je znázorněn na následujícím obrázku.

![Stránka, která naviguje na třídu](./media/navigation-overview/page-navigates-to-an-object.png "Toto je příklad stránky, která naviguje k objektu.")

Z tohoto obrázku vidíte, že se nezobrazí nic užitečného. Ve skutečnosti je zobrazená hodnota návratovou hodnotou metody `ToString` objektu **Person** ; ve výchozím nastavení je to jediná hodnota, kterou může platforma WPF použít k reprezentaci vašeho objektu. Metodu `ToString` můžete přepsat tak, aby vracela smysluplnější informace, i když bude i nadále pouze řetězcová hodnota. Jednu z možností, kterou můžete použít k prezentaci funkcí WPF, je použití datové šablony. Můžete implementovat šablonu dat, kterou může WPF přidružit k objektu určitého typu. Následující kód ukazuje datovou šablonu pro objekt `Person`.

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

Zde je šablona dat přidružena k typu `Person` pomocí rozšíření značek `x:Type` v atributu `DataType`. Šablona dat poté vytvoří vazby `TextBlock` prvků (viz <xref:System.Windows.Controls.TextBlock>) na vlastnosti třídy `Person`. Následující obrázek ukazuje aktualizovaný vzhled objektu `Person`.

![Přechod na třídu, která má šablonu dat](./media/navigation-overview/navigating-to-a-class.png "Přechod na třídu, která má datovou šablonu.")

Výhodou této techniky je konzistence, kterou získáte pomocí možnosti opětovného použití šablony dat k zobrazení objektů konzistentně kdekoli v aplikaci.

Další informace o datových šablonách najdete v tématu [Přehled šablonování dat](../data/data-templating-overview.md).

<a name="Security"></a>

## <a name="security"></a>Zabezpečení –

Podpora navigace WPF umožňuje aplikacím XBAP přejít přes Internet a umožňuje aplikacím hostovat obsah třetích stran. Pro ochranu aplikací i uživatelů před škodlivým chováním WPF poskytuje celou řadu funkcí zabezpečení, které jsou popsány [v tématu zabezpečení a](../security-wpf.md) [částečně důvěryhodné zabezpečení WPF](../wpf-partial-trust-security.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Přehled správy aplikací](application-management-overview.md)
- [Sbalení URI v technologii WPF](pack-uris-in-wpf.md)
- [Přehled strukturované navigace](structured-navigation-overview.md)
- [Přehled topologií navigace](navigation-topologies-overview.md)
- [Postupy](navigation-how-to-topics.md)
- [Nasazení aplikace WPF](deploying-a-wpf-application-wpf.md)
