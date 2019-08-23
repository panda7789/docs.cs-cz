---
title: Přehled správy aplikací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: 448c212e4afe547dc6342b000fe06d5340db112c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958743"
---
# <a name="application-management-overview"></a>Přehled správy aplikací
Všechny aplikace mají za následek sdílení společné sady funkcí, které se vztahují k implementaci a správě aplikací. Toto téma poskytuje přehled funkcí ve <xref:System.Windows.Application> třídě pro vytváření a správu aplikací.  

## <a name="the-application-class"></a>Třída aplikace  
 Ve WPF jsou společné funkce rozsahu aplikace zapouzdřeny ve <xref:System.Windows.Application> třídě. <xref:System.Windows.Application> Třída obsahuje následující funkce:  
  
- Sledování a interakce s životním cyklu aplikace.  
  
- Načítání a zpracování parametrů příkazového řádku.  
  
- Zjišťování a reakce na neošetřené výjimky.  
  
- Sdílení vlastností a prostředků oboru aplikace  
  
- Správa systému Windows v samostatných aplikacích.  
  
- Sledování a Správa navigace.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Jak provádět běžné úlohy pomocí třídy aplikace  
 Pokud si nejste zajímáte o všechny podrobnosti <xref:System.Windows.Application> třídy, v následující tabulce jsou uvedeny některé běžné úkoly pro <xref:System.Windows.Application> a jak je dosáhnout. Zobrazením souvisejících rozhraní API a témat můžete najít další informace a ukázkový kód.  
  
