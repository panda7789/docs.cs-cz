---
title: dotnet nuget povolit zdrojový příkaz
description: Dotnet nuget povolit zdrojový příkaz umožňuje existující zdroj v konfiguračních souborech NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 38fb5917361bd7952fef9c31ed897fb81f005155
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463563"
---
# <a name="dotnet-nuget-enable-source"></a>dotnet nuget enable source

**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze

## <a name="name"></a>Název

`dotnet nuget enable source`- Povolte zdroj NuGet.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget enable source` povolí existující zdroj v konfiguračních souborech NuGet.

## <a name="arguments"></a>Argumenty

- **`NAME`**

  Název zdroje.

## <a name="options"></a>Možnosti

- **`--configfile <FILE>`**

  Konfigurační soubor NuGet. Pokud je zadán, budou použita pouze nastavení z tohoto souboru. Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře. Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Příklady

- Povolit zdroj s `mySource`názvem :

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a>Viz také

- [Zdrojové oddíly balíčku v souborech NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [příkaz zdroje (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
