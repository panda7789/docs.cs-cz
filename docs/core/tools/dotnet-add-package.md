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
# <a name="dotnet-add-package"></a><span data-ttu-id="d67d1-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="d67d1-103">dotnet add package</span></span>

<span data-ttu-id="d67d1-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="d67d1-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d67d1-105">Name</span><span class="sxs-lookup"><span data-stu-id="d67d1-105">Name</span></span>

<span data-ttu-id="d67d1-106">`dotnet add package`-Přidá odkaz na balíček do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d67d1-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d67d1-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d67d1-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="d67d1-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d67d1-108">Description</span></span>

<span data-ttu-id="d67d1-109">`dotnet add package`Příkaz nabízí pohodlný možnost Přidat odkaz na balíček do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d67d1-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="d67d1-110">Po spuštění příkazu je k dispozici kontrola kompatibility, aby bylo zajištěno, že balíček je kompatibilní s rozhraními v projektu.</span><span class="sxs-lookup"><span data-stu-id="d67d1-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="d67d1-111">Pokud se tato kontrolu projde, do `<PackageReference>` souboru projektu se přidá element a [dotnet Restore](dotnet-restore.md) se spustí.</span><span class="sxs-lookup"><span data-stu-id="d67d1-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="d67d1-112">Například přidání `Newtonsoft.Json` do *todo. csproj* vytvoří výstup podobný následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="d67d1-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="d67d1-113">Soubor *todo. csproj* nyní obsahuje [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element pro odkazovaný balíček.</span><span class="sxs-lookup"><span data-stu-id="d67d1-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a><span data-ttu-id="d67d1-114">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="d67d1-114">Implicit restore</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="d67d1-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d67d1-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="d67d1-116">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="d67d1-116">Specifies the project file.</span></span> <span data-ttu-id="d67d1-117">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="d67d1-117">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="d67d1-118">Odkaz na balíček, který se má přidat</span><span class="sxs-lookup"><span data-stu-id="d67d1-118">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="d67d1-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d67d1-119">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d67d1-120">Přidá odkaz na balíček pouze v případě cílení na konkrétní [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d67d1-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="d67d1-121">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="d67d1-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="d67d1-122">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="d67d1-122">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="d67d1-123">K dispozici od verze .NET Core 2,1 SDK, verze 2.1.400 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="d67d1-123">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="d67d1-124">Přidá odkaz na balíček, aniž by bylo nutné provést obnovení ve verzi Preview a kontrolu kompatibility.</span><span class="sxs-lookup"><span data-stu-id="d67d1-124">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="d67d1-125">Adresář, do kterého se mají balíčky obnovit</span><span class="sxs-lookup"><span data-stu-id="d67d1-125">The directory where to restore the packages.</span></span> <span data-ttu-id="d67d1-126">Výchozí umístění pro obnovení balíčků je `%userprofile%\.nuget\packages` ve Windows a `~/.nuget/packages` na MacOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="d67d1-126">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="d67d1-127">Další informace najdete v tématu [Správa globálních balíčků, mezipaměti a dočasných složek v NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="d67d1-127">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="d67d1-128">Identifikátor URI zdroje balíčku NuGet, který má být použit během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="d67d1-128">The URI of the NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="d67d1-129">Verze balíčku</span><span class="sxs-lookup"><span data-stu-id="d67d1-129">Version of the package.</span></span> <span data-ttu-id="d67d1-130">Viz [Správa verzí balíčku NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="d67d1-130">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="d67d1-131">Příklady</span><span class="sxs-lookup"><span data-stu-id="d67d1-131">Examples</span></span>

- <span data-ttu-id="d67d1-132">Přidat `Newtonsoft.Json` balíček NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="d67d1-132">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="d67d1-133">Přidat konkrétní verzi balíčku do projektu:</span><span class="sxs-lookup"><span data-stu-id="d67d1-133">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="d67d1-134">Přidat balíček pomocí konkrétního zdroje NuGet:</span><span class="sxs-lookup"><span data-stu-id="d67d1-134">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="d67d1-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="d67d1-135">See also</span></span>

- [<span data-ttu-id="d67d1-136">Správa globálních balíčků, mezipaměti a dočasných složek v NuGetu</span><span class="sxs-lookup"><span data-stu-id="d67d1-136">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="d67d1-137">Správa verzí balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="d67d1-137">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
