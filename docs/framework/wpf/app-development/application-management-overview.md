---
title: "Přehled správy aplikací"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a881793c50a4ce506e752774e70e0904e30525c1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="application-management-overview"></a>Přehled správy aplikací
Všechny aplikace zpravidla sdílejí společnou sadu funkcí, které platí pro aplikaci na implementaci a správu. Toto téma obsahuje přehled funkcí v <xref:System.Windows.Application> třídu pro vytváření a Správa aplikací.  
   
  
## <a name="the-application-class"></a>Třída aplikace  
 V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], je běžné funkce obor aplikace zapouzdřené v <xref:System.Windows.Application> třídy. <xref:System.Windows.Application> Třída zahrnuje následující funkce:  
  
-   Sledování a interakci s životního cyklu aplikace.  
  
-   Načítání a zpracování parametry příkazového řádku.  
  
-   Zjišťování a zpracování neošetřených výjimek.  
  
-   Sdílení vlastnosti oboru aplikace a prostředky.  
  
-   Správa systému windows v samostatné aplikace.  
  
-   Sledování a správu navigace.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Jak provádět běžné úlohy pomocí třídy aplikace  
 Pokud vás zajímá není ve všech podrobností <xref:System.Windows.Application> třídy, v následující tabulce jsou uvedeny některé časté úlohy pro <xref:System.Windows.Application> a o způsobech je. Zobrazení související rozhraní API a témata, můžete najít další informace a ukázkový kód.  
  
