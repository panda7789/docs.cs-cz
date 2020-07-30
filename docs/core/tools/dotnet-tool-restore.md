---
title: dotnet – příkaz obnovení nástroje
description: Příkaz pro obnovení nástroje dotnet se nainstaluje na váš počítač. místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.
ms.date: 02/14/2020
ms.openlocfilehash: ceef3274ec9d337f8c51009d5a8c27e808b14035
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302669"
---
# <a name="dotnet-tool-restore"></a>dotnet tool restore

**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet tool restore`– Nainstaluje na váš počítač místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a>Popis

`dotnet tool restore`Příkaz najde soubor manifestu nástroje, který je v oboru pro aktuální adresář a nainstaluje nástroje, které jsou uvedeny v něm. Informace o souborech manifestu najdete v tématech [instalace místního nástroje](global-tools.md#install-a-local-tool) a [vyvolání místního nástroje](global-tools.md#invoke-a-local-tool).

## <a name="options"></a>Možnosti

- **`--configfile <FILE>`**

  Soubor konfigurace NuGet (*nuget.config*), který se má použít.

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

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .

## <a name="example"></a>Příklad

- **`dotnet tool restore`**

  Obnoví místní nástroje pro aktuální adresář.

## <a name="see-also"></a>Viz také:

- [Nástroje .NET Core](global-tools.md)
- [Kurz: instalace a použití místního nástroje .NET Core pomocí .NET Core CLI](local-tools-how-to-use.md)
