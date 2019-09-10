---
title: Průvodce nasazením .NET Framework pro vývojáře
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dd7bac8c0cb14421016efad60a7ec0d672e5622
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854019"
---
# <a name="net-framework-deployment-guide-for-developers"></a>Průvodce nasazením .NET Framework pro vývojáře
Toto téma poskytuje informace pro vývojáře, kteří chtějí nainstalovat jakoukoli verzi .NET Framework z .NET Framework 4,5 na [!INCLUDE[net_current](../../../includes/net-current-version.md)] s jejich aplikacemi.

Odkazy ke stažení najdete v části [redistribuovatelné balíčky](#redistributable-packages). Distribuovatelné balíčky a jazykové sady můžete také stáhnout z těchto stránek služby Stažení softwaru společnosti Microsoft:

- .NET Framework 4,8 pro všechny operační systémy ([Webová instalační služba](http://go.microsoft.com/fwlink/?LinkId=2085155) nebo [offline instalační program](https://go.microsoft.com/fwlink/?linkid=2088631))

- .NET Framework 4.7.2 pro všechny operační systémy ([Webová instalační služba](https://go.microsoft.com/fwlink/?LinkId=863262) nebo [offline instalační program](https://go.microsoft.com/fwlink/p/?LinkId=863265))

- .NET Framework 4.7.1 pro všechny operační systémy ([Webová instalační služba](https://go.microsoft.com/fwlink/?LinkId=852095) nebo [offline instalační program](https://go.microsoft.com/fwlink/p/?LinkId=852107))

- .NET Framework 4,7 pro všechny operační systémy ([Webová instalační služba](https://go.microsoft.com/fwlink/?LinkId=825299) nebo [offline instalační program](https://go.microsoft.com/fwlink/p/?LinkId=825303))

- .NET Framework 4.6.2 pro všechny operační systémy ([Webová instalační služba](https://go.microsoft.com/fwlink/?LinkId=780597) nebo [offline instalační program](https://go.microsoft.com/fwlink/p/?LinkId=780601))

- .NET Framework 4.6.1 pro všechny operační systémy ([Webová instalační služba](https://go.microsoft.com/fwlink/?LinkId=671729) nebo [offline instalační program](https://go.microsoft.com/fwlink/p/?LinkId=671744))

- .NET Framework 4,6 pro všechny operační systémy ([Webová instalační služba](https://go.microsoft.com/fwlink/?LinkId=528222) nebo [offline instalační program](https://go.microsoft.com/fwlink/p/?LinkId=528232))

- .NET Framework 4.5.2 pro všechny operační systémy ([Webová instalační služba](https://go.microsoft.com/fwlink/p/?LinkId=397703) nebo [offline instalační program](https://go.microsoft.com/fwlink/p/?LinkId=397706))

- .NET Framework 4.5.1 pro všechny operační systémy ([Webová instalační služba](https://go.microsoft.com/fwlink/p/?LinkId=310158) nebo [offline instalační program](https://go.microsoft.com/fwlink/p/?LinkId=310159))

- [.NET Framework 4,5](https://go.microsoft.com/fwlink/p/?LinkId=245484)

 Důležité poznámky:

> [!NOTE]
> Fráze ".NET Framework 4,5 a verze jejího bodu" odkazuje na .NET Framework 4,5 a všechny novější verze.

- Verze .NET Framework z .NET Framework 4.5.1 prostřednictvím [!INCLUDE[net_current](../../../includes/net-current-version.md)] jsou místní aktualizace .NET Framework 4,5, což znamená, že používají stejnou verzi modulu runtime, ale verze sestavení jsou aktualizované a obsahují nové typy a členy.

- .NET Framework 4,5 a jeho vydání bodů jsou postupně postaveny na .NET Framework 4. Při instalaci .NET Framework 4,5 nebo jeho vydání v systému, který má nainstalovaný .NET Framework 4, se sestavení verze 4 nahrazují novějšími verzemi.

- Pokud v aplikaci odkazujete na [balíček pro vzdálenou](../get-started/the-net-framework-and-out-of-band-releases.md) správu Microsoft, sestavení bude součástí balíčku aplikace.

- Pro instalaci .NET Framework 4,5 a jeho verzí musíte mít oprávnění správce.

- .NET Framework 4,5 je součástí [!INCLUDE[win8](../../../includes/win8-md.md)] a [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], takže je nemusíte nasazovat do vaší aplikace v těchto operačních systémech. Podobně platí, že .NET Framework 4.5.1 je [!INCLUDE[win81](../../../includes/win81-md.md)] součástí systému a Windows Server 2012 R2. .NET Framework 4.5.2 není součástí žádného operačního systému. .NET Framework 4,6 je součástí Windows 10, aktualizace .NET Framework 4.6.1 je součástí Windows 10 listopad Update a .NET Framework 4.6.2 je součástí aktualizace Windows 10 pro výročí.  .NET Framework 4,7 je součástí Windows 10 Creators Update, .NET Framework 4.7.1 je součástí Windows 10 Creators Updates a .NET Framework 4.7.2 je součástí Windows 10 říjen 2018 Update a Windows 10. dubna 2018 Update. .NET Framework 4,8 je součástí aktualizace Windows 10. května 2019. Úplný seznam požadavků na hardware a software najdete v tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).

- Počínaje .NET Framework 4,5 mohou uživatelé zobrazit seznam spuštěných .NET Framework aplikací během instalace a snadno je zavřít. To může zabránit restartování systému způsobenému instalací .NET Framework. Viz [snížení počtu restartování systému](../../../docs/framework/deployment/reducing-system-restarts.md).

- Odinstalování .NET Framework 4,5 nebo některé z jeho vydaných verzí také odebere již existující soubory .NET Framework 4. Pokud se chcete vrátit na .NET Framework 4, je nutné ji znovu nainstalovat a všechny její aktualizace. (Viz [instalace .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100)).)

- Distribuovatelný balíček .NET Framework 4,5 byl od 9. října 2012 aktualizován, aby opravil problém týkající se nesprávného časového razítka v digitálním certifikátu, což způsobilo, že digitální podpis u souborů vytvořených a podepsaných společností Microsoft vyprší předčasně. Pokud jste dříve nainstalovali balíček .NET Framework 4,5 Redistributable, který je vydaný 16. srpna 2012, doporučujeme, abyste aktualizovali kopii pomocí nejnovější distribuovatelné verze z webu [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=245484). Další informace o tomto problému najdete v článku [Microsoft Security advisor 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655).

Informace o tom, jak může správce systému nasadit .NET Framework a jeho systémové závislosti v síti, najdete v tématu [Průvodce nasazením pro správce](../../../docs/framework/deployment/guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Možnosti nasazení pro vaši aplikaci

Až budete připraveni k publikování aplikace na webový server nebo jiné centralizované místo, aby je uživatelé mohli nainstalovat, můžete si vybrat z několika metod nasazení. Některé z nich jsou k dispozici v aplikaci Visual Studio. Následující tabulka uvádí možnosti nasazení pro vaši aplikaci a určuje .NET Framework Distribuovatelný balíček, který podporuje jednotlivé možnosti. Kromě toho můžete napsat vlastní instalační program pro vaši aplikaci. Další informace najdete v části [řetězení instalace .NET Framework k instalačnímu programu vaší aplikace](#chaining).

|Strategie nasazení pro vaši aplikaci|Dostupné metody nasazení|.NET Framework distribuovatelné pro použití|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Instalace z webu|- [InstallAware](#installaware-deployment)<br />- [Instalací](#installshield-deployment)<br />- [Sada nástrojů WiX](#wix)<br />- [Ruční instalace](#installing_manually)|[Webová instalační služba](#redistributable-packages)|
|Nainstalovat z disku|- [InstallAware](#installaware-deployment)<br />- [Instalací](#installshield-deployment)<br />- [Sada nástrojů WiX](#wix)<br />- [Ruční instalace](#installing_manually)|[Offline instalační program](#redistributable-packages)|
|Instalace z místní sítě (pro podnikové aplikace)|- [ClickOnce](#clickonce-deployment)|Buď [webový instalační program](#redistributable-packages) (omezení viz [ClickOnce](#clickonce-deployment) ) nebo [instalační program v režimu offline](#redistributable-packages)|

## <a name="redistributable-packages"></a>Distribuovatelné balíčky

.NET Framework je k dispozici ve dvou redistribuovatelných balíčcích: Webová instalační služba (zaváděcí nástroj) a instalační program v režimu offline (samostatný Distribuovatelný). Následující tabulka porovnává dva balíčky.

||Webová instalační služba|Offline instalační program|
|-|-------------------|-----------------------|
|Stáhnout soubor|.NET Framework 4,8: <br/>[ndp48-web.exe](https://go.microsoft.com/fwlink/?LinkId=2085155)<br/><br/>.NET Framework 4.7.2: <br/>[NDP472-KB4054531-Web.exe](https://go.microsoft.com/fwlink/?LinkId=863262)<br/><br/>.NET Framework 4.7.1: <br/>[NDP471-KB4033344-Web.exe](https://go.microsoft.com/fwlink/?LinkId=852092)<br/><br/>.NET Framework 4,7: <br />[NDP47-KB3186500-Web.exe](https://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />.NET Framework 4.6.2: <br />[NDP462-KB3151802-Web.exe](https://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> .NET Framework 4.6.1:<br />[NDP461-KB3102438-Web.exe](https://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> .NET Framework 4,6:<br />[NDP46-KB3045560-Web.exe](https://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901954-Web.exe](https://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> .NET Framework 4.5.1: <br />[NDP451-KB2859818-Web.exe](https://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> .NET Framework 4,5: <br />[dotNetFx45_Full_setup.exe](https://go.microsoft.com/fwlink/?LinkId=225704)|.NET Framework 4,8: <br/>[NDP48-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?linkid=2088631)<br/><br/>.NET Framework 4.7.2: <br/>[NDP472-KB4054530-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=863265)<br/><br/>.NET Framework 4.7.1: <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />.NET Framework 4,7: <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />.NET Framework 4.6.2: <br />[NDP462-KB3151800-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> .NET Framework 4.6.1: <br />[NDP461-KB3102436-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> .NET Framework 4,6: <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> .NET Framework 4.5.2: <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> .NET Framework 4.5.1: <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> .NET Framework 4,5: <br />[dotNetFx45_Full_x86_x64.exe](https://go.microsoft.com/fwlink/?LinkId=225702)|
|Vyžaduje se připojení k Internetu?|Ano|Ne|
|Velikost stahování|Menší (zahrnuje instalační program jenom pro cílovou platformu) *|Větší|
|Jazykové sady|Zahrnuté * *|Musí se [instalovat samostatně](#chain_langpack), pokud nepoužijete balíček, který cílí na všechny operační systémy.|
|Metoda nasazení|Podporuje všechny metody:<br /><br />- [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [Instalací](#installshield-deployment)<br />- [Instalační služba systému Windows XML (WiX)](#wix)<br />- [Ruční instalace](#installing_manually)<br />- [Vlastní nastavení (zřetězení)](#chaining)|Podporuje všechny metody:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [Instalací](#installshield-deployment)<br />- [Instalační služba systému Windows XML (WiX)](#wix)<br />- [Ruční instalace](#installing_manually)<br />- [Vlastní nastavení (zřetězení)](#chaining)|
|Umístění pro stažení pro nasazení ClickOnce|Stažení softwaru společnosti Microsoft:<br /><br /> - [.NET Framework 4,8](https://go.microsoft.com/fwlink/?LinkId=2085155) <br/> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863262) <br/> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [.NET Framework 4,7](https://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780596)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671728)<br />- [.NET Framework 4,6](https://go.microsoft.com/fwlink/?LinkId=528222)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/?LinkId=397703)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [.NET Framework 4,5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|Váš vlastní server nebo stažení softwaru společnosti Microsoft:<br /><br /> - [.NET Framework 4,8](https://go.microsoft.com/fwlink/?linkid=2088631)<br /> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863265)<br /> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [.NET Framework 4,7](https://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780600)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671743)<br />- [.NET Framework 4,6](https://go.microsoft.com/fwlink/?LinkId=528232)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [.NET Framework 4,5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|

\*Instalační program v režimu offline je větší, protože obsahuje komponenty pro všechny cílové platformy. Po dokončení instalace operační systém Windows ukládá pouze instalační službu, která byla použita. Pokud je po instalaci odstraněn instalační program v režimu offline, je místo na disku stejné jako používané webovým instalačním programem. Pokud nástroj, který použijete (například [InstallAware](#installaware-deployment) nebo [InstallShield](#installshield-deployment)) k vytvoření instalačního programu vaší aplikace, poskytuje složku instalačního souboru, která se odebere po instalaci, bude možné automaticky odstranit instalační program v režimu offline tím, že ho umístíte do instalačního programu. složky.

\*\*Pokud používáte webovou Instalační službu s vlastním instalačním programem, můžete použít výchozí nastavení jazyka na základě nastavení MUI (Multilingual User Interface) uživatele nebo zadat jinou jazykovou sadu pomocí `/LCID` možnosti na příkazovém řádku. Příklady najdete v části [řetězení pomocí výchozího uživatelského rozhraní .NET Framework](#chaining_default) .

## <a name="deployment-methods"></a>Metody nasazení

 K dispozici jsou čtyři metody nasazení:

- Můžete nastavit závislost na .NET Framework. V instalaci vaší aplikace můžete určit .NET Framework, a to pomocí jedné z těchto metod:

  - Použití [ClickOnce nasazení](#clickonce-deployment) (k dispozici v aplikaci Visual Studio)

  - Vytvoření [projektu InstallAware](#installaware-deployment) (edice Free dostupná pro uživatele sady Visual Studio)

  - Vytvoření [projektu InstallShield](#installshield-deployment) (k dispozici v aplikaci Visual Studio)

  - Použití sady [nástrojů Instalační služba systému Windows XML (WiX)](#wix)

- Můžete požádat uživatele o [ruční instalaci .NET Framework](#installing_manually).

- V instalačním programu aplikace můžete zřetězit (zahrnout) proces instalace .NET Framework a rozhodnout se, jak chcete .NET Framework prostředí instalace:

  - [Použijte výchozí uživatelské rozhraní](#chaining_default). Umožněte instalačnímu programu .NET Framework poskytnout prostředí pro instalaci.

  - [Přizpůsobte uživatelské rozhraní](#chaining_custom) tak, aby obsahovalo jednotné prostředí instalace a monitoroval průběh instalace .NET Framework.

Tyto metody nasazení jsou podrobněji popsány v následujících částech.

## <a name="setting-a-dependency-on-the-net-framework"></a>Nastavení závislosti na .NET Framework

Pokud nasadíte aplikaci pomocí technologie ClickOnce, InstallAware, InstallShield nebo WiX, můžete přidat závislost na .NET Framework, aby ji bylo možné nainstalovat jako součást aplikace.

### <a name="clickonce-deployment"></a>ClickOnce – nasazení

Nasazení ClickOnce je k dispozici pro projekty, které jsou vytvořeny pomocí C#Visual Basic a vizuálu, ale nejsou k dispozici pro vizuál C++.

V aplikaci Visual Studio vyberte nasazení ClickOnce a přidejte závislost na .NET Framework:

1. Otevřete projekt aplikace, který chcete publikovat.

2. V Průzkumník řešení otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.

3. Vyberte podokno **publikování** .

4. Klikněte na tlačítko **požadavky** .

5. V dialogovém okně **požadavky** se ujistěte, že je zaškrtnuté políčko **vytvořit instalační program pro instalaci požadovaných součástí** .

6. V seznamu požadavků vyhledejte a vyberte verzi .NET Framework, kterou jste použili k sestavení projektu.

7. Zvolte možnost pro určení umístění zdroje pro požadované součásti a pak zvolte **OK**.

     Pokud zadáte adresu URL pro umístění pro stažení .NET Framework, můžete zadat web Microsoft Download Center nebo web, který vlastníte. Pokud Distribuovatelný balíček umísťujete na vlastní server, musí to být instalační program v režimu offline, nikoli Webová instalační služba. Odkaz na webovou Instalační službu můžete vytvořit pouze na webu Microsoft Download Center. Adresa URL může také určovat disk, na kterém je vaše vlastní aplikace distribuována.

8. V dialogovém okně **stránky vlastností** klikněte na **tlačítko OK**.

<a name="installaware"></a>

### <a name="installaware-deployment"></a>Nasazení InstallAware

InstallAware vytváří balíčky Windows App (APPX), Instalační služba systému Windows (MSI), nativního kódu (EXE) a App-V (Application Virtualization) z jednoho zdroje. Snadná instalace [libovolné verze .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) v nastavení, volitelně přizpůsobení instalace [úpravou výchozích skriptů](https://www.installaware.com/msicode.htm). Například InstallAware předběžně nainstaluje certifikáty do systému Windows 7 bez toho, aby se instalace .NET Framework 4,7 nezdařila. Další informace o InstallAware najdete na webu [InstallAware for Instalační služba systému Windows](https://www.installaware.com/) .

### <a name="installshield-deployment"></a>Nasazení InstallShield

V aplikaci Visual Studio vyberte nasazení InstallShield a přidejte závislost na .NET Framework:

1. V řádku nabídek sady Visual Studio vyberte možnost **soubor**, **Nový**, **projekt**.

2. V levém podokně dialogového okna **Nový projekt** vyberte možnost **ostatní typy projektů**, **nastavení a nasazení**, **InstallShield Le**.

3. Do pole **název** zadejte název projektu a klikněte na **tlačítko OK**.

4. Pokud vytváříte projekt instalace a nasazení poprvé, vyberte **Přejít na InstallShield** nebo **Povolit InstallShield unedition** , aby bylo možné stáhnout InstallShield s omezením pro vaši verzi Microsoft Visual Studio. Restartujte sadu Visual Studio.

5. Chcete-li přidat výstup projektu, klikněte na průvodce **pomocníkem projektu** a vyberte možnost **soubory aplikace** . Pomocí tohoto průvodce můžete nakonfigurovat další atributy projektu.

6. Pokračujte na **požadavky na instalaci** a vyberte operační systémy a verzi .NET Framework, kterou chcete nainstalovat.

7. Otevřete místní nabídku pro projekt instalace a vyberte možnost **sestavit**.

<a name="wix"></a>

### <a name="windows-installer-xml-wix-deployment"></a>Nasazení Instalační služba systému Windows XML (WiX)

Sada nástrojů Instalační služba systému Windows XML (WiX) vytváří instalační balíčky Windows ze zdrojového kódu XML. WiX podporuje prostředí příkazového řádku, které lze integrovat do procesů sestavení pro sestavení instalačních balíčků MSI a MSM. Pomocí WiX můžete [určit .NET Framework jako předpoklad](http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html), nebo [vytvořit řetěz](http://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) , který plně řídí možnosti nasazení .NET Framework. Další informace o WiX najdete na webu sady [nástrojů pro instalační služba systému Windows XML (WiX)](http://wixtoolset.org/) .

<a name="installing_manually"></a>

## <a name="installing-the-net-framework-manually"></a>Ruční instalace .NET Framework

V některých situacích může být nepraktické automaticky instalovat .NET Framework s vaší aplikací. V takovém případě mohou uživatelé nainstalovat .NET Framework sami. Distribuovatelný balíček je k dispozici ve [dvou balíčcích](#redistributable-packages). V procesu instalace poskytněte pokyny, jak by uživatelé měli .NET Framework najít a nainstalovat.

<a name="chaining"></a>

## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Řetězení instalace .NET Framework k instalačnímu programu vaší aplikace

Pokud vytváříte vlastní instalační program pro vaši aplikaci, můžete v procesu instalace vaší aplikace zřetězit (zahrnout) .NET Framework proces instalace. Řetězení poskytuje dvě možnosti uživatelského rozhraní pro instalaci .NET Framework:

- Použijte výchozí uživatelské rozhraní poskytnuté instalačním programem .NET Framework.

- Vytvořte vlastní uživatelské rozhraní pro .NET Framework instalaci kvůli konzistenci s instalačním programem vaší aplikace.

Obě metody umožňují použít buď webový instalátor, nebo instalační program v režimu offline. Každý balíček má své výhody:

- Použijete-li webový instalační program, proces instalace .NET Framework určí, který instalační balíček je požadován, a stáhne a nainstaluje pouze tento balíček z webu.

- Pokud používáte offline instalační program, můžete zahrnout úplnou sadu .NET Framework instalačních balíčků s vašimi distribučními médii, aby uživatelé nemuseli během instalace stahovat žádné další soubory z webu.

<a name="chaining_default"></a>

### <a name="chaining-by-using-the-default-net-framework-ui"></a>Řetězení pomocí výchozího uživatelského rozhraní .NET Framework

K tichému zřetězení procesu instalace .NET Framework a umožnění, aby instalační program .NET Framework poskytoval uživatelské rozhraní, přidejte do instalačního programu následující příkaz:

`<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>`

Pokud je například spustitelný program contoso. exe a chcete tiše nainstalovat .NET Framework 4,5 offline Distribuovatelný balíček, použijte příkaz:

`dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso`

K přizpůsobení instalace můžete použít další možnosti příkazového řádku. Příklad:

- Chcete-li uživatelům umožnit, aby zavřeli spuštěné aplikace .NET Framework pro minimalizaci restartování systému, nastavte pasivní režim a `/showrmui` použijte možnost následujícím způsobem:

    `dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso`

     Tento příkaz umožňuje správci restartování zobrazit okno se zprávou, které uživatelům umožňuje zavřít .NET Framework aplikace před instalací .NET Framework.

- Pokud používáte webovou Instalační službu, můžete použít `/LCID` možnost k zadání jazykové sady. Chcete-li například zřetězit webový instalátor .NET Framework 4,5 k instalačnímu programu společnosti Contoso a nainstalovat japonskou jazykovou sadu, přidejte do procesu instalace aplikace následující příkaz:

    `dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041`

     Pokud tuto `/LCID` možnost vynecháte, instalační program nainstaluje jazykovou sadu, která bude odpovídat nastavení MUI uživatele.

    > [!NOTE]
    > Různé jazykové sady mohou mít odlišná data vydání. Pokud zadaná jazyková sada není k dispozici ve službě Stažení softwaru, instalační program nainstaluje .NET Framework bez jazykové sady. Pokud je již .NET Framework v počítači uživatele nainstalován, instalační program nainstaluje pouze jazykovou sadu.

Úplný seznam možností najdete v části [Možnosti příkazového řádku](#command-line-options) .

Společné návratové kódy naleznete v části [návratové kódy](#return-codes) .

<a name="chaining_custom"></a>

### <a name="chaining-by-using-a-custom-ui"></a>Řetězení pomocí vlastního uživatelského rozhraní

Pokud máte vlastní instalační balíček, můžete chtít spustit tichou instalaci a sledovat nastavení .NET Framework a zároveň zobrazit průběh instalace. Pokud se jedná o tento případ, ujistěte se, že váš kód pokrývá následující:

- Vyhledejte [.NET Framework požadavky na hardware a software](../../../docs/framework/get-started/system-requirements.md).

- [Zjišťuje](#detect_net) , zda je v počítači uživatele již nainstalována správná verze .NET Framework.

    > [!IMPORTANT]
    > Při určování, jestli je už nainstalovaná správná verze .NET Framework, byste měli ověřit, jestli je nainstalovaná vaše cílová verze *nebo* novější verze, a to bez ohledu na to, jestli je vaše cílová verze nainstalovaná. Jinými slovy, měli byste vyhodnotit, jestli je klíč verze, který načtete z registru, větší nebo roven klíči verze cílové verze, a to *bez* ohledu na to, jestli se rovná klíč verze cílové verze.

- [Zjišťuje](#detecting-the-language-packs) , zda jsou v počítači uživatele již nainstalovány jazykové sady.

- Chcete-li řídit nasazení, tiche spuštění a sledování procesu instalace .NET Framework (viz [postup: Získejte průběh z instalačního programu](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).NET Framework 4,5).

- Pokud nasazujete offline instalační program, [řetězte si jazykové sady samostatně](#chain_langpack).

- Přizpůsobení nasazení pomocí [možností příkazového řádku](#command-line-options) Pokud například provádíte zřetězení .NET Framework webový instalátor, ale chcete přepsat výchozí jazykovou sadu, použijte `/LCID` možnost, jak je popsáno v předchozí části.

- [Řešení potíží](#troubleshooting).

<a name="detect_net"></a>

### <a name="detecting-the-net-framework"></a>Zjišťování .NET Framework

Instalační program .NET Framework zapisuje klíče registru po úspěšném dokončení instalace. Můžete otestovat, jestli je nainstalovaná .NET Framework 4,5 nebo novější, kontrolou `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` složky v registru `DWORD` pro hodnotu s názvem `Release`. (Všimněte si, že ".NET Framework Setup" nezačíná tečkou.) Existence tohoto klíče indikuje, že na tomto počítači je nainstalovaná .NET Framework 4,5 nebo novější verze. Hodnota `Release` označuje, která verze .NET Framework je nainstalována.

> [!IMPORTANT]
> Při pokusu o zjištění, zda je k dispozici konkrétní verze, byste měli zjistit hodnotu, která je **větší nebo rovna** hodnotě klíčového slova verze.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|Version|Hodnota DWORD verze|
|-------------|--------------------------------|
|Aktualizace .NET Framework 4,8 nainstalované ve Windows 10 Květen 2019|528040|
|Aktualizace .NET Framework 4,8 nainstalovaná ve všech jiných verzích operačního systému než Windows 10, které by byly 2019|528049|
|.NET Framework 4.7.2 nainstalované ve Windows 10. dubna 2018 Update a na Windows serveru, verze 1803|461808|
|.NET Framework 4.7.2 nainstalované na všech verzích operačních systémů, které jsou jiné než Windows 10, duben 2018 Update a Windows Server verze 1803. To zahrnuje aktualizaci Windows 10 říjen 2018 Update. |461814|
|.NET Framework 4.7.1 nainstalovaná ve Windows 10 je aktualizace Creators Update a Windows Server verze 1709.|461308|
|.NET Framework 4.7.1 nainstalované na všech verzích operačních systémů, které jsou jiné než Windows 10, patří tvůrci aktualizace a Windows Server verze 1709.|461310|
|Aktualizace .NET Framework 4,7 nainstalované ve Windows 10 Creators Update|460798|
|Verze .NET Framework 4,7 nainstalovaná ve všech jiných verzích operačních systémů než Windows 10 Creators Update|460805|
|.NET Framework 4.6.2 nainstalované na Windows 10 výročí Edition a Windows Server 2016|394802|
|.NET Framework 4.6.2 nainstalované na všech jiných verzích operačních systémů než Windows 10 a Windows Server 2016|394806|
|Aktualizace .NET Framework 4.6.1 nainstalovaná ve Windows 10 listopadu Update|394254|
|.NET Framework 4.6.1 nainstalovaná ve všech jiných verzích operačních systémů než Windows 10 listopad Update|394271|
|.NET Framework 4,6 nainstalované ve Windows 10|393295|
|.NET Framework 4,6 nainstalované na všech jiných verzích operačních systémů než Windows 10|393297|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.5.1 nainstalované se [!INCLUDE[win81](../../../includes/win81-md.md)] systémem nebo Windows Server 2012 R2|378675|
|Nainstalovaná verze .NET Framework [!INCLUDE[win8](../../../includes/win8-md.md)]4.5.1 v systému, Windows 7|378758|
|.NET Framework 4.5|378389|

### <a name="detecting-the-language-packs"></a>Zjišťují se jazykové sady.

Můžete otestovat, jestli je konkrétní jazyková sada nainstalovaná, kontrolou složky HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* v registru pro hodnotu DWORD s názvem `Release`. (Všimněte si, že ".NET Framework Setup" nezačíná tečkou.) *LCID* Určuje identifikátor národního prostředí; Seznam těchto seznamů najdete v části [podporované jazyky](#supported-languages) .

Chcete-li například zjistit, zda je nainstalována úplná japonská jazyková sada (LCID = 1041), načtěte z registru následující pojmenovanou hodnotu:

| | |
|-|-|
| Key | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041 |
| Name | Vydaná verze |
| type | DWORD |

Pokud chcete zjistit, jestli je nainstalovaná konečná verze jazykové sady pro konkrétní verzi .NET Framework od 4,5 do 4.7.2, zkontrolujte hodnotu klíče verze DWORD popsanou v předchozí části a zjistěte [.NET Framework ](#detect_net).

<a name="chain_langpack"></a>

### <a name="chaining-the-language-packs-to-your-app-setup"></a>Řetězení jazykových sad k nastavení aplikace

.NET Framework poskytuje sadu samostatných spustitelných souborů jazykové sady, které obsahují lokalizované prostředky pro konkrétní jazykové verze. Jazykové sady jsou k dispozici na webu Microsoft Download Center:

- [Jazykové sady .NET Framework 4,8](https://go.microsoft.com/fwlink/p/?LinkId=2086170)

- [Jazykové sady .NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863275)

- [Jazykové sady .NET Framework 4.7.1](https://go.microsoft.com/fwlink/p/?LinkId=852090)

- [Jazykové sady .NET Framework 4,7](https://go.microsoft.com/fwlink/p/?LinkId=825306)

- [Jazykové sady .NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?LinkId=780604)

- [.NET Framework jazykové sady 4.6.1](https://go.microsoft.com/fwlink/p/?LinkId=671747)

- [Jazykové sady .NET Framework 4,6](https://go.microsoft.com/fwlink/p/?LinkId=528314)

- [.NET Framework jazykové sady 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397701)

- [Jazykové sady .NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=322101)

- [Jazykové sady .NET Framework 4,5](https://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> Jazykové sady neobsahují .NET Framework komponenty, které jsou nutné ke spuštění aplikace. před instalací jazykové sady je nutné nainstalovat .NET Framework pomocí webového nebo offline instalačního programu.

Počínaje .NET Framework 4.5.1 mají názvy balíčků`version`formu NDP < >-KB <`number`>-x86-x64-povolit-<`culture`>. exe, kde `version` je číslo verze .NET Framework `number` . Číslo článku znalostní báze Microsoft Knowledge Base `culture` a určuje [zemi nebo oblast](#supported-languages). Příkladem jednoho z těchto balíčků je `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Názvy balíčků jsou uvedené v části [Distribuovatelný balíčky](#redistributable-packages) výše v tomto článku.

Chcete-li nainstalovat jazykovou sadu pomocí instalačního programu .NET Framework v režimu offline, musíte ji zřetězit k instalaci vaší aplikace. Pokud například chcete nasadit instalační program pro .NET Framework 4.5.1 offline pomocí japonské jazykové sady, použijte následující příkaz:

`NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>`

Pokud používáte webovou Instalační službu, nemusíte zřetězit jazykové sady. Instalační program nainstaluje jazykovou sadu, která odpovídá nastavení MUI uživatele. Pokud chcete nainstalovat jiný jazyk, můžete použít `/LCID` možnost k zadání jazykové sady.

Úplný seznam možností příkazového řádku najdete v části [Možnosti příkazového řádku](#command-line-options) .

### <a name="troubleshooting"></a>Poradce při potížích

#### <a name="return-codes"></a>Návratové kódy

Následující tabulka uvádí nejběžnější návratové kódy pro .NET Framework Distribuovatelný instalační program. Návratové kódy jsou stejné pro všechny verze instalačního programu. Odkazy na podrobné informace naleznete v další části.

|Návratový kód|Popis|
|-----------------|-----------------|
|0|Instalace byla úspěšně dokončena.|
|1602|Instalace byla zrušena uživatelem.|
|1603|Při instalaci došlo k závažné chybě.|
|1641|K dokončení instalace je nutné provést restart. Tato zpráva znamená úspěch.|
|3010|K dokončení instalace je nutné provést restart. Tato zpráva znamená úspěch.|
|5100|Počítač uživatele nesplňuje požadavky systému.|

#### <a name="download-error-codes"></a>Kódy chyb stahování

Podívejte se na následující obsah:

- [Kódy chyb Background Intelligent Transfer Service (BITS)](https://go.microsoft.com/fwlink/?LinkId=180946)

- [Kódy chyb monikeru URL](https://go.microsoft.com/fwlink/?LinkId=180947)

- [Kódy chyb služby WinHttp](https://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Další kódy chyb

Podívejte se na následující obsah:

- [Kódy chyb Instalační služba systému Windows](https://go.microsoft.com/fwlink/?LinkId=180949)

- [web Windows Update kódy výsledků agenta](https://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>Odinstalace .NET Framework

Počínaje verzí můžete odinstalovat .NET Framework 4,5 nebo některou z jeho vydání bodů pomocí **Možnosti zapnout nebo vypnout funkce systému Windows** v Ovládacích panelech. [!INCLUDE[win8](../../../includes/win8-md.md)] Ve starších verzích Windows můžete odinstalovat .NET Framework 4,5 nebo některé z jeho vydání bodů pomocí ovládacího panelu **Přidat nebo odebrat programy** .

> [!IMPORTANT]
> V systémech Windows 7 a starších operačních systémech odinstalování .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 nebo 4,8 neobnoví .NET Framework 4,5 soubory a odinstaluje .NET Framework 4,5 neobnoví .NET Framework 4 soubory. Pokud se chcete vrátit na starší verzi, je nutné ji znovu nainstalovat a všechny její aktualizace.

## <a name="appendix"></a>Příloha

### <a name="command-line-options"></a>Možnosti příkazového řádku

V následující tabulce jsou uvedeny možnosti, které můžete zahrnout při zřetězení .NET Framework 4,5 distribuovat do instalačního programu aplikace.

|Možnost|Popis|
|------------|-----------------|
|**/CEIPConsent**|Přepíše výchozí chování a pošle anonymní zpětnou vazbu Microsoftu, aby vylepšil budoucí prostředí nasazení. Tuto možnost lze použít pouze v případě, že instalační program vyzve k zadání souhlasu a pokud uživatel udělí oprávnění k odeslání anonymní zpětné vazby společnosti Microsoft.|
|**/chainingpackage**`packageName`|Určuje název spustitelného souboru, který provádí řetězení. Tyto informace se odesílají společnosti Microsoft jako anonymní zpětná vazba, která pomáhá zlepšovat budoucí prostředí nasazení.<br /><br /> Pokud název balíčku obsahuje mezery, použijte dvojité uvozovky jako oddělovače. Příklad: **/chainingpackage "Lucerne Publishing"** . Příklad zřetězení balíčku najdete v tématu [získávání informací o průběhu z instalačního balíčku](https://go.microsoft.com/fwlink/?LinkId=181926) v knihovně MSDN.|
|**/LCID**  `LCID`<br /><br /> kde `LCID` Určuje identifikátor národního prostředí (viz [podporované jazyky](#supported-languages))|Nainstaluje jazykovou sadu určenou `LCID` v a vynutí zobrazení uživatelského rozhraní v tomto jazyce, není-li nastaven tichý režim.<br /><br /> Pro webovou Instalační službu tento řetěz možností – nainstaluje jazykový balíček z webu. **Poznámka:**  Tuto možnost použijte pouze s webovým instalačním programem.|
|**/log** `file` &#124;`folder`|Určuje umístění souboru protokolu. Výchozím nastavením je dočasná složka pro daný proces a výchozí název souboru je založen na balíčku. Je-li Přípona souboru. txt, je vytvořen textový protokol. Pokud zadáte jiné rozšíření nebo žádné rozšíření, vytvoří se protokol HTML.|
|**/msioptions**|Určuje možnosti, které se mají předat pro položky. msi a. msp; například: `/msioptions "PROPERTY1='Value'"`.|
|**/ norestart /**|Zabraňuje automatickému restartování instalačního programu. Použijete-li tuto možnost, musí zřetězená aplikace zachytit návratový kód a zpracovat restartování (viz část [získání informací o průběhu z instalačního balíčku](https://go.microsoft.com/fwlink/?LinkId=179606) v knihovně MSDN).|
|**/passive**|Nastaví pasivní režim. Zobrazí indikátor průběhu, který indikuje, že instalace probíhá, ale nezobrazuje žádné výzvy ani chybové zprávy pro uživatele. V tomto režimu, při zřetězení instalačního programu, musí zřetězení balíčku zpracovat [návratové kódy](#return-codes).|
|**/pipe**|Vytvoří komunikační kanál, který umožní zřetězení balíčku, aby se mohl získat průběh.|
|**/promptrestart**|Pouze pasivní režim, pokud instalační program vyžaduje restart, vyzve uživatele. Tato možnost vyžaduje zásah uživatele, pokud je vyžadováno restartování.|
|**/q**|Nastaví tichý režim.|
|**/ repair**|Aktivuje funkci opravy.|
|**/serialdownload**|Vynutí instalaci, aby se provedla až po stažení balíčku.|
|**/showfinalerror**|Nastaví pasivní režim. Zobrazí chyby pouze v případě, že instalace není úspěšná. Tato možnost vyžaduje zásah uživatele, pokud instalace není úspěšná.|
|**/showrmui**|Používá se pouze s možností **/passive** . Zobrazí okno se zprávou, která vyzývá uživatele, aby zavřeli .NET Framework aktuálně spuštěných aplikacích. Toto okno se zprávou se chová stejně jako v pasivním a nepasivním režimu.|
|**/Uninstall**|Odinstaluje .NET Framework redistributable.|

### <a name="supported-languages"></a>Podporované jazyky

V následující tabulce jsou uvedeny .NET Framework jazykové sady, které jsou k dispozici pro .NET Framework 4,5 a jejich verze.

|IDENTIFIKÁTORY|Jazyk – země/oblast|Jazyková verze|
|----------|--------------------------------|-------------|
|1025|Arabština – Saúdská Arábie|snížen|
|1028|Čínština – tradiční|zh – Hant|
|1029|Čeština|cs|
|1030|dánština|da|
|1031|Němčina – Německo|&|
|1032|Řečtina|el|
|1035|Finština|fi|
|1036|Francouzština – Francie|fr|
|1037|Hebrejština|uvede|
|1038|Maďarština|hu|
|1040|Italština – Itálie|její|
|1041|Japonština|dža|
|1042|Korejština|Ko|
|1043|Holandština – Nizozemsko|nl|
|1044|Norština (Bokmål)|Ne|
|1045|Polština|pl|
|1046|Portugalština – Brazílie|pt-BR|
|1049|Ruština|ru|
|1053|švédština|sv|
|1055|Turečtina|recenzent|
|2052|Čínština – zjednodušená|zh – Hans|
|2070|Portugalština – Portugalsko|pt-PT|
|3082|Španělština – Španělsko (moderní řazení)|jednomu|

## <a name="see-also"></a>Viz také:

- [Příručka nasazení pro administrátory](../../../docs/framework/deployment/guide-for-administrators.md)
- [Požadavky na systém](../../../docs/framework/get-started/system-requirements.md)
- [Instalace .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md)
- [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
- [Omezení restartů systému při instalaci rozhraní .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)
- [Postupy: Získání průběhu z instalačního programu .NET Framework 4,5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
