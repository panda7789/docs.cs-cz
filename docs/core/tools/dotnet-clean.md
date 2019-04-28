---
title: čištění příkaz DotNet
description: Příkaz dotnet clean odstraní aktuální adresář.
ms.date: 12/04/2018
ms.openlocfilehash: a25b7930794795e3dff5051a8ca1dd1b9c261dfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665212"
---
# <a name="dotnet-clean"></a>DotNet čisté

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet clean` -Vyčistí výstup projektu.

## <a name="synopsis"></a>Souhrn

```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Popis

`dotnet clean` Příkaz vyčistí výstupního předchozím sestavením. Je implementován jako [cíl nástroje MSBuild](/visualstudio/msbuild/msbuild-targets), takže projekt je vyhodnocen při spuštění příkazu. Pouze výstupů během sestavení se vytvořila vymazána. Obě zprostředkující (*obj*) a závěrečný výstup (*bin*) se čištění složky.

## <a name="arguments"></a>Arguments

`PROJECT`

Projekt MSBuild pro čištění. Pokud není zadán soubor projektu, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí na *proj* a použije tento soubor.

## <a name="options"></a>Možnosti

* **`-c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`. Tato možnost je pouze při čištění, pokud jste zadali během doby sestavení vyžaduje.

* **`-f|--framework <FRAMEWORK>`**

  [Framework](../../standard/frameworks.md) , který byl zadán v okamžiku sestavení. Rozhraní musí být definován v [soubor projektu](csproj.md). Pokud jste zadali rozhraní v okamžiku sestavení, je nutné zadat rozhraní framework při čištění souboru.

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Adresář, ve kterém je umístí výstupy sestavení. Zadejte `-f|--framework <FRAMEWORK>` přepnout s přepínačem výstupní adresář, pokud jste zadali rozhraní, když byl projekt sestaven.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Vyčištění výstupní složky zadaného modulu runtime. Používá se při [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) byl vytvořen. Možnost dostupné od verze rozhraní .NET Core 2.0 SDK.

* **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené úrovně jsou q [uiet], m [inimal], n [ormal], d [etailed] a diag [nostic].

## <a name="examples"></a>Příklady

* Vyčištění výchozí sestavení projektu:

  ```console
  dotnet clean
  ```

* Vyčistěte projekt vyvíjené v konfiguraci vydané verze:

  ```console
  dotnet clean --configuration Release
  ```