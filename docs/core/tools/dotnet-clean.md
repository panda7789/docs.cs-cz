---
title: DotNet vyčistit příkaz – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet clean odstraní aktuální adresář.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 5553e4b4423a2d824c05caf7114c47b5f1c20477
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668272"
---
# <a name="dotnet-clean"></a>DotNet čisté

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet clean` -Vyčistí výstup projektu.

## <a name="synopsis"></a>Souhrn

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet clean` Příkaz vyčistí výstupního předchozím sestavením. Je implementován jako [cíl nástroje MSBuild](/visualstudio/msbuild/msbuild-targets), takže projekt je vyhodnocen při spuštění příkazu. Pouze výstupů během sestavení se vytvořila vymazána. Obě zprostředkující (*obj*) a závěrečný výstup (*bin*) se čištění složky.

## <a name="arguments"></a>Arguments

`PROJECT`

Projekt MSBuild pro čištění. Pokud není zadán soubor projektu, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí na *proj* a použije tento soubor.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`. Tato možnost je pouze při čištění, pokud jste zadali během doby sestavení vyžaduje.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) , který byl zadán v okamžiku sestavení. Rozhraní musí být definován v [soubor projektu](csproj.md). Pokud jste zadali rozhraní v okamžiku sestavení, je nutné zadat rozhraní framework při čištění souboru.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, ve kterém je umístí výstupy sestavení. Zadejte `-f|--framework <FRAMEWORK>` přepnout s přepínačem výstupní adresář, pokud jste zadali rozhraní, když byl projekt sestaven.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Vyčištění výstupní složky zadaného modulu runtime. Používá se při [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) byl vytvořen.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené úrovně jsou q [uiet], m [inimal], n [ormal], d [etailed] a diag [nostic].

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`. Tato možnost je pouze při čištění, pokud jste zadali během doby sestavení vyžaduje.

`-f|--framework <FRAMEWORK>`

[Framework](../../standard/frameworks.md) , který byl zadán v okamžiku sestavení. Rozhraní musí být definován v [soubor projektu](csproj.md). Pokud jste zadali rozhraní v okamžiku sestavení, je nutné zadat rozhraní framework při čištění souboru.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, ve kterém je umístí výstupy sestavení. Zadejte `-f|--framework <FRAMEWORK>` přepnout s přepínačem výstupní adresář, pokud jste zadali rozhraní, když byl projekt sestaven.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené úrovně jsou q [uiet], m [inimal], n [ormal], d [etailed] a diag [nostic].

---

## <a name="examples"></a>Příklady

Vyčištění výchozí sestavení projektu:

`dotnet clean`

Vyčistěte projekt vyvíjené v konfiguraci vydané verze:

`dotnet clean --configuration Release`
