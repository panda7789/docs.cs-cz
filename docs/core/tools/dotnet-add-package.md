---
title: příkaz DotNet add příkaz balíčku
description: Příkaz "se příkaz dotnet add package" poskytuje vhodnou možnost Přidat odkaz na balíček NuGet do projektu.
ms.date: 06/26/2019
ms.openlocfilehash: f387d32cbf706e1711439e393c1a7811bc8f47bd
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422051"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="6a687-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="6a687-103">dotnet add package</span></span>

<span data-ttu-id="6a687-104">**Tento článek se týká: ✓** .NET Core 1.x sady SDK a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="6a687-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="6a687-105">Name</span><span class="sxs-lookup"><span data-stu-id="6a687-105">Name</span></span>

<span data-ttu-id="6a687-106">`dotnet add package` -Přidá odkaz na balíček do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="6a687-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6a687-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="6a687-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="6a687-108">Popis</span><span class="sxs-lookup"><span data-stu-id="6a687-108">Description</span></span>

<span data-ttu-id="6a687-109">`dotnet add package` Příkaz poskytuje vhodnou možnost Přidat odkaz na balíček do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="6a687-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="6a687-110">Po spuštění příkazu je kontrolu kompatibility a ujistěte se, že balíček je kompatibilní s architekturami, které v projektu.</span><span class="sxs-lookup"><span data-stu-id="6a687-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="6a687-111">Pokud je kontrola proběhne úspěšně, `<PackageReference>` element je přidat do souboru projektu a [dotnet restore](dotnet-restore.md) běží.</span><span class="sxs-lookup"><span data-stu-id="6a687-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="6a687-112">Například přidáním `Newtonsoft.Json` k *ToDo.csproj* vytváří výstup podobný následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="6a687-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="6a687-113">*ToDo.csproj* nyní obsahuje soubor [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) – element pro odkazované balíčku.</span><span class="sxs-lookup"><span data-stu-id="6a687-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="6a687-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="6a687-114">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="6a687-115">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="6a687-115">Specifies the project file.</span></span> <span data-ttu-id="6a687-116">Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.</span><span class="sxs-lookup"><span data-stu-id="6a687-116">If not specified, the command searches the current directory for one.</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="6a687-117">Odkaz na balíček pro přidání.</span><span class="sxs-lookup"><span data-stu-id="6a687-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="6a687-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="6a687-118">Options</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6a687-119">Přidá odkaz na balíček pouze v případě cílení na konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6a687-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

* **`-h|--help`**

  <span data-ttu-id="6a687-120">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="6a687-120">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="6a687-121">Povoluje příkazu zastavit a počkat na vstup uživatele nebo akci (třeba k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="6a687-121">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="6a687-122">Dostupné od verze rozhraní .NET Core 2.1 SDK verze 2.1.400 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="6a687-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

* **`-n|--no-restore`**

  <span data-ttu-id="6a687-123">Přidá odkaz na balíček bez provedení kontroly obnovení ve verzi preview a kompatibility.</span><span class="sxs-lookup"><span data-stu-id="6a687-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

* **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="6a687-124">Adresář umístění, kam obnovit balíčky.</span><span class="sxs-lookup"><span data-stu-id="6a687-124">The directory where to restore the packages.</span></span> <span data-ttu-id="6a687-125">Výchozí umístění pro obnovení balíčků je `%userprofile%\.nuget\packages` na Windows a `~/.nuget/packages` v systémech macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="6a687-125">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="6a687-126">Další informace najdete v tématu [Správa globálních balíčků, mezipaměť a dočasné složky ve Správci NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="6a687-126">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="6a687-127">Zdroj balíčku NuGet pro použití během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="6a687-127">The NuGet package source to use during the restore operation.</span></span>

* **`-v|--version <VERSION>`**

  <span data-ttu-id="6a687-128">Verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="6a687-128">Version of the package.</span></span> <span data-ttu-id="6a687-129">Zobrazit [Správa verzí balíčků NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="6a687-129">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="6a687-130">Příklady</span><span class="sxs-lookup"><span data-stu-id="6a687-130">Examples</span></span>

* <span data-ttu-id="6a687-131">Přidat `Newtonsoft.Json` balíček NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="6a687-131">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```console
  dotnet add package Newtonsoft.Json
  ```

* <span data-ttu-id="6a687-132">Přidání konkrétní verzi balíčku do projektu:</span><span class="sxs-lookup"><span data-stu-id="6a687-132">Add a specific version of a package to a project:</span></span>

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

* <span data-ttu-id="6a687-133">Přidání balíčku pomocí konkrétního zdroje NuGet:</span><span class="sxs-lookup"><span data-stu-id="6a687-133">Add a package using a specific NuGet source:</span></span>

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="6a687-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a687-134">See also</span></span>

- [<span data-ttu-id="6a687-135">Správa globálních balíčků, mezipaměť a dočasné složky ve Správci NuGet</span><span class="sxs-lookup"><span data-stu-id="6a687-135">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="6a687-136">Správa verzí balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="6a687-136">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)