---
title: DotNet migrate příkaz
description: Dotnet migrate příkaz migruje projektu a všechny jeho závislosti.
ms.date: 06/26/2019
ms.openlocfilehash: 3304f666d15d9188cdae76a401747d91791f817f
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539388"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="a6fad-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a6fad-103">dotnet migrate</span></span>

<span data-ttu-id="a6fad-104">**Toto téma platí pro: ✓** .NET Core 1.x sady SDK a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="a6fad-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="a6fad-105">Name</span><span class="sxs-lookup"><span data-stu-id="a6fad-105">Name</span></span>

<span data-ttu-id="a6fad-106">`dotnet migrate` -Migruje do projektu .NET Core SDK – vizuální styl projektu .NET Core 2 ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="a6fad-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

> [!NOTE]
> <span data-ttu-id="a6fad-107">`dotnet migrate` Odebere ze sady SDK .NET Core 3.0 v další vydané verzi preview.</span><span class="sxs-lookup"><span data-stu-id="a6fad-107">`dotnet migrate` will be removed from the .NET Core 3.0 SDK in the next preview release.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a6fad-108">Souhrn</span><span class="sxs-lookup"><span data-stu-id="a6fad-108">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="a6fad-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a6fad-109">Description</span></span>

<span data-ttu-id="a6fad-110">`dotnet migrate` Příkaz migraci platné ve verzi Preview 2 *project.json*– na základě projektu platný sady SDK .NET Core – styl *csproj* projektu.</span><span class="sxs-lookup"><span data-stu-id="a6fad-110">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK-style *csproj* project.</span></span>

<span data-ttu-id="a6fad-111">Ve výchozím nastavení příkaz migruje kořenového projektu a všechny odkazy projektu, které obsahuje projekt kořenové.</span><span class="sxs-lookup"><span data-stu-id="a6fad-111">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="a6fad-112">Toto chování je zakázáno použití `--skip-project-references` možnost za běhu.</span><span class="sxs-lookup"><span data-stu-id="a6fad-112">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="a6fad-113">Migrace lze provést na následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="a6fad-113">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="a6fad-114">Zadáním jednoho projektu *project.json* souboru migrace.</span><span class="sxs-lookup"><span data-stu-id="a6fad-114">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="a6fad-115">Všechny adresáře určené v *global.json* předáním cesty k souboru *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="a6fad-115">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="a6fad-116">A *solution.sln* souboru, kde migruje projekty odkazované v řešení.</span><span class="sxs-lookup"><span data-stu-id="a6fad-116">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="a6fad-117">Na všechny podadresáře rekurzivně zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="a6fad-117">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="a6fad-118">`dotnet migrate` Příkaz udržuje migrovaných *project.json* soubor uvnitř `backup` adresáře, který vytvoří, pokud adresář neexistuje.</span><span class="sxs-lookup"><span data-stu-id="a6fad-118">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="a6fad-119">Toto chování je přepsat pomocí `--skip-backup` možnost.</span><span class="sxs-lookup"><span data-stu-id="a6fad-119">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="a6fad-120">Ve výchozím nastavení vypíše operace migrace stavu procesu migrace do standardního výstupního (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="a6fad-120">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="a6fad-121">Pokud používáte `--report-file <REPORT_FILE>` možnost, výstup bude uložen do souboru zadejte.</span><span class="sxs-lookup"><span data-stu-id="a6fad-121">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="a6fad-122">`dotnet migrate` Platné ve verzi Preview 2 podporuje pouze příkaz *project.json*-projektů založených na.</span><span class="sxs-lookup"><span data-stu-id="a6fad-122">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="a6fad-123">To znamená, že je nelze použít k migraci DNX nebo ve verzi Preview 1 *project.json*– na základě projekty přímo do projektů MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="a6fad-123">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="a6fad-124">Nejdřív musíte ručně provést migraci projekt na verzi Preview 2 *project.json*– na základě projektu a pak `dotnet migrate` příkaz chcete projekt migrovat.</span><span class="sxs-lookup"><span data-stu-id="a6fad-124">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="a6fad-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="a6fad-125">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="a6fad-126">Cesta k jednomu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="a6fad-126">The path to one of the following:</span></span>

* <span data-ttu-id="a6fad-127">*project.json* souboru migrace.</span><span class="sxs-lookup"><span data-stu-id="a6fad-127">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="a6fad-128">*global.json* souboru: složky zadané v *global.json* se migrují.</span><span class="sxs-lookup"><span data-stu-id="a6fad-128">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="a6fad-129">*solution.sln* souboru: projekty odkazované v řešení se migrují.</span><span class="sxs-lookup"><span data-stu-id="a6fad-129">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="a6fad-130">adresář pro migraci: rekurzivně vyhledává *project.json* soubory určené k migraci do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="a6fad-130">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="a6fad-131">Výchozí hodnota je do aktuálního adresáře, pokud není zadáno žádné umístění.</span><span class="sxs-lookup"><span data-stu-id="a6fad-131">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="a6fad-132">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a6fad-132">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="a6fad-133">Výstup souboru sestavy migrace jako JSON a nikoli uživatele zprávy.</span><span class="sxs-lookup"><span data-stu-id="a6fad-133">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="a6fad-134">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a6fad-134">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="a6fad-135">Sestava migrace výstup do souboru kromě konzole.</span><span class="sxs-lookup"><span data-stu-id="a6fad-135">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="a6fad-136">Přeskočit migrace projekt odkazuje.</span><span class="sxs-lookup"><span data-stu-id="a6fad-136">Skip migrating project references.</span></span> <span data-ttu-id="a6fad-137">Ve výchozím nastavení odkazy na projekt jsou migrované rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="a6fad-137">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="a6fad-138">Přeskočit přesun *project.json*, *global.json*, a  *\*xproj* k `backup` adresáře po úspěšné migraci.</span><span class="sxs-lookup"><span data-stu-id="a6fad-138">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="a6fad-139">Soubor csproj šablonu chcete použít pro migraci.</span><span class="sxs-lookup"><span data-stu-id="a6fad-139">Template csproj file to use for migration.</span></span> <span data-ttu-id="a6fad-140">Ve výchozím nastavení, stejné šablony jako zrušených správcem `dotnet new console` se používá.</span><span class="sxs-lookup"><span data-stu-id="a6fad-140">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="a6fad-141">Verze balíčku sady sdk, na který odkazuje migrované aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6fad-141">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="a6fad-142">Výchozí hodnota je verze sady SDK v `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="a6fad-142">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="a6fad-143">Cesta k souboru xproj používat.</span><span class="sxs-lookup"><span data-stu-id="a6fad-143">The path to the xproj file to use.</span></span> <span data-ttu-id="a6fad-144">Povinné, když je více než jeden xproj v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="a6fad-144">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="a6fad-145">Příklady</span><span class="sxs-lookup"><span data-stu-id="a6fad-145">Examples</span></span>

<span data-ttu-id="a6fad-146">Migrate projekt v aktuálním adresáři a všechny jeho závislosti projektu na projekt:</span><span class="sxs-lookup"><span data-stu-id="a6fad-146">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="a6fad-147">Migrovat všechny projekty, které *global.json* soubor obsahuje:</span><span class="sxs-lookup"><span data-stu-id="a6fad-147">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="a6fad-148">Migrujte pouze pro aktuální projekt a nemá žádné závislosti projektu na projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="a6fad-148">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="a6fad-149">Také použijte konkrétní verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="a6fad-149">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
