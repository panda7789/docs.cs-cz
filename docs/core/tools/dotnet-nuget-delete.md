---
title: příkaz DotNet nuget delete
description: Příkaz dotnet-nuget-delete Odstraní nebo unlists balíčku ze serveru.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: a657fa273ca6b5229a1713fbcaf003217a59fd7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648671"
---
# <a name="dotnet-nuget-delete"></a>DotNet nuget delete

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet nuget delete` -Odstraní nebo unlists balíčku ze serveru.

## <a name="synopsis"></a>Souhrn

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```

---

## <a name="description"></a>Popis

`dotnet nuget delete` Příkaz odstraní nebo unlists balíčku ze serveru. Pro [nuget.org](https://www.nuget.org/), "action" je k vyjmutí ze seznamu balíčku.

## <a name="arguments"></a>Arguments

* **`PACKAGE_NAME`**

  Název nebo ID balíčku, který se odstranit.

* **`PACKAGE_VERSION`**

  Verze balíčku, který se odstranit.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

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

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

* **`--force-english-output`**

  Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`-k|--api-key <API_KEY>`**

  Klíč rozhraní API pro server.

* **`--non-interactive`**

  Není výzvu k zadání uživatele o vstup ani potvrzení.

* **`-s|--source <SOURCE>`**

  Určuje adresu URL serveru. Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`. Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).

---

## <a name="examples"></a>Příklady

* Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`, ne výzvou pro uživatele pro přihlašovací údaje nebo druhý vstup:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```