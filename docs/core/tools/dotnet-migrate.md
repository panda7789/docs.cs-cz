---
title: dotnet migrate, příkaz
description: Příkaz migrace dotnet migruje projekt a všechny jeho závislosti.
ms.date: 02/14/2020
ms.openlocfilehash: 71f587c1bfadd445aca818448bdd5f136f009fe0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463640"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="71233-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="71233-103">dotnet migrate</span></span>

<span data-ttu-id="71233-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="71233-104">**This article applies to:** ✔️ .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="71233-105">Název</span><span class="sxs-lookup"><span data-stu-id="71233-105">Name</span></span>

<span data-ttu-id="71233-106">`dotnet migrate`- Migruje projekt Preview 2 .NET Core do projektu ve stylu sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="71233-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="71233-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="71233-107">Synopsis</span></span>

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json <REPORT_FILE>]
    [-r|--report-file <REPORT_FILE>] [-s|--skip-project-references [Debug|Release]]
    [--skip-backup] [-t|--template-file <TEMPLATE_FILE>] [-v|--sdk-package-version]
    [-x|--xproj-file]

dotnet migrate -h|--help
```

## <a name="description"></a><span data-ttu-id="71233-108">Popis</span><span class="sxs-lookup"><span data-stu-id="71233-108">Description</span></span>

<span data-ttu-id="71233-109">Tento příkaz je zastaralé.</span><span class="sxs-lookup"><span data-stu-id="71233-109">This command is deprecated.</span></span> <span data-ttu-id="71233-110">Příkaz `dotnet migrate` již není k dispozici počínaje sadou .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="71233-110">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span> <span data-ttu-id="71233-111">Může migrovat pouze projekt Preview 2 .NET Core do projektu 1.x .NET Core, který je mimo podporu.</span><span class="sxs-lookup"><span data-stu-id="71233-111">It can only migrate a Preview 2 .NET Core project to a 1.x .NET Core project, which is out of support.</span></span>

<span data-ttu-id="71233-112">Ve výchozím nastavení příkaz migruje kořenový projekt a všechny odkazy na projekt, které kořenový projekt obsahuje.</span><span class="sxs-lookup"><span data-stu-id="71233-112">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="71233-113">Toto chování je `--skip-project-references` zakázáno pomocí možnosti za běhu.</span><span class="sxs-lookup"><span data-stu-id="71233-113">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="71233-114">Migraci lze provést u následujících prostředků:</span><span class="sxs-lookup"><span data-stu-id="71233-114">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="71233-115">Jeden projekt zadáním souboru *project.json* k migraci.</span><span class="sxs-lookup"><span data-stu-id="71233-115">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="71233-116">Všechny adresáře zadané v souboru *global.json* předáním v cestě k souboru *global.json.*</span><span class="sxs-lookup"><span data-stu-id="71233-116">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="71233-117">Soubor *solution.sln,* kde migruje projekty odkazované v řešení.</span><span class="sxs-lookup"><span data-stu-id="71233-117">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="71233-118">Ve všech podadresářích daného adresáře rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="71233-118">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="71233-119">Příkaz `dotnet migrate` uchovává migrovaný soubor *project.json* uvnitř `backup` adresáře, který vytvoří, pokud adresář neexistuje.</span><span class="sxs-lookup"><span data-stu-id="71233-119">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="71233-120">Toto chování je `--skip-backup` přepsáno pomocí možnosti.</span><span class="sxs-lookup"><span data-stu-id="71233-120">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="71233-121">Ve výchozím nastavení operace migrace vypisuje stav procesu migrace na standardní výstup (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="71233-121">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="71233-122">Pokud použijete `--report-file <REPORT_FILE>` tuto možnost, výstup se uloží do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="71233-122">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="71233-123">Příkaz `dotnet migrate` podporuje pouze platné projekty založené na *projektu.json*preview 2.</span><span class="sxs-lookup"><span data-stu-id="71233-123">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="71233-124">To znamená, že jej nelze použít k migraci projektů založených na *projektu*DNX nebo Preview 1 přímo do projektů MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="71233-124">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="71233-125">Nejprve je třeba ručně migrovat projekt do projektu.json verze `dotnet migrate` Preview 2 a potom pomocí příkazu k migraci projektu. *project.json*</span><span class="sxs-lookup"><span data-stu-id="71233-125">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="71233-126">Argumenty</span><span class="sxs-lookup"><span data-stu-id="71233-126">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="71233-127">Cesta k jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="71233-127">The path to one of the following:</span></span>

* <span data-ttu-id="71233-128">soubor *u množení.*</span><span class="sxs-lookup"><span data-stu-id="71233-128">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="71233-129">*global.json* soubor: složky zadané v *global.json* jsou migrovány.</span><span class="sxs-lookup"><span data-stu-id="71233-129">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="71233-130">soubor *solution.sln:* projekty odkazované v řešení jsou migrovány.</span><span class="sxs-lookup"><span data-stu-id="71233-130">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="71233-131">adresář pro migraci: rekurzivně vyhledá soubory *project.json,* které mají být migrovány uvnitř zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="71233-131">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="71233-132">Pokud není nic zadáno, výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="71233-132">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="71233-133">Možnosti</span><span class="sxs-lookup"><span data-stu-id="71233-133">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="71233-134">Výstupní migrace soubor sestavy jako JSON spíše než uživatelské zprávy.</span><span class="sxs-lookup"><span data-stu-id="71233-134">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="71233-135">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="71233-135">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="71233-136">Výstupní zpráva o migraci do souboru kromě konzoly.</span><span class="sxs-lookup"><span data-stu-id="71233-136">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="71233-137">Přeskočení migrace odkazů na projekt</span><span class="sxs-lookup"><span data-stu-id="71233-137">Skip migrating project references.</span></span> <span data-ttu-id="71233-138">Ve výchozím nastavení jsou odkazy na projekt migrovány rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="71233-138">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="71233-139">Po úspěšné migraci přeskočte `backup` přesunutí *souboru project.json*, *global.json*a \* \*.xproj\* do adresáře.</span><span class="sxs-lookup"><span data-stu-id="71233-139">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="71233-140">Šablona csproj soubor pro migraci.</span><span class="sxs-lookup"><span data-stu-id="71233-140">Template csproj file to use for migration.</span></span> <span data-ttu-id="71233-141">Ve výchozím nastavení se používá stejná šablona, kterou jste upustili. `dotnet new console`</span><span class="sxs-lookup"><span data-stu-id="71233-141">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="71233-142">Verze balíčku sady SDK, na kterou odkazuje migrovaná aplikace.</span><span class="sxs-lookup"><span data-stu-id="71233-142">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="71233-143">Výchozí je verze sady SDK `dotnet new`v .</span><span class="sxs-lookup"><span data-stu-id="71233-143">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="71233-144">Cesta k souboru xproj, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="71233-144">The path to the xproj file to use.</span></span> <span data-ttu-id="71233-145">Povinné v případě, že je více než jeden xproj v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="71233-145">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="71233-146">Příklady</span><span class="sxs-lookup"><span data-stu-id="71233-146">Examples</span></span>

<span data-ttu-id="71233-147">Migrujte projekt v aktuálním adresáři a všechny jeho závislosti mezi projekty:</span><span class="sxs-lookup"><span data-stu-id="71233-147">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="71233-148">Migrace všech projektů, které soubor *global.json* obsahuje:</span><span class="sxs-lookup"><span data-stu-id="71233-148">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="71233-149">Migrujte pouze aktuální projekt a žádné závislosti projektu k projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="71233-149">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="71233-150">Použijte také konkrétní verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="71233-150">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
