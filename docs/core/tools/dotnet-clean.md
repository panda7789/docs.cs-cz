---
title: čištění příkaz DotNet
description: Příkaz dotnet clean odstraní aktuální adresář.
ms.date: 04/14/2019
ms.openlocfilehash: 3e735c02c9be9b6f51a8cdf048c18eff34f838cb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754120"
---
# <a name="dotnet-clean"></a>DotNet čisté

**Toto téma platí pro: ✓** .NET Core 1.x sady SDK a novějších verzích

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet clean` -Vyčistí výstup projektu.

## <a name="synopsis"></a>Souhrn

```
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Popis

`dotnet clean` Příkaz vyčistí výstupního předchozím sestavením. Je implementován jako [cíl nástroje MSBuild](/visualstudio/msbuild/msbuild-targets), takže projekt je vyhodnocen při spuštění příkazu. Pouze výstupů během sestavení se vytvořila vymazána. Obě zprostředkující (*obj*) a závěrečný výstup (*bin*) se čištění složky.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Nástroj MSBuild projekt nebo řešení pro čištění. Pokud není zadán soubor projektu nebo řešení, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí na *proj* nebo *sln*a použije tento soubor.

## <a name="options"></a>Možnosti

* **`-c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`. Tato možnost je pouze při čištění, pokud jste zadali během doby sestavení vyžaduje.

* **`-f|--framework <FRAMEWORK>`**

  [Framework](../../standard/frameworks.md) , který byl zadán v okamžiku sestavení. Rozhraní musí být definován v [soubor projektu](csproj.md). Pokud jste zadali rozhraní v okamžiku sestavení, je nutné zadat rozhraní framework při čištění souboru.

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`--interactive`**

  Povoluje příkazu zastavit a počkat na vstup uživatele nebo akce. Například k dokončení ověřování. Tato možnost je k dispozici, protože .NET Core 3.0 SDK.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Adresář, který obsahuje artefakty sestavení k odstranění. Zadejte `-f|--framework <FRAMEWORK>` přepnout s přepínačem výstupní adresář, pokud jste zadali rozhraní, když byl projekt sestaven.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Vyčištění výstupní složky zadaného modulu runtime. Používá se při [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) byl vytvořen. Možnost dostupné od verze rozhraní .NET Core 2.0 SDK.

* **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností MSBuild. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`. Výchozí hodnota je `normal`.

## <a name="examples"></a>Příklady

* Vyčištění výchozí sestavení projektu:

  ```console
  dotnet clean
  ```

* Vyčistěte projekt vyvíjené v konfiguraci vydané verze:

  ```console
  dotnet clean --configuration Release
  ```