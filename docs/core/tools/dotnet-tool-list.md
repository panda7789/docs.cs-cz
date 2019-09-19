---
title: příkaz pro seznam nástrojů dotnet
description: Příkaz pro výpis seznamu nástrojů dotnet obsahuje seznam zadaného globálního nástroje .NET Core z počítače.
ms.date: 05/29/2018
ms.openlocfilehash: 6d35b1dce0c6d57edb0c6dd5f9711f093bc804aa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117561"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Name

`dotnet tool list`– Zobrazí seznam všech [globálních nástrojů .NET Core](global-tools.md) , které jsou aktuálně nainstalované ve výchozím adresáři na vašem počítači nebo v zadané cestě.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a>Popis

`dotnet tool list` Příkaz umožňuje zobrazit seznam všech globálních nástrojů .NET Core nainstalovaných na vašem počítači (aktuální profil uživatele) nebo v zadané cestě. Příkaz vypíše název balíčku, nainstalovanou verzi a příkaz globálních nástrojů. Chcete-li použít příkaz list, je nutné určit, že chcete zobrazit všechny nástroje pro celý uživatel pomocí `--global` možnosti nebo zadat vlastní cestu `--tool-path` pomocí možnosti.

## <a name="options"></a>Možnosti

`-g|--global`

Obsahuje seznam globálních nástrojů pro všechny uživatele. Nelze kombinovat s `--tool-path` možností. Pokud tuto možnost nezadáte, musíte zadat `--tool-path` možnost.

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`--tool-path <PATH>`

Určuje vlastní umístění, kde se mají najít globální nástroje. Cesta může být absolutní nebo relativní. Nelze kombinovat s `--global` možností. Pokud tuto možnost nezadáte, musíte zadat `--global` možnost.

## <a name="examples"></a>Příklady

Zobrazí seznam všech globálních nástrojů nainstalovaných v celém počítači (aktuální profil uživatele):

`dotnet tool list -g`

Zobrazí seznam globálních nástrojů z konkrétní složky systému Windows:

`dotnet tool list --tool-path c:\global-tools`

Zobrazí seznam globálních nástrojů z konkrétní složky Linux/macOS:

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a>Viz také:

- [Globální nástroje .NET Core](global-tools.md)
