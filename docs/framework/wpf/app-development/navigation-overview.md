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
ms.openlocfilehash: 7636a7d9a100d0df95f7d5462672819624ba52a4
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679967"
---
# <a name="navigation-overview"></a>Přehled navigace
Windows Presentation Foundation (WPF) podporuje stylu prohlížeče navigace, který je možné do dvou typů aplikací: samostatné aplikace a [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. K balíčku obsahu pro navigaci [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje <xref:System.Windows.Controls.Page> třídy. Můžete přejít z jednoho <xref:System.Windows.Controls.Page> do jiného deklarativně pomocí <xref:System.Windows.Documents.Hyperlink>, nebo prostřednictvím kódu programu, s použitím <xref:System.Windows.Navigation.NavigationService>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] používá deník pamatovat stránky, které přešli z a chcete přejít zpátky k sobě.  
  
 <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>, a deníku tvoří jádro navigace podporu, kterou nabízí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Tento přehled popisuje tyto funkce podrobně před zahrnující podporu Pokročilá navigace, která zahrnuje navigaci na dojde ke ztrátě [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubory, [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] soubory a objekty.  
  
> [!NOTE]
>  V tomto tématu se pojem "prohlížeče" představuje pouze do prohlížečů, které můžete hostovat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, které aktuálně obsahuje [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] a Firefox. Pokud konkrétní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] funkce jsou podporovány pouze určitého prohlížeče, se označuje verzi prohlížeče.  
   
     
## <a name="navigation-in-wpf-applications"></a>Navigace v aplikacích WPF  
 Toto téma obsahuje přehled možností klíče navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Tyto možnosti jsou k dispozici pro samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], i když je toto téma představuje v rámci [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
> [!NOTE]
>  Toto téma se nezabývá jak sestavit a nasadit [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Další informace o [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], naleznete v tématu [přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).  
  
 Tato část popisuje a ukazuje následující aspekty navigace:  
  
-   [Implementace stránky](#CreatingAXAMLPage)  
  
-   [Konfigurace úvodní stránky](#Configuring_a_Start_Page)  
  
-   [Konfigurace názvu, šířku a výšku okna hostitele](#ConfiguringAXAMLPage)  
  
-   [Navigace na hypertextový odkaz](#NavigatingBetweenXAMLPages)  
  
-   [Procházení fragmentů](#FragmentNavigation)  
  
-   [Služba navigace](#NavigationService)  
  
-   [Programově řízená navigace ve službě navigace](#Programmatic_Navigation_with_the_Navigation_Service)  
  
-   [Doba života navigace](#Navigation_Lifetime)  
  
-   [Zapamatování navigace pomocí deníku](#NavigationHistory)  
  
-   [Životní cyklus stránky a deníku](#PageLifetime)  
  
-   [Zachování stavu obsahu s využitím historii navigace](#RetainingContentStateWithNavigationHistory)  
  
-   [Soubory cookie](#Cookies)  
  
-   [Strukturované navigace](#Structured_Navigation)  
  
<a name="CreatingAXAMLPage"></a>   
### <a name="implementing-a-page"></a>Implementace stránky  
 V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], můžete přejít na několik typů obsahu, které obsahují objekty rozhraní .NET Framework, vlastních objektů, hodnoty výčtu, uživatelské ovládací prvky, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, a [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] soubory. Nicméně, zjistíte, že nejvíce běžné a pohodlný způsob, jak obsah balíčku je pomocí <xref:System.Windows.Controls.Page>. Kromě toho <xref:System.Windows.Controls.Page> implementuje funkce specifické pro navigaci vylepšovat jejich výskytu a zjednodušení vývoje.  
  
 Pomocí <xref:System.Windows.Controls.Page>, můžete implementovat deklarativně navigaci stránce [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu pomocí značek následujícím postupem.  
  
 [!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]  
  
 A <xref:System.Windows.Controls.Page> , která je implementovaná v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek má `Page` jako jeho kořenový element a vyžaduje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] deklarace oboru názvů. `Page` Prvek obsahuje obsah, který chcete k procházení a zobrazení. Přidat obsah tak, že nastavíte `Page.Content` vlastnost elementu, jak je znázorněno v následujícím kódu.  
  
 [!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]  
  
 `Page.Content` může obsahovat pouze jeden podřízený element. v předchozím příkladu je obsah jeden řetězec "Hello, stránky!" V praxi, obvykle použijete rozložení ovládacího prvku jako podřízeného prvku (viz [rozložení](../advanced/layout.md)) obsahovala a vytváření obsahu.  
  
 Podřízené prvky `Page` element jsou považovány za obsah <xref:System.Windows.Controls.Page> a v důsledku toho není nutné použít explicitní `Page.Content` deklarace. Následující kód je deklarativní odpovídá předchozí ukázce.  
  
 [!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]  
  
 V takovém případě `Page.Content` se automaticky nastaví pomocí podřízených elementů `Page` elementu. Další informace najdete v tématu [Model obsahu WPF](../controls/wpf-content-model.md).  
  
 Pouze značky <xref:System.Windows.Controls.Page> je užitečné při zobrazování obsahu. Ale <xref:System.Windows.Controls.Page> můžete také ovládací prvky zobrazení, které umožňují uživatelům interakci s stránky a můžou reagovat na interakci uživatele tak, že zpracování událostí a volání aplikací logiky. Interaktivní <xref:System.Windows.Controls.Page> je implementovaný s využitím kombinace značek a kódu, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
 [!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]  
  
 Pokud chcete povolit souboru označení a použití modelu code-behind soubor spolupráce, následující konfigurace je potřeba:  
  
-   V kódu `Page` musí obsahovat element `x:Class` atribut. Když je aplikace sestavená, existenci `x:Class` ve značkách soubor způsobí, že [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] k vytvoření `partial` třídu odvozenou od <xref:System.Windows.Controls.Page> a má název, který je určen `x:Class` atribut. To vyžaduje přidání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklarace oboru názvů pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schématu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Vygenerovaný `partial` implementuje třída `InitializeComponent`, která je volána k registraci události a nastavte vlastnosti, které jsou implementovány v kódu.  
  
-   V modelu code-behind, musí být třída `partial` třídy se stejným názvem, která je zadána `x:Class` atribut v kódu který musí být odvozen od <xref:System.Windows.Controls.Page>. To umožňuje použití modelu code-behind souboru má být spojen s `partial` třídu, která se vygeneruje pro označovacího souboru, když je aplikace sestavená (viz [sestavení aplikace WPF](building-a-wpf-application-wpf.md)).  
  
-   V modelu code-behind <xref:System.Windows.Controls.Page> třída musí implementovat konstruktor, který volá `InitializeComponent` metody. `InitializeComponent` je implementován ve značce vygenerovaný soubor `partial` třídy k registraci události a nastavte vlastnosti, které jsou definovány v kódu.  
  
> [!NOTE]
>  Když přidáte nový <xref:System.Windows.Controls.Page> do projektu pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Controls.Page> je implementováno pomocí značek a kódu, a obsahuje nezbytnou konfiguraci pro vytvoření přidružení mezi značky a modelu code-behind soubory jako najdete tady.  
  
 Jakmile budete mít <xref:System.Windows.Controls.Page>, můžete přejít k němu. Chcete-li určit první <xref:System.Windows.Controls.Page> , že aplikace přejde na, budete muset nakonfigurovat počáteční <xref:System.Windows.Controls.Page>.  
  
<a name="Configuring_a_Start_Page"></a>   
### <a name="configuring-a-start-page"></a>Konfigurace úvodní stránky  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] vyžadovat určité množství aplikací infrastruktury hostované v prohlížeči. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], <xref:System.Windows.Application> třídy je součástí definice aplikace, která vytvoří infrastrukturu požadovanou aplikaci (viz [přehled správy aplikací](application-management-overview.md)).  
  
 Definice aplikace je obvykle implementovány pomocí značek a kódu, s označovacího souboru, který je nakonfigurovaný jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` položky. Tady je pro definici aplikace [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
 [!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
 [!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]  
  
 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Jeho definice aplikace můžete použít k určení počáteční <xref:System.Windows.Controls.Page>, což je <xref:System.Windows.Controls.Page> , které se vyplní automaticky, když [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] spuštění. To provedete tak, že nastavíte <xref:System.Windows.Application.StartupUri%2A> vlastnost s [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] pro požadovaný <xref:System.Windows.Controls.Page>.  
  
> [!NOTE]
>  Ve většině případů <xref:System.Windows.Controls.Page> je zkompilován nebo nasazována s aplikací. V těchto případech [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který identifikuje <xref:System.Windows.Controls.Page> je sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], což je [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který odpovídá *pack* schéma. Balíček [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] jsou popsány dále v [identifikátory Pack URI v subsystému WPF](pack-uris-in-wpf.md). Můžete také přejít na obsah pomocí schéma protokolu http, které jsou popsány níže.  
  
 Můžete nastavit <xref:System.Windows.Application.StartupUri%2A> deklarativně v kódu, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 V tomto příkladu `StartupUri` atribut je nastaven s relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , který identifikuje HomePage.xaml. Když [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je spuštěn, HomePage.xaml automaticky přejde a zobrazit. Tento postup je znázorněn v následujícím obrázku, který ukazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , který byl spuštěn z webového serveru.  
  
 ![Stránka XBAP](./media/navigation-overview/xbap-launched-from-a-web-server.png "zobrazí XBAP, který spustí z webového serveru.")  
  
> [!NOTE]
>  Další informace týkající se vývoje a nasazování [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], naleznete v tématu [přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md) a [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).  
  
<a name="ConfiguringAXAMLPage"></a>   
### <a name="configuring-the-host-windows-title-width-and-height"></a>Konfigurace názvu, šířku a výšku okna hostitele  
 Jedna věc, možná jste si všimli z předchozí obrázek je skutečnost, že název v prohlížeči i na kartě panelu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Kromě toho dlouho, není název atraktivní ani informativní. Z tohoto důvodu <xref:System.Windows.Controls.Page> nabízí způsob, jak můžete změnit název tak, že nastavíte <xref:System.Windows.Controls.Page.WindowTitle%2A> vlastnost. Kromě toho můžete nakonfigurovat šířku a výšku okna prohlížeče tak, že nastavíte <xref:System.Windows.Controls.Page.WindowWidth%2A> a <xref:System.Windows.Controls.Page.WindowHeight%2A>v uvedeném pořadí.  
  
 <xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page.WindowHeight%2A> lze nastavit deklarací v kódu, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 Výsledek je znázorněno na následujícím obrázku.  
  
 ![Název okna, výška a šířka](./media/navigation-overview/window-title-width-height.png "zobrazí záhlaví okna, výšku a šířku, můžete nakonfigurovat.")  
  
<a name="NavigatingBetweenXAMLPages"></a>   
### <a name="hyperlink-navigation"></a>Navigace na hypertextový odkaz  
 Typické [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] se skládá z několika stránek. Nejjednodušší způsob, jak přecházejí z jedné stránky na jiný, je použít <xref:System.Windows.Documents.Hyperlink>. Deklarativně přidáte <xref:System.Windows.Documents.Hyperlink> k <xref:System.Windows.Controls.Page> pomocí `Hyperlink` element, který je znázorněno v následujícím kódu.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 A `Hyperlink` element vyžaduje následující:  
  
-   Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> přejít na, podle `NavigateUri` atribut.  
  
-   Obsah, může uživatel klepnout na zahájení navigace, jako je například textu a obrázků (pro obsah, který `Hyperlink` element může obsahovat, naleznete v tématu <xref:System.Windows.Documents.Hyperlink>).  
  
 Následující obrázek ukazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] s <xref:System.Windows.Controls.Page> , který má <xref:System.Windows.Documents.Hyperlink>.  
  
 ![Stránka s hypertextovým odkazem](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "zobrazí XBAP, který se stránkou s hypertextovým odkazem.")  
  
 Dle očekávání, kliknutím <xref:System.Windows.Documents.Hyperlink> způsobí, že [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] přejít na <xref:System.Windows.Controls.Page> , který je identifikován `NavigateUri` atribut. Kromě toho [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] přidá záznam pro předchozí <xref:System.Windows.Controls.Page> do seznamu poslední stránky v [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. To je ukázáno na následujícím obrázku.  
  
 ![Tlačítka Zpět a vpřed](./media/navigation-overview/back-and-forward-navigation.png "Navigovat pomocí tlačítka vpřed a zpět.")  
  
 A také podpora navigace z jednoho <xref:System.Windows.Controls.Page> do druhého, <xref:System.Windows.Documents.Hyperlink> také podporuje fragment navigace.  
  
<a name="FragmentNavigation"></a>   
### <a name="fragment-navigation"></a>Procházení fragmentů  
 *Fragment navigace* je navigace na fragment obsahu buď aktuální <xref:System.Windows.Controls.Page> nebo jiném <xref:System.Windows.Controls.Page>. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], fragment obsahu je obsah, který je obsažen v prvek s názvem. Pojmenovaný prvek je prvek, který má jeho `Name` sadu atributů. Následující kód ukazuje pojmenovaná `TextBlock` element, který obsahuje fragment obsahu.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]  
  
 Pro <xref:System.Windows.Documents.Hyperlink> navigace na fragment obsahu `NavigateUri` atribut musí obsahovat následující:  
  
-   [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> s obsahu fragmentu přejděte k položce.  
  
-   Znak "#".  
  
-   Název elementu na <xref:System.Windows.Controls.Page> , který obsahuje obsahu fragmentu.  
  
 Fragment [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] má následující formát.  
  
 *PageURI* `#` *ElementName*  
  
 Následující příklad ukazuje, `Hyperlink` , který je nakonfigurovaný pro navigaci na fragment obsahu.  
  
 [!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]  
  
> [!NOTE]
>  Tato část popisuje výchozí implementace navigace fragment v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] také umožňuje implementovat vlastní schéma fragment navigace, která částečně vyžaduje zpracování <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> událostí.  
  
> [!IMPORTANT]
>  Můžete přejít na fragmenty v dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky (pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory s `Page` jako kořenový element) pouze v případě, že na stránkách můžete procházet přes [!INCLUDE[TLA2#tla_http](../../../../includes/tla2sharptla-http-md.md)].  
>   
>  Nicméně dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránku můžete přejít na své vlastní fragmenty.  
  
<a name="NavigationService"></a>   
### <a name="navigation-service"></a>Služba navigace  
 Zatímco <xref:System.Windows.Documents.Hyperlink> umožňuje uživateli iniciovat navigaci na konkrétní <xref:System.Windows.Controls.Page>, provádí práci při vyhledávání a stahování stránky <xref:System.Windows.Navigation.NavigationService> třídy. V podstatě <xref:System.Windows.Navigation.NavigationService> poskytuje možnost zpracování požadavku na navigační jménem kód klienta, jako <xref:System.Windows.Documents.Hyperlink>. Kromě toho <xref:System.Windows.Navigation.NavigationService> implementuje vyšší úrovně podpory pro sledování a vliv na žádost o navigaci.  
  
 Když <xref:System.Windows.Documents.Hyperlink> kliknutí na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] volání <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> vyhledejte a stáhněte si <xref:System.Windows.Controls.Page> na zadaný balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Na stažený <xref:System.Windows.Controls.Page> je převést na strom objektů, jejichž kořenový objekt je instancí na stažený <xref:System.Windows.Controls.Page>. Odkaz na kořenovém adresáři <xref:System.Windows.Controls.Page> objekt uložen v <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> vlastnost. Této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro obsah, na kterou se přejde je uložený ve <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> vlastnost, zatímco <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> ukládá této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] poslední stránky, na kterou se přejde.  
  
> [!NOTE]
>  Je možné, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace mít více než jednu aktivní <xref:System.Windows.Navigation.NavigationService>. Další informace najdete v tématu [hostitel pro navigaci](#Navigation_Hosts) dále v tomto tématu.  
  
<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>   
### <a name="programmatic-navigation-with-the-navigation-service"></a>Programově řízená navigace ve službě navigace  
 Nemusíte vědět o <xref:System.Windows.Navigation.NavigationService> Pokud navigace je implementovaná deklarativně v kódu pomocí <xref:System.Windows.Documents.Hyperlink>, protože <xref:System.Windows.Documents.Hyperlink> používá <xref:System.Windows.Navigation.NavigationService> vaším jménem. To znamená, že tak dlouho, dokud buď přímé nebo nepřímé nadřazeného člena <xref:System.Windows.Documents.Hyperlink> hostitel navigace (naleznete v tématu [hostitel pro navigaci](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> budou moci najít a použití služby navigace navigace hostitele ke zpracování požadavek pro navigaci.  
  
 Nicméně existují situace, když budete chtít použít <xref:System.Windows.Navigation.NavigationService> přímo, včetně následujících:  
  
-   Když budete muset vytvořit instanci <xref:System.Windows.Controls.Page> pomocí jiného než výchozího konstruktoru.  
  
-   Když budete muset nastavit vlastnosti <xref:System.Windows.Controls.Page> předtím, než přejdete k němu.  
  
-   Když <xref:System.Windows.Controls.Page> , potřebuje k přejde určen pouze v době běhu.  
  
 V těchto situacích, budete muset psát kód chcete programově zahájit navigace pomocí volání <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metodu <xref:System.Windows.Navigation.NavigationService> objektu. Která vyžaduje odkaz na získávání <xref:System.Windows.Navigation.NavigationService>.  
  
#### <a name="getting-a-reference-to-the-navigationservice"></a>Získání odkazu na Stoploading  
 Z důvodů, které jsou popsané v [hostitel pro navigaci](#Navigation_Hosts) části, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace může mít více než jeden <xref:System.Windows.Navigation.NavigationService>. To znamená, že váš kód potřebuje způsob, jak vyhledat <xref:System.Windows.Navigation.NavigationService>, což je obvykle <xref:System.Windows.Navigation.NavigationService> , která přejde do aktuální <xref:System.Windows.Controls.Page>. Můžete získat odkaz na <xref:System.Windows.Navigation.NavigationService> voláním `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> metody. Chcete-li získat <xref:System.Windows.Navigation.NavigationService> , která přejde na konkrétní <xref:System.Windows.Controls.Page>, předáte odkaz na <xref:System.Windows.Controls.Page> jako argument <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> – metoda. Následující kód ukazuje, jak získat <xref:System.Windows.Navigation.NavigationService> pro aktuální <xref:System.Windows.Controls.Page>.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]  
  
 Jako zástupce pro hledání <xref:System.Windows.Navigation.NavigationService> pro <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> implementuje <xref:System.Windows.Controls.Page.NavigationService%2A> vlastnost. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Page> můžete získat pouze odkaz na jeho <xref:System.Windows.Navigation.NavigationService> při <xref:System.Windows.Controls.Page> vyvolá <xref:System.Windows.FrameworkElement.Loaded> událostí.  
  
#### <a name="programmatic-navigation-to-a-page-object"></a>Programově řízená navigace do objektu Page  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Navigation.NavigationService> prostřednictvím kódu programu přejděte k položce <xref:System.Windows.Controls.Page>. Programově řízená navigace je vyžadován, protože <xref:System.Windows.Controls.Page> , který je právě přejde pouze dá vytvořit instance pomocí jednoho, jiné než výchozí konstruktor. <xref:System.Windows.Controls.Page> Pomocí jiného než výchozího konstruktoru je znázorněno v následujících značek a kódu.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
 [!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]  
  
 <xref:System.Windows.Controls.Page> , Která přejde <xref:System.Windows.Controls.Page> pomocí jiného než výchozího konstruktoru je znázorněno v následujících značek a kódu.  
  
 [!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]  
  
 Když <xref:System.Windows.Documents.Hyperlink> na tomto <xref:System.Windows.Controls.Page> je kliknutí na navigační aktivováno po vytvoření instance <xref:System.Windows.Controls.Page> přejít na použití jiného než výchozího konstruktoru a volání <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> – metoda. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> přijímá odkaz na objekt, který <xref:System.Windows.Navigation.NavigationService> přejdete na, ne sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
#### <a name="programmatic-navigation-with-a-pack-uri"></a>Programově řízená navigace se identifikátor URI protokolu Pack  
 Pokud je potřeba vytvořit sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] prostřednictvím kódu programu (když můžete určit pouze této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] běhu, třeba), můžete použít <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metoda. To je ukázáno v následujícím příkladu.  
  
 [!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]  
  
#### <a name="refreshing-the-current-page"></a>Obnovit aktuální stránku  
 A <xref:System.Windows.Controls.Page> se nestáhne, pokud má stejné sadě [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , která je uložena v <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> vlastnost. Chcete-li vynutit [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aktuální stránku stáhnout znovu, můžete volat <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> způsob, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]  
  
<a name="Navigation_Lifetime"></a>   
### <a name="navigation-lifetime"></a>Doba života navigace  
 Jak už víte, existuje mnoho způsobů, jak inicializovat navigaci. Když je zahájeno navigace, a během navigace, můžou sledovat a ovlivnit navigace pomocí následujících událostí, které implementují <xref:System.Windows.Navigation.NavigationService>:  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigating>. Nastane, pokud se požaduje novou navigaci. Je možné zrušit navigaci.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Nastává pravidelně během stahování, aby se poskytují informace o průběhu navigace.  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigated>. Nastane, pokud byl nachází a stáhnout na stránce.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Nastane, pokud se zastaví navigaci (voláním <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), nebo když je požadováno novou navigaci probíhá aktuální navigace.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. Nastane, pokud dojde k chybě při navigaci na požadovaný obsah.  
  
-   <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Vyvolá se v případě obsahu, na kterou se přejde je načten a analyzován a zahájení vykreslování.  
  
-   <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Nastane po zahájení navigace na fragment obsahu, který se stane:  
  
    -   Okamžitě Pokud požadovaný fragment je v aktuálním obsahu.  
  
    -   Po zdrojový obsah se načetl, pokud požadovaný fragment probíhá jiný obsah.  
  
 Navigační události jsou vyvolány v pořadí, ve kterém je znázorněn v následujícím obrázku.  
  
 ![Vývojový diagram navigace stránky](./media/navigation-overview/order-of-navigation-events.png "stránky navigační události vývojový diagram")  
  
 Obecně platí <xref:System.Windows.Controls.Page> není obavy o těchto událostech. Je pravděpodobnější, že aplikaci jde s nimi a z tohoto důvodu tyto události jsou také generovány <xref:System.Windows.Application> třídy:  
  
-   <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>  
  
 Pokaždé, když <xref:System.Windows.Navigation.NavigationService> vyvolá událost, <xref:System.Windows.Application> třída vyvolá příslušné události. <xref:System.Windows.Controls.Frame> a <xref:System.Windows.Navigation.NavigationWindow> nabízí stejné události k detekci navigace v rámci svých odpovídajících obory.  
  
 V některých případech <xref:System.Windows.Controls.Page> může zajímat tyto události. Například <xref:System.Windows.Controls.Page> může zpracovat <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> událostí k určení, jestli se mají zrušit navigace směrem od samotného. To je ukázáno v následujícím příkladu.  
  
 [!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]  
  
 Pokud zaregistrujete obslužnou rutinu události navigace z <xref:System.Windows.Controls.Page>, stejně jako v předchozím příkladu, musí také zrušit registraci obslužné rutiny události. Pokud to neuděláte, může mít vedlejší účinky s ohledem na tom [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] si pamatuje navigace <xref:System.Windows.Controls.Page> navigace pomocí deníku.  
  
<a name="NavigationHistory"></a>   
### <a name="remembering-navigation-with-the-journal"></a>Zapamatování navigace pomocí deníku  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Mějte na paměti, které jste přešli ze stránky pomocí dvou zásobníky: zpět zásobník a stohu. Pokud přejdete z aktuálního <xref:System.Windows.Controls.Page> do nového <xref:System.Windows.Controls.Page> dopředu na existující nebo <xref:System.Windows.Controls.Page>, aktuální <xref:System.Windows.Controls.Page> se přidá do *zpět zásobník*. Pokud přejdete z aktuálního <xref:System.Windows.Controls.Page> zpět na předchozí <xref:System.Windows.Controls.Page>, aktuální <xref:System.Windows.Controls.Page> se přidá do *stohu*. Zpět zásobník, stohu a funkce pro správu, než se souhrnně označují jako deníku. Každá položka v zpět zásobník a stohu je instance <xref:System.Windows.Navigation.JournalEntry> třídy a označuje se jako *deníku*.  
  
#### <a name="navigating-the-journal-from-internet-explorer"></a>Navigace deníku z aplikace Internet Explorer  
 Koncepčně tento deník funguje stejně způsobu, jakým **zpět** a **vpřed** tlačítka v [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] provést. Tyto aspekty znázorňuje následující obrázek.  
  
 ![Tlačítka Zpět a vpřed](./media/navigation-overview/back-and-forward-navigation.png "Navigovat pomocí tlačítka vpřed a zpět.")  
  
 Pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] hostované [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integruje tento deník do navigační [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. To umožňuje uživatelům procházení stránek v [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pomocí **zpět**, **vpřed**, a **poslední stránky** tlačítka v [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Deník není integrovaný do [!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)] stejným způsobem, jako je pro [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] nebo Internet Explorer 8. Místo toho [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vykreslí navigace nahraďte [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!IMPORTANT]
>  V [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], když uživatel přejde ze a zpět [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], pouze položky deníku pro stránky, které nebyly zachovány aktivní uchovávaných v deníku. Informace o zachování stránky zachování připojení, najdete v části [životnost stránky a deníku](#PageLifetime) dále v tomto tématu.  
  
 Ve výchozím nastavení text pro každou <xref:System.Windows.Controls.Page> , který se zobrazí **poslední stránky** seznam [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] je [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro <xref:System.Windows.Controls.Page>. V mnoha případech to není zejména srozumitelné pro uživatele. Naštěstí můžete změnit text pomocí jedné následující možnosti:  
  
1.  Připojený `JournalEntry.Name` hodnotu atributu.  
  
2.  `Page.Title` Hodnotu atributu.  
  
3.  `Page.WindowTitle` Hodnotu atributu a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro aktuální <xref:System.Windows.Controls.Page>.  
  
4.  [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Pro aktuální <xref:System.Windows.Controls.Page>. (Výchozí)  
  
 Pořadí, ve kterém jsou uvedeny možnosti odpovídá pořadí priorit pro hledání textu. Například pokud `JournalEntry.Name` je nastavena hodnoty jsou ignorovány.  
  
 V následujícím příkladu `Page.Title` atribut ke změně textu, který se zobrazí položky deníku.  
  
 [!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]  
  
#### <a name="navigating-the-journal-using-wpf"></a>Navigace deníku pomocí grafického subsystému WPF  
 I když se uživatel může dostat deníku pomocí **zpět**, **vpřed**, a **poslední stránky** v [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], se můžete dostat také pomocí obou deník Deklarativní a programová mechanismy poskytované [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Provedete to jedním z důvodů je poskytnout vlastní navigační [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] na stránkách.  
  
 Podpora navigačního deníku můžete přidat deklarativně pomocí navigačních příkazů vystavené <xref:System.Windows.Input.NavigationCommands>. Následující příklad ukazuje způsob použití `BrowseBack` příkaz navigace.  
  
 [!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]  
  
 Deník prostřednictvím kódu programu můžete přejít pomocí jedné z následujících členů <xref:System.Windows.Navigation.NavigationService> třídy:  
  
-   <xref:System.Windows.Navigation.NavigationService.GoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.GoForward%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>  
  
 Deník lze ovládat také prostřednictvím kódu programu, jak je popsáno v [podpůrné stav obsahu v historii navigace](#RetainingContentStateWithNavigationHistory) dále v tomto tématu.  
  
<a name="PageLifetime"></a>   
### <a name="page-lifetime-and-the-journal"></a>Životní cyklus stránky a deníku  
 Vezměte v úvahu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] s několika stránek, které obsahují formátovaný obsah, včetně obrázků, animace a média. Nároky na paměť pro stránky, jako jsou tyto může být poměrně rozsáhlé, zejména v případě, že video a audiostreamů médium slouží. Vzhledem k tomu, že deníku stránky, které se přejde poté, například "si pamatuje" [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] může rychle používat znatelný i velké množství paměti.  
  
 Z tohoto důvodu je výchozí chování deníku Uložit <xref:System.Windows.Controls.Page> v každé položky deníku spíše než odkaz na metadata <xref:System.Windows.Controls.Page> objektu. Když je položka deníku přejde, jeho <xref:System.Windows.Controls.Page> metadat se používá k vytvoření nové instance zadaného <xref:System.Windows.Controls.Page>. V důsledku toho každá <xref:System.Windows.Controls.Page> , který se přejde poté, je doba života, který je znázorněn v následujícím obrázku.  
  
 ![Doba života stránky](./media/navigation-overview/navigated-page-lifetime.png "Zobrazí dobu života, když přejde na stránku.")  
  
 I když se pomocí záznamu do deníku výchozí chování můžete uložit na spotřebu paměti, se může snížit výkon při vykreslování na stránku; reinstantiating <xref:System.Windows.Controls.Page> může být náročné na čas, zejména v případě, že má spoustu různého obsahu. Pokud potřebujete zachovat <xref:System.Windows.Controls.Page> instance v deníku, lze nakreslit na dvě techniky to udělat. Nejprve můžete programově přejít na <xref:System.Windows.Controls.Page> objektu voláním <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metody.  
  
 Za druhé, můžete určit, že [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zachovat instance <xref:System.Windows.Controls.Page> v deníku nastavením <xref:System.Windows.Controls.Page.KeepAlive%2A> vlastnost `true` (výchozí hodnota je `false`). Jak je znázorněno v následujícím příkladu, můžete nastavit <xref:System.Windows.Controls.Page.KeepAlive%2A> deklarativně v kódu.  
  
 [!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]  
  
 Životnost <xref:System.Windows.Controls.Page> , který je zachováno se trochu liší od, který není. První <xref:System.Windows.Controls.Page> , který je uložen zachování připojení se přejde poté, je vytvořena instance stejně jako <xref:System.Windows.Controls.Page> , který není zachováno. Ale protože instance <xref:System.Windows.Controls.Page> se uchovávají v deníku, kdy je nikdy vytvořen znovu pro tak dlouho, dokud zůstává v deníku. V důsledku toho pokud <xref:System.Windows.Controls.Page> inicializace logiku, která musí být volána pokaždé, když má <xref:System.Windows.Controls.Page> se přejde poté, byste měli přesunout ji z konstruktoru do obslužné rutiny pro <xref:System.Windows.FrameworkElement.Loaded> událostí. Jak je znázorněno na následujícím obrázku <xref:System.Windows.FrameworkElement.Loaded> a <xref:System.Windows.FrameworkElement.Unloaded> události jsou vyvolány stále pokaždé, když <xref:System.Windows.Controls.Page> je přejde do a z, v uvedeném pořadí.  
  
 ![Když jsou vyvolány události Loaded a Unloaded](./media/navigation-overview/loaded-and-unloaded-events.png "Loaded a uvolněné události jsou vyvolány, když je stránka přejde do a z.")  
  
 Když <xref:System.Windows.Controls.Page> není zachováno, neměli byste některého z následujících:  
  
-   Odkaz na nebo libovolné části Store.  
  
-   Zaregistrujte obslužné rutiny událostí s událostmi, které nejsou implementované.  
  
 Jedním z nich vytvoří odkazy, které vynucují <xref:System.Windows.Controls.Page> příznakem pro zachování paměti, i když se odebral z deníku.  
  
 Obecně byste měli dát přednost výchozí <xref:System.Windows.Controls.Page> chování není udržování <xref:System.Windows.Controls.Page> zachování připojení. Však tato akce nemá vliv na stav, které jsou popsané v další části.  
  
<a name="RetainingContentStateWithNavigationHistory"></a>   
### <a name="retaining-content-state-with-navigation-history"></a>Zachování stavu obsahu s využitím historii navigace  
 Pokud <xref:System.Windows.Controls.Page> není zachováno, a obsahuje ovládací prvky, které shromažďování dat od uživatele, co se stane data, pokud uživatel přejde ze a zpět <xref:System.Windows.Controls.Page>? Z pohledu zkušenosti uživatele, uživatel by měl očekávat dříve zadaná data. Bohužel protože novou instanci třídy <xref:System.Windows.Controls.Page> se vytvoří s každou navigační ovládací prvky, reinstantiated shromážděná data jsou a data budou ztracena.  
  
 Naštěstí deníku poskytuje podporu pro zapamatování dat napříč <xref:System.Windows.Controls.Page> navigaci, včetně dat ovládacího prvku. Konkrétně položka deníku pro každou <xref:System.Windows.Controls.Page> funguje jako kontejner pro přidružený dočasný <xref:System.Windows.Controls.Page> stavu. Následující kroky popisují, jak se používá tato podpora při <xref:System.Windows.Controls.Page> přešel z:  
  
1.  Záznam pro aktuální <xref:System.Windows.Controls.Page> se přidá do deníku.  
  
2.  Stav <xref:System.Windows.Controls.Page> se uloží spolu s položka deníku pro tuto stránku, která se přidá do pozadí zásobníku.  
  
3.  Nové <xref:System.Windows.Controls.Page> se přejde poté.  
  
 Pokud na stránce <xref:System.Windows.Controls.Page> je přejde zpět do deníku, pomocí následujících kroků provést:  
  
1.  <xref:System.Windows.Controls.Page> (Položka hlavní deníku back zásobníku) je vytvořena instance.  
  
2.  <xref:System.Windows.Controls.Page> Se aktualizují pomocí stavu, která byla uložená s položka deníku pro <xref:System.Windows.Controls.Page>.  
  
3.  <xref:System.Windows.Controls.Page> Přejde zpět.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automaticky použije tato podpora při následující ovládací prvky se používají na <xref:System.Windows.Controls.Page>:  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ProgressBar>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Slider>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
-   <xref:System.Windows.Controls.TextBox>  
  
 Pokud <xref:System.Windows.Controls.Page> používá tyto ovládací prvky dat zadaných do nich je zapamatovaných napříč <xref:System.Windows.Controls.Page> navigaci, jak je uvedeno ve **Oblíbené barva** <xref:System.Windows.Controls.ListBox> na následujícím obrázku.  
  
 ![Stránka s ovládacími prvky, které nezapomeňte stavu](./media/navigation-overview/data-remembered-across-page-navigations.png "zadaná Data se uloží, v navigaci na stránce.")  
  
 Když <xref:System.Windows.Controls.Page> obsahuje ovládací prvky než ty, které v předchozím seznamu, nebo když stav je uložený ve vlastních objektů, je potřeba napsat kód, který způsobí deníku pamatovat stavem, ať už <xref:System.Windows.Controls.Page> navigaci.  
  
 Pokud je potřeba si vzpomenout malých kousků stavem, ať už <xref:System.Windows.Controls.Page> navigaci, můžete použít vlastnosti závislosti (naleznete v tématu <xref:System.Windows.DependencyProperty>), které jsou nakonfigurovány s <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> příznak metadat.  
  
 Pokud stav, který vaše <xref:System.Windows.Controls.Page> je potřeba pamatovat napříč navigaci se skládá z více částí dat, může být pro vás menším množstvím kódu k zapouzdření svůj stav do jedné třídy a implementovat náročné na <xref:System.Windows.Navigation.IProvideCustomContentState> rozhraní.  
  
 Pokud potřebujete procházet různé stavy jediného <xref:System.Windows.Controls.Page>, bez přechodu z <xref:System.Windows.Controls.Page> samostatně, můžete použít <xref:System.Windows.Navigation.IProvideCustomContentState> a <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.  
  
<a name="Cookies"></a>   
### <a name="cookies"></a>Soubory cookie  
 Jiné způsobu, jakým [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ukládají data aplikace se se soubory cookie, které se vytvoří, aktualizovat a odstraňovat pomocí <xref:System.Windows.Application.SetCookie%2A> a <xref:System.Windows.Application.GetCookie%2A> metody. Soubory cookie, které můžete vytvořit v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jsou stejné soubory cookie používat další typy webových aplikací, soubory cookie jsou libovolné části dat, která jsou uložena v aplikaci na klientském počítači během nebo mezi jednotlivými relacemi aplikace. Data souborů cookie má obvykle tvar z dvojice název/hodnota v následujícím formátu.  
  
 *Název* `=` *hodnota*  
  
 Pokud je předán data <xref:System.Windows.Application.SetCookie%2A>, spolu s <xref:System.Uri> umístění, u které je třeba nastavit soubor cookie, soubor cookie se vytvoří v paměti a je k dispozici pouze po dobu trvání aktuální relace aplikace. Tento typ souboru cookie, který se označuje jako *souboru cookie relace*.  
  
 Datum vypršení platnosti musí mezi jednotlivými relacemi aplikace ukládat do souboru cookie, přidat do souboru cookie, v následujícím formátu.  
  
 *NÁZEV* `=` *HODNOTA* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`  
  
 Datum vypršení platnosti souboru cookie je uložen v aktuálním [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] instalace složka dočasných souborů Internetu do vypršení platnosti souboru cookie. Je soubor cookie se označuje jako *trvalého souboru cookie* protože zůstává zachována mezi jednotlivými relacemi aplikace.  
  
 Načíst relace a trvalé soubory cookie voláním <xref:System.Windows.Application.GetCookie%2A> předejte <xref:System.Uri> umístění, kde byl soubor cookie nastaven s <xref:System.Windows.Application.SetCookie%2A> metoda.  
  
 Toto jsou některé způsoby, jakými soubory cookie jsou podporovány v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:  
  
-   [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] můžete i vytvořit a spravovat soubory cookie.  
  
-   Soubory cookie, které jsou vytvořeny pomocí [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je přístupný z prohlížeče.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ze stejné domény můžete vytvářet a sdílet soubory cookie.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] a [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] stránky ze stejné domény můžete vytvářet a sdílet soubory cookie.  
  
-   Soubory cookie se odešlou, filtrovaly při [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] a dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky vytvoření webových požadavků.  
  
-   Obě nejvyšší úrovně [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] konání prvky IFRAME můžete přístupu k souboru cookie.  
  
-   Podpora cookies v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je stejný pro všechny podporované prohlížeče.  
  
-   V [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], je kompilátorem respektovány P3P zásady, které se vztahují na soubory cookie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zejména s ohledem na první strany a třetích stran [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Structured_Navigation"></a>   
### <a name="structured-navigation"></a>Strukturované navigace  
 Pokud je potřeba předat data z jednoho <xref:System.Windows.Controls.Page> do jiného, můžete data předat jako argumenty pro jiné než výchozí konstruktor třídy <xref:System.Windows.Controls.Page>. Mějte na paměti, že pokud použijete tento postup, je nutné zachovat <xref:System.Windows.Controls.Page> zachování připojení; Pokud ne, příště přejdete <xref:System.Windows.Controls.Page>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opětovně <xref:System.Windows.Controls.Page> pomocí výchozího konstruktoru.  
  
 Můžete také vaše <xref:System.Windows.Controls.Page> můžete implementovat vlastnosti, které jsou nastavené s daty, která má být předán. Věci stát složité, ale, když <xref:System.Windows.Controls.Page> potřebuje k předání dat zpět do <xref:System.Windows.Controls.Page> , která přejde do něj. Problém je, že navigace nepodporuje nativně mechanismy pro zaručit, že <xref:System.Windows.Controls.Page> bude vrácena hodnota po se přejde poté z. Navigace v podstatě nepodporuje volání nebo vracet sémantiku. Pro vyřešení tohoto problému [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje <xref:System.Windows.Navigation.PageFunction%601> třídy, který vám pomůže zajistit, aby <xref:System.Windows.Controls.Page> se vrátí do předvídatelný a strukturované způsobem. Další informace najdete v tématu [přehled strukturované navigace](structured-navigation-overview.md).  
  
<a name="The_NavigationWindow_Class"></a>   
## <a name="the-navigationwindow-class"></a>NavigationWindow – třída  
 Do této chvíle jste viděli škále navigace služby, které jste se s největší pravděpodobností používat k vytváření aplikací pomocí nástroje lze procházet obsah. Tyto služby byly popsané v kontextu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], i když už nejsou omezeni na [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Moderní operačních systémů a aplikací Windows Využijte výhod možností prohlížeče moderní uživatelů začlenit navigace ve stylu prohlížeče do samostatné aplikace. Mezi běžné příklady patří:  
  
-   **Word tezauru**: Přejděte volby slov.  
  
-   **Průzkumník souborů**: Procházení souborů a složek.  
  
-   **Průvodci**: Rozdělení do několika stránek, které se dá Navigovat mezi složitý úkol. Příkladem je průvodce Windows komponenty, která zpracovává přidávání a odebírání funkcí Windows.  
  
 Navigace ve stylu prohlížeče začlenit do samostatné aplikace, můžete použít <xref:System.Windows.Navigation.NavigationWindow> třídy. <xref:System.Windows.Navigation.NavigationWindow> je odvozen od <xref:System.Windows.Window> a rozšiřuje ji stejné podporu pro navigaci, který [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] poskytují. Můžete použít <xref:System.Windows.Navigation.NavigationWindow> jako hlavní okno samostatná aplikace nebo jako sekundární okno, jako je třeba dialogového okna.  
  
 K implementaci <xref:System.Windows.Navigation.NavigationWindow>, stejně jako u většiny třídy nejvyšší úrovně v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, a tak dále), použijte kombinaci značek a kódu. To je ukázáno v následujícím příkladu.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
 [!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]  
  
 Tento kód vytvoří <xref:System.Windows.Navigation.NavigationWindow> , který automaticky přejde na <xref:System.Windows.Controls.Page> (HomePage.xaml) při <xref:System.Windows.Navigation.NavigationWindow> je otevřen. Pokud <xref:System.Windows.Navigation.NavigationWindow> je hlavního okna aplikace, můžete použít `StartupUri` atribut spusťte ji. To je ukázáno v následujícím kódu.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]  
  
 Následující obrázek ukazuje <xref:System.Windows.Navigation.NavigationWindow> jako hlavní okno samostatné aplikace.  
  
 ![Hlavní okno](./media/navigation-overview/navigation-window-as-main-window.png "navigačním okně jako hlavní okno")  
  
 Z na obrázku vidíte, že <xref:System.Windows.Navigation.NavigationWindow> má název, i když v není nastavená <xref:System.Windows.Navigation.NavigationWindow> implementační kód z předchozího příkladu. Místo toho název se nastavuje pomocí <xref:System.Windows.Controls.Page.WindowTitle%2A> vlastnost, která je znázorněna v následujícím kódu.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]  
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]  
  
 Nastavení <xref:System.Windows.Controls.Page.WindowWidth%2A> a <xref:System.Windows.Controls.Page.WindowHeight%2A> vlastnosti má vliv také <xref:System.Windows.Navigation.NavigationWindow>.  
  
 Obvykle můžete implementovat vlastní <xref:System.Windows.Navigation.NavigationWindow> když potřebujete přizpůsobit chování aplikace nebo její vzhled. Pokud tak učiníte, ani jedno, můžete použít zástupce. Při zadání této sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> jako <xref:System.Windows.Application.StartupUri%2A> v samostatné aplikaci, <xref:System.Windows.Application> automaticky vytvoří <xref:System.Windows.Navigation.NavigationWindow> na hostitele <xref:System.Windows.Controls.Page>. Následující kód ukazuje, jak ji povolit.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]  
  
 Pokud chcete okno sekundární aplikace, jako je například dialogové okno bude <xref:System.Windows.Navigation.NavigationWindow>, můžete použít kód v následujícím příkladu ho otevřete.  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
 [!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]  
  
 Následující obrázek ukazuje výsledek.  
  
 ![Dialogové okno](./media/navigation-overview/navigation-window-as-dialog-box.png "navigačním okně jako dialogové okno")  
  
 Jak je vidět, <xref:System.Windows.Navigation.NavigationWindow> zobrazí [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]-style **zpět** a **vpřed** tlačítka, díky kterým můžou uživatelé přejít do deníku. Tato tlačítka poskytují stejné prostředí pro uživatele, jak je znázorněno na následujícím obrázku.  
  
 ![Tlačítka v okně Navigace zpět a vpřed](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "tlačítka v navigačním okně zpět a vpřed")  
  
 Pokud vaše stránky zadejte svoje vlastní uživatelské rozhraní a podpora navigačního deníku, můžete skrýt **zpět** a **vpřed** tlačítka zobrazený <xref:System.Windows.Navigation.NavigationWindow> tak, že nastavíte hodnotu <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> vlastnost `false`.  
  
 Alternativně můžete použít podpory vlastního nastavení v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nahradit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z <xref:System.Windows.Navigation.NavigationWindow> samotný.  
  
<a name="Frame_in_Standalone_Applications"></a>   
## <a name="the-frame-class"></a>Třída rámce  
 Obě prohlížeče a <xref:System.Windows.Navigation.NavigationWindow> se naviguje obsahu hostitele systému windows. V některých případech může aplikace mají obsah, který nemusí být hostovány celé okno. Místo toho takový obsah hostovat uvnitř jiného obsahu. Lze procházet obsah můžete vložit do další obsah pomocí <xref:System.Windows.Controls.Frame> třídy. <xref:System.Windows.Controls.Frame> podporuje stejné jako <xref:System.Windows.Navigation.NavigationWindow> a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
 Následující příklad ukazuje, jak přidat <xref:System.Windows.Controls.Frame> k <xref:System.Windows.Controls.Page> deklarativně pomocí `Frame` elementu.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]  
  
 Tento kód nastaví `Source` atribut `Frame` element s pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro <xref:System.Windows.Controls.Page> , který <xref:System.Windows.Controls.Frame> by měly nejprve přejděte do. Následující obrázek ukazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] s <xref:System.Windows.Controls.Page> , který má <xref:System.Windows.Controls.Frame> , který přešel mezi několik stránek.  
  
 ![Snímek, který přešel mezi více stránek](./media/navigation-overview/frame-navigation-between-multiple-pages.png "ukazuje rámce navigace mezi více stránek.")  
  
 Pouze nemusíte používat <xref:System.Windows.Controls.Frame> uvnitř obsahu <xref:System.Windows.Controls.Page>. Je běžné hostovat <xref:System.Windows.Controls.Frame> uvnitř obsahu <xref:System.Windows.Window>.  
  
 Ve výchozím nastavení <xref:System.Windows.Controls.Frame> pouze používá vlastní deník neexistují jiném deníku. Pokud <xref:System.Windows.Controls.Frame> je součástí obsahu, který je umístěn uvnitř buď <xref:System.Windows.Navigation.NavigationWindow> nebo [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame> používá, který patří do deníku <xref:System.Windows.Navigation.NavigationWindow> nebo [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. V některých případech však <xref:System.Windows.Controls.Frame> může být nutné odpovědný za vlastní deník. Provedete to jedním z důvodů je umožnit deníku navigace v rámci stránky, které jsou hostovány <xref:System.Windows.Controls.Frame>. To je znázorněno v následujícím obrázku.  
  
 ![Diagram rámce a stránky](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "ukazuje deníku navigace v rámci stránky hostitelem objektu frame.")  
  
 V takovém případě můžete nakonfigurovat <xref:System.Windows.Controls.Frame> používat vlastní deník nastavením <xref:System.Windows.Controls.Frame.JournalOwnership%2A> vlastnost <xref:System.Windows.Controls.Frame> k <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. To je ukázáno v následujícím kódu.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]  
  
 Následující obrázek ukazuje účinek podrobné ukázky navigace v rámci <xref:System.Windows.Controls.Frame> , která používá vlastní deník.  
  
 ![Snímek, který používá vlastní deník](./media/navigation-overview/frame-uses-its-own-journal.png "to demonstruje účinek podrobné ukázky navigace v rámci, která používá vlastní deník.")  
  
 Všimněte si, že deníku položky jsou seřazeny podle navigaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v <xref:System.Windows.Controls.Frame>, spíše než [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)].  
  
> [!NOTE]
>  Pokud <xref:System.Windows.Controls.Frame> je součástí obsahu, který je hostován v <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> používá vlastní deník a v důsledku toho se zobrazí jeho vlastní navigace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Pokud vyžaduje činnost koncového uživatele <xref:System.Windows.Controls.Frame> poskytnout vlastní deník bez toho, abych navigaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], lze skrýt navigační [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nastavením <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> k <xref:System.Windows.Visibility.Hidden>. To je ukázáno v následujícím kódu.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]  
  
<a name="Navigation_Hosts"></a>   
## <a name="navigation-hosts"></a>Hostitel pro navigaci  
 <xref:System.Windows.Controls.Frame> a <xref:System.Windows.Navigation.NavigationWindow> jsou třídy, které jsou označovány jako hostitel pro navigaci. A *navigace hostitele* je třída, která můžete přejít na a zobrazit obsah. K tomu každou navigační hostitel používá vlastní <xref:System.Windows.Navigation.NavigationService> a deníku. Základní konstrukce hostitele navigace se zobrazí na následujícím obrázku.  
  
 ![Navigátor diagramy](./media/navigation-overview/navigation-host-construction.png "základní konstrukce hostitele navigace")  
  
 V podstatě to umožňuje <xref:System.Windows.Navigation.NavigationWindow> a <xref:System.Windows.Controls.Frame> poskytnout stejné, která podporují navigace [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] poskytuje, když jsou hostované v prohlížeči.  
  
 Kromě použití <xref:System.Windows.Navigation.NavigationService> a deníku, hostitel pro navigaci implementovat stejné členy, které <xref:System.Windows.Navigation.NavigationService> implementuje. To je znázorněno v následujícím obrázku.  
  
 ![Deník v rámci a okna NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "navigačním okně a snímků")  
  
 Umožňuje programu podpora navigačního přímo před nimi. To může být vhodné, pokud je potřeba zadat vlastní navigační [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro <xref:System.Windows.Controls.Frame> , která je hostována v <xref:System.Windows.Window>. Kromě toho oba typy implementovat další, související navigačního členů, včetně `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) a `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), které umožňují vytvořit výčet položky deníku v pozadí Stack a jejich předávání zásobníku, v uvedeném pořadí.  
  
 Jak už bylo zmíněno dříve, může existovat více než jeden deníku v rámci aplikace. Následující obrázek poskytuje příklad, když k tomu může dojít.  
  
 ![Více deníků v rámci jedné aplikace](./media/navigation-overview/multiple-journals-in-one-application.png "Toto je příklad více než jeden deníku v aplikaci.")  
  
<a name="Navigating_to_Content_Other_than_Pages"></a>   
## <a name="navigating-to-content-other-than-xaml-pages"></a>Přechod na obsah než stránky XAML  
 V tomto tématu <xref:System.Windows.Controls.Page> a aktualizací Service pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] se používají na různých navigace předvedou možnosti dostupné v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Ale <xref:System.Windows.Controls.Page> , který je zkompilován do aplikace není jediným typem obsahu, který se dá Navigovat a aktualizací Service pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nejsou jediný způsob, jak identifikovat obsah.  
  
 Jak tato část ukazuje, můžete také přejít na dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] soubory a objekty.  
  
<a name="Navigating_to_Loose_XAML_Files"></a>   
### <a name="navigating-to-loose-xaml-files"></a>Přejděte na volný XAML soubory  
 Dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je soubor s následujícími charakteristikami:  
  
-   Obsahuje pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (to znamená žádný kód).  
  
-   Obsahuje deklaraci odpovídající obor názvů.  
  
-   Má příponu názvu souboru .xaml.  
  
 Představte si třeba následující obsah, který je uložený jako dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru Person.xaml.  
  
 [!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]  
  
 Když dvakrát kliknete soubor v prohlížeči se otevře a přejde na a zobrazí obsah. To je ukázáno na následujícím obrázku.  
  
 ![Zobrazení obsahu souboru Person.XAML](./media/navigation-overview/contents-of-person-xaml-file.png "zobrazí obsah souboru Person.XAML.")  
  
 Můžete zobrazit dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru z následujících možností:  
  
-   Web na místním počítači, intranetu nebo Internetu.  
  
-   A [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] sdílenou složku.  
  
-   Místní disk.  
  
 Dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor lze přidat k oblíbeným položkám prohlížeče, nebo se v prohlížeči na domovské stránce.  
  
> [!NOTE]
>  Další informace o publikování a spuštění volné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky, najdete v článku [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).  
  
 Jediným omezením s ohledem na dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je, že může hostovat pouze obsah, který je bezpečný pro spuštění v částečném vztahu důvěryhodnosti. Například `Window` nemůže být kořenový element dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru. Další informace najdete v tématu [částečné zabezpečení důvěryhodnosti WPF](../wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_Frame"></a>   
### <a name="navigating-to-html-files-by-using-frame"></a>Procházení souborů ve formátu HTML pomocí rámce  
 Jak byste asi očekávali, můžete také přejít na [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]. Stačí jednoduše zadat [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] používající schéma protokolu http. Například následující [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ukazuje <xref:System.Windows.Controls.Frame> , která přejde do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] stránky.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]  
  
 Přejděte na [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] vyžaduje speciální oprávnění. Například, nejde přejít ze [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , na kterém je spuštěn v sandboxu zabezpečení částečným vztahem důvěryhodnosti zóny Internet. Další informace najdete v tématu [částečné zabezpečení důvěryhodnosti WPF](../wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>   
### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Procházení souborů ve formátu HTML pomocí ovládacího prvku WebBrowser  
 <xref:System.Windows.Controls.WebBrowser> Podporuje ovládací prvek [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] hostování dokumentu, navigace a skript/spravovaného kódu vzájemná funkční spolupráce. Podrobné informace týkající <xref:System.Windows.Controls.WebBrowser> řídí, najdete v článku <xref:System.Windows.Controls.WebBrowser>.  
  
 Stejně jako <xref:System.Windows.Controls.Frame>, navigační k [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] pomocí <xref:System.Windows.Controls.WebBrowser> vyžaduje speciální oprávnění. Například z aplikace částečným vztahem důvěryhodnosti, můžete přejít jenom do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] nachází v lokalitě původu. Další informace najdete v tématu [částečné zabezpečení důvěryhodnosti WPF](../wpf-partial-trust-security.md).  
  
<a name="Navigating_to_Objects"></a>   
### <a name="navigating-to-custom-objects"></a>Přejděte na vlastních objektech  
 Pokud máte data, která je uložená jako vlastní objekty, je vytvořit jeden způsob, jak tato data zobrazit <xref:System.Windows.Controls.Page> s obsahem, který je vázán na tyto objekty (viz [přehled datových vazeb](../data/data-binding-overview.md)). Pokud už nebudete potřebovat režii vytvoření celé stránky pouze pro zobrazení objektů, můžete přejít přímo na jejich místo.  
  
 Vezměte v úvahu `Person` třídu, která je implementována v následujícím kódu.  
  
 [!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
 [!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]  
  
 Chcete-li přejít k němu, zavolejte <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> způsob, jak je ukázáno v následujícím kódu.  
  
 [!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]  
  
 [!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
 [!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]  
  
 Následující obrázek ukazuje výsledek.  
  
 ![Na stránce, který odkazuje na třídu](./media/navigation-overview/page-navigates-to-an-object.png "Toto je příklad stránky, který odkazuje na objekt.")  
  
 Na tomto obrázku uvidíte, že užitečné nezobrazí se. Ve skutečnosti zobrazená hodnota je vrácená hodnota `ToString` metodu **osoba** objektu; ve výchozím nastavení, toto je jediná hodnota, která [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] můžete použít k reprezentaci objektu. Může přepsat `ToString` metoda vrátí smysluplnější informace, i když bude stále být pouze hodnotu řetězce. Jednou z metod můžete použít, který využívá funkce prezentace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je použití šablony data. Můžete implementovat datové šablony, která [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] můžete přiřadit k objektu určitého typu. Následující kód ukazuje datové šablony pro `Person` objektu.  
  
 [!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]  
  
 Tady je přidružené šablony `Person` typu pomocí `x:Type` – rozšíření značek v `DataType` atribut. Potom vytvoří vazbu šablony `TextBlock` elementy (naleznete v tématu <xref:System.Windows.Controls.TextBlock>) k vlastnostem `Person` třídy. Následující obrázek znázorňuje aktualizovaný vzhled `Person` objektu.  
  
 ![Navigace na třídu, která má datové šablony](./media/navigation-overview/navigating-to-a-class.png "přejdete na třídu, která má datové šablony.")  
  
 Výhoda této techniky je konzistence můžete získat díky možnosti opakovaně používat šablony pro zobrazení objektů konzistentně kdekoli ve vaší aplikaci.  
  
 Další informace o šablonách dat, naleznete v tématu [přehled datových šablon](../data/data-templating-overview.md).  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpečení  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje podporu navigace [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] k přejde přes Internet a umožňuje aplikacím, aby hostitel obsahu třetí strany. K ochraně aplikací a uživatelů ze škodlivé chování, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje širokou škálu funkcí zabezpečení, které jsou popsány v [zabezpečení](../security-wpf.md) a [částečné zabezpečení důvěryhodnosti WPF](../wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [Přehled správy aplikací](application-management-overview.md)
- [Sbalení URI v technologii WPF](pack-uris-in-wpf.md)
- [Přehled strukturované navigace](structured-navigation-overview.md)
- [Přehled topologií navigace](navigation-topologies-overview.md)
- [Témata s postupy](navigation-how-to-topics.md)
- [Nasazení aplikace WPF](deploying-a-wpf-application-wpf.md)
