---
title: skriptů instalace DotNet.
description: Další informace o skriptů dotnet instalace k instalaci nástroje příkazového řádku .NET Core a sdílený modul runtime.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.openlocfilehash: acdf49950ebb49751c55ae72b3f623e590489202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-install-scripts-reference"></a>referenční skriptů instalace DotNet.

## <a name="name"></a>Název

`dotnet-install.ps1` | `dotnet-install.sh` -Skriptu použít k instalaci nástroje příkazového řádku .NET Core a sdílený modul runtime.

## <a name="synopsis"></a>Stručný obsah

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

systému macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a>Popis

`dotnet-install` Skripty se používají k provedení instalace bez oprávnění správce systému .NET Core SDK, která zahrnuje nástroje příkazového řádku .NET Core a sdílený modul runtime.

Doporučujeme použít stabilní verze, která je hostovaná na [hlavní webové stránky .NET Core](https://dot.net). Přímé cest k skripty jsou:

* https://dot.net/v1/dotnet-install.sh (bash, UNIX)
* https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)

Hlavní užitečnost tyto skripty se automatizace scénáře a instalace bez oprávnění správce. Existují dva skripty: jeden je skript prostředí PowerShell, který funguje v systému Windows. Další skript je bash skript, který funguje na systému Linux nebo macOS. Oba skripty mají stejné chování. Skript bash také přečte přepínače prostředí PowerShell, abyste je mohli používat přepínače prostředí PowerShell pomocí skriptu v systémech Linux/systému macOS. 

Skripty instalace stáhnout soubor ZIP nebo tarball z vyřazuje sestavení rozhraní příkazového řádku a přejděte k jeho instalaci ve výchozím umístění nebo do umístění určeného `-InstallDir|--install-dir`. Ve výchozím nastavení instalační skripty stažení sady SDK a nainstalujte ji. Pokud chcete jen získat sdílený modul runtime, zadejte `--shared-runtime` argument. 

Ve výchozím nastavení přidá skript umístění instalace $PATH pro aktuální relaci. Toto výchozí chování potlačit zadáním `--no-path` argument. 

Před spuštěním skriptu nainstalujte požadované [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

Můžete nainstalovat konkrétní verzi pomocí `--version` argument. Verze musí být zadán jako část 3 verze (například 1.0.0-13232). Pokud se vynechá, použije `latest` verze.

## <a name="options"></a>Možnosti

`-Channel <CHANNEL>`

Určuje zdroj kanál pro instalaci. Možné hodnoty jsou:

- `Current` -Aktuální verzi
- `LTS` -Dlouhodobé podporu kanál (aktuální podporovanou verzi)
- Dvě části verze ve formátu X.Y představující konkrétní vydání (například `2.0` nebo `1.0`)
- Název větve [například `release/2.0.0`, `release/2.0.0-preview2`, nebo `master` nejnovější z `master` větve ("vykrvení edge" noční verzích)]

Výchozí hodnota je `LTS`. Další informace o kanály podpory rozhraní .NET najdete v tématu [životní cyklus podpory na .NET Core](https://www.microsoft.com/net/core/support) tématu.

`-Version <VERSION>`

Představuje verzi konkrétní sestavení. Možné hodnoty jsou:

- `latest` -Nejnovější sestavení na kanálu (používá se `-Channel` možnost)
- `coherent` -Nejnovější souvislý sestavení na kanálu; používá kombinaci nejnovější stabilní balíčku (použít s názvu větve `-Channel` možnosti)
- Verze třemi částmi ve formátu X.Y.Z představující konkrétní sestavení verze; nahrazuje `-Channel` možnost. Například: `2.0.0-preview2-006120`

Pokud tento parametr vynechán, `-Version` výchozí `latest`.

`-InstallDir <DIRECTORY>`

Určuje cestu instalace. Daný adresář je vytvořen, pokud neexistuje. Výchozí hodnota je *LocalAppData %\.dotnet*. Všimněte si, že binární soubory jsou umístěny přímo v adresáři.

`-Architecture <ARCHITECTURE>`

Architektura .NET Core binární soubory pro instalaci. Možné hodnoty jsou `auto`, `x64`, a `x86`. Výchozí hodnota je `auto`, který reprezentuje probíhající architektury operačního systému.

`-SharedRuntime`

Pokud nastavíte, tento přepínač omezuje na sdílený modul runtime instalace. Celá sada SDK není nainstalována.

`-DryRun`

Pokud nastavíte, neprovede skript instalace; ale místo toho zobrazí jaké příkazového řádku pomocí konzistentně nainstalovat aktuálně požadovanou verzi rozhraní příkazového řádku .NET Core. Například pokud zadejte verzi `latest`, se zobrazí odkaz s konkrétní verzi, aby tento příkaz lze použít nepodmíněně ve skriptu buildu. Pokud chcete nainstalovat nebo stáhnout sami umístění na binární soubor, zobrazí se také.

`-NoPath`

Pokud nastavíte, předponu/installdir neexportují k cestě pro aktuální relaci. Ve výchozím nastavení bude skript upravit cesta, která zpřístupňuje nástrojů příkazového řádku okamžitě po instalaci.

`-AzureFeed`

Určuje, že adresa URL pro Azure kanálu pro instalační program. Není doporučeno tuto hodnotu změnit. Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.

`-ProxyAddress`

Pokud sadu, instalační program používá proxy server při vytváření webových požadavků. (Platné pouze pro Windows)

`--verbose`

Zobrazit diagnostické informace.

`--help`

Vytiskne nápovědy pro skript.

## <a name="examples"></a>Příklady

Nainstalujte nejnovější dlouhodobé podporovanou verzi (LTS) do výchozího umístění:

Windows:

`./dotnet-install.ps1 -Channel LTS`

systému macOS/Linux:

`./dotnet-install.sh --channel LTS`

Nainstalujte nejnovější verzi z 2.0 kanálu do zadaného umístění:

Windows:

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

systému macOS/Linux:

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

Nainstalujte 1.1.0 verzi sdílený modul runtime:

Windows:

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

systému macOS/Linux:

`./dotnet-install.sh --shared-runtime --version 1.1.0`

Získat skript a nainstalovat .NET Core rozhraní příkazového řádku one-liner příklady:

Windows:

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

systému macOS/Linux:

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a>Viz také

[Verze .NET core](https://github.com/dotnet/core/releases)   
[.NET core Runtime a sadu SDK stáhněte archivu](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