|Úloha|Přístup|  
|----------|--------------|  
|Získat objekt, který představuje aktuální aplikace.|Použití <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> vlastnost.|  
|Přidat do aplikace úvodní obrazovky|V tématu [úvodní obrazovka přidání do aplikace WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Spuštění aplikace|Použití <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> metoda.|  
|Zastavte aplikaci|Použití <xref:System.Windows.Application.Shutdown%2A> metodu <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> objektu.|  
|Získat argumenty z příkazového řádku|Zpracování <xref:System.Windows.Application.Startup?displayProperty=nameWithType> událostí a použití <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> vlastnost. Příklad, naleznete v části <xref:System.Windows.Application.Startup?displayProperty=nameWithType> událostí.|  
|Získání a nastavení kód ukončení aplikace|Nastavit <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Application.Exit?displayProperty=nameWithType> obslužné rutiny události nebo volání <xref:System.Windows.Application.Shutdown%2A> metoda a předejte jí celé číslo.|  
|Zjistit a reagovat na neošetřených výjimek|Zpracování <xref:System.Windows.Application.DispatcherUnhandledException> událostí.|  
|Získání a nastavení rozsahu aplikace prostředky|Použití <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> vlastnost.|  
|Pomocí slovníku oboru aplikace prostředků|V tématu [pomocí slovníku oboru aplikace prostředků](../../../../docs/framework/wpf/app-development/how-to-use-an-application-scope-resource-dictionary.md).|  
|Získání a nastavení vlastnosti pro obor aplikace|Použití <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> vlastnost.|  
|Získat a uložit stav aplikace|V tématu [zachovat a obnovit vlastnosti oboru aplikace napříč relacemi aplikace](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).|  
|Správa dat bez kódu souborů, včetně zdrojových souborů, soubory obsahu a souborů lokality původu.|V tématu [prostředek aplikace WPF, obsah a datové soubory](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).|  
|Správa windows v samostatné aplikace|V tématu [WPF ve Windows – přehled](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).|  
|Sledování a správě navigace|V tématu [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>Definice aplikace  
 Abyste mohli využívat funkce <xref:System.Windows.Application> třídy, je nutné implementovat definice aplikace. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definice aplikace je třída, která je odvozena z <xref:System.Windows.Application> a je nakonfigurovaná s speciální [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] nastavení.  
  
### <a name="implementing-an-application-definition"></a>Implementace definice aplikace  
 Typické [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definice aplikace je implementovaná pomocí značek a kódu. To umožňuje používat značky deklarativně nastavit vlastnosti aplikace, prostředky, a zaregistrovat události, při zpracování událostí a implementace chování specifické pro aplikaci v kódu.  
  
 Následující příklad ukazuje, jak implementovat definice aplikace pomocí značek a kódu:  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Povolit soubor značek a kódu soubor používat společně, následující potřebuje provést:  
  
-   V kódu `Application` musí obsahovat element `x:Class` atribut. Když je aplikace vytvářena, existenci `x:Class` ve značkách souboru způsobí, že [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] k vytvoření `partial` třídu odvozenou od <xref:System.Windows.Application> a má název, který je zadán `x:Class` atribut. To vyžaduje přidání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklaraci oboru názvů pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schématu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).  
  
-   V kódu, musí být třída `partial` třídy se stejným názvem, která je zadána `x:Class` v značek a musí být odvozeny od <xref:System.Windows.Application>. To umožňuje souboru kódu, který má být spojen s `partial` třídu, která se vygeneruje pro soubor značek, když je aplikace vytvářena (najdete v části [vytváření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
>  Když vytvoříte nový projekt aplikace WPF nebo projekt pomocí aplikace prohlížeče WPF [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], definice aplikace je zahrnutý ve výchozím nastavení a je definován pomocí značek a kódu.  
  
 Tento kód je minimální, který je potřeba implementovat definice aplikace. Však další [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] konfigurace je potřeba provést k definici aplikace před sestavení a spuštění aplikace.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Konfigurace aplikace definici nástroje MSBuild  
 Samostatné aplikace a [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] vyžadovat provedení určité úrovně infrastruktury ještě před jejich spuštěním. Nejdůležitější část této infrastruktury je vstupní bod. Když uživatel spustí aplikaci, operační systém zavolá vstupní bod, který je dobře známé funkce pro spuštění aplikace.  
  
 Vývojáři mají obvyklým potřebná k zápisu některé nebo všechny tento kód sami, v závislosti na technologie. Ale [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] generuje tento kód pro vás, když kód soubor definice aplikace je nakonfigurovaný jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` položky, jak je znázorněno v následujícím [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] soubor projektu:  
  
```xml  
<Project   
  DefaultTargets="Build"  
                        xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  ...  
  <ApplicationDefinition Include="App.xaml" />  
  <Compile Include="App.xaml.cs" />  
  ...  
</Project>  
```  
  
 Protože soubor kódu obsahuje kód, je označeno [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` položky, jako je normální.  
  
 Používání těchto [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] způsobí, že konfigurace, které soubory značek a kódu definice aplikace [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] pro generování kódu takto:  
  
 [!code-csharp[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode1)]
 [!code-vb[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode1)]  
[!code-csharp[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode2)]
[!code-vb[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode2)]  
  
 Výsledný kód rozšiřuje vaše definice aplikace další infrastrukturu kód, který obsahuje vstupní bod metody `Main`. <xref:System.STAThreadAttribute> Je použit atribut `Main` metoda, která označuje, že hlavní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro přístup z více vláken [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace je STA vláken, který je vyžadován pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace. Při volání, `Main` vytvoří novou instanci třídy `App` před voláním `InitializeComponent` metoda registrace události a nastavte vlastnosti, které jsou implementované v kódu. Protože `InitializeComponent` se vygeneruje, nemusíte explicitně volání `InitializeComponent` z definice aplikace, jako je tomu u <xref:System.Windows.Controls.Page> a <xref:System.Windows.Window> implementace. Nakonec <xref:System.Windows.Application.Run%2A> metoda je volána a spusťte aplikaci.  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Získávání aktuální aplikace.  
 Protože funkce <xref:System.Windows.Application> třídy jsou sdíleny aplikace, může existovat pouze jedna instance <xref:System.Windows.Application> třídy za <xref:System.AppDomain>. Tím nepomůže, <xref:System.Windows.Application> třída je implementovaný jako třída singleton (najdete v části [implementace jednotlivý prvek v C#](http://go.microsoft.com/fwlink/?LinkId=100567)), který vytvoří jednu instanci sám sebe a poskytuje sdílený přístup k němu s `static` <xref:System.Windows.Application.Current%2A> Vlastnost.  
  
 Následující kód ukazuje, jak získat odkaz na <xref:System.Windows.Application> objekt pro aktuální <xref:System.AppDomain>.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A>Vrátí odkaz na instanci <xref:System.Windows.Application> třídy. Pokud chcete odkaz na vaši <xref:System.Windows.Application> odvozené třídy musí převést hodnotu <xref:System.Windows.Application.Current%2A> vlastnost, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Si můžete prohlédnout hodnotu <xref:System.Windows.Application.Current%2A> v libovolném bodě životnost <xref:System.Windows.Application> objektu. Nicméně byste měli být opatrní. Po <xref:System.Windows.Application> vytvoření instance třídy, existuje období, během které je stav <xref:System.Windows.Application> objektu je nekonzistentní. Během této doby <xref:System.Windows.Application> provádí různé úlohy inicializace, které vyžaduje váš kód ke spuštění, včetně zřízení infrastruktury aplikace, nastavení vlastností a registraci události. Pokud se pokusíte použít <xref:System.Windows.Application> objektu během této doby kódu může mít neočekávané výsledky, zvlášť pokud závisí na různých <xref:System.Windows.Application> se nastaveny vlastnosti.  
  
 Když <xref:System.Windows.Application> nedokončí svoji práci inicializace skutečně začne celé jeho životnosti.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Životního cyklu aplikací  
 Životnost [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace je označena kvalifikátorem několik událostí, které jsou vydané <xref:System.Windows.Application> pokaždé, když je aplikace spuštěna, má se aktivovat a deaktivovat a byla vypnuta.  
  
  
<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Úvodní obrazovka  
 Počínaje [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], můžete zadat obrázek, který se použije v okně spuštění nebo *úvodní obrazovka*. <xref:System.Windows.SplashScreen> Třída umožňuje snadno zobrazit okno spuštění při načítání aplikace. <xref:System.Windows.SplashScreen> Okno se vytvoří a zobrazí před <xref:System.Windows.Application.Run%2A> je volána. Další informace najdete v tématu [doba spuštění aplikace](../../../../docs/framework/wpf/advanced/application-startup-time.md) a [úvodní obrazovka přidání do aplikace WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Spuštění aplikace  
 Po <xref:System.Windows.Application.Run%2A> nazývá a aplikace je inicializován, je připraven ke spuštění aplikace. Aktuálně jsou označeny při <xref:System.Windows.Application.Startup> událost se vyvolá:  
  
 [!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind1)]
 [!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind1)]  
[!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind2)]
[!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind2)]  
  
 Nejběžnější krokem v životního cyklu aplikace, v tomto okamžiku je zobrazíte [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Showing_a_User_Interface"></a>   
### <a name="showing-a-user-interface"></a>Zobrazuje uživatelské rozhraní  
 Většina samostatné [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] aplikace otevřete <xref:System.Windows.Window> kdy začnou systémem. <xref:System.Windows.Application.Startup> Obslužné rutiny události je jedno umístění, ze kterého můžete k tomu, jak je ukázáno v následujícím kódu.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  První <xref:System.Windows.Window> Chcete-li vytvořit v samostatné instanci aplikace změní hlavní okno aplikace ve výchozím nastavení. To <xref:System.Windows.Window> objekt odkazuje <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> vlastnost. Hodnota <xref:System.Windows.Application.MainWindow%2A> vlastnost může být změněna programově, pokud jiné časové období než první instanci <xref:System.Windows.Window> by měl být hlavní okno.  
  
 Když [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] první spuštění, se budou s největší pravděpodobností přejděte na <xref:System.Windows.Controls.Page>. To je znázorněno v následujícím kódu.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 Pokud zpracováváte <xref:System.Windows.Application.Startup> pouze otevřít <xref:System.Windows.Window> nebo přejděte na <xref:System.Windows.Controls.Page>, můžete nastavit `StartupUri` místo něj atribut značek.  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Application.StartupUri%2A> ze samostatné aplikace pro otevření <xref:System.Windows.Window>.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Application.StartupUri%2A> z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] přejděte na <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Tento kód má stejný účinek jako předchozí kód pro otevření okna.  
  
> [!NOTE]
>  Další informace o navigace, najdete v části [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 Je třeba zpracovat <xref:System.Windows.Application.Startup> událostí otevřít <xref:System.Windows.Window> Pokud budete muset vytvořit instanci pomocí jiné než výchozí konstruktor, budete muset nastavit jeho vlastnosti nebo se přihlásit k odběru události před zobrazením je nebo je potřeba zpracovat žádných argumentů příkazového řádku, nebyly zadány, když byla aplikace spuštěná.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Zpracování argumentů příkazového řádku  
 V [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)], samostatné aplikace může být spuštěn z příkazového řádku nebo z plochy. V obou případech může být předán argumenty příkazového řádku k aplikaci. Následující příklad ukazuje, aplikace, který je spuštěn s jediným argumentem příkazového řádku, "/ StartMinimized":  
  
 `wpfapplication.exe /StartMinimized`  
  
 Během inicializace aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] načte argumenty příkazového řádku z operačního systému a předá je <xref:System.Windows.Application.Startup> obslužné rutiny události prostřednictvím <xref:System.Windows.StartupEventArgs.Args%2A> vlastnost <xref:System.Windows.StartupEventArgs> parametr. Můžete načíst a uložit argumenty příkazového řádku pomocí kódu podobně jako tento.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 Kód obslužné rutiny <xref:System.Windows.Application.Startup> zkontrolujte zda **/StartMinimized** byl zadaný argument příkazového řádku; Pokud ano, otevře se hlavní okno s <xref:System.Windows.WindowState> z <xref:System.Windows.WindowState.Minimized>. Všimněte si, že <xref:System.Windows.Window.WindowState%2A> musí být nastavena vlastnost prostřednictvím kódu programu, hlavní <xref:System.Windows.Window> musí být explicitně otevřen v kódu.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]Nelze načíst a zpracovat argumenty příkazového řádku, protože jejich spouštění pomocí [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] nasazení (viz [nasazení aplikace WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)). Můžete však načíst a parametrů řetězce dotazu z adresy URL, které se používají ke spuštění je zpracovat.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Aplikace aktivace a deaktivace  
 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)]umožňuje uživatelům přepínat mezi aplikacemi. Nejběžnější způsob je pomocí kombinace kláves ALT + TAB. Aplikace je možné přepnout na pouze, pokud má zobrazené <xref:System.Windows.Window> , můžete vybrat uživatele. Aktuálně vybrané <xref:System.Windows.Window> je *aktivní okno* (také označované jako *popředí okno*) a je <xref:System.Windows.Window> která přijme vstup uživatele. Aplikace s aktivní okno *aktivní aplikační* (nebo *popředí aplikace*). Aplikace se změní na aktivní aplikace v následujících případech:  
  
-   Jeho spuštění a zobrazuje <xref:System.Windows.Window>.  
  
-   Uživatel přepíná z jiné aplikace tak, že vyberete <xref:System.Windows.Window> v aplikaci.  
  
 Můžete zjistit při aplikaci stane aktivní ve zpracování <xref:System.Windows.Application.Activated?displayProperty=nameWithType> událostí.  
  
 Aplikace se může stát, neaktivní v následujících případech:  
  
-   Uživatel přepíná z aktuální do jiné aplikace.  
  
-   Při vypnutí aplikace.  
  
 Můžete může rozpoznat, kdy se změní na neaktivní aplikace ve zpracování <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> událostí.  
  
 Následující kód ukazuje, jak bude zpracováván <xref:System.Windows.Application.Activated> a <xref:System.Windows.Application.Deactivated> události, abyste zjistili, zda je aplikace aktivní.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 A <xref:System.Windows.Window> můžete také aktivovat a deaktivovat. V tématu <xref:System.Windows.Window.Activated?displayProperty=nameWithType> a <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> Další informace.  
  
> [!NOTE]
>  Ani <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ani <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> se vyvolá pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Ukončení aplikace  
 Dobu životnosti aplikace skončí, když je vypnutý, kterému může dojít z následujících důvodů:  
  
-   Uživatel zavře každých <xref:System.Windows.Window>.  
  
-   Uživatel zavře hlavní <xref:System.Windows.Window>.  
  
-   Uživatel končí [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] relace odhlášení nebo vypnutí.  
  
-   Byla splněna podmínka konkrétní aplikace.  
  
 Ke správě ukončení aplikace <xref:System.Windows.Application> poskytuje <xref:System.Windows.Application.Shutdown%2A> metody <xref:System.Windows.Application.ShutdownMode%2A> vlastnost a <xref:System.Windows.Application.SessionEnding> a <xref:System.Windows.Application.Exit> události.  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A>lze volat pouze z aplikace, které mají <xref:System.Security.Permissions.UIPermission>. Samostatné [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací mít vždy toto oprávnění. Ale [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] spuštěné v karanténě částečným vztahem důvěryhodnosti zabezpečení zóně Internet nepodporují.  
  
#### <a name="shutdown-mode"></a>Vypnutí režimu  
 Většina aplikací vypnout když jsou uzavřeny všechny systémy windows nebo pokud je hlavní okno zavřít. V některých případech však další podmínky specifické pro aplikace může určit, kdy aplikace ukončí. Můžete zadat podmínky, za kterých vaše aplikace bude ukončena nastavením <xref:System.Windows.Application.ShutdownMode%2A> s jedním z následujících <xref:System.Windows.ShutdownMode> hodnot výčtu:  
  
-   <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 Výchozí hodnota <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnLastWindowClose>, což znamená, že aplikace automaticky ukončí při zavření posledního okna v aplikaci uživatele. Ale pokud vaše aplikace by měla vypnout, když hlavní okno zavřený, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automaticky, pokud jste nastavili nemá <xref:System.Windows.Application.ShutdownMode%2A> k <xref:System.Windows.ShutdownMode.OnMainWindowClose>. To je ukázáno v následujícím příkladu.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Pokud máte specifické pro aplikaci vypnutí podmínky, nastavíte <xref:System.Windows.Application.ShutdownMode%2A> k <xref:System.Windows.ShutdownMode.OnExplicitShutdown>. V takovém případě je vaší povinností vypnutí aplikace explicitně voláním <xref:System.Windows.Application.Shutdown%2A> metodu; jinak, vaše aplikace bude dále běžet i v případě, že jsou zavřeny všechny systémy windows. Všimněte si, že <xref:System.Windows.Application.Shutdown%2A> je implicitně volána, když <xref:System.Windows.Application.ShutdownMode%2A> je buď <xref:System.Windows.ShutdownMode.OnLastWindowClose> nebo <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A>můžete nastavit od [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], ale je ignorován; [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] se vždy vypne při jeho je opuštění v prohlížeči nebo prohlížeče, který hostuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je uzavřený. Další informace najdete v tématu [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
#### <a name="session-ending"></a>Ukončování relace  
 Vypnutí podmínky, které jsou popsány <xref:System.Windows.Application.ShutdownMode%2A> vlastnost jsou specifické pro aplikaci. V některých případech ale aplikace může vypnout v důsledku podmínku externí. Nejběžnější externí podmínku nastane, když uživatel končí [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] relace následující akce:  
  
-   Odhlášení  
  
-   Vypínání  
  
-   Restartování  
  
-   V režimu spánku  
  
 Rozpoznat, kdy [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] neukončí relace může zpracovat <xref:System.Windows.Application.SessionEnding> událostí, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 V tomto příkladu zkontroluje kód <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> vlastnosti k určení jak [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] konec relace. Tato hodnota používá k uživateli zobrazí potvrzovací zpráva. Pokud uživatel nechce relace k ukončení, nastaví kód <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> k `true` zabránit [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] relace ukončuje.  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding>není aktivována pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
#### <a name="exit"></a>Ukončit  
 Při vypnutí aplikace potřebuje k provedení některých konečnému zpracování, jako je například zachování stavu aplikace. V takových situacích může zpracovat <xref:System.Windows.Application.Exit> událostí.  
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml1)]  
[!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml2)]  
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind1)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind1)]  
[!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind2)]
[!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind2)]  
  
 Úplný příklad najdete v tématu [zachovat a obnovit vlastnosti oboru aplikace napříč relacemi aplikace](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit>můžete ji zpracovat oba samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], <xref:System.Windows.Application.Exit> se vyvolá, když v následujících případech:  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Je opuštění.  
  
