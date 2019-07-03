---
title: příkaz DotNet nuget delete
description: Příkaz dotnet-nuget-delete Odstraní nebo unlists balíčku ze serveru.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0b2ba64b70bae5e06f213457e30fedeca26a9819
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539256"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Toto téma platí pro: ✓** .NET Core 1.x sady SDK a novějších verzích

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet nuget delete` -Odstraní nebo unlists balíčku ze serveru.

## <a name="synopsis"></a>Souhrn

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Popis

`dotnet nuget delete` Příkaz odstraní nebo unlists balíčku ze serveru. Pro [nuget.org](https://www.nuget.org/), "action" je k vyjmutí ze seznamu balíčku.

## <a name="arguments"></a>Arguments

* **`PACKAGE_NAME`**

  Název nebo ID balíčku, který se odstranit.

* **`PACKAGE_VERSION`**

  Verze balíčku, který se odstranit.

## <a name="options"></a>Možnosti

* **`--force-english-output`**

  Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`--interactive`**

  Umožňuje příkazu blokování a vyžaduje ruční akci pro operace, jako je například ověřování. Možnost dostupné od verze sady SDK 2.2 .NET Core.

* **`-k|--api-key <API_KEY>`**

  Klíč rozhraní API pro server.

* **`--no-service-endpoint`**

  "Api/v2/balíček" nemá připojení k zdrojová adresa URL. Možnost dostupné od verze sady SDK .NET Core 2.1.

* **`--non-interactive`**

  Není výzvu k zadání uživatele o vstup ani potvrzení.

* **`-s|--source <SOURCE>`**

  Určuje adresu URL serveru. Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`. Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).

## <a name="examples"></a>Příklady

* Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`, ne výzvou pro uživatele pro přihlašovací údaje nebo druhý vstup:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
