---
title: příkaz DotNet úložiště
description: "'Dotnet Restore' příkaz uloží na zadaná sestavení do úložiště balíčků modulu runtime."
author: bleroy
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 58889039d117a2231cda693e4aca7790f018d1b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648604"
---
# <a name="dotnet-store"></a>DotNet Restore

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Název

`dotnet store` -Ukládá zadané sestavení v [úložiště balíčků modulu runtime](../deploying/runtime-store.md).

## <a name="synopsis"></a>Souhrn

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>Popis

`dotnet store` ukládá zadané sestavení v [úložiště balíčků modulu runtime](../deploying/runtime-store.md). Ve výchozím nastavení jsou sestavení optimalizované pro cílový modul runtime a rozhraní. Další informace najdete v tématu [úložiště balíčků modulu runtime](../deploying/runtime-store.md) tématu.

## <a name="required-options"></a>Požadované možnosti

`-f|--framework <FRAMEWORK>`

Určuje, [Cílová architektura](../../standard/frameworks.md).

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

*Souboru manifestu balíčku úložiště* je soubor XML, který obsahuje seznam balíčků pro uložení. Formát souboru manifestu je kompatibilní s formátem SDK – vizuální styl projektu. Ano, soubor projektu, který odkazuje na požadované balíčky je možné s `-m|--manifest` možnosti k uložení sestavení v úložiště balíčků modulu runtime. Pokud chcete zadat více souborů manifestu, opakujte pro každý soubor možnost a cestu. Například: `--manifest packages1.csproj --manifest packages2.csproj`.

`-r|--runtime <RUNTIME_IDENTIFIER>`

[Identifikátor modulu runtime](../rid-catalog.md) do cíle.

## <a name="optional-options"></a>Volitelné možnosti

`--framework-version <FRAMEWORK_VERSION>`

Určuje verzi .NET Core SDK. Tato možnost umožňuje vybrat konkrétní verzi rozhraní framework verze mimo rámec určené `-f|--framework` možnost.

`-h|--help`

Zobrazí nápovědu informace.

`-o|--output <OUTPUT_DIRECTORY>`

Určuje cestu k úložiště balíčků modulu runtime. Pokud není zadán, použije se výchozí *ukládání* podadresář instalační adresář uživatelského profilu .NET Core.

`--skip-optimization`

Přeskočí fáze optimalizace.

`--skip-symbols`

Přeskočí symbol generace. V současné době můžete generovat jenom symboly, s Windows a Linux.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

Pracovní adresář použité příkazem. Pokud není zadán, použije *obj* podadresář aktuálního adresáře.

## <a name="examples"></a>Příklady

Balíčky zadané v Store *packages.csproj* soubor projektu pro .NET Core 2.0.0:

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

Balíčky zadané v Store *packages.csproj* bez optimalizace:

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>Viz také:

- [Úložiště balíčků modulu runtime](../deploying/runtime-store.md)
