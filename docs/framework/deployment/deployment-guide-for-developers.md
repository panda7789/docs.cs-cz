---
title: Průvodce nasazením rozhraní .NET Framework pro vývojáře
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
ms.openlocfilehash: 26c168040b0fa5e975e64a7518b0d0bf250c4711
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628121"
---
# <a name="net-framework-deployment-guide-for-developers"></a>Průvodce nasazením rozhraní .NET Framework pro vývojáře
Toto téma obsahuje informace pro vývojáře, kteří chtějí nainstalovat libovolnou [!INCLUDE[net_current](../../../includes/net-current-version.md)] verzi rozhraní .NET Framework z rozhraní .NET Framework 4.5 do svých aplikací.

Redistribuovatelné balíčky a jazykové sady pro rozhraní .NET Framework si můžete stáhnout ze stránek pro stahování:

- [Rozhraní .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [Rozhraní .NET 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [Rozhraní .NET 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [Rozhraní .NET Framework 4.7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

 Důležité poznámky:

- Verze rozhraní .NET Framework od rozhraní .NET Framework [!INCLUDE[net_current](../../../includes/net-current-version.md)] 4.5.1 až 000 000 jsou aktuální aktualizace rozhraní .NET Framework 4.5, což znamená, že používají stejnou verzi za běhu, ale verze sestavení jsou aktualizovány a obsahují nové typy a členy.

- Rozhraní .NET Framework 4.5 a novější verze jsou postupně sestaveny v rozhraní .NET Framework 4. Při instalaci rozhraní .NET Framework 4.5 nebo novějších verzí do systému, ve kterých je nainstalována rozhraní .NET Framework 4, jsou sestavení verze 4 nahrazena novějšími verzemi.

- Pokud odkazujete na [nerozpadlý balíček](../get-started/the-net-framework-and-out-of-band-releases.md) Microsoftu ve vaší aplikaci, sestavení bude zahrnuto do balíčku aplikace.

- K instalaci rozhraní .NET Framework 4.5 nebo novějších verzí musíte mít oprávnění správce.

- Rozhraní .NET Framework 4.5 je součástí Windows 8 a Windows Server 2012, takže ji nemusíte nasazovat s aplikací v těchto operačních systémech. Podobně rozhraní .NET Framework 4.5.1 je součástí windows 8.1 a Windows Server 2012 R2. Rozhraní .NET Framework 4.5.2 není součástí žádného operačního systému. Rozhraní .NET Framework 4.6 je součástí windows 10, rozhraní .NET Framework 4.6.1 je součástí listopadové aktualizace windows 10 a rozhraní .NET Framework 4.6.2 je součástí aktualizace Windows 10 Anniversary Update.  .NET Framework 4.7 je součástí aktualizace Windows 10 Creators Update, .NET Framework 4.7.1 je součástí aktualizace Windows 10 Fall Creators Update a .NET Framework 4.7.2 je součástí aktualizace Windows 10 říjen 2018 a Windows 10 duben 2018 Update. Rozhraní .NET Framework 4.8 je součástí aktualizace Windows 10 z května 2019. Úplný seznam požadavků na hardware a software naleznete v [tématu Systémové požadavky](../get-started/system-requirements.md).

- Počínaje rozhraním .NET Framework 4.5 mohou uživatelé během instalace zobrazit seznam spuštěných aplikací rozhraní .NET Framework a snadno je zavřít. To může pomoci zabránit restartování systému způsobené instalacemi rozhraní .NET Framework. Viz [Snížení restartování systému](reducing-system-restarts.md).

- Odinstalace rozhraní .NET Framework 4.5 nebo novějších verzí také odebere již existující soubory rozhraní .NET Framework 4. Pokud se chcete vrátit do rozhraní .NET Framework 4, je nutné ji přeinstalovat a všechny její aktualizace. Viz [Instalace rozhraní .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100)).

- 9. října 2012 byla aktualizována redistribuovatelná architektura .NET Framework 4.5, aby opravila problém související s nesprávným časovým razítkem na digitálním certifikátu, který způsobil předčasné vypršení platnosti digitálního podpisu na souborech vytvořených a podepsaných společností Microsoft. Pokud jste dříve nainstalovali balíček .NET Framework 4.5 redistributable ze srpna 16, 2012, doporučujeme aktualizovat kopii s nejnovější redistribuovatelné ze [stránky pro stažení rozhraní .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/net45). Další informace o tomto problému naleznete [v informačním zpravodaji zabezpečení společnosti Microsoft 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655).

Informace o tom, jak může správce systému nasadit rozhraní .NET Framework a jeho systémové závislosti v síti, naleznete v [Příručce pro nasazení pro správce](guide-for-administrators.md).

## <a name="deployment-options-for-your-app"></a>Možnosti nasazení pro vaši aplikaci

Až budete připraveni publikovat aplikaci na webovém serveru nebo v jiném centralizovaném umístění, aby ji uživatelé mohli nainstalovat, můžete si vybrat z několika metod nasazení. Některé z nich jsou k dispozici s Visual Studio. V následující tabulce jsou uvedeny možnosti nasazení pro vaši aplikaci a určuje balíček .NET Framework redistributable, který podporuje každou možnost. Kromě těchto, můžete napsat vlastní instalační program pro vaši aplikaci; Další informace naleznete v části [Řetězování instalace rozhraní .NET Framework do instalačního programu aplikace](#chaining).

|Strategie nasazení pro vaši aplikaci|Dostupné metody nasazení|Redistribuovatelné rozhraní .NET Framework|
|--------------------------------------|----------------------------------|-------------------------------------------|
|Instalace z webu|- [Installaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [Sada nástrojů WiX](#wix)<br />- [Ruční instalace](#installing_manually)|[Webový instalační program](#redistributable-packages)|
|Instalace z disku|- [Installaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [Sada nástrojů WiX](#wix)<br />- [Ruční instalace](#installing_manually)|[Offline instalační program](#redistributable-packages)|
|Instalace z místní sítě (pro podnikové aplikace)|- [Clickonce](#clickonce-deployment)|Buď [webový instalátor](#redistributable-packages) (omezení naleznete v [tématu ClickOnce)](#clickonce-deployment) nebo [offline instalační program](#redistributable-packages)|

## <a name="redistributable-packages"></a>Redistribuovatelné balíčky

Rozhraní .NET Framework je k dispozici ve dvou redistribuovatelných balíčcích: webový instalační program (zaváděcí nástroj) a offline instalační program (samostatný redistribuovatelný). Všechna stahovaná rozhraní .NET Framework jsou hostována na [stránce Download .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/). Následující tabulka porovnává dva balíčky:

||Webový instalační program|Offline instalační program|
|-|-------------------|-----------------------|
|Je vyžadováno připojení k internetu?|Ano|Ne|
|Velikost stahování|Menší (zahrnuje instalační program pouze pro cílovou platformu)*|Větší*|
|Jazykové sady|Zahrnuto**|Musí být [nainstalován samostatně](#chain_langpack), pokud nepoužíváte balíček, který se zaměřuje na všechny operační systémy|
|Metoda nasazení|Podporuje všechny metody:<br /><br />- [Clickonce](#clickonce-deployment)<br />- [Installaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [Jazyk XML Instalační služby systému Windows (WiX)](#wix)<br />- [Ruční instalace](#installing_manually)<br />- [Vlastní nastavení (řetězení)](#chaining)|Podporuje všechny metody:<br /><br /> - [Clickonce](#clickonce-deployment)<br />- [Installaware](#installaware-deployment)<br />- [Installshield](#installshield-deployment)<br />- [Jazyk XML Instalační služby systému Windows (WiX)](#wix)<br />- [Ruční instalace](#installing_manually)<br />- [Vlastní nastavení (řetězení)](#chaining)|

\*Offline instalační program je větší, protože obsahuje součásti pro všechny cílové platformy. Po dokončení spuštění instalace uloží operační systém Windows do mezipaměti pouze použitou instalační službu. Pokud je offline instalační program po instalaci odstraněn, je využité místo na disku stejné jako místo používané webovým instalačním programem. Pokud nástroj, který používáte (například [InstallAware](#installaware-deployment) nebo [InstallShield](#installshield-deployment)) k vytvoření instalačního programu aplikace, poskytuje složku instalačního souboru, která je odebrána po instalaci, lze offline instalační program automaticky odstranit umístěním do instalační složky.

\*\*Pokud používáte webovou instalační službu s vlastním nastavením, můžete použít výchozí nastavení jazyka na základě nastavení vícejazyčné uživatelské `/LCID` rozhraní (MUI) uživatele nebo zadat jinou jazykovou sadu pomocí možnosti na příkazovém řádku. Ukázky naleznete v části [Řetězení pomocí výchozího rozhraní .NET Framework.](#chaining_default)

## <a name="deployment-methods"></a>Metody nasazení

 K dispozici jsou čtyři metody nasazení:

- Můžete nastavit závislost na rozhraní .NET Framework. Rozhraní .NET Framework můžete zadat jako předpoklad v instalaci aplikace pomocí jedné z těchto metod:

  - Použití [nasazení ClickOnce](#clickonce-deployment) (k dispozici v sadě Visual Studio)

  - Vytvoření [projektu InstallAware](#installaware-deployment) (bezplatná edice je k dispozici pro uživatele sady Visual Studio)

  - Vytvoření [projektu InstallShield](#installshield-deployment) (k dispozici v sadě Visual Studio)

  - Použití [sady nástrojů Xml (WiX) Instalační služby systému Windows](#wix)

- Můžete požádat uživatele o [ruční instalaci rozhraní .NET Framework](#installing_manually).

- Můžete zřetězit (zahrnout) proces instalace rozhraní .NET Framework v nastavení aplikace a rozhodnout, jak chcete zpracovat prostředí instalace rozhraní .NET Framework:

  - [Použijte výchozí ui](#chaining_default). Umožňuje instalačnímu programu rozhraní .NET Framework poskytnout prostředí instalace.

  - [Přizpůsobte uživatelské rozhraní](#chaining_custom) tak, aby představovalo jednotné prostředí instalace a monitorovalo průběh instalace rozhraní .NET Framework.

Tyto metody nasazení jsou podrobně popsány v následujících částech.

## <a name="setting-a-dependency-on-the-net-framework"></a>Nastavení závislosti na rozhraní .NET Framework

Pokud k nasazení aplikace používáte clickonce, InstallAware, InstallShield nebo WiX, můžete přidat závislost na rozhraní .NET Framework, aby ji bylo možné nainstalovat jako součást vaší aplikace.

### <a name="clickonce-deployment"></a>ClickOnce – nasazení

Nasazení ClickOnce je k dispozici pro projekty, které jsou vytvořeny pomocí jazyka Visual Basic a Visual C#, ale není k dispozici pro visual c++.

V sadě Visual Studio zvolte nasazení ClickOnce a přidejte závislost na rozhraní .NET Framework:

1. Otevřete projekt aplikace, který chcete publikovat.

2. V Průzkumníku řešení otevřete místní nabídku projektu a pak zvolte **Vlastnosti**.

3. Zvolte podokno **Publikovat.**

4. Zvolte tlačítko **Požadavky.**

5. V dialogovém okně **Požadavky** zkontrolujte, zda je zaškrtnuto políčko **Vytvořit instalační program k instalaci nezbytných součástí.**

6. V seznamu požadavků vyhledejte a vyberte verzi rozhraní .NET Framework, kterou jste použili k sestavení projektu.

7. Zvolte možnost, chcete-li určit zdrojové umístění pro požadavky, a pak zvolte **OK**.

     Pokud zadáte adresu URL pro umístění pro stahování rozhraní .NET Framework, můžete zadat stránku pro stažení rozhraní .NET Framework nebo vlastní web. Pokud umisťujete redistribuovatelný balíček na vlastní server, musí se jednat o offline instalační program a nikoli o webový instalátor. Na stránku pro stahování rozhraní .NET Framework lze vytvořit odkaz pouze na webovou instalační službu. Adresa URL může také určit disk, na kterém je distribuována vaše vlastní aplikace.

8. V dialogovém okně **Stránky vlastností** zvolte **OK**.

<a name="installaware"></a>

### <a name="installaware-deployment"></a>Nasazení InstallAware

InstallAware vytvoří balíčky aplikace pro Windows (APPX), Instalační služby Systému Windows (MSI), nativníkód (EXE) a balíčky App-V (Virtualizace aplikací) z jednoho zdroje. Snadno [zahrnout libovolnou verzi rozhraní .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) do instalace, volitelně přizpůsobení instalace [úpravou výchozí skripty](https://www.installaware.com/msicode.htm). Například InstallAware předinstaluje certifikáty v systému Windows 7, bez kterého se instalace rozhraní .NET Framework 4.7 nezdaří. Další informace o službě InstallAware naleznete na webu [InstallAware for Windows Installer.](https://www.installaware.com/)

### <a name="installshield-deployment"></a>Nasazení programu InstallShield

InstallShield vytváří balíčky aplikací pro Windows (MSIX, APPX), instalační programy Instalační služby systému Windows (MSI) a Instalační programy nativního kódu (EXE). InstallShield také poskytuje integraci sady Visual Studio. Další informace naleznete na webu [InstallShield.](https://www.flexerasoftware.com/install/products/installshield.html)

<a name="wix"></a>

### <a name="windows-installer-xml-wix-deployment"></a>Nasazení XML (WiX) Instalační služby systému Windows

Sada nástrojů WiX (Installer XML) systému Windows vytváří instalační balíčky systému Windows ze zdrojového kódu XML. WiX podporuje prostředí příkazového řádku, které lze integrovat do vašich procesů sestavení a vytvářet instalační balíčky MSI a MSM. Pomocí WiX můžete [jako předpoklad zadat rozhraní .NET Framework](https://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html)nebo [vytvořit chainer](https://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) pro úplné řízení prostředí pro nasazení rozhraní .NET Framework. Další informace o wi-w. naleznete na webu sady nástrojů Windows [Installer XML (WiX).](https://wixtoolset.org/)

<a name="installing_manually"></a>

## <a name="installing-the-net-framework-manually"></a>Ruční instalace rozhraní .NET Framework

V některých situacích může být nepraktické automaticky nainstalovat rozhraní .NET Framework s vaší aplikací. V takovém případě můžete nechat uživatele nainstalovat rozhraní .NET Framework sami. Redistribuovatelný balíček je k dispozici ve [dvou balíčcích](#redistributable-packages). V procesu instalace zadejte pokyny, jak by měli uživatelé vyhledat a nainstalovat rozhraní .NET Framework.

<a name="chaining"></a>

## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>Zřetězení instalace rozhraní .NET Framework do nastavení aplikace

Pokud vytváříte vlastní instalační program pro vaši aplikaci, můžete zřetězit (zahrnout) proces nastavení rozhraní .NET Framework v procesu instalace aplikace. Řetězení poskytuje dvě možnosti rozhraní pro instalaci rozhraní .NET Framework:

- Použijte výchozí rozhraní poskytované instalačním programem rozhraní .NET Framework.

- Vytvořte vlastní rozhraní pro instalaci rozhraní .NET Framework pro konzistenci s instalačním programem vaší aplikace.

Obě metody umožňují používat webový instalátor nebo offline instalátor. Každý balíček má své výhody:

- Pokud použijete webový instalační program, proces instalace rozhraní .NET Framework rozhodne, který instalační balíček je vyžadován, a stáhne te a nainstalujete pouze tento balíček z webu.

- Pokud používáte offline instalační program, můžete zahrnout úplnou sadu instalačních balíčků rozhraní .NET Framework s redistribučním médiem, aby uživatelé nemuseli během instalace stahovat žádné další soubory z webu.

<a name="chaining_default"></a>

### <a name="chaining-by-using-the-default-net-framework-ui"></a>Řetězení pomocí výchozího rozhraní rozhraní rozhraní .NET Framework

Chcete-li bezobslužně zřetězit proces instalace rozhraní .NET Framework a nechat instalační program rozhraní .NET Framework poskytnout, přidejte do instalačního programu následující příkaz:

`<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>`

Pokud je například spustitelný program Contoso.exe a chcete bezobslužně nainstalovat balíček redistribuovatelné ho rozhraní .NET Framework 4.5 offline, použijte příkaz:

`dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso`

K přizpůsobení instalace můžete použít další možnosti příkazového řádku. Například:

- Chcete-li uživatelům poskytnout způsob, jak zavřít spuštěné aplikace rozhraní .NET `/showrmui` Framework, aby se minimalizovalo restartování systému, nastavte pasivní režim a použijte následující možnost:

    `dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso`

     Tento příkaz umožňuje Správci restartování zobrazit okno se zprávou, které uživatelům umožňuje před instalací rozhraní .NET Framework zavřít aplikace rozhraní .NET Framework.

- Pokud používáte webovou instalační službu, `/LCID` můžete pomocí možnosti zadat jazykovou sadu. Chcete-li například zřetězit webový instalační program rozhraní .NET Framework 4.5 do instalačního programu contoso a nainstalovat japonskou jazykovou sadu, přidejte do procesu instalace aplikace následující příkaz:

    `dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041`

     Pokud `/LCID` tuto možnost vynecháte, instalační program nainstaluje jazykovou sadu, která odpovídá nastavení MUI uživatele.

    > [!NOTE]
    > Různé jazykové sady mohou mít různá data vydání. Pokud zadaná jazyková sada není k dispozici v centru pro stahování, instalační program nainstaluje rozhraní .NET Framework bez jazykové sady. Pokud je rozhraní .NET Framework již v počítači uživatele nainstalováno, instalační program nainstaluje pouze jazykovou sadu.

Úplný seznam možností naleznete v části [Možnosti příkazového řádku.](#command-line-options)

Běžné návratové kódy naleznete v části [Návratové kódy.](#return-codes)

<a name="chaining_custom"></a>

### <a name="chaining-by-using-a-custom-ui"></a>Řetězení pomocí vlastního ui

Pokud máte vlastní instalační balíček, můžete chtít tiše spustit a sledovat nastavení rozhraní .NET Framework při zobrazení vlastního zobrazení průběhu instalace. Pokud se jedná o tento případ, ujistěte se, že váš kód zahrnuje následující:

- Zkontrolujte [požadavky na hardware a software rozhraní .NET Framework](../get-started/system-requirements.md).

- [Zjistěte,](#detect_net) zda je v počítači uživatele již nainstalována správná verze rozhraní .NET Framework.

    > [!IMPORTANT]
    > Při určování, zda je správná verze rozhraní .NET Framework již nainstalována, byste měli zkontrolovat, zda je nainstalována cílová verze *nebo* novější verze, nikoli zda je nainstalována cílová verze. Jinými slovy byste měli vyhodnotit, zda je klíč verze načítaný z registru větší nebo roven klíči vydání cílové verze, *nikoli* zda se rovná klíči vydání cílové verze.

- [Zjistěte,](#detecting-the-language-packs) zda jsou jazykové sady již nainstalovány v počítači uživatele.

- Pokud chcete řídit nasazení, tiše spusťte a sledujte proces nastavení rozhraní .NET Framework (viz [Postup: Získat průběh z instalačního programu rozhraní .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)).

- Pokud nasazujete offline instalační program, [zřetězete jazykové sady samostatně](#chain_langpack).

- Přizpůsobení nasazení pomocí [možností příkazového řádku](#command-line-options). Pokud například řetězíte webovou instalační službu rozhraní .NET Framework, ale chcete přepsat `/LCID` výchozí jazykovou sadu, použijte tuto možnost, jak je popsáno v předchozí části.

- [Poradce při potížích](#troubleshooting).

<a name="detect_net"></a>

### <a name="detecting-the-net-framework"></a>Zjišťování rozhraní .NET Framework

Instalační program rozhraní .NET Framework zapisuje klíče registru, když je instalace úspěšná. Můžete otestovat, zda je nainstalována rozhraní .NET `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` Framework 4.5 `DWORD` nebo `Release`novější kontrolou složky v registru pro hodnotu s názvem . (Všimněte si, že "NET Framework Setup" nezačíná tečkou.) Existence tohoto klíče znamená, že v tomto počítači byla nainstalována rozhraní .NET Framework 4.5 nebo novější verze. Hodnota `Release` označuje, která verze rozhraní .NET Framework je nainstalována.

> [!IMPORTANT]
> Při pokusu o zjištění, zda je k dispozici určitá verze, byste měli zkontrolovat hodnotu **větší nebo rovnou** hodnotě klíčového slova pro vydání.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|Version|Hodnota DWORD verze|
|-------------|--------------------------------|
|Rozhraní .NET Framework 4.8 nainstalované v aktualizaci Windows 10 z května 2019|528040|
|Rozhraní .NET Framework 4.8 nainstalované ve všech verzích operačního systému jiných než Windows 10 May 2019 Update|528049|
|Rozhraní .NET Framework 4.7.2 nainstalované v aktualizaci Windows 10 z dubna 2018 a v systému Windows Server verze 1803|461808|
|Rozhraní .NET Framework 4.7.2 je nainstalováno ve všech verzích operačního systému jiných než Windows 10 april 2018 Update a Windows Server verze 1803. To zahrnuje aktualizaci Windows 10 z října 2018. |461814|
|Rozhraní .NET Framework 4.7.1 nainstalované v aktualizaci Windows 10 Fall Creators Update a windows server verze 1709|461308|
|Rozhraní .NET Framework 4.7.1 nainstalované ve všech verzích operačního systému jiných než Windows 10 Fall Creators Update a Windows Server verze 1709|461310|
|Rozhraní .NET Framework 4.7 nainstalované v aktualizaci Windows 10 Creators Update|460798|
|Rozhraní .NET Framework 4.7 nainstalované ve všech verzích operačního systému jiných než Windows 10 Creators Update|460805|
|Rozhraní .NET Framework 4.6.2 nainstalované ve Windows 10 Anniversary Edition a Windows Server 2016|394802|
|Rozhraní .NET Framework 4.6.2 nainstalované ve všech verzích operačního systému kromě Windows 10 Anniversary Edition a Windows Server 2016|394806|
|Rozhraní .NET Framework 4.6.1 nainstalované v listopadové aktualizaci Windows 10|394254|
|Rozhraní .NET Framework 4.6.1 nainstalované ve všech verzích operačního systému jiných než listopadová aktualizace systému Windows 10|394271|
|Rozhraní .NET Framework 4.6 nainstalované ve Windows 10|393295|
|Rozhraní .NET Framework 4.6 nainstalované ve všech verzích operačního systému jiných než Windows 10|393297|
|.NET Framework 4.5.2|379893|
|Rozhraní .NET Framework 4.5.1 nainstalované ve Windows 8.1 nebo Windows Server 2012 R2|378675|
|Rozhraní .NET Framework 4.5.1 nainstalované ve Windows 8, Windows 7|378758|
|.NET Framework 4.5|378389|

### <a name="detecting-the-language-packs"></a>Zjišťování jazykových sad

Zda je nainstalována určitá jazyková sada, můžete zkontrolovat HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* `Release`v registru, zda neobsahuje hodnotu DWORD s názvem . (Všimněte si, že "NET Framework Setup" nezačíná tečkou.) *Identifikátor LCID* určuje identifikátor národního prostředí; seznam těchto jazyků naleznete v [podporovaných](#supported-languages) jazycích.

Chcete-li například zjistit, zda je nainstalována úplná japonská jazyková sada (LCID=1041), načtěte z registru následující pojmenovanou hodnotu:

| | |
|-|-|
| Klíč | HKEY_LOCAL_MACHINE\SOFTWARE\Instalace rozhraní Microsoft\NET Framework\NDP\v4\Full\1041 |
| Name (Název) | Vydat |
| Typ | DWORD |

Chcete-li zjistit, zda je pro určitou verzi rozhraní .NET Framework nainstalována konečná verze jazykové sady od 4.5 do 4.7.2, zkontrolujte hodnotu hodnoty DWORD klíče RELEASE popsanou v předchozí části [Zjištění rozhraní .NET Framework](#detect_net).

<a name="chain_langpack"></a>

### <a name="chaining-the-language-packs-to-your-app-setup"></a>Řetězení jazykových sad k nastavení aplikace

Rozhraní .NET Framework poskytuje sadu samostatných spustitelných souborů sady language pack, které obsahují lokalizované prostředky pro konkrétní jazykové verze. Jazykové sady jsou k dispozici na stránkách Download .NET Framework:

- [Rozhraní .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [Rozhraní .NET 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [Rozhraní .NET 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [Rozhraní .NET Framework 4.7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
- [.NET Framework 4.5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

> [!IMPORTANT]
> Jazykové sady neobsahují součásti rozhraní .NET Framework, které jsou nutné ke spuštění aplikace. Před instalací jazykové sady je nutné nainstalovat rozhraní .NET Framework pomocí webového nebo offline instalačního programu.

Počínaje rozhraním .NET Framework 4.5.1 mají názvy `version` balíčků podobu `number` NDP<>-KB `culture`<>-x86-x64-AllOS-<>.exe, kde `version` je číslo verze rozhraní .NET Framework, `number` je číslo článku znalostní báze Microsoft Knowledge Base a `culture` určuje zemi nebo [oblast](#supported-languages). Příkladem jednoho z těchto `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`balíčků je . Názvy balíčků jsou uvedeny v části [Redistributable Packages](#redistributable-packages) dříve v tomto článku.

Chcete-li nainstalovat jazykovou sadu s offline instalačním programem rozhraní .NET Framework, musíte ji zřetězit do nastavení aplikace. Chcete-li například nasadit offline instalační program rozhraní .NET Framework 4.5.1 s japonskou jazykovou sadou, použijte následující příkaz:

`NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>`

Pokud používáte webový instalační program, není nutné je řetězovat. instalační program nainstaluje jazykovou sadu, která odpovídá nastavení MUI uživatele. Chcete-li nainstalovat jiný jazyk, můžete `/LCID` pomocí možnosti zadat jazykovou sadu.

Úplný seznam možností příkazového řádku naleznete v části [Možnosti příkazového řádku.](#command-line-options)

### <a name="troubleshooting"></a>Řešení potíží

#### <a name="return-codes"></a>Návratové kódy

V následující tabulce jsou uvedeny nejběžnější návratové kódy redistribuovatelného instalačního programu rozhraní .NET Framework. Návratové kódy jsou stejné pro všechny verze instalačního programu. Odkazy na podrobné informace naleznete v další části.

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

- [Kódy chyb služby INTELIGENTNÍ PŘENOS na pozadí (BITS)](https://go.microsoft.com/fwlink/?LinkId=180946)

- [Kódy chyb zástupný název adresy URL](https://go.microsoft.com/fwlink/?LinkId=180947)

- [Kódy chyb WinHttp](https://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>Další kódy chyb

Podívejte se na následující obsah:

- [Kódy chyb Instalační služby systému Windows](https://go.microsoft.com/fwlink/?LinkId=180949)

- [Kódy výsledků agenta služby Windows Update](https://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>Odinstalace rozhraní .NET Framework

Počínaje Windows 8 můžete odinstalovat rozhraní .NET Framework 4.5 nebo novější verze pomocí **funkce systému Windows zapnout a vypnout** v Ovládacích panelech. Ve starších verzích systému Windows můžete odinstalovat rozhraní .NET Framework 4.5 nebo novější verze pomocí ovládacího panelu **Přidat nebo odebrat programy.**

> [!IMPORTANT]
> Pro operační systémy Windows 7 a starší operační systémy odinstalováním rozhraní .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 nebo 4.8 neobnoví soubory rozhraní .NET Framework 4.5 a odinstalování souborů .NET Framework 4.5 neobnoví soubory .NET Framework 4. Pokud se chcete vrátit ke starší verzi, musíte ji přeinstalovat a všechny její aktualizace.

## <a name="appendix"></a>Příloha

### <a name="command-line-options"></a>Možnosti příkazového řádku

V následující tabulce jsou uvedeny možnosti, které můžete zahrnout při řetězení rozhraní .NET Framework 4.5 redistribuovatelné do nastavení vaší aplikace.

|Možnost|Popis|
|------------|-----------------|
|**/Souhlas programu Zlepšování softwaru a adres**|Přepíše výchozí chování a odešle anonymní zpětnou vazbu společnosti Microsoft, aby se zlepšila budoucí možnosti nasazení. Tuto možnost lze použít pouze v případě, že instalační program vyzve k udělení souhlasu a pokud uživatel udělí oprávnění k odeslání anonymní zpětné vazby společnosti Microsoft.|
|**/řetězeníbalíček**`packageName`|Určuje název spustitelného souboru, který provádí řetězení. Tyto informace jsou odesílány společnosti Microsoft jako anonymní zpětná vazba, která pomáhá zlepšit budoucí možnosti nasazení.<br /><br /> Pokud název balíčku obsahuje mezery, použijte jako oddělovače dvojité uvozovky; například: **/chainingpackage "Lucerne Publishing"**. Příklad řetězení balíčku naleznete [v tématu získání informací o průběhu z instalačního balíčku](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).|
|**/LCID**  `LCID`<br /><br /> kde `LCID` je specifikován identifikátor národního prostředí (viz [podporované jazyky)](#supported-languages)|Nainstaluje jazykovou sadu `LCID` určenou a vynutí zobrazení uI v tomto jazyce, pokud není nastaven tichý režim.<br /><br /> Pro webový instalační program tato možnost řetěz nainstaluje jazykový balíček z webu. **Poznámka:**  Tuto možnost použijte pouze u webového instalačního programu.|
|**/log** `file` &#124;`folder`|Určuje umístění souboru protokolu. Výchozí je dočasná složka procesu a výchozí název souboru je založen na balíčku. Pokud je přípona souboru .txt, je vytvořen textový protokol. Pokud zadáte jiné rozšíření nebo žádné rozšíření, vytvoří se protokol HTML.|
|**/msioptions**|Určuje možnosti, které mají být předány pro položky MSI a MSP; například: `/msioptions "PROPERTY1='Value'"`.|
|**/norestart**|Zabrání automatickému restartování instalačního programu. Pokud použijete tuto možnost, řetězení aplikace musí zachytit návratový kód a zpracování restartování (viz [Získání informací o průběhu z instalačního balíčku](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100))).|
|**/pasivní**|Nastaví pasivní režim. Zobrazí indikátor průběhu označující, že probíhá instalace, ale nezobrazuje žádné výzvy ani chybové zprávy uživateli. V tomto režimu při zřetězení instalačním programem musí řetězený balíček zpracovávat [návratové kódy](#return-codes).|
|**/potrubí**|Vytvoří komunikační kanál povolit řetězení balíček získat průběh.|
|**/promptrestart**|Pouze pasivní režim, pokud instalační program vyžaduje restartování, vyzve uživatele. Tato možnost vyžaduje interakci uživatele, pokud je vyžadováno restartování.|
|**/q**|Nastaví tichý režim.|
|**/oprava**|Spustí funkci opravy.|
|**/serialdownload**|Vynutí, aby k instalaci došlo až po stažení balíčku.|
|**/showfinalerror**|Nastaví pasivní režim. Zobrazí chyby pouze v případě, že instalace není úspěšná. Tato možnost vyžaduje interakci uživatele, pokud instalace není úspěšná.|
|**/showrmui**|Používá se pouze s **možností /passive.** Zobrazí okno se zprávou, které vyzve uživatele k ukončení aktuálně spuštěných aplikací rozhraní .NET Framework. Toto okno se zprávou se chová stejně v pasivním a nepasivním režimu.|
|**/odinstalovat**|Odinstaluje redistribuovatelné rozhraní .NET Framework.|

### <a name="supported-languages"></a>Podporované jazyky

V následující tabulce jsou uvedeny jazykové sady .NET Framework, které jsou k dispozici pro rozhraní .NET Framework 4.5 a novější verze.

|LCID|Jazyk – země/oblast|Culture|
|----------|--------------------------------|-------------|
|1025|Arabština - Saúdská Arábie|ar|
|1028|Čínština – tradiční|zh-Hant|
|1029|Čeština|Cs|
|1030|Dánština|Da|
|1031|Němčina – Německo|De|
|1032|Řečtina|El|
|1035|Finština|ﬁ|
|1036|Francouzština – Francie|Fr|
|1037|Hebrejština|on|
|1038|Maďarština|Hu|
|1040|Italština – Itálie|je to|
|1041|Japonština|ja|
|1042|Korejština|Ko|
|1043|Nizozemština – Nizozemsko|Nl|
|1044|Norština (Bokmål)|ne|
|1045|Polština|Pl|
|1046|Portugalština – Brazílie|pt-BR|
|1049|Ruština|Ru|
|1053|Švédština|sv|
|1055|Turečtina|Tr|
|2052|Čínština – zjednodušená|zh-Hans|
|2070|Portugalština – Portugalsko|pt-PT|
|3082|Španělština - Španělsko (moderní řazení)|Ano|

## <a name="see-also"></a>Viz také

- [Příručka nasazení pro administrátory](guide-for-administrators.md)
- [Systémové požadavky](../get-started/system-requirements.md)
- [Instalace rozhraní .NET Framework pro vývojáře](../install/guide-for-developers.md)
- [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
- [Omezení restartů systému při instalaci rozhraní .NET Framework 4.5](reducing-system-restarts.md)
- [Postupy: Získání procesu z instalačního programu .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)
