---
title: dotnet – příkaz migrace
description: Příkaz dotnet migruje migruje projekt a všechny jeho závislosti.
ms.date: 02/14/2020
ms.openlocfilehash: 2e7f9ae5a1d11c54280d914b04df761f0d5aff99
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284089"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="3b9ff-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="3b9ff-103">dotnet migrate</span></span>

<span data-ttu-id="3b9ff-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK</span><span class="sxs-lookup"><span data-stu-id="3b9ff-104">**This article applies to:** ✔️ .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="3b9ff-105">Name</span><span class="sxs-lookup"><span data-stu-id="3b9ff-105">Name</span></span>

<span data-ttu-id="3b9ff-106">`dotnet migrate`– Migruje projekt .NET Core ve verzi Preview 2 na projekt ve stylu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3b9ff-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="3b9ff-107">Synopsis</span></span>

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json <REPORT_FILE>]
    [-r|--report-file <REPORT_FILE>] [-s|--skip-project-references [Debug|Release]]
    [--skip-backup] [-t|--template-file <TEMPLATE_FILE>] [-v|--sdk-package-version]
    [-x|--xproj-file]

dotnet migrate -h|--help
```

## <a name="description"></a><span data-ttu-id="3b9ff-108">Description</span><span class="sxs-lookup"><span data-stu-id="3b9ff-108">Description</span></span>

<span data-ttu-id="3b9ff-109">Tento příkaz je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-109">This command is deprecated.</span></span> <span data-ttu-id="3b9ff-110">`dotnet migrate`Příkaz již není od sady .NET Core 3,0 SDK k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-110">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span> <span data-ttu-id="3b9ff-111">Může migrovat pouze projekt verze Preview 2 .NET Core do projektu .NET Core s 1. x, který není podporován.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-111">It can only migrate a Preview 2 .NET Core project to a 1.x .NET Core project, which is out of support.</span></span>

<span data-ttu-id="3b9ff-112">Ve výchozím nastavení příkaz migruje kořenový projekt a všechny odkazy projektu, které obsahuje kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-112">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="3b9ff-113">Toto chování je zakázáno pomocí `--skip-project-references` Možnosti v době běhu.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-113">This behavior is disabled using the `--skip-project-references` option at run time.</span></span>

<span data-ttu-id="3b9ff-114">Migraci můžete provádět na těchto prostředcích:</span><span class="sxs-lookup"><span data-stu-id="3b9ff-114">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="3b9ff-115">Jeden projekt zadáním souboru *Project. JSON* , který se má migrovat.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-115">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="3b9ff-116">Všechny adresáře zadané v souboru *Global. JSON* předáním cesty k souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="3b9ff-116">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="3b9ff-117">Soubor *řešení. sln* , kde migruje projekty, na které je odkazováno v řešení.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-117">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="3b9ff-118">Ve všech podadresářích daného adresáře rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-118">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="3b9ff-119">`dotnet migrate`Příkaz udržuje migrovaný soubor *Project. JSON* v `backup` adresáři, který vytvoří, pokud adresář neexistuje.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-119">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="3b9ff-120">Toto chování je přepsáno pomocí `--skip-backup` Možnosti.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-120">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="3b9ff-121">Ve výchozím nastavení operace migrace vypíše stav procesu migrace do standardního výstupu (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="3b9ff-121">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="3b9ff-122">Použijete-li `--report-file <REPORT_FILE>` možnost, bude výstup uložen do souboru.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-122">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="3b9ff-123">`dotnet migrate`Příkaz podporuje pouze platná verze Preview 2 projekty založené na *projektu. JSON*.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-123">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="3b9ff-124">To znamená, že ho nemůžete použít k migraci DNX nebo Preview 1 projektů založených na *Project. JSON*přímo do projektů MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-124">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="3b9ff-125">Nejprve je třeba ručně migrovat projekt do projektu verze Preview 2 *Project. JSON*a potom použít `dotnet migrate` příkaz k migraci projektu.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-125">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="3b9ff-126">Arguments</span><span class="sxs-lookup"><span data-stu-id="3b9ff-126">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="3b9ff-127">Cesta k jednomu z následujících:</span><span class="sxs-lookup"><span data-stu-id="3b9ff-127">The path to one of the following:</span></span>

* <span data-ttu-id="3b9ff-128">soubor *Project. JSON* , který se má migrovat</span><span class="sxs-lookup"><span data-stu-id="3b9ff-128">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="3b9ff-129">soubor *Global. JSON* : složky zadané v souboru *Global. JSON* se migrují.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-129">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="3b9ff-130">soubor *řešení. sln* : projekty odkazované v řešení jsou migrovány.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-130">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="3b9ff-131">Adresář, který se má migrovat: rekurzivně vyhledává soubory *Project. JSON* , které se mají migrovat do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-131">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="3b9ff-132">Použije se výchozí nastavení aktuální adresář, pokud není nic zadané.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-132">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="3b9ff-133">Možnosti</span><span class="sxs-lookup"><span data-stu-id="3b9ff-133">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="3b9ff-134">Výstupní soubor sestavy migrace jako JSON, nikoli zprávy uživatele</span><span class="sxs-lookup"><span data-stu-id="3b9ff-134">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="3b9ff-135">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-135">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="3b9ff-136">Výstup sestavy migrace do souboru spolu s konzolou.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-136">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="3b9ff-137">Přeskočit migraci odkazů na projekt</span><span class="sxs-lookup"><span data-stu-id="3b9ff-137">Skip migrating project references.</span></span> <span data-ttu-id="3b9ff-138">Ve výchozím nastavení jsou odkazy na projekt migrovány rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-138">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="3b9ff-139">Po úspěšné migraci můžete přeskočit přesunutí *Project. JSON*, *Global. JSON*a \* \* . xproj\* do `backup` adresáře.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-139">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="3b9ff-140">Soubor CSPROJ šablony, který se má použít pro migraci</span><span class="sxs-lookup"><span data-stu-id="3b9ff-140">Template csproj file to use for migration.</span></span> <span data-ttu-id="3b9ff-141">Ve výchozím nastavení se používá stejná šablona jako vyhozená `dotnet new console` .</span><span class="sxs-lookup"><span data-stu-id="3b9ff-141">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="3b9ff-142">Verze balíčku sady SDK, na který se odkazuje migrovaná aplikace</span><span class="sxs-lookup"><span data-stu-id="3b9ff-142">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="3b9ff-143">Výchozím nastavením je verze sady SDK v nástroji `dotnet new` .</span><span class="sxs-lookup"><span data-stu-id="3b9ff-143">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="3b9ff-144">Cesta k souboru xproj, který se má použít</span><span class="sxs-lookup"><span data-stu-id="3b9ff-144">The path to the xproj file to use.</span></span> <span data-ttu-id="3b9ff-145">Požadováno v případě, že je v adresáři projektu více než jeden xproj.</span><span class="sxs-lookup"><span data-stu-id="3b9ff-145">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="3b9ff-146">Příklady</span><span class="sxs-lookup"><span data-stu-id="3b9ff-146">Examples</span></span>

<span data-ttu-id="3b9ff-147">Migrovat projekt v aktuálním adresáři a všech jeho závislostech mezi projekty:</span><span class="sxs-lookup"><span data-stu-id="3b9ff-147">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="3b9ff-148">Migrujte všechny projekty, které obsahuje soubor *Global. JSON* :</span><span class="sxs-lookup"><span data-stu-id="3b9ff-148">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="3b9ff-149">Migrujte pouze aktuální projekt a žádné závislosti mezi projekty (P2P).</span><span class="sxs-lookup"><span data-stu-id="3b9ff-149">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="3b9ff-150">Použijte také konkrétní verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="3b9ff-150">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
