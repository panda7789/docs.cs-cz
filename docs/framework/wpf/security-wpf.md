---
title: "Zabezpečení (WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML files [WPF], sandbox behavior
- browser-hosted application security [WPF]
- application security [WPF]
- navigation security [WPF]
- loose XAML files [WPF], sandbox behavior
- WPF security [WPF]
- WebBrowser control [WPF], security
- feature controls [WPF], security
- XBAP security [WPF]
- Internet Explorer security settings [WPF]
ms.assetid: ee1baea0-3611-4e36-9ad6-fcd5205376fb
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fae5c8553cc395268b1c6afb1b64727014756975
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="security-wpf"></a>Zabezpečení (WPF)
<a name="introduction"></a>Při vývoji [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] samostatné a webové aplikace, musíte zvážit modelu zabezpečení. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]spuštění samostatné aplikace s neomezená oprávnění ( [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **FullTrust** sadě oprávnění), jestli nasadit pomocí Instalační služby systému Windows (.msi), XCopy, nebo [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]. Nasazení částečným vztahem důvěryhodnosti, samostatné aplikace WPF s ClickOnce není podporováno. Plné důvěryhodnosti hostitelskou aplikaci však můžete vytvořit s částečnou důvěryhodností <xref:System.AppDomain> pomocí modelu doplňku rozhraní .NET Framework. Další informace najdete v tématu [WPF doplňky přehled](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]aplikace hostované prohlížečem hostuje [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)] nebo Firefox, a může být buď [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] nebo přijít [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] dokumenty, kde najdete další informace najdete v tématu [přehled aplikace prohlížeče XAML WPF](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]aplikace hostované prohlížečem provést v rámci izolovaného prostoru zabezpečení částečné důvěryhodnosti, ve výchozím nastavení, která je omezená na výchozí [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **Internet** oprávnění sady zón. To efektivně izoluje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace hostované prohlížečem z klientského počítače stejným způsobem, kterou byste očekávali typické webové aplikace k izolaci. XBAP můžete zvýšit oprávnění, až úplný vztah důvěryhodnosti, v závislosti na zóny zabezpečení adresu nasazení a konfigurace zabezpečení klienta. Další informace najdete v tématu [WPF částečné důvěryhodnosti zabezpečení](../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
 Toto téma popisuje model zabezpečení pro [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] samostatné a webové aplikace.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Bezpečné navigace](#SafeTopLevelNavigation)  
  
-   [Nastavení zabezpečení webové procházení softwaru](#InternetExplorerSecuritySettings)  
  
-   [WebBrowser – ovládací prvek a ovládací prvky funkce](#webbrowser_control_and_feature_controls)  
  
-   [Zakázání APTCA sestavení pro klientské částečně důvěryhodné aplikace](#APTCA)  
  
-   [Chování izolovaného prostoru pro soubory přijít XAML](#LooseContentSandboxing)  
  
-   [Prostředky pro vývoj WPF aplikace, které podporují zabezpečení](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Bezpečné navigace  
 Pro [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] rozlišuje dva typy navigace: aplikace a prohlížeč.  
  
 *Navigace aplikace* je navigace mezi položkami obsahu v rámci aplikace, která je hostovaná v prohlížeči. *Navigace* je navigace, který změní adresu URL obsahu a umístění prohlížeče sám sebe. Vztah mezi aplikací navigace (obvykle XAML) a prohlížeče navigace (obvykle HTML) je znázorněn na následujícím obrázku:
  
 ![Navigace – diagram](../../../docs/framework/wpf/media/safetoplevelnavigationfigure.png "SafeTopLevelNavigationFigure")  
  
 Typ obsahu, který je považován za bezpečné pro přístup [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] přejděte na je primárně určen podle zda je použit navigační aplikace nebo prohlížeče navigace.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Navigace zabezpečení aplikací  
 Navigace aplikace se považuje za bezpečné, pokud je možné identifikovat pomocí sadu [!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)], který podporuje čtyři typy obsahu:  
  
|Typ obsahu|Popis|Příklad identifikátoru URI|  
|------------------|-----------------|-----------------|  
|Prostředek|Soubory, které jsou přidány do projektu s typem sestavení **prostředků**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Obsah|Soubory, které jsou přidány do projektu s typem sestavení **obsahu**.|`pack://application:,,,/MyContentFile.xaml`|  
|Lokality původu|Soubory, které jsou přidány do projektu s typem sestavení **žádné**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Kód aplikace|XAML prostředky, které mají kompilované kódu na pozadí.<br /><br /> -nebo-<br /><br /> Soubory XAML, které jsou přidány do projektu s typem sestavení **stránky**.|`pack://application:,,,/MyResourceFile``.xaml`|  
  
> [!NOTE]
>  Další informace o souborech data aplikací a aktualizací Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)], najdete v části [prostředek aplikace WPF, obsah a datové soubory](../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 Soubory tyto typy obsahu můžete přesměrováni do buď uživatelem nebo prostřednictvím kódu programu:  
  
-   **Navigace uživatele**. Uživatel přejde kliknutím <xref:System.Windows.Documents.Hyperlink> elementu.  
  
-   **Programová navigační**. Aplikace přejde bez zásahu uživatele, například nastavením <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> vlastnost.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Navigace zabezpečení prohlížeče  
 Navigace je považováno za bezpečné pouze za následujících podmínek:  
  
-   **Navigace uživatele**. Uživatel přejde kliknutím <xref:System.Windows.Documents.Hyperlink> element, který je v rámci hlavní <xref:System.Windows.Navigation.NavigationWindow>není v vnořený <xref:System.Windows.Controls.Frame>.  
  
-   **Zóny**. Obsah se přešli se nachází na Internetu nebo místní intranet.  
  
-   **Protokol**. Používá protokol je buď **http**, **https**, **soubor**, nebo **mailto**.  
  
 Pokud [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] pokusí přejděte na obsah způsobem, který není v souladu s těmito podmínkami <xref:System.Security.SecurityException> je vyvolána výjimka.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Nastavení zabezpečení webové procházení softwaru  
 Nastavení zabezpečení ve vašem počítači určit přístup, který je povolen libovolný pro webové procházení softwaru. Pro webové procházení softwaru zahrnuje všechny aplikace nebo součásti, která používá [WinINet](http://go.microsoft.com/fwlink/?LinkId=179379) nebo [UrlMon](http://go.microsoft.com/fwlink/?LinkId=179383) rozhraní API, včetně aplikace Internet Explorer a PresentationHost.exe.  
  
 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)]poskytuje mechanismus, pomocí kterého můžete nakonfigurovat funkce, které je povoleno spustit pomocí nebo z [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)], včetně následujících:  
  
-   [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)]-spolehlivé součásti  
  
-   Moduly plug-in a ovládacích prvků ActiveX  
  
-   Soubory ke stažení  
  
-   Skriptování  
  
-   Ověření uživatele  
  
 Kolekce funkcí, které mohly být zabezpečeny tímto způsobem je konfigurováno na základě na zóny pro **Internet**, **intranetu**, **Důvěryhodné servery**, a  **Servery s omezeným přístupem** zóny. Následující kroky popisují, jak konfigurovat nastavení zabezpečení:  
  
1.  Otevřete **ovládací panely**.  
  
2.  Klikněte na tlačítko **síť a Internet** a pak klikněte na **Možnosti Internetu**.  
  
     Zobrazí se dialogové okno Možnosti Internetu.  
  
3.  Na **zabezpečení** vyberte ke konfiguraci nastavení zabezpečení pro zónu.  
  
4.  Klikněte **vlastní úroveň** tlačítko.  
  
     **Nastavení zabezpečení** se zobrazí dialogové okno a můžete nakonfigurovat nastavení zabezpečení pro vybrané zóny.  
  
     ![Dialogové okno nastavení zabezpečení](../../../docs/framework/wpf/media/wpfsecurityfigure1.PNG "WPFSecurityFigure1")  
  
> [!NOTE]
>  Do dialogového okna Možnosti Internetu můžete získat také z aplikace Internet Explorer. Klikněte na tlačítko **nástroje** a pak klikněte na **Možnosti Internetu**.  
  
 Počínaje [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], konkrétně pro následující nastavení zabezpečení [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] jsou zahrnuty:  
  
-   **Ke ztrátě XAML**. Ovládací prvky zda [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] můžete přejít k a ztrátě [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory. (Povolit, zakázat a výzvu možnosti).  
  
-   **Aplikace prohlížeče XAML**. Ovládací prvky zda [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] můžete přejít k a spustit [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. (Povolit, zakázat a výzvu možnosti).  
  
 Ve výchozím nastavení, tato nastavení jsou všechny povolena pro **Internet**, **místní intranet**, a **Důvěryhodné servery** zóny a zakázáno **servery s omezeným přístupem**  zóny.  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>Nastavení registru související se zabezpečením WPF  
 Kromě nastavení zabezpečení jsou dostupná prostřednictvím možnosti Internetu jsou k dispozici pro selektivní blokování celou řadu funkcí WPF citlivé na zabezpečení následující hodnoty registru. Hodnoty jsou definovány v následujícím klíči:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 V následující tabulce jsou uvedeny hodnoty, které lze nastavit.  
  
|Název hodnoty|Typ hodnoty|Údaj hodnoty|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|1 tak, aby zakázala; 0 pro povolení.|  
|LooseXamlDisallow|REG_DWORD|1 tak, aby zakázala; 0 pro povolení.|  
|WebBrowserDisallow|REG_DWORD|1 tak, aby zakázala; 0 pro povolení.|  
|MediaAudioDisallow|REG_DWORD|1 tak, aby zakázala; 0 pro povolení.|  
|MediaImageDisallow|REG_DWORD|1 tak, aby zakázala; 0 pro povolení.|  
|MediaVideoDisallow|REG_DWORD|1 tak, aby zakázala; 0 pro povolení.|  
|ScriptInteropDisallow|REG_DWORD|1 tak, aby zakázala; 0 pro povolení.|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## <a name="webbrowser-control-and-feature-controls"></a>WebBrowser – ovládací prvek a ovládací prvky funkce  
 WPF <xref:System.Windows.Controls.WebBrowser> řízení lze použít k hostování webového obsahu. WPF <xref:System.Windows.Controls.WebBrowser> řízení zabalí základní ovládacího prvku WebBrowser ActiveX. WPF poskytuje některé podporu pro zabezpečení aplikace při použití WPF <xref:System.Windows.Controls.WebBrowser> řízení hostitele nedůvěryhodná webového obsahu. Ale některé funkce zabezpečení se musí použít přímo pomocí aplikací pomocí <xref:System.Windows.Controls.WebBrowser> ovládacího prvku. Další informace o ovládacího prvku WebBrowser ActiveX najdete v tématu [WebBrowser řízení přehledy a kurzy](http://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
>  Tato část platí také pro <xref:System.Windows.Controls.Frame> řízení vzhledem k tomu, že se používá <xref:System.Windows.Controls.WebBrowser> přejděte na obsah HTML.  
  
 Pokud WPF <xref:System.Windows.Controls.WebBrowser> řízení se používá k hostování nedůvěryhodné webového obsahu, vaše aplikace by měla používat s částečnou důvěryhodností <xref:System.AppDomain> pomohou izolovat kódu aplikace z potenciálně škodlivý kód skriptu HTML. To platí hlavně v případě aplikace komunikuje s hostované skriptu pomocí <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> metoda a <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> vlastnost. Další informace najdete v tématu [WPF doplňky přehled](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 Pokud vaše aplikace používá WPF <xref:System.Windows.Controls.WebBrowser> řízení, jiný způsob, jak zvýšit zabezpečení a zmírnit útoky je umožnit ovládací prvky funkce Internet Exploreru. Ovládací prvky funkce jsou dodatky do aplikace Internet Explorer, které umožňují správcům a vývojářům konfigurovat funkce Internet Exploreru a aplikací, které jsou hostiteli ovládacího prvku WebBrowser ActiveX, který WPF <xref:System.Windows.Controls.WebBrowser> řízení zabalí. Funkce lze nakonfigurovat pomocí [CoInternetSetFeatureEnabled](http://go.microsoft.com/fwlink/?LinkId=179394) funkce nebo změnou hodnoty v registru. Další informace o ovládacích prvcích funkce najdete v tématu [Úvod k ovládacím prvkům funkce](http://go.microsoft.com/fwlink/?LinkId=179390) a [internetové ovládací prvky funkce](http://go.microsoft.com/fwlink/?LinkId=179392).  
  
 Pokud vyvíjíte aplikace WPF samostatné, která používá WPF <xref:System.Windows.Controls.WebBrowser> řízení, WPF automaticky povolí funkci ovládací prvky pro vaši aplikaci.  
  
|Funkce řízení|  
|---------------------|  
|FEATURE_MIME_HANDLING|  
|FEATURE_MIME_SNIFFING|  
|FEATURE_OBJECT_CACHING|  
|FEATURE_SAFE_BINDTOOBJECT|  
|FEATURE_WINDOW_RESTRICTIONS|  
|FEATURE_ZONE_ELEVATION|  
|FEATURE_RESTRICT_FILEDOWNLOAD|  
|FEATURE_RESTRICT_ACTIVEXINSTALL|  
|FEATURE_ADDON_MANAGEMENT|  
|FEATURE_HTTP_USERNAME_PASSWORD_DISABLE|  
|FEATURE_SECURITYBAND|  
|FEATURE_UNC_SAVEDFILECHECK|  
|FEATURE_VALIDATE_NAVIGATE_URL|  
|FEATURE_DISABLE_TELNET_PROTOCOL|  
|FEATURE_WEBOC_POPUPMANAGEMENT|  
|FEATURE_DISABLE_LEGACY_COMPRESSION|  
|FEATURE_SSLUX|  
  
 Vzhledem k tomu, že tyto funkce ovládací prvky jsou povolené bezpodmínečně, plné důvěryhodnosti aplikace může být narušena je. V takovém případě pokud nehrozí nebezpečí zabezpečení pro konkrétní aplikace a obsah, který je hostitelem, je možné zakázat ovládacího prvku odpovídající funkce.  
  
 Ovládací prvky funkce platí procesem vytvoření instance objektu WebBrowser ActiveX. Proto pokud vytváříte samostatná aplikace, která můžete přejít na nedůvěryhodný obsah, byste měli vážně zvážit povolení dalších funkcí ovládací prvky.  
  
> [!NOTE]
>  Toto doporučení je založena na obecná doporučení pro zabezpečení MSHTML a SHDOCVW hostitele. Další informace najdete v tématu [The MSHTML hostitele zabezpečení – nejčastější dotazy: část I II](http://go.microsoft.com/fwlink/?LinkId=179396) a [The MSHTML hostitele zabezpečení – nejčastější dotazy: část II II](http://go.microsoft.com/fwlink/?LinkId=179415).  
  
 Pro vaše spustitelný soubor zvažte povolení následující ovládací prvky funkce nastavením hodnotu registru na 1.  
  
|Funkce řízení|  
|---------------------|  
|FEATURE_ACTIVEX_REPURPOSEDETECTION|  
|FEATURE_BLOCK_LMZ_IMG|  
|FEATURE_BLOCK_LMZ_OBJECT|  
|FEATURE_BLOCK_LMZ_SCRIPT|  
|FEATURE_RESTRICT_RES_TO_LMZ|  
|FEATURE_RESTRICT_ABOUT_PROTOCOL_IE7|  
|FEATURE_SHOW_APP_PROTOCOL_WARN_DIALOG|  
|FEATURE_LOCALMACHINE_LOCKDOWN|  
|FEATURE_FORCE_ADDR_AND_STATUS|  
|FEATURE_RESTRICTED_ZONE_WHEN_FILE_NOT_FOUND|  
  
 Pro vaše spustitelný soubor zvažte zákaz následující funkce řízení nastavením hodnotu registru na 0.  
  
|Funkce řízení|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Pokud spustíte s částečnou důvěryhodností [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] WPF, který obsahuje <xref:System.Windows.Controls.WebBrowser> řídit ve [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)], WPF hostitelem ovládacího prvku WebBrowser ActiveX v adresním prostoru procesu aplikace Internet Explorer. Vzhledem k tomu, že je ovládací prvek WebBrowser ActiveX hostované v [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] zpracovat všechny ovládací prvky funkce pro Internet Explorer je povolená i u ovládacího prvku WebBrowser ActiveX.  
  
 Aplikace XBAP spuštěna v aplikaci Internet Explorer také získat další úroveň zabezpečení ve srovnání s normální samostatné aplikace. Je tento další zabezpečení, protože aplikace Internet Explorer a proto ovládacího prvku WebBrowser ActiveX spouští v chráněném režimu, ve výchozím nastavení na [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] a [!INCLUDE[win7](../../../includes/win7-md.md)]. Další informace o chráněném režimu, najdete v části [Princip fungování a způsob práce v Internet Exploreru chráněný režim](http://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
>  Pokud zkusíte spustit XBAP, která zahrnuje WPF <xref:System.Windows.Controls.WebBrowser> ovládacího prvku Firefox, zatímco v zóně Internet, <xref:System.Security.SecurityException> bude vyvolána. Toto je z důvodu zásad zabezpečení WPF.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Zakázání APTCA sestavení pro klientské částečně důvěryhodné aplikace  
 Když jsou spravované sestavení nainstalované do [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)], budou k plně důvěryhodná, protože uživatel musí poskytnout výslovná oprávnění k instalaci. Protože jsou plně důvěryhodné, můžete je používat jenom plně důvěryhodný pro spravované klientské aplikace. Povolit částečně důvěryhodné aplikace používat, musí být označené <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). K tomuto atributu by měl být označen pouze sestavení, které byly testovány jako bezpečné pro spuštění v částečné důvěryhodnosti.  
  
 Je však možné APTCA sestavení vykazovat chyba zabezpečení po nainstalování do [!INCLUDE[TLA2#tla_gac](../../../includes/tla2sharptla-gac-md.md)]. Po zjištění chyby zabezpečení vydavatelů sestavení může vytvořit aktualizaci zabezpečení vyřešte problém na existující instalace a k ochraně proti instalace, které po problému může dojít ke zjištění. Jednou z možností pro aktualizaci je odinstaluje sestavení, i když, je možné ukončit jiné plně důvěryhodný pro klientské aplikace používající sestavení.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]poskytuje mechanismus, pomocí kterého je možné zakázat APTCA sestavení pro částečně důvěryhodné [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] bez odinstalace APTCA sestavení.  
  
 Chcete-li zakázat APTCA sestavení, budete muset vytvořte klíč registru speciální:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Na obrázku je příklad:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Tento klíč vytváří záznam pro APTCA sestavení. Také budete muset vytvořit hodnotu v tomto klíči, který povolí nebo zakáže sestavení. Tady jsou podrobnosti o hodnotě:  
  
-   Název hodnoty: **APTCA_FLAG**.  
  
-   Typ hodnoty: **REG_DWORD**.  
  
-   Údaj hodnoty: **1** zakázat; **0** povolit.  
  
 Pokud má být zakázána klientské částečně důvěryhodné aplikace sestavení, můžete napsat aktualizaci, která vytvoří klíč registru a hodnoty.  
  
> [!NOTE]
>  Základní [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] sestavení nemá vliv zakázání tímto způsobem, protože jsou potřebné pro spouštění spravovaných aplikací. Podpora pro zakázání APTCA sestavení je primárně určeno k aplikacím třetích stran.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Chování izolovaného prostoru pro soubory přijít XAML  
 Uvolněná [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory jsou jen značek soubory XAML, které nezávisí na žádné kódu, obslužné rutiny události nebo sestavení specifické pro aplikaci. Pokud ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory jsou přešli přímo z prohlížeče, jsou načteny v izolovaném prostoru zabezpečení založené na sadě oprávnění výchozí internetové zóny.  
  
 Chování zabezpečení je však jinou, když volné [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory jsou buď z přešli <xref:System.Windows.Navigation.NavigationWindow> nebo <xref:System.Windows.Controls.Frame> v samostatné aplikaci.  
  
 V obou případech přijít [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubor, který je přešli dědí oprávnění jeho hostitelskou aplikaci. Toto chování však může být žádoucí z hlediska zabezpečení, zvlášť pokud ztratit [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubor byl vytvořen entita, která není důvěryhodný nebo je neznámý. Tento typ obsahu, se označuje jako *externí obsah*a obě <xref:System.Windows.Controls.Frame> a <xref:System.Windows.Navigation.NavigationWindow> lze nakonfigurovat, aby izolovat ji při navigaci na. Izolace se dosahuje nastavení **SandboxExternalContent** vlastnost na hodnotu true, jak je znázorněno v následujících příkladech pro <xref:System.Windows.Controls.Frame> a <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 S tímto nastavením budou načteny externí obsah do procesu, která je oddělená od proces, který je hostitelem aplikace. Tento proces je omezen na výchozí internetové zóny oprávnění sady, efektivně izoluje od hostitelskou aplikaci a klientským počítačem.  
  
> [!NOTE]
>  I když navigace k přijít [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory z buď <xref:System.Windows.Navigation.NavigationWindow> nebo <xref:System.Windows.Controls.Frame> v samostatné je implementováno aplikace založené na prohlížeči WPF hosting infrastruktury, zahrnující proces PresentationHost úroveň zabezpečení je mírně nižší než při načtení obsah přímo v aplikaci Internet Explorer na [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] a [!INCLUDE[win7](../../../includes/win7-md.md)] (což by nadále prostřednictvím PresentationHost). Důvodem je samostatná aplikace WPF pomocí webového prohlížeče neposkytuje další funkce chráněný režim zabezpečení aplikace Internet Explorer.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Prostředky pro vývoj WPF aplikace, které podporují zabezpečení  
 Toto jsou některé další zdroje, které vám pomůžou s vývojem [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace, které podporují zabezpečení:  
  
|Oblast|Prostředek|  
|----------|--------------|  
|Spravovaný kód|[Vzory a postupy doprovodné materiály zabezpečení pro aplikace](http://go.microsoft.com/fwlink/?LinkId=117426)|  
|[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]|[Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)|  
|[!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]|[ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[Částečné zabezpečení důvěryhodnosti WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Viz také  
 [Částečné zabezpečení důvěryhodnosti WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [Strategie zabezpečení WPF – zabezpečení platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [Strategie zabezpečení WPF – engineering zabezpečení](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)  
 [Vzory a postupy doprovodné materiály zabezpečení pro aplikace](http://go.microsoft.com/fwlink/?LinkId=117426)  
 [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)  
 [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
