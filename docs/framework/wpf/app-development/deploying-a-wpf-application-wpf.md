---
title: Nasazení aplikace WPF (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: daa69997f70c22a97482fd7e63d42506e7051732
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291296"
---
# <a name="deploying-a-wpf-application-wpf"></a>Nasazení aplikace WPF (WPF)
Po sestavení aplikací Windows Presentation Foundation (WPF) je nutné je nasadit. Windows a .NET Framework zahrnují několik technologií nasazení. Technologie nasazení, která se používá k nasazení aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], závisí na typu aplikace. Toto téma poskytuje stručný přehled každé technologie nasazení a způsobu jejich použití ve spojení s požadavky na nasazení každého typu aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Technologie nasazení  
 Windows a .NET Framework zahrnují několik technologií nasazení, včetně:  
  
- Nasazení XCopy.  
  
- nasazení [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)].  
  
- Nasazení ClickOnce.  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>Nasazení XCopy  
 XCopy nasazování odkazuje na použití programu příkazového řádku XCopy ke kopírování souborů z jednoho umístění do druhého. Nasazení XCopy je vhodné za následujících okolností:  
  
- Aplikace je samostatná. Není nutné aktualizovat klienta, aby běžel.  
  
- Soubory aplikace musí být přesunuty z jednoho umístění do druhého, například z umístění sestavení (místní disk, sdílená složka UNC atd.) do umístění pro publikování (web, sdílená složka UNC atd.).  
  
