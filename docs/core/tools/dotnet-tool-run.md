---
title: příkaz pro spuštění nástroje dotnet
description: Příkaz pro spuštění nástroje dotnet vyvolá místní nástroj.
ms.date: 02/14/2020
ms.openlocfilehash: 05b21c0f5ea86f4b99b220f556c61bf83f464114
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543878"
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

## <a name="see-also"></a>Viz také:

- [Nástroje .NET Core](global-tools.md)
