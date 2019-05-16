---
title: příkaz DotNet serveru sestavení
description: Příkaz dotnet sestavení serveru komunikuje se servery tím, že sestavení.
ms.date: 04/24/2019
ms.openlocfilehash: fa663bc045e8abfc3375a0226be7d16331b49740
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632087"
---
# <a name="dotnet-build-server"></a>DotNet – server sestavení

**Tento článek se týká: ✓** sady SDK .NET Core 2.1 a novějších verzích

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>Name

`dotnet build-server` -Komunikuje se servery pro spuštění sestavení.

## <a name="synopsis"></a>Souhrn

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Příkazy

* **`shutdown`**

  Vypne sestavovací servery, které jsou spuštěny z dotnet. Ve výchozím nastavení jsou všechny servery vypnout.

## <a name="options"></a>Možnosti

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`--msbuild`**

  Ukončí MSBuild serveru sestavení.

* **`--razor`**

  Server sestavení vypne syntaxi Razor.

* **`--vbcscompiler`**

  Vypne jazyce Visual Basic / server sestavení kompilátor jazyka C#.