- Aplikace nevyžaduje integraci prostředí (zástupce v nabídce Start, ikona pracovní plochy atd.).  
  
 I když je příkaz XCopy vhodný pro jednoduché scénáře nasazení, je omezen, pokud jsou požadovány složitější možnosti nasazení. Konkrétně použití příkazu XCopy často vystává režii při vytváření, spouštění a údržbě skriptů pro správu nasazení robustním způsobem. Kromě toho XCopy nepodporuje správu verzí, odinstalaci ani vrácení změn.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Instalační služba systému Windows  
 @no__t – 0 umožňuje zabalit aplikace jako samostatné spustitelné soubory, které je možné snadno distribuovat klientům a spustit. Kromě toho je [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] nainstalovaný se systémem Windows a umožňuje integraci s plochou, nabídkou Start a ovládacími panely programu.  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] zjednodušuje instalaci a odinstalaci aplikací, ale neposkytuje vybavení pro zajištění aktuálnosti nainstalovaných aplikací z hlediska správy verzí.  
  
 Další informace o Instalační služba systému Windows najdete v tématu [nasazení Instalační služba systému Windows](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce – nasazení  
 ClickOnce umožňuje nasazení aplikace webového stylu pro jiné než webové aplikace. Aplikace se publikují na webové nebo souborové servery a nasazují se z nich. I když ClickOnce nepodporuje celou škálu funkcí klienta, které @no__t -0 aplikace, podporují podmnožinu, která zahrnuje následující:  
  
- Integrace pomocí nabídky Start a ovládacích panelů programy.  
  
- Správa verzí, vrácení zpět a odinstalace.  
  
- Online režim instalace, který vždy spustí aplikaci z umístění nasazení.  
  
- Automatické aktualizace při vydání nových verzí.  
  
- Registrace přípon souborů.  
  
 Další informace o ClickOnce najdete v tématu [zabezpečení a nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>Nasazení aplikací WPF  
 Možnosti nasazení aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] závisí na typu aplikace. Z perspektivy nasazení má [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tři významné typy aplikací:  
  
- Samostatné aplikace.  
  
- Pouze s označením aplikace [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
- [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Nasazení samostatných aplikací  
 Samostatné aplikace jsou nasazeny buď pomocí ClickOnce, nebo [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. V obou případech samostatné aplikace vyžadují úplný vztah důvěryhodnosti pro spuštění. Pro samostatné aplikace, které jsou nasazené pomocí [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)], se automaticky udělí úplný vztah důvěryhodnosti. Samostatným aplikacím, které jsou nasazeny pomocí technologie ClickOnce, se automaticky neudělí úplný vztah důvěryhodnosti. Místo toho ClickOnce zobrazí dialogové okno upozornění zabezpečení, které uživatelé musí přijmout před instalací samostatné aplikace. V případě přijetí se samostatná aplikace nainstaluje a udělí Plná důvěra. V takovém případě není samostatná aplikace nainstalována.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Nasazení aplikací XAML pouze s označením  
 Pouze označení @no__t – 0 stránky jsou obvykle publikovány na webové servery, jako jsou stránky HTML, a lze je zobrazit pomocí aplikace Internet Explorer. Pouze označení @no__t – 0 stránky spouštěné v izolovaném prostoru zabezpečení s částečnou důvěryhodností s omezeními, která jsou definována sadou oprávnění zóny Internet. To poskytuje ekvivalentní bezpečnostní izolovaný prostor (sandbox) pro webové aplikace založené na HTML.  
  
 Další informace o zabezpečení pro aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] najdete v tématu [zabezpečení](../security-wpf.md).  
  
 Pomocí příkazu XCopy nebo [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] lze do místního systému souborů nainstalovat pouze @no__t – 0 stránek. Tyto stránky lze zobrazit pomocí aplikace Internet Explorer nebo Průzkumníka Windows.  
  
 Další informace o XAML naleznete v tématu [XAML Overview (WPF)](../advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>Nasazení aplikací prohlížeče XAML  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] jsou kompilované aplikace, které vyžadují nasazení následujících tří souborů:  
  
- *ApplicationName*. exe: spustitelný soubor aplikace sestavení.  
  
- *ApplicationName*. XBAP: manifest nasazení.  
  
- *ApplicationName*. exe. manifest: manifest aplikace.  
  
> [!NOTE]
> Další informace o nasazení a manifestech aplikací naleznete v tématu [sestavování aplikace WPF](building-a-wpf-application-wpf.md).  
  
 Tyto soubory jsou vytvářeny, když je sestavena [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Další informace najdete v tématu [Postup: vytvoření nového projektu aplikace WPF Browser](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Například stránky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pouze s označením, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] jsou obvykle publikovány na webový server a zobrazovány pomocí aplikace Internet Explorer.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] lze nasadit do klientů pomocí kterékoli z technik nasazení. Technologie ClickOnce se však doporučuje, protože poskytuje následující možnosti:  
  
1. Automatické aktualizace, když je publikována nová verze.  
  
2. Oprávnění ke zvýšení oprávnění pro [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] běžící s úplným vztahem důvěryhodnosti.  
  
 Ve výchozím nastavení ClickOnce publikuje soubory aplikace s příponou. deploy. Může to být problematické, ale je možné ho zakázat. Další informace najdete v tématu [problémy s konfigurací serveru a klienta v nasazeních ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Další informace o nasazení [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] naleznete v tématu [Přehled aplikací WPF XAML browser](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>Instalace rozhraní .NET Framework  
 Chcete-li spustit aplikaci [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], musí být na klientovi nainstalována aplikace Microsoft .NET Framework. Internet Explorer automaticky zjišťuje, zda jsou klienti nainstalovány s .NET Framework při zobrazení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací hostovaných v prohlížeči. Pokud .NET Framework není nainstalován, aplikace Internet Explorer vyzve uživatele k jeho instalaci.  
  
 Aby bylo možné zjistit, zda .NET Framework nainstalováno, obsahuje aplikace Internet Explorer aplikaci zaváděcího nástroje, která je registrována jako záložní obslužná rutina MIME (Multipurpose Multipurpose Internet Mail Extensions) pro soubory obsahu s následujícími příponami:. XAML,. XPS,. XBAP. a. Application. Pokud přejdete na tyto typy souborů a .NET Framework není nainstalován v klientovi, aplikace zaváděcího nástroje požaduje oprávnění k její instalaci. Pokud není k dispozici oprávnění, .NET Framework ani aplikace nainstalována nejsou.  
  
 Pokud je udělené oprávnění, Internet Explorer stáhne a nainstaluje .NET Framework pomocí Microsoft Background Intelligent Transfer Service (BITS). Po úspěšné instalaci .NET Framework se původně požadovaný soubor otevře v novém okně prohlížeče.  
  
 Další informace najdete v tématu [nasazení .NET Framework a aplikací](../../deployment/index.md).  
  
## <a name="see-also"></a>Viz také:

- [Sestavení aplikace WPF](building-a-wpf-application-wpf.md)
- [Zabezpečení](../security-wpf.md)
