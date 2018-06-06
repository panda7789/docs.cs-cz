---
title: příkaz - .NET Core rozhraní příkazového řádku instalovat nástroj DotNet.
description: Nástroj dotnet. Nainstalujte příkaz nainstaluje zadaný rozhraní .NET Core globální nástroj na váš počítač.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f3068848910d6672a10ecfb639bac8e18a72818d
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697284"
---
# <a name="dotnet-tool-install"></a>Instalace nástroje pro DotNet.

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Název

`dotnet tool install` -Nainstaluje zadaný [.NET Core globální nástroj](global-tools.md) na váš počítač.

## <a name="synopsis"></a>Stručný obsah

```
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Popis

`dotnet tool install` Příkaz nabízí způsob, jak k instalaci .NET Core globální nástroje na váš počítač. Použití příkazu, buď musíte zadat, že chcete uživatele celou instalace pomocí `--global` možnost nebo zadejte cestu k instalaci pomocí `--tool-path` možnost.

Globální nástroje jsou nainstalovány v následujících adresářích ve výchozím nastavení, když zadáte `-g` (nebo `--global`) možnost:

| OPERAČNÍ SYSTÉM          | Cesta                          |
|-------------|-------------------------------|
| Linux/systému macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Název nebo ID balíčku NuGet, který obsahuje rozhraní .NET Core globální nástroj pro instalaci.

## <a name="options"></a>Možnosti

`--add-source <SOURCE>`

Přidá další zdroj balíčku NuGet chcete použít během instalace.

`--configfile <FILE>`

Konfigurace NuGet (*nuget.config*) souboru k použití.

`--framework <FRAMEWORK>`

Určuje, [cílové rozhraní](../../standard/frameworks.md) k instalaci nástroje pro. Ve výchozím nastavení se pokusí vybrat nejvhodnější cílové rozhraní .NET Core SDK.

`-g|--global`

Určuje, že instalace je uživatel široké. Nelze kombinovat s `--tool-path` možnost. Pokud nezadáte tuto možnost, musíte zadat `--tool-path` možnost.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--tool-path <PATH>`

Určuje umístění, kam se má nainstalovat nástroj globální. Cesta může být absolutní nebo relativní. Pokud cesta neexistuje, příkaz se pokusí se ji vytvořit. Nelze kombinovat s `--global` možnost. Pokud nezadáte tuto možnost, musíte zadat `--global` možnost.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

`--version <VERSION_NUMBER>`

Používaná verze nástroje pro instalaci. Ve výchozím nastavení je nainstalovaná nejnovější verze stabilní balíčku. Tuto možnost použijte k instalaci preview nebo starší verze nástroje.

## <a name="examples"></a>Příklady

Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj ve výchozím umístění:

`dotnet tool install -g dotnetsay`

Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj určité složky systému Windows:

`dotnet tool install dotnetsay --tool-path c:\global-tools`

Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj v konkrétní složce systému Linux nebo macOS:

`dotnet tool install dotnetsay --tool-path ~/bin`

Nainstaluje verzi 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje:

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a>Viz také:

[.NET core globální nástroje](global-tools.md)