|Úloha|Přístup|  
|----------|--------------|  
|Získat objekt, který představuje aktuální aplikaci|<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> Použijte vlastnost.|  
|Přidání úvodní obrazovky do aplikace|Viz [Přidání úvodní obrazovky do aplikace WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Spuštění aplikace|<xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> Použijte metodu.|  
|Zastavení aplikace|<xref:System.Windows.Application.Shutdown%2A> Použijte metodu<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> objektu.|  
|Získat argumenty z příkazového řádku|Zpracujte událost a použijte <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType>vlastnost. <xref:System.Windows.Application.Startup?displayProperty=nameWithType> Příklad naleznete v tématu <xref:System.Windows.Application.Startup?displayProperty=nameWithType> událost.|  
|Získat a nastavit ukončovací kód aplikace|Nastavte vlastnost v obslužné rutině <xref:System.Windows.Application.Shutdown%2A> událostinebovolejtemetoduapředejteceléčíslo.<xref:System.Windows.Application.Exit?displayProperty=nameWithType> <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType>|  
|Detekce a reakce na neošetřené výjimky|<xref:System.Windows.Application.DispatcherUnhandledException> Zpracujte událost.|  
|Získání a nastavení prostředků v rozsahu aplikace|<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> Použijte vlastnost.|  
|Použití slovníku prostředků oboru aplikace|Viz [Použití slovníku prostředků oboru aplikace](how-to-use-an-application-scope-resource-dictionary.md).|  
|Získání a nastavení vlastností v rozsahu aplikace|<xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> Použijte vlastnost.|  
|Získání a uložení stavu aplikace|Viz [zachování a obnovení vlastností rozsahu aplikace napříč relacemi aplikace](persist-and-restore-application-scope-properties.md).|  
|Spravujte soubory dat nesouvisející s kódem, včetně souborů prostředků, souborů obsahu a souborů, které jsou v původním umístění.|Viz [prostředek aplikace WPF, obsah a datové soubory](wpf-application-resource-content-and-data-files.md).|  
|Správa Windows v samostatných aplikacích|Viz [Přehled Windows WPF](wpf-windows-overview.md).|  
|Sledování a Správa navigace|Viz [Přehled navigace](navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>Definice aplikace  
 Chcete-li využít funkci <xref:System.Windows.Application> třídy, je nutné implementovat definici aplikace. Definice aplikace WPF je třída, která je odvozena z <xref:System.Windows.Application> a je nakonfigurována se speciálním nastavením nástroje MSBuild.  

### <a name="implementing-an-application-definition"></a>Implementace definice aplikace  
 Typická definice aplikace WPF je implementována pomocí kódu a kódu na pozadí. To vám umožňuje používat značky k deklarativnímu nastavení vlastností aplikace, prostředků a registrování událostí a současně zpracovávat události a implementaci chování specifického pro aplikaci v kódu na pozadí.  
  
 Následující příklad ukazuje, jak implementovat definici aplikace pomocí značek a kódu na pozadí:  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Chcete-li, aby soubor značek a soubor s kódem na pozadí pracovaly společně, je nutné provést následující:  
  
- V kódu `Application` musí element `x:Class` obsahovat atribut. Když `x:Class` je aplikace sestavena, existence v souboru označení způsobí, že nástroj MSBuild `partial` vytvoří třídu, která je odvozena z <xref:System.Windows.Application> a `x:Class` má název, který je určen atributem. To vyžaduje přidání deklarace oboru názvů XML pro schéma XAML (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`).
  
- V kódu na pozadí třída musí být `partial` třída se stejným názvem, který je určen `x:Class` atributem v označení a musí odvozovat z <xref:System.Windows.Application>. To umožňuje, aby soubor s kódem na pozadí byl přidružen `partial` ke třídě, která je generována pro soubor označení při sestavení aplikace (viz [Vytvoření aplikace WPF](building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
> Když vytvoříte nový projekt aplikace WPF nebo projekt WPF aplikace pomocí sady Visual Studio, definice aplikace je součástí výchozího nastavení a je definována pomocí kódu a kódu na pozadí.  
  
 Tento kód je minimální, který je požadován k implementaci definice aplikace. Před vytvořením a spuštěním aplikace je však nutné provést další konfiguraci nástroje MSBuild v definici aplikace.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Konfigurace definice aplikace pro MSBuild  
 Samostatné aplikace a aplikace prohlížeče XAML (XBAP) vyžadují implementaci určité úrovně infrastruktury předtím, než budou moct běžet. Nejdůležitější součástí této infrastruktury je vstupní bod. Když uživatel spustí aplikaci, operační systém zavolá vstupní bod, což je dobře známá funkce pro spouštění aplikací.  
  
 Vývojáři obvykle potřebují pro sebe napsat nějaký nebo celý tento kód, a to v závislosti na technologii. WPF ale tento kód vygeneruje, když je soubor označení vaší definice aplikace nakonfigurovaný jako položka MSBuild `ApplicationDefinition` , jak je znázorněno v následujícím souboru projektu MSBuild:  
  
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
  
 Vzhledem k tomu, že soubor kódu na pozadí obsahuje kód, je označen jako `Compile` položka MSBuild, protože je normální.  
  
 Použití těchto konfigurací nástroje MSBuild na značky a soubory kódu na pozadí definice aplikace způsobí, že nástroj MSBuild generuje kód podobný následujícímu:  
  
 [!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
 [!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]  
  
 Výsledný kód rozšiřuje definici vaší aplikace o další kód infrastruktury, který obsahuje metodu `Main`vstupního bodu. Atribut se aplikuje `Main` na metodu, která označuje, že hlavní vlákno uživatelského rozhraní pro aplikaci WPF je vlákno STA, které je vyžadováno pro aplikace WPF. <xref:System.STAThreadAttribute> Při volání `Main` vytvoří novou `App` instanci před voláním `InitializeComponent` metody pro registraci událostí a nastavení vlastností, které jsou implementovány v kódu. Vzhledem `InitializeComponent` k tomu, že je pro vás vygenerována, `InitializeComponent` nemusíte explicitně volat z definice aplikace <xref:System.Windows.Controls.Page> , <xref:System.Windows.Window> jako je například pro a implementace. Nakonec je volána metoda pro spuštění aplikace. <xref:System.Windows.Application.Run%2A>  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Získávání aktuální aplikace  
 Vzhledem k tomu, že <xref:System.Windows.Application> funkce třídy jsou sdíleny napříč aplikací, může existovat pouze jedna instance <xref:System.Windows.Application> třídy na <xref:System.AppDomain>. Chcete-li toto vyhovět, <xref:System.Windows.Application> třída je implementována jako třída typu Singleton (viz [implementace singleton v C# ](https://go.microsoft.com/fwlink/?LinkId=100567)rámci), která vytváří jednu instanci sebe sama a poskytuje `static` <xref:System.Windows.Application.Current%2A> sdílený přístup k ní s vlastností.  
  
 Následující kód ukazuje, jak získat odkaz na <xref:System.Windows.Application> objekt pro aktuální. <xref:System.AppDomain>  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A>Vrátí odkaz na instanci <xref:System.Windows.Application> třídy. Pokud chcete odkaz na <xref:System.Windows.Application> odvozenou třídu, musíte přetypovat hodnotu <xref:System.Windows.Application.Current%2A> vlastnosti, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Můžete zkontrolovat hodnotu <xref:System.Windows.Application.Current%2A> v jakémkoli okamžiku životnosti <xref:System.Windows.Application> objektu. Měli byste si však být opatrní. Po vytvoření instance <xref:System.Windows.Application> třídyexistujeobdobí,běhemkteréhojestav<xref:System.Windows.Application> objektu nekonzistentní. Během této doby <xref:System.Windows.Application> provádí různé inicializační úlohy, které váš kód vyžaduje ke spuštění, včetně stanovení infrastruktury aplikace, nastavení vlastností a registrování událostí. Pokud se pokusíte použít <xref:System.Windows.Application> objekt během této doby, váš kód může mít neočekávané výsledky, zejména v případě, že závisí na různých <xref:System.Windows.Application> vlastnostech, které jsou nastaveny.  
  
 Po <xref:System.Windows.Application> dokončení své inicializační práce se skutečně zahájí jeho životnost.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Doba života aplikace  
 Životnost aplikace WPF je označena několika událostmi, které jsou vyvolány <xref:System.Windows.Application> a umožňují vám zjistit, zda byla aplikace spuštěna, zda byla aktivována a dezaktivována a byla ukončena.  

<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Úvodní obrazovka  
 Počínaje verzí .NET Framework 3,5 SP1 můžete určit obrázek, který se má použít v okně pro spuštění, nebo na *úvodní obrazovce*. <xref:System.Windows.SplashScreen> Třída usnadňuje zobrazení spouštěcího okna během načítání aplikace. Okno se vytvoří a zobrazí se před <xref:System.Windows.Application.Run%2A> tím, než se zavolá. <xref:System.Windows.SplashScreen> Další informace najdete v tématu [čas spuštění aplikace](../advanced/application-startup-time.md) a [Přidání úvodní obrazovky do aplikace WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Spuštění aplikace  
 Po <xref:System.Windows.Application.Run%2A> volání a inicializaci aplikace je aplikace připravena ke spuštění. Tento okamžik je označen při <xref:System.Windows.Application.Startup> vyvolání události:  
  
[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]
  
 V tomto okamžiku životního cyklu aplikace je nejběžnější postup zobrazit uživatelské rozhraní.  
  
<a name="Showing_a_User_Interface"></a>
### <a name="showing-a-user-interface"></a>Zobrazení uživatelského rozhraní  
 Většina samostatných aplikací systému Windows otevře <xref:System.Windows.Window> při zahájení běhu. Obslužná <xref:System.Windows.Application.Startup> rutina události je jedno umístění, ze kterého lze provést, jak je znázorněno v následujícím kódu.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
> První <xref:System.Windows.Window> instance, která má být vytvořena v samostatné aplikaci, se ve výchozím nastavení stal hlavním oknem aplikace. <xref:System.Windows.Window> Na<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> tento objekt odkazuje vlastnost. Hodnota <xref:System.Windows.Application.MainWindow%2A> vlastnosti může být změněna programově, pokud <xref:System.Windows.Window> by jiné okno než první instance mělo být hlavním oknem.  
  
 Při prvním spuštění aplikace XBAP bude pravděpodobně možné přejít na <xref:System.Windows.Controls.Page>. Tento kód je zobrazen v následujícím kódu.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 Pokud zpracováváte <xref:System.Windows.Application.Startup> <xref:System.Windows.Window> pouze otevření nebo nebo navigovat na <xref:System.Windows.Controls.Page>, můžete místo toho nastavit `StartupUri` atribut v označení.  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Application.StartupUri%2A> ze samostatné aplikace k <xref:System.Windows.Window>otevření.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Application.StartupUri%2A> z aplikace XBAP k přechodu <xref:System.Windows.Controls.Page>na.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Tento kód má stejný účinek jako předchozí kód pro otevření okna.  
  
> [!NOTE]
> Další informace o navigaci najdete v tématu [Přehled navigace](navigation-overview.md).  
  
 Je nutné zpracovat <xref:System.Windows.Application.Startup> událost pro <xref:System.Windows.Window> otevření, pokud je třeba ji vytvořit pomocí konstruktoru bez parametrů, nebo musíte nastavit její vlastnosti nebo se přihlásit k odběru jejích událostí, než je zobrazíte, nebo potřebujete zpracovat argumenty příkazového řádku. které byly zadány při spuštění aplikace.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Zpracování argumentů příkazového řádku  
 V systému Windows můžete samostatné aplikace spustit z příkazového řádku nebo z plochy. V obou případech lze do aplikace předat argumenty příkazového řádku. Následující příklad ukazuje aplikaci, která se spustí s jedním argumentem příkazového řádku, "/StartMinimized":  
  
 `wpfapplication.exe /StartMinimized`  
  
 Při inicializaci aplikace WPF načte argumenty příkazového řádku z operačního systému a předá je <xref:System.Windows.Application.Startup> obslužné rutině události <xref:System.Windows.StartupEventArgs.Args%2A> prostřednictvím vlastnosti <xref:System.Windows.StartupEventArgs> parametru. Argumenty příkazového řádku můžete načíst a uložit pomocí kódu podobného následujícímu.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 Popisovač <xref:System.Windows.Application.Startup> kódu kontroluje, zda byl zadán argument příkazového řádku **/StartMinimized** . Pokud ano, otevře se <xref:System.Windows.WindowState> hlavní <xref:System.Windows.WindowState.Minimized>okno s. Všimněte si, že <xref:System.Windows.Window.WindowState%2A> vzhledem k tomu, že vlastnost musí být <xref:System.Windows.Window> nastavena programově, musí být hlavní otevřený explicitně v kódu.  
  
 XBAP nemohou načíst a zpracovat argumenty příkazového řádku, protože jsou spouštěny pomocí nasazení ClickOnce (viz [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md)). Můžou ale načítat a zpracovávat parametry řetězce dotazu z adres URL, které se používají ke spuštění.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Aktivace a deaktivace aplikace  
 Systém Windows umožňuje uživatelům přepínat mezi aplikacemi. Nejběžnějším způsobem je použití kombinace kláves ALT + TAB. Aplikaci lze přepnout do pouze v případě, že je viditelná <xref:System.Windows.Window> , kterou může uživatel vybrat. Aktuálně vybraný <xref:System.Windows.Window> je *aktivní okno* (označované také jako <xref:System.Windows.Window> okno na *popředí*), které přijímá vstup uživatele. Aplikace s aktivním oknem je *aktivní aplikace* (nebo aplikace v *popředí*). Aplikace se bude aktivní aplikací v následujících případech:  
  
- Spustí se a zobrazí se <xref:System.Windows.Window>.  
  
- Uživatel přepne z jiné aplikace výběrem a <xref:System.Windows.Window> v aplikaci.  
  
 Můžete zjistit, kdy se aplikace bude aktivní, a to <xref:System.Windows.Application.Activated?displayProperty=nameWithType> tak, že se událost zpracuje.  
  
 Podobně může být aplikace neaktivní v následujících případech:  
  
- Uživatel přepne do jiné aplikace z aktuálního.  
  
- Když se aplikace vypíná.  
  
 Můžete zjistit, kdy se aplikace bude neaktivní, a to <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> zpracováním události.  
  
 Následující kód ukazuje, jak zpracovat <xref:System.Windows.Application.Activated> události a <xref:System.Windows.Application.Deactivated> k určení, zda je aplikace aktivní.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 <xref:System.Windows.Window> Lze také aktivovat a deaktivovat. Další <xref:System.Windows.Window.Activated?displayProperty=nameWithType> informace <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> najdete v tématu a.  
  
> [!NOTE]
> Pro XBAP <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> není anivyvolána.<xref:System.Windows.Application.Activated?displayProperty=nameWithType>  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Vypnutí aplikace  
 Životnost aplikace končí, když je vypnutá, což může nastat z následujících důvodů:  
  
- Uživatel se zavře každý <xref:System.Windows.Window>.  
  
- Uživatel zavírá hlavní <xref:System.Windows.Window>.  
  
- Uživatel ukončí relaci systému Windows odhlášením nebo vypnutím.  
  
- Byla splněna podmínka specifická pro aplikaci.  
  
 Pro usnadnění správy vypnutí <xref:System.Windows.Application> aplikace <xref:System.Windows.Application.Shutdown%2A> poskytuje metoda, <xref:System.Windows.Application.ShutdownMode%2A> vlastnost a <xref:System.Windows.Application.SessionEnding> události a <xref:System.Windows.Application.Exit> .  
  
> [!NOTE]
> <xref:System.Windows.Application.Shutdown%2A>lze ji volat pouze z aplikací, které <xref:System.Security.Permissions.UIPermission>mají. Samostatná aplikace WPF mají vždy toto oprávnění. Aplikace XBAP spuštěné v izolovaném prostoru zabezpečení zóny Internet Zone ale nepodporují.  
  
#### <a name="shutdown-mode"></a>Režim vypnutí  
 Většina aplikací se vypne buď při zavření všech oken nebo při zavření hlavního okna. Někdy ale jiné podmínky specifické pro aplikace mohou určit, kdy se aplikace vypíná. Můžete určit podmínky, za kterých se vaše aplikace vypne, nastavením <xref:System.Windows.Application.ShutdownMode%2A> jedné z následujících <xref:System.Windows.ShutdownMode> hodnot výčtu:  
  
- <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 Výchozí hodnota <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnLastWindowClose>, což znamená, že aplikace se automaticky vypne, když uživatel zavře poslední okno aplikace. Pokud by však měla být aplikace ukončena při zavření hlavního okna, WPF automaticky provede, že pokud nastavíte <xref:System.Windows.Application.ShutdownMode%2A> na. <xref:System.Windows.ShutdownMode.OnMainWindowClose> To je ukázáno v následujícím příkladu.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Pokud máte podmínky pro vypnutí specifické pro aplikaci, nastavte <xref:System.Windows.Application.ShutdownMode%2A> na. <xref:System.Windows.ShutdownMode.OnExplicitShutdown> V tomto případě je vaší zodpovědností ukončit aplikaci tím, že explicitně zavoláte <xref:System.Windows.Application.Shutdown%2A> metodu. v opačném případě bude aplikace dál běžet i v případě, že jsou všechna okna zavřena. Všimněte si <xref:System.Windows.Application.Shutdown%2A> , že implicitně se volá <xref:System.Windows.Application.ShutdownMode%2A> , když <xref:System.Windows.ShutdownMode.OnLastWindowClose> je <xref:System.Windows.ShutdownMode.OnMainWindowClose>buď nebo.  
  
> [!NOTE]
> <xref:System.Windows.Application.ShutdownMode%2A>dá se nastavit z XBAP, ale ignoruje se. XBAP je vždy vypnuta, když je přecházení v prohlížeči nebo když je zavřen prohlížeč, který je hostitelem aplikace XBAP. Další informace najdete v tématu [Přehled navigace](navigation-overview.md).  
  
#### <a name="session-ending"></a>Ukončení relace  
 Podmínky vypnutí, které jsou popsány <xref:System.Windows.Application.ShutdownMode%2A> vlastností, jsou specifické pro aplikaci. V některých případech ale může dojít k vypnutí aplikace v důsledku externí podmínky. Nejběžnější externí podmínka nastane, když uživatel ukončí relaci systému Windows následujícími akcemi:  
  
- Odhlášení  
  
- Vypínání  
  
- Restartovat  
  
- Hibernace  
  
 Chcete-li zjistit, kdy relace systému Windows skončí, můžete <xref:System.Windows.Application.SessionEnding> zpracovat událost, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 V tomto příkladu kód zkontroluje <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> vlastnost a určí, jak probíhá ukončování relace systému Windows. Tato hodnota se používá k zobrazení potvrzovací zprávy uživateli. Pokud uživatel nechce ukončit relaci, kód nastaví <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> `true` , aby nedošlo k ukončení relace systému Windows.  
  
> [!NOTE]
> <xref:System.Windows.Application.SessionEnding>není vyvoláno pro XBAP.

#### <a name="exit"></a>Ukončit  
 Když se aplikace ukončí, může být nutné provést nějaké konečné zpracování, jako je například zachování stavu aplikace. V těchto situacích lze <xref:System.Windows.Application.Exit> událost zpracovat, `App_Exit` jako obslužná rutina události, v následujícím příkladu. Je definován jako obslužná rutina události v souboru *App. XAML* . Jeho implementace je zvýrazněna v souborech *App.XAML.cs* a *Application. XAML. vb* .
  
[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]  
  
 [!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
 [!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]  
  
 Úplný příklad naleznete v tématu [trvalé a obnovení vlastností rozsahu aplikace napříč relacemi aplikace](persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit>může být zpracována samostatnými aplikacemi i XBAP. Pro XBAP <xref:System.Windows.Application.Exit> je vyvolána v následujících případech:  
  
- Aplikace XBAP přešla jinam.  
  
- V aplikaci Internet Explorer, pokud je zavřena karta, která je hostitelem aplikace XBAP.  
  
- Při zavření prohlížeče.  
  
#### <a name="exit-code"></a>Ukončovací kód  
 Aplikace jsou většinou spuštěné operačním systémem v reakci na požadavek uživatele. Aplikaci však lze spustit jinou aplikací k provedení určitého úkolu. Po ukončení spuštěné aplikace může spuštění aplikace chtít znát podmínku, za kterou se spuštěné aplikace vypnula. V těchto situacích systém Windows umožňuje aplikacím vracet ukončovací kód aplikace při vypnutí. Ve výchozím nastavení aplikace WPF vrátí ukončovací kód s hodnotou 0.  
  
> [!NOTE]
> Při ladění ze sady Visual Studio se ukončovací kód aplikace zobrazuje v okně **výstup** , když se aplikace ukončí, ve zprávě, která vypadá takto:  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Otevřete okno **výstup** kliknutím na **výstup** v nabídce **zobrazení** .  
  
 Chcete-li změnit ukončovací kód, můžete volat <xref:System.Windows.Application.Shutdown%28System.Int32%29> přetížení, které přijímá celočíselný argument jako ukončovací kód:  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Můžete zjistit hodnotu ukončovacího kódu a změnit ji pomocí zpracování <xref:System.Windows.Application.Exit> události. Obslužná rutina <xref:System.Windows.ExitEventArgs>událostije předána, která poskytuje přístup k ukončovacímu kódu <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> s vlastností. <xref:System.Windows.Application.Exit> Další informace naleznete v tématu <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
> Ukončovací kód můžete nastavit jak v samostatných aplikacích, tak v XBAP. Hodnota ukončovacího kódu se ale pro aplikace XBAP ignoruje.  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>Neošetřené výjimky  
 V některých případech se může stát, že se aplikace vypne za abnormálních podmínek, například při vyvolání neočekávané výjimky. V tomto případě aplikace nemusí mít kód pro detekci a zpracování výjimky. Tento typ výjimky je Neošetřená výjimka; oznámení podobné tomuto obrázku zobrazenému na následujícím obrázku je zobrazeno před zavřením aplikace.  
  
 ![Snímek obrazovky, který zobrazuje oznámení o neošetřené výjimce.](./media/application-management-overview/unhandled-exception-notification.png)  
  
 V perspektivě uživatelského prostředí je lepší, aby aplikace zabránila tomuto výchozímu chování tím, že provádí některé nebo všechny následující akce:  
  
- Zobrazují se uživatelsky přívětivé informace.  
  
- Probíhá pokus o zachování aplikace v chodu.  
  
- V protokolu událostí systému Windows se zaznamenávají podrobné informace o výjimce pro vývojáře.  
  
 Implementace této podpory závisí na schopnostech detekovat neošetřené výjimky, což znamená, že <xref:System.Windows.Application.DispatcherUnhandledException> událost je vyvolána pro.  
  
[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]  
  
 Obslužné rutině <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs>událostije předán parametr, který obsahuje kontextové informace týkající se neošetřené výjimky, včetně samotné výjimky (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). <xref:System.Windows.Application.DispatcherUnhandledException> Tyto informace můžete použít k určení, jak se má výjimka zpracovat.  
  
 Při zpracování <xref:System.Windows.Application.DispatcherUnhandledException> <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> vlastnosti byste měli nastavit vlastnost na `true`hodnotu; v opačném případě WPF stále považuje výjimku za neošetřenou a vrátí se k výchozímu chování popsanému výše. Je-li vyvolána neošetřená výjimka a <xref:System.Windows.Application.DispatcherUnhandledException> událost není zpracována nebo událost je zpracována a <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> je nastavena na `false`hodnotu, aplikace se okamžitě ukončí. Kromě toho nejsou vyvolány žádné další <xref:System.Windows.Application> události. V důsledku toho je nutné zpracovat <xref:System.Windows.Application.DispatcherUnhandledException> , zda má aplikace kód, který musí být spuštěn před vypnutím aplikace.  
  
 I když se aplikace může vypnout v důsledku neošetřené výjimky, aplikace se obvykle vypne v reakci na požadavek uživatele, jak je popsáno v další části.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Události životního cyklu aplikace  
 Samostatné aplikace a XBAP nemají přesně stejné životnosti. Následující obrázek znázorňuje klíčové události při životnosti samostatné aplikace a ukazuje pořadí, ve kterém jsou vyvolány.  
  
 ![Samostatné události &#45; objektu aplikační aplikace](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 Podobně následující obrázek ilustruje klíčové události v době životnosti XBAP a zobrazuje sekvenci, ve které jsou vyvolány.  
  
 ![Události &#45; objektu aplikace XBAP](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Application>
- [Přehled Windows ve WPF](wpf-windows-overview.md)
- [Přehled navigace](navigation-overview.md)
- [Prostředek, obsah a datové soubory aplikace WPF](wpf-application-resource-content-and-data-files.md)
- [Sbalení URI v technologii WPF](pack-uris-in-wpf.md)
- [Aplikační model: Témata s postupy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [Vývoj aplikací](index.md)
