---
title: dotnet nástroj spustit, příkaz
description: Příkaz spuštění nástroje dotnet vyvolá místní nástroj.
ms.date: 02/14/2020
ms.openlocfilehash: f79c239363e8b3abbd55c54dd1912443e6777fb7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463330"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze

## <a name="name"></a>Název

`dotnet tool run`- Vyvolá místní nástroj.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet tool run` prohledává soubory manifestů nástroje, které jsou v oboru pro aktuální adresář. Když najde odkaz na zadaný nástroj, spustí nástroj. Další informace naleznete [v tématu Invoke a local tool](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`COMMAND_NAME`**

  Název příkazu nástroje, který má být spuštěn.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

## <a name="example"></a>Příklad

- **`dotnet tool run dotnetsay`**

  Spustí `dotnetsay` místní nástroj.

## <a name="see-also"></a>Viz také

- [Nástroje .NET Core](global-tools.md)
- [Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET](local-tools-how-to-use.md)
