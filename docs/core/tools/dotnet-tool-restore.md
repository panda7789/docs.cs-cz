---
title: dotnet nástroj obnovit, příkaz
description: Příkaz obnovení nástroje dotnet nainstaluje do počítače místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.
ms.date: 02/14/2020
ms.openlocfilehash: cb46f70afb58e482b6aedfddfbf5f3a0c40674f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146434"
---
# <a name="dotnet-tool-restore"></a>obnovení nástroje dotnet

**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet tool restore`- Nainstaluje do počítače místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [-interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a>Popis

Příkaz `dotnet tool restore` vyhledá soubor manifestu nástroje, který je v oboru pro aktuální adresář, a nainstaluje nástroje, které jsou v něm uvedeny. Informace o souborech manifestu naleznete [v tématu Instalace místního nástroje](global-tools.md#install-a-local-tool) a [Vyvolání místního nástroje](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

Název/ID balíčku NuGet, který obsahuje nástroj .NET Core k instalaci.

## <a name="options"></a>Možnosti

- **`--configfile <FILE>`**

  Soubor konfigurace NuGet (*nuget.config).*

- **`--add-source <SOURCE>`**

  Přidá další zdroj balíčku NuGet pro použití během instalace.

- **`--tool-manifest <PATH>`**

  Cesta k souboru manifestu.

- **`--disable-parallel`**

  Zabránit obnovení více projektů paralelně.

- **`--ignore-failed-sources`**

  Považovat selhání zdroje balíčku jako upozornění.

- **`--no-cache`**

  Neukládat do mezipaměti balíčky a požadavky http.

- **`--interactive`**

  Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci (například k dokončení ověřování).

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .

## <a name="example"></a>Příklad

- **`dotnet tool restore`**

  Obnoví místní nástroje pro aktuální adresář.

## <a name="see-also"></a>Viz také

- [Nástroje .NET Core](global-tools.md)
- [Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET](local-tools-how-to-use.md)
