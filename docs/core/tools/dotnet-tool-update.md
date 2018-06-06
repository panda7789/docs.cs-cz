---
title: příkaz aktualizace DotNet nástroj - .NET Core rozhraní příkazového řádku
description: Příkaz aktualizace nástrojů dotnet aktualizuje zadaný .NET Core globální nástroj na počítači.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 35a0bd0f85f0beed06d4250d8f195ce4fe4fcca4
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696686"
---
# <a name="dotnet-tool-update"></a>aktualizace nástrojů DotNet.

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Název

`dotnet tool update` -Aktualizace zadaný [.NET Core globální nástroj](global-tools.md) na váš počítač.

## <a name="synopsis"></a>Stručný obsah

```
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Popis

`dotnet tool update` Příkaz nabízí způsob, jak můžete aktualizovat .NET Core globální nástroje na váš počítač nejnovější stabilní verze balíčku. Příkaz odinstaluje a přeinstaluje nástroj efektivně jeho aktualizaci. Použití příkazu, buď musíte zadat, že chcete aktualizovat nástroj z instalace celou uživatele pomocí `--global` možnost nebo zadejte cestu k umístění, kde je nástroj nainstalován pomocí `--tool-path` možnost.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Název nebo ID balíčku NuGet, který obsahuje rozhraní .NET Core globální nástroj k aktualizaci. Můžete najít pomocí názvu balíčku [seznam nástrojů dotnet](dotnet-tool-list.md) příkaz.

## <a name="options"></a>Možnosti

`--add-source <SOURCE>`

Přidá další zdroj balíčku NuGet chcete použít během instalace.

`--configfile <FILE>`

Konfigurace NuGet (*nuget.config*) souboru k použití.

`--framework <FRAMEWORK>`

Určuje, [cílové rozhraní](../../standard/frameworks.md) aktualizovat nástroj pro.

`-g|--global`

Určuje, že aktualizace je pro nástroj na úrovni uživatele. Nelze kombinovat s `--tool-path` možnost. Pokud nezadáte tuto možnost, musíte zadat `--tool-path` možnost.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--tool-path <PATH>`

Určuje umístění, kde je nainstalován nástroj globální. Cesta může být absolutní nebo relativní. Nelze kombinovat s `--global` možnost. Pokud nezadáte tuto možnost, musíte zadat `--global` možnost.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

## <a name="examples"></a>Příklady

Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje:

`dotnet tool update -g dotnetsay`

Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální umístěný v konkrétní složce systému Windows:

`dotnet tool update dotnetsay --tool-path c:\global-tools`

Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální umístěný v konkrétní složce systému Linux nebo macOS:

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Viz také:

[.NET core globální nástroje](global-tools.md)