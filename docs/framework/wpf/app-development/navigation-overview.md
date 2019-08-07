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
ms.openlocfilehash: ee2f6050eeea6eec840156ed5dce9fb9b6172149
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796867"
---
# <a name="navigation-overview"></a>Přehled navigace

Windows Presentation Foundation (WPF) podporuje navigaci ve stylu prohlížeče, kterou lze použít ve dvou typech aplikací: samostatné aplikace a [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Pro zabalení obsahu pro navigaci [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <xref:System.Windows.Controls.Page> poskytuje třídu. Můžete přecházet z jednoho <xref:System.Windows.Controls.Page> na jiný deklarativní, <xref:System.Windows.Documents.Hyperlink>pomocí nebo <xref:System.Windows.Navigation.NavigationService>programově pomocí. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]pomocí deníku zapamatuje stránky, na které byly přecházet, a přejděte zpět na ně.

<xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>a deníku tvoří základní podporu navigace, kterou nabízí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Tento přehled podrobněji prozkoumá tyto funkce před tím, než pokrývá rozšířenou podporu navigace, která [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] zahrnuje navigaci na volné soubory, soubory HTML a objekty.

> [!NOTE]
> V tomto tématu pojem "prohlížeč" odkazuje pouze na prohlížeče, které mohou hostovat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, které aktuálně obsahují [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] a Firefox. V případě [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , že konkrétní funkce jsou podporovány pouze konkrétním prohlížečem, je na verzi prohlížeče odkazováno.

## <a name="navigation-in-wpf-applications"></a>Navigace v aplikacích WPF

V tomto tématu najdete přehled klíčových navigačních funkcí v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nástroji. Tyto možnosti jsou dostupné jak pro samostatné aplikace, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]tak i v případě, že je toto téma prezentuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]v kontextu.

> [!NOTE]
> Toto téma se zabývá sestavou a nasazením [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Další informace o [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]naleznete v tématu [Přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).

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

V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]můžete přejít na několik typů obsahu, které zahrnují .NET Framework objekty, vlastní objekty, hodnoty výčtu, uživatelské ovládací prvky, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory a soubory HTML. Ale zjistíte, že nejběžnější a pohodlný způsob balení obsahu je pomocí <xref:System.Windows.Controls.Page>. Kromě toho <xref:System.Windows.Controls.Page> implementuje funkce specifické pro navigaci a zlepšuje jejich vzhled a zjednodušuje vývoj.

Pomocí <xref:System.Windows.Controls.Page>můžete deklarativně implementovat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránku naviguje obsahu pomocí značek, jako je následující.

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

Objekt <xref:System.Windows.Controls.Page> , který je implementován [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v označení `Page` , má jako svůj kořenový prvek a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vyžaduje [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] deklaraci oboru názvů. `Page` Element obsahuje obsah, na který chcete přejít a zobrazit. Obsah můžete přidat nastavením `Page.Content` prvku vlastnosti, jak je znázorněno v následujícím kódu.

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content`může obsahovat pouze jeden podřízený element; v předchozím příkladu je obsahem jeden řetězec "Hello, Page!" V praxi obvykle použijete ovládací prvek rozložení jako podřízený element (viz [rozložení](../advanced/layout.md)), který bude obsahovat a vytvořit obsah.

Podřízené prvky `Page` elementu jsou považovány za obsah <xref:System.Windows.Controls.Page> a a v důsledku toho nemusíte používat explicitní `Page.Content` deklaraci. Následující kód je deklarativní ekvivalent předchozí ukázky.

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

V tomto případě `Page.Content` je automaticky nastaveno s podřízenými prvky `Page` elementu. Další informace najdete v tématu [model obsahu WPF](../controls/wpf-content-model.md).

Pouze <xref:System.Windows.Controls.Page> označení je užitečné pro zobrazení obsahu. <xref:System.Windows.Controls.Page> Může však také zobrazit ovládací prvky, které umožňují uživatelům interakci se stránkou, a může reagovat na interakci uživatele, a to zpracováním událostí a voláním logiky aplikace. Interaktivní <xref:System.Windows.Controls.Page> je implementována pomocí kombinace kódu a kódu na pozadí, jak je znázorněno v následujícím příkladu.

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

Chcete-li, aby soubor značek a soubor s kódem na pozadí pracovaly společně, je vyžadována následující konfigurace:

- V kódu `Page` musí element `x:Class` obsahovat atribut. Když je aplikace `x:Class` sestavena, existence v souboru označení způsobí [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] , že vytvoří `partial` třídu, která je odvozena z <xref:System.Windows.Controls.Page> a má název, který je určen `x:Class` atributem. To vyžaduje přidání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklarace oboru názvů [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro schéma ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Vygenerovaná `partial` třída implementuje `InitializeComponent`rozhraní, které je voláno k registraci událostí a nastavení vlastností, které jsou implementovány v označení.

- V kódu na pozadí třída musí být `partial` třída se stejným názvem, který je určen `x:Class` atributem v označení a musí odvozovat z <xref:System.Windows.Controls.Page>. To umožňuje, aby soubor s kódem na pozadí byl přidružen `partial` ke třídě, která je generována pro soubor označení při sestavení aplikace (viz [Vytvoření aplikace WPF](building-a-wpf-application-wpf.md)).

- V kódu na pozadí <xref:System.Windows.Controls.Page> třída musí implementovat konstruktor, který `InitializeComponent` volá metodu. `InitializeComponent`je implementována třídou vygenerovanou `partial` souborem označení pro registraci událostí a nastavení vlastností, které jsou definovány v označení.

> [!NOTE]
> Přidáte-li do projektu <xref:System.Windows.Controls.Page> nový pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Controls.Page> je implementováno pomocí kódu a kódu na pozadí a obsahuje nezbytnou konfiguraci pro vytvoření přidružení mezi značkami a soubory kódu na pozadí jako popsané tady.

Jakmile budete mít <xref:System.Windows.Controls.Page>, můžete na něj přejít. Chcete-li určit <xref:System.Windows.Controls.Page> první, na který aplikace přejde, je nutné nakonfigurovat spuštění. <xref:System.Windows.Controls.Page>

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>Konfigurace úvodní stránky

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]vyžaduje hostování určitého množství aplikační infrastruktury v prohlížeči. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nástrojije třídasoučástídefiniceaplikace,kterávytvářípožadovanouaplikačníinfrastrukturu(vizPřehledsprávyaplikací).<xref:System.Windows.Application> [](application-management-overview.md)

Definice aplikace je obvykle implementována pomocí značek i kódu na pozadí se souborem označení, který je nakonfigurován jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` položka. Následuje definice aplikace pro [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

Může použít definici aplikace k určení začátku <xref:System.Windows.Controls.Page>, což je <xref:System.Windows.Controls.Page> automaticky načteno při [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] spuštění. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] To provedete nastavením <xref:System.Windows.Application.StartupUri%2A> vlastnosti [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] pro požadovanou <xref:System.Windows.Controls.Page>.

> [!NOTE]
> Ve většině případů <xref:System.Windows.Controls.Page> je buď zkompilován nebo nasazen s aplikací. V těchto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] případech, který identifikuje a <xref:System.Windows.Controls.Page> je [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] balík [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], který odpovídá schématu *balíčku* . Tato [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] sada je podrobněji popsána v tématu [identifikátory URI balíčku v](pack-uris-in-wpf.md)subsystému WPF. Můžete také přejít k obsahu pomocí schématu http, které je popsáno níže.

