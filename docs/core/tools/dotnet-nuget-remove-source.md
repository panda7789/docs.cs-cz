---
title: dotnet nuget odebrat zdroj ový příkaz
description: Dotnet nuget odebrat zdroj příkaz odebere existující zdroj z konfiguračních souborů NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 65c97b98ab50121fb4ebc184da65f021c16e0634
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148538"
---
# <a name="dotnet-nuget-remove-source"></a>dotnet nuget odebrat zdroj

**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet nuget remove source`- Odeberte zdroj NuGet.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet nuget remove source <NAME> [--configfile]
dotnet nuget remove source [-h|--help]
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
