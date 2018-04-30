---
title: Nasazení aplikace WPF (WPF)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bf38c4b15f59ca90d00f8f6b365a3233ee3516bb
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="deploying-a-wpf-application-wpf"></a>Nasazení aplikace WPF (WPF)
Po aplikace Windows Presentation Foundation (WPF) jsou vytvářeny, které potřebují k nasazení. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a rozhraní .NET Framework zahrnují několik technologií nasazení. Nasazení technologie, která se používá k nasazení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace závisí na typu aplikace. Toto téma obsahuje stručný přehled technologie každé nasazení a jak se používají ve spojení s požadavky na nasazení jednotlivých [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] typ aplikace.  
  
   
<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Technologie nasazení  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a rozhraní .NET Framework zahrnují několik technologií nasazení, včetně:  
  
-   XCopy nasazení.  
  
-   [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] nasazení.  
  
-   [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] nasazení.  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>XCopy nasazení  
 XCopy nasazení odkazuje na použití příkazového řádku programu XCopy kopírovat soubory z jednoho umístění do druhého. XCopy nasazení je vhodné v následujících případech:  
  
-   Aplikace je úplný a samostatný. Nemusí se k aktualizaci klienta ke spuštění.  
  
-   Soubory aplikace je třeba přesunout z jednoho umístění do druhého, například z umístění sestavení (místní disk, [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] sdílené složky a tak dále) do umístění pro publikování (webu, [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] sdílené složky a tak dále).  
  
-   Aplikace nevyžaduje integrace prostředí (z nabídky Start, ikony na ploše a tak dále).  
  
 I když XCopy je vhodná pro scénáře jednoduché nasazení, je omezen Pokud složitější možnosti nasazení je potřeba. Konkrétně často pomocí příkazu XCopy náročnější, pro vytváření, spouštění a údržbě skriptů pro správu nasazení robustní způsobem. Kromě toho XCopy nepodporuje správu verzí, odinstalace nebo vrácení změn.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Instalační služba systému Windows  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] umožňuje aplikacím zabalené jako samostatná spustitelné soubory, které lze snadno distribuovaná klientům a spustit. Kromě toho [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] se instaluje s [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a umožňuje integraci s plochy, nabídky Start a programy v Ovládacích panelech.  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] zjednodušuje instalace a odinstalace aplikací, ale neposkytuje zařízení k zajištění, že nainstalovaných aplikací, budou kopírovány z hlediska správy verzí.  
  
 Další informace o [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)], najdete v části [nasazení Instalační služby systému Windows](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce – nasazení  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] umožňuje nasazení stylu webové aplikace pro jiné webové aplikace. Aplikace se publikována a nasazené z webového nebo souborových serverů. I když [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] nepodporuje celý rozsah klientské funkce, které [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]-udělat nainstalovaných aplikací, podporuje podmnožinu, která zahrnuje následující:  
  
-   Integrace s nabídky Start a programy v Ovládacích panelech.  
  
-   Správa verzí, vrácení zpět a odinstalaci.  
  
-   Online režimu, který vždy spouští aplikace z nasazení umístění instalace.  
  
-   Automatické aktualizace, když jsou vydávány nové verze.  
  
-   Registrace přípon souborů.  
  
 Další informace o [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], najdete v části [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>Nasazení aplikací WPF  
 Možnosti nasazení pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace závisí na typu aplikace. Z hlediska nasazení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] má tři typy významné aplikací:  
  
-   Samostatné aplikace.  
  
