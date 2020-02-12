---
title: Přehled správy aplikací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: dbc5bd9f699415fb47f21c6a45b1c58cfcff0f33
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124517"
---
# <a name="application-management-overview"></a>Přehled správy aplikací

Všechny aplikace mají za následek sdílení společné sady funkcí, které se vztahují k implementaci a správě aplikací. V tomto tématu najdete přehled funkcí třídy <xref:System.Windows.Application> pro vytváření a správu aplikací.

## <a name="the-application-class"></a>Třída aplikace

V rámci WPF jsou společné funkce rozsahu aplikace zapouzdřeny ve třídě <xref:System.Windows.Application>. Třída <xref:System.Windows.Application> obsahuje následující funkce:

- Sledování a interakce s životním cyklu aplikace.

- Načítání a zpracování parametrů příkazového řádku.

- Zjišťování a reakce na neošetřené výjimky.

- Sdílení vlastností a prostředků oboru aplikace

- Správa systému Windows v samostatných aplikacích.

- Sledování a Správa navigace.

<a name="The_Application_Class"></a>

## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Jak provádět běžné úlohy pomocí třídy aplikace

Pokud si nejste jistí, jaké jsou informace o <xref:System.Windows.Application> třídě, v následující tabulce jsou uvedeny některé běžné úlohy pro <xref:System.Windows.Application> a jejich provádění. Zobrazením souvisejících rozhraní API a témat můžete najít další informace a ukázkový kód.

|Úkol|Přístup|
|----------|--------------|
|Získat objekt, který představuje aktuální aplikaci|Použijte vlastnost <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>.|
|Přidání úvodní obrazovky do aplikace|Viz [Přidání úvodní obrazovky do aplikace WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).|
|Spuštění aplikace|Použijte metodu <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType>.|
|Zastavení aplikace|Použijte metodu <xref:System.Windows.Application.Shutdown%2A> objektu <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>.|
|Získat argumenty z příkazového řádku|Zpracujte událost <xref:System.Windows.Application.Startup?displayProperty=nameWithType> a použijte vlastnost <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType>. Příklad naleznete v tématu událost <xref:System.Windows.Application.Startup?displayProperty=nameWithType>.|
|Získat a nastavit ukončovací kód aplikace|Nastavte vlastnost <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> v obslužné rutině události <xref:System.Windows.Application.Exit?displayProperty=nameWithType> nebo volejte metodu <xref:System.Windows.Application.Shutdown%2A> a předejte celé číslo.|
|Detekce a reakce na neošetřené výjimky|Zpracujte událost <xref:System.Windows.Application.DispatcherUnhandledException>.|
|Získání a nastavení prostředků v rozsahu aplikace|Použijte vlastnost <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>.|
|Použití slovníku prostředků oboru aplikace|Viz [Použití slovníku prostředků oboru aplikace](how-to-use-an-application-scope-resource-dictionary.md).|
|Získání a nastavení vlastností v rozsahu aplikace|Použijte vlastnost <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType>.|
|Získání a uložení stavu aplikace|Viz [zachování a obnovení vlastností rozsahu aplikace napříč relacemi aplikace](persist-and-restore-application-scope-properties.md).|
|Spravujte soubory dat nesouvisející s kódem, včetně souborů prostředků, souborů obsahu a souborů, které jsou v původním umístění.|Viz [prostředek aplikace WPF, obsah a datové soubory](wpf-application-resource-content-and-data-files.md).|
|Správa Windows v samostatných aplikacích|Viz [Přehled Windows WPF](wpf-windows-overview.md).|
|Sledování a Správa navigace|Viz [Přehled navigace](navigation-overview.md).|

<a name="The_Application_Definition"></a>

## <a name="the-application-definition"></a>Definice aplikace

