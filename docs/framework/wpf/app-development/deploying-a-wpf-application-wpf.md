---
title: Nasazení aplikace WPF (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 2079d4b4f6bedcc30c4826f8798729c5c9263751
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648092"
---
# <a name="deploying-a-wpf-application-wpf"></a>Nasazení aplikace WPF (WPF)
Po aplikace Windows Presentation Foundation (WPF) se vytvářejí, musí být nasazeny. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a rozhraní .NET Framework zahrnují několik technologie nasazení. Technologie nasazení, která se používá k nasazení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace závisí na typu aplikace. Toto téma nabízí stručný přehled této technologie každého nasazení, a jak se používají ve spojení s požadavky na nasazení každého [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] typu aplikace.  
  
   
<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Technologie nasazení  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a rozhraní .NET Framework zahrnují několik nasazení technologií, včetně:  
  
-   Nasazení XCopy.  
  
-   [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] nasazení.  
  
-   [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] nasazení.  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>Nasazení XCopy  
 Nasazení XCopy odkazuje na použití příkazu XCopy příkazového řádku programu ke kopírování souborů z jednoho umístění do druhého. Nasazení XCopy je vhodný v následujících případech:  
  
-   Je samostatná aplikace. Nemusí se k aktualizaci klienta ke spuštění.  
  
-   Soubory aplikace musí přesunout z jednoho umístění do druhého, například z umístění sestavení (místního disku, [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] sdílené složky a tak dále) do umístění pro publikování (webové stránky, [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] sdílené složky a tak dále).  
  
-   Aplikace nevyžaduje, aby prostředí integrace (zástupce v nabídce Start, ikony na ploše a tak dále).  
  
 I když je vhodné pro scénáře nasazení jednoduchého příkazu XCopy, je omezen při složitější možnosti nasazení jsou požadovány. Zejména pomocí příkazu XCopy často zahrnuje režii při vytváření, provádění a údržbě skriptů pro správu nasazení tak robustní. Kromě toho XCopy nepodporuje správu verzí, odinstalace nebo vrácení zpět.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Instalační služba systému Windows  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] umožňuje aplikacím, aby se zabalil jako samostatné spustitelné soubory, které můžete snadno distribuovat do klientů a spustit. Kromě toho [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] se instaluje s [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a umožňuje integraci s plochou, v nabídce Start a programy v Ovládacích panelech.  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] zjednodušuje instalace a odinstalace aplikací, ale neposkytuje funkce pro zajištění, že jsou pořád aktuální z hlediska správy verzí nainstalovaných aplikací.  
  
 Další informace o [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)], naleznete v tématu [nasazení Instalační služby systému Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce – nasazení  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] umožňuje nasazení webových aplikací pro jiné webové aplikace. Aplikace jsou publikovaná a nasadit z webu nebo serverů. I když [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] nepodporuje celý rozsah klientské funkce, které [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]-nainstalované aplikace, podporuje podmnožinu, která obsahuje následující:  
  
-   Integrace se v nabídce Start a programy v Ovládacích panelech.  
  
-   Správa verzí, vrácení zpět a odinstalaci.  
  
-   Online instalace režim, ve kterém vždy spustí aplikaci z umístění nasazení.  
  
-   Automatické aktualizace, pokud se vydávají nové verze.  
  
-   Registrace přípon souborů.  
  
 Další informace o [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], naleznete v tématu [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>Nasazení aplikací WPF  
 O možnostech nasazení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace závisí na typu aplikace. Z hlediska nasazení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] má tři typy významných aplikací:  
  
-   Samostatné aplikace.  
  
