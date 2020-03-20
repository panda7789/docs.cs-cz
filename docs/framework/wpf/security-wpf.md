---
title: Zabezpečení
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
ms.openlocfilehash: e0a56dcbf8d151fcb0d4f6271ecba15c0ff955a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174612"
---
# <a name="security-wpf"></a>Zabezpečení (WPF)
<a name="introduction"></a>Při vývoji samostatné aplikace Windows Presentation Foundation (WPF) a hostované v prohlížeči je třeba zvážit model zabezpečení. Samostatné aplikace WPF se spouštějí s neomezenými oprávněními (sada oprávnění CAS**FullTrust),** ať už jsou nasazeny pomocí Instalační služby systému Windows (.msi), XCopy nebo ClickOnce. Nasazení aplikací s částečnou důvěryhodností, samostatné wpf s ClickOnce není podporováno. Hostitelská aplikace s plnou důvěryhodností však <xref:System.AppDomain> může vytvořit částečnou důvěryhodnost pomocí modelu doplňku rozhraní .NET Framework. Další informace naleznete [v tématu Přehled doplňků WPF](./app-development/wpf-add-ins-overview.md).  
  
 WPF browser-hostované aplikace jsou hostovány v aplikaci Windows Internet Explorer nebo Firefox, a [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] může být buď XAML prohlížeč aplikace (XBAPs) nebo volné dokumenty Pro více informací naleznete [WPF XAML Browser Applications Overview](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 Aplikace hostované prohlížečem WPF se ve výchozím nastavení spouštějí v rámci izolovaného prostoru zabezpečení s částečnou důvěryhodností, která je omezena na výchozí sadu oprávnění zóny CAS**Pro Internet.** To efektivně izoluje WPF hostované aplikace z klientského počítače stejným způsobem, že byste očekávali typické webové aplikace, které mají být izolovány. XBAP může zvýšit oprávnění až na plnou důvěryhodnost v závislosti na zóně zabezpečení adresy URL nasazení a konfiguraci zabezpečení klienta. Další informace naleznete v tématu [WPF Partial Trust Security](wpf-partial-trust-security.md).  
  
 Toto téma popisuje model zabezpečení pro samostatné aplikace WPF (Windows Presentation Foundation) a aplikace hostované v prohlížeči.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Bezpečná navigace](#SafeTopLevelNavigation)  
  
- [Nastavení zabezpečení softwaru pro procházení webu](#InternetExplorerSecuritySettings)  
  
- [Ovládací prvky webového prohlížeče a ovládací prvky funkcí](#webbrowser_control_and_feature_controls)  
  
- [Zakázání sestavení APTCA pro částečně důvěryhodné klientské aplikace](#APTCA)  
  
- [Chování izolovaného prostoru pro volné soubory XAML](#LooseContentSandboxing)  
  
- [Prostředky pro vývoj wpf aplikací, které podporují zabezpečení](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>
## <a name="safe-navigation"></a>Bezpečná navigace  
 Pro XBAPs WPF rozlišuje dva typy navigace: aplikace a prohlížeč.  
  
 *Navigace v aplikaci* je navigace mezi položkami obsahu v rámci aplikace, která je hostována prohlížečem. *Navigace v prohlížeči* je navigace, která mění obsah a umístění URL prohlížeče samotného. Vztah mezi navigací aplikace (obvykle XAML) a navigací prohlížeče (obvykle HTML) je znázorněn na následujícím obrázku:
  
 ![Vztah mezi navigací aplikace a navigací prohlížeče.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 Typ obsahu, který je považován za bezpečný pro XBAP přejít na je primárně určena tím, zda se používá navigace aplikace nebo navigace v prohlížeči.  
  
<a name="Application_Navigation_Security"></a>
### <a name="application-navigation-security"></a>Zabezpečení navigace aplikací  
 Navigace aplikace je považována za bezpečnou, pokud ji lze identifikovat pomocí identifikátoru URI balíčku, který podporuje čtyři typy obsahu:  
  
|Typ obsahu|Popis|Příklad identifikátoru URI|  
|------------------|-----------------|-----------------|  
|Prostředek|Soubory, které jsou přidány do projektu s typem sestavení **zdroje**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Obsah|Soubory, které jsou přidány do projektu s typem sestavení **obsahu**.|`pack://application:,,,/MyContentFile.xaml`|  
|Místo původu|Soubory, které jsou přidány do projektu s typem sestavení **None**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Kód aplikace|Prostředky XAML, které mají zkompilovaný kód na pozadí.<br /><br /> -nebo-<br /><br /> Soubory XAML, které jsou přidány do projektu s typem sestavení **Page**.|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
> Další informace o datových souborech aplikací a identifikátorech URI balíčku naleznete v [tématu WPF Application Resource, Content a Data Files](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 Soubory těchto typů obsahu mohou být navigovány uživatelem nebo programově:  
  
- **Uživatelská navigace**. Uživatel přejde klepnutím <xref:System.Windows.Documents.Hyperlink> na prvek.  
  
- **Programová navigace**. Aplikace přejde bez zapojení uživatele, například nastavením vlastnosti. <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
<a name="Browser_Navigation_Security"></a>
### <a name="browser-navigation-security"></a>Zabezpečení navigace v prohlížeči  
 Navigace v prohlížeči je považována za bezpečnou pouze za následujících podmínek:  
  
- **Uživatelská navigace**. Uživatel přejde klepnutím <xref:System.Windows.Documents.Hyperlink> na prvek, který <xref:System.Windows.Navigation.NavigationWindow>je v rámci <xref:System.Windows.Controls.Frame>hlavní , není v nociované .  
  
- **Zóna**. Obsah, na který se přecvádíte, je umístěn v Síti Internet nebo v místním intranetu.  
  
- **protokolu**. Používaný protokol je **http**, **https**, **file**nebo **mailto**.  
  
 Pokud XBAP pokusí přejít na obsah způsobem, který není v <xref:System.Security.SecurityException> souladu s těmito podmínkami, je vyvolána.  
  
<a name="InternetExplorerSecuritySettings"></a>
## <a name="web-browsing-software-security-settings"></a>Nastavení zabezpečení softwaru pro procházení webu  
 Nastavení zabezpečení v počítači určuje přístup k udělení jakéhokoli softwaru pro procházení webu. Software pro procházení webu zahrnuje všechny aplikace nebo součásti, které používají [rozhraní API WinINet](/windows/win32/wininet/portal) nebo [UrlMon,](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767916(v=vs.85)) včetně aplikací Internet Explorer a PresentationHost.exe.  
  
 Aplikace Internet Explorer poskytuje mechanismus, pomocí kterého můžete konfigurovat funkce, které mohou být prováděny aplikací Internet Explorer nebo z ní, včetně následujících funkcí:  
  
- Součásti závislé na rozhraní .NET Framework  
  
- Ovládací prvky ActiveX a moduly plug-in  
  
- Soubory ke stažení  
  
- Skriptování  
  
- Ověřování uživatelů  
  
 Kolekce funkcí, které lze zabezpečit tímto způsobem, je konfigurována pro zóny **Internet**, **Intranet**, **Důvěryhodné servery**a **Servery s omezeným přístupem.** Následující kroky popisují konfiguraci nastavení zabezpečení:  
  
1. Otevřete **Ovládací panely**.  
  
2. Klepněte na **položku Síť a Internet** a potom na **položku Možnosti Internetu**.  
  
     Zobrazí se dialogové okno Možnosti Internetu.  
  
3. Na kartě **Zabezpečení** vyberte zónu, pro kterou chcete konfigurovat nastavení zabezpečení.  
  
4. Klikněte na tlačítko **Vlastní úroveň.**  
  
     Zobrazí se dialogové okno **Nastavení zabezpečení** a můžete nakonfigurovat nastavení zabezpečení pro vybranou zónu.  
  
     ![Snímek obrazovky s dialogovým oknem Nastavení zabezpečení](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> K dialogovému oknu Možnosti Internetu se můžete také dostat z aplikace Internet Explorer. Klepněte na **položku Nástroje** a potom na **položku Možnosti Internetu**.  
  
 Počínaje aplikací Windows Internet Explorer 7 jsou zahrnuta následující nastavení zabezpečení speciálně pro rozhraní .NET Framework:  
  
- **Uvolněné XAML**. Určuje, zda může aplikace [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] Internet Explorer přejít na soubory a uvolnit je. (Možnosti Povolit, Zakázat a Zobrazit).  
  
- **Aplikace prohlížeče XAML**. Určuje, zda může aplikace Internet Explorer přejít na xbaps a spustit jej. (Možnosti Povolit, Zakázat a Zobrazit).  
  
 Ve výchozím nastavení jsou všechna tato nastavení povolena pro zóny **Internet**, **Místní intranet**a **Důvěryhodné servery** a pro zónu **Servery s omezeným přístupem** jsou zakázána.  
  
<a name="Security_Settings_for_IE6_and_Below"></a>
### <a name="security-related-wpf-registry-settings"></a>Nastavení registru WPF související se zabezpečením  
 Kromě nastavení zabezpečení, které jsou k dispozici prostřednictvím možností Internetu, jsou k dispozici následující hodnoty registru pro selektivní blokování řady funkcí WPF citlivých na zabezpečení. Hodnoty jsou definovány pod následujícím klíčem:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 V následující tabulce jsou uvedeny hodnoty, které lze nastavit.  
  
|Název hodnoty|Typ hodnoty|Data hodnoty|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|1 zakázat; 0 povolit.|  
|LooseXamlDisallow|REG_DWORD|1 zakázat; 0 povolit.|  
|WebBrowserDisallow|REG_DWORD|1 zakázat; 0 povolit.|  
|MediaAudioDisallow|REG_DWORD|1 zakázat; 0 povolit.|  
|MediaImageDisallow|REG_DWORD|1 zakázat; 0 povolit.|  
|MediaVideoDisallow|REG_DWORD|1 zakázat; 0 povolit.|  
|SkriptInteropDisallow|REG_DWORD|1 zakázat; 0 povolit.|  
  
<a name="webbrowser_control_and_feature_controls"></a>
## <a name="webbrowser-control-and-feature-controls"></a>Ovládací prvky webového prohlížeče a ovládací prvky funkcí  
 Ovládací prvek <xref:System.Windows.Controls.WebBrowser> WPF lze použít k hostování webového obsahu. Ovládací prvek <xref:System.Windows.Controls.WebBrowser> WPF zabalí základní ovládací prvek ActiveX webového prohlížeče. WPF poskytuje určitou podporu pro zabezpečení aplikace <xref:System.Windows.Controls.WebBrowser> při použití ovládacího prvku WPF k hostování nedůvěryhodného webového obsahu. Některé funkce zabezpečení však musí být použity přímo aplikacemi používajícími <xref:System.Windows.Controls.WebBrowser> ovládací prvek. Další informace o ovládacím prvku ActiveX webového prohlížeče naleznete v tématu [Přehledy ovládacích prvku webprohlížeče a výukové programy](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752041(v=vs.85)).  
  
> [!NOTE]
> Tato část se vztahuje <xref:System.Windows.Controls.Frame> také na <xref:System.Windows.Controls.WebBrowser> ovládací prvek, protože používá k přechodu na obsah HTML.  
  
 Pokud wpf <xref:System.Windows.Controls.WebBrowser> ovládací prvek se používá k hostování nedůvěryhodného webového obsahu, aplikace by měla použít částečné důvěryhodnosti <xref:System.AppDomain> pomoci izolovat kód aplikace z potenciálně škodlivého kódu skriptu HTML. To platí zejména v případě, že vaše aplikace interaguje s hostovaným skriptem <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> pomocí metody a vlastnosti. <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> Další informace naleznete [v tématu Přehled doplňků WPF](./app-development/wpf-add-ins-overview.md).  
  
 Pokud vaše aplikace používá <xref:System.Windows.Controls.WebBrowser> ovládací prvek WPF, dalším způsobem, jak zvýšit zabezpečení a zmírnit útoky, je povolení ovládacích prvků funkcí aplikace Internet Explorer. Ovládací prvky funkcí jsou dodatky aplikace Internet Explorer, které umožňují správcům a vývojářům konfigurovat funkce <xref:System.Windows.Controls.WebBrowser> aplikace Internet Explorer a aplikací, které jsou hostiteli ovládacího prvku ActiveX webového prohlížeče, který ovládací prvek WPF zabalí. Ovládací prvky funkcí lze konfigurovat pomocí funkce [CoInternetSetFeatureEnabled](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537168(v=vs.85)) nebo změnou hodnot v registru. Další informace o ovládacích prvcích funkcí naleznete [v tématu Úvod do ovládacích prvků funkcí](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537184(v=vs.85)) a [ovládacích prvků funkcí Internetu](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/general-info/ee330720(v=vs.85)).  
  
 Pokud vyvíjíte samostatnou aplikaci WPF, <xref:System.Windows.Controls.WebBrowser> která používá ovládací prvek WPF, WPF automaticky povolí následující ovládací prvky funkcí pro vaši aplikaci.  
  
|Ovládací prvek funkcí|  
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
  
 Vzhledem k tomu, že tyto ovládací prvky funkcí jsou povoleny bezpodmínečně, může být jejich plná důvěryhodnost narušena. V tomto případě, pokud neexistuje žádné bezpečnostní riziko pro konkrétní aplikaci a obsah, který je hostitelem, odpovídající funkce ovládacíprvek může být zakázán.  
  
 Ovládací prvky funkcí jsou použity procesem, který instancije objekt ActiveX webového prohlížeče. Proto pokud vytváříte samostatnou aplikaci, která může přejít na nedůvěryhodný obsah, měli byste vážně zvážit povolení dalších ovládacích prvků funkcí.  
  
> [!NOTE]
> Toto doporučení je založeno na obecných doporučeních pro zabezpečení hostitele MSHTML a SHDOCVW. Další informace naleznete [v nejčastějších dotazech k zabezpečení hostitele MSHTML: Část I II](https://msrc-blog.microsoft.com/2009/04/02/the-mshtml-host-security-faq-part-i-of-ii/) a [Nejčastější dotazy k zabezpečení hostitele MSHTML: Část II iI](https://msrc-blog.microsoft.com/2009/04/03/the-mshtml-host-security-faq-part-ii-of-ii/).  
  
 Pro spustitelný soubor zvažte povolení následujících ovládacích prvků funkcí nastavením hodnoty registru na hodnotu 1.  
  
|Ovládací prvek funkcí|  
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
  
 Pro spustitelný soubor zvažte zakázání následující ho ovládacího prvku funkce nastavením hodnoty registru na hodnotu 0.  
  
|Ovládací prvek funkcí|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Pokud spustíte aplikaci prohlížeče XAML s částečnou důvěryhodností, <xref:System.Windows.Controls.WebBrowser> která obsahuje ovládací prvek WPF v aplikaci Windows Internet Explorer, wpf hostuje ovládací prvek ActiveX webového prohlížeče v adresním prostoru procesu aplikace Internet Explorer. Vzhledem k tomu, že ovládací prvek ActiveX webového prohlížeče je hostován v procesu aplikace Internet Explorer, jsou pro ovládací prvek ActiveX webového prohlížeče povoleny také všechny ovládací prvky funkcí pro aplikaci Internet Explorer.  
  
 XBAPs spuštěné v aplikaci Internet Explorer také získat další úroveň zabezpečení ve srovnání s běžnými samostatnými aplikacemi. Toto dodatečné zabezpečení je způsobeno tím, že aplikace Internet Explorer, a tedy ovládací prvek ActiveX webového prohlížeče, je ve výchozím nastavení spuštěna v chráněném režimu v systémech Windows Vista a Windows 7. Další informace o chráněném režimu naleznete [v tématu Principy a práce v chráněném režimu aplikace Internet Explorer](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/).  
  
> [!NOTE]
> Pokud se pokusíte spustit XBAP, <xref:System.Windows.Controls.WebBrowser> který obsahuje ovládací prvek WPF <xref:System.Security.SecurityException> ve Firefoxu, zatímco v zóně Internet, bude vyvolána. To je způsobeno zásadou zabezpečení WPF.  
  
<a name="APTCA"></a>
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Zakázání sestavení APTCA pro částečně důvěryhodné klientské aplikace  
 Pokud jsou spravovaná sestavení nainstalována do globální mezipaměti sestavení (GAC), stanou se plně důvěryhodnými, protože uživatel musí poskytnout výslovné oprávnění k jejich instalaci. Vzhledem k tomu, že jsou plně důvěryhodné, mohou je používat pouze plně důvěryhodné spravované klientské aplikace. Chcete-li povolit částečně důvěryhodné aplikace používat, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> musí být označeny (APTCA). Tímto atributem by měla být označena pouze sestavení, která byla testována jako bezpečná pro spuštění v částečném vztahu důvěryhodnosti.  
  
 Je však možné, aby sestavení APTCA vykazovalo chybu zabezpečení po instalaci do GAC . Jakmile je zjištěna chyba zabezpečení, vydavatelé sestavení mohou vytvořit aktualizaci zabezpečení, která problém vyřeší na existujících instalacích a že se ochrání před instalacemi, ke kterým může dojít po zjištění problému. Jednou z možností aktualizace je odinstalovat sestavení, i když to může přerušit jiné plně důvěryhodné klientské aplikace, které používají sestavení.  
  
 WPF poskytuje mechanismus, kterým lze sestavení APTCA zakázat pro částečně důvěryhodné XBAPs bez odinstalace sestavení APTCA.  
  
 Chcete-li zakázat sestavení APTCA, musíte vytvořit speciální klíč registru:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Následující příklad ukazuje:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Tento klíč vytvoří položku pro sestavení APTCA. Musíte také vytvořit hodnotu v tomto klíči, který umožňuje nebo zakáže sestavení. Níže jsou uvedeny podrobnosti o hodnotě:  
  
- Název hodnoty: **APTCA_FLAG**.  
  
- Typ hodnoty: **REG_DWORD**.  
  
- Data hodnoty: **1** zakázat; **0** povolit.  
  
 Pokud sestavení má být zakázáno pro částečně důvěryhodné klientské aplikace, můžete napsat aktualizaci, která vytvoří klíč registru a hodnotu.  
  
> [!NOTE]
> Sestavení rozhraní Core .NET Framework nejsou tímto způsobem ovlivněna jejich zakázáním, protože jsou vyžadována pro schované aplikace ke spuštění. Podpora pro zakázání sestavení APTCA je primárně určena pro aplikace třetích stran.  
  
<a name="LooseContentSandboxing"></a>
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Chování izolovaného prostoru pro volné soubory XAML  
 Volné [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory jsou pouze značky XAML soubory, které nezávisí na žádné kód na pozadí, obslužné rutiny události nebo sestavení specifické pro aplikaci. Pokud [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jsou volné soubory navigovány přímo z prohlížeče, jsou načteny do izolovaného prostoru zabezpečení na základě výchozí sady oprávnění zóny Internet.  
  
 Chování zabezpečení se však [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] liší při volné soubory <xref:System.Windows.Navigation.NavigationWindow> jsou <xref:System.Windows.Controls.Frame> navigovány z nebo v samostatné aplikaci.  
  
 V obou případech [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] volný soubor, který je navigován dědí oprávnění jeho hostitelské aplikace. Toto chování však může být nežádoucí z hlediska [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zabezpečení, zejména v případě, že volný soubor byl vytvořen entitou, která není důvěryhodný nebo neznámý. Tento typ obsahu se označuje jako <xref:System.Windows.Controls.Frame> externí <xref:System.Windows.Navigation.NavigationWindow> *obsah*a lze jej nakonfigurovat tak, aby byl při přechodu na něj izolován. Izolace je dosaženo nastavením **SandboxExternalContent** vlastnost true, jak <xref:System.Windows.Controls.Frame> je <xref:System.Windows.Navigation.NavigationWindow>znázorněno v následujících příkladech pro a :  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 S tímto nastavením bude externí obsah načten do procesu, který je oddělený od procesu, který je hostitelem aplikace. Tento proces je omezen na výchozí sadu oprávnění zóny Internet, která jej účinně izoluje od hostitelské aplikace a klientského počítače.  
  
> [!NOTE]
> I když navigace [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] na volné <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame> soubory z a nebo v samostatné aplikaci je implementována na základě wpf prohlížeče hosting infrastruktury, zahrnující Proces PresentationHost, úroveň zabezpečení je o něco menší, než když je obsah načten přímo v aplikaci Internet Explorer na Windows Vista a Windows 7 (což by ještě být přes PresentationHost). Důvodem je, že samostatná aplikace WPF používající webový prohlížeč neposkytuje další funkci zabezpečení chráněného režimu aplikace Internet Explorer.  
  
<a name="BestPractices"></a>
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Prostředky pro vývoj wpf aplikací, které podporují zabezpečení  
 Následují některé další zdroje informací, které pomáhají vyvíjet aplikace WPF, které podporují zabezpečení:  
  
|Oblast|Prostředek|  
|----------|--------------|  
|Spravovaný kód|[Vzory a postupy bezpečnostní pokyny pro aplikace](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))|  
|CAS|[Zabezpečení přístupu kódu](../misc/code-access-security.md)|  
|ClickOnce|[ClickOnce Zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)|  
|WPF|[WPF částečné zabezpečení důvěryhodnosti](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Viz také

- [WPF částečné zabezpečení důvěryhodnosti](wpf-partial-trust-security.md)
- [Strategie zabezpečení WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)
- [Strategie zabezpečení WPF – engineering zabezpečení](wpf-security-strategy-security-engineering.md)
- [Vzory a postupy bezpečnostní pokyny pro aplikace](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))
- [Zabezpečení přístupu kódu](../misc/code-access-security.md)
- [ClickOnce Zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
- [Přehled XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
