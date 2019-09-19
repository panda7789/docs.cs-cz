---
title: příkaz pro instalaci nástroje dotnet
description: Instalační příkaz nástroje dotnet nainstaluje na svém počítači zadaný globální nástroj .NET Core.
ms.date: 05/29/2018
ms.openlocfilehash: d6f691117e93a39c9837b282dca19e452515c80a
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117469"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Name

`dotnet tool install`– Nainstaluje na váš počítač zadaný [globální nástroj .NET Core](global-tools.md) .

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Popis

`dotnet tool install` Příkaz nabízí způsob, jak na svém počítači nainstalovat globální nástroje .NET Core. Chcete-li použít příkaz, musíte určit, že chcete provést instalaci pro všechny uživatele pomocí `--global` možnosti, nebo zadat cestu k její instalaci `--tool-path` pomocí možnosti.

Globální nástroje jsou ve výchozím nastavení nainstalovány v následujících adresářích při zadání `-g` možnosti (nebo `--global`):

| OS          | Cesta                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Název nebo ID balíčku NuGet, který obsahuje globální nástroj .NET Core, který se má nainstalovat

## <a name="options"></a>Možnosti

`--add-source <SOURCE>`

Přidá další zdroj balíčku NuGet, který se použije při instalaci.

`--configfile <FILE>`

Soubor konfigurace NuGet (*NuGet. config*), který se má použít.

`--framework <FRAMEWORK>`

Určuje [cílovou platformu](../../standard/frameworks.md) pro instalaci nástroje pro. Ve výchozím nastavení se .NET Core SDK pokusí zvolit nejvhodnější cílové rozhraní.

`-g|--global`

Určuje, že instalace je rozsáhlá pro uživatele. Nelze kombinovat s `--tool-path` možností. Pokud tuto možnost nezadáte, musíte zadat `--tool-path` možnost.

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`--tool-path <PATH>`

Určuje umístění, kam se má nainstalovat globální nástroj. Cesta může být absolutní nebo relativní. Pokud cesta neexistuje, příkaz se pokusí ho vytvořit. Nelze kombinovat s `--global` možností. Pokud tuto možnost nezadáte, musíte zadat `--global` možnost.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`

`--version <VERSION_NUMBER>`

Verze nástroje, který se má nainstalovat Ve výchozím nastavení je nainstalovaná nejnovější stabilní verze balíčku. Tuto možnost použijte k instalaci verze Preview nebo starší verze nástroje.

## <a name="examples"></a>Příklady

Nainstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do výchozího umístění:

`dotnet tool install -g dotnetsay`

Nainstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do určité složky Windows:

`dotnet tool install dotnetsay --tool-path c:\global-tools`

Nainstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do konkrétní složky Linux/MacOS:

`dotnet tool install dotnetsay --tool-path ~/bin`

Nainstaluje 2.0.0 verze globálního nástroje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a>Viz také:

- [Globální nástroje .NET Core](global-tools.md)
