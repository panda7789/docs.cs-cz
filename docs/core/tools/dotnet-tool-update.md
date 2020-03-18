---
title: dotnet nástroj aktualizovat, příkaz
description: Příkaz aktualizace nástroje dotnet aktualizuje zadaný nástroj .NET Core v počítači.
ms.date: 02/14/2020
ms.openlocfilehash: 497b052a8b9cfa9dca8d80316075fe7565d6b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847817"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet tool update`- Aktualizuje zadaný [nástroj .NET Core v](global-tools.md) počítači.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME> <--tool-path>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <-h|--help>
```

## <a name="description"></a>Popis

Příkaz `dotnet tool update` poskytuje způsob, jak aktualizovat nástroje .NET Core v počítači na nejnovější stabilní verzi balíčku. Příkaz odinstaluje a přeinstaluje nástroj, efektivně jej aktualizuje. Chcete-li použít příkaz, zadejte jednu z následujících možností:

* Chcete-li aktualizovat globální nástroj, který byl `--global` nainstalován ve výchozím umístění, použijte možnost
* Chcete-li aktualizovat globální nástroj, který byl `--tool-path` nainstalován ve vlastním umístění, použijte tuto možnost.
* Chcete-li aktualizovat místní nástroj, `--global` `--tool-path` vynechte možnosti a.

**Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.**

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Název/ID balíčku NuGet, který obsahuje globální nástroj .NET Core, který má být aktualizován. Název balíčku můžete najít pomocí příkazu [seznamu nástrojů dotnet.](dotnet-tool-list.md)

## <a name="options"></a>Možnosti

- **`--add-source <SOURCE>`**

  Přidá další zdroj balíčku NuGet pro použití během instalace.

- **`--configfile <FILE>`**

  Soubor konfigurace NuGet (*nuget.config).*

- **`--framework <FRAMEWORK>`**

  Určuje [cílovou architekturu,](../../standard/frameworks.md) pro kterou má být nástroj aktualizován.

- **`-g|--global`**

  Určuje, že aktualizace je určen pro nástroj pro celý uživatele. Nelze kombinovat s `--tool-path` možností. Vynechání obou `--global` `--tool-path` a určuje, že nástroj, který má být aktualizován, je místní nástroj.

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--tool-path <PATH>`**

  Určuje umístění, kde je globální nástroj nainstalován. CESTA může být absolutní nebo relativní. Nelze kombinovat s `--global` možností. Vynechání obou `--global` `--tool-path` a určuje, že nástroj, který má být aktualizován, je místní nástroj.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .

## <a name="examples"></a>Příklady

- **`dotnet tool update -g dotnetsay`**

  Aktualizuje globální nástroj [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři systému Windows.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři Linux/macOS.

- **`dotnet tool update dotnetsay`**

  Aktualizuje místní nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) nainstalovaný pro aktuální adresář.

## <a name="see-also"></a>Viz také

- [Nástroje .NET Core](global-tools.md)
- [Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET](global-tools-how-to-use.md)
- [Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET](local-tools-how-to-use.md)
