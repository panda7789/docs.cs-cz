---
title: Nasazení aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 54d14503a0f65bb50f2dfb14d40af3b47d51589c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186315"
---
# <a name="deploy-a-wpf-application"></a>Nasazení aplikace WPF

Po spuštění aplikací Windows Presentation Foundation (WPF) je třeba je nasadit. Systém Windows a rozhraní .NET Framework zahrnují několik technologií nasazení. Technologie nasazení, která se používá k nasazení aplikace WPF, závisí na typu aplikace. Toto téma obsahuje stručný přehled jednotlivých technologií nasazení a způsob jejich použití ve spojení s požadavky na nasazení každého typu aplikace WPF.

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a>Technologie nasazení  
 Systém Windows a rozhraní .NET Framework zahrnují několik technologií nasazení, včetně:  
  
- Nasazení XCopy.  
  
- Nasazení Instalační služby systému Windows.  
  
- ClickOnce nasazení.  
  
<a name="XCopy_Deployment"></a>
### <a name="xcopy-deployment"></a>Nasazení XCopy  
 Nasazení XCopy označuje použití programu příkazového řádku XCopy ke kopírování souborů z jednoho umístění do druhého. Nasazení XCopy je vhodné za následujících okolností:  
  
- Aplikace je samostatná. Není nutné aktualizovat klienta ke spuštění.  
  
- Soubory aplikací musí být přesunuty z jednoho umístění do jiného, například z umístění sestavení (místní disk, sdílená složka UNC a tak dále) do umístění publikování (web, sdílená složka UNC a tak dále).  
  
- Aplikace nevyžaduje integraci prostředí (zástupce nabídky Start, ikona na ploše a tak dále).  
  
 Přestože XCopy je vhodný pro jednoduché scénáře nasazení, je omezena, pokud jsou požadovány složitější možnosti nasazení. Zejména pomocí XCopy často vznikne režie pro vytváření, provádění a údržbu skriptů pro správu nasazení robustním způsobem. Kromě toho XCopy nepodporuje správu verzí, odinstalace nebo vrácení zpět.  
  
