---
title: příkaz - .NET Core rozhraní příkazového řádku odstranit nuget DotNet.
description: Příkaz dotnet-nuget-delete Odstraní nebo unlists balíčku ze serveru.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 639ade54bfed5eb2de89bdb3b7f451393b4be187
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-nuget-delete"></a>odstranění nuget DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet nuget delete` -Odstraní nebo unlists balíčku ze serveru.

## <a name="synopsis"></a>Stručný obsah

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a>Popis

`dotnet nuget delete` Příkaz odstraní nebo unlists balíčku ze serveru. Pro [nuget.org](https://www.nuget.org/), akce se má unlist balíčku.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Balíček odstranit.

`PACKAGE_VERSION`

Verze balíčku, který má odstranit.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-s|--source <SOURCE>`

Určuje adresu URL serveru. Podporované adresy URL pro zahrnují nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, a `http://www.nuget.org/api/v2/package`. Pro privátní informační kanály, nahraďte název hostitele (například `%hostname%/api/v3`).

`--non-interactive`

Není výzvu pro vstup uživatele nebo potvrzení.

`-k|--api-key <API_KEY>`

Klíč rozhraní API pro server.

`--force-english-output`

Vynutí příkazového řádku výstup v angličtině.

## <a name="examples"></a>Příklady

Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`, není výzvy uživatele pro přihlašovací údaje nebo jiné vstupní:

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`