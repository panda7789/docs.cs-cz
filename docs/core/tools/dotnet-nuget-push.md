---
title: "příkaz nabízené DotNet nuget - .NET Core rozhraní příkazového řádku"
description: "Příkaz dotnet nuget nabízené nabízených oznámení balíček na server a vydává je."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: a0f872ae930d17638e018cdd204cc08a773a3df5
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2018
---
# <a name="dotnet-nuget-push"></a>nabízená nuget DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet nuget push` -Sami balíček na server a vydává je.

## <a name="synopsis"></a>Stručný obsah

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a>Popis

`dotnet nuget push` Příkaz nabízených oznámení balíček na server a vydává je. Příkaz nabízené používá server a podrobnosti o přihlašovacích údajích, které najde v konfiguračním souboru systému NuGet nebo řetězu konfigurační soubory. Další informace o konfigurační soubory, najdete v části [konfigurace chování NuGet](/nuget/consume-packages/configuring-nuget-behavior). NuGet výchozí konfiguraci se získávají načtením *%AppData%\NuGet\NuGet.config* (Windows) nebo *$HOME/.local/share* (Linux/systému macOS), pak všechny načítání *nuget.config*nebo *.nuget\nuget.config* z kořene jednotky počáteční a koncovou v aktuálním adresáři.

## <a name="arguments"></a>Arguments

`ROOT`

Určuje cestu k souboru na balíček, který chcete poslat.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-s|--source <SOURCE>`

Určuje adresu URL serveru. Tato možnost je povinná, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.

`--symbol-source <SOURCE>`

Určuje adresu URL serveru symbol.

`-t|--timeout <TIMEOUT>`

Určuje časový limit pro vkládání na server v sekundách. Výchozí hodnota je 300 sekund (5 minut). Zadáním 0 (nula sekund) platí výchozí hodnota.

`-k|--api-key <API_KEY>`

Klíč rozhraní API pro server.

`--symbol-api-key <API_KEY>`

Klíč rozhraní API pro symbol server.

`-d|--disable-buffering`

Zakáže ukládání do vyrovnávací paměti při nabízení do serveru protokolu HTTP (S), jak snížit využití paměti.

`-n|--no-symbols`

Není push symboly (i pokud existuje).

`--force-english-output`

Vynutí protokolovat výstup v angličtině.

## <a name="examples"></a>Příklady

Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí poskytování klíč rozhraní API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Nabízená *foo.nupkg* ke zdroji vlastní nabízené `http://customsource`, poskytuje klíč rozhraní API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí:

`dotnet nuget push foo.nupkg`

Nabízených oznámení *foo.symbols.nupkg* ke zdroji výchozí symboly:

`dotnet nuget push foo.symbols.nupkg`

Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí zadání 360 druhý vypršení časového limitu:

`dotnet nuget push foo.nupkg --timeout 360`

Všechny sami *.nupkg* soubory v aktuálním adresáři ke zdroji nabízené výchozí:

`dotnet nuget push *.nupkg`

Všechny sami *.nupkg* soubory v aktuálním adresáři ke zdroji nabízené výchozí, zadáním souboru vlastní konfigurace *./config/My.Config*:

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
