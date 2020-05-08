---
title: dotnet – příkaz push NuGet
description: Příkaz dotnet NuGet push odešle balíček na server a publikuje ho.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 1e7831de4c041591b3602e405418f89f1d1d27d1
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895460"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

## <a name="name"></a>Name

`dotnet nuget push`– Odešle balíček na server a publikuje ho.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a>Popis

`dotnet nuget push` Příkaz odešle balíček na server a publikuje ho. Příkaz push používá podrobnosti serveru a přihlašovacích údajů, které se našly v konfiguračním souboru NuGet systému nebo v řetězci konfiguračních souborů. Další informace o konfiguračních souborech najdete v tématu [Konfigurace chování NuGet](/nuget/consume-packages/configuring-nuget-behavior). Výchozí konfigurace NuGet se získá tak, že se načtou *%AppData%\NuGet\NuGet.config* (Windows) nebo *$Home/.local/share* (Linux/MacOS) a pak se načte jakákoli soubor *NuGet. config* nebo *. NuGet\NuGet.config* počínaje kořenovým adresářem jednotky a končí aktuálním adresářem.

Příkaz vloží existující balíček. Nevytváří balíček. K vytvoření balíčku použijte [`dotnet pack`](dotnet-pack.md).

## <a name="arguments"></a>Argumenty

- **`ROOT`**

  Určuje cestu k balíčku, který má být vložen.

## <a name="options"></a>Možnosti

- **`-d|--disable-buffering`**

  Zakáže ukládání do vyrovnávací paměti při doručování na server HTTP (S), aby se snížilo využití paměti.

- **`--force-english-output`**

  Vynutí spuštění aplikace s využitím neutrální jazykové verze založené na angličtině.

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--interactive`**

  Umožňuje příkazu blokovat a vyžadovat ruční akci pro operace, jako je ověřování. Možnost je k dispozici od verze .NET Core 2,2 SDK.

- **`-k|--api-key <API_KEY>`**

  Klíč rozhraní API pro server

- **`-n|--no-symbols`**

  Symboly nejsou nabízeny (i v případě, že jsou k dispozici).

- **`--no-service-endpoint`**

  Nepřipojí k zdrojové adrese URL rozhraní API/v2/Package. Možnost je k dispozici od verze .NET Core 2,1 SDK.

- **`-s|--source <SOURCE>`**

  Určuje adresu URL serveru. Tato možnost je povinná, pokud `DefaultPushSource` konfigurační hodnota není nastavená v konfiguračním souboru NuGet.

- **`--skip-duplicate`**

  Při nahrávání více balíčků na server HTTP (S) zachází s každou odpovědí na 409 konfliktů jako s upozorněním, aby bylo možné pokračovat v nabízení. K dispozici od verze .NET Core 3,1 SDK.

- **`-sk|--symbol-api-key <API_KEY>`**

  Klíč rozhraní API pro server symbolů.

- **`-ss|--symbol-source <SOURCE>`**

  Určuje adresu URL serveru symbolů.

- **`-t|--timeout <TIMEOUT>`**

  Určuje časový limit pro doručování na server během několika sekund. Výchozí hodnota je 300 sekund (5 minut). Zadáním hodnoty 0 (nula sekund) se použije výchozí hodnota.

## <a name="examples"></a>Příklady

- Vložení *foo. nupkg* na výchozí zdroj nabízených oznámení a zadání klíče rozhraní API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- Vložení *foo. nupkg* do oficiálního serveru NuGet a zadání klíče rozhraní API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * Vložení *foo. nupkg* do vlastního zdroje `https://customsource`nabízených oznámení zadání klíče rozhraní API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- Vložení *foo. nupkg* na výchozí zdroj nabízených oznámení:

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- Vložení *foo. Symbols. nupkg* do výchozího zdroje symbolů:

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- Vložení *foo. nupkg* na výchozí zdroj nabízených oznámení a zadání časového limitu 360 sekund:

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- Nahrajte všechny soubory *. nupkg* v aktuálním adresáři do výchozího zdroje nabízených oznámení:

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > Pokud tento příkaz nefunguje, může to být způsobeno chybou, která existovala ve starších verzích sady SDK (.NET Core 2,1 SDK a starších verzích).
  > Pokud to chcete opravit, upgradujte verzi sady SDK nebo spusťte následující příkaz:`dotnet nuget push **/*.nupkg`

- Nahrajte všechny soubory *. nupkg* i v případě, že server http (S) vrátí odpověď na konflikt 409:

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```

- Nahrajte všechny soubory *. nupkg* v aktuálním adresáři do místního adresáře informačního kanálu:

  ```dotnetcli
  dotnet nuget push *.nupkg -s c:\mydir
  ```

  Tento příkaz neukládá balíčky do hierarchické struktury složek, což se doporučuje pro optimalizaci výkonu. Další informace najdete v tématu [místní informační kanály](/nuget/hosting-packages/local-feeds).  
