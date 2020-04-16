---
title: dotnet nuget přidat zdrojový příkaz
description: Dotnet nuget přidat zdrojový příkaz přidá nový zdroj balíčku do konfiguračních souborů NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 319501e026f1c3102006b0be5357f127b8e366a7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463593"
---
# <a name="dotnet-nuget-add-source"></a>dotnet nuget add source

**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze

## <a name="name"></a>Název

`dotnet nuget add source`- Přidejte zdroj NuGet.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget add source` přidá nový zdroj balíčku do konfiguračních souborů NuGet.

## <a name="arguments"></a>Argumenty

- **`PACKAGE_SOURCE_PATH`**

  Cesta ke zdroji balíčku.

## <a name="options"></a>Možnosti

- **`--configfile <FILE>`**

  Konfigurační soubor NuGet. Pokud je zadán, budou použita pouze nastavení z tohoto souboru. Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře. Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`-n|--name <SOURCE_NAME>`**

  Název zdroje.

- **`-p|--password <PASSWORD>`**

  Heslo, které se má použít při připojování k ověřenému zdroji.

- **`--store-password-in-clear-text`**

  Umožňuje ukládání pověření zdroje přenosných balíčků zakázáním šifrování hesel.

- **`-u|--username <USER>`**

  Uživatelské jméno, které má být použito při připojování k ověřenému zdroji.

- **`--valid-authentication-types <TYPES>`**

  Seznam platných typů ověřování pro tento zdroj oddělený čárkou. Nastavte tuto `basic` možnost na, pokud server inzeruje NTLM nebo Negotiate a vaše přihlašovací údaje musí být odeslány pomocí základnímechanismus, například při použití PAT s místní Azure DevOps Server. Mezi další `negotiate`platné `kerberos` `ntlm`hodnoty `digest`patří , , a , ale tyto hodnoty pravděpodobně nebudou užitečné.

## <a name="examples"></a>Příklady

- Přidat `nuget.org` jako zdroj:

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- Přidat `c:\packages` jako místní zdroj:

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- Přidejte zdroj, který vyžaduje ověření:

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- Přidejte zdroj, který potřebuje ověření (pak přejděte k instalaci zprostředkovatele pověření):

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>Viz také

- [Zdrojové oddíly balíčku v souborech NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [příkaz zdroje (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
