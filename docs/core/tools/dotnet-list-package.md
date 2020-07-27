---
title: příkaz dotnet list Package
description: Příkaz dotnet list Package nabízí pohodlný možnost zobrazit seznam odkazů na balíčky pro projekt nebo řešení.
ms.date: 02/14/2020
ms.openlocfilehash: 7157e56860936d10aa322854a589ae89e2bc0826
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164750"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="d89a8-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="d89a8-103">dotnet list package</span></span>

<span data-ttu-id="d89a8-104">**Tento článek se týká:** ✔️ .net Core 2,2 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="d89a8-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d89a8-105">Název</span><span class="sxs-lookup"><span data-stu-id="d89a8-105">Name</span></span>

<span data-ttu-id="d89a8-106">`dotnet list package`– Obsahuje odkazy na balíčky pro projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="d89a8-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d89a8-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d89a8-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--deprecated]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>]

dotnet list package -h|--help
```

## <a name="description"></a><span data-ttu-id="d89a8-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d89a8-108">Description</span></span>

<span data-ttu-id="d89a8-109">`dotnet list package`Příkaz nabízí pohodlný možnost zobrazit seznam všech odkazů balíčků NuGet pro konkrétní projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="d89a8-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="d89a8-110">Nejprve je třeba sestavit projekt, aby bylo možné pro tento příkaz zpracovat potřebné prostředky.</span><span class="sxs-lookup"><span data-stu-id="d89a8-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="d89a8-111">Následující příklad ukazuje výstup `dotnet list package` příkazu pro projekt [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) :</span><span class="sxs-lookup"><span data-stu-id="d89a8-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="d89a8-112">**Požadovaný** sloupec odkazuje na verzi balíčku zadanou v souboru projektu a může být rozsahem.</span><span class="sxs-lookup"><span data-stu-id="d89a8-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="d89a8-113">Sloupec **vyřešený** obsahuje verzi, kterou projekt aktuálně používá, a je vždy jednou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="d89a8-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="d89a8-114">Balíčky zobrazující `(A)` právo vedle jejich názvů představují [Implicitní odkazy na balíčky](csproj.md#implicit-package-references) , které jsou odvozeny z nastavení projektu ( `Sdk` typ, `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost atd.).</span><span class="sxs-lookup"><span data-stu-id="d89a8-114">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="d89a8-115">Pomocí `--outdated` Možnosti zjistíte, jestli jsou v projektech k dispozici novější verze balíčků, které používáte.</span><span class="sxs-lookup"><span data-stu-id="d89a8-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="d89a8-116">Ve výchozím nastavení `--outdated` zobrazí seznam nejnovějších stabilních balíčků, pokud není přeložená verze zároveň předprodejní verze.</span><span class="sxs-lookup"><span data-stu-id="d89a8-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="d89a8-117">Pokud chcete při výpisu novějších verzí zahrnout předběžné verze, zadejte také `--include-prerelease` možnost.</span><span class="sxs-lookup"><span data-stu-id="d89a8-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="d89a8-118">Následující příklady ukazují výstup `dotnet list package --outdated --include-prerelease` příkazu pro stejný projekt jako předchozí příklad:</span><span class="sxs-lookup"><span data-stu-id="d89a8-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="d89a8-119">Pokud potřebujete zjistit, zda má váš projekt přenositelné závislosti, použijte `--include-transitive` možnost.</span><span class="sxs-lookup"><span data-stu-id="d89a8-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="d89a8-120">K přenosným závislostem dochází při přidávání balíčku do projektu, který se následně spoléhá na jiný balíček.</span><span class="sxs-lookup"><span data-stu-id="d89a8-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="d89a8-121">Následující příklad ukazuje výstup z spuštění `dotnet list package --include-transitive` příkazu pro projekt [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) , který zobrazuje balíčky nejvyšší úrovně a balíčky, na kterých jsou závislé:</span><span class="sxs-lookup"><span data-stu-id="d89a8-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="d89a8-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="d89a8-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="d89a8-123">Soubor projektu nebo řešení, na kterém chcete pracovat.</span><span class="sxs-lookup"><span data-stu-id="d89a8-123">The project or solution file to operate on.</span></span> <span data-ttu-id="d89a8-124">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="d89a8-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="d89a8-125">Pokud se najde více než jedno řešení nebo projekt, vyvolá se chyba.</span><span class="sxs-lookup"><span data-stu-id="d89a8-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="d89a8-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d89a8-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="d89a8-127">Zdroje NuGet, které se mají použít při hledání novějších balíčků</span><span class="sxs-lookup"><span data-stu-id="d89a8-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="d89a8-128">Vyžaduje `--outdated` možnost.</span><span class="sxs-lookup"><span data-stu-id="d89a8-128">Requires the `--outdated` option.</span></span>

