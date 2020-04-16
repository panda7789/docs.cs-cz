---
title: Dotnet list reference příkaz
description: Příkaz odkazu na seznam dotnet poskytuje vhodnou možnost vypsat odkazy na projekty.
ms.date: 02/14/2020
ms.openlocfilehash: c0ea46298123e69ae527870e50d204d8fcf5cc85
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463648"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Název

`dotnet list reference`- Uvádí odkazy mezi projekty.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] reference

dotnet list -h|--help
```

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
