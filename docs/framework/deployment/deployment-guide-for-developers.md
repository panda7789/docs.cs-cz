---
title: Průvodce nasazením .NET Framework pro vývojáře
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
ms.openlocfilehash: 26c168040b0fa5e975e64a7518b0d0bf250c4711
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628121"
---
# <a name="net-framework-deployment-guide-for-developers"></a>Průvodce nasazením .NET Framework pro vývojáře
Toto téma poskytuje informace pro vývojáře, kteří chtějí nainstalovat jakoukoli verzi .NET Framework z .NET Framework 4,5 na [!INCLUDE[net_current](../../../includes/net-current-version.md)] s jejich aplikacemi.

Redistribuovatelné balíčky a jazykové sady pro .NET Framework můžete stáhnout ze stránek pro stažení:

- [.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Framework 4,7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4,6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

 Důležité poznámky:

- Verze .NET Framework z .NET Framework 4.5.1 prostřednictvím [!INCLUDE[net_current](../../../includes/net-current-version.md)] jsou místní aktualizace .NET Framework 4,5, což znamená, že používají stejnou verzi modulu runtime, ale aktualizované verze sestavení a zahrnují nové typy a členy.

- .NET Framework 4,5 a novější verze jsou postupně postaveny na .NET Framework 4. Při instalaci .NET Framework 4,5 nebo novějších verzí do systému, který má nainstalovaný .NET Framework 4, se sestavení verze 4 nahrazují novějšími verzemi.

- Pokud v aplikaci odkazujete na [balíček pro vzdálenou](../get-started/the-net-framework-and-out-of-band-releases.md) správu Microsoft, sestavení bude součástí balíčku aplikace.

- K instalaci .NET Framework 4,5 nebo novějších verzí musíte mít oprávnění správce.

- .NET Framework 4,5 je součástí systémů Windows 8 a Windows Server 2012, takže je nemusíte nasazovat do vaší aplikace v těchto operačních systémech. Podobně .NET Framework 4.5.1 je součástí Windows 8.1 a Windows Serveru 2012 R2. .NET Framework 4.5.2 není součástí žádného operačního systému. .NET Framework 4,6 je součástí Windows 10, aktualizace .NET Framework 4.6.1 je součástí Windows 10 listopad Update a .NET Framework 4.6.2 je součástí aktualizace Windows 10 pro výročí.  .NET Framework 4,7 je součástí Windows 10 Creators Update, .NET Framework 4.7.1 je součástí Windows 10 Creators Updates a .NET Framework 4.7.2 je součástí Windows 10 říjen 2018 Update a Windows 10. dubna 2018 Update. .NET Framework 4,8 je součástí aktualizace Windows 10. května 2019. Úplný seznam požadavků na hardware a software najdete v tématu [požadavky na systém](../get-started/system-requirements.md).

- Počínaje .NET Framework 4,5 mohou uživatelé zobrazit seznam spuštěných .NET Framework aplikací během instalace a snadno je zavřít. To může zabránit restartování systému způsobenému instalací .NET Framework. Viz [snížení počtu restartování systému](reducing-system-restarts.md).

- Odinstalace .NET Framework 4,5 nebo novějších verzí také odstraní existující soubory .NET Framework 4. Pokud se chcete vrátit na .NET Framework 4, je nutné ji znovu nainstalovat a všechny její aktualizace. Viz [instalace .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100)).

- Distribuovatelný balíček .NET Framework 4,5 byl od 9. října 2012 aktualizován, aby opravil problém týkající se nesprávného časového razítka v digitálním certifikátu, což způsobilo, že digitální podpis u souborů vytvořených a podepsaných společností Microsoft vyprší předčasně. Pokud jste dříve nainstalovali balíček .NET Framework 4,5 Redistributable, který je vydaný 16. srpna 2012, doporučujeme, abyste aktualizovali kopii pomocí nejnovější distribuovatelné stránky ze [stránky pro stažení .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/net45). Další informace o tomto problému najdete v článku [Microsoft Security advisor 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655).

