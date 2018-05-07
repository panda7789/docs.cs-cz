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
ms.openlocfilehash: b326d623da49cf02b95be8a22a75b3ea3d199e27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="navigation-overview"></a>Přehled navigace
Windows Presentation Foundation (WPF) podporuje navigační stylu prohlížeče, který lze použít v dva typy aplikací: samostatné aplikace a [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Obsah balíčku pro navigaci [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje <xref:System.Windows.Controls.Page> třídy. Můžete přejít na jednom <xref:System.Windows.Controls.Page> do jiného deklarativně, pomocí <xref:System.Windows.Documents.Hyperlink>, nebo prostřednictvím kódu programu, pomocí <xref:System.Windows.Navigation.NavigationService>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] využívá deník pamatovat stránek, které byly zpřístupněny z a přejděte zpět na ně.  
  
 <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>, a deník tvoří základní navigační podpory, které nabízí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Tento přehled zde tyto funkce podrobně popsány před pokrývajících podporu pokročilé navigace, což zahrnuje navigaci na přijít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubory, [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] souborů a objektů.  
  
> [!NOTE]
>  V tomto tématu se pojem "browser" odkazuje pouze do prohlížečů, které může být hostitelem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, které aktuálně zahrnuje [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] a Firefox. Kde konkrétní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] funkce jsou podporovány pouze určitého prohlížeče, je uvedená verze prohlížeče.  
   
     
## <a name="navigation-in-wpf-applications"></a>Navigace v aplikacích WPF  
 Toto téma obsahuje přehled možností klíče navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Tyto možnosti jsou k dispozici pro samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], i když je toto téma představuje v kontextu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
