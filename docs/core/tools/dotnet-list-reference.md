---
title: dotnet – příkaz odkazu na seznam
description: Příkaz referenčního seznamu dotnet nabízí pohodlný možnost seznamu odkazů na projekt.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503714"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

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
