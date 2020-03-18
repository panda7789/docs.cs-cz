---
title: dotnet odebrat odkaz, příkaz
description: Dotnet remove reference příkaz poskytuje vhodnou možnost odebrat projekt na odkazy projektu.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503616"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet remove reference`- Odebere odkazy mezi projekty.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet remove reference` poskytuje vhodnou možnost odebrání odkazů na projekt z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Cílový soubor projektu. Pokud není zadán, příkaz prohledá aktuální adresář pro jeden.

`PROJECT_REFERENCES`

Odkazy projektu na projekt (P2P) k odstranění. Můžete zadat jeden nebo více projektů. Glob vzory jsou [podporovány](https://en.wikipedia.org/wiki/Glob_(programming)) na Unix / Linux založené terminály.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`-f|--framework <FRAMEWORK>`**

  Odebere odkaz pouze při cílení na konkrétní [rámec](../../standard/frameworks.md).

## <a name="examples"></a>Příklady

- Odeberte odkaz na projekt ze zadaného projektu:

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- Odebrání více odkazů na projekt z projektu v aktuálním adresáři:

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Odstraňte více odkazů na projekt pomocí glob vzoru na Unix /Linux:

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
