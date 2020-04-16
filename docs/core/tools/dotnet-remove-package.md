---
title: dotnet odebrat balíček, příkaz
description: Dotnet remove package příkaz poskytuje vhodnou možnost odebrat odkaz na balíček NuGet na projekt.
ms.date: 02/14/2020
ms.openlocfilehash: fc74ac1364a0ed027b83dab270d382f238dc00e5
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463457"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Název

`dotnet remove package`- Odebere odkaz na balíček ze souboru projektu.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME>

dotnet remove package -h|--help
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
