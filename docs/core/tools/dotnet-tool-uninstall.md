---
title: příkaz - .NET Core rozhraní příkazového řádku odinstalovat nástroj DotNet.
description: Příkaz odinstalovat nástroj dotnet odinstaluje zadaný nástroj globální základní .NET z vašeho počítače.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5cf80d1756dbf4e88bb52a8028d186d44978f440
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696935"
---
# <a name="dotnet-tool-uninstall"></a>Odinstalace nástroje pro DotNet.

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Název

`dotnet tool uninstall` -Odinstaluje zadaný [.NET Core globální nástroj](global-tools.md) z vašeho počítače.

## <a name="synopsis"></a>Stručný obsah

```
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Popis

`dotnet tool uninstall` Příkaz nabízí způsob, jak můžete odinstalovat .NET Core globální nástroje z vašeho počítače. Použití příkazu, buď musíte zadat, že chcete odebrat uživatele celou nástroj pomocí `--global` možnost nebo zadejte cestu k umístění, kde je nástroj nainstalován pomocí `--tool-path` možnost.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Název nebo ID balíčku NuGet, který obsahuje rozhraní .NET Core globální nástroj pro odinstalaci. Můžete najít pomocí názvu balíčku [seznam nástrojů dotnet](dotnet-tool-list.md) příkaz.

## <a name="options"></a>Možnosti

`-g|--global`

Určuje, že nástroj odeberou se z instalace úrovni uživatele. Nelze kombinovat s `--tool-path` možnost. Pokud nezadáte tuto možnost, musíte zadat `--tool-path` možnost.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--tool-path <PATH>`

Určuje umístění, kde chcete-li odinstalovat nástroj globální. Cesta může být absolutní nebo relativní. Nelze kombinovat s `--global` možnost. Pokud nezadáte tuto možnost, musíte zadat `--global` možnost.

## <a name="examples"></a>Příklady

Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje:

`dotnet tool uninstall -g dotnetsay`

Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj z určité složky systému Windows:

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj z určité složky systému Linux nebo macOS:

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Viz také:

[.NET core globální nástroje](global-tools.md)