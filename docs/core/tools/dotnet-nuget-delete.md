---
title: příkaz – rozhraní příkazového řádku .NET Core DotNet nuget delete
description: Příkaz dotnet-nuget-delete Odstraní nebo unlists balíčku ze serveru.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: f4aa027a465c4adea1de13853063d03e8e295411
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180874"
---
# <a name="dotnet-nuget-delete"></a>DotNet nuget delete

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet nuget delete` -Odstraní nebo unlists balíčku ze serveru.

## <a name="synopsis"></a>Souhrn

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet nuget delete` Příkaz odstraní nebo unlists balíčku ze serveru. Pro [nuget.org](https://www.nuget.org/), "action" je k vyjmutí ze seznamu balíčku.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Název nebo ID balíčku, který se odstranit.

`PACKAGE_VERSION`

Verze balíčku, který se odstranit.

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--force-english-output`

 Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-k|--api-key <API_KEY>`

Klíč rozhraní API pro server.

`--no-service-endpoint` "Api/v2/balíček" nemá připojení k zdrojová adresa URL.

`--non-interactive`

Není výzvu k zadání uživatele o vstup ani potvrzení.

`-s|--source <SOURCE>`

Určuje adresu URL serveru. Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`. Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--force-english-output`

 Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-k|--api-key <API_KEY>`

Klíč rozhraní API pro server.

`--non-interactive`

Není výzvu k zadání uživatele o vstup ani potvrzení.

`-s|--source <SOURCE>`

Určuje adresu URL serveru. Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`. Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--force-english-output`

 Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-k|--api-key <API_KEY>`

Klíč rozhraní API pro server.

`--non-interactive`

Není výzvu k zadání uživatele o vstup ani potvrzení.

`-s|--source <SOURCE>`

Určuje adresu URL serveru. Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`. Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).

---

## <a name="examples"></a>Příklady

Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`, ne výzvou pro uživatele pro přihlašovací údaje nebo druhý vstup:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
