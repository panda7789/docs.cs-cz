---
title: příkaz nabízené DotNet nuget - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet nuget nabízené nabízených oznámení balíček na server a vydává je.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: 8a64f9cdc11d03bed82a132265c3b4e1de290807
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728573"
---
# <a name="dotnet-nuget-push"></a>nabízená nuget DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet nuget push` -Sami balíček na server a vydává je.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet nuget push` Příkaz nabízených oznámení balíček na server a vydává je. Příkaz nabízené používá server a podrobnosti o přihlašovacích údajích, které najde v konfiguračním souboru systému NuGet nebo řetězu konfigurační soubory. Další informace o konfigurační soubory, najdete v části [konfigurace chování NuGet](/nuget/consume-packages/configuring-nuget-behavior). NuGet výchozí konfiguraci se získávají načtením *%AppData%\NuGet\NuGet.config* (Windows) nebo *$HOME/.local/share* (Linux/systému macOS), pak všechny načítání *nuget.config*nebo *.nuget\nuget.config* z kořene jednotky počáteční a koncovou v aktuálním adresáři.

## <a name="arguments"></a>Arguments

`ROOT`

Určuje cestu k souboru na balíček, který chcete poslat.

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`-d|--disable-buffering`

Zakáže ukládání do vyrovnávací paměti při nabízení do serveru protokolu HTTP (S) ke snížení využití paměti.

`--force-english-output`

Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-k|--api-key <API_KEY>`

Klíč rozhraní API pro server.

`-n|--no-symbols`

Není push symboly (i pokud existuje).

`--no-service-endpoint`

Není připojit "v2/api/balíček" na adresu URL zdroje.

`-s|--source <SOURCE>`

Určuje adresu URL serveru. Tato možnost je povinná, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.

`-sk|--symbol-api-key <API_KEY>`

Klíč rozhraní API pro symbol server.

`-ss|--symbol-source <SOURCE>`

Určuje adresu URL serveru symbol.

`-t|--timeout <TIMEOUT>`

Určuje časový limit pro vkládání na server v sekundách. Výchozí hodnota je 300 sekund (5 minut). Zadáním 0 (nula sekund) platí výchozí hodnota.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`-d|--disable-buffering`

Zakáže ukládání do vyrovnávací paměti při nabízení do serveru protokolu HTTP (S) ke snížení využití paměti.

`--force-english-output`

Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-k|--api-key <API_KEY>`

Klíč rozhraní API pro server.

`-n|--no-symbols`

Není push symboly (i pokud existuje).

`-s|--source <SOURCE>`

Určuje adresu URL serveru. Tato možnost je povinná, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.

`-sk|--symbol-api-key <API_KEY>`

Klíč rozhraní API pro symbol server.

`-ss|--symbol-source <SOURCE>`

Určuje adresu URL serveru symbol.

`-t|--timeout <TIMEOUT>`

Určuje časový limit pro vkládání na server v sekundách. Výchozí hodnota je 300 sekund (5 minut). Zadáním 0 (nula sekund) platí výchozí hodnota.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`-d|--disable-buffering`

Zakáže ukládání do vyrovnávací paměti při nabízení do serveru protokolu HTTP (S) ke snížení využití paměti.

`--force-english-output`

Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-k|--api-key <API_KEY>`

Klíč rozhraní API pro server.

`-n|--no-symbols`

Není push symboly (i pokud existuje).

`-s|--source <SOURCE>`

Určuje adresu URL serveru. Tato možnost je povinná, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.

`-sk|--symbol-api-key <API_KEY>`

Klíč rozhraní API pro symbol server.

`-ss|--symbol-source <SOURCE>`

Určuje adresu URL serveru symbol.

`-t|--timeout <TIMEOUT>`

Určuje časový limit pro vkládání na server v sekundách. Výchozí hodnota je 300 sekund (5 minut). Zadáním 0 (nula sekund) platí výchozí hodnota.

---

## <a name="examples"></a>Příklady

Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí zadání klíč rozhraní API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Nabízená *foo.nupkg* ke zdroji vlastní nabízené `http://customsource`, zadání klíč rozhraní API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí:

`dotnet nuget push foo.nupkg`

Nabízených oznámení *foo.symbols.nupkg* ke zdroji výchozí symboly:

`dotnet nuget push foo.symbols.nupkg`

Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí zadání vypršení časového limitu 360 sekundu:

`dotnet nuget push foo.nupkg --timeout 360`

Všechny sami *.nupkg* soubory v aktuálním adresáři ke zdroji nabízené výchozí:

`dotnet nuget push *.nupkg`

Všechny sami *.nupkg* soubory v aktuálním adresáři ke zdroji nabízené výchozí, zadáním souboru vlastní konfigurace *./config/My.Config*:

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
