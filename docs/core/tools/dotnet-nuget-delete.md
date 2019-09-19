---
title: dotnet – příkaz odstranění NuGet
description: Příkaz dotnet-NuGet-delete odstraní nebo zruší výpis balíčku ze serveru.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 79634baa9d6d7ff1f388f6a794ffd816687be105
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117632"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Toto téma se týká: ✓** .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet nuget delete`-Odstraní nebo zruší výpis balíčku ze serveru.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Popis

`dotnet nuget delete` Příkaz odstraní nebo zruší výpis balíčku ze serveru. V případě [NuGet.org](https://www.nuget.org/)je akce odpisovat balíček.

## <a name="arguments"></a>Arguments

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

  Určuje adresu URL serveru. Podporované adresy URL pro NuGet.org `https://www.nuget.org`zahrnují `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`. V případě privátních informačních kanálů nahraďte název hostitele (například `%hostname%/api/v3`).

## <a name="examples"></a>Příklady

* Odstraní verzi 1,0 balíčku `Microsoft.AspNetCore.Mvc`:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Odstraní verzi 1,0 balíčku `Microsoft.AspNetCore.Mvc`, nezobrazuje výzvu k zadání přihlašovacích údajů uživatele nebo jiný vstup:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
