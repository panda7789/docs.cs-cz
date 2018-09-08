---
title: DotNet – instalačních skriptů
description: Další informace o dotnet instalačních skriptů k instalaci nástroje rozhraní příkazového řádku .NET Core a sdílený modul runtime.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.openlocfilehash: 8d1c6ebb30bd45575bb61206799c9c3e5c47ff0c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140694"
---
# <a name="dotnet-install-scripts-reference"></a>odkazovat na DotNet instalačních skriptů

## <a name="name"></a>Název

`dotnet-install.ps1` | `dotnet-install.sh` -Skriptu pro instalaci nástroje rozhraní příkazového řádku .NET Core a sdílený modul runtime.

## <a name="synopsis"></a>Souhrn

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

macOS nebo Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a>Popis

`dotnet-install` Skripty se používají k provedení instalace bez oprávnění správce systému .NET Core SDK, které zahrnují nástroje příkazového řádku .NET Core a sdílený modul runtime.

Doporučujeme použít stabilní verzi, která je hostována na [hlavní webové stránky .NET Core](https://dot.net). Přímé cesty pro skripty jsou:

* https://dot.net/v1/dotnet-install.sh (bash, UNIX)
* https://dot.net/v1/dotnet-install.ps1 (Prostředí Powershell, Windows)

Hlavní užitečnost tyto skripty se scénáře automatizace a zařízení bez oprávnění správce. Existují dva skripty: jeden je skript prostředí PowerShell, který funguje ve Windows. Tento skript je skriptu bash, která funguje v systému Linux/macOS. Skripty mají stejné chování. Skriptu bash také přečte přepínače prostředí PowerShell, takže přepínače prostředí PowerShell můžete použít skript v systémech Linux nebo macOS s.

Instalační skripty stáhne soubor ZIP/tarballu z buildů rozhraní příkazového řádku a pokračovat v instalaci je ve výchozím umístění nebo v umístění určeném `-InstallDir|--install-dir`. Ve výchozím nastavení instalační skripty stáhnout sadu SDK a nainstalujte ho. Pokud chcete jen získat sdílený modul runtime, zadejte `--shared-runtime` argument.

Ve výchozím nastavení přidá skript umístění instalace $PATH pro aktuální relaci. Toto výchozí chování přepsat tak, že zadáte `--no-path` argument.

Před spuštěním skriptu, instalaci požadovaných [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

Můžete nainstalovat konkrétní verzi pomocí `--version` argument. Verze musí být zadán jako část 3 verze (například 1.0.0-13232). Pokud tento parametr vynechán, použije `latest` verze.

## <a name="options"></a>Možnosti

`-Channel <CHANNEL>`

Určuje zdroj kanálu pro instalaci. Možné hodnoty jsou:

- `Current` -Aktuální verze
- `LTS` – Dlouhodobé kanál podpory (aktuální podporovanou verzi)
- Verze dvěma částmi ve formátu X.Y představující konkrétní verze (například `2.0` nebo `1.0`)
- Název větve [například `release/2.0.0`, `release/2.0.0-preview2`, nebo `master` pro informace o novinkách od `master` větev ("vykrvení hrany" noční vydání)]

Výchozí hodnota je `LTS`. Další informace o kanály podpory .NET najdete v článku [životní cyklus podpory na .NET Core](https://www.microsoft.com/net/core/support) tématu.

`-Version <VERSION>`

Představuje verzi konkrétního sestavení. Možné hodnoty jsou:

- `latest` -Nejnovější build na kanálu (používá se `-Channel` možnost)
- `coherent` -Nejnovější souvislé sestavení na kanálu; používá kombinaci nejnovější stabilní balíček (používá se název větve `-Channel` možnosti)
- Verze třemi částmi ve formátu X.Y.Z představující konkrétní sestavení verze; nahrazuje `-Channel` možnost. Příklad: `2.0.0-preview2-006120`

Pokud tento parametr vynechán, `-Version` výchozí hodnota je `latest`.

`-InstallDir <DIRECTORY>`

Určuje cestu instalace. Adresář se vytvoří, pokud neexistuje. Výchozí hodnota je *% LocalAppData %\.dotnet*. Všimněte si, že binární soubory jsou umístěné přímo v adresáři.

`-Architecture <ARCHITECTURE>`

Architektury .NET Core binární soubory pro instalaci. Možné hodnoty jsou `auto`, `x64`, a `x86`. Výchozí hodnota je `auto`, která představuje aktuálně spuštěné Architektura operačního systému.

`-SharedRuntime`

Pokud nastavíte, tento přepínač omezuje na sdílený modul runtime instalace. Celá sada SDK není nainstalovaná.

`-DryRun`

Pokud nastavíte, neprovede skriptu instalace; ale místo toho zobrazí jaké příkazový řádek použitý k instalaci konzistentně aktuálně požadovanou verzi rozhraní příkazového řádku .NET Core. Například pokud zadáte verze `latest`, zobrazí odkaz s konkrétní verzí tak, aby tento příkaz můžete použít nepodmíněně ve skriptu buildu. Pokud chcete nainstalovat nebo stáhnout sami umístění binárního souboru, zobrazí se také.

`-NoPath`

Pokud nastavíte, předponu/installdir se nebudou exportovat do cesty pro aktuální relaci. Ve výchozím nastavení bude skript upravte CESTU, která díky nástrojům rozhraní příkazového řádku k dispozici okamžitě po instalaci.

`-AzureFeed`

Určuje že adresu URL pro Azure informačního kanálu do instalačního programu. Nedoporučujeme tuto hodnotu změnit. Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.

`-ProxyAddress`

Pokud sada, instalační program používá proxy server při vytváření webových požadavků. (Platí jenom pro Windows)

`--verbose`

Zobrazit diagnostické informace.

`--help`

Vytiskne nápovědy pro skript.

## <a name="examples"></a>Příklady

Nainstalujte nejnovější dlouhodobé podporovanou verzi (LTS) do výchozího umístění:

Windows:

`./dotnet-install.ps1 -Channel LTS`

macOS nebo Linux:

`./dotnet-install.sh --channel LTS`

Nainstalujte nejnovější verzi z 2.0 kanál do zadaného umístění:

Windows:

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

macOS nebo Linux:

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

Nainstalujte 1.1.0 verzi sdílený modul runtime:

Windows:

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

macOS nebo Linux:

`./dotnet-install.sh --shared-runtime --version 1.1.0`

Získat skript a nainstalovat rozhraní příkazového řádku .NET Core one-liner příklady:

Windows:

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

macOS nebo Linux:

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a>Viz také:

* [Verze .NET core](https://github.com/dotnet/core/releases)
* [.NET core Runtime a sadu SDK stáhněte archiv](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