Chcete-li využít funkci <xref:System.Windows.Application> třídy, je nutné implementovat definici aplikace. Definice aplikace WPF je třída, která je odvozena od <xref:System.Windows.Application> a je nakonfigurována se speciálním nastavením nástroje MSBuild.

### <a name="implementing-an-application-definition"></a>Implementace definice aplikace

Typická definice aplikace WPF je implementována pomocí kódu a kódu na pozadí. To vám umožňuje používat značky k deklarativnímu nastavení vlastností aplikace, prostředků a registrování událostí a současně zpracovávat události a implementaci chování specifického pro aplikaci v kódu na pozadí.

Následující příklad ukazuje, jak implementovat definici aplikace pomocí značek a kódu na pozadí:

[!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]

[!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
[!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]

Chcete-li, aby soubor značek a soubor s kódem na pozadí pracovaly společně, je nutné provést následující:

- V kódu `Application` element musí zahrnovat atribut `x:Class`. Když je aplikace sestavena, existence `x:Class` v souboru označení způsobí, že nástroj MSBuild vytvoří třídu `partial`, která je odvozena z <xref:System.Windows.Application> a má název, který je určen atributem `x:Class`. To vyžaduje přidání deklarace oboru názvů XML pro schéma XAML (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`).

- V kódu na pozadí třída musí být `partial` třídy se stejným názvem, který je určen atributem `x:Class` v kódu a musí odvozovat z <xref:System.Windows.Application>. To umožňuje, aby soubor s kódem na pozadí byl přidružen k třídě `partial`, která je generována pro soubor označení při sestavení aplikace (viz [Vytvoření aplikace WPF](building-a-wpf-application-wpf.md)).

> [!NOTE]
> Když vytvoříte nový projekt aplikace WPF nebo projekt WPF aplikace pomocí sady Visual Studio, definice aplikace je součástí výchozího nastavení a je definována pomocí kódu a kódu na pozadí.

Tento kód je minimální, který je požadován k implementaci definice aplikace. Před vytvořením a spuštěním aplikace je však nutné provést další konfiguraci nástroje MSBuild v definici aplikace.

### <a name="configuring-the-application-definition-for-msbuild"></a>Konfigurace definice aplikace pro MSBuild

Samostatné aplikace a aplikace prohlížeče XAML (XBAP) vyžadují implementaci určité úrovně infrastruktury předtím, než budou moct běžet. Nejdůležitější součástí této infrastruktury je vstupní bod. Když uživatel spustí aplikaci, operační systém zavolá vstupní bod, což je dobře známá funkce pro spouštění aplikací.

Vývojáři obvykle potřebují pro sebe napsat nějaký nebo celý tento kód, a to v závislosti na technologii. WPF ale tento kód vygeneruje, když je soubor označení vaší definice aplikace nakonfigurovaný jako MSBuild `ApplicationDefinition` položka, jak je znázorněno v následujícím souboru projektu MSBuild:

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

Vzhledem k tomu, že soubor kódu na pozadí obsahuje kód, je označený jako `Compile` položka MSBuild, jak je normální.

Použití těchto konfigurací nástroje MSBuild na značky a soubory kódu na pozadí definice aplikace způsobí, že nástroj MSBuild generuje kód podobný následujícímu:

[!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
[!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]

Výsledný kód rozšiřuje definici vaší aplikace o další kód infrastruktury, který zahrnuje metodu vstupního bodu `Main`. Atribut <xref:System.STAThreadAttribute> je použit na metodu `Main` k označení toho, že hlavní vlákno uživatelského rozhraní pro aplikaci WPF je vlákno STA, které je vyžadováno pro aplikace WPF. Při volání `Main` vytvoří novou instanci `App` před voláním metody `InitializeComponent` pro registraci událostí a nastavení vlastností, které jsou implementovány v kódu. Vzhledem k tomu, že pro vás je vygenerována `InitializeComponent`, nemusíte explicitně volat `InitializeComponent` z definice aplikace, jako je třeba pro <xref:System.Windows.Controls.Page> a <xref:System.Windows.Window> implementace. Nakonec je volána metoda <xref:System.Windows.Application.Run%2A> pro spuštění aplikace.

<a name="Getting_the_Current_Application"></a>

## <a name="getting-the-current-application"></a>Získávání aktuální aplikace

Vzhledem k tomu, že funkce <xref:System.Windows.Application> třídy jsou sdíleny napříč aplikací, může být na <xref:System.AppDomain>pouze jedna instance <xref:System.Windows.Application> třídy. Chcete-li toto vyhovět, třída <xref:System.Windows.Application> je implementována jako třída typu Singleton (viz [implementace singleton v C# ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316(v=pandp.10))rámci), která vytváří jednu instanci sebe sama a poskytuje pro ni sdílený přístup s vlastností <xref:System.Windows.Application.Current%2A> `static`.

Následující kód ukazuje, jak získat odkaz na objekt <xref:System.Windows.Application> pro aktuální <xref:System.AppDomain>.

[!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]

<xref:System.Windows.Application.Current%2A> vrátí odkaz na instanci <xref:System.Windows.Application> třídy. Pokud chcete odkaz na třídu <xref:System.Windows.Application> odvozené třídy, musíte přetypovat hodnotu vlastnosti <xref:System.Windows.Application.Current%2A>, jak je znázorněno v následujícím příkladu.

[!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]

Můžete zkontrolovat hodnotu <xref:System.Windows.Application.Current%2A> v jakémkoli bodě životnosti objektu <xref:System.Windows.Application>. Měli byste si však být opatrní. Po vytvoření instance <xref:System.Windows.Application> třídy existuje období, během kterého je stav objektu <xref:System.Windows.Application> nekonzistentní. Během této doby <xref:System.Windows.Application> provádí různé inicializační úlohy, které váš kód vyžaduje ke spuštění, včetně vytvoření infrastruktury aplikace, nastavení vlastností a registrování událostí. Pokud se pokusíte použít <xref:System.Windows.Application> objekt během této doby, váš kód může mít neočekávané výsledky, zejména v případě, že závisí na různých vlastnostech <xref:System.Windows.Application>, které se nastavují.

Když <xref:System.Windows.Application> dokončí svou inicializační práci, je skutečně zahájena její životnost.

<a name="Application_Lifetime"></a>

## <a name="application-lifetime"></a>Doba života aplikace

Životnost aplikace WPF je označena několika událostmi, které jsou vyvolány <xref:System.Windows.Application>, které vám pomohou zjistit, zda byla aplikace spuštěna, zda byla aktivována a dezaktivována a byla ukončena.

<a name="Splash_Screen"></a>

### <a name="splash-screen"></a>Úvodní obrazovka

Počínaje verzí .NET Framework 3,5 SP1 můžete určit obrázek, který se má použít v okně pro spuštění, nebo na *úvodní obrazovce*. Třída <xref:System.Windows.SplashScreen> umožňuje snadno zobrazit okno po spuštění, když se vaše aplikace načítá. Okno <xref:System.Windows.SplashScreen> se vytvoří a zobrazí se před voláním <xref:System.Windows.Application.Run%2A>. Další informace najdete v tématu [čas spuštění aplikace](../advanced/application-startup-time.md) a [Přidání úvodní obrazovky do aplikace WPF](how-to-add-a-splash-screen-to-a-wpf-application.md).

<a name="Starting_an_Application"></a>

### <a name="starting-an-application"></a>Spuštění aplikace

Po volání <xref:System.Windows.Application.Run%2A> a inicializaci aplikace je aplikace připravena ke spuštění. Tento okamžik je označen při vyvolání události <xref:System.Windows.Application.Startup>:

[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]

V tomto okamžiku životního cyklu aplikace je nejběžnější postup zobrazit uživatelské rozhraní.

<a name="Showing_a_User_Interface"></a>

### <a name="showing-a-user-interface"></a>Zobrazení uživatelského rozhraní

Většina samostatných aplikací systému Windows při spuštění spustí <xref:System.Windows.Window>. Obslužná rutina události <xref:System.Windows.Application.Startup> je jedno umístění, ze kterého můžete provést tento postup, jak je znázorněno v následujícím kódu.

[!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]

[!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
[!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]

> [!NOTE]
> První <xref:System.Windows.Window>, který má být vytvořen v samostatné aplikaci, se ve výchozím nastavení zobrazí jako hlavní okno aplikace. Na tento objekt <xref:System.Windows.Window> odkazuje vlastnost <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>. Hodnotu vlastnosti <xref:System.Windows.Application.MainWindow%2A> lze změnit programově, pokud by jiné okno, než první instance <xref:System.Windows.Window>, mělo být hlavním oknem.

Při prvním spuštění aplikace XBAP bude pravděpodobně možné přejít na <xref:System.Windows.Controls.Page>. Tento kód je zobrazen v následujícím kódu.

[!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]

[!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
[!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]

Pokud zpracováváte <xref:System.Windows.Application.Startup> jenom pro otevření <xref:System.Windows.Window> nebo přechod na <xref:System.Windows.Controls.Page>, můžete místo toho nastavit atribut `StartupUri` v kódu.

Následující příklad ukazuje, jak použít <xref:System.Windows.Application.StartupUri%2A> ze samostatné aplikace k otevření <xref:System.Windows.Window>.

[!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]

Následující příklad ukazuje, jak použít <xref:System.Windows.Application.StartupUri%2A> z XBAP k přechodu na <xref:System.Windows.Controls.Page>.

[!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]

Tento kód má stejný účinek jako předchozí kód pro otevření okna.

> [!NOTE]
> Další informace o navigaci najdete v tématu [Přehled navigace](navigation-overview.md).

Je nutné zpracovat událost <xref:System.Windows.Application.Startup> pro otevření <xref:System.Windows.Window>, je-li nutné ji vytvořit pomocí konstruktoru bez parametrů, nebo je nutné nastavit její vlastnosti nebo se přihlásit k odběru jejích událostí, než je zobrazíte, nebo musíte zpracovat argumenty příkazového řádku, které byly zadány při spuštění aplikace.

<a name="Processing_Command_Line_Arguments"></a>

### <a name="processing-command-line-arguments"></a>Zpracování argumentů příkazového řádku

V systému Windows můžete samostatné aplikace spustit z příkazového řádku nebo z plochy. V obou případech lze do aplikace předat argumenty příkazového řádku. Následující příklad ukazuje aplikaci, která se spustí s jedním argumentem příkazového řádku, "/StartMinimized":

`wpfapplication.exe /StartMinimized`

Při inicializaci aplikace WPF načte argumenty příkazového řádku z operačního systému a předá je obslužné rutině <xref:System.Windows.Application.Startup> události prostřednictvím vlastnosti <xref:System.Windows.StartupEventArgs.Args%2A> parametru <xref:System.Windows.StartupEventArgs>. Argumenty příkazového řádku můžete načíst a uložit pomocí kódu podobného následujícímu.

[!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]

[!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
[!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]

Kód zpracovává <xref:System.Windows.Application.Startup>, aby zkontroloval, zda byl zadán argument příkazového řádku **/StartMinimized** ; Pokud ano, otevře se hlavní okno s <xref:System.Windows.WindowState> <xref:System.Windows.WindowState.Minimized>. Všimněte si, že vzhledem k tomu, že vlastnost <xref:System.Windows.Window.WindowState%2A> musí být nastavena programově, musí být hlavní <xref:System.Windows.Window> otevřen explicitně v kódu.

XBAP nemohou načíst a zpracovat argumenty příkazového řádku, protože jsou spouštěny pomocí nasazení ClickOnce (viz [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md)). Můžou ale načítat a zpracovávat parametry řetězce dotazu z adres URL, které se používají ke spuštění.

<a name="Application_Activation_and_Deactivation"></a>

### <a name="application-activation-and-deactivation"></a>Aktivace a deaktivace aplikace

Systém Windows umožňuje uživatelům přepínat mezi aplikacemi. Nejběžnějším způsobem je použití kombinace kláves ALT + TAB. Aplikaci lze přepnout do pouze v případě, že je viditelná <xref:System.Windows.Window>, kterou může uživatel vybrat. Aktuálně vybraný <xref:System.Windows.Window> je *aktivní okno* (označované také jako okno na *popředí*) a je <xref:System.Windows.Window>, které přijímá vstup uživatele. Aplikace s aktivním oknem je *aktivní aplikace* (nebo aplikace v *popředí*). Aplikace se bude aktivní aplikací v následujících případech:

- Spustí se a zobrazí <xref:System.Windows.Window>.

- Uživatel přepne z jiné aplikace výběrem <xref:System.Windows.Window> v aplikaci.

Můžete zjistit, kdy se aplikace bude aktivní, a to tak, že zpracuje událost <xref:System.Windows.Application.Activated?displayProperty=nameWithType>.

Podobně může být aplikace neaktivní v následujících případech:

- Uživatel přepne do jiné aplikace z aktuálního.

- Když se aplikace vypíná.

Můžete zjistit, kdy se aplikace bude neaktivní, a to tak, že zpracuje událost <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>.

Následující kód ukazuje, jak zpracovat <xref:System.Windows.Application.Activated> a <xref:System.Windows.Application.Deactivated> události k určení, zda je aplikace aktivní.

[!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]

[!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
[!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]

Lze také aktivovat a deaktivovat <xref:System.Windows.Window>. Další informace najdete v tématu <xref:System.Windows.Window.Activated?displayProperty=nameWithType> a <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType>.

> [!NOTE]
> Pro XBAP nejsou vyvolány <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ani <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>.

<a name="Application_Shutdown"></a>

### <a name="application-shutdown"></a>Vypnutí aplikace

Životnost aplikace končí, když je vypnutá, což může nastat z následujících důvodů:

- Uživatel zavře všechny <xref:System.Windows.Window>.

- Uživatel zavírá hlavní <xref:System.Windows.Window>.

- Uživatel ukončí relaci systému Windows odhlášením nebo vypnutím.

- Byla splněna podmínka specifická pro aplikaci.

Pro usnadnění správy vypnutí aplikace <xref:System.Windows.Application> poskytuje <xref:System.Windows.Application.Shutdown%2A> metodu, vlastnost <xref:System.Windows.Application.ShutdownMode%2A> a události <xref:System.Windows.Application.SessionEnding> a <xref:System.Windows.Application.Exit>.

> [!NOTE]
> <xref:System.Windows.Application.Shutdown%2A> lze volat pouze z aplikací, které mají <xref:System.Security.Permissions.UIPermission>. Samostatná aplikace WPF mají vždy toto oprávnění. Aplikace XBAP spuštěné v izolovaném prostoru zabezpečení zóny Internet Zone ale nepodporují.

#### <a name="shutdown-mode"></a>Režim vypnutí

Většina aplikací se vypne buď při zavření všech oken nebo při zavření hlavního okna. Někdy ale jiné podmínky specifické pro aplikace mohou určit, kdy se aplikace vypíná. Můžete určit podmínky, za kterých se vaše aplikace vypne, nastavením <xref:System.Windows.Application.ShutdownMode%2A> s jednou z následujících <xref:System.Windows.ShutdownMode> hodnot výčtu:

- <xref:System.Windows.ShutdownMode.OnLastWindowClose>

- <xref:System.Windows.ShutdownMode.OnMainWindowClose>

- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>

Výchozí hodnota <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnLastWindowClose>, což znamená, že se aplikace automaticky ukončí, když uživatel zavře poslední okno aplikace. Pokud by však měla být aplikace ukončena při zavření hlavního okna, WPF automaticky provede nastavení <xref:System.Windows.Application.ShutdownMode%2A> na <xref:System.Windows.ShutdownMode.OnMainWindowClose>. To je ukázáno v následujícím příkladu.

[!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]

Pokud máte podmínky pro vypnutí specifické pro aplikaci, nastavte <xref:System.Windows.Application.ShutdownMode%2A> na <xref:System.Windows.ShutdownMode.OnExplicitShutdown>. V takovém případě je vaší zodpovědností ukončit aplikaci tím, že explicitně zavoláte metodu <xref:System.Windows.Application.Shutdown%2A>; v opačném případě bude aplikace dál běžet i v případě, že jsou všechna okna zavřena. Všimněte si, že <xref:System.Windows.Application.Shutdown%2A> je volána implicitně, pokud je <xref:System.Windows.Application.ShutdownMode%2A> buď <xref:System.Windows.ShutdownMode.OnLastWindowClose> nebo <xref:System.Windows.ShutdownMode.OnMainWindowClose>.

> [!NOTE]
> <xref:System.Windows.Application.ShutdownMode%2A> lze nastavit z XBAP, ale je ignorována; XBAP je vždy vypnuta, když je přecházení v prohlížeči nebo když je zavřen prohlížeč, který je hostitelem aplikace XBAP. Další informace najdete v tématu [Přehled navigace](navigation-overview.md).

#### <a name="session-ending"></a>Ukončení relace

Podmínky vypnutí, které jsou popsány vlastností <xref:System.Windows.Application.ShutdownMode%2A>, jsou specifické pro aplikaci. V některých případech ale může dojít k vypnutí aplikace v důsledku externí podmínky. Nejběžnější externí podmínka nastane, když uživatel ukončí relaci systému Windows následujícími akcemi:

- Odhlášení

- Vypínání

- Restartovat

- Hibernace

Chcete-li zjistit, kdy relace systému Windows skončí, můžete zpracovat událost <xref:System.Windows.Application.SessionEnding>, jak je znázorněno v následujícím příkladu.

[!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]

[!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
[!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]

V tomto příkladu kód zkontroluje vlastnost <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> a určí, jak probíhá ukončování relace systému Windows. Tato hodnota se používá k zobrazení potvrzovací zprávy uživateli. Pokud uživatel nechce ukončit relaci, sada kódů <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> `true`, aby nedošlo k ukončení relace systému Windows.

> [!NOTE]
> pro XBAP nejsou vyvolány <xref:System.Windows.Application.SessionEnding>.

#### <a name="exit"></a>Ukončit

Když se aplikace ukončí, může být nutné provést nějaké konečné zpracování, jako je například zachování stavu aplikace. V těchto situacích můžete zpracovat událost <xref:System.Windows.Application.Exit>, jako obslužná rutina `App_Exit` události v následujícím příkladu. Je definován jako obslužná rutina události v souboru *App. XAML* . Jeho implementace je zvýrazněna v souborech *App.XAML.cs* a *Application. XAML. vb* .

[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]

[!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
[!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]

Úplný příklad naleznete v tématu [trvalé a obnovení vlastností rozsahu aplikace napříč relacemi aplikace](persist-and-restore-application-scope-properties.md).

<xref:System.Windows.Application.Exit> může zpracovávat samostatné aplikace i XBAP. Pro XBAP je <xref:System.Windows.Application.Exit> vyvolána v následujících případech:

- Aplikace XBAP přešla jinam.

- V aplikaci Internet Explorer, pokud je zavřena karta, která je hostitelem aplikace XBAP.

- Při zavření prohlížeče.

#### <a name="exit-code"></a>Ukončovací kód

Aplikace jsou většinou spuštěné operačním systémem v reakci na požadavek uživatele. Aplikaci však lze spustit jinou aplikací k provedení určitého úkolu. Po ukončení spuštěné aplikace může spuštění aplikace chtít znát podmínku, za kterou se spuštěné aplikace vypnula. V těchto situacích systém Windows umožňuje aplikacím vracet ukončovací kód aplikace při vypnutí. Ve výchozím nastavení aplikace WPF vrátí ukončovací kód s hodnotou 0.

> [!NOTE]
> Při ladění ze sady Visual Studio se ukončovací kód aplikace zobrazuje v okně **výstup** , když se aplikace ukončí, ve zprávě, která vypadá takto:
>
> `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`
>
> Otevřete okno **výstup** kliknutím na **výstup** v nabídce **zobrazení** .

Chcete-li změnit ukončovací kód, můžete zavolat <xref:System.Windows.Application.Shutdown%28System.Int32%29> přetížení, které přijímá celočíselný argument jako ukončovací kód:

[!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
[!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]

Můžete zjistit hodnotu ukončovacího kódu a změnit ji pomocí zpracování události <xref:System.Windows.Application.Exit>. Obslužná rutina události <xref:System.Windows.Application.Exit> je předána <xref:System.Windows.ExitEventArgs>, která poskytuje přístup k ukončovacímu kódu s vlastností <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A>. Další informace naleznete v tématu <xref:System.Windows.Application.Exit>.

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

Implementace této podpory závisí na schopnostech detekovat neošetřené výjimky, což znamená, že se událost <xref:System.Windows.Application.DispatcherUnhandledException> vyvolá pro.

[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]

[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]

Obslužné rutině události <xref:System.Windows.Application.DispatcherUnhandledException> se předává <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> parametr, který obsahuje kontextové informace týkající se neošetřené výjimky, včetně samotné výjimky (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). Tyto informace můžete použít k určení, jak se má výjimka zpracovat.

Při zpracování <xref:System.Windows.Application.DispatcherUnhandledException>byste měli nastavit vlastnost <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> na `true`; v opačném případě WPF stále považuje výjimku za neošetřenou a obnoví výchozí chování popsané výše. Je-li vyvolána neošetřená výjimka a událost <xref:System.Windows.Application.DispatcherUnhandledException> není zpracována nebo je událost zpracována a <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> je nastavena na hodnotu `false`, aplikace se okamžitě ukončí. Kromě toho nejsou vyvolány žádné další <xref:System.Windows.Application> události. V důsledku toho je potřeba zpracovat <xref:System.Windows.Application.DispatcherUnhandledException>, pokud má aplikace kód, který musí běžet před vypnutím aplikace.

I když se aplikace může vypnout v důsledku neošetřené výjimky, aplikace se obvykle vypne v reakci na požadavek uživatele, jak je popsáno v další části.

<a name="Application_Lifetime_Events"></a>

### <a name="application-lifetime-events"></a>Události životního cyklu aplikace

Samostatné aplikace a XBAP nemají přesně stejné životnosti. Následující obrázek znázorňuje klíčové události při životnosti samostatné aplikace a ukazuje pořadí, ve kterém jsou vyvolány.

![Samostatné události &#45; objektu aplikační aplikace](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")

Podobně následující obrázek ilustruje klíčové události v době životnosti XBAP a zobrazuje sekvenci, ve které jsou vyvolány.

![Události &#45; objektu aplikace XBAP](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Application>
- [Přehled Windows ve WPF](wpf-windows-overview.md)
- [Přehled navigace](navigation-overview.md)
- [Prostředek, obsah a datové soubory aplikace WPF](wpf-application-resource-content-and-data-files.md)
- [Sbalení URI v technologii WPF](pack-uris-in-wpf.md)
- [Aplikační model: témata s postupy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [Vývoj aplikací](index.md)
