---
title: dotnet – příkaz odkazu na seznam
description: Příkaz referenčního seznamu dotnet nabízí pohodlný možnost seznamu odkazů na projekt.
ms.date: 06/26/2019
ms.openlocfilehash: b4b82ca1e7aeb2b73d9f99aff1c97452b2166770
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117674"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Toto téma se týká: ✓** .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet list reference`-Obsahuje odkazy z projektu na projekt.

## <a name="synopsis"></a>Stručný obsah

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Popis

`dotnet list reference` Příkaz nabízí pohodlný možnost zobrazit odkazy projektu pro daný projekt nebo řešení.

## <a name="arguments"></a>Arguments

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
