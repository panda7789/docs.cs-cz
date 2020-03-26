---
title: Dotnet nuget zdroj aktualizace příkaz
description: Dotnet nuget update source command updates a existing source in your NuGet configuration files.
ms.date: 03/20/2020
ms.openlocfilehash: 38335e07f91850756c7671413e1193c2578e7e7e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148545"
---
# <a name="dotnet-nuget-update-source"></a>Zdroj aktualizace dotnet nuget

**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet nuget update source`- Aktualizace nuget zdroj.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet nuget update source <NAME> [--source] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget update source [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget update source` aktualizuje existující zdroj v konfiguračních souborech NuGet.

## <a name="arguments"></a>Argumenty

- **`NAME`**

  Název zdroje.

## <a name="options"></a>Možnosti

- **`--configfile`**

  Konfigurační soubor NuGet. Pokud je zadán, budou použita pouze nastavení z tohoto souboru. Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře. Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`-p|--password`**

  Heslo, které se má použít při připojování k ověřenému zdroji.

- **`-s|--source`**

  Cesta ke zdroji balíčku.

- **`--store-password-in-clear-text`**

  Umožňuje ukládání pověření zdroje přenosných balíčků zakázáním šifrování hesel.

- **`-u|--username`**

  Uživatelské jméno, které má být použito při připojování k ověřenému zdroji.

- **`--valid-authentication-types`**

  Seznam platných typů ověřování pro tento zdroj oddělený čárkou. Nastavte tuto `basic` možnost na, pokud server inzeruje NTLM nebo Negotiate a vaše přihlašovací údaje musí být odeslány pomocí základnímechanismus, například při použití PAT s místní Azure DevOps Server. Mezi další `negotiate`platné `kerberos` `ntlm`hodnoty `digest`patří , , a , ale tyto hodnoty pravděpodobně nebudou užitečné.

## <a name="examples"></a>Příklady

- Aktualizace zdroje s `mySource`názvem :

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>Viz také

- [Zdrojové oddíly balíčku v souborech NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [příkaz zdroje (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
