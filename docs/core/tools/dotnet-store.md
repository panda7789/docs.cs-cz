---
title: dotnet store, příkaz
description: Příkaz 'dotnet store' ukládá zadaná sestavení v runtime package store.
ms.date: 02/14/2020
ms.openlocfilehash: 2f28a9bc287a87f600bda385c579e8070cbaa5ab
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463387"
---
# <a name="dotnet-store"></a>dotnet store

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Název

`dotnet store`- Ukládá zadaná sestavení v [runtime package store](../deploying/runtime-store.md).

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet store -m|--manifest <PATH_TO_MANIFEST_FILE>
    -f|--framework <FRAMEWORK_VERSION> -r|--runtime <RUNTIME_IDENTIFIER>
    [--framework-version <FRAMEWORK_VERSION>] [--output <OUTPUT_DIRECTORY>]
    [--skip-optimization] [--skip-symbols] [-v|--verbosity <LEVEL>]
    [--working-dir <WORKING_DIRECTORY>]

dotnet store -h|--help
```

## <a name="description"></a>Popis

`dotnet store`ukládá zadaná sestavení do [runtime package store](../deploying/runtime-store.md). Ve výchozím nastavení jsou sestavení optimalizována pro cílový běh za běhu a rozhraní. Další informace naleznete v tématu [runtime package store.](../deploying/runtime-store.md)

## <a name="required-options"></a>Požadované možnosti

- **`-f|--framework <FRAMEWORK>`**

  Určuje [cílovou architekturu](../../standard/frameworks.md). Cílová architektura musí být zadána v souboru projektu.

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  *Soubor manifestu úložiště balíčků* je soubor XML, který obsahuje seznam balíčků k uložení. Formát souboru manifestu je kompatibilní s formátem projektu ve stylu sady SDK. Takže soubor projektu, který odkazuje na požadované balíčky lze použít s `-m|--manifest` možností ukládat sestavení v úložišti balíčků runtime. Chcete-li určit více souborů manifestu, opakujte volbu a cestu pro každý soubor. Například: `--manifest packages1.csproj --manifest packages2.csproj`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  [Identifikátor za běhu](../rid-catalog.md) cíl.

## <a name="optional-options"></a>Volitelné možnosti

- **`--framework-version <FRAMEWORK_VERSION>`**

  Určuje verzi sady .NET Core SDK. Tato možnost umožňuje vybrat konkrétní verzi architektury nad `-f|--framework` rámec určený možností.

- **`-h|--help`**

  Zobrazí informace nápovědy.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Určuje cestu k runtime package store. Pokud není zadán, je výchozí podadresář *úložiště* instalačního adresáře .NET Core.

- **`--skip-optimization`**

  Přeskočí fázi optimalizace.

- **`--skip-symbols`**

  Přeskočí generování symbolů. V současné době můžete generovat pouze symboly v systému Windows a Linux.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  Pracovní adresář používaný příkazem. Pokud není zadán, používá *podadresář obj* aktuálního adresáře.

## <a name="examples"></a>Příklady

- Uložte balíčky zadané v souboru projektu *packages.csproj* pro rozhraní .NET Core 2.0.0:

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- Uložte balíčky zadané v *packages.csproj* bez optimalizace:

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a>Viz také

- [Úložiště balíčků modulu runtime](../deploying/runtime-store.md)
