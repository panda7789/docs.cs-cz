---
title: dotnet přidat balíček, příkaz
description: Příkaz "dotnet add package" poskytuje vhodnou možnost přidání odkazu na balíček NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 24a25cdab2aab30d52f8407adfda437f47437290
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463758"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Název

`dotnet add package`- Přidá odkaz na balíček do souboru projektu.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet add package` poskytuje vhodnou možnost přidání odkazu na balíček do souboru projektu. Po spuštění příkazu je kontrola kompatibility k zajištění balíček je kompatibilní s rámci v projektu. Pokud kontrola předá, `<PackageReference>` je do souboru projektu přidán prvek a je spuštěno obnovení [dotnet.](dotnet-restore.md)

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

Například přidání `Newtonsoft.Json` do *ToDo.csproj* vytváří výstup podobný následujícímu příkladu:

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

Soubor *ToDo.csproj* nyní [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) obsahuje prvek pro odkazovaný balíček.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a>Argumenty

- **`PROJECT`**

  Určuje soubor projektu. Pokud není zadán, příkaz prohledá aktuální adresář pro jeden.

- **`PACKAGE_NAME`**

  Odkaz na balíček přidat.

## <a name="options"></a>Možnosti

- **`-f|--framework <FRAMEWORK>`**

  Přidá odkaz na balíček pouze při cílení na konkrétní [rámec](../../standard/frameworks.md).

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--interactive`**

  Umožňuje příkazu zastavit a čekat na vstup nebo akci uživatele (například k dokončení ověřování). K dispozici od .NET Core 2.1 SDK, verze 2.1.400 nebo novější.

- **`-n|--no-restore`**

  Přidá odkaz na balíček bez provedení náhledu obnovení a kontroly kompatibility.

- **`--package-directory <PACKAGE_DIRECTORY>`**

  Adresář, kde chcete obnovit balíčky. Výchozí umístění obnovení `%userprofile%\.nuget\packages` balíčku je `~/.nuget/packages` v systému Windows a na macOS a Linuxu. Další informace naleznete [v tématu Správa globálních balíčků, mezipaměti a dočasných složek v NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).

- **`-s|--source <SOURCE>`**

  NuGet zdroj balíčku použít během operace obnovení.

- **`-v|--version <VERSION>`**

  Verze balíčku. Viz [NuGet balíček verze .](https://docs.microsoft.com/nuget/reference/package-versioning)

## <a name="examples"></a>Příklady

- Přidejte `Newtonsoft.Json` balíček NuGet do projektu:

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- Přidání konkrétní verze balíčku do projektu:

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- Přidejte balíček pomocí konkrétního zdroje NuGet:

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>Viz také

- [Správa globálních balíčků, mezipaměti a dočasných složek v NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [Správa verzí balíčku NuGet](https://docs.microsoft.com/nuget/reference/package-versioning)
