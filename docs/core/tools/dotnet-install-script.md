---
title: dotnet-install scripts
description: Přečtěte si o skriptech dotnet-install pro instalaci sady .NET Core SDK a sdíleného běhu.
ms.date: 01/23/2020
ms.openlocfilehash: 591413a17db577560bd0324995066c8ea7a35895
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463678"
---
# <a name="dotnet-install-scripts-reference"></a>Odkaz na skripty dotnet-install

## <a name="name"></a>Název

`dotnet-install.ps1` | `dotnet-install.sh`- Skript používaný k instalaci sady .NET Core SDK a sdíleného běhu.

## <a name="synopsis"></a>Synopse

Windows:

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

dotnet-install.ps1 -Help
```

Linux/macOs:

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a>Popis

Skripty `dotnet-install` se používají k provedení instalace sady .NET Core SDK bez oprávnění správce, která zahrnuje rozhraní .NET Core CLI a sdílený běh.

Doporučujeme používat stabilní verzi skriptů:

- Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh>
- Prostředí PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1>

Hlavní užitečnost těchto skriptů je ve scénářích automatizace a instalace bez správce. Existují dva skripty: jeden je skript PowerShell, který funguje v systému Windows, a druhý je bash skript, který funguje na Linux / macOS. Oba skripty mají stejné chování. Bash skript také čte PowerShell přepínače, takže můžete použít PowerShell přepínače se skriptem na Linux / macOS systémy.

Instalační skripty stáhnout soubor ZIP/tarball z sestavení rozhraní CLI klesne a pokračovat v instalaci `-InstallDir|--install-dir`ve výchozím umístění nebo v umístění určeném . Ve výchozím nastavení instalační skripty stáhnout sadu SDK a nainstalovat. Pokud chcete získat pouze sdílený runtime, `-Runtime|--runtime` zadejte argument.

Ve výchozím nastavení skript přidá umístění instalace do $PATH pro aktuální relaci. Toto výchozí chování přepište `-NoPath|--no-path` zadáním argumentu.

Před spuštěním skriptu nainstalujte požadované [závislosti](../install/dependencies.md).

Pomocí argumentu můžete nainstalovat `-Version|--version` určitou verzi. Verze musí být zadána jako třídílná `2.1.0`verze (například ). Pokud není k dispozici, `latest` používá verzi.

## <a name="options"></a>Možnosti

- **`-Architecture|--architecture <ARCHITECTURE>`**

  Architektura binárních souborů .NET Core, které chcete nainstalovat. Možné hodnoty `<auto>` `amd64`jsou `x64` `x86`, `arm64`, `arm`, , a . Výchozí hodnota `<auto>`je , která představuje aktuálně spuštěnou architekturu operačního systému.

- **`-AzureFeed|--azure-feed`**

  Určuje adresu URL zdroje Azure instalačnímu programu. Doporučujeme, abyste tuto hodnotu neměnili. Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.

- **`-Channel|--channel <CHANNEL>`**

  Určuje zdrojový kanál pro instalaci. Možné hodnoty jsou:

  - `Current`- Nejaktuálnější vydání.
  - `LTS`- Kanál dlouhodobé podpory (nejaktuálnější podporovaná verze).
  - Dvoudílná verze ve formátu X.Y představující konkrétní `2.1` verzi `3.0`(například nebo ).
  - Název pobočky: `release/3.1.1xx` například, nebo `master` (pro noční zprávy). Tuto možnost použijte k instalaci verze z kanálu náhledu. Použijte název kanálu uvedený v [části Instalační programy a binární soubory](https://github.com/dotnet/core-sdk#installers-and-binaries).

  Výchozí hodnota je `LTS`. Další informace o kanálech podpory rozhraní .NET naleznete na stránce [zásad podpory rozhraní .NET.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

- **`-DryRun|--dry-run`**

  Pokud je nastavena, skript nebude provádět instalaci. Místo toho zobrazí, jaký příkazový řádek použít k onisnok nainstalovat aktuálně požadovanou verzi rozhraní příkazového příkazu .NET Core. Pokud například zadáte `latest`verzi , zobrazí se odkaz s konkrétní verzí, aby bylo možné tento příkaz deterministicky použít ve skriptu sestavení. Zobrazuje také umístění binárního souboru, pokud dáváte přednost instalaci nebo stažení sami.

- **`-FeedCredential|--feed-credential`**

  Používá se jako řetězec dotazu pro připojení k kanálu Azure. Umožňuje změnit adresu URL tak, aby používala neveřejné účty úložiště objektů blob.

- **`-Help|--help`**

  Vytiskne nápovědu pro skript.

- **`-InstallDir|--install-dir <DIRECTORY>`**

  Určuje instalační cestu. Adresář je vytvořen, pokud neexistuje. Výchozí hodnota je *%LocalAppData%\Microsoft\dotnet*. Binární soubory jsou umístěny přímo v tomto adresáři.

- **`-JSonFile|--jsonfile <JSONFILE>`**

  Určuje cestu k souboru [global.json,](global-json.md) který bude použit k určení verze sady SDK. Soubor *global.json* musí mít `sdk:version`hodnotu pro .

- **`-NoCdn|--no-cdn`**

  Zakáže stahování ze [sítě pro doručování obsahu Azure (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) a přímo používá kanál bez mezipaměti.

- **`-NoPath|--no-path`**

  Pokud je nastavena, instalační složka není exportována do cesty pro aktuální relaci. Ve výchozím nastavení skript upravuje PATH, který zpřístupňuje rozhraní CLI jádra .NET ihned po instalaci.

- **`-ProxyAddress`**

  Pokud je nastavena, instalační program používá proxy server při vytváření webových požadavků. (Platí pouze pro systém Windows.)

- **`ProxyUseDefaultCredentials`**

  Pokud je nastaveno, instalační program používá pověření aktuálního uživatele při použití proxy adresy. (Platí pouze pro systém Windows.)

- **`-Runtime|--runtime <RUNTIME>`**

  Nainstaluje pouze sdílený runtime, nikoli celou sadu SDK. Možné hodnoty jsou:

  - `dotnet`- `Microsoft.NETCore.App` sdíleného běhu.
  - `aspnetcore`- `Microsoft.AspNetCore.App` sdíleného běhu.
  - `windowsdesktop`- `Microsoft.WindowsDesktop.App` sdíleného běhu.

- **`--runtime-id <RID>`**

  Určuje [identifikátor za běhu,](../rid-catalog.md) pro který jsou nástroje instalovány. Používá `linux-x64` se pro přenosný Linux. (Platí pouze pro Linux/macOS.)

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > Tento parametr je zastaralý a může být odebrán v budoucí verzi skriptu. Doporučenou alternativou `-Runtime|--runtime` je možnost.

  Nainstaluje pouze sdílené bity runtime, nikoli celou sadu SDK. Tato možnost je ekvivalentní `-Runtime|--runtime dotnet`určení .

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  Přeskočí instalaci souborů s neverzí, například *dotnet.exe*, pokud již existují.

- **`-UncachedFeed|--uncached-feed`**

  Umožňuje změnu adresy URL informačního kanálu bez mezipaměti používaného tímto instalačním programem. Doporučujeme, abyste tuto hodnotu neměnili.

- **`-Verbose|--verbose`**

  Zobrazí diagnostické informace.

- **`-Version|--version <VERSION>`**

  Představuje konkrétní verzi sestavení. Možné hodnoty jsou:

  - `latest`- Nejnovější stavět na kanálu `-Channel` (používá se s možností).
  - `coherent`- Nejnovější koherentní stavět na kanálu; používá nejnovější stabilní kombinaci balíčků `-Channel` (používá se s možnostmi názvu větve).
  - Třídílná verze ve formátu X.Y.Z představující konkrétní verzi sestavení; nahrazuje `-Channel` tuto možnost. Například: `2.0.0-preview2-006120`.

  Pokud není `-Version` zadán, `latest`výchozí hodnota je .

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

- Nainstalujte nejnovější verzi z kanálu 3.1 do určeného umístění:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- Nainstalujte verzi sdíleného runtime 3.0.0:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- Získejte skript a nainstalujte verzi 2.1.2 za podnikový proxy server (pouze systém Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Získat skript a nainstalovat příklady rozhraní .NET Core CLI s jednou vložkou:

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

- [Verze jádra .NET](https://github.com/dotnet/core/releases)
- [Archiv stahování .NET Core Runtime a SDK](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
