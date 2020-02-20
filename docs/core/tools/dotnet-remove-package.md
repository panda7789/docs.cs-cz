---
title: dotnet – odebrat balíček – příkaz
description: Příkaz dotnet Remove Package nabízí pohodlný způsob, jak odebrat odkaz na balíček NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503629"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

## <a name="name"></a>Název

`dotnet remove package` – odebere odkaz na balíček ze souboru projektu.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet remove package` poskytuje pohodlný způsob, jak odebrat odkaz na balíček NuGet z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Určuje soubor projektu. Pokud není zadán, příkaz vyhledá v aktuálním adresáři.

`PACKAGE_NAME`

Odkaz na balíček, který se má odebrat

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

## <a name="examples"></a>Příklady

- Odebrat `Newtonsoft.Json` balíček NuGet z projektu v aktuálním adresáři:

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
