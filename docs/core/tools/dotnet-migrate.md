---
title: dotnet – příkaz migrace
description: Příkaz dotnet migruje migruje projekt a všechny jeho závislosti.
ms.date: 08/08/2019
ms.openlocfilehash: 790c607070ff348ca7cfe30137268de18dcb0293
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990432"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="4ed49-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="4ed49-103">dotnet migrate</span></span>

<span data-ttu-id="4ed49-104">**Tento článek se týká: ✓** .NET Core 1. x SDK **✓** .NET Core 2. x SDK</span><span class="sxs-lookup"><span data-stu-id="4ed49-104">**This article applies to: ✓** .NET Core 1.x SDK **✓** .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="4ed49-105">Name</span><span class="sxs-lookup"><span data-stu-id="4ed49-105">Name</span></span>

<span data-ttu-id="4ed49-106">`dotnet migrate`– Migruje projekt .NET Core ve verzi Preview 2 na projekt ve stylu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="4ed49-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4ed49-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="4ed49-107">Synopsis</span></span>

```console
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="4ed49-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4ed49-108">Description</span></span>

<span data-ttu-id="4ed49-109">Příkaz migruje platný projekt založený na verzi Preview 2 *Project. JSON*na platný projekt csproj ve stylu .NET Core SDK. `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="4ed49-109">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK-style *csproj* project.</span></span>

<span data-ttu-id="4ed49-110">Ve výchozím nastavení příkaz migruje kořenový projekt a všechny odkazy projektu, které obsahuje kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="4ed49-110">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="4ed49-111">Toto chování je zakázáno pomocí `--skip-project-references` možnosti za běhu.</span><span class="sxs-lookup"><span data-stu-id="4ed49-111">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="4ed49-112">Migraci můžete provádět na těchto prostředcích:</span><span class="sxs-lookup"><span data-stu-id="4ed49-112">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="4ed49-113">Jeden projekt zadáním souboru *Project. JSON* , který se má migrovat.</span><span class="sxs-lookup"><span data-stu-id="4ed49-113">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="4ed49-114">Všechny adresáře zadané v souboru *Global. JSON* předáním cesty k souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="4ed49-114">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="4ed49-115">Soubor *řešení. sln* , kde migruje projekty, na které je odkazováno v řešení.</span><span class="sxs-lookup"><span data-stu-id="4ed49-115">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="4ed49-116">Ve všech podadresářích daného adresáře rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="4ed49-116">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="4ed49-117">Příkaz udržuje migrovaný soubor *Project. JSON* v `backup` adresáři, který vytvoří, pokud adresář neexistuje. `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="4ed49-117">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="4ed49-118">Toto chování je přepsáno `--skip-backup` pomocí možnosti.</span><span class="sxs-lookup"><span data-stu-id="4ed49-118">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="4ed49-119">Ve výchozím nastavení operace migrace vypíše stav procesu migrace do standardního výstupu (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="4ed49-119">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="4ed49-120">Použijete-li `--report-file <REPORT_FILE>` možnost, bude výstup uložen do souboru.</span><span class="sxs-lookup"><span data-stu-id="4ed49-120">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="4ed49-121">Příkaz podporuje pouze platná verze Preview 2 projekty založené na *projektu. JSON.* `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="4ed49-121">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="4ed49-122">To znamená, že ho nemůžete použít k migraci DNX nebo Preview 1 projektů založených na *Project. JSON*přímo do projektů MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="4ed49-122">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="4ed49-123">Nejprve je třeba ručně migrovat projekt do projektu verze Preview 2 *Project. JSON*a potom použít `dotnet migrate` příkaz k migraci projektu.</span><span class="sxs-lookup"><span data-stu-id="4ed49-123">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

<span data-ttu-id="4ed49-124">`dotnet migrate` Příkaz již není od sady .NET Core 3,0 SDK k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4ed49-124">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span>

