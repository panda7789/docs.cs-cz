---
title: příkaz DotNet add package příkaz – rozhraní příkazového řádku .NET Core
description: Příkaz "se příkaz dotnet add package" poskytuje vhodnou možnost Přidat odkaz na balíček NuGet do projektu.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 31dda9dbb101238b3a33d8b0d9a17765744480e0
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244390"
---
# <a name="dotnet-add-package"></a>příkaz DotNet add package

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet add package` -Přidá odkaz na balíček do souboru projektu.

## <a name="synopsis"></a>Souhrn

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>Popis

`dotnet add package` Příkaz poskytuje vhodnou možnost Přidat odkaz na balíček do souboru projektu. Po spuštění příkazu je kontrolu kompatibility a ujistěte se, že balíček je kompatibilní s architekturami, které v projektu. Pokud je kontrola proběhne úspěšně, `<PackageReference>` element je přidat do souboru projektu a [dotnet restore](dotnet-restore.md) běží.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Například přidáním `Newtonsoft.Json` k *ToDo.csproj* vytváří výstup podobný následujícímu příkladu:

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

*ToDo.csproj* nyní obsahuje soubor [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) – element pro odkazované balíčku.

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a>Arguments

`PROJECT`

Určuje soubor projektu. Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.

`PACKAGE_NAME`

Odkaz na balíček pro přidání.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-f|--framework <FRAMEWORK>`

Přidá odkaz na balíček pouze v případě cílení na konkrétní [framework](../../standard/frameworks.md).

`-n|--no-restore`

Přidá odkaz na balíček bez provedení kontroly obnovení ve verzi preview a kompatibility.

`--package-directory <PACKAGE_DIRECTORY>`

Obnoví balíčku do zadaného adresáře.

`-s|--source <SOURCE>`

Během operace obnovení používá konkrétní zdroj balíčku NuGet.

`-v|--version <VERSION>`

Verze balíčku.

## <a name="examples"></a>Příklady

Přidat `Newtonsoft.Json` balíček NuGet do projektu:

`dotnet add package Newtonsoft.Json`

Přidání konkrétní verzi balíčku do projektu:

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

Přidání balíčku pomocí konkrétního zdroje NuGet:

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
