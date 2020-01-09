---
title: dotnet – příkaz pro úložiště
description: Příkaz dotnet Store ukládá zadaná sestavení do úložiště balíčků modulu runtime.
author: bleroy
ms.date: 05/29/2018
ms.openlocfilehash: 3a81e06f36ffbed68b7cc35de47aa5dca32bab6e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714200"
---
# <a name="dotnet-store"></a>dotnet store

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Name

`dotnet store` – uloží zadaná sestavení do [úložiště balíčků modulu runtime](../deploying/runtime-store.md).

## <a name="synopsis"></a>Stručný obsah

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>Popis

`dotnet store` ukládá zadaná sestavení do [úložiště balíčků modulu runtime](../deploying/runtime-store.md). Ve výchozím nastavení jsou sestavení optimalizována pro cílový modul runtime a rozhraní. Další informace najdete v tématu [úložiště balíčků za běhu](../deploying/runtime-store.md) .

## <a name="required-options"></a>Požadované možnosti

`-f|--framework <FRAMEWORK>`

Určuje [cílovou architekturu](../../standard/frameworks.md).

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

*Soubor manifestu úložiště balíčku* je soubor XML, který obsahuje seznam balíčků, které mají být uloženy. Formát souboru manifestu je kompatibilní s formátem projektu ve stylu sady SDK. Soubor projektu, který odkazuje na požadované balíčky, lze proto použít s možností `-m|--manifest` pro uložení sestavení v úložišti balíčků modulu runtime. Chcete-li zadat více souborů manifestu, opakujte možnost a cestu pro každý soubor. Například: `--manifest packages1.csproj --manifest packages2.csproj`.

`-r|--runtime <RUNTIME_IDENTIFIER>`

[Identifikátor modulu runtime](../rid-catalog.md) , který má být cílen.

## <a name="optional-options"></a>Volitelné možnosti

`--framework-version <FRAMEWORK_VERSION>`

Určuje .NET Core SDK verzi. Tato možnost umožňuje vybrat konkrétní verzi rozhraní nad rámec určenou možností `-f|--framework`.

`-h|--help`

Zobrazí informace o nápovědě.

`-o|--output <OUTPUT_DIRECTORY>`

Určuje cestu k úložišti balíčků modulu runtime. Pokud není zadaný, použije se výchozí podadresář *úložiště* instalačního adresáře .NET Core uživatelského profilu.

`--skip-optimization`

Přeskočí fázi optimalizace.

`--skip-symbols`

Přeskočí generování symbolů. V současné době můžete generovat symboly jenom v systémech Windows a Linux.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

Pracovní adresář použitý příkazem. Pokud není zadaný, použije se podadresář *obj* aktuálního adresáře.

## <a name="examples"></a>Příklady

Uložte balíčky zadané v souboru projektu *Packages. csproj* pro .NET Core 2.0.0:

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

Uložit balíčky zadané v *balíčku. csproj* bez optimalizace:

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>Viz také:

- [Úložiště balíčků modulu runtime](../deploying/runtime-store.md)
