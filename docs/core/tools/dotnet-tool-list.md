---
title: příkaz seznamu DotNet nástroj - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet nástroj seznam uvádí zadaný .NET Core globální nástroj z vašeho počítače.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5f4793cd37c3a8df06eb6930ad9f381ac70d4e67
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696722"
---
# <a name="dotnet-tool-list"></a>seznam nástrojů DotNet.

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Název

`dotnet tool list` -Obsahuje seznam všech [.NET Core globální nástroje](global-tools.md) nainstalovány v výchozí adresář na počítači nebo v zadané cestě.

## <a name="synopsis"></a>Stručný obsah

```
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a>Popis

`dotnet tool list` Příkaz nabízí způsob, jak lze uvést všechny .NET Core globální nástroje nainstalovat celou uživatele na váš počítač (aktuální profil uživatele) nebo v zadané cestě. Příkaz uvádí název balíčku, verzi a příkaz globální nástroj. Použití příkazu seznamu, můžete mít buď k určení, zda chcete zobrazit všechny nástroje celou uživatele pomocí `--global` možnost nebo zadejte vlastní cesta pomocí `--tool-path` možnost.

## <a name="options"></a>Možnosti

`-g|--global`

Obsahuje seznam nástrojů globální úrovni uživatele. Nelze kombinovat s `--tool-path` možnost. Pokud nezadáte tuto možnost, musíte zadat `--tool-path` možnost.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--tool-path <PATH>`

Určuje do vlastního umístění, kde najít nástroje na globální. Cesta může být absolutní nebo relativní. Nelze kombinovat s `--global` možnost. Pokud nezadáte tuto možnost, musíte zadat `--global` možnost.

## <a name="examples"></a>Příklady

Obsahuje všechny globální nástroje nainstalované uživatele celou na počítači (aktuální profil uživatele):

`dotnet tool list -g`

Obsahuje seznam nástrojů globální z určité složky systému Windows:

`dotnet tool list --tool-path c:\global-tools`

Obsahuje seznam nástrojů globální z určité složky systému Linux nebo macOS:

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a>Viz také:

[.NET core globální nástroje](global-tools.md)