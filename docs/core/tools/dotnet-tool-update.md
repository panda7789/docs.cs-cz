---
title: příkaz pro aktualizaci nástroje dotnet
description: Příkaz pro aktualizaci nástroje dotnet aktualizuje zadaný nástroj .NET Core na vašem počítači.
ms.date: 07/08/2020
ms.openlocfilehash: a212fbb40af68019c1bc9a63963d960292be6b08
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308868"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet tool update`– Aktualizuje zadaný [nástroj .NET Core](global-tools.md) na vašem počítači.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a>Popis

`dotnet tool update`Příkaz nabízí způsob, jak aktualizovat nástroje .NET Core na vašem počítači na nejnovější stabilní verzi balíčku. Příkaz odinstaluje a znovu nainstaluje nástroj a efektivně ho aktualizuje. Chcete-li použít příkaz, zadejte jednu z následujících možností:

* Pokud chcete aktualizovat globální nástroj, který byl nainstalovaný ve výchozím umístění, použijte `--global` možnost.
* Chcete-li aktualizovat globální nástroj, který byl nainstalován ve vlastním umístění, použijte `--tool-path` možnost.
* Pokud chcete aktualizovat místní nástroj, použijte `--local` možnost.

**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**

## <a name="arguments"></a>Arguments

- **`PACKAGE_ID`**

  Název nebo ID balíčku NuGet, který obsahuje globální nástroj .NET Core, který se má aktualizovat Název balíčku můžete najít pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .

## <a name="options"></a>Možnosti

- **`--add-source <SOURCE>`**

  Přidá další zdroj balíčku NuGet, který se použije při instalaci.

- **`--configfile <FILE>`**

  Soubor konfigurace NuGet (*nuget.config*), který se má použít.

- **`--disable-parallel`**

  Zabránit v paralelním obnovení více projektů.

- **`--framework <FRAMEWORK>`**

  Určuje [cílovou platformu](../../standard/frameworks.md) , pro kterou chcete nástroj aktualizovat.

- **`--ignore-failed-sources`**

  Považovat selhání zdroje balíčku za upozornění.

- **`--interactive`**

  Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).

- **`--local`**

  Aktualizujte nástroj a manifest místního nástroje. Nelze kombinovat s `--global` možností nebo `--tool-path` možností.

- **`--no-cache`**

  Neukládat balíčky a požadavky HTTP do mezipaměti.

- **`--tool-manifest <PATH>`**

  Cesta k souboru manifestu.

- **`--tool-path <PATH>`**

  Určuje umístění, kde je nainstalován globální nástroj. Cesta může být absolutní nebo relativní. Nelze kombinovat s `--global` možností. Vynechání obou `--global` a `--tool-path` určí, že nástroj, který má být aktualizován, je místní nástroj.

- **`--version <VERSION>`**

  Rozsah verzí balíčku nástroje, na který se má aktualizace aktualizovat Tato verze se nedá použít k downgradům verzí, ale `uninstall` nejdřív je potřeba novější verze.

- **`-g|--global`**

  Určuje, že je aktualizace určena pro nástroj pro uživatelský rozsah. Nelze kombinovat s `--tool-path` možností. Vynechání obou `--global` a `--tool-path` určí, že nástroj, který má být aktualizován, je místní nástroj.

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .

## <a name="examples"></a>Příklady

- **`dotnet tool update -g dotnetsay`**

  Aktualizuje nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global.

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři Windows.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři Linux/MacOS.

- **`dotnet tool update dotnetsay`**

  Aktualizuje místní nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) nainstalovaný pro aktuální adresář.

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) na nejnovější verzi opravy s hlavní verzí `2` a podverzí nástroje `0` .

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) na nejnižší verzi v zadaném rozsahu `(> 2.0.0 && < 2.1.4)` , verze se `2.1.0` nainstaluje. Další informace o rozsahu sémantických verzí najdete v tématu [rozsahy verzí balíčku NuGet](/nuget/concepts/package-versioning#version-ranges).

## <a name="see-also"></a>Viz také

- [Nástroje .NET Core](global-tools.md)
- [Sémantická verze](https://semver.org)
- [Kurz: instalace a použití globálního nástroje .NET Core pomocí .NET Core CLI](global-tools-how-to-use.md)
- [Kurz: instalace a použití místního nástroje .NET Core pomocí .NET Core CLI](local-tools-how-to-use.md)
