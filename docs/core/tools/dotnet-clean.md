---
title: dotnet – příkaz Vyčištění
description: Příkaz dotnet Cleanup vyčistí aktuální adresář.
ms.date: 06/26/2019
ms.openlocfilehash: 715a33a8a1aa13a2a76f9d4522413dcc72e4b4aa
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451353"
---
# <a name="dotnet-clean"></a>dotnet clean

**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Název

`dotnet clean` – vyčistí výstup projektu.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet clean` vyčistí výstup předchozího buildu. Je implementována jako [cíl nástroje MSBuild](/visualstudio/msbuild/msbuild-targets), takže projekt je vyhodnocen při spuštění příkazu. Vyčištěny jsou pouze výstupy vytvořené během sestavení. Jsou vyčištěny mezilehlé složky (*obj*) i finální výstupní složky (*bin*).

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Projekt nebo řešení MSBuild, které se má vyčistit Pokud není zadán soubor projektu nebo řešení, nástroj MSBuild vyhledá aktuální pracovní adresář pro soubor s příponou souboru, který končí v *proj* nebo *sln*, a použije tento soubor.

## <a name="options"></a>Možnosti

* **`-c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`. Tato možnost je vyžadována pouze při čištění, pokud jste ji zadali během sestavování.

* **`-f|--framework <FRAMEWORK>`**

  [Rozhraní](../../standard/frameworks.md) , které bylo zadáno v čase sestavení. Rozhraní musí být definováno v [souboru projektu](csproj.md). Pokud jste v době sestavení zadali rozhraní, je nutné při čištění zadat rozhraní.

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

* **`--interactive`**

  Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele. Například k dokončení ověřování. K dispozici od verze .NET Core 3,0 SDK.

* **`--nologo`**

  Nezobrazuje úvodní nápis nebo zprávu o autorských právech. K dispozici od verze .NET Core 3,0 SDK.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Adresář obsahující artefakty sestavení, které mají být vyčištěny. Zadejte `-f|--framework <FRAMEWORK>` přepínač s přepínačem výstupní adresář, pokud jste zadali rozhraní při sestavení projektu.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Vyčistí výstupní složku zadaného modulu runtime. Tato funkce se používá, když se vytvořilo [samostatné nasazení](../deploying/index.md#publish-self-contained) . Možnost je k dispozici od verze .NET Core 2,0 SDK.

* **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností MSBuild. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`. Výchozí formát je `normal`.

## <a name="examples"></a>Příklady

* Vyčistit výchozí sestavení projektu:

  ```dotnetcli
  dotnet clean
  ```

* Vyčištění projektu vytvořeného pomocí konfigurace vydané verze:

  ```dotnetcli
  dotnet clean --configuration Release
  ```
