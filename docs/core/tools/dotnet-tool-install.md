---
title: dotnet nástroj instalace, příkaz
description: Příkaz instalace nástroje dotnet nainstaluje do počítače zadaný nástroj .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 723d25caa6009288dbb55d55f173b04d7b983450
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463366"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Název

`dotnet tool install`- Nainstaluje do počítače zadaný [nástroj .NET Core.](global-tools.md)

## <a name="synopsis"></a>Synopse

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

Příkaz `dotnet tool install` umožňuje instalaci nástrojů .NET Core do počítače. Chcete-li použít příkaz, zadejte jednu z následujících možností instalace:

* Chcete-li nainstalovat globální nástroj do `--global` výchozího umístění, použijte tuto možnost.
* Chcete-li nainstalovat globální nástroj do `--tool-path` vlastního umístění, použijte tuto možnost.
* Chcete-li nainstalovat místní nástroj, `--global` `--tool-path` vynechte možnosti a.

**Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.**

Globální nástroje jsou nainstalovány v následujících adresářích ve výchozím nastavení, když zadáte `-g` možnost nebo: `--global`

| Operační systém          | Cesta                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Místní nástroje jsou přidány do souboru *tool-manifest.json* v *adresáři .config* pod aktuálním adresářem. Pokud soubor manifestu ještě neexistuje, vytvořte jej spuštěním následujícího příkazu:

```dotnetcli
dotnet new tool-manifest
```

Další informace naleznete [v tématu Instalace místního nástroje](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Název/ID balíčku NuGet, který obsahuje nástroj .NET Core k instalaci.

## <a name="options"></a>Možnosti

- **`add-source <SOURCE>`**

  Přidá další zdroj balíčku NuGet pro použití během instalace.

- **`configfile <FILE>`**

  Soubor konfigurace NuGet (*nuget.config).*

- **`framework <FRAMEWORK>`**

  Určuje [cílovou architekturu,](../../standard/frameworks.md) pro kterou má být nástroj nainstalován. Ve výchozím nastavení se sada .NET Core SDK pokusí vybrat nejvhodnější cílovou architekturu.

- **`-g|--global`**

  Určuje, že instalace je široká jako uživatel. Nelze kombinovat s `--tool-path` možností. Vynechání obou `--global` `--tool-path` a určuje instalaci místního nástroje.

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`tool-path <PATH>`**

  Určuje umístění, kam má být globální nástroj nainstalován. CESTA může být absolutní nebo relativní. Pokud cesta neexistuje, příkaz se pokusí vytvořit. Vynechání obou `--global` `--tool-path` a určuje instalaci místního nástroje.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .

- **`--version <VERSION_NUMBER>`**

  Verze nástroje k instalaci. Ve výchozím nastavení je nainstalována nejnovější stabilní verze balíčku. Tuto možnost použijte k instalaci náhledu nebo starších verzí nástroje.

## <a name="examples"></a>Příklady

- **`dotnet tool install -g dotnetsay`**

  Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj ve výchozím umístění.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj v určitém adresáři systému Windows.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj v určitém adresáři Linux / macOS.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  Nainstaluje verzi 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj.

- **`dotnet tool install dotnetsay`**

  Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako místní nástroj pro aktuální adresář.

## <a name="see-also"></a>Viz také

- [Nástroje .NET Core](global-tools.md)
- [Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET](global-tools-how-to-use.md)
- [Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET](local-tools-how-to-use.md)