-   V [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)], když na kartě, který je hostitelem [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je uzavřený.  
  
-   Při zavření prohlížeče.  
  
#### <a name="exit-code"></a>Ukončovací kód  
 Aplikace jsou většinou spuštěn operační systém v reakci na žádost uživatele. Aplikaci však může být spuštěn v jiné aplikaci k provedení některých konkrétní úlohu. Při vypnutí aplikace spuštěného spuštění aplikace může chtít vědět podmínku, pod kterým aplikace spuštěného vypnout. V těchto situacích [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] umožňuje aplikacím vrátí ukončovací kód aplikace na vypnutí. Ve výchozím nastavení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace vrátit hodnotu ukončovací kód 0.  
  
> [!NOTE]
>  Když ladíte [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], kód ukončení aplikace se zobrazí v **výstup** okno při vypnutí aplikace, ve zprávě, vypadá podobně jako následující:  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Otevřete **výstup** okno kliknutím **výstup** na **zobrazení** nabídky.  
  
 Chcete-li změnit ukončovací kód, můžete zavolat <xref:System.Windows.Application.Shutdown%28System.Int32%29> přetížení, která přijímá byl argument celé číslo v něm ukončovací kód:  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Můžete zjistit hodnotu ukončovací kód a změnit, tak, že zpracování <xref:System.Windows.Application.Exit> událostí. <xref:System.Windows.Application.Exit> Obslužné rutiny události je předána <xref:System.Windows.ExitEventArgs> která poskytuje přístup k v něm ukončovací kód s <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> vlastnost. Další informace naleznete v tématu <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
>  V obou samostatné aplikace můžete nastavit v něm ukončovací kód a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Ale pro se ignoruje hodnotu ukončovacího kódu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>Nezpracované výjimky  
 Aplikace může někdy vypnout dolů v části nestandardní podmínky, například když je vyvolána k neočekávané výjimce. V takovém případě aplikace nemusí mít kód ke zjištění a zpracování výjimky. Tento typ výjimky je k neošetřené výjimce; Před ukončením aplikace se zobrazí oznámení podobná zobrazená na následujícím obrázku.  
  
 ![Neošetřená výjimka oznámení](../../../../docs/framework/wpf/app-development/media/applicationmanagementoverviewfigure2.png "ApplicationManagementOverviewFigure2")  
  
 Z hlediska zkušeností uživatele je lepší pro aplikaci, aby se zabránilo toto výchozí chování díky některé nebo všechny z následujících akcí:  
  
-   Zobrazení informací o uživatelsky přívětivý.  
  
-   Pokus zachovat aplikace spuštěna.  
  
-   Nahrávání informací podrobné, uživatelsky, výjimka v [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] protokolu událostí.  
  
 Tato podpora implementace závisí na schopnost rozpoznat neošetřených výjimek, to znamená, co <xref:System.Windows.Application.DispatcherUnhandledException> událost se vyvolá pro.  
  
 [!code-xaml[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
 [!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind1)]
 [!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind1)]  
[!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind2)]
[!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind2)]  
  
 <xref:System.Windows.Application.DispatcherUnhandledException> Obslužné rutiny události je předána <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> parametr, který obsahuje kontextové informace týkající se neošetřené výjimky, včetně výjimek, samotné (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). Tyto informace můžete použít k určení způsobu zpracování výjimky.  
  
 Při zpracování <xref:System.Windows.Application.DispatcherUnhandledException>, byste měli nastavit <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> vlastnost `true`, jinak hodnota [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] stále zvažuje výjimka, která má neošetřených a vrátí do výchozího chování popsané výše. Pokud neošetřené výjimce a buď <xref:System.Windows.Application.DispatcherUnhandledException> událost není zpracována, nebo se zpracovává události a <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> je nastaven na `false`, okamžitě vypnutí aplikace. Kromě toho jiná <xref:System.Windows.Application> události jsou vyvolány. V důsledku toho je potřeba zpracovat <xref:System.Windows.Application.DispatcherUnhandledException> Pokud vaše aplikace obsahuje kód, který se musí spustit před vypnutí aplikace.  
  
 I když může aplikace vypnout v důsledku neošetřené výjimky, aplikace obvykle vypne v reakci na žádost uživatele, jak je popsáno v následující části.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Události životního cyklu aplikací  
 Samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nemají přesně stejnou životnosti. Následující obrázek ukazuje klíče události v životnost samostatná aplikace a zobrazuje pořadí, ve kterém jsou vyvolány.  
  
 ![Samostatné aplikace & č. 45; Události aplikačního objektu](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 Podobně následující obrázek ukazuje klíče události v životnost [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]a zobrazuje pořadí, ve kterém jsou vyvolány.  
  
 ![XBAP & č. 45; Události aplikačního objektu](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Application>  
 [Přehled Windows ve WPF](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)  
 [Přehled navigace](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [Prostředek, obsah a datové soubory aplikace WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)  
 [Sbalení URI v technologii WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Aplikačního modelu: Postupy: témata](http://msdn.microsoft.com/library/76771b09-3688-4d1c-8818-9b3f4cf39a30)  
 [Vývoj aplikací](../../../../docs/framework/wpf/app-development/index.md)
