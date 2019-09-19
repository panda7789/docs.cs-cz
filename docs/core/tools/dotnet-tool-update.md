---
title: příkaz pro aktualizaci nástroje dotnet
description: Příkaz pro aktualizaci nástroje dotnet aktualizuje zadaný globální nástroj .NET Core na vašem počítači.
ms.date: 05/29/2018
ms.openlocfilehash: b10ce39c8b9d4df23243bcf672454a455e34eec1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117531"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Name

`dotnet tool update`– Aktualizuje zadaný [globální nástroj .NET Core](global-tools.md) na vašem počítači.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Popis

`dotnet tool update` Příkaz nabízí způsob, jak aktualizovat globální nástroje .NET Core na vašem počítači na nejnovější stabilní verzi balíčku. Příkaz odinstaluje a znovu nainstaluje nástroj a efektivně ho aktualizuje. Chcete-li použít příkaz, musíte určit, že chcete nástroj aktualizovat z uživatelské instalace pomocí `--global` možnosti nebo zadat cestu k umístění nástroje `--tool-path` pomocí možnosti.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Název nebo ID balíčku NuGet, který obsahuje globální nástroj .NET Core, který se má aktualizovat Název balíčku můžete najít pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .

## <a name="options"></a>Možnosti

`--add-source <SOURCE>`

Přidá další zdroj balíčku NuGet, který se použije při instalaci.

`--configfile <FILE>`

Soubor konfigurace NuGet (*NuGet. config*), který se má použít.

`--framework <FRAMEWORK>`

Určuje [cílovou platformu](../../standard/frameworks.md) , pro kterou chcete nástroj aktualizovat.

`-g|--global`

Určuje, že je aktualizace určena pro nástroj pro uživatelský rozsah. Nelze kombinovat s `--tool-path` možností. Pokud tuto možnost nezadáte, musíte zadat `--tool-path` možnost.

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`--tool-path <PATH>`

Určuje umístění, kde je nainstalován globální nástroj. Cesta může být absolutní nebo relativní. Nelze kombinovat s `--global` možností. Pokud tuto možnost nezadáte, musíte zadat `--global` možnost.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`

## <a name="examples"></a>Příklady

Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :

`dotnet tool update -g dotnetsay`

Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v konkrétní složce systému Windows:

`dotnet tool update dotnetsay --tool-path c:\global-tools`

Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v konkrétní složce Linux/MacOS:

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Viz také:

- [Globální nástroje .NET Core](global-tools.md)
