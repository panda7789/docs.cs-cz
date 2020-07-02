---
title: Nasazení aplikace
description: Prozkoumejte technologie nasazení, které Windows a .NET Framework použít pro aplikace Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 62904ccd47800c8340d68c223e50688902170063
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619296"
---
# <a name="deploy-a-wpf-application"></a>Nasazení aplikace WPF

Po sestavení aplikací Windows Presentation Foundation (WPF) je nutné je nasadit. Windows a .NET Framework zahrnují několik technologií nasazení. Technologie nasazení, která se používá k nasazení aplikace WPF, závisí na typu aplikace. Toto téma poskytuje stručný přehled každé technologie nasazení a způsobu jejich použití ve spojení s požadavky nasazení každého typu aplikace WPF.

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a>Technologie nasazení  
 Windows a .NET Framework zahrnují několik technologií nasazení, včetně:  
  
- Nasazení XCopy.  
  
- Nasazení Instalační služba systému Windows.  
  
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
 Instalační služba systému Windows umožňuje, aby se aplikace zabalí jako samostatné spustitelné soubory, které je možné snadno distribuovat klientům a spustit. Kromě toho je Instalační služba systému Windows nainstalován se systémem Windows a umožňuje integraci s plochou, v nabídce Start a na ovládacím panelu programy.  
  
 Instalační služba systému Windows zjednodušuje instalaci a odinstalaci aplikací, ale neposkytuje vybavení pro zajištění aktuálnosti nainstalovaných aplikací z hlediska správy verzí.  
  
 Další informace o Instalační služba systému Windows najdete v tématu [nasazení Instalační služba systému Windows](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a>ClickOnce – nasazení  
 ClickOnce umožňuje nasazení aplikace webového stylu pro jiné než webové aplikace. Aplikace se publikují na webové nebo souborové servery a nasazují se z nich. I když ClickOnce nepodporuje celou škálu funkcí klienta, které aplikace Instalační služba systému Windows instalovat, podporuje podmnožinu, která zahrnuje následující:  
  
- Integrace pomocí nabídky Start a ovládacích panelů programy.  
  
- Správa verzí, vrácení zpět a odinstalace.  
  
- Online režim instalace, který vždy spustí aplikaci z umístění nasazení.  
  
- Automatické aktualizace při vydání nových verzí.  
  
- Registrace přípon souborů.  
  
 Další informace o ClickOnce najdete v tématu [zabezpečení a nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a>Nasazení aplikací WPF  
 Možnosti nasazení pro aplikaci WPF závisí na typu aplikace. V perspektivě nasazení má WPF tři významné typy aplikací:  
  
- Samostatné aplikace.  
  
- Aplikace jenom s označením [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .  
  
- Aplikace prohlížeče XAML (XBAP)  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a>Nasazení samostatných aplikací  
 Samostatné aplikace jsou nasazeny buď pomocí ClickOnce, nebo Instalační služba systému Windows. V obou případech samostatné aplikace vyžadují úplný vztah důvěryhodnosti pro spuštění. K samostatným aplikacím, které jsou nasazeny pomocí Instalační služba systému Windows, se automaticky udělí úplný vztah důvěryhodnosti. Samostatným aplikacím, které jsou nasazeny pomocí technologie ClickOnce, se automaticky neudělí úplný vztah důvěryhodnosti. Místo toho ClickOnce zobrazí dialogové okno upozornění zabezpečení, které uživatelé musí přijmout před instalací samostatné aplikace. V případě přijetí se samostatná aplikace nainstaluje a udělí Plná důvěra. V takovém případě není samostatná aplikace nainstalována.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a>Nasazení aplikací XAML pouze s označením  
 Stránky pouze s označením [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou obvykle publikovány na webových serverech, jako jsou stránky HTML, a lze je zobrazit pomocí aplikace Internet Explorer. Stránky pouze s označením jsou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] spouštěny v izolovaném prostoru zabezpečení s částečnou důvěryhodností s omezeními, která jsou definována sadou oprávnění zóny Internetu. To poskytuje ekvivalentní bezpečnostní izolovaný prostor (sandbox) pro webové aplikace založené na HTML.  
  
 Další informace o zabezpečení pro aplikace WPF najdete v tématu [zabezpečení](../security-wpf.md).  
  
 Stránky pouze s označením [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lze nainstalovat do místního systému souborů pomocí příkazu xcopy nebo instalační služba systému Windows. Tyto stránky lze zobrazit pomocí aplikace Internet Explorer nebo Průzkumníka Windows.  
  
 Další informace o XAML naleznete v tématu [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a>Nasazení aplikací prohlížeče XAML  
 XBAP jsou zkompilované aplikace, které vyžadují nasazení následujících tří souborů:  
  
- *ApplicationName*. exe: spustitelný soubor aplikace sestavení.  
  
- *ApplicationName*. XBAP: manifest nasazení.  
  
- *ApplicationName*. exe. manifest: manifest aplikace.  
  
> [!NOTE]
> Další informace o nasazení a manifestech aplikací naleznete v tématu [sestavování aplikace WPF](building-a-wpf-application-wpf.md).  
  
 Tyto soubory jsou vytvářeny, když je vytvořena XBAP. Další informace najdete v tématu [Postup: vytvoření nového projektu aplikace WPF Browser](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Podobně jako stránky pouze s označením [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou aplikace XBAP obvykle publikovány na webovém serveru a zobrazovány pomocí aplikace Internet Explorer.  
  
 Aplikace XBAP lze nasadit do klientů pomocí kterékoli z technik nasazení. Technologie ClickOnce se však doporučuje, protože poskytuje následující možnosti:  
  
1. Automatické aktualizace, když je publikována nová verze.  
  
2. Oprávnění ke zvýšení oprávnění pro aplikaci XBAP běžící s úplným vztahem důvěryhodnosti.  
  
 Ve výchozím nastavení ClickOnce publikuje soubory aplikace s příponou. deploy. Může to být problematické, ale je možné ho zakázat. Další informace najdete v tématu [problémy s konfigurací serveru a klienta v nasazeních ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Další informace o nasazení aplikací prohlížeče XAML (XBAP) naleznete v tématu [Přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a>Instalace rozhraní .NET Framework  
 Chcete-li spustit aplikaci WPF, musí být na klientovi nainstalována aplikace Microsoft .NET Framework. Internet Explorer automaticky zjišťuje, zda jsou klienti nainstalovány s .NET Framework při zobrazení aplikací hostovaných v prohlížeči WPF. Pokud .NET Framework není nainstalován, aplikace Internet Explorer vyzve uživatele k jeho instalaci.  
  
 Aby bylo možné zjistit, zda .NET Framework nainstalováno, obsahuje aplikace Internet Explorer aplikaci zaváděcího nástroje, která je registrována jako záložní obslužná rutina MIME (Multipurpose Multipurpose Internet Mail Extensions) pro soubory obsahu s následujícími příponami:. XAML,. XPS,. XBAP a. Application. Pokud přejdete na tyto typy souborů a .NET Framework není nainstalován v klientovi, aplikace zaváděcího nástroje požaduje oprávnění k její instalaci. Pokud není k dispozici oprávnění, .NET Framework ani aplikace nainstalována nejsou.  
  
 Pokud je udělené oprávnění, Internet Explorer stáhne a nainstaluje .NET Framework pomocí Microsoft Background Intelligent Transfer Service (BITS). Po úspěšné instalaci .NET Framework se původně požadovaný soubor otevře v novém okně prohlížeče.  
  
 Další informace najdete v tématu [nasazení .NET Framework a aplikací](../../deployment/index.md).  
  
## <a name="see-also"></a>Viz také:

- [Sestavení aplikace WPF](building-a-wpf-application-wpf.md)
- [Zabezpečení](../security-wpf.md)