Můžete nastavit <xref:System.Windows.Application.StartupUri%2A> deklarativně v kódu, jak je znázorněno v následujícím příkladu.

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

V tomto příkladu `StartupUri` je atribut nastaven s relativním balíčkem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který identifikuje soubor domoves. XAML. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Když se spustí, Domovská stránka. XAML automaticky přejde do a zobrazí se. To je znázorněno na následujícím obrázku, který ukazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , který se spustil z webového serveru.

![Stránka XBAP](./media/navigation-overview/xbap-launched-from-a-web-server.png "Zobrazuje se XBAP spouštěná z webového serveru.")

> [!NOTE]
> Další informace týkající se vývoje a nasazení [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]nástroje naleznete v tématu [Přehled aplikací WPF XAML browser](wpf-xaml-browser-applications-overview.md) a [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>Konfigurace názvu, šířky a výšky hostitelského okna

Jedna věc, kterou jste si poznamenali na předchozím obrázku, je, že název prohlížeče i panelu karet je [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]pro. Kromě toho není název ani atraktivní ani informativní. Z tohoto důvodu nabízí <xref:System.Windows.Controls.Page> způsob, jak změnit název <xref:System.Windows.Controls.Page.WindowTitle%2A> nastavením vlastnosti. Kromě toho můžete nakonfigurovat šířku a výšku okna <xref:System.Windows.Controls.Page.WindowWidth%2A> prohlížeče nastavením a <xref:System.Windows.Controls.Page.WindowHeight%2A>v uvedeném pořadí.

<xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A> a<xref:System.Windows.Controls.Page.WindowHeight%2A> lze nastavit deklarativně v kódu, jak je znázorněno v následujícím příkladu.

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

Výsledek je znázorněn na následujícím obrázku.

![Název, Výška a šířka okna](./media/navigation-overview/window-title-width-height.png "Zobrazí se název okna, Výška a šířka, které můžete konfigurovat.")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>Navigace hypertextovými odkazy

Typický [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] představuje několik stránek. Nejjednodušší způsob, jak přejít z jedné stránky na druhou, je použít <xref:System.Windows.Documents.Hyperlink>. Můžete deklarativně přidat <xref:System.Windows.Documents.Hyperlink> do a <xref:System.Windows.Controls.Page> pomocí `Hyperlink` elementu, který je zobrazen v následujícím kódu.

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

`Hyperlink` Element vyžaduje následující:

- Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ,na`NavigateUri` kterou se mápřejítna,jakjeurčenoatributem.<xref:System.Windows.Controls.Page>

- Obsah, na který může uživatel kliknout pro zahájení navigace, jako je například text a obrázky (pro obsah, který `Hyperlink` prvek může obsahovat, viz <xref:System.Windows.Documents.Hyperlink>).

Následující obrázek ukazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] s a <xref:System.Windows.Controls.Page> , který má <xref:System.Windows.Documents.Hyperlink>.

![Stránka s hypertextovým odkazem](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "To ukazuje XBAP se stránkou s hypertextovým odkazem.")

Jak byste očekávali, klikněte na <xref:System.Windows.Documents.Hyperlink> tlačítko [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] způsobí, že přejdete <xref:System.Windows.Controls.Page> na, který je identifikován `NavigateUri` atributem. Kromě toho [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] přidá položku pro předchozí <xref:System.Windows.Controls.Page> seznam posledních stránek v [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. To je znázorněno na následujícím obrázku.

![Tlačítka zpět a] přeposílání (./media/navigation-overview/back-and-forward-navigation.png "Přejděte pomocí tlačítek zpět a vpřed.")

Stejně jako podpora navigace z jednoho <xref:System.Windows.Controls.Page> na <xref:System.Windows.Documents.Hyperlink> jiný podporuje také navigaci fragmentem.

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>Navigace v fragmentu

*Navigace fragmentem* je navigace na fragment obsahu v aktuálním <xref:System.Windows.Controls.Page> nebo jiném. <xref:System.Windows.Controls.Page> V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nástroji je fragment obsahu obsah obsažený v pojmenovaném elementu. Pojmenovaný element je element, který má nastaven jeho `Name` atribut. Následující kód ukazuje pojmenovaný `TextBlock` prvek, který obsahuje fragment obsahu.

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

Aby bylo možné přejít k fragmentu obsahu `NavigateUri` , musí atribut obsahovat následující: <xref:System.Windows.Documents.Hyperlink>

- [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Zčástisfragmentemobsahu,<xref:System.Windows.Controls.Page> na který chcete přejít.

- Znak "#".

- Název prvku v <xref:System.Windows.Controls.Page> , který obsahuje fragment obsahu.

Fragment [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] má následující formát.

*PageURI* `#` *ElementName*

Následující příklad ukazuje příklad `Hyperlink` , který je nakonfigurován k přechodu na fragment obsahu.

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> Tato část popisuje výchozí implementaci navigace v rámci fragmentů v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nástroji. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]také umožňuje implementovat vlastní navigační schéma fragmentů, které v rámci součásti vyžaduje zpracování <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> události.

> [!IMPORTANT]
> V případě, že stránky lze procházet [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocí protokolu HTTP, můžete [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] přejít na `Page` fragmenty na volných stránkách (soubory pouze s označením jako kořenový element).
>
> Nicméně volná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka může přejít na vlastní fragmenty.

<a name="NavigationService"></a>

### <a name="navigation-service"></a>Navigační služba

I <xref:System.Windows.Documents.Hyperlink> když umožňuje uživateli iniciovat navigaci na určitou <xref:System.Windows.Controls.Page>činnost, která vyhledává a stahuje <xref:System.Windows.Navigation.NavigationService> stránku, je prováděna třídou. V podstatě <xref:System.Windows.Documents.Hyperlink>poskytuje možnost zpracování žádosti o navigaci jménem kódu klienta, jako je například. <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Navigation.NavigationService> Navíc implementuje podporu vyšší úrovně pro sledování a vliv na navigační požadavek.

<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]Když kliknete na, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] volání pro vyhledání a stažení v zadaném balíčku. <xref:System.Windows.Documents.Hyperlink> Stažený <xref:System.Windows.Controls.Page> prvek je převeden na strom objektů, jejichž kořenový objekt je instancí staženého <xref:System.Windows.Controls.Page>objektu. Odkaz na kořenový <xref:System.Windows.Controls.Page> objekt je uložen <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> ve vlastnosti. Balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro obsah, na který se přešel, je uložený <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> ve vlastnosti, zatímco <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> ukládá balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro poslední stránku, na kterou se přešlo.

