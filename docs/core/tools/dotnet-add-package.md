---
title: "příkaz balíček - .NET Core rozhraní příkazového řádku přidejte DotNet."
description: "Příkaz 'dotnet. Přidejte balíček' poskytuje vhodnou možnost Přidat odkaz na balíček NuGet do projektu."
author: mairaw
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 7518ec32d669e64d713e77f687d285279b012967
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-add-package"></a>Přidejte balíček DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet add package`-Přidá balíček odkaz na soubor projektu.

## <a name="synopsis"></a>Stručný obsah

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]`

## <a name="description"></a>Popis

`dotnet add package` Příkaz poskytuje vhodnou možnost Přidat balíček odkaz na soubor projektu. Po spuštění příkazu, je kontrola kompatibility zajistěte, aby byl že tento balíček je kompatibilní s rozhraní v projektu. Pokud je kontrola úspěšně projde, `<PackageReference>` prvek přidán na soubor projektu a [dotnet obnovení](dotnet-restore.md) běží.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Například přidání `Newtonsoft.Json` k *ToDo.csproj* výstup v následujícím příkladu:

```
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

`-v|--version <VERSION>`

Verze balíčku.

`-f|--framework <FRAMEWORK>`

Přidá odkaz na balíček jenom při cílení na konkrétní [framework](../../standard/frameworks.md).

`-n|--no-restore`

Přidá odkaz na balíček bez provedení kontroly obnovení preview a kompatibility.

`-s|--source <SOURCE>`

Během operace obnovení používá konkrétního zdroje balíčku NuGet.

`--package-directory <PACKAGE_DIRECTORY>`

Obnoví balíček do zadaného adresáře.

## <a name="examples"></a>Příklady

Přidat `Newtonsoft.Json` balíček NuGet do projektu:

`dotnet add package Newtonsoft.Json`

Přidání na konkrétní verzi balíčku do projektu:

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

Přidání balíčku pomocí konkrétního zdroje NuGet:

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
