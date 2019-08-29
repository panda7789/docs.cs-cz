---
title: dotnet – přidat balíček – příkaz
description: Příkaz dotnet Add Package nabízí pohodlný možnost přidat do projektu odkaz na balíček NuGet.
ms.date: 06/26/2019
ms.openlocfilehash: 124e42b1d5897802bb1698c8e22b7e76031391a2
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105167"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Tento článek se týká: ✓** .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet add package`-Přidá odkaz na balíček do souboru projektu.

## <a name="synopsis"></a>Stručný obsah

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>Popis

`dotnet add package` Příkaz nabízí pohodlný možnost Přidat odkaz na balíček do souboru projektu. Po spuštění příkazu je k dispozici kontrola kompatibility, aby bylo zajištěno, že balíček je kompatibilní s rozhraními v projektu. Pokud se tato kontrolu projde, `<PackageReference>` do souboru projektu se přidá element a [dotnet Restore](dotnet-restore.md) se spustí.

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

Například přidání `Newtonsoft.Json` do *todo. csproj* vytvoří výstup podobný následujícímu příkladu:

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
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

## <a name="arguments"></a>Arguments

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

  Zdroj balíčku NuGet, který se má použít během operace obnovení.

- **`-v|--version <VERSION>`**

  Verze balíčku Viz [Správa verzí balíčku NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).

## <a name="examples"></a>Příklady

- Přidat `Newtonsoft.Json` balíček NuGet do projektu:

  ```console
  dotnet add package Newtonsoft.Json
  ```

- Přidat konkrétní verzi balíčku do projektu:

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- Přidat balíček pomocí konkrétního zdroje NuGet:

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>Viz také:

- [Správa globálních balíčků, mezipaměti a dočasných složek v NuGetu](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [Správa verzí balíčků NuGet](https://docs.microsoft.com/nuget/reference/package-versioning)
