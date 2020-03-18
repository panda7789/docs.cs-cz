---
title: dotnet odebrat balíček, příkaz
description: Dotnet remove package příkaz poskytuje vhodnou možnost odebrat odkaz na balíček NuGet na projekt.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503629"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet remove package`- Odebere odkaz na balíček ze souboru projektu.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet remove package` poskytuje vhodnou možnost odebrat odkaz na balíček NuGet z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Určuje soubor projektu. Pokud není zadán, příkaz prohledá aktuální adresář pro jeden.

`PACKAGE_NAME`

Odkaz na balíček odebrat.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

## <a name="examples"></a>Příklady

- Odebrat `Newtonsoft.Json` balíček NuGet z projektu v aktuálním adresáři:

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
