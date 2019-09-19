---
title: příkaz dotnet nástroje pro odinstalaci
description: Příkaz pro odinstalaci nástroje dotnet odinstaluje zadaný globální nástroj .NET Core z počítače.
ms.date: 05/29/2018
ms.openlocfilehash: 033753f44464e78b826e908e0b6cdf276da8a179
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117541"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Name

`dotnet tool uninstall`– Odinstaluje zadaný [globální nástroj .NET Core](global-tools.md) z počítače.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Popis

`dotnet tool uninstall` Příkaz nabízí způsob, jak odinstalovat globální nástroje .NET Core z počítače. Chcete-li použít příkaz, musíte určit, že chcete odebrat nástroj pro všechny uživatele pomocí `--global` možnosti nebo zadat cestu k umístění nástroje `--tool-path` pomocí možnosti.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Název nebo ID balíčku NuGet, který obsahuje globální nástroj .NET Core pro odinstalaci. Název balíčku můžete najít pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .

## <a name="options"></a>Možnosti

`-g|--global`

Určuje, že nástroj, který se má odebrat, pochází z instalace v rámci uživatele. Nelze kombinovat s `--tool-path` možností. Pokud tuto možnost nezadáte, musíte zadat `--tool-path` možnost.

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`--tool-path <PATH>`

Určuje umístění, kam se má globální nástroj odinstalovat. Cesta může být absolutní nebo relativní. Nelze kombinovat s `--global` možností. Pokud tuto možnost nezadáte, musíte zadat `--global` možnost.

## <a name="examples"></a>Příklady

Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :

`dotnet tool uninstall -g dotnetsay`

Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z určité složky systému Windows:

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z konkrétní složky Linux/MacOS:

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Viz také:

- [Globální nástroje .NET Core](global-tools.md)
