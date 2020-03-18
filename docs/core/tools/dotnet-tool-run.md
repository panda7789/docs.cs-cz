---
title: dotnet nástroj spustit, příkaz
description: Příkaz spuštění nástroje dotnet vyvolá místní nástroj.
ms.date: 02/14/2020
ms.openlocfilehash: a088cd0b7f4bba014234a8189a42a63aa6d88f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847843"
---
# <a name="dotnet-tool-run"></a>spuštění nástroje dotnet

**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet tool run`- Vyvolá místní nástroj.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run <-h|--help>
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
