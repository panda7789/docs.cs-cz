---
title: DotNet – instalačních skriptů
description: Další informace o dotnet instalačních skriptů k instalaci nástroje rozhraní příkazového řádku .NET Core a sdílený modul runtime.
ms.date: 01/16/2019
ms.openlocfilehash: f796ac494c0be5458b3ea192e809a4d875bcc6dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608786"
---
# <a name="dotnet-install-scripts-reference"></a>odkazovat na DotNet instalačních skriptů

## <a name="name"></a>Název

`dotnet-install.ps1` | `dotnet-install.sh` -Skriptu pro instalaci nástroje rozhraní příkazového řádku .NET Core a sdílený modul runtime.

## <a name="synopsis"></a>Souhrn

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a>Popis

`dotnet-install` Skripty se používají k provedení instalace bez oprávnění správce systému .NET Core SDK, které zahrnují nástroje příkazového řádku .NET Core a sdílený modul runtime.

Doporučujeme použít stabilní verzi, která je hostována na [hlavní webové stránky .NET Core](https://dot.net). Přímé cesty pro skripty jsou:

* <https://dot.net/v1/dotnet-install.sh> (bash, UNIX)
* <https://dot.net/v1/dotnet-install.ps1> (Prostředí Powershell, Windows)

Hlavní užitečnost tyto skripty se scénáře automatizace a zařízení bez oprávnění správce. Existují dva skripty: jeden je skript prostředí PowerShell, který funguje ve Windows a druhá je skript bash, která funguje v systému Linux nebo macOS. Skripty mají stejné chování. Skriptu bash také přečte přepínače prostředí PowerShell, takže přepínače prostředí PowerShell můžete použít skript v systémech Linux nebo macOS s.

Instalační skripty stáhne soubor ZIP/tarballu z buildů rozhraní příkazového řádku a pokračovat v instalaci je ve výchozím umístění nebo v umístění určeném `-InstallDir|--install-dir`. Ve výchozím nastavení instalační skripty stáhnout sadu SDK a nainstalujte ho. Pokud chcete jen získat sdílený modul runtime, zadejte `--shared-runtime` argument.

Ve výchozím nastavení přidá skript umístění instalace $PATH pro aktuální relaci. Toto výchozí chování přepsat tak, že zadáte `--no-path` argument.

Před spuštěním skriptu, instalaci požadovaných [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

Můžete nainstalovat konkrétní verzi pomocí `--version` argument. Verze musí být zadán jako část třídílné verze (například 1.0.0-13232). Pokud se nezadá, použije `latest` verze.

## <a name="options"></a>Možnosti

* **`-Channel <CHANNEL>`**

  Určuje zdroj kanálu pro instalaci. Možné hodnoty jsou:

  * `Current` -Nejaktuálnější verze.
  * `LTS` – Dlouhodobé kanál podpory (nejnovější podporovanou verzi).
  * Verze dvěma částmi ve formátu X.Y představující konkrétní verze (například `2.0` nebo `1.0`).
  * Název větve. Například `release/2.0.0`, `release/2.0.0-preview2`, nebo `master` (pro noční vydání).

  Výchozí hodnota je `LTS`. Další informace o kanály podpory .NET najdete v článku [zásady podpory .NET](https://www.microsoft.com/net/platform/support-policy#dotnet-core) stránky.

* **`-Version <VERSION>`**

  Představuje verzi konkrétního sestavení. Možné hodnoty jsou:

  * `latest` -Nejnovější build na kanálu (používá se `-Channel` možnost).
  * `coherent` -Nejnovější souvislé sestavení na kanálu; používá kombinaci nejnovější stabilní balíček (používá se název větve `-Channel` možnosti).
  * Verze třemi částmi ve formátu X.Y.Z představující konkrétní sestavení verze; nahrazuje `-Channel` možnost. Například: `2.0.0-preview2-006120`.

  Pokud není zadán, `-Version` výchozí hodnota je `latest`.

* **`-InstallDir <DIRECTORY>`**

  Určuje cestu instalace. Adresář se vytvoří, pokud neexistuje. Výchozí hodnota je *%LocalAppData%\Microsoft\dotnet*. Binární soubory jsou umístěny přímo v tomto adresáři.

* **`-Architecture <ARCHITECTURE>`**

  Architektury .NET Core binární soubory pro instalaci. Možné hodnoty jsou `<auto>`, `amd64`, `x64`, `x86`, `arm64`, a `arm`. Výchozí hodnota je `<auto>`, která představuje aktuálně spuštěné Architektura operačního systému.

* **`-SharedRuntime`**

  > [!NOTE]
  > Tento parametr je zastaralá a v budoucí verzi souboru, který může být odebrán. Doporučenou alternativou je `Runtime` možnost.

  Nainstaluje pouze bity sdílený modul runtime, ne celou sadu SDK. To je ekvivalentní se zadáním `-Runtime dotnet`.

* **`-Runtime <RUNTIME>`**

  Nainstaluje jenom sdílený modul runtime, ne celou sadu SDK. Možné hodnoty jsou:

  * `dotnet` - `Microsoft.NETCore.App` sdílený modul runtime.
  * `aspnetcore` - `Microsoft.AspNetCore.App` sdílený modul runtime.

* **`-DryRun`**

  Pokud nastavíte, neprovede skriptu instalace. Místo toho zobrazí jaké příkazový řádek použitý k instalaci konzistentně aktuálně požadovanou verzi rozhraní příkazového řádku .NET Core. Například, pokud zadáte verze `latest`, zobrazí odkaz s konkrétní verzí tak, aby tento příkaz můžete použít nepodmíněně ve skriptu buildu. Pokud chcete nainstalovat nebo stáhnout sami umístění binárního souboru, zobrazí se také.

* **`-NoPath`**

  Pokud sada instalační složky sady neexportoval k cestě pro aktuální relaci. Ve výchozím nastavení skript změní cesty, která díky nástrojům rozhraní příkazového řádku k dispozici okamžitě po instalaci.

* **`-Verbose`**

  Zobrazí diagnostické informace.

* **`-AzureFeed`**

  Určuje že adresu URL pro Azure informačního kanálu do instalačního programu. Doporučujeme tuto hodnotu nechcete změnit. Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.

* **`-UncachedFeed`**

  Umožňuje změnit adresu URL bez mezipaměti kanál používá tento instalační program. Doporučujeme tuto hodnotu nechcete změnit.

* **`-NoCdn`**

  Zakáže stahování [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) a mezipamětí informační kanál používá přímo.

* **`-FeedCredential`**

  Použít jako řetězec dotazu pro připojení k Azure informačního kanálu. To umožňuje změnit adresu URL, aby používaly účty úložiště blob neveřejné.

* **`-ProxyAddress`**

  Pokud sada, instalační program používá proxy server při vytváření webových požadavků. (Platí jenom pro Windows)

* **`ProxyUseDefaultCredentials`**

  Pokud sada, instalační program používá přihlašovací údaje aktuálního uživatele při použití adresa proxy serveru. (Platí jenom pro Windows)

* **`-SkipNonVersionedFiles`**

  Přeskočí instalaci bez správy verzí souborů, jako například *dotnet.exe*, pokud ještě neexistuje.

* **`-Help`**

  Vytiskne nápovědy pro skript.

## <a name="examples"></a>Příklady

* Nainstalujte nejnovější dlouhodobé podporovanou verzi (LTS) do výchozího umístění:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

* Nainstalujte nejnovější verzi z 2.0 kanál do zadaného umístění:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

* Nainstalujte 1.1.0 verzi sdílený modul runtime:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -SharedRuntime -Version 1.1.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --shared-runtime --version 1.1.0
  ```

* Získat skript a nainstalovat 2.1.2 verze za firemním proxy (jenom Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

* Získat skript a nainstalovat rozhraní příkazového řádku .NET Core one-liner příklady:

  Windows:

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Viz také:

- [Verze .NET core](https://github.com/dotnet/core/releases)
- [.NET core Runtime a sadu SDK stáhněte archiv](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