> [!NOTE]
>  Toto téma se nezabývá sestavení a nasazení [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Další informace o [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], najdete v části [přehled aplikace prohlížeče XAML WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
 Tato část vysvětluje a ukazuje, navigace na následující aspekty:  
  
-   [Implementace stránky](#CreatingAXAMLPage)  
  
-   [Konfigurace úvodní stránky](#Configuring_a_Start_Page)  
  
-   [Konfigurace názvu, šířku a výšku okna hostitele](#ConfiguringAXAMLPage)  
  
-   [Navigace hypertextový odkaz](#NavigatingBetweenXAMLPages)  
  
-   [Fragment navigace](#FragmentNavigation)  
  
-   [Navigační služby](#NavigationService)  
  
-   [Programová navigační službou navigace](#Programmatic_Navigation_with_the_Navigation_Service)  
  
-   [Doba platnosti navigace](#Navigation_Lifetime)  
  
-   [Nezapomeňte, navigace pomocí deník](#NavigationHistory)  
  
-   [Doba života stránky a deníku](#PageLifetime)  
  
-   [Zachování stavu obsahu s historie navigace](#RetainingContentStateWithNavigationHistory)  
  
-   [Soubory cookie](#Cookies)  
  
-   [Strukturované navigace](#Structured_Navigation)  
  
<a name="CreatingAXAMLPage"></a>   
### <a name="implementing-a-page"></a>Implementace stránky  
 V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], můžete přejít na několik typů obsahu, které obsahují objekty rozhraní .NET Framework, vlastní objekty, hodnot výčtu, uživatelských ovládacích prvků, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, a [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] soubory. Ale zjistíte, že obsah balíčku nejvíce běžné a pohodlný způsob je pomocí <xref:System.Windows.Controls.Page>. Kromě toho <xref:System.Windows.Controls.Page> implementuje funkce specifické pro navigační zlepšit jejich vzhled a zjednodušují vývoj.  
  
 Pomocí <xref:System.Windows.Controls.Page>, můžete implementovat deklarativně navigaci stránka [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu pomocí značek jako následující.  
  
 [!code-xaml[NavigationOverviewSnippets#Page1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]  
  
 A <xref:System.Windows.Controls.Page> která je implementovaná v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek má `Page` jako jeho kořenový element a vyžaduje, aby [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] deklaraci oboru názvů. `Page` Element obsahuje obsah, který chcete a přejděte do zobrazení. Přidat obsah nastavením `Page.Content` element vlastnosti, jak je znázorněno v následující kód.  
  
 [!code-xaml[NavigationOverviewSnippets#Page2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]  
  
 `Page.Content` může obsahovat pouze jeden podřízený element; v předchozím příkladu je obsah jednoho řetězce "Hello, stránky!" V praxi, obvykle použijete rozložení ovládacího prvku jako podřízeného prvku (viz [rozložení](../../../../docs/framework/wpf/advanced/layout.md)) a obsahovat napište svůj obsah.  
  
 Podřízené elementy `Page` se považují za obsah elementu <xref:System.Windows.Controls.Page> a v důsledku toho není nutné používat explicitní `Page.Content` deklarace. Následující kód je o deklarativní ekvivalent v předchozím příkladu.  
  
 [!code-xaml[NavigationOverviewSnippets#Page3XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]  
  
 V takovém případě `Page.Content` bude automaticky nastavena s podřízených elementů `Page` elementu. Další informace najdete v tématu [modelu obsahu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
 Pouze značek <xref:System.Windows.Controls.Page> je užitečná pro zobrazení obsahu. Ale <xref:System.Windows.Controls.Page> můžete také ovládací prvky zobrazení, které umožňují uživatelům interakci s hledanou stránkou, a může reagovat na interakci s uživatelem zpracování událostí a volání logiku aplikace. Interaktivní <xref:System.Windows.Controls.Page> je implementována pomocí kombinace značek a kódu, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
 [!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]  
  
 Povolit soubor značek a kódu soubor používat společně, následující konfigurace je potřeba:  
  
-   V kódu `Page` musí obsahovat element `x:Class` atribut. Když je aplikace vytvářena, existenci `x:Class` ve značkách souboru způsobí, že [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] k vytvoření `partial` třídu odvozenou od <xref:System.Windows.Controls.Page> a má název, který je zadán `x:Class` atribut. To vyžaduje přidání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklaraci oboru názvů pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schématu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Generovaný objekt `partial` třída implementuje `InitializeComponent`, tzv. k registraci události a nastavte vlastnosti, které jsou implementované v kódu.  
  
-   V kódu, musí být třída `partial` třídy se stejným názvem, která je zadána `x:Class` atribut ve značce a musí být odvozeny od <xref:System.Windows.Controls.Page>. To umožňuje souboru kódu, který má být spojen s `partial` třídu, která se vygeneruje pro soubor značek, když je aplikace vytvářena (najdete v části [vytváření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
-   V modelu code-behind <xref:System.Windows.Controls.Page> třída musí implementovat konstruktor, který volá `InitializeComponent` metoda. `InitializeComponent` je implementována ve kód je generována souboru `partial` třída registrace události a nastavte vlastnosti, které jsou definovány v kódu.  
  
> [!NOTE]
>  Když přidáte novou <xref:System.Windows.Controls.Page> do vašeho projektu pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Controls.Page> je implementovaná pomocí značek a kódu, a obsahuje nezbytné konfigurace k vytvoření přidružení mezi soubory značek a kódu jako popsané v tomto poli.  
  
 Jakmile máte <xref:System.Windows.Controls.Page>, můžete přejít k němu. Chcete-li určit první <xref:System.Windows.Controls.Page> , aplikace přejde na, budete muset nakonfigurovat spuštění <xref:System.Windows.Controls.Page>.  
  
<a name="Configuring_a_Start_Page"></a>   
### <a name="configuring-a-start-page"></a>Konfigurace úvodní stránky  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] vyžadovat určité množství infrastruktury aplikací pro hostování v prohlížeči. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], <xref:System.Windows.Application> třída je součástí definice aplikace, která vytvoří infrastrukturu požadovanou aplikaci (viz [přehled správy aplikací](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
 Definice aplikace je obvykle implementovaná pomocí značek a kódu, souborem značek, který je nakonfigurovaný jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` položky. Toto je definice aplikace pro [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
 [!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
 [!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]  
  
 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Jeho definice aplikace můžete použít k určení spuštění <xref:System.Windows.Controls.Page>, který je <xref:System.Windows.Controls.Page> automaticky při načtené [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] spuštění. To provedete nastavením <xref:System.Windows.Application.StartupUri%2A> vlastnost s [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] pro požadovanou <xref:System.Windows.Controls.Page>.  
  
> [!NOTE]
>  Ve většině případů <xref:System.Windows.Controls.Page> je buď zkompilovat do nebo nasadit pomocí aplikace. V těchto případech [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] identifikující <xref:System.Windows.Controls.Page> je sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], který je [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] uložená *pack* schéma. Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] jsou popsané v další [Pack identifikátory URI v grafickém subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md). Můžete také přejít k obsahu použít schéma http, která je popsána níže.  
  
 Můžete nastavit <xref:System.Windows.Application.StartupUri%2A> deklarativně ve značce, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 V tomto příkladu `StartupUri` s relativní pack nastavený atribut [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] identifikující HomePage.xaml. Když [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je spuštění HomePage.xaml automaticky přešli a zobrazit. Tento postup je znázorněn podle na následujícím obrázku, který ukazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] který byl spuštěn z webového serveru.  
  
 ![Stránka XBAP](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure9.png "NavigationOverviewFigure9")  
  
> [!NOTE]
>  Další informace týkající se vývoje a nasazení [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], najdete v části [přehled aplikace prohlížeče XAML WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md) a [nasazení aplikace WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
<a name="ConfiguringAXAMLPage"></a>   
### <a name="configuring-the-host-windows-title-width-and-height"></a>Konfigurace názvu, šířku a výšku okna hostitele  
 Jednou z věcí může dojít k tomu z předchozí obrázek je, že je název prohlížeče a na kartě panelu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Kromě toho se dlouho, název není atraktivní ani informativní. Z tohoto důvodu <xref:System.Windows.Controls.Page> nabízí způsob, jak můžete změnit název, nastavení <xref:System.Windows.Controls.Page.WindowTitle%2A> vlastnost. Kromě toho můžete nakonfigurovat šířku a výšku okna prohlížeče nastavením <xref:System.Windows.Controls.Page.WindowWidth%2A> a <xref:System.Windows.Controls.Page.WindowHeight%2A>, v uvedeném pořadí.  
  
 <xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page.WindowHeight%2A> lze nastavit deklarativně ve značce, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 Výsledkem je znázorněno na následujícím obrázku.  
  
 ![Název okna, výška a šířka](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure2.png "NavigationOverviewFigure2")  
  
<a name="NavigatingBetweenXAMLPages"></a>   
### <a name="hyperlink-navigation"></a>Navigace hypertextový odkaz  
 Typické [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] se skládá z několika stránek. Nejjednodušší způsob, jak přecházejí z jedné stránky na jiný je použití <xref:System.Windows.Documents.Hyperlink>. Deklarativně můžete přidat <xref:System.Windows.Documents.Hyperlink> k <xref:System.Windows.Controls.Page> pomocí `Hyperlink` element, který se zobrazí v následující kód.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 A `Hyperlink` prvek vyžaduje následující:  
  
-   Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> přejděte na, jak je stanoveno `NavigateUri` atribut.  
  
-   Obsahu, můžete kliknutím na uživatele k zahájení navigace, například textu a obrázků (pro obsah, který `Hyperlink` element může obsahovat naleznete v tématu <xref:System.Windows.Documents.Hyperlink>).  
  
 Následující obrázek ukazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] s <xref:System.Windows.Controls.Page> má <xref:System.Windows.Documents.Hyperlink>.  
  
 ![Stránka s hypertextovým odkazem](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure3.png "NavigationOverviewFigure3")  
  
 Jak jste zvyklí, kliknutím na tlačítko <xref:System.Windows.Documents.Hyperlink> způsobí, že [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] přejděte na <xref:System.Windows.Controls.Page> , je identifikovaný `NavigateUri` atribut. Kromě toho [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] přidá položku pro předchozí <xref:System.Windows.Controls.Page> v seznamu poslední stránky [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. To je znázorněno na následujícím obrázku.  
  
 ![Tlačítka Zpět a vpřed](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure4.png "NavigationOverviewFigure4")  
  
 A také podpora navigace z jednoho <xref:System.Windows.Controls.Page> do druhého, <xref:System.Windows.Documents.Hyperlink> také podporuje fragmentovat navigace.  
  
<a name="FragmentNavigation"></a>   
### <a name="fragment-navigation"></a>Fragment navigace  
 *Fragmentovat navigační* je navigace k obsahu fragment buď aktuální <xref:System.Windows.Controls.Page> nebo jiný <xref:System.Windows.Controls.Page>. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], fragment obsahu je obsah, který je obsažený v pojmenovaného elementu. Element s názvem je element, který má jeho `Name` nastaven atribut. Následující kód ukazuje pojmenovaná `TextBlock` elementu, který obsahuje fragment obsahu.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]  
  
 Pro <xref:System.Windows.Documents.Hyperlink> přejděte na fragment obsahu `NavigateUri` atributu musí zahrnovat následující:  
  
-   [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> s obsahu fragment přejděte k položce.  
  
-   Znak "#".  
  
-   Název elementu na <xref:System.Windows.Controls.Page> obsahující obsahu fragment.  
  
 Fragment [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] má následující formát.  
  
 *PageURI* `#` *ElementName*  
  
 Následující příklad ukazuje, `Hyperlink` nakonfigurovaný přejděte na fragment obsahu.  
  
 [!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]  
  
> [!NOTE]
>  Tato část popisuje výchozí implementace navigační fragment v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Můžete taky implementovat vlastní schéma fragment navigace, který částečně vyžaduje zpracování <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> událostí.  
  
> [!IMPORTANT]
>  Můžete přejít na fragmenty v přijít [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky (pouze kód [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory s `Page` jako kořenový element) pouze v případě, že na stránkách můžete procházet přes [!INCLUDE[TLA2#tla_http](../../../../includes/tla2sharptla-http-md.md)].  
>   
>  Ale přijít [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky můžete přejít na svůj vlastní fragmenty.  
  
<a name="NavigationService"></a>   
### <a name="navigation-service"></a>Navigační služby  
 Při <xref:System.Windows.Documents.Hyperlink> umožňuje uživatelům zahájit navigační ke konkrétní <xref:System.Windows.Controls.Page>, provádí práci při hledání a stahování stránky <xref:System.Windows.Navigation.NavigationService> třídy. V podstatě <xref:System.Windows.Navigation.NavigationService> poskytuje možnost zpracování žádost navigační jménem kód klienta, jako je například <xref:System.Windows.Documents.Hyperlink>. Kromě toho <xref:System.Windows.Navigation.NavigationService> implementuje vyšší úrovně podpory pro sledování a ovlivňování žádost o navigaci.  
  
 Když <xref:System.Windows.Documents.Hyperlink> po kliknutí na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] volání <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> vyhledat a stáhnout <xref:System.Windows.Controls.Page> v zadané pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Stažené <xref:System.Windows.Controls.Page> je převést na strom objektů, jejichž kořenový objekt je instance stažené <xref:System.Windows.Controls.Page>. Odkaz na kořenovém <xref:System.Windows.Controls.Page> objekt uložen v <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> vlastnost. Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro obsah, který byl přešli je uložené v <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> vlastnost, při <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> ukládá sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro poslední stránku, který byl přešli.  
  
> [!NOTE]
>  Je možné, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací mít více než jednu aktivní <xref:System.Windows.Navigation.NavigationService>. Další informace najdete v tématu [navigační hostitelů](#Navigation_Hosts) dál v tomto tématu.  
  
<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>   
### <a name="programmatic-navigation-with-the-navigation-service"></a>Programová navigační službou navigace  
 Nemusíte vědět o <xref:System.Windows.Navigation.NavigationService> Pokud navigační je implementovaný deklarativně pomocí značek <xref:System.Windows.Documents.Hyperlink>, protože <xref:System.Windows.Documents.Hyperlink> používá <xref:System.Windows.Navigation.NavigationService> vaším jménem. To znamená, že tak dlouho, dokud buď přímý nebo nepřímý nadřazeného <xref:System.Windows.Documents.Hyperlink> hostitel navigace (najdete v části [navigační hostitelů](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> budou moci najít a zpracovat pomocí služby navigační navigační hostitele žádost o navigaci.  
  
 Existují však situace při budete muset použít <xref:System.Windows.Navigation.NavigationService> přímo, včetně následujících:  
  
-   Když potřebujete k vytváření instancí <xref:System.Windows.Controls.Page> pomocí jiné než výchozí konstruktor.  
  
-   Když budete muset nastavit vlastnosti u <xref:System.Windows.Controls.Page> předtím, než přejdete k němu.  
  
-   Když <xref:System.Windows.Controls.Page> , potřebuje k přesměrováni do určen pouze v době běhu.  
  
 V těchto situacích, budete muset napsat kód pro prostřednictvím kódu programu navigační iniciovat volání <xref:System.Windows.Navigation.NavigationService.Navigate%2A> metodu <xref:System.Windows.Navigation.NavigationService> objektu. Která vyžaduje odkaz na získávání <xref:System.Windows.Navigation.NavigationService>.  
  
#### <a name="getting-a-reference-to-the-navigationservice"></a>Získávání odkaz na NavigationService  
 Z důvodů, které jsou popsané v [navigační hostitelů](#Navigation_Hosts) části [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace může mít více než jeden <xref:System.Windows.Navigation.NavigationService>. To znamená, že váš kód potřebuje způsob, jak vyhledat <xref:System.Windows.Navigation.NavigationService>, který je obvykle <xref:System.Windows.Navigation.NavigationService> , přešli na aktuální <xref:System.Windows.Controls.Page>. Můžete získat odkaz na <xref:System.Windows.Navigation.NavigationService> voláním `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> metoda. Chcete-li získat <xref:System.Windows.Navigation.NavigationService> , přešli na konkrétní <xref:System.Windows.Controls.Page>, předáte odkaz na <xref:System.Windows.Controls.Page> jako argument <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> metoda. Následující kód ukazuje, jak získat <xref:System.Windows.Navigation.NavigationService> pro aktuální <xref:System.Windows.Controls.Page>.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]  
  
 Jako zástupce pro vyhledání <xref:System.Windows.Navigation.NavigationService> pro <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> implementuje <xref:System.Windows.Controls.Page.NavigationService%2A> vlastnost. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Page> může získat pouze odkaz na jeho <xref:System.Windows.Navigation.NavigationService> při <xref:System.Windows.Controls.Page> vyvolá <xref:System.Windows.FrameworkElement.Loaded> událostí.  
  
#### <a name="programmatic-navigation-to-a-page-object"></a>Programové navigace k objektu stránky  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Navigation.NavigationService> prostřednictvím kódu programu přejděte na <xref:System.Windows.Controls.Page>. Programové navigace není nutná, protože <xref:System.Windows.Controls.Page> který je právě přešli se dá jenom vytvořit instance pomocí jednoho, jiné než výchozí konstruktor. <xref:System.Windows.Controls.Page> s jiné než výchozí konstruktor je uvedeno v následující kód a kód.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
 [!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]  
  
 <xref:System.Windows.Controls.Page> Který přejde <xref:System.Windows.Controls.Page> s jiné než výchozí konstruktor je uvedeno v následující kód a kód.  
  
 [!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]  
  
 Při <xref:System.Windows.Documents.Hyperlink> v tomto <xref:System.Windows.Controls.Page> je klikli, navigace je zahájeno vytváření instancí <xref:System.Windows.Controls.Page> přejděte na používání jiné než výchozí konstruktor a volání <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metoda. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> přijímá odkaz na objekt, <xref:System.Windows.Navigation.NavigationService> bude, přejděte místo sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
#### <a name="programmatic-navigation-with-a-pack-uri"></a>Programové navigace pomocí sadu identifikátor URI  
 Pokud potřebujete vytvořit sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] prostřednictvím kódu programu (když můžete určit pouze sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] na dobu běhu, třeba), můžete použít <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metoda. To je ukázáno v následujícím příkladu.  
  
 [!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]  
  
#### <a name="refreshing-the-current-page"></a>Aktualizovat aktuální stránku.  
 A <xref:System.Windows.Controls.Page> se nestáhne, pokud má stejné sadě [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] který je uložený v <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> vlastnost. Chcete-li vynutit [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] stáhnout aktuální stránku znovu, můžete volat <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> metoda, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]  
  
<a name="Navigation_Lifetime"></a>   
### <a name="navigation-lifetime"></a>Doba platnosti navigace  
 Existuje mnoho způsobů zahájíte navigaci, jak jste se seznámili s. Při inicializaci navigace, a když probíhá navigace, můžete sledovat a ovlivnit navigační pomocí následující události, které implementují <xref:System.Windows.Navigation.NavigationService>:  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigating>. Nastane, když se požaduje nové navigaci. Umožňuje zrušit navigaci.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Nastane pravidelně během stahování poskytnout informace o průběhu navigace.  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigated>. Nastane, když stránky je umístěn a stáhli.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Nastane, když je zastavena navigaci (voláním <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), nebo když je nový navigační požádali v průběhu aktuální navigaci.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. Nastane, když je vyvolána chyba při navigaci na požadovaný obsah.  
  
-   <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Nastane, když obsah, který byl přešli je načíst a analyzovat a zahájení vykreslování.  
  
-   <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Nastane, když začne navigační s fragmentem obsahu, který se stane:  
  
    -   Okamžitě pokud je požadovaný fragment aktuální obsah.  
  
    -   Po zdrojový obsah byl načten, pokud je požadovaný fragment jiný obsah.  
  
 Navigace události jsou vyvolávány v pořadí, ve kterém je zobrazená ve na následujícím obrázku.  
  
 ![Vývojový diagram navigace stránky](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure11.png "NavigationOverviewFigure11")  
  
 Obecně platí <xref:System.Windows.Controls.Page> není obavy o těchto událostech. Je více pravděpodobné, že aplikace problémem je, a proto tyto události jsou také vydané <xref:System.Windows.Application> třídy:  
  
-   <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>  
  
 Pokaždé, když <xref:System.Windows.Navigation.NavigationService> vyvolá událost, <xref:System.Windows.Application> třída vyvolá příslušné události. <xref:System.Windows.Controls.Frame> a <xref:System.Windows.Navigation.NavigationWindow> nabízet stejné události, které chcete zjišťovat navigace v rámci svých příslušných oborů.  
  
 V některých případech <xref:System.Windows.Controls.Page> by mohl zajímat tyto události. Například <xref:System.Windows.Controls.Page> může zpracovat <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> událostí k určení, zda chcete zrušit navigační od sám sebe. To je ukázáno v následujícím příkladu.  
  
 [!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]  
  
 Pokud zaregistrujete obslužná rutina s navigační událostí z <xref:System.Windows.Controls.Page>, stejně jako v předchozím příkladu, musíte také zrušit registraci obslužné rutiny události. Pokud to neuděláte, může být vedlejší účinky s ohledem na postupy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] navigační pamatuje <xref:System.Windows.Controls.Page> navigační pomocí deníku.  
  
<a name="NavigationHistory"></a>   
### <a name="remembering-navigation-with-the-journal"></a>Nezapomeňte, navigace pomocí deník  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] používá dva zásobníky pamatovat stránek, které jste přešli ze: back zásobníku a předat dál zásobníku. Pokud přejdete z aktuální <xref:System.Windows.Controls.Page> na nový <xref:System.Windows.Controls.Page> nebo předat dál na stávající <xref:System.Windows.Controls.Page>, aktuální <xref:System.Windows.Controls.Page> je přidán do *back zásobníku*. Pokud přejdete z aktuální <xref:System.Windows.Controls.Page> zpět na předchozí <xref:System.Windows.Controls.Page>, aktuální <xref:System.Windows.Controls.Page> je přidán do *dopředného zásobníku*. Back zásobníku, předat dál zásobníku a funkce pro správu, se souhrnně označují jako deník. Každá položka v back zásobníku a předat dál zásobník představuje instanci <xref:System.Windows.Navigation.JournalEntry> třídy a se označuje jako *položku deníku*.  
  
#### <a name="navigating-the-journal-from-internet-explorer"></a>Navigace deník z Internet Exploreru  
 Koncepčně, deník funguje stejně způsobem, jako **zpět** a **dál** tlačítka v [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] provést. Tyto aspekty znázorňuje následující obrázek.  
  
 ![Tlačítka Zpět a vpřed](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure4.png "NavigationOverviewFigure4")  
  
 Pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] který jsou hostitelem [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integruje deník do navigaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. To umožňuje uživatelům procházet stránky v [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pomocí **zpět**, **dál**, a **poslední stránky** tlačítka v [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Deník není integrovaný do [!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)] stejným způsobem, jako je pro [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] nebo Internet Explorer 8. Místo toho [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vykreslí navigaci substitute [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!IMPORTANT]
>  V [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], když uživatel přejde směrem od a zpět [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], v deníku jsou uchovány pouze položky deníku pro stránky, které nebyly zachovány zachování připojení. Informace o udržování stránky zachování připojení, najdete v článku [stránky životnost a deník](#PageLifetime) dál v tomto tématu.  
  
 Ve výchozím nastavení text pro každou <xref:System.Windows.Controls.Page> které se zobrazí v **poslední stránky** seznam [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] je [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro <xref:System.Windows.Controls.Page>. V řadě případů to není zvlášť srozumitelné pro uživatele. Naštěstí můžete změnit text pomocí jednoho následující možnosti:  
  
1.  Připojený `JournalEntry.Name` hodnota atributu.  
  
2.  `Page.Title` Hodnota atributu.  
  
3.  `Page.WindowTitle` Hodnotu atributu a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro aktuální <xref:System.Windows.Controls.Page>.  
  
4.  [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Pro aktuální <xref:System.Windows.Controls.Page>. (Výchozí)  
  
 Pořadí, ve kterém jsou uvedeny možnosti odpovídá pořadí priorit pro hledání textu. Například pokud `JournalEntry.Name` není nastaven, ostatní hodnoty jsou ignorovány.  
  
 Následující příklad používá `Page.Title` atribut změnit text, který se pro položku deníku.  
  
 [!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]  
  
#### <a name="navigating-the-journal-using-wpf"></a>Navigace deník pomocí grafického subsystému WPF  
 I když se uživatel může dostat deník pomocí **zpět**, **dál**, a **poslední stránky** v [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], můžete také přejít deník pomocí obou Deklarativní a programové mechanismy poskytované [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Jeden důvod k tomu je poskytnout vlastní navigační [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] na stránkách.  
  
 Podpora navigace deníku můžete přidat deklarativně pomocí příkazů navigační vystavené <xref:System.Windows.Input.NavigationCommands>. Následující příklad ukazuje, jak používat `BrowseBack` příkaz navigace.  
  
 [!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]  
  
 Deník prostřednictvím kódu programu můžete přejít pomocí jedné z následujících členů <xref:System.Windows.Navigation.NavigationService> třídy:  
  
-   <xref:System.Windows.Navigation.NavigationService.GoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.GoForward%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>  
  
 Také deník programově, jak je popsáno v manipulovat [podpůrné stav obsahu s historie navigace](#RetainingContentStateWithNavigationHistory) dál v tomto tématu.  
  
<a name="PageLifetime"></a>   
### <a name="page-lifetime-and-the-journal"></a>Doba života stránky a deníku  
 Vezměte v úvahu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] s několika stránek, které obsahují bohaté obsah, včetně obrázků, animace a média. Nároky na paměť pro stránky takovéto může být poměrně rozsáhlé, zvlášť pokud videa a zvuku médium se používá. Vzhledem k tomu, že deník "pamatuje" stránky, které byly přešli, například [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] může rychle využívat znatelné i velké množství paměti.  
  
 Z tohoto důvodu je výchozí chování deník uložit <xref:System.Windows.Controls.Page> metadata v každé položky deníku spíše než odkaz na <xref:System.Windows.Controls.Page> objektu. Když je položka deníku přešli, jeho <xref:System.Windows.Controls.Page> metadata se používá k vytvoření nové instance zadaného <xref:System.Windows.Controls.Page>. V důsledku toho každý <xref:System.Windows.Controls.Page> , která má dobu života, která je zobrazená ve na následujícím obrázku.  
  
 ![Doba života stránky](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure10.PNG "NavigationOverviewFigure10")  
  
 I když na spotřebu paměti můžete uložit pomocí výchozí chování deníku, může snížit výkon vykreslování na stránku; reinstantiating <xref:System.Windows.Controls.Page> může být časově náročný, zejména v případě, že má spoustu obsah. Pokud je potřeba zachovat <xref:System.Windows.Controls.Page> instance do deníku, můžete psát na dvě techniky, jak to udělat. První, můžete programově přejít na <xref:System.Windows.Controls.Page> objekt voláním <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> metoda.  
  
 Druhý, můžete určit, že [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zachovat instanci <xref:System.Windows.Controls.Page> v deníku nastavením <xref:System.Windows.Controls.Page.KeepAlive%2A> vlastnost `true` (výchozí hodnota je `false`). Jak je znázorněno v následujícím příkladu, můžete nastavit <xref:System.Windows.Controls.Page.KeepAlive%2A> deklarativně v kódu.  
  
 [!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]  
  
 Životnost <xref:System.Windows.Controls.Page> který je zachováno je mírně odlišný od ten, který není. První <xref:System.Windows.Controls.Page> , je udržováno je přešli zachování připojení, je vytvořena instance podobně jako <xref:System.Windows.Controls.Page> , není zachováno. Ale protože instanci <xref:System.Windows.Controls.Page> se uchovávají v deníku, nikdy vytvoření instance znovu pro tak dlouho, dokud zůstává v deníku. V důsledku toho pokud <xref:System.Windows.Controls.Page> má inicializace logiku, která musí být volána pokaždé, když <xref:System.Windows.Controls.Page> je navigaci, přesuňte ho z konstruktoru do obslužné rutiny pro <xref:System.Windows.FrameworkElement.Loaded> událostí. Jak je znázorněno na následujícím obrázku <xref:System.Windows.FrameworkElement.Loaded> a <xref:System.Windows.FrameworkElement.Unloaded> události jsou vyvolány stále pokaždé, když <xref:System.Windows.Controls.Page> je přešli do a z, v uvedeném pořadí.  
  
 ![Když jsou vyvolány události načteno a uvolněno](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure17.png "NavigationOverviewFigure17")  
  
 Když <xref:System.Windows.Controls.Page> je udržována není aktivní, neměli byste z následujících:  
  
-   Odkaz na nebo libovolná součást úložiště.  
  
-   Zaregistrujte se na události, které nejsou implementované obslužné rutiny událostí.  
  
 Jedním z těchto vytvoří odkazy, které vynutí <xref:System.Windows.Controls.Page> pro zachování v paměti, i když byl odebrán z deníku.  
  
 Obecně platí, měli byste upřednostnit výchozí <xref:System.Windows.Controls.Page> chování, aby nebyl <xref:System.Windows.Controls.Page> zachování připojení. To však má důsledky stavu, které jsou popsané v další části.  
  
<a name="RetainingContentStateWithNavigationHistory"></a>   
### <a name="retaining-content-state-with-navigation-history"></a>Zachování stavu obsahu s historie navigace  
 Pokud <xref:System.Windows.Controls.Page> není zachovány zachování připojení, a obsahuje ovládací prvky pro shromažďování dat od uživatele, co se stane data, pokud uživatel přejde směrem od a zpět <xref:System.Windows.Controls.Page>? Z hlediska zkušeností uživatele, uživatel by měl očekávat data, která zadali dříve. Bohužel protože novou instanci třídy <xref:System.Windows.Controls.Page> je vytvořena s každou navigační ovládací prvky, že reinstantiated shromážděná data jsou a data budou ztracena.  
  
 Naštěstí Deník poskytuje podporu pro zapamatování dat mezi <xref:System.Windows.Controls.Page> navigací, včetně data ovládacího prvku. Konkrétně deníku záznam pro každou <xref:System.Windows.Controls.Page> funguje jako dočasné kontejner pro přidruženého <xref:System.Windows.Controls.Page> stavu. Následující kroky popisují, jak se používá tato podpora při <xref:System.Windows.Controls.Page> je navigaci z:  
  
1.  Položka pro aktuální <xref:System.Windows.Controls.Page> se přidá do deníku.  
  
2.  Stav <xref:System.Windows.Controls.Page> se uloží spolu položka deníku pro tuto stránku, která se přidá do back zásobníku.  
  
3.  Nové <xref:System.Windows.Controls.Page> je přešli.  
  
 Pokud stránky <xref:System.Windows.Controls.Page> je přešli zpět, deník, pomocí následujících kroků provést:  
  
1.  <xref:System.Windows.Controls.Page> Je vytvořena instance (položka nejvyšší deníku v back zásobníku).  
  
2.  <xref:System.Windows.Controls.Page> Je aktualizovat stavu, která byla uložená s deníku položku <xref:System.Windows.Controls.Page>.  
  
3.  <xref:System.Windows.Controls.Page> Je přešli zpět.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automaticky použije tuto podporu, v případě použití na následující ovládací prvky <xref:System.Windows.Controls.Page>:  
  
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
  
 Pokud <xref:System.Windows.Controls.Page> používá tyto prvky, data zadaná do nich je zapamatovaných napříč <xref:System.Windows.Controls.Page> navigací, jak je předvedeno podle **Oblíbené barva** <xref:System.Windows.Controls.ListBox> na následujícím obrázku.  
  
 ![Stránka s ovládacími prvky, které mějte na paměti, stav](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure13.png "NavigationOverviewFigure13")  
  
 Když <xref:System.Windows.Controls.Page> má ovládací prvky nejsou uvedeny v předchozím seznamu, nebo když stav je uložený ve vlastní objekty, budete muset napsat kód pro způsobit deník pamatovat stavu napříč <xref:System.Windows.Controls.Page> navigaci.  
  
 Pokud je třeba pamatovat malé stavu napříč <xref:System.Windows.Controls.Page> navigací, můžete použít vlastnosti závislosti (najdete v části <xref:System.Windows.DependencyProperty>) které jsou nakonfigurovány s <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> příznak metadat.  
  
 Pokud stav, vaše <xref:System.Windows.Controls.Page> je potřeba pamatovat napříč navigací se skládá z více částí dat, může být méně kódu náročné zapouzdření vašemu stavu do jedné třídy a implementovat <xref:System.Windows.Navigation.IProvideCustomContentState> rozhraní.  
  
 Pokud budete muset procházet různé stavy jedné <xref:System.Windows.Controls.Page>, bez nutnosti z <xref:System.Windows.Controls.Page> samostatně, můžete použít <xref:System.Windows.Navigation.IProvideCustomContentState> a <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.  
  
<a name="Cookies"></a>   
### <a name="cookies"></a>Soubory cookie  
 Jiné způsobem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ukládají data aplikace se soubory cookie, které se vytváří, aktualizovat a odstranit pomocí <xref:System.Windows.Application.SetCookie%2A> a <xref:System.Windows.Application.GetCookie%2A> metody. Soubory cookie, které můžete vytvořit v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jsou soubory cookie jsou libovolné části data, která se uloží aplikaci na klientský počítač během nebo mezi relacemi aplikace; použít stejné soubory cookie jiných typů webových aplikací. Cookie data obvykle trvá formu dvojici název/hodnota v následujícím formátu.  
  
 *Název* `=` *hodnota*  
  
 Pokud je předán data <xref:System.Windows.Application.SetCookie%2A>, spolu s <xref:System.Uri> umístění, u které je třeba nastavit soubor cookie, soubor cookie se vytvoří v paměti, a je k dispozici pouze po dobu trvání aktuální relaci aplikace. Tento typ souboru cookie, který se označuje jako *souboru cookie relace*.  
  
 K uložení souboru cookie mezi relacemi aplikace, je nutné přidat datum vypršení platnosti souboru cookie, v následujícím formátu.  
  
 *NÁZEV* `=` *HODNOTA* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`  
  
 Soubor cookie s datum vypršení platnosti je uložen v aktuální [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] složka dočasných souborů Internetu instalace do vypršení platnosti souboru cookie. Do souboru cookie se označuje jako *trvalého souboru cookie* protože zůstává v rámci relací aplikace.  
  
 Získat relace a trvalé soubory cookie pomocí volání <xref:System.Windows.Application.GetCookie%2A> metodu a předá <xref:System.Uri> umístění, kde byl nastaven soubor cookie s <xref:System.Windows.Application.SetCookie%2A> metoda.  
  
 Toto jsou některé způsoby, které soubory cookie jsou podporovány v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:  
  
-   [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] jak vytvářet a spravovat soubory cookie.  
  
-   Soubory cookie, které jsou vytvořené pomocí [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je přístupný z prohlížeče.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ze stejné domény můžete vytvořit a sdílet soubory cookie.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] a [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] stránky ze stejné domény může vytvářet a sdílet soubory cookie.  
  
-   Soubory cookie se odesílají při [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] a ztratit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky zkontrolujte webových požadavků.  
  
-   Obě nejvyšší úrovně [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] hostované v prvky IFRAME přístup soubory cookie.  
  
-   Podpora cookies v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je stejný pro všechny podporované prohlížeče.  
  
-   V [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], P3P zásady, které se vztahují na soubory cookie se berou v úvahu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zejména s ohledem na první strany a třetí strany [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Structured_Navigation"></a>   
### <a name="structured-navigation"></a>Strukturované navigace  
 Pokud potřebujete předat data z jednoho <xref:System.Windows.Controls.Page> na jiný, můžete předat data jako argumenty pro jiné než výchozí konstruktor <xref:System.Windows.Controls.Page>. Všimněte si, že pokud použijete tento postup, je nutné zachovat <xref:System.Windows.Controls.Page> zachování připojení; Pokud ne, při příštím přejdete <xref:System.Windows.Controls.Page>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] reinstantiates <xref:System.Windows.Controls.Page> pomocí výchozí konstruktor.  
  
 Alternativně vaší <xref:System.Windows.Controls.Page> můžete implementovat vlastnosti, které jsou nastavené s daty, která musí být předán. Věcí stát složité, ale když <xref:System.Windows.Controls.Page> musí předat data zpět do <xref:System.Windows.Controls.Page> , přešli na ni. Problém je, že navigační nenabízí nativní podporu mechanismy pro zaručit, že <xref:System.Windows.Controls.Page> se vrátí po je navigaci z. Navigace v podstatě nepodporuje sémantiku volání nebo vrátit. Chcete tento problém vyřešit [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje <xref:System.Windows.Navigation.PageFunction%601> třídu, která vám pomůže zajistit, aby <xref:System.Windows.Controls.Page> je vrácen do předvídatelný a strukturovaných způsobem. Další informace najdete v tématu [strukturovaných navigační přehled](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).  
  
<a name="The_NavigationWindow_Class"></a>   
## <a name="the-navigationwindow-class"></a>Okně navigace – třída  
 K tomuto bodu jste se seznámili škálu navigační služby, které jste se s největší pravděpodobností používat k vytváření aplikací s obsahem navigaci. Tyto služby byly popsané v kontextu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], i když nejsou omezeny na [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Moderních operačních systémů a aplikací systému Windows využívat výhod možností prohlížeče moderní uživatelům začlenit navigační stylu prohlížeče do samostatné aplikace. Běžné mezi příklady patří:  
  
-   **Word tezauru**: přejděte možnosti aplikace word.  
  
-   **Soubor Explorer**: procházení souborů a složek.  
  
-   **Průvodci**: rozdělení do více stránek, které lze procházet mezi složitý úkol. Příkladem je Průvodce součástmi systému Windows, která zpracovává přidávání a odebírání funkce systému Windows.  
  
 Do samostatné aplikace zahrnout navigační stylu prohlížeče, můžete použít <xref:System.Windows.Navigation.NavigationWindow> třídy. <xref:System.Windows.Navigation.NavigationWindow> odvozená z <xref:System.Windows.Window> a rozšiřuje si ho stejným podporu pro navigaci, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] poskytnout. Můžete použít <xref:System.Windows.Navigation.NavigationWindow> jako hlavní okno samostatná aplikace, nebo jako sekundární okno například dialogové okno.  
  
 K implementaci <xref:System.Windows.Navigation.NavigationWindow>, stejně jako u většiny třídy nejvyšší úrovně v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>a tak dále), můžete použít kombinaci značek a kódu. To je ukázáno v následujícím příkladu.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
 [!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]  
  
 Tento kód vytvoří <xref:System.Windows.Navigation.NavigationWindow> , automaticky přejde na <xref:System.Windows.Controls.Page> (HomePage.xaml) Pokud <xref:System.Windows.Navigation.NavigationWindow> je otevřen. Pokud <xref:System.Windows.Navigation.NavigationWindow> je hlavní okno aplikace, můžete použít `StartupUri` atribut spustíte. To ukazuje následující kód.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]  
  
 Následující obrázek ukazuje <xref:System.Windows.Navigation.NavigationWindow> jako hlavní okno samostatné aplikace.  
  
 ![Hlavní okno](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure18.png "NavigationOverviewFigure18")  
  
 Z obrázku, můžete uvidíte, že <xref:System.Windows.Navigation.NavigationWindow> má název, i když nebyla nastavena <xref:System.Windows.Navigation.NavigationWindow> implementace kód z předchozího příkladu. Místo toho je název nastavit pomocí <xref:System.Windows.Controls.Page.WindowTitle%2A> vlastnosti, která je znázorněno v následujícím kódu.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]  
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]  
  
 Nastavení <xref:System.Windows.Controls.Page.WindowWidth%2A> a <xref:System.Windows.Controls.Page.WindowHeight%2A> vlastnosti ovlivní také <xref:System.Windows.Navigation.NavigationWindow>.  
  
 Obvykle můžete implementovat vlastní <xref:System.Windows.Navigation.NavigationWindow> když potřebujete přizpůsobit své chování nebo její vzhled. Pokud ani to uděláte, můžete použít zástupce. Pokud zadáte sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] z <xref:System.Windows.Controls.Page> jako <xref:System.Windows.Application.StartupUri%2A> v samostatná aplikace, <xref:System.Windows.Application> automaticky vytvoří <xref:System.Windows.Navigation.NavigationWindow> hostitele <xref:System.Windows.Controls.Page>. Následující kód ukazuje, jak povolit tuto funkci.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]  
  
 Pokud budete chtít okno sekundární aplikace například dialogové okno s být <xref:System.Windows.Navigation.NavigationWindow>, můžete použít kód v následujícím příkladu ho otevřete.  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
 [!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]  
  
 Následující obrázek znázorňuje výsledek.  
  
 ![Dialogové okno](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure19.png "NavigationOverviewFigure19")  
  
 Jak vidíte, <xref:System.Windows.Navigation.NavigationWindow> zobrazí [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]– styl **zpět** a **dál** tlačítka, který umožní uživatelům procházet deníku. Tato tlačítka zadejte stejné prostředí pro uživatele, jak je znázorněno na následujícím obrázku.  
  
 ![Tlačítka v okně Navigace zpět a vpřed](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure20.png "NavigationOverviewFigure20")  
  
 Pokud vaše stránky poskytují vlastní podporu navigace deníku a uživatelského rozhraní, můžete skrýt **zpět** a **dál** tlačítka zobrazená podle <xref:System.Windows.Navigation.NavigationWindow> nastavením hodnoty <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> vlastnost `false`.  
  
 Alternativně můžete použít vlastní nastavení podpory v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nahradit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z <xref:System.Windows.Navigation.NavigationWindow> sám sebe.  
  
<a name="Frame_in_Standalone_Applications"></a>   
## <a name="the-frame-class"></a>Třída rámce  
 I v prohlížeči a <xref:System.Windows.Navigation.NavigationWindow> jsou windows navigaci obsah hostitele. V některých případech aplikace mají obsah, který nemusí být hostované celé okno. Místo toho se takový obsah hostovanou v rámci jiný obsah. Navigaci obsah můžete vložit do jiného obsahu pomocí <xref:System.Windows.Controls.Frame> třídy. <xref:System.Windows.Controls.Frame> podporuje stejné jako <xref:System.Windows.Navigation.NavigationWindow> a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
 Následující příklad ukazuje, jak přidat <xref:System.Windows.Controls.Frame> k <xref:System.Windows.Controls.Page> deklarativně pomocí `Frame` elementu.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]  
  
 Nastaví tento kód `Source` atribut `Frame` element s sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro <xref:System.Windows.Controls.Page> , <xref:System.Windows.Controls.Frame> by měl původně přejděte do. Následující obrázek ukazuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] s <xref:System.Windows.Controls.Page> má <xref:System.Windows.Controls.Frame> který navigací mezi více stránkách.  
  
 ![Rámce, který má navigaci mezi stránkami,](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure5.png "NavigationOverviewFigure5")  
  
 Nemáte pouze pomocí <xref:System.Windows.Controls.Frame> uvnitř obsah <xref:System.Windows.Controls.Page>. Je také společné pro hostitele <xref:System.Windows.Controls.Frame> uvnitř obsah <xref:System.Windows.Window>.  
  
 Ve výchozím nastavení <xref:System.Windows.Controls.Frame> pouze používá vlastní deníku neexistuje jiná deníku. Pokud <xref:System.Windows.Controls.Frame> je součástí obsah, který je umístěn uvnitř buď <xref:System.Windows.Navigation.NavigationWindow> nebo [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame> využívá deník, který patří do <xref:System.Windows.Navigation.NavigationWindow> nebo [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. V některých případech ale <xref:System.Windows.Controls.Frame> může být potřeba zodpovědná za vlastní deníku. Jeden důvod k tomu je umožnit deníku navigace v rámci stránek, které jsou hostované <xref:System.Windows.Controls.Frame>. Tento koncept je znázorněn podle na následujícím obrázku.  
  
 ![Diagram rámce a stránky](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure7.png "NavigationOverviewFigure7")  
  
 V takovém případě můžete nakonfigurovat <xref:System.Windows.Controls.Frame> používat vlastní deníku nastavením <xref:System.Windows.Controls.Frame.JournalOwnership%2A> vlastnost <xref:System.Windows.Controls.Frame> k <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. To ukazuje následující kód.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]  
  
 Následující obrázek ukazuje účinek navigace v rámci <xref:System.Windows.Controls.Frame> používající vlastní deníku.  
  
 ![Rámce, který používá svou vlastní deníku](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure8.png "NavigationOverviewFigure8")  
  
 Všimněte si, že položky deníku jsou seřazeny podle navigaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v <xref:System.Windows.Controls.Frame>, spíše než [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)].  
  
> [!NOTE]
>  Pokud <xref:System.Windows.Controls.Frame> je součástí obsah, který je hostován v <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> používá vlastní deníku a v důsledku toho zobrazí vlastní navigační [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Pokud vyžaduje činnost koncového uživatele <xref:System.Windows.Controls.Frame> poskytnout vlastní deníku bez zobrazení navigaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], můžete skrýt, navigaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nastavením <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> k <xref:System.Windows.Visibility.Hidden>. To ukazuje následující kód.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]  
  
<a name="Navigation_Hosts"></a>   
## <a name="navigation-hosts"></a>Navigace hostitele  
 <xref:System.Windows.Controls.Frame> a <xref:System.Windows.Navigation.NavigationWindow> jsou třídy, které jsou známé jako hostitele navigace. A *navigační hostitele* je třída, která můžete přejít k a zobrazit obsah. K tomu, každý hostitel navigační používá vlastní <xref:System.Windows.Navigation.NavigationService> a deníku. Základní konstrukce navigační hostitele je vidět na následujícím obrázku.  
  
 ![Navigátor diagramy](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure15.png "NavigationOverviewFigure15")  
  
 V podstatě to umožňuje <xref:System.Windows.Navigation.NavigationWindow> a <xref:System.Windows.Controls.Frame> zajistit stejné navigační podpory, který [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] poskytuje, když jsou hostované v prohlížeči.  
  
 Kromě použití <xref:System.Windows.Navigation.NavigationService> a deníku, navigace hostitelů implementovat stejné členy, <xref:System.Windows.Navigation.NavigationService> implementuje. Tento koncept je znázorněn podle na následujícím obrázku.  
  
 ![Deník v rámci a v okně navigace](../../../../docs/framework/wpf/app-development/media/naivgationoverviewfigure24.png "NaivgationOverviewFigure24")  
  
 Umožňuje programu navigační podporu přímo proti. To může zvažte, pokud je třeba zadat vlastní navigační [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro <xref:System.Windows.Controls.Frame> který je hostován v <xref:System.Windows.Window>. Kromě toho oba typy implementace další, navigace členů, včetně `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) a `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), které umožňují vytvořit výčet položky deníku v pozadí zásobník a jejich předávání zásobníku, v uvedeném pořadí.  
  
 Jak už bylo zmíněno dříve, může existovat více než jeden deníku v aplikaci. Následující obrázek poskytuje příklad, pokud k tomu může dojít.  
  
 ![Více deníků v jedné aplikaci](../../../../docs/framework/wpf/app-development/media/naivgationoverviewfigure25.png "NaivgationOverviewFigure25")  
  
<a name="Navigating_to_Content_Other_than_Pages"></a>   
## <a name="navigating-to-content-other-than-xaml-pages"></a>Navigace k obsahu než stránky XAML  
 V tomto tématu se <xref:System.Windows.Controls.Page> a aktualizací Service pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] již byly použity k předvedení různé možnosti navigační [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Ale <xref:System.Windows.Controls.Page> tedy zkompilovat do aplikace není pouze typ obsahu, který lze procházet k a aktualizací Service pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nejsou jediný způsob, jak identifikovat obsah.  
  
 Jak v této části ukážeme, můžete také přejít na přijít [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] souborů a objektů.  
  
<a name="Navigating_to_Loose_XAML_Files"></a>   
### <a name="navigating-to-loose-xaml-files"></a>Navigace k souborům přijít XAML  
 Ztratit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je soubor s následujícími charakteristikami:  
  
-   Obsahuje pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (tj. žádný kód).  
  
-   Obsahuje deklarace odpovídající oboru názvů.  
  
-   Má příponu názvu souboru XAML.  
  
 Zvažte například následující obsah, který je uložený jako přijít [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru Person.xaml.  
  
 [!code-xaml[NavigationOverviewSnippets#LooseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]  
  
 Když dvakrát kliknete na soubor, otevře se prohlížeč a přejde na a zobrazí obsah. To je znázorněno na následujícím obrázku.  
  
 ![Zobrazení obsahu souboru Person.XAML](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure21.png "NavigationOverviewFigure21")  
  
 Můžete zobrazit ztratit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru z následujícího:  
  
-   Web na místním počítači, intranetu nebo Internetu.  
  
-   A [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] sdílené složky.  
  
-   Místní disk.  
  
 Ztratit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor lze přidat k oblíbeným položkám v prohlížeči, nebo se v prohlížeči na domovskou stránku.  
  
> [!NOTE]
>  Další informace o publikování a spuštění volné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] najdete v části stránky, [nasazení aplikace WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
 Jedním z omezení s ohledem na přijít [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je, že můžou hostovat pouze obsah, který je bezpečné pro spuštění v částečné důvěryhodnosti. Například `Window` nemůže být kořenový prvek ztratit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru. Další informace najdete v tématu [WPF částečné důvěryhodnosti zabezpečení](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_Frame"></a>   
### <a name="navigating-to-html-files-by-using-frame"></a>Procházení souborů ve formátu HTML pomocí rámce  
 Podle očekávání, můžete také přejít na [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]. Jednoduše je potřeba zadat [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] používající schéma protokolu http. Například následující [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ukazuje <xref:System.Windows.Controls.Frame> , přejde [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] stránky.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]  
  
 Přejdete na [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] vyžaduje speciální oprávnění. Například, nejde přejít z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] který se spouští v karanténě zabezpečení Internetu zóny částečnou důvěryhodností. Další informace najdete v tématu [WPF částečné důvěryhodnosti zabezpečení](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>   
### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Procházení souborů ve formátu HTML pomocí ovládacího prvku WebBrowser  
 <xref:System.Windows.Controls.WebBrowser> Podporuje ovládací prvek [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] hostování dokumentu, navigace a skript nebo spravovaný kód interoperability. Podrobné informace o <xref:System.Windows.Controls.WebBrowser> řízení najdete v tématu <xref:System.Windows.Controls.WebBrowser>.  
  
 Jako <xref:System.Windows.Controls.Frame>, navigační k [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] pomocí <xref:System.Windows.Controls.WebBrowser> vyžaduje speciální oprávnění. Například z částečně důvěryhodné aplikace, můžete přejít pouze [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] umístěný v lokalitě původu. Další informace najdete v tématu [WPF částečné důvěryhodnosti zabezpečení](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_Objects"></a>   
### <a name="navigating-to-custom-objects"></a>Navigace na vlastní objekty  
 Pokud máte data, která je uložena jako vlastní objekty, je vytvoření jeden způsob zobrazení dat <xref:System.Windows.Controls.Page> s obsahem, který je vázán k těmto objektům (najdete v části [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md)). Pokud nepotřebujete režijní náklady na celou stránku k zobrazení objektů pro vytváření, můžete přejít přímo na jejich místo.  
  
 Vezměte v úvahu `Person` třídu, která je implementovaná v následujícím kódu.  
  
 [!code-csharp[NavigateToObjectSnippets#PersonClassCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
 [!code-vb[NavigateToObjectSnippets#PersonClassCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]  
  
 Přejděte k němu, zavoláte <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> metoda, jak je ukázáno v následujícím kódu.  
  
 [!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]  
  
 [!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
 [!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]  
  
 Následující obrázek znázorňuje výsledek.  
  
 ![Na stránce, který odkazuje na třídu](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure22.png "NavigationOverviewFigure22")  
  
 Z tohoto obrázku vidíte, že užitečné, nezobrazí se. Ve skutečnosti se zobrazí hodnota je vrácenou hodnotu `ToString` metodu **osoba** objektu; ve výchozím nastavení, je to jediný hodnotu, která [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] lze použít k reprezentaci objektu. Může přepsat `ToString` metoda vrátí další důležité informace, i když bude stále pouze být řetězcová hodnota. Jedna metoda můžete použít, která využívá možnosti prezentace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , je použít šablonu data. Můžete implementovat šablonu dat, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] můžete přidružit objekt určitého typu. Následující kód ukazuje šablonu dat pro `Person` objektu.  
  
 [!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]  
  
 Tady je přidružen šabloně data `Person` typu pomocí `x:Type` – rozšíření značek v `DataType` atribut. Datová šablona pak váže `TextBlock` elementy (najdete v části <xref:System.Windows.Controls.TextBlock>) k vlastnosti `Person` – třída. Následující obrázek znázorňuje aktualizované vzhled `Person` objektu.  
  
 ![Navigace na třídu, která má šablonu dat](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure23.png "NavigationOverviewFigure23")  
  
 Výhodou této technice je konzistence získáte tím, že je mohli znovu použít šablonu data k zobrazení vašich objektů konzistentně kdekoli v aplikaci.  
  
 Další informace o šablonách dat najdete v tématu [přehled Ukázka dat](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpečení  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje podporu navigace [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] přesměrováni do přes Internet a povoluje aplikace jako hostitele obsahu třetích stran. K ochraně aplikace a uživatele z škodlivé chování, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje celou řadu funkcí zabezpečení, které jsou popsané v [zabezpečení](../../../../docs/framework/wpf/security-wpf.md) a [WPF částečné důvěryhodnosti zabezpečení](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Application.SetCookie%2A>  
 <xref:System.Windows.Application.GetCookie%2A>  
 [Přehled správy aplikací](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [Sbalení URI v technologii WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Přehled strukturované navigace](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)  
 [Přehled topologií navigace](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/app-development/navigation-how-to-topics.md)  
 [Nasazení aplikace WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