Informace o tom, jak může správce systému nasadit .NET Framework a jeho systémové závislosti v síti, najdete v tématu [Průvodce nasazením pro správce](guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Možnosti nasazení pro vaši aplikaci

Až budete připraveni k publikování aplikace na webový server nebo jiné centralizované místo, aby je uživatelé mohli nainstalovat, můžete si vybrat z několika metod nasazení. Některé z nich jsou k dispozici v aplikaci Visual Studio. Následující tabulka uvádí možnosti nasazení pro vaši aplikaci a určuje .NET Framework Distribuovatelný balíček, který podporuje jednotlivé možnosti. Kromě toho můžete napsat vlastní instalační program pro vaši aplikaci. Další informace najdete v části [řetězení instalace .NET Framework k instalačnímu programu vaší aplikace](#chaining).

|Strategie nasazení pro vaši aplikaci|Dostupné metody nasazení|.NET Framework distribuovatelné pro použití|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Instalace z webu|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />[Sada nástrojů - WIX](#wix)<br />- [Ruční instalace](#installing_manually)|[Webová instalační služba](#redistributable-packages)|
|Nainstalovat z disku|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />[Sada nástrojů - WIX](#wix)<br />- [Ruční instalace](#installing_manually)|[Offline instalační program](#redistributable-packages)|
|Instalace z místní sítě (pro podnikové aplikace)|- [ClickOnce](#clickonce-deployment)|Buď [webový instalační program](#redistributable-packages) (omezení viz [ClickOnce](#clickonce-deployment) ) nebo [instalační program v režimu offline](#redistributable-packages)|

## <a name="redistributable-packages"></a>Distribuovatelné balíčky

.NET Framework je k dispozici ve dvou redistribuovatelných balíčcích: Webová instalační služba (zaváděcí nástroj) a instalační program v režimu offline (samostatný Distribuovatelný). Všechny soubory ke stažení .NET Framework jsou hostovány na [stránce pro stažení .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/). Následující tabulka porovnává tyto dva balíčky:

||Webová instalační služba|Offline instalační program|
|-|-------------------|-----------------------|
|Vyžaduje se připojení k Internetu?|Ano|Ne|
|Velikost stahování|Menší (zahrnuje instalační program jenom pro cílovou platformu) *|Větší|
|Jazykové sady|Zahrnuté * *|Musí se [instalovat samostatně](#chain_langpack), pokud nepoužijete balíček, který cílí na všechny operační systémy.|
|Metoda nasazení|Podporuje všechny metody:<br /><br />- [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />[XML - Instalační služba systému Windows (WiX)](#wix)<br />- [Ruční instalace](#installing_manually)<br />- [vlastní nastavení (zřetězení)](#chaining)|Podporuje všechny metody:<br /><br /> - [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />[XML - Instalační služba systému Windows (WiX)](#wix)<br />- [Ruční instalace](#installing_manually)<br />- [vlastní nastavení (zřetězení)](#chaining)|

\* instalační program offline je větší, protože obsahuje komponenty pro všechny cílové platformy. Po dokončení instalace operační systém Windows ukládá pouze instalační službu, která byla použita. Pokud je po instalaci odstraněn instalační program v režimu offline, je místo na disku stejné jako používané webovým instalačním programem. Pokud nástroj, který použijete (například [InstallAware](#installaware-deployment) nebo [InstallShield](#installshield-deployment)) k vytvoření instalačního programu vaší aplikace, poskytuje složku instalačního souboru, která se odebere po instalaci, můžete automaticky odstranit instalační program offline tím, že ho umístíte do složky pro instalaci.

\*\* Pokud používáte webový instalátor s vlastním instalačním programem, můžete použít výchozí nastavení jazyka na základě nastavení sady MUI (Multilingual User Interface) uživatele nebo zadat jinou jazykovou sadu pomocí možnosti `/LCID` na příkazovém řádku. Příklady najdete v části [řetězení pomocí výchozího uživatelského rozhraní .NET Framework](#chaining_default) .

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

     Pokud zadáte adresu URL pro umístění pro stažení .NET Framework, můžete zadat buď stránku pro stažení .NET Framework, nebo web, který vlastníte. Pokud Distribuovatelný balíček umísťujete na vlastní server, musí to být instalační program v režimu offline, nikoli Webová instalační služba. Odkaz na webovou Instalační službu můžete vytvořit pouze na stránce pro stažení .NET Framework. Adresa URL může také určovat disk, na kterém je vaše vlastní aplikace distribuována.

8. V dialogovém okně **stránky vlastností** klikněte na **tlačítko OK**.

<a name="installaware"></a>

### <a name="installaware-deployment"></a>Nasazení InstallAware

InstallAware vytváří balíčky Windows App (APPX), Instalační služba systému Windows (MSI), nativního kódu (EXE) a App-V (Application Virtualization) z jednoho zdroje. Snadná instalace [libovolné verze .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) v nastavení, volitelně přizpůsobení instalace [úpravou výchozích skriptů](https://www.installaware.com/msicode.htm). Například InstallAware předběžně nainstaluje certifikáty do systému Windows 7 bez toho, aby se instalace .NET Framework 4,7 nezdařila. Další informace o InstallAware najdete na webu [InstallAware for Instalační služba systému Windows](https://www.installaware.com/) .

### <a name="installshield-deployment"></a>Nasazení InstallShield

InstallShield sestaví balíčky aplikací systému Windows (MSIX, APPX), balíčky Instalační služba systému Windows (MSI) a nativního kódu (EXE). InstallShield také poskytuje integraci se službou Visual Studio. Další informace najdete na webu [InstallShield](https://www.flexerasoftware.com/install/products/installshield.html) .

<a name="wix"></a>

### <a name="windows-installer-xml-wix-deployment"></a>Nasazení Instalační služba systému Windows XML (WiX)

Sada nástrojů Instalační služba systému Windows XML (WiX) vytváří instalační balíčky Windows ze zdrojového kódu XML. WiX podporuje prostředí příkazového řádku, které lze integrovat do procesů sestavení pro sestavení instalačních balíčků MSI a MSM. Pomocí WiX můžete [určit .NET Framework jako předpoklad](https://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html), nebo [vytvořit řetěz](https://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) , který plně řídí možnosti nasazení .NET Framework. Další informace o WiX najdete na webu sady [nástrojů pro instalační služba systému Windows XML (WiX)](https://wixtoolset.org/) .

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

- Chcete-li uživatelům umožnit, aby zavřeli spuštěné aplikace .NET Framework pro minimalizaci restartování systému, nastavte pasivní režim a použijte možnost `/showrmui` následujícím způsobem:

    `dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso`

     Tento příkaz umožňuje správci restartování zobrazit okno se zprávou, které uživatelům umožňuje zavřít .NET Framework aplikace před instalací .NET Framework.

- Pokud používáte webový instalační program, můžete k zadání jazykové sady použít možnost `/LCID`. Chcete-li například zřetězit webový instalátor .NET Framework 4,5 k instalačnímu programu společnosti Contoso a nainstalovat japonskou jazykovou sadu, přidejte do procesu instalace aplikace následující příkaz:

    `dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041`

     Pokud vynecháte možnost `/LCID`, instalační program nainstaluje jazykovou sadu, která bude odpovídat nastavení MUI uživatele.

    > [!NOTE]
    > Různé jazykové sady mohou mít odlišná data vydání. Pokud zadaná jazyková sada není k dispozici ve službě Stažení softwaru, instalační program nainstaluje .NET Framework bez jazykové sady. Pokud je již .NET Framework v počítači uživatele nainstalován, instalační program nainstaluje pouze jazykovou sadu.

Úplný seznam možností najdete v části [Možnosti příkazového řádku](#command-line-options) .

Společné návratové kódy naleznete v části [návratové kódy](#return-codes) .

<a name="chaining_custom"></a>

### <a name="chaining-by-using-a-custom-ui"></a>Řetězení pomocí vlastního uživatelského rozhraní

Pokud máte vlastní instalační balíček, můžete chtít spustit tichou instalaci a sledovat nastavení .NET Framework a zároveň zobrazit průběh instalace. Pokud se jedná o tento případ, ujistěte se, že váš kód pokrývá následující:

- Vyhledejte [.NET Framework požadavky na hardware a software](../get-started/system-requirements.md).

- [Zjišťuje](#detect_net) , zda je v počítači uživatele již nainstalována správná verze .NET Framework.

    > [!IMPORTANT]
    > Při určování, jestli je už nainstalovaná správná verze .NET Framework, byste měli ověřit, jestli je nainstalovaná vaše cílová verze *nebo* novější verze, a to bez ohledu na to, jestli je vaše cílová verze nainstalovaná. Jinými slovy, měli byste vyhodnotit, jestli je klíč verze, který načtete z registru, větší nebo roven klíči verze cílové verze, a to *bez* ohledu na to, jestli se rovná klíč verze cílové verze.

- [Zjišťuje](#detecting-the-language-packs) , zda jsou v počítači uživatele již nainstalovány jazykové sady.

- Pokud chcete řízení nasazení řídit, spouštějte a sledujte proces instalace .NET Framework (viz [Postupy: získání průběhu z instalačního programu .NET Framework 4,5](how-to-get-progress-from-the-dotnet-installer.md)).

- Pokud nasazujete offline instalační program, [řetězte si jazykové sady samostatně](#chain_langpack).

- Přizpůsobení nasazení pomocí [možností příkazového řádku](#command-line-options) Pokud například provádíte řetězení webové instalační služby .NET Framework, ale chcete přepsat výchozí jazykovou sadu, použijte možnost `/LCID`, jak je popsáno v předchozí části.

- [Řešení potíží](#troubleshooting).

<a name="detect_net"></a>

### <a name="detecting-the-net-framework"></a>Zjišťování .NET Framework

Instalační program .NET Framework zapisuje klíče registru po úspěšném dokončení instalace. Můžete otestovat, jestli je nainstalovaná .NET Framework 4,5 nebo novější, a to tak, že zkontrolujete složku `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` v registru pro hodnotu `DWORD` s názvem `Release`. (Všimněte si, že ".NET Framework Setup" nezačíná tečkou.) Existence tohoto klíče indikuje, že na tomto počítači je nainstalovaná .NET Framework 4,5 nebo novější verze. Hodnota `Release` určuje, která verze .NET Framework je nainstalována.

> [!IMPORTANT]
> Při pokusu o zjištění, zda je k dispozici konkrétní verze, byste měli zjistit hodnotu, která je **větší nebo rovna** hodnotě klíčového slova verze.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|Verze|Hodnota DWORD verze|
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
|.NET Framework 4.5.1 nainstalováno s Windows 8.1 nebo Windows Server 2012 R2|378675|
|Nainstalovaná verze .NET Framework 4.5.1 ve Windows 8, Windows 7|378758|
|.NET Framework 4.5|378389|

### <a name="detecting-the-language-packs"></a>Zjišťují se jazykové sady.

Můžete otestovat, jestli je konkrétní jazyková sada nainstalovaná, a to tak, že zkontrolujete složku HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* v registru pro hodnotu DWORD s názvem `Release`. (Všimněte si, že ".NET Framework Setup" nezačíná tečkou.) *LCID* Určuje identifikátor národního prostředí; Seznam těchto seznamů najdete v části [podporované jazyky](#supported-languages) .

Chcete-li například zjistit, zda je nainstalována úplná japonská jazyková sada (LCID = 1041), načtěte z registru následující pojmenovanou hodnotu:

| | |
|-|-|
| Klíč | HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041 |
| Název | Vydat |
| Typ | DWORD |

Pokud chcete zjistit, jestli je nainstalovaná konečná verze jazykové sady pro konkrétní verzi .NET Framework od 4,5 do 4.7.2, zkontrolujte hodnotu klíče verze DWORD popsanou v předchozí části a zjistěte [.NET Framework](#detect_net).

<a name="chain_langpack"></a>

### <a name="chaining-the-language-packs-to-your-app-setup"></a>Řetězení jazykových sad k nastavení aplikace

.NET Framework poskytuje sadu samostatných spustitelných souborů jazykové sady, které obsahují lokalizované prostředky pro konkrétní jazykové verze. Jazykové sady jsou k dispozici na stránkách pro stažení .NET Framework:

- [.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Framework 4,7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4,6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

> [!IMPORTANT]
> Jazykové sady neobsahují .NET Framework komponenty, které jsou nutné ke spuštění aplikace. před instalací jazykové sady je nutné nainstalovat .NET Framework pomocí webového nebo offline instalačního programu.

Počínaje .NET Framework 4.5.1 mají názvy balíčků formu NDP <`version`>-KB <`number`>-x86-x64 – povolit – <`culture`>. exe, kde `version` je číslo verze .NET Framework, `number` je číslo článku znalostní báze Microsoft Knowledge Base a `culture` Určuje [zemi nebo oblast](#supported-languages). Příkladem jednoho z těchto balíčků je `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`. Názvy balíčků jsou uvedené v části [Distribuovatelný balíčky](#redistributable-packages) výše v tomto článku.

Chcete-li nainstalovat jazykovou sadu pomocí instalačního programu .NET Framework v režimu offline, musíte ji zřetězit k instalaci vaší aplikace. Pokud například chcete nasadit instalační program pro .NET Framework 4.5.1 offline pomocí japonské jazykové sady, použijte následující příkaz:

`NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>`

Pokud používáte webovou Instalační službu, nemusíte zřetězit jazykové sady. Instalační program nainstaluje jazykovou sadu, která odpovídá nastavení MUI uživatele. Pokud chcete nainstalovat jiný jazyk, můžete použít možnost `/LCID` k určení jazykové sady.

Úplný seznam možností příkazového řádku najdete v části [Možnosti příkazového řádku](#command-line-options) .

### <a name="troubleshooting"></a>Řešení potíží

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

Počínaje systémem Windows 8 můžete odinstalovat .NET Framework 4,5 nebo novější verze pomocí ovládacího panelu **zapnout nebo vypnout funkce systému Windows** . Ve starších verzích Windows můžete odinstalovat .NET Framework 4,5 nebo novější verze pomocí ovládacího panelu **Přidat nebo odebrat programy** .

> [!IMPORTANT]
> V systémech Windows 7 a starších operačních systémech odinstalování .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 nebo 4,8 neobnoví .NET Framework 4,5 soubory a odinstaluje .NET Framework 4,5 neobnoví .NET Framework 4 soubory. Pokud se chcete vrátit na starší verzi, je nutné ji znovu nainstalovat a všechny její aktualizace.

## <a name="appendix"></a>Příloha

### <a name="command-line-options"></a>Možnosti příkazového řádku

V následující tabulce jsou uvedeny možnosti, které můžete zahrnout při zřetězení .NET Framework 4,5 distribuovat do instalačního programu aplikace.

|Možnost|Popis|
|------------|-----------------|
|**/CEIPConsent**|Přepíše výchozí chování a pošle anonymní zpětnou vazbu Microsoftu, aby vylepšil budoucí prostředí nasazení. Tuto možnost lze použít pouze v případě, že instalační program vyzve k zadání souhlasu a pokud uživatel udělí oprávnění k odeslání anonymní zpětné vazby společnosti Microsoft.|
|**/chainingpackage** `packageName`|Určuje název spustitelného souboru, který provádí řetězení. Tyto informace se odesílají společnosti Microsoft jako anonymní zpětná vazba, která pomáhá zlepšovat budoucí prostředí nasazení.<br /><br /> Pokud název balíčku obsahuje mezery, použijte dvojité uvozovky jako oddělovače. Příklad: **/chainingpackage "Lucerne Publishing"** . Příklad zřetězení balíčku najdete v tématu [získávání informací o průběhu z instalačního balíčku](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).|
|**/LCID**`LCID`<br /><br /> kde `LCID` Určuje identifikátor národního prostředí (viz [podporované jazyky](#supported-languages))|Nainstaluje jazykovou sadu určenou v `LCID` a vynutí zobrazení zobrazeného uživatelského rozhraní v tomto jazyce, není-li nastaven tichý režim.<br /><br /> Pro webovou Instalační službu tento řetěz možností – nainstaluje jazykový balíček z webu. **Poznámka:**  Tuto možnost použijte pouze s webovým instalačním programem.|
|**/log** `file` &#124; `folder`|Určuje umístění souboru protokolu. Výchozím nastavením je dočasná složka pro daný proces a výchozí název souboru je založen na balíčku. Je-li Přípona souboru. txt, je vytvořen textový protokol. Pokud zadáte jiné rozšíření nebo žádné rozšíření, vytvoří se protokol HTML.|
|**/msioptions**|Určuje možnosti, které se mají předat pro položky. msi a. msp; například: `/msioptions "PROPERTY1='Value'"`.|
|**/norestart**|Zabraňuje automatickému restartování instalačního programu. Použijete-li tuto možnost, musí zřetězená aplikace zachytit návratový kód a zpracovat restartování (viz část [získání informací o průběhu z instalačního balíčku](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100))).|
|**/passive**|Nastaví pasivní režim. Zobrazí indikátor průběhu, který indikuje, že instalace probíhá, ale nezobrazuje žádné výzvy ani chybové zprávy pro uživatele. V tomto režimu, při zřetězení instalačního programu, musí zřetězení balíčku zpracovat [návratové kódy](#return-codes).|
|**/pipe**|Vytvoří komunikační kanál, který umožní zřetězení balíčku, aby se mohl získat průběh.|
|**/promptrestart**|Pouze pasivní režim, pokud instalační program vyžaduje restart, vyzve uživatele. Tato možnost vyžaduje zásah uživatele, pokud je vyžadováno restartování.|
|**parametr**|Nastaví tichý režim.|
|**/Repair**|Aktivuje funkci opravy.|
|**/serialdownload**|Vynutí instalaci, aby se provedla až po stažení balíčku.|
|**/showfinalerror**|Nastaví pasivní režim. Zobrazí chyby pouze v případě, že instalace není úspěšná. Tato možnost vyžaduje zásah uživatele, pokud instalace není úspěšná.|
|**/showrmui**|Používá se pouze s možností **/passive** . Zobrazí okno se zprávou, která vyzývá uživatele, aby zavřeli .NET Framework aktuálně spuštěných aplikacích. Toto okno se zprávou se chová stejně jako v pasivním a nepasivním režimu.|
|**/Uninstall**|Odinstaluje .NET Framework redistributable.|

### <a name="supported-languages"></a>Podporované jazyky

V následující tabulce jsou uvedeny .NET Framework jazykové sady, které jsou k dispozici pro .NET Framework 4,5 a novější verze.

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
|1044|Norština (Bokmål)|ne|
|1045|Polština|pl|
|1046|Portugalština – Brazílie|pt-BR|
|1049|Ruština|ru|
|1053|švédština|sv|
|1055|Turečtina|recenzent|
|2052|Čínština – zjednodušená|zh – Hans|
|2070|Portugalština – Portugalsko|pt-PT|
|3082|Španělština – Španělsko (moderní řazení)|jednomu|

## <a name="see-also"></a>Viz také

- [Příručka nasazení pro administrátory](guide-for-administrators.md)
- [Požadavky na systém](../get-started/system-requirements.md)
- [Instalace .NET Framework pro vývojáře](../install/guide-for-developers.md)
- [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
- [Omezení restartů systému při instalaci rozhraní .NET Framework 4.5](reducing-system-restarts.md)
- [Postupy: Získání procesu z instalačního programu .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)
