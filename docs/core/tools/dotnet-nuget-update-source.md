---
title: Dotnet nuget zdroj aktualizace příkaz
description: Dotnet nuget update source command updates a existing source in your NuGet configuration files.
ms.date: 03/20/2020
ms.openlocfilehash: 42b1aec95cdd57e53f966400f6692a3d0150c16c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463481"
---
# <a name="dotnet-nuget-update-source"></a>dotnet nuget update source

**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze

## <a name="name"></a>Název

`dotnet nuget update source`- Aktualizace nuget zdroj.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget update source` aktualizuje existující zdroj v konfiguračních souborech NuGet.

## <a name="arguments"></a>Argumenty

- **`NAME`**

  Název zdroje.

## <a name="options"></a>Možnosti

- **`--configfile <FILE>`**

  Konfigurační soubor NuGet. Pokud je zadán, budou použita pouze nastavení z tohoto souboru. Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře. Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`-p|--password <PASSWORD>`**

  Heslo, které se má použít při připojování k ověřenému zdroji.

- **`-s|--source <SOURCE>`**

  Cesta ke zdroji balíčku.

- **`--store-password-in-clear-text`**

  Umožňuje ukládání pověření zdroje přenosných balíčků zakázáním šifrování hesel.

- **`-u|--username <USER>`**

  Uživatelské jméno, které má být použito při připojování k ověřenému zdroji.

- **`--valid-authentication-types <TYPES>`**

  Seznam platných typů ověřování pro tento zdroj oddělený čárkou. Nastavte tuto `basic` možnost na, pokud server inzeruje NTLM nebo Negotiate a vaše přihlašovací údaje musí být odeslány pomocí základnímechanismus, například při použití PAT s místní Azure DevOps Server. Mezi další `negotiate`platné `kerberos` `ntlm`hodnoty `digest`patří , , a , ale tyto hodnoty pravděpodobně nebudou užitečné.

## <a name="examples"></a>Příklady

- Aktualizace zdroje s `mySource`názvem :

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>Viz také

- [Zdrojové oddíly balíčku v souborech NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [příkaz zdroje (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
