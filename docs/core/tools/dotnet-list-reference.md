---
title: dotnet – příkaz odkazu na seznam
description: Příkaz referenčního seznamu dotnet nabízí pohodlný možnost seznamu odkazů na projekt.
ms.date: 06/26/2019
ms.openlocfilehash: 496cbcd8fa4d921e30b363904ad0273bd5ebacd5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733220"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Název

`dotnet list reference` – vypíše odkazy z projektu na projekt.

## <a name="synopsis"></a>Stručný obsah

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Popis

Příkaz `dotnet list reference` poskytuje pohodlný způsob pro výpis odkazů projektu pro daný projekt nebo řešení.

## <a name="arguments"></a>Argumenty

* **`PROJECT | SOLUTION`**

  Určuje soubor projektu nebo řešení, který se má použít pro výpis odkazů. Pokud není zadán, příkaz vyhledá v aktuálním adresáři soubor projektu.

## <a name="options"></a>Možnosti

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

## <a name="examples"></a>Příklady

* Vypíše odkazy projektu pro zadaný projekt:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Vypíše odkazy na projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet list reference
  ```