-   Pouze značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikace.  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Nasazení samostatné aplikace  
 Samostatné aplikace jsou nasazeny pomocí buď [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] nebo [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. V obou případech samostatné aplikace vyžadují úplný vztah důvěryhodnosti ke spuštění. Úplný vztah důvěryhodnosti je automaticky uděleno samostatné aplikace, které jsou nasazeny pomocí [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Samostatné aplikace, které jsou nasazeny pomocí [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] nejsou automaticky udělí úplný vztah důvěryhodnosti. Místo toho [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] zobrazí dialogové okno upozornění, které uživatelé musí přijmout před instalací je samostatná aplikace zabezpečení. Pokud přijata, je samostatná aplikace nainstalována a udělit úplný vztah důvěryhodnosti. Pokud ne, není nainstalovaná samostatné aplikace.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Nasazení aplikací pouze kód XAML  
 Pouze značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky jsou obvykle publikované na webové servery, jako je třeba [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] stránky a lze ji zobrazit pomocí [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]. Pouze značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky spuštěny v rámci izolovaného prostoru částečným vztahem důvěryhodnosti zabezpečení, omezení, které jsou definované sadě oprávnění zónu Internetu. To poskytuje ekvivalentní zabezpečení izolovaného prostoru pro [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]– na základě webové aplikace.  
  
 Další informace o zabezpečení pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, najdete v části [zabezpečení](../../../../docs/framework/wpf/security-wpf.md).  
  
 Pouze značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky lze nainstalovat do místního systému souborů pomocí buď XCopy nebo [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Tyto stránky lze zobrazit pomocí [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] nebo v Průzkumníku Windows.  
  
 Další informace o XAML najdete v tématu [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>Nasazení aplikace prohlížeče XAML  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] jsou kompilované aplikace, které vyžadují následující tři soubory k nasazení:  
  
-   *ApplicationName*.exe: souboru spustitelný soubor sestavení aplikace.  
  
-   *ApplicationName*.xbap: manifest nasazení.  
  
-   *ApplicationName*. exe.manifest: manifest aplikace.  
  
> [!NOTE]
>  Další informace o nasazení a aplikací manifesty, najdete v části [vytváření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
 Tyto soubory se vytváří při [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je sestaven. Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace prohlížeče WPF](http://msdn.microsoft.com/library/72ef4d90-e163-42a1-8df0-ea7ccfd1901f). Jako jen značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] jsou obvykle publikovat na webový server a zobrazit pomocí [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)].  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] můžete nasadit na klienty, kteří používají některé techniky nasazení. Ale [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] se doporučuje, protože poskytuje následující možnosti:  
  
1.  Automatické aktualizace, když je vydána nová verze.  
  
2.  Zvýšení oprávnění pro [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] s úplným vztahem důvěryhodnosti.  
  
 ClickOnce publikuje ve výchozím nastavení aplikace soubory s příponou .deploy. To může být problematické, ale je možné zakázat. Další informace najdete v tématu [Server a problémy s konfigurací klienta v nasazeních ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Další informace o nasazení [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], najdete v části [přehled aplikace prohlížeče XAML WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>Instalace rozhraní .NET Framework  
 Ke spuštění [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, musí být na klientovi nainstalované rozhraní Microsoft .NET Framework. [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] automaticky zjišťuje, zda klienti jsou instalováni pomocí rozhraní .NET Framework při [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jsou vnímány – aplikace hostované prohlížečem. Pokud není nainstalované rozhraní .NET Framework, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] vyzve uživatele k jeho instalaci.  
  
 Chcete-li zjistit, zda je nainstalována rozhraní .NET Framework, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] zahrnuje zaváděcího nástroje aplikace, která je registrována jako záložní [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] obslužnou rutinu pro soubory obsahu s těmito příponami: XAML, XPS, .xbap a .application. Pokud přejdete na tyto typy souborů a na klientovi není nainstalované rozhraní .NET Framework, aplikace zaváděcího nástroje požádá o oprávnění k její instalaci. Pokud není k dispozici oprávnění, je nainstalované rozhraní .NET Framework ani aplikace.  
  
 Pokud je povoleno, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] stáhne a nainstaluje s použitím rozhraní .NET Framework [!INCLUDE[TLA#tla_bits](../../../../includes/tlasharptla-bits-md.md)]. Po úspěšné instalaci rozhraní .NET Framework je původně požadovaný soubor otevřít v novém okně prohlížeče.  
  
 Automatické zjišťování rozhraní .NET framework je k dispozici na [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)], a [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] klienti, kteří mají [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] nainstalovaný nebo novější.  
  
 Další informace najdete v tématu [nasazení rozhraní .NET Framework a aplikace](../../../../docs/framework/deployment/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Sestavení aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Zabezpečení](../../../../docs/framework/wpf/security-wpf.md)
