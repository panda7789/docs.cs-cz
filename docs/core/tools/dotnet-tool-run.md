---
title: příkaz pro spuštění nástroje dotnet
description: Příkaz pro spuštění nástroje dotnet vyvolá místní nástroj.
ms.date: 02/14/2020
ms.openlocfilehash: 76830b8a8088fbf21f14ab0722b9547eabde7ba4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156956"
---
# <a name="dotnet-tool-run"></a>spuštění nástroje dotnet

**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet tool run` – vyvolá místní nástroj.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool run <COMMAND NAME>
dotnet tool run <-h|--help>
```

## <a name="description"></a>Popis

Příkaz `dotnet tool run` vyhledá soubory manifestu nástroje, které jsou v oboru pro aktuální adresář. Když najde odkaz na zadaný nástroj, nástroj ho spustí. Další informace naleznete v tématu [vyvolání místního nástroje](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`COMMAND_NAME`**

  Název příkazu nástroje, který se má spustit.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

## <a name="example"></a>Příklad

- **`dotnet tool run dotnetsay`**

  Spustí místní nástroj `dotnetsay`.

## <a name="see-also"></a>Viz také

- [Nástroje .NET Core](global-tools.md)
