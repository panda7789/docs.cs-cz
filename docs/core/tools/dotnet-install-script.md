---
title: dotnet-install scripts
description: Přečtěte si o dotnet – instalace skriptů pro instalaci nástrojů .NET Core CLI a sdíleného modulu runtime.
ms.date: 01/16/2019
ms.openlocfilehash: f72e12fc415824a9c69eba6f52e3c01717cf654c
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740527"
---
# <a name="dotnet-install-scripts-reference"></a>dotnet – Reference k instalaci skriptů

## <a name="name"></a>Name

`dotnet-install.ps1` | `dotnet-install.sh`-skript používaný k instalaci nástrojů .NET Core CLI a sdíleného modulu runtime.

## <a name="synopsis"></a>Stručný obsah

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a>Popis

Skripty `dotnet-install` slouží k provedení instalace .NET Core SDK bez správy, která zahrnuje nástroje .NET Core CLI a sdílený modul runtime.

Doporučujeme používat stabilní verzi, která je hostována na [hlavním webu .NET Core](https://dot.net). K přímým cestám ke skriptům patří:

- <https://dot.net/v1/dotnet-install.sh> (bash, UNIX)
- <https://dot.net/v1/dotnet-install.ps1> (PowerShell, Windows)

Hlavní užitečnost těchto skriptů je ve scénářích automatizace a v instalacích bez správy. Existují dva skripty: jeden je PowerShellový skript, který funguje ve Windows, a druhý je bash skript, který funguje na Linux/macOS. Oba skripty mají stejné chování. Skript bash také čte přepínače prostředí PowerShell, takže můžete použít přepínače prostředí PowerShell se skriptem v systémech Linux/macOS.

Instalační skripty stáhnou soubor ZIP/tarballu z buildu CLI a budou pokračovat v jeho instalaci buď ve výchozím umístění, nebo v umístění určeném parametrem `-InstallDir|--install-dir`. Ve výchozím nastavení stáhnou instalační skripty sadu SDK a nainstaluje ji. Pokud chcete získat pouze sdílený modul runtime, zadejte argument `--runtime`.

Ve výchozím nastavení skript přidá umístění instalace do $PATH pro aktuální relaci. Přepsat toto výchozí chování zadáním argumentu `--no-path`.

Před spuštěním skriptu nainstalujte požadované [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

Konkrétní verzi můžete nainstalovat pomocí argumentu `--version`. Verze musí být zadaná jako verze se třemi částmi (například 1.0.0-13232). Pokud není k dispozici, používá `latest` verzi.

## <a name="options"></a>Možnosti

- **`-Channel <CHANNEL>`**

  Určuje zdrojový kanál pro instalaci. Možné hodnoty jsou:

  - `Current` – aktuální verze.
  - `LTS` – kanál dlouhodobé podpory (aktuálně podporovaná verze).
  - Verze se dvěma částmi ve formátu X. Y představující specifickou verzi (například `2.0` nebo `1.0`).
  - Název větve Například `release/2.0.0`, `release/2.0.0-preview2`nebo `master` (pro noční vydání).

  Výchozí hodnota je `LTS`. Další informace o kanálech podpory rozhraní .NET najdete na stránce [zásady podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .

- **`-Version <VERSION>`**

  Představuje konkrétní verzi buildu. Možné hodnoty jsou:

  - `latest` – nejnovější sestavení kanálu (používá se s možností `-Channel`)
  - `coherent` – nejnovější souvislé sestavení na kanálu; používá nejnovější kombinaci stabilního balíčku (používá se s názvem větve `-Channel` možností).
  - Verze se třemi částmi ve formátu X. Y. Z představující specifickou verzi buildu; nahrazuje možnost `-Channel`. Například: `2.0.0-preview2-006120`.

  Pokud není zadaný, `-Version` výchozí nastavení `latest`.

- **`-InstallDir <DIRECTORY>`**

  Určuje instalační cestu. Adresář se vytvoří, pokud neexistuje. Výchozí hodnota je *%localappdata%\Microsoft\dotnet*. Binární soubory jsou umístěny přímo v tomto adresáři.

- **`-Architecture <ARCHITECTURE>`**

  Architektura binárních souborů .NET Core, které se mají nainstalovat Možné hodnoty jsou `<auto>`, `amd64`, `x64`, `x86`, `arm64`a `arm`. Výchozí hodnota je `<auto>`, která představuje aktuálně běžící architekturu OS.

- **`-SharedRuntime`**

  > [!NOTE]
  > Tento parametr je zastaralý a v budoucí verzi skriptu ho můžete odebrat. Doporučená alternativa je `Runtime` možnost.

  Nainstaluje jenom sdílené běhové bity, ne celou sadu SDK. Jedná se o ekvivalent určení `-Runtime dotnet`.

- **`-Runtime <RUNTIME>`**

  Nainstaluje pouze sdílený modul runtime, nikoli celou sadu SDK. Možné hodnoty jsou:

  - `dotnet` – `Microsoft.NETCore.App` sdílený modul runtime.
  - `aspnetcore` – `Microsoft.AspNetCore.App` sdílený modul runtime.

- **`-DryRun`**

  Když se tato nastavení nastaví, skript neprovede instalaci. Místo toho zobrazí příkazový řádek, který se má použít k konzistentně instalaci požadované verze .NET Core CLI. Například pokud zadáte `latest`verze, zobrazí se odkaz s konkrétní verzí, aby tento příkaz bylo možné použít ve skriptu sestavení deterministické. Také se zobrazí umístění binárního souboru, pokud dáváte přednost instalaci nebo stažení.

- **`-NoPath`**

  Je-li nastavena, instalační složka není exportována do cesty pro aktuální relaci. Ve výchozím nastavení skript upraví cestu, která zpřístupňuje nástroje rozhraní příkazového řádku hned po instalaci.

- **`-Verbose`**

  Zobrazí diagnostické informace.

- **`-AzureFeed`**

  Určuje adresu URL pro instalační službu Azure feed. Doporučujeme, abyste tuto hodnotu nezměnili. Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.

- **`-UncachedFeed`**

  Umožňuje změnit adresu URL informačního kanálu neuloženého v mezipaměti, který používá tento instalační program. Doporučujeme, abyste tuto hodnotu nezměnili.

- **`-NoCdn`**

  Zakáže stahování z [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) a používá neuložené kanály přímo.

- **`-FeedCredential`**

  Slouží jako řetězec dotazu, který se má připojit k datovému kanálu Azure. Umožňuje změnit adresu URL tak, aby používala neveřejné účty úložiště BLOB.

- **`-ProxyAddress`**

  Pokud je tato nastavení nastavena, instalační program při vytváření webových požadavků používá proxy server. (Platí jenom pro Windows)

- **`ProxyUseDefaultCredentials`**

  Pokud je nastaveno, instalační program při použití adresy proxy používá přihlašovací údaje aktuálního uživatele. (Platí jenom pro Windows)

- **`-SkipNonVersionedFiles`**

  Přeskočí instalaci souborů bez verze, jako je například *dotnet. exe*, pokud již existují.

- **`-Help`**

  Vytiskne nápovědu pro skript.

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

- Nainstalujte nejnovější verzi z kanálu 2,0 do zadaného umístění:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

- Instalace verze 1.1.0 sdíleného modulu runtime:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

- Získání skriptu a instalace verze 2.1.2 za podnikovým proxy serverem (pouze Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Získání skriptu a instalace .NET Core CLI v jednom-linii příkladech:

  Windows:

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -ssl https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Viz také:

- [Verze .NET Core](https://github.com/dotnet/core/releases)
- [Archiv rozhraní .NET Core Runtime a sady SDK ke stažení](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
