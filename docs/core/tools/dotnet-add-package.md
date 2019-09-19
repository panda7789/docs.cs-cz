---
title: dotnet – přidat balíček – příkaz
description: Příkaz dotnet Add Package nabízí pohodlný možnost přidat do projektu odkaz na balíček NuGet.
ms.date: 06/26/2019
ms.openlocfilehash: 9445cf686ec1733f5a8b3403b7efea3a544fbc99
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117790"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="eb4d4-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="eb4d4-103">dotnet add package</span></span>

<span data-ttu-id="eb4d4-104">**Tento článek se týká: ✓** .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="eb4d4-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="eb4d4-105">Name</span><span class="sxs-lookup"><span data-stu-id="eb4d4-105">Name</span></span>

<span data-ttu-id="eb4d4-106">`dotnet add package`-Přidá odkaz na balíček do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="eb4d4-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="eb4d4-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="eb4d4-108">Popis</span><span class="sxs-lookup"><span data-stu-id="eb4d4-108">Description</span></span>

<span data-ttu-id="eb4d4-109">`dotnet add package` Příkaz nabízí pohodlný možnost Přidat odkaz na balíček do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="eb4d4-110">Po spuštění příkazu je k dispozici kontrola kompatibility, aby bylo zajištěno, že balíček je kompatibilní s rozhraními v projektu.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="eb4d4-111">Pokud se tato kontrolu projde, `<PackageReference>` do souboru projektu se přidá element a [dotnet Restore](dotnet-restore.md) se spustí.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="eb4d4-112">Například přidání `Newtonsoft.Json` do *todo. csproj* vytvoří výstup podobný následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="eb4d4-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="eb4d4-113">Soubor *todo. csproj* nyní obsahuje [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element pro odkazovaný balíček.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="eb4d4-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="eb4d4-114">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="eb4d4-115">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-115">Specifies the project file.</span></span> <span data-ttu-id="eb4d4-116">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-116">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="eb4d4-117">Odkaz na balíček, který se má přidat</span><span class="sxs-lookup"><span data-stu-id="eb4d4-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="eb4d4-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="eb4d4-118">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="eb4d4-119">Přidá odkaz na balíček pouze v případě cílení na konkrétní [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="eb4d4-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="eb4d4-120">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-120">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="eb4d4-121">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="eb4d4-121">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="eb4d4-122">K dispozici od verze .NET Core 2,1 SDK, verze 2.1.400 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="eb4d4-123">Přidá odkaz na balíček, aniž by bylo nutné provést obnovení ve verzi Preview a kontrolu kompatibility.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="eb4d4-124">Adresář, do kterého se mají balíčky obnovit</span><span class="sxs-lookup"><span data-stu-id="eb4d4-124">The directory where to restore the packages.</span></span> <span data-ttu-id="eb4d4-125">Výchozí umístění pro obnovení balíčků je `%userprofile%\.nuget\packages` ve Windows a `~/.nuget/packages` na MacOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-125">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="eb4d4-126">Další informace najdete v tématu [Správa globálních balíčků, mezipaměti a dočasných složek v NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="eb4d4-126">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="eb4d4-127">Zdroj balíčku NuGet, který se má použít během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="eb4d4-127">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="eb4d4-128">Verze balíčku</span><span class="sxs-lookup"><span data-stu-id="eb4d4-128">Version of the package.</span></span> <span data-ttu-id="eb4d4-129">Viz [Správa verzí balíčku NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="eb4d4-129">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="eb4d4-130">Příklady</span><span class="sxs-lookup"><span data-stu-id="eb4d4-130">Examples</span></span>

- <span data-ttu-id="eb4d4-131">Přidat `Newtonsoft.Json` balíček NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="eb4d4-131">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="eb4d4-132">Přidat konkrétní verzi balíčku do projektu:</span><span class="sxs-lookup"><span data-stu-id="eb4d4-132">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="eb4d4-133">Přidat balíček pomocí konkrétního zdroje NuGet:</span><span class="sxs-lookup"><span data-stu-id="eb4d4-133">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="eb4d4-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb4d4-134">See also</span></span>

- [<span data-ttu-id="eb4d4-135">Správa globálních balíčků, mezipaměti a dočasných složek v NuGetu</span><span class="sxs-lookup"><span data-stu-id="eb4d4-135">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="eb4d4-136">Správa verzí balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="eb4d4-136">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
