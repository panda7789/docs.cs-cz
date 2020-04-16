---
title: dotnet build-server, příkaz
description: Příkaz dotnet build-server spolupracuje se servery spuštěnými sestavením.
ms.date: 02/14/2020
ms.openlocfilehash: 882b697c07aac0e20266f3ad4e6c11888a0b7acc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463728"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Název

`dotnet build-server`- Spolupracuje se servery spuštěnými sestavením.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]

dotnet build-server shutdown -h|--help

dotnet build-server -h|--help
```

## <a name="commands"></a>Příkazy

- **`shutdown`**

  Vypne servery sestavení, které jsou spuštěny z dotnet. Ve výchozím nastavení jsou všechny servery vypnuty.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--msbuild`**

  Vypne server sestavení MSBuild.

- **`--razor`**

  Vypne server sestavení Razor.

- **`--vbcscompiler`**

  Vypne server sestavení kompilátoru VB/C#.
