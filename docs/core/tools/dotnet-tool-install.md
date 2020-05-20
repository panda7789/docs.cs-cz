---
title: příkaz pro instalaci nástroje dotnet
description: Příkaz pro instalaci nástroje dotnet nainstaluje na váš počítač zadaný nástroj .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 067f90124833da537370a36934ff212aba7577f3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702810"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Name

`dotnet tool install`– Nainstaluje na váš počítač zadaný [nástroj .NET Core](global-tools.md) .

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a>Popis

`dotnet tool install`Příkaz nabízí způsob, jak nainstalovat nástroje .NET Core na váš počítač. Chcete-li použít příkaz, zadejte jednu z následujících možností instalace:

* Pokud chcete nainstalovat globální nástroj ve výchozím umístění, použijte `--global` možnost.
* Pokud chcete nainstalovat globální nástroj ve vlastním umístění, použijte `--tool-path` možnost.
* Chcete-li nainstalovat místní nástroj, vynechejte `--global` `--tool-path` Možnosti a.

**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**

Globální nástroje jsou ve výchozím nastavení nainstalovány v následujících adresářích při zadání `-g` Možnosti nebo `--global` :

| Operační systém          | Cesta                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Místní nástroje jsou přidány do souboru *dotnet-Tools. JSON* v adresáři *. config* v rámci aktuálního adresáře. Pokud soubor manifestu ještě neexistuje, vytvořte ho spuštěním následujícího příkazu:

```dotnetcli
dotnet new tool-manifest
```

Další informace najdete v tématu [instalace místního nástroje](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Arguments

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

  Určuje, že instalace je rozsáhlá pro uživatele. Nelze kombinovat s `--tool-path` možností. Vynechání obou `--global` a `--tool-path` určí instalaci místního nástroje.

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`tool-path <PATH>`**

  Určuje umístění, kam se má nainstalovat globální nástroj. Cesta může být absolutní nebo relativní. Pokud cesta neexistuje, příkaz se pokusí ho vytvořit. Vynechání obou `--global` a `--tool-path` určí instalaci místního nástroje.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .

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

## <a name="see-also"></a>Viz také

- [Nástroje .NET Core](global-tools.md)
- [Kurz: instalace a použití globálního nástroje .NET Core pomocí .NET Core CLI](global-tools-how-to-use.md)
- [Kurz: instalace a použití místního nástroje .NET Core pomocí .NET Core CLI](local-tools-how-to-use.md)
