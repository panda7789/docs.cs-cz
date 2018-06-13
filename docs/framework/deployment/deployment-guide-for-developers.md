---
title: Rozhraní .NET framework – Průvodce nasazením pro vývojáře
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14bb5cd242a45b98a23a9d807b22aa4487d2591e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392187"
---
# <a name="net-framework-deployment-guide-for-developers"></a>Rozhraní .NET framework – Průvodce nasazením pro vývojáře
Toto téma obsahuje informace pro vývojáře, kteří chtějí nainstalovat z rozhraní .NET Framework 4.5 na verzi rozhraní .NET Framework [!INCLUDE[net_current](../../../includes/net-current-version.md)] s svoje aplikace.

Odkazy na stažení, najdete v části [Distribuovatelné balíčky](#redistributable-packages). Jazykové sady a Distribuovatelné balíčky můžete také stáhnout z těchto stránkách Microsoft Download Center:

- Rozhraní .NET framework 4.7.2 pro všechny operační systémy ([instalačního programu webové](http://go.microsoft.com/fwlink/?LinkId=863262) nebo [offline instalačního programu](http://go.microsoft.com/fwlink/p/?LinkId=863265))

- Rozhraní .NET framework 4.7.1 pro všechny operační systémy ([instalačního programu webové](http://go.microsoft.com/fwlink/?LinkId=852095) nebo [offline instalačního programu](http://go.microsoft.com/fwlink/p/?LinkId=852107))

- 4.7 rozhraní .NET framework pro všechny operační systémy ([instalačního programu webové](http://go.microsoft.com/fwlink/?LinkId=825299) nebo [offline instalačního programu](http://go.microsoft.com/fwlink/p/?LinkId=825303))

- [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] pro všechny operační systémy ([instalačního programu webové](http://go.microsoft.com/fwlink/?LinkId=780597) nebo [offline instalačního programu](http://go.microsoft.com/fwlink/p/?LinkId=780601))

- [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] pro všechny operační systémy ([instalačního programu webové](http://go.microsoft.com/fwlink/?LinkId=671729) nebo [offline instalačního programu](http://go.microsoft.com/fwlink/p/?LinkId=671744))

- [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] pro všechny operační systémy ([instalačního programu webové](http://go.microsoft.com/fwlink/?LinkId=528222) nebo [offline instalačního programu](http://go.microsoft.com/fwlink/p/?LinkId=528232))

- Rozhraní .NET framework 4.5.2 pro všechny operační systémy ([instalačního programu webové](http://go.microsoft.com/fwlink/p/?LinkId=397703) nebo [offline instalačního programu](http://go.microsoft.com/fwlink/p/?LinkId=397706))

- Rozhraní .NET framework 4.5.1 pro všechny operační systémy ([instalačního programu webové](http://go.microsoft.com/fwlink/p/?LinkId=310158) nebo [offline instalačního programu](http://go.microsoft.com/fwlink/p/?LinkId=310159))

- [Rozhraní .NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)

 Důležité poznámky:

> [!NOTE]
> Fráze " [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho bod" odkazuje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a všechny novější verze.

- Verze rozhraní .NET Framework z [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] prostřednictvím [!INCLUDE[net_current](../../../includes/net-current-version.md)] jsou na místě aktualizace [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], což znamená, používají stejnou verzi modulu runtime, ale verze sestavení jsou aktualizovány a zahrnuje nové typy a členy.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho verze bodu jsou postupně na založený [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Při instalaci [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo jeho bod uvolní v systému, který má [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] nainstalovaná, verze 4 sestavení jsou nahrazena novější verze.

- Pokud je odkazováno na Microsoft [out-of-band balíček](http://msdn.microsoft.com/library/dn151288\(v=vs.110\).aspx) ve vaší aplikaci, bude sestavení součástí balíčku aplikace.

- Musí mít oprávnění správce k instalaci [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho bod.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Je součástí [!INCLUDE[win8](../../../includes/win8-md.md)] a [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], takže není nutné k nasazení s vaší aplikací na těchto operačních systémech. Podobně [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] je součástí [!INCLUDE[win81](../../../includes/win81-md.md)] a Windows Server 2012 R2. Rozhraní .NET Framework 4.5.2 není zahrnut ve všech operačních systémech. [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] Je součástí systému Windows 10 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] je součástí systému Windows 10 listopadu aktualizace a [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] je součástí systému Windows 10 Anniversary aktualizace.  4.7 rozhraní .NET Framework je součástí systému Windows 10 Creators aktualizace, rozhraní .NET Framework 4.7.1 je součástí systému Windows 10 patří Creators aktualizace a rozhraní .NET Framework 4.7.2 je součástí systému Windows 10. dubna 2018 aktualizovat. Úplný seznam požadavků na hardware a software najdete v tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).

- Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], můžete zobrazit seznam spuštěných aplikací rozhraní .NET Framework během instalace a zavřete je a snadno vaši uživatelé. To může pomoci zabránit restartu systému se nezdařila z důvodu instalace rozhraní .NET Framework. V tématu [omezení restartů systému](../../../docs/framework/deployment/reducing-system-restarts.md).

- Odinstalace [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo jeden z jeho bod uvolní také odebere existující [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] soubory. Pokud chcete přejít zpět do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], je nutné přeinstalovat a všechny aktualizace. (Viz [instalace rozhraní .NET Framework 4](http://msdn.microsoft.com/library/5a4x27ek\(v=vs.100\).aspx).)

- Rozhraní .NET Framework 4.5 redistributable byl aktualizován na 9. října 2012 opravit problém související s nesprávné časové razítko digitální certifikát, který chybu způsobil digitální podpis na soubory, které vytváří a podepsán společností Microsoft předčasně vyprší. Pokud jste dříve nainstalovali rozhraní .NET Framework 4.5 redistribuovatelný balíček s datem 16 srpen 2012, doporučujeme aktualizovat místní kopii s nejnovější distribuovatelné z [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=245484). Další informace o tomto problému najdete v tématu [2749655 informační zpravodaj zabezpečení společnosti Microsoft](http://technet.microsoft.com/security/advisory/2749655).

 Informace o správce systému nasazení rozhraní .NET Framework a jeho závislé součásti systému v síti najdete v tématu [Průvodce nasazením pro administrátory](../../../docs/framework/deployment/guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Možnosti nasazení pro vaši aplikaci.
 Až budete připraveni k publikování aplikace do webového serveru nebo jiných centralizovaném umístění tak, aby uživatelé ji můžou instalovat, můžete z několika metod nasazení. Některé z těchto nastavení najdete pomocí sady Visual Studio. Následující tabulka uvádí možnosti nasazení pro vaši aplikaci a určuje Distribuovatelný balíček .NET Framework, který podporuje jednotlivých možností. Kromě toho můžete napsat vlastní instalační program pro aplikaci; Další informace najdete v části [řetězení instalace rozhraní .NET Framework na instalaci aplikace na](#chaining).

|Strategie nasazení pro vaši aplikaci.|Dostupné metody nasazení|Rozhraní .NET framework redistributable používat|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Nainstalovat z webu|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Sadu nástrojů WiX toolset](#wix)<br />- [Ruční instalace](#installing_manually)|[Instalační program webové](#redistributable-packages)|
|Instalace z disku|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Sadu nástrojů WiX toolset](#wix)<br />- [Ruční instalace](#installing_manually)|[Offline instalační program](#redistributable-packages)|
|Instalaci z místní sítě (pro podnikové aplikace)|- [ClickOnce](#clickonce-deployment)|Buď [instalačního programu webové](#redistributable-packages) (viz [ClickOnce](#clickonce-deployment) pro omezení) nebo [offline instalačního programu](#redistributable-packages)|

## <a name="redistributable-packages"></a>Distribuovatelné balíčky
 Rozhraní .NET Framework je k dispozici ve dvou Distribuovatelné balíčky: webový instalační program (zaváděcího nástroje) a offline instalačního programu (samostatné redistributable). Následující tabulka porovnává dva balíčky.

||Instalační program webové|Offline instalační program|
|-|-------------------|-----------------------|
|Stažení souboru|Rozhraní .NET framework 4.7.2: <br/>[NDP472. KB4054531 Web.exe](http://go.microsoft.com/fwlink/?LinkId=863262)<br/><br/>Rozhraní .NET framework 4.7.1: <br/>[NDP471-KB4033344-Web.exe](http://go.microsoft.com/fwlink/?LinkId=852092)<br/><br/>Rozhraní .NET framework 4.7: <br />[NDP47-KB3186500-Web.exe](http://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151802-Web.exe](http://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]:<br />[NDP461-KB3102438-Web.exe](http://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]:<br />[NDP46-KB3045560-Web.exe](http://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> Rozhraní .NET framework 4.5.2: <br />[NDP452-KB2901954-Web.exe](http://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2859818-Web.exe](http://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_setup.exe](http://go.microsoft.com/fwlink/?LinkId=225704)|Rozhraní .NET framework 4.7.2: <br/>[NDP472-KB4054530-x86-x64-AllOS-enu.exe](http://go.microsoft.com/fwlink/?LinkId=863265)<br/><br/>Rozhraní .NET framework 4.7.1: <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />Rozhraní .NET framework 4.7: <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151800-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]: <br />[NDP461-KB3102436-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]: <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> Rozhraní .NET framework 4.5.2: <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_x86_x64.exe](http://go.microsoft.com/fwlink/?LinkId=225702)|
|Vyžaduje připojení k Internetu?|Ano|Ne|
|Velikost souborů ke stažení|Menší (zahrnuje instalační program pro cílovou platformu pouze) *|Větší *|
|Jazykové sady|Zahrnuté **|Musí být [nainstalovat samostatně](#chain_langpack), pokud nechcete použít balíček, který cílí všechny operační systémy|
|Metody nasazení|Podporuje všechny metody:<br /><br />- [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Instalační služba systému Windows XML (WiX)](#wix)<br />- [Ruční instalace](#installing_manually)<br />- [Vlastní instalace (řetězení)](#chaining)|Podporuje všechny metody:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Instalační služba systému Windows XML (WiX)](#wix)<br />- [Ruční instalace](#installing_manually)<br />- [Vlastní instalace (řetězení)](#chaining)|
|Umístění souborů ke stažení pro nasazení ClickOnce|Microsoft Download Center:<br /><br /> - [Rozhraní .NET framework 4.7.1](http://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [Rozhraní .NET framework 4.7](http://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [Rozhraní .NET framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780596)<br />- [Rozhraní .NET framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671728)<br />- [Rozhraní .NET framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528222)<br />- [Rozhraní .NET framework 4.5.2](http://go.microsoft.com/fwlink/?LinkId=397703)<br />- [Rozhraní .NET framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [Rozhraní .NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|Vlastní server nebo Microsoft Download Center:<br /><br /> - [Rozhraní .NET framework 4.7.1](http://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [Rozhraní .NET framework 4.7](http://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [Rozhraní .NET framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780600)<br />- [Rozhraní .NET framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671743)<br />- [Rozhraní .NET framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528232)<br />- [Rozhraní .NET framework 4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [Rozhraní .NET framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [Rozhraní .NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|

 \* Offline instalační program je větší, protože obsahuje součásti pro všechny cílové platformy. Po dokončení instalace operačního systému Windows, ukládá do mezipaměti pouze instalační program, který byl použit. Pokud offline instalačního programu se odstraní po instalaci, využití místa na disku je stejný, který používá webové instalační služby. Pokud používáte nástroj (například [InstallAware](#installaware-deployment) nebo [InstallShield](#installshield-deployment)) k vytvoření vaší aplikace Instalační program poskytuje instalační složky souboru, která bude odebrána po instalaci, může být offline instalačního programu automaticky se odstraní podle jeho umístění do složky, instalační program.

 ** Pokud používáte webovou Instalační službu s vlastní instalace, můžete použít výchozí nastavení jazyka na základě nastavení Multilingual User Interface (MUI) uživatele, nebo zadejte jinou jazykovou sadu pomocí `/LCID` možnost na příkazovém řádku. Najdete v části [řetězení pomocí rozhraní .NET Framework výchozí](#chaining_default) příklady.

## <a name="deployment-methods"></a>Metody nasazení
 K dispozici jsou čtyři metody nasazení:

- Můžete nastavit závislost na rozhraní .NET Framework. Rozhraní .NET Framework můžete určit jako předpoklady v instalaci vaší aplikace pomocí jednoho z těchto metod:

    - Použití [ClickOnce – nasazení](#clickonce-deployment) (k dispozici pomocí sady Visual Studio)

    - Vytvoření [InstallAware projektu](#installaware-deployment) (Bezplatná edice k dispozici pro uživatele v sadě Visual Studio)

    - Vytvoření [projekt InstallShield](#installshield-deployment) (k dispozici pomocí sady Visual Studio)

    - Použití [sada nástrojů Windows Installer XML (WiX)](#wix)

- Může požádat uživatele, aby [ruční instalace rozhraní .NET Framework](#installing_manually).

- Můžete řetězu (zahrnout) rozhraní .NET Framework instalace v instalačním programu vaší aplikace a rozhodnout, jak pro zpracování prostředí instalace rozhraní .NET Framework:

    - [Použít výchozí nastavení uživatelského rozhraní](#chaining_default). Umožní zadat možnosti instalace Instalační služby rozhraní .NET Framework.

    - [Přizpůsobení uživatelského rozhraní](#chaining_custom) předložit jednotnou instalaci prostředí a monitorovat průběh instalace rozhraní .NET Framework.

 Tyto metody nasazení jsou podrobněji v následujících částech.

## <a name="setting-a-dependency-on-the-net-framework"></a>Nastavení závislost na rozhraní .NET Framework
Pokud používáte k nasazení aplikace ClickOnce, InstallAware, InstallShield nebo WiX, můžete přidat závislost na rozhraní .NET Framework proto může být nainstalované v rámci vaší aplikace.

### <a name="clickonce-deployment"></a>ClickOnce – nasazení
 ClickOnce – nasazení je k dispozici pro projekty, které jsou vytvořeny pomocí jazyka Visual Basic a Visual C#, ale není k dispozici pro Visual C++.

 V sadě Visual Studio, vyberte nasazení ClickOnce a přidat závislost na rozhraní .NET Framework:

1.  Otevřete projekt aplikace, kterou chcete publikovat.

2.  V Průzkumníku řešení otevřete místní nabídky pro svůj projekt a zvolte **vlastnosti**.

3.  Vyberte **publikovat** podokně.

4.  Vyberte **požadavky** tlačítko.

5.  V **požadavky** dialogové okno pole, ujistěte se, že **vytvořit instalační program pro instalaci požadovaných součástí** je zaškrtnuté políčko.

6.  V seznamu požadavky vyhledejte a vyberte verzi rozhraní .NET Framework, který jste použili k vytvoření projektu.

7.  Zvolte možnost zadejte umístění zdroje pro požadavky, a pak vyberte **OK**.

     Pokud zadáte adresu URL pro umístění stahování rozhraní .NET Framework, můžete zadat webu Microsoft Download Center nebo vlastní lokalitě. Pokud jsou uvedení redistribuovatelného balíčku na vlastní server, musí být offline instalačního programu a není webové instalační služby. Můžete propojit pouze s webovou Instalační službu na webu Microsoft Download Center. Adresu URL můžete také zadat disk, na kterém je distribuován vlastní aplikace.

8.  V **stránky vlastností** dialogovém okně vyberte **OK**.

<a name="installaware"></a> 
### <a name="installaware-deployment"></a>InstallAware nasazení
InstallAware sestavení aplikace pro Windows (APPX), instalační služby systému Windows (MSI), nativního kódu (EXE) a balíčky App-V (Application Virtualization) z jednoho zdroje. Snadno [obsahovat všechny verze rozhraní .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) v nastavení aplikace volitelně přizpůsobení instalace pomocí [úpravy výchozí skripty](https://www.installaware.com/msicode.htm). Například InstallAware předem nainstaluje certifikátů ve Windows 7, bez kterých instalace rozhraní .NET Framework 4.7 nezdaří. Další informace o InstallAware najdete v tématu [InstallAware pro Instalační služby systému Windows](https://www.installaware.com/) webu.

### <a name="installshield-deployment"></a>InstallShield nasazení
 V sadě Visual Studio, a vyberte InstallShield nasazení a přidat závislost na rozhraní .NET Framework:

1.  Na panelu nabídek Visual Studio zvolte **soubor**, **nový**, **projektu**.

2.  V levém podokně **nový projekt** dialogovém okně vyberte **jiné typy projektů**, **instalace a nasazení**, **InstallShield LE**.

3.  V **název** pole, zadejte název projektu a potom zvolte **OK**.

4.  Instalace a nasazení projektu při prvním vytváření, zvolte **přejít na InstallShield** nebo **Povolit InstallShield Limited Edition** ke stažení pro vaši verzi InstallShield Limited Edition Sadu Microsoft Visual Studio. Restartujte sadu Visual Studio.

5.  Přejděte na **projektu pomocníka** průvodce a vyberte **soubory aplikace** přidat výstup projektu. Pomocí tohoto průvodce můžete nakonfigurovat další atributy projektu.

6.  Přejděte na **požadavky na instalaci** a vyberte operační systémy a verze rozhraní .NET Framework, kterou chcete nainstalovat.

7.  Otevřete místní nabídku pro projekt instalace a zvolte **sestavení**.
 
<a name="wix"></a> 
### <a name="windows-installer-xml-wix-deployment"></a>Nasazení Windows Installer XML (WiX)
 Sada nástrojů Windows Installer XML (WiX) vytvoří balíčky instalace systému Windows ze zdrojového kódu XML. WiX podporuje prostředí příkazového řádku, který se dá integrovat do svých sestavení sestavovat balíčky, instalační program MSI a MSM. Pomocí WiX můžete [zadejte rozhraní .NET Framework jako předpoklad](http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html), nebo [vytvořit zřetězeného souboru](http://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) plně řídit možnosti nasazení rozhraní .NET Framework. Další informace o WiX najdete v tématu [Windows Installer XML (WiX) toolset](http://wixtoolset.org/) webu.

<a name="installing_manually"></a> 
## <a name="installing-the-net-framework-manually"></a>Ruční instalace rozhraní .NET Framework
 V některých situacích může být nepraktické můžete automaticky nainstalovat rozhraní .NET Framework s vaší aplikací. V takovém případě může mít uživatelé nainstalovat rozhraní .NET Framework. Distribuovatelný balíček je k dispozici v [dva balíčky](#redistributable-packages). V procesu instalace poskytují pokyny pro jak uživatelé měli najít a nainstalovat rozhraní .NET Framework.

<a name="chaining"></a> 
## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Řetězení instalace rozhraní .NET Framework pro instalaci vaší aplikace
 Pokud vytváříte vlastní instalační program pro aplikaci, které tvoří řetěz (zahrnout) procesu instalace rozhraní .NET Framework v procesu instalace vaší aplikace. Řetězení nabízí dvě možnosti uživatelského rozhraní pro instalaci rozhraní .NET Framework:

- Použijte výchozí nastavení uživatelského rozhraní poskytované instalační program rozhraní .NET Framework.

- Vytvořte vlastní uživatelské rozhraní pro instalaci rozhraní .NET Framework pro konzistence s instalačním programem vaší aplikace.

 Obě metody umožňují použít instalační program webové nebo offline instalačního programu. Každý balíček má svoje výhody:

- Pokud používáte webovou Instalační službu, proces instalace rozhraní .NET Framework rozhodnout, které instalační balíček není povinné a stáhněte a nainstalujte pouze tento balíček z webu.

- Pokud používáte offline instalačního programu, můžete zahrnout kompletní sadu rozhraní .NET Framework instalační balíčky s médiu Redistribuce tak, aby vaši uživatelé nemají žádné další soubory stáhnout z webu během instalace.

<a name="chaining_default"></a> 
### <a name="chaining-by-using-the-default-net-framework-ui"></a>Řetězení pomocí výchozí uživatelského rozhraní .NET Framework
 Bezobslužná řetězu proces instalace rozhraní .NET Framework a nechat instalační program rozhraní .NET Framework, zadejte uživatelské rozhraní, přidejte do instalačního programu následující příkaz:

```
<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>
```

 Například pokud spustitelný program Contoso.exe a chcete bezobslužně nainstalovat [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] offline redistribuovatelný balíček, použijte příkaz:

```
dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso
```

 Další možnosti příkazového řádku můžete použít k přizpůsobení instalace. Příklad:

- Poskytnout způsob, jak uživatelům zavřete spuštěné aplikace rozhraní .NET Framework pro minimalizaci restartování systému, nastavte pasivní režim a použít `/showrmui` možnost následujícím způsobem:

    ```
    dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso
    ```

     Tento příkaz umožňuje restartovat správce zobrazit okno se zprávou, která poskytuje uživatelům možnost Zavřít aplikací rozhraní .NET Framework před instalací rozhraní .NET Framework.

- Pokud používáte webovou Instalační službu, můžete použít `/LCID` možnost zadat jazykovou sadu. Například pro řetězec [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] webové instalační služby systému vaší společnosti Contoso instalační program a nainstalujte japonská jazyková sada, přidáním následujícího příkazu do procesu instalace vaší aplikace:

    ```
    dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041
    ```

     V případě vynechání `/LCID` možnost, instalační program nainstaluje jazyková sada, která odpovídá MUI nastavení uživatele.

    > [!NOTE]
    > Data jinou verzi může mít různé jazykové sady. Pokud vámi zadaných jazyková sada není k dispozici na webu Stažení softwaru, instalační program nainstaluje rozhraní .NET Framework bez jazykové sady. Pokud rozhraní .NET Framework je již nainstalován na počítači uživatele, instalační program nainstaluje pouze jazykové sady.

 Úplný seznam možností, najdete v článku [možnosti příkazového řádku](#command-line-options) části.

 Běžné návratové kódy, najdete v článku [návratové kódy](#return-codes) části.

<a name="chaining_custom"></a>
### <a name="chaining-by-using-a-custom-ui"></a>Řetězení pomocí vlastního uživatelského rozhraní
 Pokud máte vlastní instalační balíček, můžete bezobslužně spustit a sledovat instalaci rozhraní .NET Framework při zobrazování zobrazení průběh instalačního programu. Pokud je to tento případ, ujistěte se, že se vztahuje na následující kód:

- Zkontrolujte [rozhraní .NET Framework hardwarové a softwarové požadavky](../../../docs/framework/get-started/system-requirements.md).

- [Zjištění](#detect_net) tom, jestli je již nainstalována správná verze rozhraní .NET Framework na počítači uživatele.

    > [!IMPORTANT]
    > Při určování, zda je již nainstalována správná verze rozhraní .NET Framework, byste měli zkontrolovat, zda cílová verze *nebo* je nainstalovaná novější verze, není, zda je nainstalována cílovou verzi. Jinými slovy, byste měli zvážit, zda klíč verze načíst z registru je větší než nebo rovna hodnotě klíč verze cílová verze, *není* jestli ho rovná verzi klíč cílovou verzi.

- [Zjištění](#detecting-the-language-packs) tom, jestli jsou již nainstalovány jazykové sady v počítači uživatele.

- Pokud chcete k řízení nasazení, bezobslužně spusťte a sledovat proces instalace rozhraní .NET Framework (viz [postup: průběh získat z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)).

- Pokud nasazujete offline instalačního programu, [řetězu jazykové sady samostatně](#chain_langpack).

- Přizpůsobit nasazení pomocí [možnosti příkazového řádku](#command-line-options). Například, pokud jste řetězení instalačního programu webové rozhraní .NET Framework, ale chcete přepsat výchozí jazykové sady, použijte `/LCID` možnost, jak je popsáno v předchozí části.

- [Řešení potíží s](#troubleshooting).

<a name="detect_net"></a>
### <a name="detecting-the-net-framework"></a>Zjišťování rozhraní .NET Framework
 Instalační program rozhraní .NET Framework zapíše klíče registru po úspěšné instalaci. Můžete otestovat jestli [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější je nainstalována kontrolou `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` složky v registru pro `DWORD` hodnotu s názvem `Release`. (Všimněte si, že "NET Framework instalace" nezačíná s dobou.) Existence tohoto klíče znamená, že [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo na tomto počítači je nainstalovaná novější verze. Hodnota `Release` označuje, která verze rozhraní .NET Framework je nainstalovaná.

> [!IMPORTANT]
> Je potřeba zkontrolovat pro hodnotu **větší než nebo rovna hodnotě** – klíčové slovo hodnotu verze při pokusu o zjistí, zda je na konkrétní verzi nachází.

|Version|Hodnota DWORD verze|
|-------------|--------------------------------|
|Rozhraní .NET framework 4.7.2 nainstalovaná v systému Windows 10. dubna 2018 aktualizace|461808|
|Rozhraní .NET framework 4.7.2 nainstalován ve všech verzích operačního systému než Windows 10. dubna 2018 aktualizace|461814|
|Rozhraní .NET framework 4.7.1 nainstalovaný na Windows 10 patří Creators aktualizace|461308|
|Rozhraní .NET framework 4.7.1 nainstalován ve všech verzích operačního systému než Windows 10 patří Creators aktualizace|461310|
|Rozhraní .NET framework 4.7 nainstalovaný na Windows 10 Creators Update|460798|
|Rozhraní .NET framework 4.7 nainstalován ve všech verzích operačního systému než Windows 10 Creators Update|460805|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nainstalovat na Windows 10 Anniversary Edition|394802|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nainstalovaná ve všech verzích operačního systému než Windows 10 Anniversary Edition|394806|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nainstalovat na Windows 10 listopadu Update|394254|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nainstalovaná ve všech verzích operačního systému než Windows 10 listopadu Update|394271|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] nainstalovat na Windows 10|393295|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] nainstalovaná ve všech verzích operačního systému než Windows 10|393297|
|.NET Framework 4.5.2|379893|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] nainstalované s [!INCLUDE[win81](../../../includes/win81-md.md)] nebo Windows Server 2012 R2|378675|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] nainstalovat na [!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7|378758|
|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|378389|

### <a name="detecting-the-language-packs"></a>Zjišťování jazykové sady
 Můžete zkontrolovat, zda je nainstalován konkrétní jazykové sady kontrolou HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* složku v registru pro hodnotu DWORD s názvem `Release`. (Všimněte si, že "NET Framework instalace" nezačíná s dobou.) *LCID* Určuje identifikátor národního prostředí; najdete v části [podporované jazyky](#supported-languages) pro seznam.

 Například k detekci jestli úplné japonská jazyková pack (LCID = 1041) je nainstalována, zkontrolujte následující hodnoty v registru:

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041
Name: Release
Type: DWORD
```

 Pokud chcete zjistit, zda je nainstalovaná poslední vydané verze jazykové sady pro konkrétní verzi rozhraní .NET Framework 4.5 prostřednictvím 4.7.2, zkontrolujte hodnotu verze klíče hodnotu DWORD popsané v předchozí části, [zjišťování .NET Framework](#detect_net).

<a name="chain_langpack"></a> 
### <a name="chaining-the-language-packs-to-your-app-setup"></a>Řetězení jazyk sady do vašeho nastavení aplikace
 Rozhraní .NET Framework poskytuje sadu samostatné language pack spustitelné soubory, které obsahují lokalizované prostředky pro konkrétní jazykové verze. Jazykové sady jsou k dispozici z webu Microsoft Download Center:

- [Rozhraní .NET framework 4.7.2 jazykové sady](http://go.microsoft.com/fwlink/p/?LinkId=863258)

- [Rozhraní .NET framework 4.7.1 jazykové sady](http://go.microsoft.com/fwlink/p/?LinkId=852090)

- [Rozhraní .NET framework 4.7 jazykové sady](http://go.microsoft.com/fwlink/p/?LinkId=825306)

- [Rozhraní .NET framework 4.6.2 jazykové sady](http://go.microsoft.com/fwlink/p/?LinkId=780604)

- [Rozhraní .NET framework 4.6.1 jazykové sady](http://go.microsoft.com/fwlink/p/?LinkId=671747)

- [Rozhraní .NET framework 4.6 jazykové sady](http://go.microsoft.com/fwlink/p/?LinkId=528314)

- [Rozhraní .NET framework 4.5.2 jazykové sady](http://go.microsoft.com/fwlink/p/?LinkId=397701)

- [Rozhraní .NET framework 4.5.1 jazykové sady](http://go.microsoft.com/fwlink/p/?LinkId=322101)

- [Rozhraní .NET framework 4.5 jazykové sady](http://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> Jazykové sady neobsahují součásti rozhraní .NET Framework, které jsou nutné ke spuštění aplikace; pomocí webové nebo offline instalační program před instalací jazykové sady, musíte nainstalovat rozhraní .NET Framework.

 Počínaje [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], názvy balíčků ve formě NRP <`version`>-KB <`number`>-x86-x64 - AllOS - <`culture`> .exe, kde `version` je číslo verze rozhraní .NET Framework, `number` je Číslo článku znalostní báze Microsoft Knowledge Base, a `culture` Určuje [země nebo oblast](#supported-languages). Je například jeden z těchto balíčků `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Balíček názvy jsou uvedeny v [Distribuovatelné balíčky](#redistributable-packages) dříve v tomto článku.

 Chcete-li nainstalovat jazykovou sadu s offline instalační program rozhraní .NET Framework, musí být propojeny s instalaci vaší aplikace. Například pro nasazení [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] offline instalačního programu s japonská jazyková sada, použijte následující příkaz:

```
NDP451-KB2858728-x86-x64-AllOS-JPN.exe/q /norestart /ChainingPackage <ProductName>
```

 Nemáte řetězu jazykové sady, pokud používáte webovou Instalační službu; Instalační program nainstaluje jazyková sada, která odpovídá MUI nastavení uživatele. Pokud chcete nainstalovat na jiný jazyk, můžete použít `/LCID` možnost zadat jazykovou sadu.

 Úplný seznam možností příkazového řádku, najdete v článku [možnosti příkazového řádku](#command-line-options) části.

### <a name="troubleshooting"></a>Poradce při potížích

#### <a name="return-codes"></a>Návratové kódy
 Následující tabulka uvádí nejběžnější návratové kódy pro instalační program rozhraní .NET Framework redistributable. Návratové kódy jsou stejné pro všechny verze instalačního programu. Odkazy na podrobnější informace najdete v další části.

|Návratový kód|Popis|
|-----------------|-----------------|
|0|Instalace byla úspěšně dokončena.|
|1602|Instalace byla zrušena uživatelem.|
|1603|Při instalaci došlo k závažné chybě.|
|1641|K dokončení instalace je nutné provést restart. Tato zpráva znamená úspěch.|
|3010|K dokončení instalace je nutné provést restart. Tato zpráva znamená úspěch.|
|5100|Počítač uživatele nesplňuje požadavky systému.|

#### <a name="download-error-codes"></a>Kódy chyb stahování
 Zobrazit následující obsah:

- [Kódy chyb Background Intelligent Transfer Service (BITS)](http://go.microsoft.com/fwlink/?LinkId=180946)

- [Adresa URL Přezdívka chybové kódy](http://go.microsoft.com/fwlink/?LinkId=180947)

- [Kódy chyb WinHttp](http://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Další kódy chyb
 Zobrazit následující obsah:

- [Kódy chyb Instalační služby systému Windows](http://go.microsoft.com/fwlink/?LinkId=180949)

- [Kódy výsledků agenta Windows Update Agent](http://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>Odinstalace rozhraní .NET Framework
 Počínaje [!INCLUDE[win8](../../../includes/win8-md.md)], můžete odinstalovat [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo jeden z jeho bod uvolní pomocí **zapnout funkce systému Windows a vypnutí** v Ovládacích panelech. Ve starších verzích Windows, můžete odinstalovat [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo jeden z jeho bod uvolní pomocí **přidat nebo odebrat programy** v Ovládacích panelech.

> [!IMPORTANT]
> Pro systém Windows 7 a starší operační systémy, odinstalace [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 nebo 4.7.2 nepodporuje obnovení [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] soubory a odinstalace [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nepodporuje obnovení [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] soubory. Pokud chcete přejít zpět na starší verzi, musíte ho přeinstalovat a všechny aktualizace.

## <a name="appendix"></a>Příloha

### <a name="command-line-options"></a>Možnosti příkazového řádku
 V následující tabulce je uveden seznam možností, které lze zahrnout při zřetězení [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] distribuovatelná součást k instalaci vaší aplikace.

|Možnost|Popis|
|------------|-----------------|
|**/ CEIPConsent**|Přepíše výchozí chování a odešle anonymní názory společnosti Microsoft zlepšovat prostředí budoucí nasazení. Tuto možnost lze použít pouze v případě, že instalační program zobrazí výzvu k souhlasu, a pokud uživatel uděluje oprávnění k posílat anonymní názory společnosti Microsoft.|
|**/chainingpackage** `packageName`|Určuje název spustitelného souboru, který provádí řetězení. Tyto informace se odesílají do Microsoftu jako vyskytne anonymní informace pomohou vylepšit budoucí nasazení.<br /><br /> Pokud název balíčku obsahuje mezery, použijte dvojité uvozovky jako oddělovače; Příklad: **/chainingpackage "Lucerne publikování"**. Příklad řetězení balíčku naleznete v části [získávání informace o průběhu z instalačního balíku](http://go.microsoft.com/fwlink/?LinkId=181926) v knihovně MSDN.|
|**/ LCID**  `LCID`<br /><br /> kde `LCID` Určuje identifikátor národního prostředí (viz [podporované jazyky](#supported-languages))|Instalujte jazykový balíček určeného `LCID` a pokud tichý režim je nastaven vynutí zobrazené uživatelské rozhraní zobrazený v daném jazyce.<br /><br /> Pro web instalační program tato možnost řetězu instalaci jazykovou sadu z webu. **Poznámka:** tuto možnost použijte pouze s webovou Instalační službu.|
|**/ log** `file`&#124; `folder`|Určuje umístění souboru protokolu. Výchozí hodnota je dočasnou složku pro proces a výchozí název souboru je založen na balíčku. Pokud přípona souboru .txt, textový protokol vytváří. Pokud zadáte jiné rozšíření nebo bez přípony, vytvoří se protokol HTML.|
|**/msioptions**|Určuje možnosti, které mají být předány .msi a .msp položek; Příklad: `/msioptions "PROPERTY1='Value'"`.|
|**/ norestart**|Zabrání restartování automaticky instalační program. Pokud použijete tuto možnost, k zaznamenání návratový kód a zpracování restartování má řetězení aplikace (viz [získávání informace o průběhu z instalačního balíku](http://go.microsoft.com/fwlink/?LinkId=179606) v knihovně MSDN).|
|**/passive**|Nastaví pasivní režim. Zobrazuje indikátor průběhu označíte, že je v průběhu instalace, ale nezobrazí žádné chybové zprávy nebo výzvy pro uživatele. V tomto režimu, pokud zřetězené instalační program řetězení balíčku musí zpracovávat [návratové kódy](#return-codes).|
|**/pipe**|Vytvoří komunikační kanál povolit řetězení balíčku k načtení průběh.|
|**/ promptrestart**|Pouze pasivní režim, pokud instalační program vyžaduje restartování, vyzve uživatele. Tato možnost vyžaduje interakci s uživatelem, pokud je vyžadováno restartování.|
|**/q**|Nastaví tichý režim.|
|**spínače/opravy**|Aktivuje funkci opravit.|
|**/serialdownload**|Vynutí instalaci provést až po stažení balíčku.|
|**/showfinalerror**|Nastaví pasivní režim. Zobrazí chyby jenom v případě, že instalace není úspěšná. Tato možnost vyžaduje interakci s uživatelem, pokud instalace není úspěšná.|
|**/showrmui**|Použít pouze s **/passive** možnost. Zobrazí okno se zprávou, která vyzve uživatele, aby zavřete aplikace rozhraní .NET Framework, které jsou aktuálně spuštěny. Toto okno se zprávou se chová stejně v pasivním a bez pasivní režim.|
|**/ uninstall**|Odinstaluje redistributable rozhraní .NET Framework.|

### <a name="supported-languages"></a>Podporované jazyky
Následující tabulka uvádí jazykových sad rozhraní .NET Framework, které jsou dostupné pro [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho bod.

|LCID|Jazyk – země nebo oblast|Jazyková verze|
|----------|--------------------------------|-------------|
|1025|Arabština - Saúdská Arábie|ar|
|1028|Tradiční čínština –|zh-Hant|
|1029|Čeština|cs|
|1030|Dánština|da|
|1031|Němčina – Německo|Německo|
|1032|Řečtina|El|
|1035|Finština|Fi|
|1036|Francouzština – Francie|FR|
|1037|Hebrejština|mu|
|1038|Maďarština|HU|
|1040|Italština – Itálie|ho|
|1041|Japonština|Japonsko|
|1042|Korejština|Ko|
|1043|Holandština – Nizozemsko|NL|
|1044|Norština (Bokmål)|Ne|
|1045|Polština|PL|
|1046|Portugalština – Brazílie|pt-BR|
|1049|Ruština|RU|
|1053|Švédština|sv|
|1055|Turečtina|tr|
|2052|– Zjednodušená čínština|zh-Hans|
|2070|Portugalština – Portugalsko|pt-PT|
|3082|Španělština – Španělsko (moderní řazení)|ES|

## <a name="see-also"></a>Viz také
 [Příručka nasazení pro administrátory](../../../docs/framework/deployment/guide-for-administrators.md)  
 [Požadavky na systém](../../../docs/framework/get-started/system-requirements.md)  
 [Nainstalujte rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md)  
 [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
 [Omezení restartů systému při instalaci rozhraní .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)  
 [Postupy: Získání procesu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
