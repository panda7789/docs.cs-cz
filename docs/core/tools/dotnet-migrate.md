---
title: DotNet migrate příkaz
description: Dotnet migrate příkaz migruje projektu a všechny jeho závislosti.
ms.date: 05/25/2018
ms.openlocfilehash: 73e0169e64be4b55e10127ecca0101885061767e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665023"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="52138-103">DotNet migrate</span><span class="sxs-lookup"><span data-stu-id="52138-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="52138-104">Název</span><span class="sxs-lookup"><span data-stu-id="52138-104">Name</span></span>

<span data-ttu-id="52138-105">`dotnet migrate` -Migruje projektu .NET Core 2 ve verzi Preview do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="52138-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="52138-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="52138-106">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="52138-107">Popis</span><span class="sxs-lookup"><span data-stu-id="52138-107">Description</span></span>

<span data-ttu-id="52138-108">`dotnet migrate` Příkaz migraci platné ve verzi Preview 2 *project.json*– na základě projektu platný .NET Core SDK 1.0 *csproj* projektu.</span><span class="sxs-lookup"><span data-stu-id="52138-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span>

<span data-ttu-id="52138-109">Ve výchozím nastavení příkaz migruje kořenového projektu a všechny odkazy projektu, které obsahuje projekt kořenové.</span><span class="sxs-lookup"><span data-stu-id="52138-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="52138-110">Toto chování je zakázáno použití `--skip-project-references` možnost za běhu.</span><span class="sxs-lookup"><span data-stu-id="52138-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="52138-111">Migrace lze provést na následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="52138-111">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="52138-112">Zadáním jednoho projektu *project.json* souboru migrace.</span><span class="sxs-lookup"><span data-stu-id="52138-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="52138-113">Všechny adresáře určené v *global.json* předáním cesty k souboru *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="52138-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="52138-114">A *solution.sln* souboru, kde migruje projekty odkazované v řešení.</span><span class="sxs-lookup"><span data-stu-id="52138-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="52138-115">Na všechny podadresáře rekurzivně zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="52138-115">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="52138-116">`dotnet migrate` Příkaz udržuje migrovaných *project.json* soubor uvnitř `backup` adresáře, který vytvoří, pokud adresář neexistuje.</span><span class="sxs-lookup"><span data-stu-id="52138-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="52138-117">Toto chování je přepsat pomocí `--skip-backup` možnost.</span><span class="sxs-lookup"><span data-stu-id="52138-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="52138-118">Ve výchozím nastavení vypíše operace migrace stavu procesu migrace do standardního výstupního (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="52138-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="52138-119">Pokud používáte `--report-file <REPORT_FILE>` možnost, výstup bude uložen do souboru zadejte.</span><span class="sxs-lookup"><span data-stu-id="52138-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="52138-120">`dotnet migrate` Platné ve verzi Preview 2 podporuje pouze příkaz *project.json*-projektů založených na.</span><span class="sxs-lookup"><span data-stu-id="52138-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="52138-121">To znamená, že je nelze použít k migraci DNX nebo ve verzi Preview 1 *project.json*– na základě projekty přímo do projektů MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="52138-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="52138-122">Nejdřív musíte ručně provést migraci projekt na verzi Preview 2 *project.json*– na základě projektu a pak `dotnet migrate` příkaz chcete projekt migrovat.</span><span class="sxs-lookup"><span data-stu-id="52138-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="52138-123">Arguments</span><span class="sxs-lookup"><span data-stu-id="52138-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="52138-124">Cesta k jednomu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="52138-124">The path to one of the following:</span></span>

* <span data-ttu-id="52138-125">*project.json* souboru migrace.</span><span class="sxs-lookup"><span data-stu-id="52138-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="52138-126">*global.json* souboru: složky zadané v *global.json* se migrují.</span><span class="sxs-lookup"><span data-stu-id="52138-126">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="52138-127">*solution.sln* souboru: projekty odkazované v řešení se migrují.</span><span class="sxs-lookup"><span data-stu-id="52138-127">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="52138-128">adresář pro migraci: rekurzivně vyhledává *project.json* soubory určené k migraci do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="52138-128">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="52138-129">Výchozí hodnota je do aktuálního adresáře, pokud není zadáno žádné umístění.</span><span class="sxs-lookup"><span data-stu-id="52138-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="52138-130">Možnosti</span><span class="sxs-lookup"><span data-stu-id="52138-130">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="52138-131">Výstup souboru sestavy migrace jako JSON a nikoli uživatele zprávy.</span><span class="sxs-lookup"><span data-stu-id="52138-131">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="52138-132">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="52138-132">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="52138-133">Sestava migrace výstup do souboru kromě konzole.</span><span class="sxs-lookup"><span data-stu-id="52138-133">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="52138-134">Přeskočit migrace projekt odkazuje.</span><span class="sxs-lookup"><span data-stu-id="52138-134">Skip migrating project references.</span></span> <span data-ttu-id="52138-135">Ve výchozím nastavení odkazy na projekt jsou migrované rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="52138-135">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="52138-136">Přeskočit přesun *project.json*, *global.json*, a  *\*xproj* k `backup` adresáře po úspěšné migraci.</span><span class="sxs-lookup"><span data-stu-id="52138-136">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="52138-137">Soubor csproj šablonu chcete použít pro migraci.</span><span class="sxs-lookup"><span data-stu-id="52138-137">Template csproj file to use for migration.</span></span> <span data-ttu-id="52138-138">Ve výchozím nastavení, stejné šablony jako zrušených správcem `dotnet new console` se používá.</span><span class="sxs-lookup"><span data-stu-id="52138-138">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="52138-139">Verze balíčku sady sdk, na který odkazuje migrované aplikace.</span><span class="sxs-lookup"><span data-stu-id="52138-139">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="52138-140">Výchozí hodnota je verze sady SDK v `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="52138-140">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="52138-141">Cesta k souboru xproj používat.</span><span class="sxs-lookup"><span data-stu-id="52138-141">The path to the xproj file to use.</span></span> <span data-ttu-id="52138-142">Povinné, když je více než jeden xproj v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="52138-142">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="52138-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="52138-143">Examples</span></span>

<span data-ttu-id="52138-144">Migrate projekt v aktuálním adresáři a všechny jeho závislosti projektu na projekt:</span><span class="sxs-lookup"><span data-stu-id="52138-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="52138-145">Migrovat všechny projekty, které *global.json* soubor obsahuje:</span><span class="sxs-lookup"><span data-stu-id="52138-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="52138-146">Migrujte pouze pro aktuální projekt a nemá žádné závislosti projektu na projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="52138-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="52138-147">Také použijte konkrétní verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="52138-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`