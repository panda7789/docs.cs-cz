---
title: příkaz pro instalaci nástroje dotnet
description: Příkaz pro instalaci nástroje dotnet nainstaluje na váš počítač zadaný nástroj .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 2705defe9b77009ca1411da28dd86d144ccc19e6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543466"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet tool install` – nainstaluje na váš počítač zadaný [nástroj .NET Core](global-tools.md) .

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Popis

Příkaz `dotnet tool install` poskytuje způsob, jak nainstalovat nástroje .NET Core na váš počítač. Chcete-li použít příkaz, zadejte jednu z následujících možností instalace:

* Pokud chcete nainstalovat globální nástroj ve výchozím umístění, použijte možnost `--tool-path`.
* Pokud chcete nainstalovat globální nástroj ve vlastním umístění, použijte možnost `--tool-path`.
* Chcete-li nainstalovat místní nástroj, vynechejte možnosti `--global` a `--tool-path`.

**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**

Globální nástroje se ve výchozím nastavení nainstalují do následujících adresářů, když zadáte `-g` nebo `--global` možnosti:

| Operační systém          | Cesta                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Místní nástroje jsou přidány do souboru *nástroje-manifest. JSON* v adresáři *. config* v rámci aktuálního adresáře. Pokud soubor manifestu ještě neexistuje, vytvořte ho spuštěním následujícího příkazu:

```dotnetcli
dotnet new tool-manifest
```

Další informace najdete v tématu [instalace místního nástroje](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Název nebo ID balíčku NuGet, který obsahuje nástroj .NET Core, který se má nainstalovat

## <a name="options"></a>Možnosti

- **`add-source <SOURCE>`**

  Přidá další zdroj balíčku NuGet, který se použije při instalaci.

- **`configfile <FILE>`**

  Soubor konfigurace NuGet (*NuGet. config*), který se má použít.

- **`framework <FRAMEWORK>`**

  Určuje [cílovou platformu](../../standard/frameworks.md) pro instalaci nástroje pro. Ve výchozím nastavení se .NET Core SDK pokusí zvolit nejvhodnější cílové rozhraní.

- **`-g|--global`**

  Určuje, že instalace je rozsáhlá pro uživatele. Nelze kombinovat s možností `--tool-path`. Vynechání `--global` a `--tool-path` Určuje instalaci místního nástroje. 

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`tool-path <PATH>`**

  Určuje umístění, kam se má nainstalovat globální nástroj. Cesta může být absolutní nebo relativní. Pokud cesta neexistuje, příkaz se pokusí ho vytvořit. Vynechání `--global` a `--tool-path` Určuje instalaci místního nástroje. 

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.

- **`--version <VERSION_NUMBER>`**

  Verze nástroje, který se má nainstalovat Ve výchozím nastavení je nainstalovaná nejnovější stabilní verze balíčku. Tuto možnost použijte k instalaci verze Preview nebo starší verze nástroje.

## <a name="examples"></a>Příklady

- **`dotnet tool install -g dotnetsay`**

  Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj ve výchozím umístění.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj do konkrétního adresáře Windows.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj do konkrétního adresáře Linux/MacOS.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  Nainstaluje 2.0.0 verze [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj.

- **`dotnet tool install dotnetsay`**

  Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako místní Nástroj pro aktuální adresář.

## <a name="see-also"></a>Viz také:

- [Nástroje .NET Core](global-tools.md)