## <a name="arguments"></a><span data-ttu-id="4ed49-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="4ed49-125">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="4ed49-126">Cesta k jednomu z následujících:</span><span class="sxs-lookup"><span data-stu-id="4ed49-126">The path to one of the following:</span></span>

* <span data-ttu-id="4ed49-127">soubor *Project. JSON* , který se má migrovat</span><span class="sxs-lookup"><span data-stu-id="4ed49-127">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="4ed49-128">soubor *Global. JSON* : složky zadané v souboru *Global. JSON* se migrují.</span><span class="sxs-lookup"><span data-stu-id="4ed49-128">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="4ed49-129">soubor *řešení. sln* : projekty odkazované v řešení jsou migrovány.</span><span class="sxs-lookup"><span data-stu-id="4ed49-129">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="4ed49-130">Adresář, který se má migrovat: rekurzivně vyhledává soubory *Project. JSON* , které se mají migrovat do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="4ed49-130">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="4ed49-131">Použije se výchozí nastavení aktuální adresář, pokud není nic zadané.</span><span class="sxs-lookup"><span data-stu-id="4ed49-131">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="4ed49-132">Možnosti</span><span class="sxs-lookup"><span data-stu-id="4ed49-132">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="4ed49-133">Výstupní soubor sestavy migrace jako JSON, nikoli zprávy uživatele</span><span class="sxs-lookup"><span data-stu-id="4ed49-133">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="4ed49-134">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="4ed49-134">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="4ed49-135">Výstup sestavy migrace do souboru spolu s konzolou.</span><span class="sxs-lookup"><span data-stu-id="4ed49-135">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="4ed49-136">Přeskočit migraci odkazů na projekt</span><span class="sxs-lookup"><span data-stu-id="4ed49-136">Skip migrating project references.</span></span> <span data-ttu-id="4ed49-137">Ve výchozím nastavení jsou odkazy na projekt migrovány rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="4ed49-137">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="4ed49-138">Po úspěšné migraci můžete přeskočit přesunutí *Project. JSON*, *Global. JSON*a  *\*. xproj* do `backup` adresáře.</span><span class="sxs-lookup"><span data-stu-id="4ed49-138">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="4ed49-139">Soubor CSPROJ šablony, který se má použít pro migraci</span><span class="sxs-lookup"><span data-stu-id="4ed49-139">Template csproj file to use for migration.</span></span> <span data-ttu-id="4ed49-140">Ve výchozím nastavení `dotnet new console` se používá stejná šablona jako vyhozená.</span><span class="sxs-lookup"><span data-stu-id="4ed49-140">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="4ed49-141">Verze balíčku sady SDK, na který se odkazuje migrovaná aplikace</span><span class="sxs-lookup"><span data-stu-id="4ed49-141">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="4ed49-142">Výchozím nastavením je verze sady SDK v `dotnet new`nástroji.</span><span class="sxs-lookup"><span data-stu-id="4ed49-142">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="4ed49-143">Cesta k souboru xproj, který se má použít</span><span class="sxs-lookup"><span data-stu-id="4ed49-143">The path to the xproj file to use.</span></span> <span data-ttu-id="4ed49-144">Požadováno v případě, že je v adresáři projektu více než jeden xproj.</span><span class="sxs-lookup"><span data-stu-id="4ed49-144">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="4ed49-145">Příklady</span><span class="sxs-lookup"><span data-stu-id="4ed49-145">Examples</span></span>

<span data-ttu-id="4ed49-146">Migrovat projekt v aktuálním adresáři a všech jeho závislostech mezi projekty:</span><span class="sxs-lookup"><span data-stu-id="4ed49-146">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="4ed49-147">Migrujte všechny projekty, které obsahuje soubor *Global. JSON* :</span><span class="sxs-lookup"><span data-stu-id="4ed49-147">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="4ed49-148">Migrujte pouze aktuální projekt a žádné závislosti mezi projekty (P2P).</span><span class="sxs-lookup"><span data-stu-id="4ed49-148">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="4ed49-149">Použijte také konkrétní verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="4ed49-149">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