-   Pouze značky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikací.  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Nasazení samostatné aplikace  
 Samostatné aplikace jsou nasazeny pomocí buď [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] nebo [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. V obou případech samostatné aplikace vyžadují úplný vztah důvěryhodnosti ke spuštění. Úplný vztah důvěryhodnosti je automaticky udělena pro samostatné aplikace, které jsou nasazeny pomocí [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Samostatné aplikace, které jsou nasazeny pomocí [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] nejsou automaticky udělena úplná důvěryhodnost. Místo toho [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] zobrazí dialogové okno s upozorněním, že uživatelé musí přijmout před instalací je samostatná aplikace zabezpečení. Pokud přijat, samostatné aplikace je nainstalovaná a udělena úplná důvěryhodnost. Pokud ne, není nainstalovaná samostatné aplikace.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Nasazení aplikací pouze značky XAML  
 Pouze značky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky jsou obvykle publikované na webové servery, jako je třeba [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] stránky a lze ji zobrazit pomocí [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]. Pouze značky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky spustit v sandboxu částečným vztahem důvěryhodnosti zabezpečení s nakonfigurovanými omezeními, které jsou definovány sada oprávnění Internetu zóny. To poskytuje ekvivalentní karanténě k [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]– na základě webové aplikace.  
  
 Další informace o zabezpečení pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] naleznete v tématu [zabezpečení](../../../../docs/framework/wpf/security-wpf.md).  
  
 Pouze značky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky lze nainstalovat do místního systému souborů pomocí obou příkazu XCopy nebo [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Tyto stránky lze zobrazit pomocí [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] nebo Průzkumníka Windows.  
  
 Další informace o XAML najdete v tématu [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>Nasazení aplikace prohlížeče XAML  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] jsou kompilované aplikace, které vyžadují následující tři soubory k nasazení:  
  
-   *ApplicationName*.exe: Sestavení spustitelný soubor aplikace.  
  
-   *ApplicationName*.xbap: Manifest nasazení.  
  
-   *ApplicationName*.exe.manifest: Manifest aplikace.  
  
> [!NOTE]
>  Další informace o manifesty nasazení a aplikace, najdete v části [sestavení aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
 Tyto soubory jsou vytvářeny při [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je vytvořená. Další informace najdete v tématu [jak: Vytvoření nového projektu aplikace prohlížeče WPF](https://msdn.microsoft.com/library/72ef4d90-e163-42a1-8df0-ea7ccfd1901f). Například pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] jsou obvykle vydávané na webový server a prohlížet pomocí [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)].  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] je možné nasadit na klienty některou z metod nasazení. Nicméně [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] je doporučeno, protože poskytuje následující možnosti:  
  
1.  Automatické aktualizace, když se publikuje novou verzi.  
  
2.  Zvýšení úrovně oprávnění pro [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] s úplným vztahem důvěryhodnosti.  
  
 ClickOnce publikuje ve výchozím nastavení aplikace soubory s příponu .deploy odstraní. To může být problematické, ale je možné zakázat. Další informace najdete v tématu [serveru a problémy s konfigurací klienta v nasazeních ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Další informace o nasazení [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], naleznete v tématu [přehled aplikací prohlížeče WPF XAML](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>Instalace rozhraní .NET Framework  
 Ke spuštění [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, musí být na klientovi nainstalované rozhraní Microsoft .NET Framework. [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] automaticky zjišťuje, zda klienti jsou instalováni pomocí rozhraní .NET Framework při [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se při zobrazení aplikace hostované prohlížečem. Pokud není nainstalované rozhraní .NET Framework, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] vyzve uživatele k jeho instalaci.  
  
 Chcete-li zjistit, jestli je nainstalované rozhraní .NET Framework, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] zahrnuje aplikaci zaváděcí nástroj, který je registrovaný jako na náhradní řešení [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] obslužné rutiny souborů obsahu s těmito příponami: .xaml, XPS, .xbap a .application. Pokud přejdete na tyto typy souborů a na klientovi není nainstalované rozhraní .NET Framework, zaváděcí nástroj aplikace požádá o oprávnění k jeho instalaci. Pokud není k dispozici oprávnění, se nainstaluje rozhraní .NET Framework ani aplikace.  
  
 Pokud je povoleno, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] stáhne a nainstaluje s použitím rozhraní .NET Framework [!INCLUDE[TLA#tla_bits](../../../../includes/tlasharptla-bits-md.md)]. Po úspěšné instalaci rozhraní .NET Framework je původně požadované soubor otevřít v novém okně prohlížeče.  
  
 Automatické zjišťování rozhraní .NET framework je k dispozici na [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)], a [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] klienti, kteří mají [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] nebo novější.  
  
 Další informace najdete v tématu [nasazení rozhraní .NET Framework a aplikace](../../../../docs/framework/deployment/index.md).  
  
## <a name="see-also"></a>Viz také:
- [Sestavení aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [Zabezpečení](../../../../docs/framework/wpf/security-wpf.md)
