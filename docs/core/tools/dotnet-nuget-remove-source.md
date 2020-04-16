---
title: dotnet nuget odebrat zdroj ový příkaz
description: Dotnet nuget odebrat zdroj příkaz odebere existující zdroj z konfiguračních souborů NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: b259873e1885644b272136fa31414410bdfd9f27
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463494"
---
# <a name="dotnet-nuget-remove-source"></a>dotnet nuget remove source

**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze

## <a name="name"></a>Název

`dotnet nuget remove source`- Odeberte zdroj NuGet.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet nuget remove source <NAME> [--configfile <FILE>]

dotnet nuget remove source -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget remove source` odebere existující zdroj z konfiguračních souborů NuGet.

## <a name="arguments"></a>Argumenty

- **`NAME`**

  Název zdroje.

## <a name="options"></a>Možnosti

- **`--configfile`**

  Konfigurační soubor NuGet. Pokud je zadán, budou použita pouze nastavení z tohoto souboru. Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře. Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Příklady

- Odebrání zdroje s `mySource`názvem :

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a>Viz také

- [Zdrojové oddíly balíčku v souborech NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [příkaz zdroje (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
