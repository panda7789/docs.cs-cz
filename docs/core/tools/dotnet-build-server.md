---
title: příkaz serveru sestavení DotNet - .NET Core rozhraní příkazového řádku
description: Serveru sestavení dotnet komunikuje se servery, které jsou spouštěné sestavení.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 929b8d74aa5f3f0ad73b108be8a5bf22f86e30d6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696251"
---
# <a name="dotnet-build"></a>sestavení pro DotNet.

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Název

`dotnet build-server` -Komunikuje se servery, které jsou spouštěné sestavení.

## <a name="synopsis"></a>Stručný obsah

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Příkazy

`shutdown`

Vypne servery sestavení, které jsou spuštěné z dotnet. Ve výchozím nastavení jsou všechny servery vypnout.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--msbuild`

Jejím ukončení MSBuild sestavení serveru.

`--razor`

Jejím ukončení syntaxi Razor sestavení serveru.

`--vbcscompiler`

Ukončí jazyce Visual Basic / kompilátor jazyka C# sestavení serveru.
