---
title: dotnet – příkaz odstranění NuGet
description: Příkaz dotnet-NuGet-delete odstraní nebo zruší výpis balíčku ze serveru.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733119"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Název

`dotnet nuget delete` – odstraní nebo zruší výpis balíčku ze serveru.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget delete` odstraní nebo zruší výpis balíčku ze serveru. V případě [NuGet.org](https://www.nuget.org/)je akce odpisovat balíček.

## <a name="arguments"></a>Argumenty

* **`PACKAGE_NAME`**

  Název nebo ID balíčku, který se má odstranit

* **`PACKAGE_VERSION`**

  Verze balíčku, který se má odstranit

## <a name="options"></a>Možnosti

* **`--force-english-output`**

  Vynutí spuštění aplikace s využitím neutrální jazykové verze založené na angličtině.

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

* **`--interactive`**

  Umožňuje příkazu blokovat a vyžadovat ruční akci pro operace, jako je ověřování. Možnost je k dispozici od verze .NET Core 2,2 SDK.

* **`-k|--api-key <API_KEY>`**

  Klíč rozhraní API pro server

* **`--no-service-endpoint`**

  Nepřipojí k zdrojové adrese URL rozhraní API/v2/Package. Možnost je k dispozici od verze .NET Core 2,1 SDK.

* **`--non-interactive`**

  Nezobrazuje výzvu k zadání vstupu uživatele nebo potvrzení.

* **`-s|--source <SOURCE>`**

  Určuje adresu URL serveru. Podporované adresy URL pro nuget.org zahrnují `https://www.nuget.org`, `https://www.nuget.org/api/v3`a `https://www.nuget.org/api/v2/package`. V případě privátních informačních kanálů nahraďte název hostitele (například `%hostname%/api/v3`).

## <a name="examples"></a>Příklady

* Odstraní verzi 1,0 balíčku `Microsoft.AspNetCore.Mvc`:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Odstraní verzi 1,0 balíčku `Microsoft.AspNetCore.Mvc`, nezobrazuje výzvu k zadání přihlašovacích údajů nebo jiného vstupu:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
