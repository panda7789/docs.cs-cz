---
title: příkaz aktualizace nástrojů DotNet
description: Příkaz dotnet nástroj aktualizace aktualizuje zadaný nástroje rozhraní .NET Core globální na svém počítači.
ms.date: 05/29/2018
ms.openlocfilehash: bc7edada013c118564d44cbe4542dacb76925692
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516639"
---
# <a name="dotnet-tool-update"></a>aktualizace nástrojů DotNet

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Název

`dotnet tool update` -Aktualizace zadaný [globální nástroje .NET Core](global-tools.md) na svém počítači.

## <a name="synopsis"></a>Souhrn

```console
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Popis

`dotnet tool update` Příkaz poskytuje způsob, jak můžete aktualizovat globální nástroje .NET Core na svém počítači na nejnovější stabilní verze balíčku. Příkaz odinstaluje a přeinstaluje nástroj efektivně aktualizace. Použití příkazu, buď musíte zadat, že chcete nástroj z celé uživatelské instalace pomocí aktualizací `--global` možnost nebo zadejte cestu k umístění, kde je nástroj nainstalován pomocí `--tool-path` možnost.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Název nebo ID balíčku NuGet, který obsahuje globální nástroji .NET Core k aktualizaci. Můžete najít pomocí názvu balíčku [seznam nástrojů dotnet](dotnet-tool-list.md) příkazu.

## <a name="options"></a>Možnosti

`--add-source <SOURCE>`

Přidá další zdroj balíčku NuGet pro použití během instalace.

`--configfile <FILE>`

Konfigurace NuGet (*nuget.config*) soubor se má použít.

`--framework <FRAMEWORK>`

Určuje [Cílová architektura](../../standard/frameworks.md) aktualizovat nástroj pro.

`-g|--global`

Určuje, že je aktualizace pro celé uživatelské nástroje. Nelze kombinovat s `--tool-path` možnost. Pokud nezadáte tuto možnost, je nutné zadat `--tool-path` možnost.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--tool-path <PATH>`

Určuje umístění, kde je nainstalován nástroj globální. Cesta může být absolutní nebo relativní. Nelze kombinovat s `--global` možnost. Pokud nezadáte tuto možnost, je nutné zadat `--global` možnost.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

## <a name="examples"></a>Příklady

Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje:

`dotnet tool update -g dotnetsay`

Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje nachází v určité složce Windows:

`dotnet tool update dotnetsay --tool-path c:\global-tools`

Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální umístěný do konkrétní složky Linux nebo macOS:

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Viz také:

- [.NET Core Global Tools](global-tools.md)
