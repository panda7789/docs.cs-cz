---
title: příkaz balíček - .NET Core rozhraní příkazového řádku přidejte DotNet.
description: Příkaz 'dotnet. Přidejte balíček' poskytuje vhodnou možnost Přidat odkaz na balíček NuGet do projektu.
author: mairaw
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 3a8752ff83e069d21ebbda346efef34b17360e3b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-add-package"></a><span data-ttu-id="969aa-103">Přidejte balíček DotNet.</span><span class="sxs-lookup"><span data-stu-id="969aa-103">dotnet add package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="969aa-104">Název</span><span class="sxs-lookup"><span data-stu-id="969aa-104">Name</span></span>

<span data-ttu-id="969aa-105">`dotnet add package` -Přidá balíček odkaz na soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="969aa-105">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="969aa-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="969aa-106">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]`

## <a name="description"></a><span data-ttu-id="969aa-107">Popis</span><span class="sxs-lookup"><span data-stu-id="969aa-107">Description</span></span>

<span data-ttu-id="969aa-108">`dotnet add package` Příkaz poskytuje vhodnou možnost Přidat balíček odkaz na soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="969aa-108">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="969aa-109">Po spuštění příkazu, je kontrola kompatibility zajistěte, aby byl že tento balíček je kompatibilní s rozhraní v projektu.</span><span class="sxs-lookup"><span data-stu-id="969aa-109">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="969aa-110">Pokud je kontrola úspěšně projde, `<PackageReference>` prvek přidán na soubor projektu a [dotnet obnovení](dotnet-restore.md) běží.</span><span class="sxs-lookup"><span data-stu-id="969aa-110">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="969aa-111">Například přidání `Newtonsoft.Json` k *ToDo.csproj* výstup v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="969aa-111">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="969aa-112">*ToDo.csproj* soubor nyní obsahuje [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) element pro odkazovaný balíček.</span><span class="sxs-lookup"><span data-stu-id="969aa-112">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="969aa-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="969aa-113">Arguments</span></span>

`PROJECT`

<span data-ttu-id="969aa-114">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="969aa-114">Specifies the project file.</span></span> <span data-ttu-id="969aa-115">Pokud není zadaný, hledá příkaz aktuální adresář pro jednu.</span><span class="sxs-lookup"><span data-stu-id="969aa-115">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="969aa-116">Odkaz na balíček přidat.</span><span class="sxs-lookup"><span data-stu-id="969aa-116">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="969aa-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="969aa-117">Options</span></span>

`-h|--help`

<span data-ttu-id="969aa-118">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="969aa-118">Prints out a short help for the command.</span></span>

`-v|--version <VERSION>`

<span data-ttu-id="969aa-119">Verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="969aa-119">Version of the package.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="969aa-120">Přidá odkaz na balíček jenom při cílení na konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="969aa-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

`-n|--no-restore`

<span data-ttu-id="969aa-121">Přidá odkaz na balíček bez provedení kontroly obnovení preview a kompatibility.</span><span class="sxs-lookup"><span data-stu-id="969aa-121">Adds a package reference without performing a restore preview and compatibility check.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="969aa-122">Během operace obnovení používá konkrétního zdroje balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="969aa-122">Uses a specific NuGet package source during the restore operation.</span></span>

`--package-directory <PACKAGE_DIRECTORY>`

<span data-ttu-id="969aa-123">Obnoví balíček do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="969aa-123">Restores the package to the specified directory.</span></span>

## <a name="examples"></a><span data-ttu-id="969aa-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="969aa-124">Examples</span></span>

<span data-ttu-id="969aa-125">Přidat `Newtonsoft.Json` balíček NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="969aa-125">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

`dotnet add package Newtonsoft.Json`

<span data-ttu-id="969aa-126">Přidání na konkrétní verzi balíčku do projektu:</span><span class="sxs-lookup"><span data-stu-id="969aa-126">Add a specific version of a package to a project:</span></span>

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

<span data-ttu-id="969aa-127">Přidání balíčku pomocí konkrétního zdroje NuGet:</span><span class="sxs-lookup"><span data-stu-id="969aa-127">Add a package using a specific NuGet source:</span></span>

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
