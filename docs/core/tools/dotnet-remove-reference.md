---
title: dotnet – příkaz Remove reference
description: Příkaz dotnet Remove Reference poskytuje pohodlný způsob, jak odebrat projekt odkazům na projekt.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503616"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

## <a name="name"></a>Název

`dotnet remove reference` – odebere odkazy z projektu na projekt.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet remove reference` poskytuje pohodlný způsob, jak odebrat odkazy na projekt z projektu.

## <a name="arguments"></a>Argumenty

`PROJECT`

Cílový soubor projektu. Pokud není zadán, příkaz vyhledá v aktuálním adresáři.

`PROJECT_REFERENCES`

Odkazy z projektu na projekt (P2P), které se mají odebrat. Můžete určit jeden nebo více projektů. [Glob vzory](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v terminálech založených na systému UNIX/Linux.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`-f|--framework <FRAMEWORK>`**

  Odebere odkaz pouze v případě, že cílí na konkrétní [rozhraní](../../standard/frameworks.md).

## <a name="examples"></a>Příklady

- Odebrat odkaz na projekt ze zadaného projektu:

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- Odebrat více odkazů na projekt z projektu v aktuálním adresáři:

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Odebrání více odkazů na projekt pomocí vzoru glob v systému UNIX/Linux:

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
