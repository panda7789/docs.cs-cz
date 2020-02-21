---
title: příkaz pro aktualizaci nástroje dotnet
description: Příkaz pro aktualizaci nástroje dotnet aktualizuje zadaný nástroj .NET Core na vašem počítači.
ms.date: 02/14/2020
ms.openlocfilehash: 50bb366fedfb0ea69b8b6007ff89e366b4f689de
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543414"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet tool update` – aktualizuje zadaný [nástroj .NET Core](global-tools.md) na vašem počítači.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Popis

Příkaz `dotnet tool update` poskytuje způsob, jak aktualizovat nástroje .NET Core na vašem počítači na nejnovější stabilní verzi balíčku. Příkaz odinstaluje a znovu nainstaluje nástroj a efektivně ho aktualizuje. Chcete-li použít příkaz, zadejte jednu z následujících možností:

* Pokud chcete aktualizovat globální nástroj, který byl nainstalovaný ve výchozím umístění, použijte možnost `--global`.
* Chcete-li aktualizovat globální nástroj, který byl nainstalován ve vlastním umístění, použijte možnost `--tool-path`.
* Chcete-li aktualizovat místní nástroj, vynechejte možnosti `--global` a `--tool-path`.

**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Název nebo ID balíčku NuGet, který obsahuje globální nástroj .NET Core, který se má aktualizovat Název balíčku můžete najít pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .

## <a name="options"></a>Možnosti

- **`--add-source <SOURCE>`**

  Přidá další zdroj balíčku NuGet, který se použije při instalaci.

- **`--configfile <FILE>`**

  Soubor konfigurace NuGet (*NuGet. config*), který se má použít.

- **`--framework <FRAMEWORK>`**

  Určuje [cílovou platformu](../../standard/frameworks.md) , pro kterou chcete nástroj aktualizovat.

- **`-g|--global`**

  Určuje, že je aktualizace určena pro nástroj pro uživatelský rozsah. Nelze kombinovat s možností `--tool-path`. Vynechání `--global` a `--tool-path` určuje, že nástroj, který se má aktualizovat, je místní nástroj. 

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--tool-path <PATH>`**

  Určuje umístění, kde je nainstalován globální nástroj. Cesta může být absolutní nebo relativní. Nelze kombinovat s možností `--global`. Vynechání `--global` a `--tool-path` určuje, že nástroj, který se má aktualizovat, je místní nástroj. 

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.

## <a name="examples"></a>Příklady

- **`dotnet tool update -g dotnetsay`**

  Aktualizuje nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global.

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři Windows.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři Linux/MacOS.

- **`dotnet tool update dotnetsay`**

  Aktualizuje místní nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) nainstalovaný pro aktuální adresář.

## <a name="see-also"></a>Viz také:

- [Nástroje .NET Core](global-tools.md)
