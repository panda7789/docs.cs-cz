---
title: příkaz - .NET Core rozhraní příkazového řádku migrovat DotNet.
description: Migrace dotnet příkaz migruje projektu a všechny jeho závislé součásti.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 67a845f7604dededd00746fa6b74a320b3e134fa
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697102"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="a682f-103">migrace DotNet.</span><span class="sxs-lookup"><span data-stu-id="a682f-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a682f-104">Název</span><span class="sxs-lookup"><span data-stu-id="a682f-104">Name</span></span>

<span data-ttu-id="a682f-105">`dotnet migrate` -Migruje Preview 2 .NET Core projektu na .NET Core SDK 1.0 projekt.</span><span class="sxs-lookup"><span data-stu-id="a682f-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a682f-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="a682f-106">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="a682f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a682f-107">Description</span></span>

<span data-ttu-id="a682f-108">`dotnet migrate` Příkaz migruje platný Preview 2 *project.json*– na základě projekt, který má platný .NET Core SDK 1.0 *csproj* projektu.</span><span class="sxs-lookup"><span data-stu-id="a682f-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span>

<span data-ttu-id="a682f-109">Ve výchozím nastavení příkaz migruje kořenového projektu a všechny odkazy na projekt, které kořenové projekt obsahuje.</span><span class="sxs-lookup"><span data-stu-id="a682f-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="a682f-110">Toto chování je zakázat pomocí `--skip-project-references` možnost za běhu.</span><span class="sxs-lookup"><span data-stu-id="a682f-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="a682f-111">Migrace lze provést na následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="a682f-111">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="a682f-112">Jeden projekt tak, že zadáte *project.json* souboru migrace.</span><span class="sxs-lookup"><span data-stu-id="a682f-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="a682f-113">Všechny adresáře zadaný v *global.json* předáním cesty k souboru *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="a682f-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="a682f-114">A *solution.sln* souboru, kde se migruje projekty v řešení odkazuje.</span><span class="sxs-lookup"><span data-stu-id="a682f-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="a682f-115">Na všechny podadresáře rekurzivně zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="a682f-115">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="a682f-116">`dotnet migrate` Příkaz udržuje migrovaných *project.json* souboru uvnitř `backup` adresáři, který vytvoří, pokud adresář neexistuje.</span><span class="sxs-lookup"><span data-stu-id="a682f-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="a682f-117">Toto chování je přepsat pomocí `--skip-backup` možnost.</span><span class="sxs-lookup"><span data-stu-id="a682f-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="a682f-118">Ve výchozím nastavení výstupy operace migrace stavu procesu migrace do standardního výstupního (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="a682f-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="a682f-119">Pokud použijete `--report-file <REPORT_FILE>` možnost výstup bude uložen do souboru zadejte.</span><span class="sxs-lookup"><span data-stu-id="a682f-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="a682f-120">`dotnet migrate` Platný Preview 2 podporuje pouze příkaz *project.json*– projekty založené na.</span><span class="sxs-lookup"><span data-stu-id="a682f-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="a682f-121">To znamená, že je nemůžete použít k migraci DNX nebo Preview 1 *project.json*– projekty přímo do projektů MSBuild/csproj založené na.</span><span class="sxs-lookup"><span data-stu-id="a682f-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="a682f-122">Je nutné nejprve ručně migrovat projekt do Preview 2 *project.json*– na základě projektu a pak použít `dotnet migrate` k migraci projektu.</span><span class="sxs-lookup"><span data-stu-id="a682f-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="a682f-123">Arguments</span><span class="sxs-lookup"><span data-stu-id="a682f-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="a682f-124">Cesta k jednomu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="a682f-124">The path to one of the following:</span></span>

* <span data-ttu-id="a682f-125">*project.json* souboru migrace.</span><span class="sxs-lookup"><span data-stu-id="a682f-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="a682f-126">*global.json* souboru: složky specifikované v *global.json* se migrují.</span><span class="sxs-lookup"><span data-stu-id="a682f-126">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="a682f-127">*solution.sln* souboru: projekty v řešení odkazuje se migrují.</span><span class="sxs-lookup"><span data-stu-id="a682f-127">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="a682f-128">adresář pro migraci: rekurzivně prohledává pro *project.json* soubory určené k migraci uvnitř zadaný adresář.</span><span class="sxs-lookup"><span data-stu-id="a682f-128">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="a682f-129">Výchozí hodnota je aktuální adresář, pokud není zadáno žádné umístění.</span><span class="sxs-lookup"><span data-stu-id="a682f-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="a682f-130">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a682f-130">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="a682f-131">Soubor sestavy migrace výstup jako JSON, místo uživatelských zprávy.</span><span class="sxs-lookup"><span data-stu-id="a682f-131">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="a682f-132">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a682f-132">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="a682f-133">Sestavy migrace výstup do souboru kromě konzole.</span><span class="sxs-lookup"><span data-stu-id="a682f-133">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="a682f-134">Přeskočit migrace projekt odkazuje.</span><span class="sxs-lookup"><span data-stu-id="a682f-134">Skip migrating project references.</span></span> <span data-ttu-id="a682f-135">Ve výchozím nastavení jsou odkazy na projekt migrované rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="a682f-135">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="a682f-136">Přeskočit přesunutí *project.json*, *global.json*, a  *\*.xproj* k `backup` adresář po úspěšné migraci.</span><span class="sxs-lookup"><span data-stu-id="a682f-136">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="a682f-137">Soubor csproj šablonu použít pro migraci.</span><span class="sxs-lookup"><span data-stu-id="a682f-137">Template csproj file to use for migration.</span></span> <span data-ttu-id="a682f-138">Ve výchozím nastavení, stejné šablony jako ten, zrušených `dotnet new console` se používá.</span><span class="sxs-lookup"><span data-stu-id="a682f-138">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="a682f-139">Verze balíčku sdk, který se odkazuje v migrovanou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a682f-139">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="a682f-140">Výchozí hodnota je verze sady SDK v `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="a682f-140">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="a682f-141">Cesta k souboru xproj používat.</span><span class="sxs-lookup"><span data-stu-id="a682f-141">The path to the xproj file to use.</span></span> <span data-ttu-id="a682f-142">Vyžaduje, když je více než jeden xproj v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="a682f-142">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="a682f-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="a682f-143">Examples</span></span>

<span data-ttu-id="a682f-144">Migrace na projekt v aktuálním adresáři a všechny jeho závislosti projektu projektu:</span><span class="sxs-lookup"><span data-stu-id="a682f-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="a682f-145">Migrovat všechny projekty, které *global.json* soubor obsahuje:</span><span class="sxs-lookup"><span data-stu-id="a682f-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="a682f-146">Migrujte pouze aktuální projekt a nemá žádné závislosti projektu k projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="a682f-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="a682f-147">Také použijte konkrétní verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="a682f-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`