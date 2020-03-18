---
title: dotnet nuget odstranit příkaz
description: Příkaz dotnet-nuget-delete odstraní nebo vyřadí balíček ze serveru.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733119"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Tento článek se týká:** ✔️ .NET Core 1.x SDK a novější verze

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name (Název)

`dotnet nuget delete`- Odstraní nebo unlists balíček ze serveru.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget delete` odstraní nebo odseznamuje balíček ze serveru. Pro [nuget.org](https://www.nuget.org/)je akce zrušit seznam balíčku.

## <a name="arguments"></a>Argumenty

* **`PACKAGE_NAME`**

  Název/ID balíčku, který má být odstraněn.

* **`PACKAGE_VERSION`**

  Verze balíčku odstranit.

## <a name="options"></a>Možnosti

* **`--force-english-output`**

  Vynutí spuštění aplikace pomocí invariantní jazykové verze založené na angličtině.

* **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

* **`--interactive`**

  Umožňuje příkaz blokovat a vyžaduje ruční akci pro operace, jako je ověřování. Možnost je k dispozici od .NET Core 2.2 SDK.

* **`-k|--api-key <API_KEY>`**

  Klíč rozhraní API pro server.

* **`--no-service-endpoint`**

  Nepřipojí "api/v2/package" ke zdrojové adrese URL. Možnost je k dispozici od .NET Core 2.1 SDK.

* **`--non-interactive`**

  Nezobrazí výzvu k zadání uživatele nebo potvrzení.

* **`-s|--source <SOURCE>`**

  Určuje adresu URL serveru. Mezi podporované adresy URL `https://www.nuget.org` `https://www.nuget.org/api/v3`pro `https://www.nuget.org/api/v2/package`nuget.org patří , a . U soukromých informačních kanálů nahraďte `%hostname%/api/v3`název hostitele (například).

## <a name="examples"></a>Příklady

* Odstraní verzi 1.0 `Microsoft.AspNetCore.Mvc`balíčku :

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Odstraní verzi 1.0 `Microsoft.AspNetCore.Mvc`balíčku , nevyzve uživatele k zadání pověření nebo jiného vstupu:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