> [!NOTE]
> Je možné [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , že aplikace má více než jednu aktuálně aktivní <xref:System.Windows.Navigation.NavigationService>. Další informace naleznete v části [hostitelé navigace](#Navigation_Hosts) dále v tomto tématu.

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>Programová navigace pomocí navigační služby

Nemusíte znát informace o <xref:System.Windows.Navigation.NavigationService> tom, jestli je navigace implementovaná deklarativně v <xref:System.Windows.Documents.Hyperlink>kódu pomocí <xref:System.Windows.Documents.Hyperlink> , protože <xref:System.Windows.Navigation.NavigationService> používá vaše jménem. To znamená, že pokud je přímý nebo nepřímý nadřízený člen a <xref:System.Windows.Documents.Hyperlink> v případě navigačního hostitele (viz hostitelé [Navigace](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> bude moci vyhledat a použít navigační službu pro navigaci hostitele ke zpracování žádosti o navigaci.

Existují však situace, kdy potřebujete použít <xref:System.Windows.Navigation.NavigationService> přímo, včetně následujících:

- Když potřebujete vytvořit instanci s <xref:System.Windows.Controls.Page> použitím konstruktoru bez parametrů.

- V případě, že před přechodem na <xref:System.Windows.Controls.Page> něj potřebujete nastavit vlastnosti,

- Pokud je <xref:System.Windows.Controls.Page> nutné přejít na, aby bylo možné určit pouze v době běhu.

V těchto situacích je nutné napsat kód pro programové iniciování navigace voláním <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metody <xref:System.Windows.Navigation.NavigationService> objektu. Který vyžaduje získání odkazu na <xref:System.Windows.Navigation.NavigationService>.

#### <a name="getting-a-reference-to-the-navigationservice"></a>Získání odkazu na StopLoading

Z důvodů popsaných v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] části [Navigace hostitelé](#Navigation_Hosts) může aplikace obsahovat více než jednu. <xref:System.Windows.Navigation.NavigationService> To znamená, že váš kód potřebuje způsob <xref:System.Windows.Navigation.NavigationService>, jak najít, což je <xref:System.Windows.Navigation.NavigationService> obvykle objekt, který přešel na aktuální <xref:System.Windows.Controls.Page>. Můžete získat odkaz na adresu <xref:System.Windows.Navigation.NavigationService> `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> voláním metody. Chcete-li <xref:System.Windows.Navigation.NavigationService> získat objekt, který přešel na <xref:System.Windows.Controls.Page>konkrétní, <xref:System.Windows.Controls.Page> předáte odkaz na jako argument <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> metody. Následující kód ukazuje, jak získat <xref:System.Windows.Navigation.NavigationService> pro aktuální. <xref:System.Windows.Controls.Page>

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

Jako zástupce <xref:System.Windows.Navigation.NavigationService> pro vyhledání pro <xref:System.Windows.Controls.Page> a <xref:System.Windows.Controls.Page>implementuje <xref:System.Windows.Controls.Page.NavigationService%2A> vlastnost. To je ukázáno v následujícím příkladu.

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> Objekt <xref:System.Windows.Controls.Page> může získat odkaz na jeho <xref:System.Windows.Navigation.NavigationService> při <xref:System.Windows.Controls.Page> vyvolávání <xref:System.Windows.FrameworkElement.Loaded> události.

#### <a name="programmatic-navigation-to-a-page-object"></a>Programová navigace na objekt Page

Následující příklad ukazuje, jak použít <xref:System.Windows.Navigation.NavigationService> k programovému přechodu <xref:System.Windows.Controls.Page>na. Programová navigace je povinná <xref:System.Windows.Controls.Page> , protože objekt, na který se přechází, se dá vytvořit jenom pomocí jednoho konstruktoru bez parametrů. V následujícím kódu a kódu je uveden konstruktor withbezparametrů.<xref:System.Windows.Controls.Page>

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

Rozhraní <xref:System.Windows.Controls.Page> , které se naviguje <xref:System.Windows.Controls.Page> s konstruktorem bez parametrů, je znázorněno v následujícím kódu a kódu.

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

Při kliknutí na tuto <xref:System.Windows.Controls.Page> možnost je navigace <xref:System.Windows.Controls.Page> inicializována vytvořením instance pro přechod k použití konstruktoru <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> bez parametrů a volání metody. <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService.Navigate%2A>přijme odkaz na objekt, který <xref:System.Windows.Navigation.NavigationService> bude přecházet na místo balíčku. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]

#### <a name="programmatic-navigation-with-a-pack-uri"></a>Programová navigace pomocí identifikátoru URI balíčku

Pokud potřebujete sestavit balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] programově (například pouze v době, kdy je možné určit sadu balíčku [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] za běhu) <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> , můžete použít metodu. To je ukázáno v následujícím příkladu.

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>Aktualizace aktuální stránky

A <xref:System.Windows.Controls.Page> není stažen, pokud má stejný balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který je uložen ve <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> vlastnosti. Chcete- [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] li vynutit opětovné stažení aktuální stránky, můžete <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> zavolat metodu, jak je znázorněno v následujícím příkladu.

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

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Vyvolá se v případě, že je navigace zastavena (voláním <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>) nebo když je požadována nová navigace, zatímco probíhá aktuální navigace.

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. Vyvolá se v případě, že dojde k vyvolání chyby při přechodu na požadovaný obsah.

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Nastane, pokud se obsah, na který se přechází, načte a analyzuje a začala vykreslování.

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Vyvolá se v případě, že dojde k zahájení navigace na fragment obsahu.

  - Ihned, pokud je požadovaný fragment v aktuálním obsahu.

  - Po načtení zdrojového obsahu, pokud je požadovaný fragment v jiném obsahu.

Navigační události jsou vyvolány v pořadí, které je znázorněno na následujícím obrázku.

![Graf toku navigace na stránce](./media/navigation-overview/order-of-navigation-events.png "Diagram toku události navigace stránky")

Obecně platí, že <xref:System.Windows.Controls.Page> se o těchto událostech netýká. Je pravděpodobnější, že s nimi má aplikace obavy a z tohoto důvodu tyto události jsou také vyvolány <xref:System.Windows.Application> třídou:

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

<xref:System.Windows.Navigation.NavigationService> Pokaždé<xref:System.Windows.Application> , když vyvolá událost, třída vyvolá odpovídající událost. <xref:System.Windows.Controls.Frame>a <xref:System.Windows.Navigation.NavigationWindow> nabízejí stejné události pro detekci navigace v příslušných oborech.

V některých případech <xref:System.Windows.Controls.Page> mohou být tyto události zajímatelné. <xref:System.Windows.Controls.Page> Může například<xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> zpracovat událost, aby určila, jestli se má zrušit navigace mimo sebe. To je ukázáno v následujícím příkladu.

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

Pokud zaregistrujete obslužnou rutinu s událostí navigace z a <xref:System.Windows.Controls.Page>, jak je uvedeno v předchozím příkladu, je také nutné zrušit registraci obslužné rutiny události. Pokud ne, může docházet k vedlejším účinkům v souvislosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] s tím, jak <xref:System.Windows.Controls.Page> navigace pamatuje navigaci pomocí deníku.

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>Zapamatování navigace pomocí deníku

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]pomocí dvou hromádek si zapamatuje stránky, na které jste přešli: zásobník back-stacku a předávacího zásobníku. Když přejdete <xref:System.Windows.Controls.Page> z aktuálního na nové <xref:System.Windows.Controls.Page> nebo vpřed na stávající <xref:System.Windows.Controls.Page>, bude aktuální <xref:System.Windows.Controls.Page> přidána do *zásobníku back*-and. Když přejdete z aktuálního <xref:System.Windows.Controls.Page> zpátky na předchozí <xref:System.Windows.Controls.Page>, aktuální <xref:System.Windows.Controls.Page> je přidaný do *zásobníku vpřed*. Sada back-Stack, předávací zásobník a funkce pro jejich správu se souhrnně označují jako deník. Každá položka v zásobníku back-stack a předávací zásobník je instancí <xref:System.Windows.Navigation.JournalEntry> třídy a označuje se jako *Položka deníku*.

