---
title: příkaz DotNet server sestavení – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet sestavení serveru komunikuje se servery tím, že sestavení.
author: mairaw
ms.author: mairaw
ms.date: 07/02/2018
ms.openlocfilehash: 1c59c85f246b79c7e2552f704db5b4f076f9b502
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404330"
---
# <a name="dotnet-build-server"></a>DotNet – server sestavení

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Název

`dotnet build-server` -Komunikuje se servery pro spuštění sestavení.

## <a name="synopsis"></a>Souhrn

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Příkazy

`shutdown`

Vypne sestavovací servery, které jsou spuštěny z dotnet. Ve výchozím nastavení jsou všechny servery vypnout.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--msbuild`

Ukončí MSBuild serveru sestavení.

`--razor`

Server sestavení vypne syntaxi Razor.

`--vbcscompiler`

Vypne jazyce Visual Basic / server sestavení kompilátor jazyka C#.
