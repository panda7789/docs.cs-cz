---
title: dotnet odebrat odkaz, příkaz
description: Dotnet remove reference příkaz poskytuje vhodnou možnost odebrat projekt na odkazy projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 92d36bbbde64d806abc8f223c5f08e3f3d79ce9d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463445"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Název

`dotnet remove reference`- Odebere odkazy mezi projekty.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>] <PROJECT_REFERENCES>

dotnet remove reference -h|--help
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
