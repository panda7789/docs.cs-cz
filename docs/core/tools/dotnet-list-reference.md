---
title: Dotnet list reference příkaz
description: Příkaz odkazu na seznam dotnet poskytuje vhodnou možnost vypsat odkazy na projekty.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503714"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet list reference`- Uvádí odkazy mezi projekty.

## <a name="synopsis"></a>Synopse

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Popis

Příkaz `dotnet list reference` poskytuje vhodnou možnost vypsat odkazy na projekt pro daný projekt nebo řešení.

## <a name="arguments"></a>Argumenty

* **`PROJECT | SOLUTION`**

  Určuje soubor projektu nebo řešení, který má být používán pro výpis odkazů. Pokud není zadán, příkaz prohledá aktuální adresář pro soubor projektu.

## <a name="options"></a>Možnosti

* **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

## <a name="examples"></a>Příklady

* Seznam odkazů na projekt pro zadaný projekt:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Seznam odkazů na projekt pro projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet list reference
  ```
