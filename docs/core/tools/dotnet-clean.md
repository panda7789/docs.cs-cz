---
title: příkaz - .NET Core rozhraní příkazového řádku vyčistit DotNet.
description: Příkaz clean dotnet vyčistí aktuální adresář.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 9e68781fe00590f3c8d429631a3f72d525d29fa9
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697028"
---
# <a name="dotnet-clean"></a>Vyčištění DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet clean` -Vyčistí výstup projektu.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet clean` Příkaz vyčistí výstup předchozího sestavení. Je implementovaný jako [MSBuild cíl](/visualstudio/msbuild/msbuild-targets), takže projektu vyhodnotí při spuštění příkazu. Vyčištěním pouze výstupy vytvořené během sestavení. Obě zprostředkující (*obj*) a závěrečný výstup (*bin*) vyčištěním složek.

## <a name="arguments"></a>Arguments

`PROJECT`

Projektu nástroje MSBuild vyčistit. Pokud projekt soubor není zadán, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, které *proj* a použije tento soubor.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`. Tato možnost je pouze při čištění, pokud jste zadali během okamžiku sestavení vyžaduje.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) zadaný v čase vytvoření buildu. Rozhraní musí být definován v [soubor projektu](csproj.md). Pokud jste zadali rozhraní v čase vytvoření buildu, musíte zadat rozhraní při čištění.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, ve kterém jsou umístěny výstupy sestavení. Zadejte `-f|--framework <FRAMEWORK>` přepínač s přepínačem výstupní adresář, pokud jste zadali rozhraní, pokud byl vytvořený projekt.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Vyčistí do výstupní složky zadané modulu runtime. Používá se při [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) byla vytvořena.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené úrovně jsou q [uiet], [den] m, n [ormální], [podrobné] d a diag [nostic].

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`. Tato možnost je pouze při čištění, pokud jste zadali během okamžiku sestavení vyžaduje.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) zadaný v čase vytvoření buildu. Rozhraní musí být definován v [soubor projektu](csproj.md). Pokud jste zadali rozhraní v čase vytvoření buildu, musíte zadat rozhraní při čištění.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, ve kterém jsou umístěny výstupy sestavení. Zadejte `-f|--framework <FRAMEWORK>` přepínač s přepínačem výstupní adresář, pokud jste zadali rozhraní, pokud byl vytvořený projekt.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené úrovně jsou q [uiet], [den] m, n [ormální], [podrobné] d a diag [nostic].

---

## <a name="examples"></a>Příklady

Vyčištění sestavení výchozí projektu:

`dotnet clean`

Vyčistěte projekt sestaven pomocí konfigurace verze:

`dotnet clean --configuration Release`
