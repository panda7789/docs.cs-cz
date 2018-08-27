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
ms.openlocfilehash: 869d64902c53e20667907b99276b9f8c6f3a2e20
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932846"
---
# <a name="net-framework-deployment-guide-for-developers"></a>Rozhraní .NET framework – Průvodce nasazením pro vývojáře
Toto téma obsahuje informace pro vývojáře, kteří chtějí nainstalovat z rozhraní .NET Framework 4.5 na žádné verze rozhraní .NET Framework [!INCLUDE[net_current](../../../includes/net-current-version.md)] s aplikacemi.

Odkazy ke stažení najdete v části [Distribuovatelné balíčky](#redistributable-packages). Distribuovatelné balíčky a jazykové sady si můžete stáhnout také z tyto stránky Microsoft Download Center:

- Rozhraní .NET framework 4.7.2 pro všechny operační systémy ([Webová instalační služba](http://go.microsoft.com/fwlink/?LinkId=863262) nebo [offline instalační program](http://go.microsoft.com/fwlink/p/?LinkId=863265))

- Rozhraní .NET framework 4.7.1 pro všechny operační systémy ([Webová instalační služba](http://go.microsoft.com/fwlink/?LinkId=852095) nebo [offline instalační program](http://go.microsoft.com/fwlink/p/?LinkId=852107))

- Rozhraní .NET framework 4.7 pro všechny operační systémy ([Webová instalační služba](http://go.microsoft.com/fwlink/?LinkId=825299) nebo [offline instalační program](http://go.microsoft.com/fwlink/p/?LinkId=825303))

- [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] pro všechny operační systémy ([Webová instalační služba](http://go.microsoft.com/fwlink/?LinkId=780597) nebo [offline instalační program](http://go.microsoft.com/fwlink/p/?LinkId=780601))

- [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] pro všechny operační systémy ([Webová instalační služba](http://go.microsoft.com/fwlink/?LinkId=671729) nebo [offline instalační program](http://go.microsoft.com/fwlink/p/?LinkId=671744))

- [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] pro všechny operační systémy ([Webová instalační služba](http://go.microsoft.com/fwlink/?LinkId=528222) nebo [offline instalační program](http://go.microsoft.com/fwlink/p/?LinkId=528232))

- Rozhraní .NET framework 4.5.2 pro všechny operační systémy ([Webová instalační služba](http://go.microsoft.com/fwlink/p/?LinkId=397703) nebo [offline instalační program](http://go.microsoft.com/fwlink/p/?LinkId=397706))

- Rozhraní .NET framework 4.5.1 pro všechny operační systémy ([Webová instalační služba](http://go.microsoft.com/fwlink/p/?LinkId=310158) nebo [offline instalační program](http://go.microsoft.com/fwlink/p/?LinkId=310159))

- [Rozhraní .NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)

 Důležité poznámky:

> [!NOTE]
> Fráze " [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho verze" odkazuje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a všechny novější verze.

- Verze rozhraní .NET Framework z [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] prostřednictvím [!INCLUDE[net_current](../../../includes/net-current-version.md)] jsou aktualizace na místě [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], což znamená, že používají stejnou verzi modulu runtime, ale verze sestavení jsou aktualizované a nové typy a členy.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho vydání bodu jsou sestaveny postupně v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Při instalaci [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo jeho verze v systému, který má [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] nainstalovaná, budou sestavení verze 4 jsou nahrazena novějšími verzemi.

- Pokud odkazujete na Microsoft [out-of-band balíček](../get-started/the-net-framework-and-out-of-band-releases.md) ve vaší aplikaci, bude sestavení součástí balíčku aplikace.

- Musí mít oprávnění správce k instalaci [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho verze.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Je součástí [!INCLUDE[win8](../../../includes/win8-md.md)] a [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], takže není nutné nasazovat s vaší aplikací v těchto operačních systémech. Podobně platí [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] je součástí [!INCLUDE[win81](../../../includes/win81-md.md)] a Windows Server 2012 R2. Všechny operační systémy není součástí rozhraní .NET Framework 4.5.2. [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] Je součástí systému Windows 10 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] je součástí systému Windows 10 Listopadové aktualizace a [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] je součástí systému Windows 10 Anniversary Update.  Rozhraní .NET Framework 4.7 je součástí systému Windows 10 Creators Update, rozhraní .NET Framework 4.7.1 je součástí Windows 10 Fall Creators Update a rozhraní .NET Framework 4.7.2 je součástí systému Windows 10. dubna 2018 aktualizovat. Úplný seznam požadavků na hardware a software najdete v tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).

- Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], vaši uživatelé mohou zobrazit seznam spuštěných aplikací rozhraní .NET Framework během instalace a snadno je zavřít. To může pomoci zabránit restartování systému způsobenému instalací rozhraní .NET Framework. Zobrazit [omezení restartů systému](../../../docs/framework/deployment/reducing-system-restarts.md).

- Odinstalace [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo jeden z jeho bod uvolní také odebere existující [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] soubory. Pokud chcete přejít zpět [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], nainstalujte ho a všechny aktualizace. (Viz [instalace rozhraní .NET Framework 4](http://msdn.microsoft.com/library/5a4x27ek\(v=vs.100\).aspx).)

- Rozhraní .NET Framework 4.5 redistributable byl aktualizován na 9. října 2012 Chcete-li opravit problém související s nesprávným časovým razítkem v digitálním certifikátu, která způsobila digitální podpis souborů vytvořila a podepsala společnost Microsoft vyprší předčasně ukončen. Pokud jste dříve nainstalovali rozhraní .NET Framework 4.5 redistributable package s datem 16. srpna 2012, doporučujeme aktualizovat kopii nejnovější redistributovatelnou z [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=245484). Další informace o tomto problému najdete v tématu [Microsoft Security Advisory 2749655](http://technet.microsoft.com/security/advisory/2749655).

 Informace o tom, jak může správce systému nasadit rozhraní .NET Framework a jeho systémové závislosti napříč sítí najdete v tématu [Příručka nasazení pro administrátory](../../../docs/framework/deployment/guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Možnosti nasazení pro vaši aplikaci
 Jakmile budete připraveni k publikování aplikace na webovém serveru nebo jiné centralizované umístění tak, aby uživatelé mohli instalovat, můžete z několika metod nasazení. Některé z nich jsou součástí sady Visual Studio. Následující tabulka uvádí možnosti nasazení pro vaši aplikaci a určuje Distribuovatelný balíček rozhraní .NET Framework, která podporuje jednotlivé možnosti. Kromě toho můžete napsat vlastní instalační program pro vaši aplikaci; Další informace najdete v části [zřetězení instalace rozhraní .NET Framework do vaší aplikace](#chaining).

|Strategie nasazení pro vaši aplikaci|Dostupné metody nasazení|Rozhraní .NET framework, distribuovatelné součásti k použití|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Instalace z webu|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Sada nástrojů WiX](#wix)<br />- [Ruční instalace](#installing_manually)|[Webová instalační služba](#redistributable-packages)|
|Instalace z disku|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Sada nástrojů WiX](#wix)<br />- [Ruční instalace](#installing_manually)|[Offline instalační program](#redistributable-packages)|
|Instalace z místní sítě (pro podnikové aplikace)|- [Technologie ClickOnce](#clickonce-deployment)|Buď [Webová instalační služba](#redistributable-packages) (viz [ClickOnce](#clickonce-deployment) omezení) nebo [offline instalační program](#redistributable-packages)|

## <a name="redistributable-packages"></a>Distribuovatelné balíčky
 Rozhraní .NET Framework je k dispozici ve dvou distribuovatelných balíčcích: webový instalátor (samozavaděč) a offline instalační program (samostatné redistribuovatelné). Následující tabulka porovnává tyto dva balíčky.

||Webová instalační služba|Offline instalační program|
|-|-------------------|-----------------------|
|Stáhněte si soubor|Rozhraní .NET framework 4.7.2: <br/>[NDP472. KB4054531 Web.exe](http://go.microsoft.com/fwlink/?LinkId=863262)<br/><br/>Rozhraní .NET framework 4.7.1: <br/>[NDP471-KB4033344-Web.exe](http://go.microsoft.com/fwlink/?LinkId=852092)<br/><br/>Rozhraní .NET framework 4.7: <br />[NDP47-KB3186500-Web.exe](http://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151802-Web.exe](http://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]:<br />[NDP461-KB3102438-Web.exe](http://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]:<br />[NDP46-KB3045560-Web.exe](http://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> Rozhraní .NET framework 4.5.2: <br />[NDP452-KB2901954-Web.exe](http://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2859818-Web.exe](http://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_setup.exe](http://go.microsoft.com/fwlink/?LinkId=225704)|Rozhraní .NET framework 4.7.2: <br/>[NDP472-KB4054530-x86-x64-AllOS-enu.exe](http://go.microsoft.com/fwlink/?LinkId=863265)<br/><br/>Rozhraní .NET framework 4.7.1: <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />Rozhraní .NET framework 4.7: <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]: <br />[NDP462-KB3151800-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]: <br />[NDP461-KB3102436-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]: <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> Rozhraní .NET framework 4.5.2: <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]: <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](http://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]: <br />[dotNetFx45_Full_x86_x64.exe](http://go.microsoft.com/fwlink/?LinkId=225702)|
|Vyžadováno připojení k Internetu?|Ano|Ne|
|Velikost souboru ke stažení|Menší (obsahuje instalační program pro cílovou platformu pouze) *|Větší *|
|Jazykové sady|Zahrnuté **|Musí být [nainstalovat samostatně](#chain_langpack), pokud nepoužíváte balíček, který cílí na všechny operační systémy|
|Metoda nasazení|Podporuje všechny metody:<br /><br />- [Technologie ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [Ruční instalace](#installing_manually)<br />- [Vlastní instalace (zřetězení)](#chaining)|Podporuje všechny metody:<br /><br /> - [Technologie ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [Ruční instalace](#installing_manually)<br />- [Vlastní instalace (zřetězení)](#chaining)|
|Umístění staženého souboru pro nasazení ClickOnce|Microsoft Download Center:<br /><br /> - [Rozhraní .NET framework 4.7.2](http://go.microsoft.com/fwlink/?LinkId=863262) <br/> - [Rozhraní .NET framework 4.7.1](http://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [Rozhraní .NET framework 4.7](http://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [Rozhraní .NET framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780596)<br />- [Rozhraní .NET framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671728)<br />- [Rozhraní .NET framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528222)<br />- [Rozhraní .NET framework 4.5.2](http://go.microsoft.com/fwlink/?LinkId=397703)<br />- [Rozhraní .NET framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [Rozhraní .NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|Váš vlastní server nebo Microsoft Download Center:<br /><br /> - [Rozhraní .NET framework 4.7.2](http://go.microsoft.com/fwlink/?LinkId=863265)<br /> - [Rozhraní .NET framework 4.7.1](http://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [Rozhraní .NET framework 4.7](http://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [Rozhraní .NET framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780600)<br />- [Rozhraní .NET framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=671743)<br />- [Rozhraní .NET framework 4.6](http://go.microsoft.com/fwlink/?LinkId=528232)<br />- [Rozhraní .NET framework 4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [Rozhraní .NET framework 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [Rozhraní .NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)|

 \* Instalátor offline je větší, protože obsahuje komponenty pro všechny cílové platformy. Po dokončení instalačního programu operačního systému Windows ukládá do mezipaměti pouze instalační program, který byl použit. Pokud je po instalaci odstraněn instalátor offline, využití místa na disku je stejný jako, který se používá webová instalační služba. Pokud používáte nástroj (třeba [InstallAware](#installaware-deployment) nebo [InstallShield](#installshield-deployment)) k vytvoření instalačního programu vaší aplikace obsahuje složku pro instalační soubor, který je po instalaci odebrána, může být offline instalační program automaticky odstranit umístěním do instalační složky.

 ** Pokud používáte webový instalátor s vlastním nastavením, můžete použít výchozí nastavení jazyka na základě nastavení Multilingual User Interface (MUI) uživatele, nebo zadat jinou jazykovou sadu pomocí `/LCID` možnost na příkazovém řádku. V části [řetězení pomocí rozhraní .NET Framework výchozí](#chaining_default) příklady.

## <a name="deployment-methods"></a>Metody nasazení
 K dispozici jsou čtyři metody nasazení:

- Nastavit závislost na rozhraní .NET Framework. Můžete určit rozhraní .NET Framework jako předpoklad v instalačním programu vaší aplikace pomocí jedné z těchto metod:

    - Použití [nasazení ClickOnce](#clickonce-deployment) (k dispozici se sadou Visual Studio)

    - Vytvoření [InstallAware projektu](#installaware-deployment) (edice free k dispozici pro uživatele sady Visual Studio)

    - Vytvoření [projektu InstallShield](#installshield-deployment) (k dispozici se sadou Visual Studio)

    - Použití [sada nástrojů XML Instalační služby systému Windows (WiX)](#wix)

- Můžete požádat uživatele, aby [ruční instalace rozhraní .NET Framework](#installing_manually).

- Můžete zřetězit (zahrnout) instalace v instalačním programu vaší aplikace rozhraní .NET Framework a rozhodnutí o způsobu zpracování instalace rozhraní .NET Framework:

    - [Použijte výchozí uživatelské rozhraní](#chaining_default). Nechte instalační program rozhraní .NET Framework zajišťovat průběh instalace.

    - [Přizpůsobení uživatelského rozhraní](#chaining_custom) předložit jednotného průběhu instalace a sledovat průběh instalace rozhraní .NET Framework.

 Tyto metody nasazení jsou podrobně popsány v následující části.

## <a name="setting-a-dependency-on-the-net-framework"></a>Nastavení závislosti na rozhraní .NET Framework
Pokud používáte k nasazení aplikace ClickOnce, InstallAware, InstallShield nebo WiX, můžete přidat závislost na rozhraní .NET Framework, může být nainstalován jako součást vaší aplikace.

### <a name="clickonce-deployment"></a>ClickOnce – nasazení
 ClickOnce – nasazení je k dispozici pro projekty, které jsou vytvořené pomocí jazyka Visual Basic a Visual C#, ale není k dispozici pro aplikaci Visual C++.

 V sadě Visual Studio, volba nasazení ClickOnce a přidání závislosti na rozhraní .NET Framework:

1.  Otevřete projekt aplikace, které chcete publikovat.

2.  V Průzkumníku řešení otevřete místní nabídku pro váš projekt a klikněte na tlačítko **vlastnosti**.

3.  Zvolte **publikovat** podokně.

4.  Zvolte **požadavky** tlačítko.

5.  V **požadavky** dialogové okno pole, ujistěte se, že **vytvořit instalační program pro nainstalování nezbytných součástí** je zaškrtnuto políčko.

6.  V seznamu požadavků vyhledejte a vyberte verzi rozhraní .NET Framework, který jste použili k sestavení projektu.

7.  Zvolte možnost určení umístění zdroje pro požadavky a klikněte na tlačítko **OK**.

     Pokud zadáte adresu URL pro umístění pro stažení rozhraní .NET Framework, můžete zadat web Microsoft Download Center nebo vlastní web. Pokud umístíte opětovně Distribuovatelný balíček na vlastní server, musí být offline instalační program a ne o webový instalátor. Můžete pouze propojit webovou Instalační službu na webu Microsoft Download Center. Adresu URL můžete také určit disk, na kterém je vlastní aplikace distribuována.

8.  V **stránky vlastností** dialogového okna zvolte **OK**.

<a name="installaware"></a> 
### <a name="installaware-deployment"></a>InstallAware nasazení
InstallAware sestavení aplikace Windows (APPX), instalační služby systému Windows (MSI), nativní kód (EXE) a balíčky sady App-V (Application Virtualization) z jednoho zdroje. Snadno [zahrnout všechny verze rozhraní .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) ve vašem nastavení volitelně přizpůsobení instalace podle [úpravy skriptů výchozí](https://www.installaware.com/msicode.htm). InstallAware nainstaluje například předem certifikátů ve Windows 7, bez kterých se nezdaří instalace rozhraní .NET Framework 4.7. Další informace o InstallAware, najdete v článku [InstallAware instalačního programu pro Windows](https://www.installaware.com/) webu.

### <a name="installshield-deployment"></a>Nasazení InstallShield
 V sadě Visual Studio, volba nasazení InstallShield a přidání závislosti na rozhraní .NET Framework:

1.  Na řádku nabídek sady Visual Studio, zvolte **souboru**, **nový**, **projektu**.

2.  V levém podokně **nový projekt** dialogového okna zvolte **ostatní typy projektů**, **instalace a nasazení**, **InstallShield LE**.

3.  V **název** pole, zadejte název pro váš projekt a klikněte na tlačítko **OK**.

4.  Pokud vytváříte první projekt instalace a nasazení, zvolte **přejít na web InstallShield** nebo **Povolit InstallShield Limited Edition** a stáhněte si InstallShield Limited Edition pro vaši verzi Microsoft Visual Studio. Restartujte sadu Visual Studio.

5.  Přejděte na **Project Assistant** průvodce a zvolit **soubory aplikace** Přidání výstupu projektu. Pomocí tohoto průvodce můžete nakonfigurovat další atributy projektu.

6.  Přejděte na **požadavky na instalaci** a vyberte operační systémy a verze rozhraní .NET Framework, kterou chcete nainstalovat.

7.  Otevřete místní nabídku pro projekt instalace a zvolte **sestavení**.
 
<a name="wix"></a> 
### <a name="windows-installer-xml-wix-deployment"></a>Nasazení XML Instalační služby systému Windows (WiX)
 Sada nástrojů XML Instalační služby systému Windows (WiX) sestaví instalační balíčky Windows ze zdrojového kódu XML. Nástroj WiX podporuje prostředí příkazového řádku, který je možné integrovat do procesů sestavení k sestavení instalačních balíčků MSI a MSM. Pomocí WiX lze [určit rozhraní .NET Framework jako předpoklad](http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html), nebo [vytvořit zřetězený soubor](http://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) plně řídit možnosti nasazení rozhraní .NET Framework. Další informace o WiX naleznete v tématu [XML Instalační služby systému Windows (WiX) toolset](http://wixtoolset.org/) webu.

<a name="installing_manually"></a> 
## <a name="installing-the-net-framework-manually"></a>Ruční instalace rozhraní .NET Framework
 V některých situacích může být nepraktické můžete automaticky nainstalovat rozhraní .NET Framework s vaší aplikací. V takovém případě může mít uživatelé nainstalovat rozhraní .NET Framework. Distribuovatelný balíček je k dispozici v [dva balíčky](#redistributable-packages). V průběhu instalace poskytují pokyny pro jak uživatelům najít a nainstalovat rozhraní .NET Framework.

<a name="chaining"></a> 
## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Zřetězení instalace rozhraní .NET Framework do instalačního programu vaší aplikace
 Pokud vytváříte vlastní instalační program pro vaši aplikaci, můžete zřetězit (zahrnout) proces instalace rozhraní .NET Framework v procesu instalace vaší aplikace. Řetězení nabízí dvě možnosti uživatelského rozhraní pro instalaci rozhraní .NET Framework:

- Použijte výchozí uživatelské rozhraní poskytované instalačním programem rozhraní .NET Framework.

- Vytvoření vlastního uživatelského rozhraní pro instalaci rozhraní .NET Framework pro zajištění konzistence s instalačním programem vaší aplikace.

 Obě metody umožňují použít webovou Instalační službu nebo offline instalační program. Každý balíček má své výhody:

- Pokud používáte webový instalátor, proces instalace rozhraní .NET Framework rozhodnout, které instalační balíčky jsou požadovány a stáhněte a nainstalujte pouze tento balíček z webu.

- Pokud použijete instalátor offline, můžete zahrnout úplnou sadu instalačních balíčků rozhraní .NET Framework s vašimi distribuovatelnými médii tak, aby uživatelé nemuseli stahovat žádné další soubory z webu během instalace.

<a name="chaining_default"></a> 
### <a name="chaining-by-using-the-default-net-framework-ui"></a>Řetězení pomocí výchozího uživatelského rozhraní .NET Framework
 Bezobslužná řetězení instalačního procesu rozhraní .NET Framework a nechat instalační program rozhraní .NET Framework poskytuje uživatelské rozhraní, přidejte ke svému instalačnímu programu následující příkaz:

```
<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>
```

 Například pokud je spustitelný program Contoso.exe a chcete nainstalovat [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Distribuovatelný balíček pro offline instalaci, použijte příkaz:

```
dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso
```

 Další možnosti příkazového řádku můžete použít k přizpůsobení instalace. Příklad:

- Poskytnout způsob pro uživatele k ukončení spuštěných aplikací rozhraní .NET Framework, minimalizace počtu restartování systému, nastavte pasivní režim a použít `/showrmui` možnost následujícím způsobem:

    ```
    dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso
    ```

     Tento příkaz umožňuje správci restartování zobrazit okno se zprávou, která uživatelům nabízí možnost ukončit aplikace rozhraní .NET Framework před instalací rozhraní .NET Framework.

- Pokud používáte webový instalátor, můžete použít `/LCID` můžete zadat jazykovou sadu. Například pro zřetězení [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Webová instalační služba na instalačním programem Contoso a instalaci japonské jazykové sady, přidejte následující příkaz k instalaci vaší aplikace:

    ```
    dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041
    ```

     Vynecháte-li `/LCID` možnost, instalační program nainstaluje jazykovou sadu odpovídající nastavení MUI uživatele.

    > [!NOTE]
    > Různé jazykové sady mohou mít různá data vydání. Pokud této jazykové sady, které jste zadali, není k dispozici na webu download center, instalační program nainstaluje rozhraní .NET Framework bez jazykové sady. Pokud rozhraní .NET Framework je již nainstalována v počítači uživatele, instalační program nainstaluje jazykovou sadu.

 Úplný seznam možností, najdete v článku [možnosti příkazového řádku](#command-line-options) oddílu.

 Společné návratové kódy, najdete v článku [návratové kódy](#return-codes) oddílu.

<a name="chaining_custom"></a>
### <a name="chaining-by-using-a-custom-ui"></a>Řetězení pomocí vlastního uživatelského rozhraní
 Pokud máte vlastní instalační balíček, můžete spustit bez upozornění a sledovat instalaci rozhraní .NET Framework při vlastním zobrazením průběhu instalace. Pokud je to tento případ, ujistěte se, že váš kód obsahuje následující:

- Vyhledat [požadavky na hardware a software rozhraní .NET Framework](../../../docs/framework/get-started/system-requirements.md).

- [Zjištění](#detect_net) Určuje, zda je již nainstalována správná verze rozhraní .NET Framework na počítači uživatele.

    > [!IMPORTANT]
    > Při určování, zda je již nainstalována správná verze rozhraní .NET Framework, měli byste zkontrolovat, jestli vaši cílovou verzi *nebo* je nainstalovaná novější verze, ne, zda je nainstalována vaši cílovou verzi. Jinými slovy, by se měl vyhodnotit, jestli klíč verze načíst z registru je větší než nebo rovna verzi klíče vaši cílovou verzi *není* , jestli se rovná verzi klíče vaši cílovou verzi.

- [Zjištění](#detecting-the-language-packs) Určuje, zda jsou již nainstalovány jazykové sady v počítači uživatele.

- Pokud chcete řídit nasazování, bez upozornění spusťte a sledujte proces instalace rozhraní .NET Framework (viz [postupy: získání průběhu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)).

- Pokud nasazujete offline instalační program [řetězení jazykových sad samostatně](#chain_langpack).

- Přizpůsobte nasazení pomocí [možnosti příkazového řádku](#command-line-options). Například, pokud provádíte řetězení webového instalátoru rozhraní .NET Framework, ale chcete přepsat výchozí jazykovou sadu, použijte `/LCID` možnosti, jak je popsáno v předchozí části.

- [Řešení potíží s](#troubleshooting).

<a name="detect_net"></a>
### <a name="detecting-the-net-framework"></a>Zjištění rozhraní .NET Framework
 Instalační program rozhraní .NET Framework zapíše klíče registru, když se instalace úspěšně dokončila. Můžete otestovat, zda [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější nainstalován kontrolou `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` složky v registru `DWORD` hodnotu s názvem `Release`. (Všimněte si, že "NET Framework Setup" v registru nezačíná tečkou.) Existence tohoto klíče označuje, že [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo na tomto počítači je nainstalovaná novější verze. Hodnota `Release` označuje, která verze rozhraní .NET Framework je nainstalována.

> [!IMPORTANT]
> Hodnota by měla vyhledávat **větší než nebo rovna hodnotě** hodnotu klíčového slova verze při pokusu o zjištění, zda je k dispozici na konkrétní verzi.

|Version|Hodnota DWORD verze|
|-------------|--------------------------------|
|Rozhraní .NET framework 4.7.2 nainstalované ve Windows 10. dubna 2018 Update a Windows Server verze 1803|461808|
|Rozhraní .NET framework nainstalované na všech verzí operačního systému než Windows 10. dubna 2018 4.7.2 Update a Windows Server verze 1803|461814|
|Rozhraní .NET framework 4.7.1 nainstalovat na Windows 10 Fall Creators Update a na Windows Server verze 1709|461308|
|Rozhraní .NET framework 4.7.1 nainstalovat na všechny verze operačního systému než Windows 10 Fall Creators Update a Windows Server verze 1709|461310|
|Rozhraní .NET framework 4.7 nainstalované ve Windows 10 Creators Update|460798|
|Rozhraní .NET framework 4.7 nainstalovaný na všech verzí operačního systému než Windows 10 Creators Update|460805|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nainstalovat na Windows 10 Anniversary Edition a na Windows serveru 2016|394802|
|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] nainstalovat na všechny verze operačního systému než Windows 10 Anniversary Edition a Windows serveru 2016|394806|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nainstalované ve Windows 10. listopadu Update|394254|
|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nainstalovat na všechny verze operačního systému než Windows 10. listopadu Update|394271|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] nainstalovat na Windows 10|393295|
|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] nainstalovat na všechny verze operačního systému než Windows 10|393297|
|.NET Framework 4.5.2|379893|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] součástí [!INCLUDE[win81](../../../includes/win81-md.md)] nebo Windows Server 2012 R2|378675|
|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] nainstalovat na [!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7|378758|
|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|378389|

### <a name="detecting-the-language-packs"></a>Zjištění jazykových sad
 Můžete zkontrolovat, jestli konkrétní jazyková sada nainstalovaná tak, že zkontrolujete HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* složky v registru DWORD s názvem `Release`. (Všimněte si, že "NET Framework Setup" v registru nezačíná tečkou.) *LCID* Určuje identifikátor národního prostředí; viz [podporované jazyky](#supported-languages) pro jejich seznam.

 Například k detekci, jestli úplná Japonská sada (LCID = 1041) je nainstalovaná, zkontrolujte následující hodnoty registru:

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041
Name: Release
Type: DWORD
```

 Pokud chcete zjistit, zda je nainstalovaná poslední verze jazykové sady pro konkrétní verzi rozhraní .NET Framework 4.5 prostřednictvím 4.7.2, zkontrolujte hodnotu RELEASE DWORD hodnota klíče je popsáno v předchozí části [zjištění rozhraní .NET Rozhraní Framework](#detect_net).

<a name="chain_langpack"></a> 
### <a name="chaining-the-language-packs-to-your-app-setup"></a>Řetězení jazykových sad do instalačního programu vaší aplikace
 Rozhraní .NET Framework poskytuje sadu samostatné language pack spustitelné soubory, které obsahují lokalizované prostředky pro konkrétní jazykové verze. Jazykové sady jsou k dispozici z webu Microsoft Download Center:

- [Jazykové sady rozhraní .NET framework 4.7.2](http://go.microsoft.com/fwlink/p/?LinkId=863258)

- [Jazykové sady rozhraní .NET framework 4.7.1](http://go.microsoft.com/fwlink/p/?LinkId=852090)

- [Jazykové sady rozhraní .NET framework 4.7](http://go.microsoft.com/fwlink/p/?LinkId=825306)

- [Rozhraní .NET framework 4.6.2 language Pack](http://go.microsoft.com/fwlink/p/?LinkId=780604)

- [Rozhraní .NET framework 4.6.1 language Pack](http://go.microsoft.com/fwlink/p/?LinkId=671747)

- [Rozhraní .NET framework 4.6 language Pack](http://go.microsoft.com/fwlink/p/?LinkId=528314)

- [Jazykové sady rozhraní .NET framework 4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397701)

- [Rozhraní .NET framework 4.5.1 language Pack](http://go.microsoft.com/fwlink/p/?LinkId=322101)

- [Jazykové sady rozhraní .NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> Jazykové sady neobsahují součásti rozhraní .NET Framework, které jsou nutné ke spuštění aplikace; pomocí webu nebo offline instalační program před instalací jazykové sady musíte nainstalovat rozhraní .NET Framework.

 Počínaje [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], názvy balíčků podobu NDP <`version`>-KB <`number`>-x86-x64 - AllOS - <`culture`> .exe, kde `version` je číslo verze rozhraní .NET Framework `number` je Číslo článku znalostní báze Microsoft, a `culture` Určuje [země/oblast](#supported-languages). Příkladem jednoho z těchto balíčků je `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Názvy balíčků jsou uvedeny v [Distribuovatelné balíčky](#redistributable-packages) dříve v tomto článku.

 Pokud chcete nainstalovat jazykovou sadu pomocí offline instalační program rozhraní .NET Framework, musí být propojeny s vaší aplikace. Chcete-li například nasadit [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] offline instalační program s japonskou jazykovou sadou, použijte následující příkaz:

```
NDP451-KB2858728-x86-x64-AllOS-JPN.exe/q /norestart /ChainingPackage <ProductName>
```

 Nemáte řetězení jazykové sady, pokud používáte webový instalátor; Instalační program nainstaluje jazykovou sadu odpovídající nastavení MUI uživatele. Pokud chcete nainstalovat jiný jazyk, můžete použít `/LCID` můžete zadat jazykovou sadu.

 Úplný seznam možností příkazového řádku, najdete v článku [možnosti příkazového řádku](#command-line-options) oddílu.

### <a name="troubleshooting"></a>Poradce při potížích

#### <a name="return-codes"></a>Návratové kódy
 Následující tabulka uvádí nejběžnější návratové kódy pro distribuovatelného instalátoru rozhraní .NET Framework. Návratové kódy jsou stejné pro všechny verze instalačního programu. Odkazy na podrobné informace najdete v další části.

|Návratový kód|Popis|
|-----------------|-----------------|
|0|Instalace byla úspěšně dokončena.|
|1602|Instalace byla zrušena uživatelem.|
|1603|Při instalaci došlo k závažné chybě.|
|1641|K dokončení instalace je nutné provést restart. Tato zpráva znamená úspěch.|
|3010|K dokončení instalace je nutné provést restart. Tato zpráva znamená úspěch.|
|5100|Počítač uživatele nesplňuje požadavky systému.|

#### <a name="download-error-codes"></a>Kódy chyb stahování
 Viz následující obsah:

- [Kódy chyb služby Background Intelligent Transfer Service (BITS)](http://go.microsoft.com/fwlink/?LinkId=180946)

- [Kódy chyb monikeru URL:](http://go.microsoft.com/fwlink/?LinkId=180947)

- [Kódy chyb služby WinHttp](http://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Další kódy chyb
 Viz následující obsah:

- [Kódy chyb Instalační služby systému Windows](http://go.microsoft.com/fwlink/?LinkId=180949)

- [Výsledné kódy agenta služby Windows Update](http://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>Odinstalování rozhraní .NET Framework
 Počínaje [!INCLUDE[win8](../../../includes/win8-md.md)], můžete odinstalovat [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo jeden z jeho verze s použitím **Windows zapnout nebo vypnout funkce** v Ovládacích panelech. Ve starších verzích Windows, můžete odinstalovat [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo jeden z jeho verze s použitím **přidat nebo odebrat programy** v Ovládacích panelech.

> [!IMPORTANT]
> Pro Windows 7 a starších operačních systémech, odinstalace [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 nebo 4.7.2 neobnovuje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] soubory a odinstalace [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] neobnovuje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] soubory. Pokud chcete přejít zpátky na starší verzi, nainstalujte ho a všechny aktualizace.

## <a name="appendix"></a>Příloha

### <a name="command-line-options"></a>Možnosti příkazového řádku
 V následující tabulce jsou uvedeny možnosti, které můžete zahrnout při řetězení [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] distribuovatelná součást k instalaci vaší aplikace.

|Možnost|Popis|
|------------|-----------------|
|**/ CEIPConsent**|Přepíše výchozí chování a odešle anonymní zpětné vazby společnosti Microsoft pro zlepšení průběhu budoucích nasazení. Tato možnost se dá použít jenom v případě, že instalační program zobrazí výzvu k souhlasu a uživatel udělí oprávnění Odeslat anonymní zpětnou vazbu společnosti Microsoft.|
|**chainingpackage** `packageName`|Určuje název spustitelného souboru, který provádí řetězení. Tyto informace jsou odeslány společnosti Microsoft jako zpětná vazba k vylepšení budoucích nasazení prostředí.<br /><br /> Pokud název balíčku obsahuje mezery, použijte uvozovky jako oddělovače; Příklad: **chainingpackage "Lucerne Publishing"**. Příklad řetězeného balíčku naleznete v tématu [získávání informací o průběhu z instalačního balíčku](http://go.microsoft.com/fwlink/?LinkId=181926) v knihovně MSDN.|
|**/ LCID**  `LCID`<br /><br /> kde `LCID` Určuje identifikátor národního prostředí (viz [podporované jazyky](#supported-languages))|Nainstaluje jazykové sady určené pomocí `LCID` a vynutí zobrazení uživatelského rozhraní, který má být zobrazen v daném jazyce, není-li nastaven tichý režim.<br /><br /> U webového instalátoru tato možnost řetězí – instaluje jazykový balíček z webu. **Poznámka:** tuto možnost použijte pouze s webovým instalátorem.|
|**/ log** `file`&#124; `folder`|Určuje umístění souboru protokolu. Výchozí hodnota je dočasná složka pro proces a výchozí název souboru je založen na balíčku. Pokud je přípona .txt, vytvoří se textový protokol je vytvořen. Pokud zadáte jiné nebo žádné rozšíření, je vytvořen protokol ve formátu HTML.|
|**/msioptions**|Určuje možnosti, které mají být předány položkám .msi a .msp; Příklad: `/msioptions "PROPERTY1='Value'"`.|
|**/ norestart /**|Zabrání Instalačnímu programu v automatickém restartování. Pokud použijete tuto možnost, řetězená aplikace musí zachytit návratový kód a zpracovat restartování (viz [získávání informací o průběhu z instalačního balíčku](http://go.microsoft.com/fwlink/?LinkId=179606) v knihovně MSDN).|
|**/passive**|Nastaví pasivní režim. Zobrazí indikátor průběhu označuje, že v průběhu instalace, ale nezobrazí žádné chybové zprávy nebo výzvy uživateli. V tomto režimu při řetězení instalačního programu, musí řetězený balíček zpracovat [návratové kódy](#return-codes).|
|**/pipe**|Vytvoří komunikační kanál, který umožní řetězenému balíčku získat průběh.|
|**/ promptrestart**|Pouze pasivní režim, pokud instalační program vyžaduje restartování, vyzve uživatele. Tato možnost vyžaduje zásah uživatele, pokud je vyžadováno restartování.|
|**/q**|Nastaví tichý režim.|
|**/ repair**|Spustí funkci opravení.|
|**/serialdownload**|Vynutí spuštění instalace až po stažení balíčku.|
|**/showfinalerror**|Nastaví pasivní režim. Zobrazí chyby pouze v případě, instalace neproběhne úspěšně. Tato možnost vyžaduje zásah uživatele, pokud není instalace úspěšná.|
|**/showrmui**|Použít pouze s **/passive** možnost. Zobrazí okno se zprávou, která vyzve uživatele k ukončení aplikací rozhraní .NET Framework, které jsou aktuálně spuštěny. Toto okno se zprávou se chová stejně v pasivním a nepasivním režimu.|
|**/ uninstall**|Odinstalování rozhraní .NET Framework, distribuovatelné součásti.|

### <a name="supported-languages"></a>Podporované jazyky
Následující tabulka uvádí jazykové sady rozhraní .NET Framework, které jsou k dispozici pro [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho verze.

|LCID|Jazyk – země/oblast|Jazyková verze|
|----------|--------------------------------|-------------|
|1025|Arabština – Saúdská Arábie|ar|
|1028|Tradiční čínština|zh-Hant|
|1029|Čeština|cs|
|1030|Dánština|da|
|1031|Německo – němčina|de|
|1032|Řečtina|El|
|1035|Finština|Fi|
|1036|Francouzština-Francie|FR|
|1037|Hebrejština|mu|
|1038|Maďarština|HU|
|1040|Italština – Itálie|To|
|1041|Japonština|Japonsko|
|1042|Korejština|Ko|
|1043|Holandština – Nizozemsko|NL|
|1044|Norština (Bokmal)|Ne|
|1045|Polština|PL|
|1046|Portugalština – Brazílie|pt-BR|
|1049|Ruština|RU|
|1053|Švédština|sv|
|1055|Turečtina|tr|
|2052|Zjednodušená čínština|zh-Hans|
|2070|Portugalština – Portugalsko|pt-PT|
|3082|Španělština – Španělsko (mezinárodní řazení)|ES|

## <a name="see-also"></a>Viz také:
 [Příručka nasazení pro administrátory](../../../docs/framework/deployment/guide-for-administrators.md)  
 [Požadavky na systém](../../../docs/framework/get-started/system-requirements.md)  
 [Instalace rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md)  
 [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
 [Omezení restartů systému při instalaci rozhraní .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)  
 [Postupy: Získání procesu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
