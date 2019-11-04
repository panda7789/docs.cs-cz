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
ms.openlocfilehash: 908c3fb0baacc7fd75dae875e9a9d49a08fe5401
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459723"
---
# <a name="security-wpf"></a>Zabezpečení (WPF)
<a name="introduction"></a>Při vývoji samostatné aplikace a aplikací hostovaných v prohlížeči Windows Presentation Foundation (WPF), je nutné vzít v úvahu model zabezpečení. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] samostatné aplikace jsou spouštěny s neomezenými oprávněními (sada oprávnění CAS**FullTrust** ), ať už nasazené pomocí Instalační služba systému Windows (. msi), XCOPY nebo ClickOnce. Nasazení částečného vztahu důvěryhodnosti – samostatné aplikace WPF pomocí technologie ClickOnce nejsou podporovány. Hostitelská aplikace s plnou důvěryhodností však může vytvořit <xref:System.AppDomain> s částečným vztahem důvěryhodnosti pomocí modelu .NET Framework doplňku. Další informace najdete v tématu [Přehled doplňků WPF](./app-development/wpf-add-ins-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace hostované v prohlížeči jsou hostovány aplikací Windows Internet Explorer nebo Firefox a může se jednat buď o aplikace prohlížeče XAML (XBAP), nebo volné [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] dokumenty. Další informace najdete v tématu [Přehled aplikací WPF XAML browser](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace hostované v prohlížeči se spouštějí v izolovaném prostoru zabezpečení s částečnou důvěryhodností, což je ve výchozím nastavení omezeno na výchozí sadu oprávnění pro**internetovou** zónu CAS. Tato možnost efektivně izoluje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace hostované v prohlížeči z klientského počítače stejným způsobem, jako byste očekávali izolaci typických webových aplikací. XBAP může zvýšit oprávnění, až na úplný vztah důvěryhodnosti, v závislosti na zóně zabezpečení adresy URL nasazení a konfiguraci zabezpečení klienta. Další informace najdete v tématu [zabezpečení částečné důvěryhodnosti WPF](wpf-partial-trust-security.md).  
  
 Toto téma popisuje model zabezpečení pro samostatnou aplikaci Windows Presentation Foundation (WPF) a aplikace hostované v prohlížeči.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Bezpečná navigace](#SafeTopLevelNavigation)  
  
- [Webové procházení – nastavení zabezpečení softwaru](#InternetExplorerSecuritySettings)  
  
- [Ovládací prvek WebBrowser a ovládací prvky funkcí](#webbrowser_control_and_feature_controls)  
  
- [Zakázání sestavení APTCA pro částečně důvěryhodné klientské aplikace](#APTCA)  
  
- [Chování izolovaného prostoru pro volné soubory XAML](#LooseContentSandboxing)  
  
- [Prostředky pro vývoj aplikací WPF, které podporují zabezpečení](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Bezpečná navigace  
 Pro XBAP [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] rozlišuje dva typy navigace: aplikace a prohlížeč.  
  
 *Navigace v aplikaci* je navigace mezi položkami obsahu v rámci aplikace, jejímž hostitelem je prohlížeč. *Navigace v prohlížeči* je navigace, která mění obsah a adresu URL umístění samotného prohlížeče. Vztah mezi navigací aplikace (obvykle XAML) a navigace v prohlížeči (obvykle HTML) je znázorněna na následujícím obrázku:
  
 ![Vztah mezi navigací navigace v aplikaci a prohlížečem.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 Typ obsahu, který je považován za bezpečný pro aplikaci XBAP na navigaci, je primárně určen, zda je použita navigace aplikace nebo navigace v prohlížeči.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Zabezpečení navigace v aplikaci  
 Navigace aplikace se považuje za bezpečnou, pokud ji můžete identifikovat pomocí identifikátoru URI balíčku, který podporuje čtyři typy obsahu:  
  
|Typ obsahu|Popis|Příklad identifikátoru URI|  
|------------------|-----------------|-----------------|  
|Partner|Soubory, které jsou přidány do projektu s typem sestavení **prostředek**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Obsah|Soubory, které jsou přidány do projektu s typem sestavení **Content**.|`pack://application:,,,/MyContentFile.xaml`|  
|Původní lokalita|Soubory, které jsou přidány do projektu s typem sestavení **none**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Kód aplikace|Prostředky XAML, které mají zkompilovaný kód na pozadí.<br /><br /> -nebo-<br /><br /> Soubory XAML, které jsou přidány do projektu s typem sestavení **Page**.|`pack://application:,,,/MyResourceFile``.xaml`|  
  
> [!NOTE]
> Další informace o datových souborech aplikace a identifikátorech URI balíčku naleznete v tématu [prostředky aplikace WPF, obsah a datové soubory](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 Na soubory těchto typů obsahu se dá přejít buď uživatelem, nebo programově:  
  
- **Navigace uživatele**. Uživatel přejde kliknutím na <xref:System.Windows.Documents.Hyperlink> element.  
  
- **Programová navigace**. Aplikace naviguje bez zahrnutí uživatele, například nastavením vlastnosti <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Zabezpečení navigace v prohlížeči  
 Navigace v prohlížeči se považuje za bezpečnou jenom za těchto podmínek:  
  
- **Navigace uživatele**. Uživatel přejde kliknutím na <xref:System.Windows.Documents.Hyperlink> element, který je v rámci hlavní <xref:System.Windows.Navigation.NavigationWindow>, nikoli ve vnořeném <xref:System.Windows.Controls.Frame>.  
  
- **Zóna**. Obsah, na který se přechází, se nachází na internetu nebo v místním intranetu.  
  
- **Protokol**. Použitý protokol je buď **http**, **https**, **File**, nebo **mailto**.  
  
 Pokud se XBAP pokusí přejít k obsahu způsobem, který nedodržuje tyto podmínky, je vyvolána <xref:System.Security.SecurityException>.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Webové procházení – nastavení zabezpečení softwaru  
 Nastavení zabezpečení v počítači určuje přístup k vašemu softwaru pro procházení webu. Software pro procházení webu zahrnuje všechny aplikace nebo komponenty, které používají rozhraní [WinInet](https://go.microsoft.com/fwlink/?LinkId=179379) nebo [Urlmon](https://go.microsoft.com/fwlink/?LinkId=179383) API, včetně aplikací Internet Explorer a PresentationHost. exe.  
  
 Internet Explorer poskytuje mechanismus, pomocí kterého můžete nakonfigurovat funkce, které mohou být spuštěny nástrojem nebo z aplikace Internet Explorer, včetně následujících:  
  
- Závislé součásti .NET Framework  
  
- Ovládací prvky ActiveX a moduly plug-in  
  
- Soubory ke stažení  
  
- Skriptování  
  
- Ověřování uživatelů  
  
 Shromažďování funkcí, které je možné zabezpečit tímto způsobem, je konfigurováno pro zóny pro **Internet**, **intranet**, **Důvěryhodné servery**a **servery s omezeným přístupem** v závislosti na zóně. Následující postup popisuje, jak nakonfigurovat nastavení zabezpečení:  
  
1. Otevřete **Ovládací panely**.  
  
2. Klikněte na **síť a Internet** a pak klikněte na **Možnosti Internetu**.  
  
     Zobrazí se dialogové okno Možnosti Internetu.  
  
3. Na kartě **zabezpečení** vyberte zónu, pro kterou chcete nakonfigurovat nastavení zabezpečení.  
  
4. Klikněte na tlačítko **vlastní úroveň** .  
  
     Zobrazí se dialogové okno **nastavení zabezpečení** , ve kterém můžete nakonfigurovat nastavení zabezpečení pro vybranou zónu.  
  
     ![Snímek obrazovky, který zobrazuje dialogové okno nastavení zabezpečení.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> K dialogovému oknu Možnosti Internetu se můžete dostat taky z Internet Exploreru. Klikněte na **nástroje** a pak na **Možnosti Internetu**.  
  
 Od aplikace Windows Internet Explorer 7 jsou zahrnuta následující nastavení zabezpečení konkrétně pro .NET Framework:  
  
- **Volný kód XAML**. Určuje, zda aplikace Internet Explorer může přejít na soubory [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] a volně k nim. (Možnost povolit, zakázat a zobrazit výzvu).  
  
- **Aplikace prohlížeče XAML**. Určuje, jestli Internet Explorer může přejít na a spustit XBAP. (Možnost povolit, zakázat a zobrazit výzvu).  
  
 Ve výchozím nastavení jsou tato nastavení povolená pro zóny **Internet**, **místní intranet**a **Důvěryhodné servery** a jsou zakázané pro zónu **lokalit s omezeným přístupem** .  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>Nastavení registru WPF souvisejících se zabezpečením  
 Kromě nastavení zabezpečení dostupného prostřednictvím možností Internetu jsou k dispozici následující hodnoty registru pro selektivní blokování množství funkcí WPF citlivých na zabezpečení. Hodnoty jsou definovány v následujícím klíči:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 V následující tabulce jsou uvedeny hodnoty, které lze nastavit.  
  
|Název hodnoty|Typ hodnoty|Data hodnoty|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|1 pro zákaz; 0 pro povolení.|  
|LooseXamlDisallow|REG_DWORD|1 pro zákaz; 0 pro povolení.|  
|WebBrowserDisallow|REG_DWORD|1 pro zákaz; 0 pro povolení.|  
|MediaAudioDisallow|REG_DWORD|1 pro zákaz; 0 pro povolení.|  
|MediaImageDisallow|REG_DWORD|1 pro zákaz; 0 pro povolení.|  
|MediaVideoDisallow|REG_DWORD|1 pro zákaz; 0 pro povolení.|  
|ScriptInteropDisallow|REG_DWORD|1 pro zákaz; 0 pro povolení.|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## <a name="webbrowser-control-and-feature-controls"></a>Ovládací prvek WebBrowser a ovládací prvky funkcí  
 Pro hostování webového obsahu lze použít ovládací prvek WPF <xref:System.Windows.Controls.WebBrowser>. Ovládací prvek WPF <xref:System.Windows.Controls.WebBrowser> obtéká základní ovládací prvek ActiveX WebBrowser. WPF poskytuje určitou podporu pro zabezpečení vaší aplikace při použití ovládacího prvku WPF <xref:System.Windows.Controls.WebBrowser> k hostování nedůvěryhodného webového obsahu. Některé funkce zabezpečení však musí použít přímo aplikace pomocí ovládacího prvku <xref:System.Windows.Controls.WebBrowser>. Další informace o ovládacím prvku ActiveX WebBrowser najdete v tématu [přehledy a kurzy ovládacích prvků WebBrowser](https://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
> Tato část platí také pro ovládací prvek <xref:System.Windows.Controls.Frame>, protože používá <xref:System.Windows.Controls.WebBrowser> k přechodu na obsah HTML.  
  
 Pokud se <xref:System.Windows.Controls.WebBrowser> ovládací prvek WPF používá k hostování nedůvěryhodného webového obsahu, měla by vaše aplikace používat <xref:System.AppDomain> s částečným vztahem důvěryhodnosti k lepšímu izolování kódu aplikace před potenciálně škodlivým kódem skriptu HTML. To platí zejména v případě, že vaše aplikace pracuje s hostovaným skriptem pomocí metody <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> a vlastnosti <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A>. Další informace najdete v tématu [Přehled doplňků WPF](./app-development/wpf-add-ins-overview.md).  
  
 Pokud vaše aplikace používá ovládací prvek WPF <xref:System.Windows.Controls.WebBrowser>, další způsob, jak zvýšit zabezpečení a zmírnit útoky, je povolit ovládací prvky funkce Internet Exploreru. Ovládací prvky funkcí jsou přidání do Internet Exploreru, které správcům a vývojářům umožňují konfigurovat funkce aplikace Internet Explorer a aplikací, které jsou hostiteli ovládacího prvku WebBrowser ActiveX, který <xref:System.Windows.Controls.WebBrowser> ovládací prvek WPF. Ovládací prvky funkcí lze konfigurovat pomocí funkce [CoInternetSetFeatureEnabled](https://go.microsoft.com/fwlink/?LinkId=179394) nebo změnou hodnot v registru. Další informace o ovládacích prvcích funkcí naleznete v tématu [Úvod do ovládacích prvků funkcí](https://go.microsoft.com/fwlink/?LinkId=179390) a [Internet Feature Controls](https://go.microsoft.com/fwlink/?LinkId=179392).  
  
 Pokud vyvíjíte samostatnou aplikaci WPF, která používá ovládací prvek WPF <xref:System.Windows.Controls.WebBrowser>, WPF automaticky povolí následující ovládací prvky funkce pro vaši aplikaci.  
  
|Řízení funkcí|  
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
  
 Vzhledem k tomu, že jsou tyto ovládací prvky funkcí povoleny nepodmíněně, mohou být aplikace s plnou důvěryhodností vůči nim postiženy. V takovém případě, pokud neexistuje žádné bezpečnostní riziko pro konkrétní aplikaci a obsah, který je hostitelem, lze odpovídající ovládací prvek funkce zakázat.  
  
 Ovládací prvky funkcí jsou aplikovány procesem vytvoření instance objektu ActiveX WebBrowser. Proto pokud vytváříte samostatnou aplikaci, která může přejít na nedůvěryhodný obsah, měli byste zvážit možnost povolit další ovládací prvky funkcí.  
  
> [!NOTE]
> Toto doporučení je založené na obecných doporučeních pro zabezpečení hostitelů MSHTML a SHDOCVW. Další informace najdete v tématu [Nejčastější dotazy k zabezpečení hostitele MSHTML: část i části II](https://go.microsoft.com/fwlink/?LinkId=179396) a [Nejčastější dotazy k zabezpečení hostitele MSHTML: část II z části II](https://go.microsoft.com/fwlink/?LinkId=179415).  
  
 Pro váš spustitelný soubor zvažte povolení následujících ovládacích prvků funkce nastavením hodnoty registru na 1.  
  
|Řízení funkcí|  
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
  
 Pro váš spustitelný soubor zvažte zakázání následujícího ovládacího prvku funkce nastavením hodnoty registru na hodnotu 0.  
  
|Řízení funkcí|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Pokud spustíte aplikaci prohlížeče XAML s částečným vztahem důvěryhodnosti (XBAP), která obsahuje ovládací prvek WPF <xref:System.Windows.Controls.WebBrowser> v aplikaci Windows Internet Explorer, WPF hostuje ovládací prvek ActiveX WebBrowser v adresním prostoru procesu aplikace Internet Explorer. Vzhledem k tomu, že ovládací prvek ActiveX WebBrowser je hostován v procesu Internet Exploreru, jsou všechny ovládací prvky funkcí pro Internet Explorer povoleny také pro ovládací prvek ActiveX WebBrowser.  
  
 Aplikace XBAP spuštěné v aplikaci Internet Explorer také dostanou další úroveň zabezpečení ve srovnání se standardními samostatnými aplikacemi. Toto dodatečné zabezpečení je způsobeno tím, že aplikace Internet Explorer, a proto ovládací prvek ActiveX WebBrowser, běží v chráněném režimu ve výchozím nastavení v [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] a [!INCLUDE[win7](../../../includes/win7-md.md)]. Další informace o chráněném režimu najdete v tématu [porozumění a práce v chráněném režimu Internet Explorer](https://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
> Pokud se pokusíte spustit XBAP, který obsahuje ovládací prvek WPF <xref:System.Windows.Controls.WebBrowser> v prohlížeči Firefox, zatímco v zóně Internet, bude vyvolána <xref:System.Security.SecurityException>. Důvodem je zásada zabezpečení WPF.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Zakázání sestavení APTCA pro částečně důvěryhodné klientské aplikace  
 Když jsou spravovaná sestavení nainstalována do globální mezipaměti sestavení (GAC), stanou se plně důvěryhodná, protože uživatel musí poskytnout explicitní oprávnění k jejich instalaci. Vzhledem k tomu, že jsou plně důvěryhodné, můžou je používat jenom plně důvěryhodní klientské aplikace. Aby je bylo možné použít částečně důvěryhodné aplikace, musí být označeny pomocí <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Pouze sestavení, která byla testována jako bezpečná pro spuštění v částečném vztahu důvěryhodnosti, by měla být označena tímto atributem.  
  
 Nicméně je možné, že sestavení APTCA vykazuje chybu zabezpečení po instalaci do GAC. Po zjištění chyby zabezpečení mohou vydavatelé sestavení vytvořit aktualizaci zabezpečení, která vyřeší problém s existujícími instalacemi, a chránit před instalacemi, které mohou nastat po zjištění problému. Jednou z možností aktualizace je odinstalování sestavení, i když by mohlo dojít k přerušení jiných plně důvěryhodných klientských aplikací, které používají sestavení.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] poskytuje mechanismus, pomocí kterého je možné zakázat sestavení APTCA pro částečně důvěryhodná aplikace XBAP bez odinstalování sestavení APTCA.  
  
 Chcete-li zakázat sestavení APTCA, je nutné vytvořit speciální klíč registru:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Příklad ukazuje následující:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Tento klíč vytvoří položku pro sestavení APTCA. Také je nutné v tomto klíči vytvořit hodnotu, která povolí nebo zakáže sestavení. Níže jsou uvedeny podrobnosti o hodnotě:  
  
- Název hodnoty: **APTCA_FLAG**.  
  
- Typ hodnoty: **REG_DWORD**.  
  
- Data hodnoty: **1** pro zakázání; **0** pro povolení.  
  
 Pokud je nutné pro částečně důvěryhodné klientské aplikace zakázat sestavení, můžete napsat aktualizaci, která vytvoří klíč registru a hodnotu.  
  
> [!NOTE]
> Základní .NET Framework sestavení nejsou ovlivněna tímto způsobem, protože jsou vyžadovány ke spuštění spravovaných aplikací. Podpora pro zakázání sestavení APTCA je primárně zaměřená na aplikace třetích stran.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Chování izolovaného prostoru pro volné soubory XAML  
 Volné [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory jsou soubory XAML pouze s označením, které nezávisí na žádném kódu na pozadí, obslužné rutině události nebo sestavení specifické pro aplikaci. Když jsou volné [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory přešly přímo z prohlížeče, načtou se v izolovaném prostoru zabezpečení na základě výchozí sady oprávnění zóny Internet.  
  
 Chování zabezpečení se však liší v případě, že jsou volné [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory přesunuty z <xref:System.Windows.Navigation.NavigationWindow> nebo <xref:System.Windows.Controls.Frame> v samostatné aplikaci.  
  
 V obou případech se volný [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubor, na který se přechází, zdědí oprávnění jeho hostitelské aplikace. Toto chování může být však nežádoucí z hlediska zabezpečení, zejména v případě, že volný [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubor byl vytvořen entitou, která je buď nedůvěryhodná, nebo neznámá. Tento typ obsahu se označuje jako *externí obsah*a <xref:System.Windows.Controls.Frame> i <xref:System.Windows.Navigation.NavigationWindow> můžete nakonfigurovat tak, aby se při přechodu na něj izolují. Izolaci je dosaženo nastavením vlastnosti **vlastnost SandboxExternalContent** na hodnotu true, jak je znázorněno v následujících příkladech <xref:System.Windows.Controls.Frame> a <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Pomocí tohoto nastavení se externí obsah načte do procesu, který je oddělený od procesu, který hostuje aplikaci. Tento proces je omezený na výchozí sadu oprávnění internetové zóny a efektivně izoluje z hostující aplikace a klientského počítače.  
  
> [!NOTE]
> I když je navigace na volné [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubory z <xref:System.Windows.Navigation.NavigationWindow> nebo <xref:System.Windows.Controls.Frame> v samostatné aplikaci implementována na základě infrastruktury hostování prohlížeče WPF, která zahrnuje proces PresentationHost, je úroveň zabezpečení poněkud menší než při obsah je načten přímo v aplikaci Internet Explorer na [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] a [!INCLUDE[win7](../../../includes/win7-md.md)] (který by byl stále PresentationHost). Je to proto, že samostatná aplikace WPF používající webový prohlížeč neposkytuje další funkci zabezpečení chráněného režimu v aplikaci Internet Explorer.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Prostředky pro vývoj aplikací WPF, které podporují zabezpečení  
 Níže jsou uvedené další materiály, které vám pomohou vyvíjet [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace, které podporují zabezpečení:  
  
|Oblast|Partner|  
|----------|--------------|  
|Spravovaný kód|[Postupy zabezpečení pro aplikace a vzory a postupy](https://go.microsoft.com/fwlink/?LinkId=117426)|  
|CAS|[Zabezpečení přístupu kódu](../misc/code-access-security.md)|  
|ClickOnce|[ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[Částečné zabezpečení důvěryhodnosti WPF](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Viz také:

- [Částečné zabezpečení důvěryhodnosti WPF](wpf-partial-trust-security.md)
- [Strategie zabezpečení WPF – zabezpečení platformy](wpf-security-strategy-platform-security.md)
- [Strategie zabezpečení WPF – engineering zabezpečení](wpf-security-strategy-security-engineering.md)
- [Postupy zabezpečení pro aplikace a vzory a postupy](https://go.microsoft.com/fwlink/?LinkId=117426)
- [Zabezpečení přístupu kódu](../misc/code-access-security.md)
- [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
- [Přehled XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
