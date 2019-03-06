---
title: Zabezpečení (WPF)
ms.date: 03/30/2017
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
ms.openlocfilehash: be9f1916722b493490541046906a38b9fac63a4e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371980"
---
# <a name="security-wpf"></a>Zabezpečení (WPF)
<a name="introduction"></a> Při vývoji, nasazení samostatné služby Windows Presentation Foundation (WPF) a aplikace hostované v prohlížeči, je nutné zvážit modelu zabezpečení. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] samostatné aplikace jsou spouštěny s neomezenými oprávněními ( [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **FullTrust** sada oprávnění), ať už nasazeným v rámci Windows Installer (MSI), příkazu XCopy, nebo [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]. Nasazení částečným vztahem důvěryhodnosti, samostatné aplikace WPF s ClickOnce se nepodporuje. Však vytvořit hostitele úplného vztahu důvěryhodnosti aplikace s částečnou důvěryhodností <xref:System.AppDomain> pomocí modelu doplňku rozhraní .NET Framework. Další informace najdete v tématu [přehled doplňků WPF](./app-development/wpf-add-ins-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace hostované prohlížečem hostují [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)] nebo Firefox, a může být buď [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] nebo dojde ke ztrátě [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] dokumenty pro další informace najdete v tématu [přehled aplikací prohlížeče WPF XAML](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace hostované v prohlížeči jsou spouštěny v částečném vztahu důvěryhodnosti zabezpečení izolovaného prostoru ve výchozím nastavení, která je omezena na výchozí hodnotu [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **Internet** oprávnění sady zón. To efektivně izoluje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace hostované v prohlížeči od klientského počítače stejným způsobem, že byste očekávali typické webové aplikace. XBAP, který může zvýšení oprávnění, až plné důvěryhodnosti, v závislosti na zóně zabezpečení adresy URL nasazení a konfigurace zabezpečení klienta. Další informace najdete v tématu [částečné zabezpečení důvěryhodnosti WPF](wpf-partial-trust-security.md).  
  
 Toto téma popisuje model zabezpečení pro nasazení samostatné služby Windows Presentation Foundation (WPF) a aplikace hostované prohlížečem.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Bezpečné navigace](#SafeTopLevelNavigation)  
  
-   [Nastavení softwaru zabezpečení procházení webu](#InternetExplorerSecuritySettings)  
  
-   [WebBrowser – ovládací prvek a ovládací prvky funkcí](#webbrowser_control_and_feature_controls)  
  
-   [Zakázání sestavení APTCA pro částečně důvěryhodná klientské aplikace](#APTCA)  
  
-   [Chování izolovaného prostoru pro soubory volný XAML](#LooseContentSandboxing)  
  
-   [Zdroje informací pro vývoj aplikací WPF, které podporují zabezpečení](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Bezpečné navigace  
 Pro [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] rozlišuje dva typy navigace: aplikace a prohlížeč.  
  
 *Navigační aplikace* je navigace mezi položkami obsahu v rámci aplikace, která je hostovaná v prohlížeči. *Navigace v prohlížeči* se navigační prvek se změní obsah a umístění URL samotného prohlížeče. Vztah mezi navigační aplikace (obvykle XAML) a navigace v prohlížeči (obvykle ve formátu HTML) je znázorněn na následujícím obrázku:
  
 ![Diagram navigačního](./media/safetoplevelnavigationfigure.png "SafeTopLevelNavigationFigure")  
  
 Typ obsahu, který je bezpečný pro [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] přejděte k položce je primárně určeno, jestli se používá navigaci v rámci aplikace nebo navigace v prohlížeči.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Zabezpečení navigace aplikace  
 Navigační aplikace se považuje za bezpečné, pokud jej lze identifikovat s pack [!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)], který podporuje čtyři typy obsahu:  
  
|Typ obsahu|Popis|Příklad identifikátoru URI|  
|------------------|-----------------|-----------------|  
|Prostředek|Soubory, které jsou přidány do projektu s typem sestavení **prostředků**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Obsah|Soubory, které jsou přidány do projektu s typem sestavení **obsahu**.|`pack://application:,,,/MyContentFile.xaml`|  
|Místo původu|Soubory, které jsou přidány do projektu s typem sestavení **žádný**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Kód aplikace|Zdroje XAML, které mají zkompilovaného kódu.<br /><br /> -nebo-<br /><br /> Soubory XAML, které jsou přidány do projektu s typem sestavení **stránky**.|`pack://application:,,,/MyResourceFile``.xaml`|  
  
> [!NOTE]
>  Další informace o datových souborů aplikací a aktualizací Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)], naleznete v tématu [prostředek aplikace WPF, obsah a datové soubory](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 Soubory, typy obsahu se dá Navigovat buď uživatelem nebo prostřednictvím kódu programu:  
  
-   **Navigace**. Uživatel přejde po kliknutí <xref:System.Windows.Documents.Hyperlink> elementu.  
  
-   **Programově řízená navigace**. Přejde aplikaci bez zásahu uživatele, třeba tak, že nastavíte <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> vlastnost.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Zabezpečení navigace prohlížeče  
 Navigace v prohlížeči je považován za bezpečný pouze za následujících podmínek:  
  
-   **Navigace**. Uživatel přejde po kliknutí <xref:System.Windows.Documents.Hyperlink> element, který je v rámci hlavní <xref:System.Windows.Navigation.NavigationWindow>, nikoli v vnořený <xref:System.Windows.Controls.Frame>.  
  
-   **Zóna**. Obsah se přejde poté, je umístěn na Internetu nebo místní intranet.  
  
-   **Protokol**. Používá protokol je buď **http**, **https**, **souboru**, nebo **mailto**.  
  
 Pokud [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] pokusí přejít na obsah způsobem, který není v souladu s těmito podmínkami <xref:System.Security.SecurityException> je vyvolána výjimka.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Nastavení softwaru zabezpečení procházení webu  
 Nastavení zabezpečení v počítači určují přístup, jemuž byl poskytnut procházení softwaru. Pro webové procházení softwaru zahrnuje všechny aplikace nebo komponenty, která se používá [WinINet](https://go.microsoft.com/fwlink/?LinkId=179379) nebo [UrlMon](https://go.microsoft.com/fwlink/?LinkId=179383) rozhraní API, včetně aplikace Internet Explorer a PresentationHost.exe.  
  
 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] poskytuje mechanismus, pomocí kterého můžete nakonfigurovat funkce, které se mohou být provedeny podle nebo z [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)], včetně následujících:  
  
-   Rozhraní .NET framework spolehlivé součásti  
  
-   Moduly plug-in a ovládacích prvků ActiveX  
  
-   Soubory ke stažení  
  
-   Skriptování  
  
-   Ověřování uživatelů  
  
 Kolekce funkcí, které je možné svázat tímto způsobem je nakonfigurována na základě na zóny pro **Internet**, **intranetu**, **Důvěryhodné servery**, a  **Servery s omezeným přístupem** zóny. Následující kroky popisují, jak nakonfigurovat nastavení zabezpečení:  
  
1.  Otevřete **Ovládací panely**.  
  
2.  Klikněte na tlačítko **síť a Internet** a potom klikněte na tlačítko **Možnosti Internetu**.  
  
     Zobrazí se dialogové okno Možnosti Internetu.  
  
3.  Na **zabezpečení** kartu, vyberte nastavení zabezpečení pro zónu.  
  
4.  Klikněte na tlačítko **vlastní úroveň** tlačítko.  
  
     **Nastavení zabezpečení** dialogové okno se zobrazí a můžete nakonfigurovat nastavení zabezpečení pro vybrané zóny.  
  
     ![Dialogové okno nastavení zabezpečení](./media/wpfsecurityfigure1.PNG "WPFSecurityFigure1")  
  
> [!NOTE]
>  Do dialogového okna Možnosti Internetu můžete získat také z aplikace Internet Explorer. Klikněte na tlačítko **nástroje** a potom klikněte na tlačítko **Možnosti Internetu**.  
  
 Počínaje [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], jsou zahrnuty následující nastavení zabezpečení konkrétně pro rozhraní .NET Framework:  
  
-   **Volný XAML**. Ovládací prvky, zda [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] můžete přejít na a dojde ke snížení [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory. (Povolit, zakázat a vyzve možnosti).  
  
-   **Aplikace prohlížeče XAML**. Ovládací prvky, zda [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] můžete přejít na a spustit [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. (Povolit, zakázat a vyzve možnosti).  
  
 Ve výchozím nastavení jsou povoleny pro **Internet**, **místní intranet**, a **Důvěryhodné servery** zóny a zakázáno **servery s omezeným přístupem**  zóny.  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>Nastavení registru související se zabezpečením WPF  
 Kromě nastavení zabezpečení jsou dostupná prostřednictvím možnosti Internetu následující hodnoty registru jsou k dispozici pro selektivní blokování celou řadu funkcí WPF citlivé na zabezpečení. Hodnoty jsou definovány v následující klíči:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 V následující tabulce jsou uvedeny hodnoty, které je možné nastavit.  
  
|Název hodnoty|Typ hodnoty|Hodnota dat|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|Chcete zakázat; 1 0 pro povolení využívání.|  
|LooseXamlDisallow|REG_DWORD|Chcete zakázat; 1 0 pro povolení využívání.|  
|WebBrowserDisallow|REG_DWORD|Chcete zakázat; 1 0 pro povolení využívání.|  
|MediaAudioDisallow|REG_DWORD|Chcete zakázat; 1 0 pro povolení využívání.|  
|MediaImageDisallow|REG_DWORD|Chcete zakázat; 1 0 pro povolení využívání.|  
|MediaVideoDisallow|REG_DWORD|Chcete zakázat; 1 0 pro povolení využívání.|  
|ScriptInteropDisallow|REG_DWORD|Chcete zakázat; 1 0 pro povolení využívání.|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## <a name="webbrowser-control-and-feature-controls"></a>WebBrowser – ovládací prvek a ovládací prvky funkcí  
 WPF <xref:System.Windows.Controls.WebBrowser> ovládacího prvku je možné k hostování webového obsahu. WPF <xref:System.Windows.Controls.WebBrowser> obaluje ovládací prvek původního ovládacího prvku WebBrowser ActiveX. WPF podporuje některé pro zabezpečení aplikace, když použijete WPF <xref:System.Windows.Controls.WebBrowser> ovládacího prvku na hostitele nedůvěryhodné webového obsahu. Ale některé funkce zabezpečení se musí použít přímo z aplikace, které používají <xref:System.Windows.Controls.WebBrowser> ovládacího prvku. Další informace o ovládacím prvku WebBrowser ActiveX naleznete v tématu [WebBrowser – ovládací prvek přehledy a kurzy](https://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
>  Tato část platí také pro <xref:System.Windows.Controls.Frame> ovládací prvek, protože používá <xref:System.Windows.Controls.WebBrowser> přejít na obsah ve formátu HTML.  
  
 Pokud WPF <xref:System.Windows.Controls.WebBrowser> ovládací prvek se používá k hostování nedůvěryhodných webového obsahu, aby aplikace používala s částečnou důvěryhodností <xref:System.AppDomain> umožňující ochrání váš kód aplikace z potenciálně škodlivý kód skriptu HTML. To platí zejména v Pokud vaše aplikace pracuje s hostované skriptu s použitím <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> metoda a <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> vlastnost. Další informace najdete v tématu [přehled doplňků WPF](./app-development/wpf-add-ins-overview.md).  
  
 Pokud vaše aplikace používá WPF <xref:System.Windows.Controls.WebBrowser> ovládacího prvku, jiný způsob, jak zvýšit zabezpečení a zmírnění útoků je umožnit ovládací prvky funkcí aplikace Internet Explorer. Ovládací prvky funkcí jsou dodatky k aplikaci Internet Explorer, které umožňují správcům a vývojářům konfigurovat funkce Internet Exploreru a aplikací, které jsou hostiteli ovládacího prvku WebBrowser ActiveX, který WPF <xref:System.Windows.Controls.WebBrowser> řídit zalomí. Ovládací prvky funkcí lze nastavit pomocí [CoInternetSetFeatureEnabled](https://go.microsoft.com/fwlink/?LinkId=179394) funkce nebo změnou hodnoty registru. Další informace o ovládacích prvcích funkce, najdete v části [Úvod k ovládacím prvkům funkce](https://go.microsoft.com/fwlink/?LinkId=179390) a [ovládací prvky Internet funkce](https://go.microsoft.com/fwlink/?LinkId=179392).  
  
 Pokud vyvíjíte samostatné aplikace WPF, která používá WPF <xref:System.Windows.Controls.WebBrowser> ovládací prvek WPF automaticky povoluje následující funkce ovládací prvky pro vaši aplikaci.  
  
|Funkce ovládacího prvku|  
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
  
 Protože tyto ovládací prvky funkce jsou povolené bezpodmínečně, úplného vztahu důvěryhodnosti aplikace může být snížena je. Pokud neexistuje žádná bezpečnostní riziko pro konkrétní aplikace a obsah, který je hostitelem, v tomto případě je možné zakázat ovládací prvek odpovídající funkce.  
  
 Ovládací prvky funkcí se použijí v procesu vytváření instance objektu WebBrowser ActiveX. Proto pokud vytváříte samostatné aplikace, které můžete přejít na nedůvěryhodný obsah, byste měli vážně zvážit povolení dalších funkcí ovládacích prvků.  
  
> [!NOTE]
>  Toto doporučení je založeno na obecná doporučení pro zabezpečení MSHTML a SHDOCVW hostitele. Další informace najdete v tématu [The MSHTML hostitele zabezpečení – nejčastější dotazy: Část II](https://go.microsoft.com/fwlink/?LinkId=179396) a [zabezpečení hostitele MSHTML – nejčastější dotazy: Část II II](https://go.microsoft.com/fwlink/?LinkId=179415).  
  
 Spustitelný soubor zvažte následující ovládací prvky funkce povolíte nastavením hodnoty registru na 1.  
  
|Funkce ovládacího prvku|  
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
  
 Pro spustitelný soubor zvažte zakázání následující ovládací prvek funkce tak, že nastavíte hodnotu registru na hodnotu 0.  
  
|Funkce ovládacího prvku|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Pokud spustíte s částečnou důvěryhodností [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] , který obsahuje WPF <xref:System.Windows.Controls.WebBrowser> v ovládacím prvku [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)], WPF hostuje ovládací prvek WebBrowser ActiveX v adresním prostoru procesu aplikace Internet Explorer. Vzhledem k tomu, že ovládací prvek WebBrowser ActiveX je hostován v [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] zpracovat všechny ovládací prvky funkce pro aplikaci Internet Explorer je povolená i u ovládacího prvku WebBrowser ActiveX.  
  
 XBAP spuštění v aplikaci Internet Explorer také získat další úroveň zabezpečení ve srovnání s normální samostatné aplikace. Toto dodatečné zabezpečení je vzhledem k tomu, že aplikace Internet Explorer a proto ovládací prvek WebBrowser ActiveX běží v chráněném režimu, ve výchozím nastavení [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] a [!INCLUDE[win7](../../../includes/win7-md.md)]. Další informace o chráněném režimu, najdete v části [pochopení a používání v aplikaci Internet Explorer chráněný režim](https://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
>  Pokud se pokusíte spustit XBAP, který zahrnuje WPF <xref:System.Windows.Controls.WebBrowser> ovládacího prvku v aplikaci Firefox, zatímco v zóně Internet, <xref:System.Security.SecurityException> bude vyvolána výjimka. To je způsobeno WPF zásady zabezpečení.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Zakázání sestavení APTCA pro částečně důvěryhodná klientské aplikace  
 Pokud jsou spravovaná sestavení nainstalovány do [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)], budou plně důvěryhodný, protože uživatel musí zadat explicitní oprávnění k instalaci. Protože jsou plně důvěryhodné, můžete použít pouze plně důvěryhodné spravované klientské aplikace je. Povolit částečně důvěryhodné aplikace k jejich použití, musí být označené <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Pouze sestavení, které byly testovány v částečném vztahu důvěryhodnosti jako bezpečné pro spuštění by měly být označené tento atribut.  
  
 Nicméně je možné pro sestavení APTCA vykazovat chyba zabezpečení po nainstalování do [!INCLUDE[TLA2#tla_gac](../../../includes/tla2sharptla-gac-md.md)]. Ihned po zjištění chyba zabezpečení vydavatelů sestavení mohou vytvářet aktualizací zabezpečení pro tento problém vyřešit na existující instalace a k ochraně proti instalace, které po problému může dojít ke zjištění. Jednou z možností pro aktualizaci se při odinstalování sestavení, i když, mohou přestat fungovat jiné plně důvěryhodné klientské aplikace, které používají sestavení.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] poskytuje mechanismus, pomocí kterého lze zakázat sestavení APTCA, pro částečně důvěryhodné [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] bez odinstalování sestavení APTCA.  
  
 Zakázat sestavení APTCA, budete muset vytvořit klíč registru speciální:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Následuje příklad:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Tento klíč se vytvoří záznam pro sestavení APTCA. Také budete muset vytvořit hodnotu v tomto klíči, který povolí nebo zakáže sestavení. Toto jsou podrobnosti o hodnotě:  
  
-   Název hodnoty: **APTCA_FLAG**.  
  
-   Typ hodnoty: **REG_DWORD**.  
  
-   Údaj hodnoty: **1** zakázat; **0** povolit.  
  
 Pokud sestavení má být zakázána částečně důvěryhodné klientské aplikace, můžete napsat aktualizaci, která vytvoří klíče registru a hodnoty.  
  
> [!NOTE]
>  Sestavení rozhraní .NET Core nejsou ovlivněny zakázání tímto způsobem, protože jsou požadovány pro spouštění spravovaných aplikací. Podpora pro zakázání sestavením APTCA je primárně určený k aplikacím třetích stran.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Chování izolovaného prostoru pro soubory volný XAML  
 Přijít o provedené [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory jsou pouze soubory XAML, které nezávisí na použití modelu code-behind, obslužná rutina události nebo sestavení specifická pro aplikaci. Když dojde ke snížení [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory jsou přejde přímo z prohlížeče, jsou načteny v izolovaném prostoru zabezpečení založené na výchozí sady oprávnění zóny Internet.  
  
 Chování zabezpečení se však liší, když dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] buď z se přejde soubory <xref:System.Windows.Navigation.NavigationWindow> nebo <xref:System.Windows.Controls.Frame> v samostatné aplikace.  
  
 V obou případech platí, dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubor, na kterou se přejde dědí oprávnění hostitelské aplikaci. Toto chování však může nežádoucí z hlediska zabezpečení, zejména v případě, že je dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubor byl vytvořen entita, která není důvěryhodný nebo je neznámý. Tento typ obsahu se označuje jako *externí obsah*a obě <xref:System.Windows.Controls.Frame> a <xref:System.Windows.Navigation.NavigationWindow> dá izolovat ji při navigaci mezi. Izolace je dosaženo pomocí nastavení **vlastnost SandboxExternalContent** vlastnost na hodnotu true, jak je znázorněno v následujících příkladech týkajících <xref:System.Windows.Controls.Frame> a <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 S tímto nastavením se načtou do procesu, která je oddělená od procesu, který je hostitelem aplikace externí obsah. Tento proces je omezen na výchozí zóna sada oprávnění Internetu, efektivně izoluje od hostitelské aplikace a klientským počítačem.  
  
> [!NOTE]
>  I když navigaci na volné [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory buď z <xref:System.Windows.Navigation.NavigationWindow> nebo <xref:System.Windows.Controls.Frame> v samostatné je příslušná aplikace implementovaná podle prohlížeče WPF hostování infrastruktury, zahrnující procesu PresentationHost úroveň zabezpečení je mírně nižší než při načtení obsahu přímo v aplikaci Internet Explorer v [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] a [!INCLUDE[win7](../../../includes/win7-md.md)] (které stále by šlo prostřednictvím PresentationHost). Je to proto, že samostatné aplikace WPF pomocí webového prohlížeče neposkytuje další funkce chráněný režim zabezpečení aplikace Internet Explorer.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Zdroje informací pro vývoj aplikací WPF, které podporují zabezpečení  
 Toto jsou některé další prostředky, která pomáhá rozvíjet [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikací, které podporují zabezpečení:  
  
|Oblast|Prostředek|  
|----------|--------------|  
|Spravovaný kód|[Vzory a postupy pro doprovodné materiály zabezpečení pro aplikace](https://go.microsoft.com/fwlink/?LinkId=117426)|  
|[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]|[Zabezpečení přístupu kódu](../misc/code-access-security.md)|  
|[!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]|[ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[Částečné zabezpečení důvěryhodnosti WPF](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Viz také:
- [Částečné zabezpečení důvěryhodnosti WPF](wpf-partial-trust-security.md)
- [Strategie zabezpečení WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)
- [Strategie zabezpečení WPF – engineering zabezpečení](wpf-security-strategy-security-engineering.md)
- [Vzory a postupy pro doprovodné materiály zabezpečení pro aplikace](https://go.microsoft.com/fwlink/?LinkId=117426)
- [Zabezpečení přístupu kódu](../misc/code-access-security.md)
- [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
- [Přehled XAML (WPF)](./advanced/xaml-overview-wpf.md)
