---
title: dotnet – příkaz obnovení nástroje
description: Příkaz pro obnovení nástroje dotnet se nainstaluje na váš počítač. místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.
ms.date: 02/14/2020
ms.openlocfilehash: 2900d431987661a9232ceed10d9a424093f8be45
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543906"
---
# <a name="dotnet-tool-restore"></a>obnovení nástroje dotnet

**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet tool restore` – nainstaluje na váš počítač místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool restore <PACKAGE_NAME> [--configfile] [--add-source] [tool-manifest] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [-interactive] [-v|--verbosity]
dotnet tool restore <-h|--help>
```

## <a name="description"></a>Popis

Příkaz `dotnet tool restore` najde soubor manifestu nástroje, který je v oboru pro aktuální adresář a nainstaluje nástroje, které jsou uvedeny v něm. Informace o souborech manifestu najdete v tématech [instalace místního nástroje](global-tools.md#install-a-local-tool) a [vyvolání místního nástroje](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

Název nebo ID balíčku NuGet, který obsahuje nástroj .NET Core, který se má nainstalovat

## <a name="options"></a>Možnosti

- **`--configfile <FILE>`**

  Soubor konfigurace NuGet (*NuGet. config*), který se má použít.

- **`--add-source <SOURCE>`**

  Přidá další zdroj balíčku NuGet, který se použije při instalaci.

- **`--tool-manifest <PATH>`**

  Cesta k souboru manifestu.

- **`--disable-parallel`**

  Zabránit v paralelním obnovení více projektů.

- **`--ignore-failed-sources`**

  Považovat selhání zdroje balíčku za upozornění.

- **`--no-cache`**

  Neukládat balíčky a požadavky HTTP do mezipaměti.

- **`--interactive`**

  Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.

## <a name="example"></a>Příklad

- **`dotnet tool restore`**

  Obnoví místní nástroje pro aktuální adresář.

## <a name="see-also"></a>Viz také:

- [Nástroje .NET Core](global-tools.md)
