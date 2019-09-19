---
title: dotnet – sestavení – příkaz serveru
description: Příkaz dotnet Build-Server komunikuje s servery spuštěnými sestavením.
ms.date: 04/24/2019
ms.openlocfilehash: 89d1aba104e2cb07b46766a3768eed68d85a7aa7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117771"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Tento článek se týká: ✓** .net Core 2,1 SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>Name

`dotnet build-server`-Komunikuje se servery spuštěnými sestavením.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Příkazy

* **`shutdown`**

  Ukončí sestavovací servery, které jsou spuštěny z dotnet. Ve výchozím nastavení jsou všechny servery vypnuté.

## <a name="options"></a>Možnosti

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

* **`--msbuild`**

  Vypne server sestavení MSBuild.

* **`--razor`**

  Vypne server sestavení Razor.

* **`--vbcscompiler`**

  Ukončí server sestavení VB/C# Compiler.