- **`--deprecated`**

  <span data-ttu-id="d89a8-129">Zobrazí zastaralé balíčky.</span><span class="sxs-lookup"><span data-stu-id="d89a8-129">Displays packages that have been deprecated.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="d89a8-130">Zobrazí jenom balíčky, které platí pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d89a8-130">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d89a8-131">Pokud chcete zadat více platforem, opakujte možnost několikrát.</span><span class="sxs-lookup"><span data-stu-id="d89a8-131">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="d89a8-132">Například: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="d89a8-132">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d89a8-133">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="d89a8-133">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="d89a8-134">Při hledání novějších balíčků bere v úvahu jenom balíčky s porovnávacím číslem hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="d89a8-134">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="d89a8-135">Vyžaduje `--outdated` parametr nebo `--deprecated` .</span><span class="sxs-lookup"><span data-stu-id="d89a8-135">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="d89a8-136">Při hledání novějších balíčků bere v úvahu jenom balíčky s porovnávacími čísly hlavní verze a podverze.</span><span class="sxs-lookup"><span data-stu-id="d89a8-136">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="d89a8-137">Vyžaduje `--outdated` parametr nebo `--deprecated` .</span><span class="sxs-lookup"><span data-stu-id="d89a8-137">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="d89a8-138">Při hledání novějších balíčků bere v úvahu balíčky s předběžnou verzí.</span><span class="sxs-lookup"><span data-stu-id="d89a8-138">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="d89a8-139">Vyžaduje `--outdated` parametr nebo `--deprecated` .</span><span class="sxs-lookup"><span data-stu-id="d89a8-139">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="d89a8-140">Vypisuje přenositelné balíčky kromě balíčků nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="d89a8-140">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="d89a8-141">Když zadáte tuto možnost, zobrazí se seznam balíčků, na kterých jsou závislé balíčky na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="d89a8-141">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="d89a8-142">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="d89a8-142">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="d89a8-143">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="d89a8-143">For example, to complete authentication.</span></span> <span data-ttu-id="d89a8-144">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d89a8-144">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="d89a8-145">Vypíše balíčky s dostupnými novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="d89a8-145">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="d89a8-146">Zdroje NuGet, které se mají použít při hledání novějších balíčků</span><span class="sxs-lookup"><span data-stu-id="d89a8-146">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="d89a8-147">Vyžaduje `--outdated` parametr nebo `--deprecated` .</span><span class="sxs-lookup"><span data-stu-id="d89a8-147">Requires the `--outdated` or `--deprecated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="d89a8-148">Příklady</span><span class="sxs-lookup"><span data-stu-id="d89a8-148">Examples</span></span>

- <span data-ttu-id="d89a8-149">Výpis odkazů na balíčky určitého projektu:</span><span class="sxs-lookup"><span data-stu-id="d89a8-149">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="d89a8-150">Vypíše odkazy na balíčky s dostupnými novějšími verzemi, včetně předprodejních verzí:</span><span class="sxs-lookup"><span data-stu-id="d89a8-150">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="d89a8-151">Vypíše odkazy na balíčky pro konkrétní cílové rozhraní:</span><span class="sxs-lookup"><span data-stu-id="d89a8-151">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
