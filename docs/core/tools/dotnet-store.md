---
title: dotnet – příkaz pro úložiště
description: Příkaz dotnet Store ukládá zadaná sestavení do úložiště balíčků modulu runtime.
ms.date: 02/14/2020
ms.openlocfilehash: da1d132b2b873ff55ec104b5bb092d0194889bdc
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503577"
---
# <a name="dotnet-store"></a>dotnet store

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

## <a name="name"></a>Název

`dotnet store` – uloží zadaná sestavení do [úložiště balíčků modulu runtime](../deploying/runtime-store.md).

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]
```

## <a name="description"></a>Popis

`dotnet store` ukládá zadaná sestavení do [úložiště balíčků modulu runtime](../deploying/runtime-store.md). Ve výchozím nastavení jsou sestavení optimalizována pro cílový modul runtime a rozhraní. Další informace najdete v tématu [úložiště balíčků za běhu](../deploying/runtime-store.md) .

## <a name="required-options"></a>Požadované možnosti

- **`-f|--framework <FRAMEWORK>`**

  Určuje [cílovou architekturu](../../standard/frameworks.md). Cílová architektura musí být zadána v souboru projektu.

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  *Soubor manifestu úložiště balíčku* je soubor XML, který obsahuje seznam balíčků, které mají být uloženy. Formát souboru manifestu je kompatibilní s formátem projektu ve stylu sady SDK. Soubor projektu, který odkazuje na požadované balíčky, lze proto použít s možností `-m|--manifest` pro uložení sestavení v úložišti balíčků modulu runtime. Chcete-li zadat více souborů manifestu, opakujte možnost a cestu pro každý soubor. Například: `--manifest packages1.csproj --manifest packages2.csproj`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  [Identifikátor modulu runtime](../rid-catalog.md) , který má být cílen.

## <a name="optional-options"></a>Volitelné možnosti

- **`--framework-version <FRAMEWORK_VERSION>`**

  Určuje .NET Core SDK verzi. Tato možnost umožňuje vybrat konkrétní verzi rozhraní nad rámec určenou možností `-f|--framework`.

- **`-h|--help`**

  Zobrazí informace o nápovědě.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Určuje cestu k úložišti balíčků modulu runtime. Pokud není zadaný, použije se výchozí podadresář *úložiště* instalačního adresáře .NET Core uživatelského profilu.

- **`--skip-optimization`**

  Přeskočí fázi optimalizace.

- **`--skip-symbols`**

  Přeskočí generování symbolů. V současné době můžete generovat symboly jenom v systémech Windows a Linux.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  Pracovní adresář použitý příkazem. Pokud není zadaný, použije se podadresář *obj* aktuálního adresáře.

## <a name="examples"></a>Příklady

- Uložte balíčky zadané v souboru projektu *Packages. csproj* pro .NET Core 2.0.0:

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- Uložit balíčky zadané v *balíčku. csproj* bez optimalizace:

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a>Viz také

- [Úložiště balíčků modulu runtime](../deploying/runtime-store.md)
