---
title: dotnet – příkaz push NuGet
description: Příkaz dotnet NuGet push odešle balíček na server a publikuje ho.
author: karann-msft
ms.date: 12/04/2019
ms.openlocfilehash: a352120efa199b871e67eb8ba2442bd69a9fc4ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789873"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet nuget push` – odešle balíček na server a publikuje ho.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget push` odešle balíček na server a publikuje ho. Příkaz push používá podrobnosti serveru a přihlašovacích údajů, které se našly v konfiguračním souboru NuGet systému nebo v řetězci konfiguračních souborů. Další informace o konfiguračních souborech najdete v tématu [Konfigurace chování NuGet](/nuget/consume-packages/configuring-nuget-behavior). Výchozí konfigurace NuGet se získá tak, že se načtou *%AppData%\NuGet\NuGet.config* (Windows) nebo *$Home/.local/share* (Linux/MacOS) a pak se načte jakákoli soubor *NuGet. config* nebo *. NuGet\NuGet.config* počínaje kořenovým adresářem jednotky a končí aktuálním adresářem.

## <a name="arguments"></a>Arguments

* **`ROOT`**

  Určuje cestu k balíčku, který má být vložen.

## <a name="options"></a>Možnosti

* **`-d|--disable-buffering`**

  Zakáže ukládání do vyrovnávací paměti při doručování na server HTTP (S), aby se snížilo využití paměti.

* **`--force-english-output`**

  Vynutí spuštění aplikace s využitím neutrální jazykové verze založené na angličtině.

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

* **`--interactive`**

  Umožňuje příkazu blokovat a vyžadovat ruční akci pro operace, jako je ověřování. Možnost je k dispozici od verze .NET Core 2,2 SDK.

* **`-k|--api-key <API_KEY>`**

  Klíč rozhraní API pro server

* **`-n|--no-symbols`**

  Symboly nejsou nabízeny (i v případě, že jsou k dispozici).

* **`--no-service-endpoint`**

  Nepřipojí k zdrojové adrese URL rozhraní API/v2/Package. Možnost je k dispozici od verze .NET Core 2,1 SDK.

* **`-s|--source <SOURCE>`**

  Určuje adresu URL serveru. Tato možnost je povinná, pokud v konfiguračním souboru NuGet není nastavená hodnota `DefaultPushSource` config.

* **`--skip-duplicate`**

  Při nahrávání více balíčků na server HTTP (S) zachází s každou odpovědí na 409 konfliktů jako s upozorněním, aby bylo možné pokračovat v nabízení. K dispozici od verze .NET Core 3,1 SDK.

* **`-sk|--symbol-api-key <API_KEY>`**

  Klíč rozhraní API pro server symbolů.

* **`-ss|--symbol-source <SOURCE>`**

  Určuje adresu URL serveru symbolů.

* **`-t|--timeout <TIMEOUT>`**

  Určuje časový limit pro doručování na server během několika sekund. Výchozí hodnota je 300 sekund (5 minut). Zadáním hodnoty 0 (nula sekund) se použije výchozí hodnota.

## <a name="examples"></a>Příklady

* Vloží *foo. nupkg* na výchozí zdroj nabízených oznámení a určí klíč rozhraní API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* Vložení *foo. nupkg* do oficiálního serveru NuGet a zadání klíče rozhraní API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * Vložení *foo. nupkg* do vlastního `https://customsource`zdroje nabízených oznámení zadání klíče rozhraní API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* Vloží *foo. nupkg* na výchozí zdroj nabízených oznámení:

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

* Vloží *foo. Symbols. nupkg* na výchozí zdroj symbolů:

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

* Vloží *foo. nupkg* na výchozí zdroj nabízených oznámení a určí časový limit 360 sekund:

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

* Vloží všechny soubory *. nupkg* v aktuálním adresáři do výchozího zdroje nabízených oznámení:

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > Pokud tento příkaz nefunguje, může to být způsobeno chybou, která existovala ve starších verzích sady SDK (.NET Core 2,1 SDK a starších verzích).
  > Pokud to chcete opravit, upgradujte verzi sady SDK nebo spusťte následující příkaz: `dotnet nuget push **/*.nupkg`

* Vloží všechny soubory *. nupkg* i v případě, že server http (S) vrátí odpověď na konflikt 409:

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
