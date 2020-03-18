---
title: dotnet build-server, příkaz
description: Příkaz dotnet build-server spolupracuje se servery spuštěnými sestavením.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503776"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet build-server`- Spolupracuje se servery spuštěnými sestavením.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
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
