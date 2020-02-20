---
title: dotnet – sestavení – příkaz serveru
description: Příkaz dotnet Build-Server komunikuje s servery spuštěnými sestavením.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503776"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet build-server` – spolupracuje se servery spuštěnými sestavením.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Příkazy

- **`shutdown`**

  Ukončí sestavovací servery, které jsou spuštěny z dotnet. Ve výchozím nastavení jsou všechny servery vypnuté.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--msbuild`**

  Vypne server sestavení MSBuild.

- **`--razor`**

  Vypne server sestavení Razor.

- **`--vbcscompiler`**

  Ukončí server sestavení VB/C# Compiler.