#### <a name="navigating-the-journal-from-internet-explorer"></a>Navigace v deníku z aplikace Internet Explorer

V koncepčních případech deník funguje stejným způsobem jako tlačítko **zpět** a předávat v [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] rámci. Zobrazují se na následujícím obrázku.

![Tlačítka zpět a] přeposílání (./media/navigation-overview/back-and-forward-navigation.png "Přejděte pomocí tlačítek zpět a vpřed.")

Pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] hostování, které jsou [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]hostovány nástrojem, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]integruje deník do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] navigace. To umožňuje uživatelům navigovat stránky [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pomocí tlačítek **zpět**, **vpřed**a **poslední stránky** v [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]nástroji. Deník není integrován do [!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)] nástroje stejným způsobem [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] jako aplikace nebo Internet Explorer 8. Místo toho [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]vykreslí náhradní navigaci. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]

> [!IMPORTANT]
> V [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]případě, že když uživatel přejde pryč z a zpět [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]do, budou v deníku uchovány pouze položky deníku pro stránky, které nejsou udržované jako aktivní. Diskuzi o tom, jak udržovat stránky aktivní, najdete v části [životnost stránky a deník](#PageLifetime) dále v tomto tématu.

Ve výchozím nastavení [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] je text pro každý <xref:System.Windows.Controls.Page> , který se zobrazí v [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] seznamu **poslední stránky** , v seznamu pro <xref:System.Windows.Controls.Page>. V mnoha případech to není pro uživatele obzvláště smysluplné. Naštěstí můžete změnit text pomocí jedné z následujících možností:

1. Hodnota připojeného `JournalEntry.Name` atributu

2. Hodnota `Page.Title` atributu.

3. Hodnota atributu a pro aktuální <xref:System.Windows.Controls.Page>. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] `Page.WindowTitle`

4. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Pro aktuální<xref:System.Windows.Controls.Page>. (Výchozí)

Pořadí, ve kterém jsou možnosti uvedené, odpovídá pořadí priority pro hledání textu. Pokud `JournalEntry.Name` je například nastaveno, ostatní hodnoty jsou ignorovány.

Následující příklad používá `Page.Title` atribut ke změně textu, který se zobrazí pro položku deníku.

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>Navigace v deníku pomocí WPF

I když uživatel může přejít do deníku pomocí stránek **zpět**, **vpřed**a **nedávno** v aplikaci [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], můžete také procházet deník [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]pomocí deklarativních i programových mechanismů poskytovaných. Jedním z důvodů, jak to provést, je poskytnout [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] na svých stránkách vlastní navigaci.

Můžete deklarativně přidat podporu navigace v deníku pomocí navigačních příkazů, které <xref:System.Windows.Input.NavigationCommands>zveřejňuje. Následující příklad ukazuje, jak použít `BrowseBack` navigační příkaz.

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

Deník můžete programově procházet pomocí jednoho z následujících členů <xref:System.Windows.Navigation.NavigationService> třídy:

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