<a name="Windows_Installer"></a>
### <a name="windows-installer"></a>Instalační služba systému Windows  
 Instalační služba systému Windows umožňuje sbalit aplikace jako samostatné spustitelné soubory, které lze snadno distribuovat klientům a spouštět je. Instalační služba systému Windows je navíc nainstalována se systémem Windows a umožňuje integraci s plochou, nabídkou Start a ovládacím panelem Programy.  
  
 Instalační služba systému Windows zjednodušuje instalaci a odinstalaci aplikací, ale neposkytuje zařízení pro zajištění toho, aby nainstalované aplikace byly z hlediska správy verzí udržovány v aktuálním stavu.  
  
 Další informace o Instalační službě systému Windows naleznete v tématu [Nasazení Instalační služby systému Windows](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a>Nasazení clickonce  
 ClickOnce umožňuje nasazení aplikací ve webovém stylu pro jiné než webové aplikace. Aplikace jsou publikovány a nasazeny z webových nebo souborových serverů. Přestože ClickOnce nepodporuje celou řadu klientských funkcí, které aplikace nainstalované instalačníslužbou systému Windows, podporují podmnožinu, která obsahuje následující:  
  
- Integrace s nabídkou Start a ovládacím panelem Programy.  
  
- Správa verzí, vrácení zpět a odinstalace.  
  
- Režim instalace online, který vždy spustí aplikaci z umístění nasazení.  
  
- Automatické aktualizace při vydání nových verzí.  
  
- Registrace přípon souborů.  
  
 Další informace o clickonce naleznete v [tématu ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a>Nasazení aplikací WPF  
 Možnosti nasazení pro aplikaci WPF závisí na typu aplikace. Z hlediska nasazení wpf má tři významné typy aplikací:  
  
- Samostatné aplikace.  
  
- Aplikace pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro značky.  
  
- Aplikace prohlížeče XAML (XBAPs).  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a>Nasazení samostatných aplikací  
 Samostatné aplikace se nasazují pomocí ClickOnce nebo Instalační služby systému Windows. V obou směrech vyžadují samostatné aplikace ke spuštění úplnou důvěryhodnost. Úplný vztah důvěryhodnosti je automaticky udělen samostatným aplikacím, které jsou nasazeny pomocí Instalační služby systému Windows. Samostatné aplikace, které jsou nasazeny pomocí ClickOnce nejsou automaticky udělena úplná důvěryhodnost. Místo toho ClickOnce zobrazí dialogové okno upozornění zabezpečení, které uživatelé musí přijmout před instalací samostatné aplikace. Pokud je přijata, samostatná aplikace je nainstalována a udělena úplná důvěryhodnost. Pokud tomu tak není, není nainstalována samostatná aplikace.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a>Nasazení aplikací XAML pouze pro značky  
 Stránky pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro označení jsou obvykle publikovány na webových serverech, jako jsou stránky HTML, a lze je zobrazit pomocí aplikace Internet Explorer. Stránky pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro značky jsou spuštěny v izolovaném prostoru zabezpečení s částečnou důvěryhodností s omezeními, která jsou definována sadou oprávnění zóny Internet. To poskytuje ekvivalentní izolovaného prostoru zabezpečení webových aplikací založených na html.  
  
 Další informace o zabezpečení aplikací WPF naleznete v [tématu Zabezpečení](../security-wpf.md).  
  
 Stránky pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro označení lze nainstalovat do místního systému souborů pomocí xcopy nebo Instalační služby systému Windows. Tyto stránky lze zobrazit pomocí aplikace Internet Explorer nebo Průzkumníka Windows.  
  
 Další informace o XAML naleznete v tématu [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a>Nasazení aplikací prohlížeče XAML  
 XBAPs jsou kompilované aplikace, které vyžadují nasazení následujících tří souborů:  
  
- *ApplicationName*.exe: Soubor aplikace spustitelného sestavení.  
  
- *ApplicationName*.xbap: Manifest nasazení.  
  
- *ApplicationName*.exe.manifest: Manifest aplikace.  
  
> [!NOTE]
> Další informace o nasazení a manifesty aplikací naleznete [v tématu vytváření wpf aplikace](building-a-wpf-application-wpf.md).  
  
 Tyto soubory jsou vytvářeny při xbap je sestaven. Další informace naleznete v [tématu How to: Create a New WPF Browser Application Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Podobně jako stránky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pouze se značkami jsou xbaps obvykle publikovány na webovém serveru a zobrazeny pomocí aplikace Internet Explorer.  
  
 XBAPs lze nasadit do klientů pomocí některé ho nasazení techniky. ClickOnce se však doporučuje, protože poskytuje následující funkce:  
  
1. Automatické aktualizace při publikování nové verze.  
  
2. Oprávnění ke zvýšení oprávnění pro XBAP spuštěná s úplným vztahem důvěryhodnosti.  
  
 Ve výchozím nastavení ClickOnce publikuje soubory aplikace s příponou .deploy. To může být problematické, ale může být zakázáno. Další informace naleznete [v tématu Problémy s konfigurací serveru a klienta v tématu ClickOnce Deployments](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Další informace o nasazení aplikací prohlížeče XAML (XBAPs) naleznete v [tématu Přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a>Instalace rozhraní .NET Framework  
 Chcete-li spustit aplikaci WPF, musí být v klientovi nainstalována architektura Microsoft .NET Framework. Aplikace Internet Explorer automaticky zjistí, zda jsou klienti nainstalováni pomocí rozhraní .NET Framework při prohlížení aplikací hostovaných v prohlížeči WPF. Pokud rozhraní .NET Framework není nainstalováno, aplikace Internet Explorer vyzve uživatele k jeho instalaci.  
  
 Chcete-li zjistit, zda je nainstalována rozhraní .NET Framework, obsahuje aplikace Internet Explorer zaváděcí aplikaci, která je registrována jako záložní obslužná rutina víceúčelových rozšíření Internet Mail Extensions (MIME) pro soubory obsahu s následujícími rozšířeními: .xaml, XPS, .xbap a .application. Pokud přejdete na tyto typy souborů a rozhraní .NET Framework není v klientovi nainstalováno, aplikace zaváděcího nástroje požádá o oprávnění k jeho instalaci. Pokud oprávnění není k dispozici, není nainstalována rozhraní .NET Framework ani aplikace.  
  
 Pokud je oprávnění uděleno, aplikace Internet Explorer stáhne a nainstaluje rozhraní .NET Framework pomocí služby INTELIGENTNÍ PŘENOS NA POZADÍ společnosti Microsoft (BITS). Po úspěšné instalaci rozhraní .NET Framework je původně požadovaný soubor otevřen v novém okně prohlížeče.  
  
 Další informace naleznete [v tématu Nasazení rozhraní .NET Framework a aplikací](../../deployment/index.md).  
  
## <a name="see-also"></a>Viz také

- [Sestavení aplikace WPF](building-a-wpf-application-wpf.md)
- [Zabezpečení](../security-wpf.md)
