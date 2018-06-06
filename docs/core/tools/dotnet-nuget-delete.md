---
title: příkaz - .NET Core rozhraní příkazového řádku odstranit nuget DotNet.
description: Příkaz dotnet-nuget-delete Odstraní nebo unlists balíčku ze serveru.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: 1b58136d0bc04947f0a5baba320e5e6b3e45e2f1
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728411"
---
# <a name="dotnet-nuget-delete"></a>odstranění nuget DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet nuget delete` -Odstraní nebo unlists balíčku ze serveru.

## <a name="synopsis"></a>Stručný obsah

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
# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet nuget delete` Příkaz odstraní nebo unlists balíčku ze serveru. Pro [nuget.org](https://www.nuget.org/), akce se má unlist balíčku.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Název nebo ID balíčku, který má odstranit.

`PACKAGE_VERSION`

Verze balíčku, který má odstranit.

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--force-english-output`

 Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-k|--api-key <API_KEY>`

Klíč rozhraní API pro server.

`--no-service-endpoint` Není připojit "v2/api/balíček" na adresu URL zdroje.

`--non-interactive`

Není výzvu pro vstup uživatele nebo potvrzení.

`-s|--source <SOURCE>`

Určuje adresu URL serveru. Podporované adresy URL pro zahrnují nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, a `http://www.nuget.org/api/v2/package`. Pro privátní informační kanály, nahraďte název hostitele (například `%hostname%/api/v3`).

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--force-english-output`

 Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-k|--api-key <API_KEY>`

Klíč rozhraní API pro server.

`--non-interactive`

Není výzvu pro vstup uživatele nebo potvrzení.

`-s|--source <SOURCE>`

Určuje adresu URL serveru. Podporované adresy URL pro zahrnují nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, a `http://www.nuget.org/api/v2/package`. Pro privátní informační kanály, nahraďte název hostitele (například `%hostname%/api/v3`).

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`--force-english-output`

 Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-k|--api-key <API_KEY>`

Klíč rozhraní API pro server.

`--non-interactive`

Není výzvu pro vstup uživatele nebo potvrzení.

`-s|--source <SOURCE>`

Určuje adresu URL serveru. Podporované adresy URL pro zahrnují nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, a `http://www.nuget.org/api/v2/package`. Pro privátní informační kanály, nahraďte název hostitele (například `%hostname%/api/v3`).

---

## <a name="examples"></a>Příklady

Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`, není výzvy uživatele pro přihlašovací údaje nebo jiné vstupní:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
