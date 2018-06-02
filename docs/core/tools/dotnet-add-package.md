---
title: příkaz balíček - .NET Core rozhraní příkazového řádku přidejte DotNet.
description: Příkaz 'dotnet. Přidejte balíček' poskytuje vhodnou možnost Přidat odkaz na balíček NuGet do projektu.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 31dda9dbb101238b3a33d8b0d9a17765744480e0
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696296"
---
# <a name="dotnet-add-package"></a>Přidejte balíček DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet add package` -Přidá balíček odkaz na soubor projektu.

## <a name="synopsis"></a>Stručný obsah

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>Popis

`dotnet add package` Příkaz poskytuje vhodnou možnost Přidat balíček odkaz na soubor projektu. Po spuštění příkazu, je kontrola kompatibility zajistěte, aby byl že tento balíček je kompatibilní s rozhraní v projektu. Pokud je kontrola úspěšně projde, `<PackageReference>` prvek přidán na soubor projektu a [dotnet obnovení](dotnet-restore.md) běží.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Například přidání `Newtonsoft.Json` k *ToDo.csproj* výstup v následujícím příkladu:

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

*ToDo.csproj* soubor nyní obsahuje [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) element pro odkazovaný balíček.

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a>Arguments

`PROJECT`

Určuje soubor projektu. Pokud není zadaný, hledá příkaz aktuální adresář pro jednu.

`PACKAGE_NAME`

Odkaz na balíček přidat.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-f|--framework <FRAMEWORK>`

Přidá odkaz na balíček jenom při cílení na konkrétní [framework](../../standard/frameworks.md).

`-n|--no-restore`

Přidá odkaz na balíček bez provedení kontroly obnovení preview a kompatibility.

`--package-directory <PACKAGE_DIRECTORY>`

Obnoví balíček do zadaného adresáře.

`-s|--source <SOURCE>`

Během operace obnovení používá konkrétního zdroje balíčku NuGet.

`-v|--version <VERSION>`

Verze balíčku.

## <a name="examples"></a>Příklady

Přidat `Newtonsoft.Json` balíček NuGet do projektu:

`dotnet add package Newtonsoft.Json`

Přidání na konkrétní verzi balíčku do projektu:

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

Přidání balíčku pomocí konkrétního zdroje NuGet:

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
