---
title: dotnet nuget zdroj seznamu, příkaz
description: Dotnet nuget seznam zdroj příkaz uvede všechny existující zdroje z konfiguračních souborů NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 8b14413949bd60ddeed977d19eec9bb99982da70
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463539"
---
# <a name="dotnet-nuget-list-source"></a>dotnet nuget list source

**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze

## <a name="name"></a>Název

`dotnet nuget list source`- Zobrazí seznam všech nakonfigurovaných zdrojů NuGet.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget list source` obsahuje seznam všech existujících zdrojů z konfiguračních souborů NuGet.

## <a name="options"></a>Možnosti

- **`--configfile <FILE>`**

  Konfigurační soubor NuGet. Pokud je zadán, budou použita pouze nastavení z tohoto souboru. Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře. Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`--format [Detailed|Short]`**

  Formát výstupu příkazu seznamu: `Detailed` (výchozí) `Short`a .

## <a name="examples"></a>Příklady

- Seznam nakonfigurovaných zdrojů z aktuálního adresáře:

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>Viz také

- [Zdrojové oddíly balíčku v souborech NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [příkaz zdroje (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
