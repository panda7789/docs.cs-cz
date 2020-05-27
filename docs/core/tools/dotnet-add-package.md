---
title: dotnet – přidat balíček – příkaz
description: Příkaz dotnet Add Package nabízí pohodlný možnost přidat do projektu odkaz na balíček NuGet.
ms.date: 02/14/2020
ms.openlocfilehash: bc79fe8adf5f775ddce62f3877a8de945c6a18ab
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840894"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

## <a name="name"></a>Name

`dotnet add package`-Přidá odkaz na balíček do souboru projektu.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a>Popis

`dotnet add package`Příkaz nabízí pohodlný možnost Přidat odkaz na balíček do souboru projektu. Po spuštění příkazu je k dispozici kontrola kompatibility, aby bylo zajištěno, že balíček je kompatibilní s rozhraními v projektu. Pokud se tato kontrolu projde, do `<PackageReference>` souboru projektu se přidá element a [dotnet Restore](dotnet-restore.md) se spustí.

Například přidání `Newtonsoft.Json` do *todo. csproj* vytvoří výstup podobný následujícímu příkladu:

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

Soubor *todo. csproj* nyní obsahuje [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element pro odkazovaný balíček.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a>Implicitní obnovení

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Argumenty

- **`PROJECT`**

  Určuje soubor projektu. Pokud není zadán, příkaz vyhledá v aktuálním adresáři.

- **`PACKAGE_NAME`**

  Odkaz na balíček, který se má přidat

## <a name="options"></a>Možnosti

- **`-f|--framework <FRAMEWORK>`**

  Přidá odkaz na balíček pouze v případě cílení na konkrétní [rozhraní](../../standard/frameworks.md).

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--interactive`**

  Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování). K dispozici od verze .NET Core 2,1 SDK, verze 2.1.400 nebo novější.

- **`-n|--no-restore`**

  Přidá odkaz na balíček, aniž by bylo nutné provést obnovení ve verzi Preview a kontrolu kompatibility.

- **`--package-directory <PACKAGE_DIRECTORY>`**

  Adresář, do kterého se mají balíčky obnovit Výchozí umístění pro obnovení balíčků je `%userprofile%\.nuget\packages` ve Windows a `~/.nuget/packages` na MacOS a Linux. Další informace najdete v tématu [Správa globálních balíčků, mezipaměti a dočasných složek v NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).

- **`-s|--source <SOURCE>`**

  Identifikátor URI zdroje balíčku NuGet, který má být použit během operace obnovení.

- **`-v|--version <VERSION>`**

  Verze balíčku Viz [Správa verzí balíčku NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).

## <a name="examples"></a>Příklady

- Přidat `Newtonsoft.Json` balíček NuGet do projektu:

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- Přidat konkrétní verzi balíčku do projektu:

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- Přidat balíček pomocí konkrétního zdroje NuGet:

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>Viz také

- [Správa globálních balíčků, mezipaměti a dočasných složek v NuGetu](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [Správa verzí balíčků NuGet](https://docs.microsoft.com/nuget/reference/package-versioning)