Deník je také možné manipulovat programově, jak je popsáno v části [zachování stavu obsahu s historií navigace](#RetainingContentStateWithNavigationHistory) dále v tomto tématu.

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>Životnost stránky a deník

[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Vezměte v úvahu několik stránek, které obsahují bohatou obsah, včetně grafiky, animací a médií. Nároky na paměť pro stránky, jako jsou ty, můžou být poměrně velké, zejména pokud se používají video a zvuková média. Vzhledem k tím, že stránky "remembers", na které byly přesměrovány, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] by mohly rychle spotřebovat velkou a znatelné množství paměti.

Z tohoto důvodu je výchozím chováním deníku ukládání <xref:System.Windows.Controls.Page> metadat v jednotlivých položkách deníku, nikoli odkaz <xref:System.Windows.Controls.Page> na objekt. Při přechodu na položku deníku na je použita jeho <xref:System.Windows.Controls.Page> metadata k vytvoření nové instance určeného. <xref:System.Windows.Controls.Page> V důsledku toho má každý z <xref:System.Windows.Controls.Page> nich dobu životnosti, která je znázorněna na následujícím obrázku.

![Doba života stránky](./media/navigation-overview/navigated-page-lifetime.png "To ukazuje dobu života při přechodu stránky.")

I když použití výchozího chování při zakládání do deníku může ušetřit při využití paměti, může se snížit výkon vykreslování na stránce; opětovné vytvoření instance <xref:System.Windows.Controls.Page> může být náročné na čas, zejména v případě, že má hodně obsahu. Pokud potřebujete zachovat <xref:System.Windows.Controls.Page> instanci v deníku, můžete k tomu vykreslit dvěma způsoby. Nejprve můžete programově přejít k <xref:System.Windows.Controls.Page> objektu <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> voláním metody.

Za druhé můžete určit, že [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se má <xref:System.Windows.Controls.Page> v deníku <xref:System.Windows.Controls.Page.KeepAlive%2A> zachovat instance, nastavením vlastnosti `true` (výchozí hodnota je `false`). Jak je znázorněno v následujícím příkladu, lze nastavit <xref:System.Windows.Controls.Page.KeepAlive%2A> deklarativně v kódu.

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

Doba života <xref:System.Windows.Controls.Page> , která je udržována v Alive, je trochu odlišná od z nich. Při prvním spuštění aktivní <xref:System.Windows.Controls.Page> instance se přechází do stavu, ve kterém je instance <xref:System.Windows.Controls.Page> , která není udržována jako aktivní. Vzhledem k tomu, že instance <xref:System.Windows.Controls.Page> je zachována v deníku, není nikdy vytvořena její instance, dokud zůstane v deníku. V důsledku toho, <xref:System.Windows.Controls.Page> Pokud má inicializační logiku, která musí být volána při každém <xref:System.Windows.Controls.Page> přechodu na, měli byste ji přesunout z konstruktoru <xref:System.Windows.FrameworkElement.Loaded> do obslužné rutiny události. Jak <xref:System.Windows.Controls.Page> je znázorněno na následujícím obrázku, <xref:System.Windows.FrameworkElement.Loaded> události <xref:System.Windows.FrameworkElement.Unloaded> a jsou stále vyvolány pokaždé, když dojde k přechodu na nebo z, v uvedeném pořadí.

![Když jsou vyvolány načtené a uvolněné události](./media/navigation-overview/loaded-and-unloaded-events.png "Načtené a uvolněné události jsou vyvolány při přechodu na stránku do a z.")

<xref:System.Windows.Controls.Page> Pokud není udržována naživu, neměli byste dělat ani jednu z následujících možností:

- Uložte na něj odkaz nebo jeho část.

- Zaregistrujte obslužné rutiny událostí s událostmi, které nejsou implementovány.

Při provádění obou z těchto kroků se vytvoří odkazy, <xref:System.Windows.Controls.Page> které vynutí, aby byla zachována v paměti, i když byla odebrána z deníku.

Obecně platí, že byste měli upřednostňovat výchozí <xref:System.Windows.Controls.Page> chování při <xref:System.Windows.Controls.Page> neudržení naživu. Nicméně má dopad na stav, který je popsán v následující části.

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>Zachování stavu obsahu s historií navigace

Pokud není udržována naživu a obsahuje ovládací prvky, které shromažďují data od uživatele, co se stane s daty, pokud uživatel přejde pryč z a zpět <xref:System.Windows.Controls.Page>do? <xref:System.Windows.Controls.Page> V perspektivě uživatelského prostředí by měl uživatel očekávat, že uvidí data, která jste předtím zadali. Vzhledem k tomu, že nová instance <xref:System.Windows.Controls.Page> je vytvořena s každou navigací, jsou ovládací prvky, které shromáždily data, znovu vytvořeny instance a data jsou ztracena.

Tento deník naštěstí poskytuje podporu pro zapamatování dat napříč <xref:System.Windows.Controls.Page> navigacemi, včetně dat ovládacího prvku. Konkrétně záznam deníku pro každé <xref:System.Windows.Controls.Page> funguje jako dočasný kontejner pro přidružený <xref:System.Windows.Controls.Page> stav. Následující kroky popisují, jak se tato podpora používá, <xref:System.Windows.Controls.Page> když je přechod z:

1. Do deníku se přidá položka <xref:System.Windows.Controls.Page> pro aktuální.

2. Stav <xref:System.Windows.Controls.Page> je uložen s položkou deníku pro tuto stránku, která je přidána do zásobníku back.

3. Nový <xref:System.Windows.Controls.Page> přejde na.

Když je stránka <xref:System.Windows.Controls.Page> vrácena zpět na, používá se deník, probíhá následující postup:

1. Vytvoří se instance (hlavní položka deníku pro back-Stack). <xref:System.Windows.Controls.Page>

2. Dojde k aktualizaci se stavem, který byl uložen s položkou deníku <xref:System.Windows.Controls.Page>pro. <xref:System.Windows.Controls.Page>

3. <xref:System.Windows.Controls.Page> Přejde zpět na.

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Tato podpora se automaticky používá v <xref:System.Windows.Controls.Page>případě, že se používají následující ovládací prvky:

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

Pokud nástroj <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.ListBox> používá tyto ovládací prvky, data zadaná do těchto ovládacích prvků jsou zapsána napříč navigacemi, jak je znázorněno na základě **oblíbené barvy** na následujícím obrázku. <xref:System.Windows.Controls.Page>

![Stránka s ovládacími prvky, které zapamatují stav](./media/navigation-overview/data-remembered-across-page-navigations.png "Zadaná data jsou zapamatovatná napříč navigacemi stránky.")

Pokud má jiné ovládací prvky než ty v předchozím seznamu nebo když je stav uložený ve vlastních objektech, musíte napsat kód, který způsobí, že deník bude pamatovat stav napříč <xref:System.Windows.Controls.Page> navigacemi. <xref:System.Windows.Controls.Page>

Pokud potřebujete pamatovat malé části stavu napříč <xref:System.Windows.Controls.Page> navigacemi, můžete použít vlastnosti závislosti (viz <xref:System.Windows.DependencyProperty>) <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> , které jsou nakonfigurovány pomocí příznaku metadata.

Pokud je <xref:System.Windows.Controls.Page> nutné, aby si stav, který si zapamatujete mezi jednotlivými navigacemi, sestává z více částí dat, může být méně náročné na kódování kódu pro zapouzdření <xref:System.Windows.Navigation.IProvideCustomContentState> stavu v jediné třídě a implementaci rozhraní.

Pokud potřebujete procházet různými stavy jediného <xref:System.Windows.Controls.Page>, bez navigace <xref:System.Windows.Controls.Page> od sebe, můžete použít <xref:System.Windows.Navigation.IProvideCustomContentState> a <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.

<a name="Cookies"></a>

### <a name="cookies"></a>Soubory cookie

Jiný způsob, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jakým můžou aplikace ukládat data, jsou soubory cookie, které se vytvářejí, aktualizují a odstraňují <xref:System.Windows.Application.GetCookie%2A> <xref:System.Windows.Application.SetCookie%2A> pomocí metod a. Soubory cookie, které lze vytvořit v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nástroji, jsou stejné soubory cookie, které používají jiné typy webových aplikací; soubory cookie jsou libovolné části dat, které aplikace ukládá v klientském počítači během nebo napříč relacemi aplikací. Data souborů cookie obvykle přebírají formu dvojice název/hodnota v následujícím formátu.

*Název* `=` *Hodnota*

Když jsou data předána do <xref:System.Windows.Application.SetCookie%2A>, společně <xref:System.Uri> s umístěním, pro který by měl být soubor cookie nastaven, je soubor cookie vytvořen v paměti a je k dispozici pouze po dobu trvání aktuální relace aplikace. Tento typ souboru cookie je označován jako *soubor cookie relace*.

Chcete-li uložit soubor cookie mezi relacemi aplikace, je nutné do souboru cookie přidat datum vypršení platnosti v následujícím formátu.

*NÁZEV* `=` *HODNOTA*`; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

Soubor cookie s datem vypršení platnosti je uložen ve složce [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] dočasných internetových souborů aktuální instalace do doby, než vyprší platnost souboru cookie. Takový soubor cookie je známý jako *trvalý soubor cookie* , protože trvá napříč relacemi aplikací.

Můžete načíst relaci i trvalé soubory cookie voláním <xref:System.Windows.Application.GetCookie%2A> metody a <xref:System.Uri> předáním umístění, kde byl <xref:System.Windows.Application.SetCookie%2A> soubor cookie nastaven pomocí metody.

Níže jsou uvedené některé způsoby, jak se soubory cookie podporují [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:

- [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] můžou vytvářet a spravovat soubory cookie.

- Soubory cookie, které jsou vytvořeny [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pomocí, mohou být k dispozici z prohlížeče.

- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]ze stejné domény můžou vytvářet a sdílet soubory cookie.

- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]a stránky HTML ze stejné domény můžou vytvářet a sdílet soubory cookie.

- Soubory cookie jsou odesílány, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] když a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] volné stránky vytvářejí webové požadavky.

- Přístup k souborům cookie [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] mají [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] jenom nejvyšší úroveň i hostovaná v elementech IFRAME.

- Podpora souborů cookie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] v nástroji je stejná pro všechny podporované prohlížeče.

- V [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]nástroji se zásady P3P, které se týkají souborů cookie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], uplatňují, zejména v souvislosti s prvními a třetí stranou [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>Strukturovaná navigace

Pokud potřebujete předat data z jednoho <xref:System.Windows.Controls.Page> do druhé, můžete předat data jako argumenty konstruktoru <xref:System.Windows.Controls.Page>bez parametrů bez parametrů. Všimněte si, že pokud použijete tuto techniku, je nutné <xref:System.Windows.Controls.Page> zachovat Alive. Pokud ne, při příštím přechodu na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozhraní <xref:System.Windows.Controls.Page>znovu vytvoří instanci <xref:System.Windows.Controls.Page> pomocí konstruktoru bez parametrů.

<xref:System.Windows.Controls.Page> Případně můžete implementovat vlastnosti, které jsou nastaveny s daty, která je třeba předat. Věci se projeví, když <xref:System.Windows.Controls.Page> ale potřebuje předat data zpátky do rozhraní <xref:System.Windows.Controls.Page> , které na něj přešlo. Problémem je to, že navigace netivně podporuje mechanismy pro zajištění, že <xref:System.Windows.Controls.Page> se vrátí do po přechodu z. Navigace v podstatě nepodporuje sémantiku volání a vracení. Chcete-li tento problém [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vyřešit, <xref:System.Windows.Navigation.PageFunction%601> poskytuje třídu, kterou můžete <xref:System.Windows.Controls.Page> použít k zajištění, že se vrátí do předvídatelného a strukturovaného způsobu. Další informace najdete v tématu [Přehled strukturované navigace](structured-navigation-overview.md).

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>Třída objektu NavigationWindow

K tomuto okamžiku jste viděli škálu navigačních služeb, které nejpravděpodobněji použijete k vytváření aplikací s naviguje obsahem. Tyto služby byly projednány v kontextu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], i když nejsou omezeny na. [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] Moderní operační systémy a aplikace Windows využívají možnosti prohlížeče moderních uživatelů k začlenění navigace ve stylu prohlížeče do samostatných aplikací. Mezi běžné příklady patří:

- **Tezaurus Word**: Navigace – možnosti aplikace Word

- **Průzkumník souborů**: Navigace v souborech a složkách

- **Průvodci**: Rozdělení složitého úkolu na více stránek, mezi kterými lze přejít. Příkladem je Průvodce součástmi systému Windows, který zpracovává přidávání a odebírání funkcí systému Windows.

Chcete-li zahrnout navigaci ve stylu prohlížeče do samostatných aplikací, můžete použít <xref:System.Windows.Navigation.NavigationWindow> třídu. <xref:System.Windows.Navigation.NavigationWindow>je odvozen z <xref:System.Windows.Window> a rozšiřuje se stejnou podporou pro navigaci, která [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] poskytuje. Můžete použít <xref:System.Windows.Navigation.NavigationWindow> buď jako hlavní okno samostatné aplikace, nebo jako sekundární okno, jako je například dialogové okno.

Chcete-li <xref:System.Windows.Navigation.NavigationWindow>implementovat třídu, stejně jako u většiny tříd nejvyšší [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] úrovně<xref:System.Windows.Window>v <xref:System.Windows.Controls.Page>(, a tak dále), použijte kombinaci značek a kódu na pozadí. To je ukázáno v následujícím příkladu.

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

Tento kód vytvoří objekt <xref:System.Windows.Navigation.NavigationWindow> , který při <xref:System.Windows.Navigation.NavigationWindow> otevření automaticky naviguje <xref:System.Windows.Controls.Page> na (Domovská stránka. XAML). Pokud je hlavním oknem aplikace, můžete jej spustit `StartupUri` pomocí atributu. <xref:System.Windows.Navigation.NavigationWindow> Zobrazuje se v následujícím kódu.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

Následující obrázek ukazuje <xref:System.Windows.Navigation.NavigationWindow> hlavní okno samostatné aplikace.

![Hlavní okno](./media/navigation-overview/navigation-window-as-main-window.png "Navigační okno jako hlavní okno")

Z obrázku vidíte, že <xref:System.Windows.Navigation.NavigationWindow> má název, a to i <xref:System.Windows.Navigation.NavigationWindow> v případě, že nebyl nastaven v kódu implementace z předchozího příkladu. Místo toho je název nastaven pomocí <xref:System.Windows.Controls.Page.WindowTitle%2A> vlastnosti, která je uvedena v následujícím kódu.

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

Nastavení vlastností <xref:System.Windows.Controls.Page.WindowHeight%2A> <xref:System.Windows.Navigation.NavigationWindow>a má vliv také na. <xref:System.Windows.Controls.Page.WindowWidth%2A>

Obvykle implementujete vlastní <xref:System.Windows.Navigation.NavigationWindow> , pokud potřebujete přizpůsobit jeho chování nebo jeho vzhled. Pokud ani to neuděláte, můžete použít zástupce. Pokud [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zadáte sadu <xref:System.Windows.Controls.Page> jako <xref:System.Windows.Application.StartupUri%2A> vsamostatné<xref:System.Windows.Controls.Page>aplikaci, <xref:System.Windows.Application> aplikace automaticky vytvoří hostitele pro.<xref:System.Windows.Navigation.NavigationWindow> Následující kód ukazuje, jak to povolit.

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

Pokud chcete <xref:System.Windows.Navigation.NavigationWindow>, aby se sekundární okno aplikace, jako je dialogové okno, používalo, můžete k jeho otevření použít kód v následujícím příkladu.

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

Výsledek je znázorněn na následujícím obrázku.

![Dialogové okno](./media/navigation-overview/navigation-window-as-dialog-box.png "Navigační okno jako dialogové okno")

Jak <xref:System.Windows.Navigation.NavigationWindow> vidíte, zobrazí tlačítka pro [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]zobrazení a předávání na **pozadí** , které uživatelům umožňují procházet deník. Tato tlačítka poskytují stejné uživatelské prostředí, jak je znázorněno na následujícím obrázku.

![Tlačítka zpět a přeposílání v objektu NavigationWindow](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "Tlačítka zpět a přeposílání v navigačním okně")

Pokud vaše stránky poskytují podporu a uživatelské rozhraní **pro** navigaci v deníku, můžete skrýt <xref:System.Windows.Navigation.NavigationWindow> tlačítka **zpět** a přeslat zobrazená pomocí nastavením hodnoty <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> vlastnosti na `false`.

Alternativně můžete použít podporu vlastního nastavení v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nástroji k [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nahrazení <xref:System.Windows.Navigation.NavigationWindow> samotného.

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Třída Frame

Prohlížeč i <xref:System.Windows.Navigation.NavigationWindow> je systém Windows, který hostuje naviguje obsah. V některých případech mají aplikace obsah, který není nutné hostovat do celého okna. Místo toho se takový obsah bude hostovat v jiném obsahu. Obsah naviguje můžete vložit do dalšího obsahu pomocí <xref:System.Windows.Controls.Frame> třídy. <xref:System.Windows.Controls.Frame>poskytuje stejnou podporu jako <xref:System.Windows.Navigation.NavigationWindow> a. [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]

Následující příklad ukazuje, jak přidat objekt <xref:System.Windows.Controls.Frame> <xref:System.Windows.Controls.Page> k `Frame` deklarativnímu pomocí elementu.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

Tento `Source` kód nastaví atribut [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] `Frame` elementu s<xref:System.Windows.Controls.Frame>balíčkem , který by měl zpočátku přejít na. <xref:System.Windows.Controls.Page> Následující obrázek ukazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] <xref:System.Windows.Controls.Page> s objektem, který má <xref:System.Windows.Controls.Frame> přecházení mezi několika stránkami.

![Rámec, který přešel mezi několika stránkami](./media/navigation-overview/frame-navigation-between-multiple-pages.png "Tím se zobrazí navigace mezi několika stránkami.")

Nemusíte používat <xref:System.Windows.Controls.Frame> jenom v obsahu <xref:System.Windows.Controls.Page>. Také je běžné hostovat <xref:System.Windows.Controls.Frame> v obsahu a. <xref:System.Windows.Window>

Ve výchozím nastavení <xref:System.Windows.Controls.Frame> používá nástroj pouze vlastní deník při absenci jiného deníku. <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow> [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] <xref:System.Windows.Controls.Frame> [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]Pokud je součástí obsahu, který je hostován v rámci nebo, používá deník, který patří do nebo. <xref:System.Windows.Controls.Frame> V <xref:System.Windows.Controls.Frame> některých případech může být někdy nutné, abyste byli odpovědni za svůj vlastní deník. Jedním z důvodů, jak to udělat, je povolit navigaci v deníku na stránkách hostovaných pomocí <xref:System.Windows.Controls.Frame>. To je znázorněno na následujícím obrázku.

![Diagram rámečku a stránky](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "Tím se zobrazí navigace v deníku na stránkách hostovaných snímkem.")

<xref:System.Windows.Controls.Frame> V takovém případě můžete nakonfigurovat tak, aby používal vlastní deník, <xref:System.Windows.Controls.Frame.JournalOwnership%2A> nastavením vlastnosti <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>na. Zobrazuje se v následujícím kódu.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

Následující obrázek znázorňuje účinek přechodu v rámci <xref:System.Windows.Controls.Frame> , který používá vlastní deník.

![Rámec, který používá vlastní deník](./media/navigation-overview/frame-uses-its-own-journal.png "To ukazuje účinek přechodu v rámci rámce, který používá vlastní deník.")

Všimněte si, že položky deníku jsou zobrazeny [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame>v navigaci v místo pomocí [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)].

> [!NOTE]
> Pokud je součástí obsahu, který je hostován <xref:System.Windows.Window>v, <xref:System.Windows.Controls.Frame> používá vlastní deník a v důsledku toho zobrazí svou vlastní navigaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Controls.Frame>

<xref:System.Windows.Controls.Frame> Pokud prostředí uživatele vyžaduje, aby poskytovalo vlastní deník bez zobrazení navigace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], můžete navigaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> skrýt nastavením na <xref:System.Windows.Visibility.Hidden>. Zobrazuje se v následujícím kódu.

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>Hostitelé navigace

<xref:System.Windows.Controls.Frame>a <xref:System.Windows.Navigation.NavigationWindow> jsou třídy, které jsou známé jako hostitelé navigace. *Navigační hostitel* je třída, která může přejít na obsah a zobrazit ho. K tomu každý navigační hostitel používá vlastní <xref:System.Windows.Navigation.NavigationService> a deník. Základní konstrukce pro navigační hostitele je znázorněna na následujícím obrázku.

![Navigátorové diagramy](./media/navigation-overview/navigation-host-construction.png "Základní konstrukce pro navigačního hostitele")

V podstatě to umožňuje <xref:System.Windows.Navigation.NavigationWindow> a <xref:System.Windows.Controls.Frame> poskytnout [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] stejnou podporu navigace, kterou poskytuje, pokud je hostována v prohlížeči.

Kromě použití <xref:System.Windows.Navigation.NavigationService> a deníku, hostitelé navigace implementují stejné členy, <xref:System.Windows.Navigation.NavigationService> které implementují. To je znázorněno na následujícím obrázku.

![Deník v rámečku a v objektu NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "Navigační okno a rámec")

To vám umožní naprogramovat podporu navigace přímo proti nim. Můžete to vzít v úvahu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame> <xref:System.Windows.Window>, pokud potřebujete zadat vlastní navigaci pro, která je hostována v. Oba typy navíc implementují další členy související s navigací, včetně `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) a `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), což vám umožní vytvořit výčet položek deníku zpátky. zásobník zásobníku a vpřed, v uvedeném pořadí.

Jak bylo zmíněno dříve, více než jeden deník může existovat v rámci aplikace. Následující obrázek uvádí příklad, kdy k tomu může dojít.

![Několik deníků v rámci jedné aplikace](./media/navigation-overview/multiple-journals-in-one-application.png "Toto je příklad více než jednoho deníku v aplikaci.")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>Přechod na obsah jiný než XAML stránky

V celém tomto tématu <xref:System.Windows.Controls.Page> a balíčku [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] byly použity k předvedení různých možností navigace pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Nicméně, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] který je zkompilován do aplikace, není jediným typem obsahu, na který lze přejít, a balíček není jediným způsobem, jak identifikovat obsah. <xref:System.Windows.Controls.Page>

Jak ukazuje Tato část, můžete také přejít na volné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, soubory HTML a objekty.

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>Navigace do volných souborů XAML

Volný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je soubor s následujícími charakteristikami:

- Obsahuje pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (to znamená žádný kód).

- Má odpovídající deklaraci oboru názvů.

- Má příponu názvu souboru. XAML.

Zvažte například následující obsah, který je uložen jako volný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor Person. XAML.

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

Když dvakrát kliknete na soubor, otevře se prohlížeč a přejde na něj a zobrazí se jeho obsah. To je znázorněno na následujícím obrázku.

![Zobrazení obsahu v souboru Person. XAML](./media/navigation-overview/contents-of-person-xaml-file.png "Zobrazuje obsah souboru Person. XAML.")

Můžete zobrazit volný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor z následujících možností:

- Web na místním počítači, v intranetu nebo na internetu.

- [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] Sdílená složka.

- Místní disk.

Do oblíbených [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] položek v prohlížeči se dá přidat volný soubor, nebo se může jednat o domovskou stránku prohlížeče.

> [!NOTE]
> Další informace o publikování a spouštění volných [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránek naleznete v tématu [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).

Jedním z omezení s ohledem na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] volné je, že můžete hostovat jenom obsah, který je bezpečný pro běh v částečném vztahu důvěryhodnosti. Například `Window` nemůže být kořenovým prvkem volného [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru. Další informace najdete v tématu [zabezpečení částečné důvěryhodnosti WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>Navigace do souborů HTML pomocí rámce

Jak byste mohli očekávat, můžete také přejít na HTML. Stačí pouze zadat [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který používá schéma HTTP. Následující [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad<xref:System.Windows.Controls.Frame> ukazuje, že přejde na stránku HTML.

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

Navigace na HTML vyžaduje zvláštní oprávnění. Například nemůžete přejít z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] na, který je spuštěný v izolovaném prostoru zabezpečení zóny Internet Zone. Další informace najdete v tématu [zabezpečení částečné důvěryhodnosti WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Navigace do souborů HTML pomocí ovládacího prvku WebBrowser

<xref:System.Windows.Controls.WebBrowser> Ovládací prvek podporuje hostování dokumentů HTML, navigaci a spolupráci pomocí skriptu nebo spravovaného kódu. Podrobné informace <xref:System.Windows.Controls.WebBrowser> o ovládacím prvku naleznete v tématu <xref:System.Windows.Controls.WebBrowser>.

Podobně <xref:System.Windows.Controls.Frame>, přechod na HTML pomocí <xref:System.Windows.Controls.WebBrowser> vyžaduje zvláštní oprávnění. Například z aplikace s částečným vztahem důvěryhodnosti můžete přejít pouze k HTML, které je umístěno na webu původu. Další informace najdete v tématu [zabezpečení částečné důvěryhodnosti WPF](../wpf-partial-trust-security.md).

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>Navigace na vlastní objekty

Pokud máte data, která jsou uložená jako vlastní objekty, jedním ze způsobů, jak tato data zobrazit, je <xref:System.Windows.Controls.Page> vytvoření obsahu s obsahem vázaného na tyto objekty (viz [Přehled datové vazby](../data/data-binding-overview.md)). Pokud nepotřebujete pro zobrazení objektů režii vytváření celé stránky, můžete místo toho přejít přímo na ně.

`Person` Zvažte třídu, která je implementována v následujícím kódu.

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

Pro přechod na ni zavoláte <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> metodu, jak je znázorněno v následujícím kódu.

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

Výsledek je znázorněn na následujícím obrázku.

![Stránka, která naviguje na třídu](./media/navigation-overview/page-navigates-to-an-object.png "Toto je příklad stránky, která naviguje k objektu.")

Z tohoto obrázku vidíte, že se nezobrazí nic užitečného. Ve skutečnosti hodnota, která je zobrazena, je návratovou hodnotou `ToString` metody objektu **Person** ; ve výchozím nastavení je to jediná hodnota, kterou [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] lze použít k reprezentaci objektu. `ToString` Metodu můžete přepsat tak, aby vracela smysluplnější informace, i když bude stále pouze řetězcová hodnota. Jedna z možností, kterou můžete použít, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je použít možnosti prezentace v aplikaci, která využívá šablonu dat. Můžete implementovat šablonu dat, která [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] může být přidružena k objektu určitého typu. Následující kód ukazuje datovou šablonu pro `Person` objekt.

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

Zde je šablona dat přidružena `Person` k typu `x:Type` pomocí rozšíření označení v `DataType` atributu. Šablona dat potom vytvoří vazby `TextBlock` elementů (viz <xref:System.Windows.Controls.TextBlock>) `Person` na vlastnosti třídy. Následující obrázek znázorňuje aktualizovaný vzhled `Person` objektu.

![Přechod na třídu, která má šablonu dat](./media/navigation-overview/navigating-to-a-class.png "Přechod na třídu, která má datovou šablonu.")

Výhodou této techniky je konzistence, kterou získáte pomocí možnosti opětovného použití šablony dat k zobrazení objektů konzistentně kdekoli v aplikaci.

Další informace o datových šablonách najdete v tématu [Přehled šablonování dat](../data/data-templating-overview.md).

<a name="Security"></a>

## <a name="security"></a>Zabezpečení

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Podpora navigace umožňuje [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] přejít na celé Internetu a umožňuje aplikacím hostovat obsah třetích stran. Pokud chcete chránit aplikace i uživatele před škodlivým chováním, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje celou řadu funkcí zabezpečení, které jsou [](../security-wpf.md) popsány v tématu zabezpečení a [částečně důvěryhodné zabezpečení WPF](../wpf-partial-trust-security.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Přehled správy aplikací](application-management-overview.md)
- [Sbalení URI v technologii WPF](pack-uris-in-wpf.md)
- [Přehled strukturované navigace](structured-navigation-overview.md)
- [Přehled topologií navigace](navigation-topologies-overview.md)
- [Témata s postupy](navigation-how-to-topics.md)
- [Nasazení aplikace WPF](deploying-a-wpf-application-wpf.md)
