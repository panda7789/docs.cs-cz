---
title: příkaz listovat nástrojů DotNet
description: Příkaz dotnet nástroj seznam uvádí zadaného nástroje rozhraní .NET Core globální z vašeho počítače.
ms.date: 05/29/2018
ms.openlocfilehash: 0c17534beb80ed87a8f260342b0f82882a9e17b6
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169754"
---
# <a name="dotnet-tool-list"></a>seznam nástrojů DotNet

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Název

`dotnet tool list` -Obsahuje seznam všech [globální nástroje .NET Core](global-tools.md) aktuálně nainstalované ve výchozím adresáři na svém počítači nebo v zadané cestě.

## <a name="synopsis"></a>Souhrn

```console
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a>Popis

`dotnet tool list` Příkaz poskytuje způsob, jak můžete vypsat všechny globální nástroje .NET Core nainstalovat celou uživatel na svém počítači (profil aktuálního uživatele) nebo v zadané cestě. Příkaz vypíše název balíčku, nainstalovanou verzi a příkaz globální nástroj. Použití příkazu seznam, buď musíte zadat, že chcete zobrazit všechny nástroje celou uživatele pomocí `--global` možnost nebo zadat vlastní cesty pomocí `--tool-path` možnost.

## <a name="options"></a>Možnosti

`-g|--global`

Vypíše nástroje globální uživatelské úrovni. Nelze kombinovat s `--tool-path` možnost. Pokud nezadáte tuto možnost, je nutné zadat `--tool-path` možnost.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--tool-path <PATH>`

Určuje vlastní umístění, kde najít globální nástroje. Cesta může být absolutní nebo relativní. Nelze kombinovat s `--global` možnost. Pokud nezadáte tuto možnost, je nutné zadat `--global` možnost.

## <a name="examples"></a>Příklady

Uvádí všechny nainstalované nástroje pro globální uživatelské úrovni na svém počítači (profil aktuálního uživatele):

`dotnet tool list -g`

Vypíše globální nástroje z konkrétní složky Windows:

`dotnet tool list --tool-path c:\global-tools`

Vypíše globální nástroje z konkrétní složky Linux nebo macOS:

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a>Viz také:

* [Globální nástroje .NET core](global-tools.md)