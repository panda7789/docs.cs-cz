---
title: dotnet-install scripts
description: Přečtěte si o příkazu dotnet – instalace skriptů pro instalaci .NET Core SDK a sdíleného modulu runtime.
ms.date: 04/30/2020
ms.openlocfilehash: c3aa6549a0b521db7fc19c6ff44665e3c4ba0c5f
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024651"
---
# <a name="dotnet-install-scripts-reference"></a>dotnet – Reference k instalaci skriptů

## <a name="name"></a>Name

`dotnet-install.ps1` | `dotnet-install.sh`-Skript použitý k instalaci .NET Core SDK a sdíleného modulu runtime.

## <a name="synopsis"></a>Stručný obsah

Windows:

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress] [-ProxyBypassList <LIST_OF_URLS>]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

Get-Help ./dotnet-install.ps1
```

Linux/macOS:

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

Skript bash také čte přepínače prostředí PowerShell, takže můžete použít přepínače prostředí PowerShell se skriptem v systémech Linux/macOS.

## <a name="description"></a>Popis

`dotnet-install`Skripty provádějí instalaci .NET Core SDK bez správy, což zahrnuje .NET Core CLI a sdílený modul runtime. K dispozici jsou dva skripty:

* PowerShellový skript, který funguje v systému Windows.
* Skript bash, který funguje v systému Linux/macOS.

### <a name="purpose"></a>Účel

 Zamýšlené použití skriptů je pro scénáře průběžné integrace (CI), kde:

* Sadu SDK je potřeba nainstalovat bez zásahu uživatele a bez oprávnění správce.
* Instalace sady SDK není nutné uchovávat v několika spuštěních CI.

  Typická posloupnost událostí:
  * CI se aktivuje.
  * CI nainstaluje sadu SDK pomocí jednoho z těchto skriptů.
  * CI dokončí svou práci a vymaže dočasná data včetně instalace sady SDK.

Chcete-li nastavit vývojové prostředí nebo spustit aplikace, použijte instalační programy a nikoli tyto skripty.

### <a name="recommended-version"></a>Doporučená verze

Doporučujeme používat stabilní verzi skriptů:

- Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh>
- PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1>

### <a name="script-behavior"></a>Chování skriptu

Oba skripty mají stejné chování. Stáhnou soubor ZIP/tarballu z buildu CLI a budou pokračovat v jeho instalaci buď ve výchozím umístění, nebo v umístění určeném parametrem `-InstallDir|--install-dir` .

Ve výchozím nastavení stáhnou instalační skripty sadu SDK a nainstaluje ji. Pokud chcete získat pouze sdílený modul runtime, zadejte `-Runtime|--runtime` argument.

Ve výchozím nastavení skript přidá umístění instalace do $PATH pro aktuální relaci. Přepsat toto výchozí chování zadáním `-NoPath|--no-path` argumentu. Skript nenastavuje `DOTNET_ROOT` proměnnou prostředí.

Před spuštěním skriptu nainstalujte požadované [závislosti](../install/windows.md#dependencies).

Konkrétní verzi můžete nainstalovat pomocí `-Version|--version` argumentu. Verze musí být zadána jako číslo verze se třemi částmi, například `2.1.0` . Pokud není zadaná verze, skript nainstaluje `latest` verzi.

Instalační skripty neaktualizují registr ve Windows. Stačí stáhnout binární soubory zip a zkopírovat je do složky. Pokud chcete aktualizovat hodnoty klíčů registru, použijte instalátory .NET Core.

## <a name="options"></a>Možnosti

- **`-Architecture|--architecture <ARCHITECTURE>`**

  Architektura binárních souborů .NET Core, které se mají nainstalovat Možné hodnoty jsou `<auto>` , `amd64` , `x64` , `x86` , a `arm64` `arm` . Výchozí hodnota je `<auto>` , která představuje aktuálně běžící architekturu OS.

- **`-AzureFeed|--azure-feed`**

  Určuje adresu URL pro instalační službu Azure feed. Doporučujeme, abyste tuto hodnotu nezměnili. Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.

- **`-Channel|--channel <CHANNEL>`**

  Určuje zdrojový kanál pro instalaci. Možné hodnoty jsou:

  - `Current`– Nejvíc aktuální verze
  - `LTS`– Kanál dlouhodobé podpory (aktuálně podporovaná verze).
  - Verze se dvěma částmi ve formátu X. Y představující specifickou verzi (například `2.1` nebo `3.0` ).
  - Název větve: například `release/3.1.1xx` nebo `master` (pro noční vydání). Tuto možnost použijte, pokud chcete nainstalovat verzi z kanálu verze Preview. Použijte název kanálu, který je uvedený v části [instalátory a binární soubory](https://github.com/dotnet/core-sdk#installers-and-binaries).

  Výchozí hodnota je `LTS`. Další informace o kanálech podpory rozhraní .NET najdete na stránce [zásady podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .

- **`-DryRun|--dry-run`**

  Když se tato nastavení nastaví, skript neprovede instalaci. Místo toho zobrazí příkazový řádek, který se má použít k konzistentně instalaci požadované verze .NET Core CLI. Pokud například zadáte verzi `latest` , zobrazí se odkaz s konkrétní verzí, aby se tento příkaz mohl ve skriptu sestavení použít deterministické. Také se zobrazí umístění binárního souboru, pokud dáváte přednost instalaci nebo stažení.

- **`-FeedCredential|--feed-credential`**

  Slouží jako řetězec dotazu, který se má připojit k datovému kanálu Azure. Umožňuje změnit adresu URL tak, aby používala neveřejné účty úložiště BLOB.

- **`--help`**

  Vytiskne nápovědu pro skript. Platí jenom pro skript bash. Pro prostředí PowerShell použijte `Get-Help ./dotnet-install.ps1` .

- **`-InstallDir|--install-dir <DIRECTORY>`**

  Určuje instalační cestu. Adresář se vytvoří, pokud neexistuje. Výchozí hodnota je *%localappdata%\Microsoft\dotnet* ve Windows a */usr/share/dotnet* v systému Linux/MacOS. Binární soubory jsou umístěny přímo v tomto adresáři.

- **`-JSonFile|--jsonfile <JSONFILE>`**

  Určuje cestu k [global.jsv](global-json.md) souboru, který se použije k určení verze sady SDK. *global.jsv* souboru musí mít hodnotu pro `sdk:version` .

- **`-NoCdn|--no-cdn`**

  Zakáže stahování z [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) a používá neuložené kanály přímo.

- **`-NoPath|--no-path`**

  Je-li nastavena, instalační složka není exportována do cesty pro aktuální relaci. Ve výchozím nastavení skript upraví cestu, která zpřístupní .NET Core CLI hned po instalaci.

- **`-ProxyAddress`**

  Pokud je tato nastavení nastavena, instalační program při vytváření webových požadavků používá proxy server. (Platí jenom pro Windows.)

- **`-ProxyBypassList <LIST_OF_URLS>`**

  Pokud je nastaveno `ProxyAddress` na, poskytuje seznam adres URL oddělených čárkami, které budou proxy obcházet. (Platí jenom pro Windows.)

- **`ProxyUseDefaultCredentials`**

  Pokud je nastaveno, instalační program při použití adresy proxy používá přihlašovací údaje aktuálního uživatele. (Platí jenom pro Windows.)

- **`-Runtime|--runtime <RUNTIME>`**

  Nainstaluje pouze sdílený modul runtime, nikoli celou sadu SDK. Možné hodnoty jsou:

  - `dotnet`– `Microsoft.NETCore.App` sdílený modul runtime.
  - `aspnetcore`– `Microsoft.AspNetCore.App` sdílený modul runtime.
  - `windowsdesktop`– `Microsoft.WindowsDesktop.App` sdílený modul runtime.

- **`--runtime-id <RID>`**

  Určuje [identifikátor modulu runtime](../rid-catalog.md) , pro který jsou nástroje nainstalovány. Používá se `linux-x64` pro přenosné Linux. (Platí jenom pro Linux/macOS.)

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > Tento parametr je zastaralý a v budoucí verzi skriptu ho můžete odebrat. Doporučená alternativa je `-Runtime|--runtime` možnost.

  Nainstaluje jenom sdílené běhové bity, ne celou sadu SDK. Tato možnost je ekvivalentní se zadáním `-Runtime|--runtime dotnet` .

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  Přeskočí instalaci souborů bez verze, například *dotnet.exe*, pokud již existují.

- **`-UncachedFeed|--uncached-feed`**

  Umožňuje změnit adresu URL informačního kanálu neuloženého v mezipaměti, který používá tento instalační program. Doporučujeme, abyste tuto hodnotu nezměnili.

- **`-Verbose|--verbose`**

  Zobrazí diagnostické informace.

- **`-Version|--version <VERSION>`**

  Představuje konkrétní verzi buildu. Možné hodnoty jsou:

  - `latest`– Nejnovější sestavení kanálu (používá se s `-Channel` možností)
  - `coherent`-Nejnovější souvislý Build na kanálu; používá nejnovější kombinaci stabilního balíčku (používá se s `-Channel` možnostmi názvu větve).
  - Verze se třemi částmi ve formátu X. Y. Z představující specifickou verzi buildu; nahrazuje `-Channel` možnost. Příklad: `2.0.0-preview2-006120`.

  Pokud není zadaný, `-Version` použije se výchozí hodnota `latest` .

## <a name="examples"></a>Příklady

- Nainstalujte nejnovější dlouhodobou podporovanou verzi (LTS) do výchozího umístění:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- Nainstalujte nejnovější verzi z kanálu 3,1 do zadaného umístění:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- Instalace verze 3.0.0 sdíleného modulu runtime:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- Získání skriptu a instalace verze 2.1.2 za podnikovým proxy serverem (pouze Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Získání skriptu a instalace .NET Core CLI v jednom-linii příkladech:

  Windows:

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Viz také

- [Verze .NET Core](https://github.com/dotnet/core/releases)
- [Archiv rozhraní .NET Core Runtime a sady SDK ke stažení](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
