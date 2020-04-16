---
title: dotnet nuget push, příkaz
description: Příkaz push dotnet nuget odešle balíček na server a publikuje jej.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 96f8d008c8306a0782d5149360a24bb4097a1ec4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463521"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Název

`dotnet nuget push`- Odešle balíček na server a publikuje jej.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget push` odešle balíček na server a publikuje jej. Příkaz push používá podrobnosti o serveru a pověření, které se nacházejí v konfiguračním souboru nuget systému nebo v řetězci konfiguračních souborů. Další informace o konfiguračních souborech naleznete [v tématu Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior). Výchozí konfigurace nugetu je získána načtením *%AppData%\NuGet\NuGet.config* (Windows) nebo *$HOME/.local/share* (Linux/macOS), potom načtením *libovolného souboru nuget.config* nebo *.nuget\nuget.config* počínaje kořenem jednotky a končícím v aktuálním adresáři.

## <a name="arguments"></a>Argumenty

- **`ROOT`**

  Určuje cestu k souboru, který má být posunut.

## <a name="options"></a>Možnosti

- **`-d|--disable-buffering`**

  Zakáže ukládání do vyrovnávací paměti při odesílání na server HTTP(S), aby se snížilo využití paměti.

- **`--force-english-output`**

  Vynutí spuštění aplikace pomocí invariantní jazykové verze založené na angličtině.

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--interactive`**

  Umožňuje příkaz blokovat a vyžaduje ruční akci pro operace, jako je ověřování. Možnost je k dispozici od .NET Core 2.2 SDK.

- **`-k|--api-key <API_KEY>`**

  Klíč rozhraní API pro server.

- **`-n|--no-symbols`**

  Netlačí symboly (i když jsou k dispozici).

- **`--no-service-endpoint`**

  Nepřipojí "api/v2/package" ke zdrojové adrese URL. Možnost je k dispozici od .NET Core 2.1 SDK.

- **`-s|--source <SOURCE>`**

  Určuje adresu URL serveru. Tato možnost je `DefaultPushSource` vyžadována, pokud není v konfiguračním souboru NuGet nastavena hodnota konfigurace.

- **`--skip-duplicate`**

  Při odesílání více balíčků na server HTTP(S) považuje všechny 409 konflikt odpověď jako upozornění tak, aby push může pokračovat. K dispozici od .NET Core 3.1 SDK.

- **`-sk|--symbol-api-key <API_KEY>`**

  Klíč rozhraní API pro server symbolů.

- **`-ss|--symbol-source <SOURCE>`**

  Určuje adresu URL serveru symbolů.

- **`-t|--timeout <TIMEOUT>`**

  Určuje časový limit pro odesílání na server v sekundách. Výchozí hodnota je 300 sekund (5 minut). Zadáním 0 (nula sekund) se použije výchozí hodnota.

## <a name="examples"></a>Příklady

- Odešle *foo.nupkg* na výchozí zdroj nabízených oznámení a zadá klíč rozhraní API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- Push *foo.nupkg* na oficiální server NuGet a zadejte klíč rozhraní API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * Posuňte *foo.nupkg* na vlastní zdroj `https://customsource`nabízených síly a zadejte klíč rozhraní API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- Posune *foo.nupkg* na výchozí zdroj push:

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- Odešle *foo.symbols.nupkg* na výchozí zdroj symbolů:

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- Odešle *foo.nupkg* na výchozí zdroj nabízených oznámení a určí časový limit 360 sekund:

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- Odešle všechny soubory *NUPKG* v aktuálním adresáři na výchozí zdroj nabízených oznámení:

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > Pokud tento příkaz nefunguje, může to být způsobeno chybou, která existovala ve starších verzích sady SDK (.NET Core 2.1 SDK a starších verzích).
  > Chcete-li tento problém vyřešit, inovujte verzi sady SDK nebo spusťte místo toho následující příkaz:`dotnet nuget push **/*.nupkg`

- Odešle všechny soubory *.nupkg* i v případě, že server HTTP(S) vrátí odpověď konfliktu 409:

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
