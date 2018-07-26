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
# <a name="dotnet-add-package"></a><span data-ttu-id="8b6ba-103">příkaz DotNet add package</span><span class="sxs-lookup"><span data-stu-id="8b6ba-103">dotnet add package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8b6ba-104">Název</span><span class="sxs-lookup"><span data-stu-id="8b6ba-104">Name</span></span>

<span data-ttu-id="8b6ba-105">`dotnet add package` -Přidá odkaz na balíček do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-105">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8b6ba-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="8b6ba-106">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="8b6ba-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8b6ba-107">Description</span></span>

<span data-ttu-id="8b6ba-108">`dotnet add package` Příkaz poskytuje vhodnou možnost Přidat odkaz na balíček do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-108">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="8b6ba-109">Po spuštění příkazu je kontrolu kompatibility a ujistěte se, že balíček je kompatibilní s architekturami, které v projektu.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-109">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="8b6ba-110">Pokud je kontrola proběhne úspěšně, `<PackageReference>` element je přidat do souboru projektu a [dotnet restore](dotnet-restore.md) běží.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-110">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="8b6ba-111">Například přidáním `Newtonsoft.Json` k *ToDo.csproj* vytváří výstup podobný následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="8b6ba-111">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="8b6ba-112">*ToDo.csproj* nyní obsahuje soubor [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) – element pro odkazované balíčku.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-112">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="8b6ba-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="8b6ba-113">Arguments</span></span>

`PROJECT`

<span data-ttu-id="8b6ba-114">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-114">Specifies the project file.</span></span> <span data-ttu-id="8b6ba-115">Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-115">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="8b6ba-116">Odkaz na balíček pro přidání.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-116">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="8b6ba-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="8b6ba-117">Options</span></span>

`-h|--help`

<span data-ttu-id="8b6ba-118">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-118">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="8b6ba-119">Přidá odkaz na balíček pouze v případě cílení na konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="8b6ba-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

`-n|--no-restore`

<span data-ttu-id="8b6ba-120">Přidá odkaz na balíček bez provedení kontroly obnovení ve verzi preview a kompatibility.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-120">Adds a package reference without performing a restore preview and compatibility check.</span></span>

`--package-directory <PACKAGE_DIRECTORY>`

<span data-ttu-id="8b6ba-121">Obnoví balíčku do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-121">Restores the package to the specified directory.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="8b6ba-122">Během operace obnovení používá konkrétní zdroj balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-122">Uses a specific NuGet package source during the restore operation.</span></span>

`-v|--version <VERSION>`

<span data-ttu-id="8b6ba-123">Verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="8b6ba-123">Version of the package.</span></span>

## <a name="examples"></a><span data-ttu-id="8b6ba-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="8b6ba-124">Examples</span></span>

<span data-ttu-id="8b6ba-125">Přidat `Newtonsoft.Json` balíček NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="8b6ba-125">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

`dotnet add package Newtonsoft.Json`

<span data-ttu-id="8b6ba-126">Přidání konkrétní verzi balíčku do projektu:</span><span class="sxs-lookup"><span data-stu-id="8b6ba-126">Add a specific version of a package to a project:</span></span>

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

<span data-ttu-id="8b6ba-127">Přidání balíčku pomocí konkrétního zdroje NuGet:</span><span class="sxs-lookup"><span data-stu-id="8b6ba-127">Add a package using a specific NuGet source:</span></span>

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
