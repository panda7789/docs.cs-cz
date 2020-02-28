---
title: příkaz dotnet list Package
description: Příkaz dotnet list Package nabízí pohodlný možnost zobrazit seznam odkazů na balíčky pro projekt nebo řešení.
ms.date: 02/14/2020
ms.openlocfilehash: 1cb52b8de10b2eef2ef7465f04316e9446318763
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157229"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="0f51f-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="0f51f-103">dotnet list package</span></span>

<span data-ttu-id="0f51f-104">**Tento článek se týká:** ✔️ .net Core 2,2 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="0f51f-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0f51f-105">Název</span><span class="sxs-lookup"><span data-stu-id="0f51f-105">Name</span></span>

<span data-ttu-id="0f51f-106">`dotnet list package` – obsahuje odkazy na balíček pro projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="0f51f-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0f51f-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="0f51f-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch]
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="0f51f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="0f51f-108">Description</span></span>

<span data-ttu-id="0f51f-109">Příkaz `dotnet list package` nabízí pohodlný možnost zobrazit seznam všech odkazů na balíčky NuGet pro konkrétní projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="0f51f-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="0f51f-110">Nejprve je třeba sestavit projekt, aby bylo možné pro tento příkaz zpracovat potřebné prostředky.</span><span class="sxs-lookup"><span data-stu-id="0f51f-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="0f51f-111">Následující příklad ukazuje výstup příkazu `dotnet list package` pro projekt [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) :</span><span class="sxs-lookup"><span data-stu-id="0f51f-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="0f51f-112">**Požadovaný** sloupec odkazuje na verzi balíčku zadanou v souboru projektu a může být rozsahem.</span><span class="sxs-lookup"><span data-stu-id="0f51f-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="0f51f-113">Sloupec **vyřešený** obsahuje verzi, kterou projekt aktuálně používá, a je vždy jednou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="0f51f-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="0f51f-114">Balíčky zobrazující `(A)` vpravo vedle jejich názvů představují [Implicitní odkazy na balíčky](csproj.md#implicit-package-references) , které jsou odvozeny z nastavení projektu (typ`Sdk`, `<TargetFramework>` nebo `<TargetFrameworks>` Property atd.).</span><span class="sxs-lookup"><span data-stu-id="0f51f-114">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="0f51f-115">Pomocí možnosti `--outdated` zjistíte, jestli jsou v projektech k dispozici novější verze balíčků, které používáte.</span><span class="sxs-lookup"><span data-stu-id="0f51f-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="0f51f-116">Ve výchozím nastavení `--outdated` uvádí nejnovější stabilní balíčky, pokud není přeložená verze zároveň předprodejní verze.</span><span class="sxs-lookup"><span data-stu-id="0f51f-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="0f51f-117">Chcete-li zahrnout předprodejní verze při výpisu novějších verzí, zadejte také možnost `--include-prerelease`.</span><span class="sxs-lookup"><span data-stu-id="0f51f-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="0f51f-118">Následující příklady ukazují výstup příkazu `dotnet list package --outdated --include-prerelease` pro stejný projekt jako předchozí příklad:</span><span class="sxs-lookup"><span data-stu-id="0f51f-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="0f51f-119">Pokud potřebujete zjistit, zda má váš projekt přenositelné závislosti, použijte možnost `--include-transitive`.</span><span class="sxs-lookup"><span data-stu-id="0f51f-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="0f51f-120">K přenosným závislostem dochází při přidávání balíčku do projektu, který se následně spoléhá na jiný balíček.</span><span class="sxs-lookup"><span data-stu-id="0f51f-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="0f51f-121">Následující příklad ukazuje výstup z spuštění příkazu `dotnet list package --include-transitive` pro projekt [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) , který zobrazuje balíčky nejvyšší úrovně a balíčky, na kterých jsou závislé:</span><span class="sxs-lookup"><span data-stu-id="0f51f-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="0f51f-122">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0f51f-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="0f51f-123">Soubor projektu nebo řešení, na kterém chcete pracovat.</span><span class="sxs-lookup"><span data-stu-id="0f51f-123">The project or solution file to operate on.</span></span> <span data-ttu-id="0f51f-124">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="0f51f-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="0f51f-125">Pokud se najde více než jedno řešení nebo projekt, vyvolá se chyba.</span><span class="sxs-lookup"><span data-stu-id="0f51f-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="0f51f-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0f51f-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="0f51f-127">Zdroje NuGet, které se mají použít při hledání novějších balíčků</span><span class="sxs-lookup"><span data-stu-id="0f51f-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="0f51f-128">Vyžaduje možnost `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="0f51f-128">Requires the `--outdated` option.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="0f51f-129">Zobrazí jenom balíčky, které platí pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0f51f-129">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="0f51f-130">Pokud chcete zadat více platforem, opakujte možnost několikrát.</span><span class="sxs-lookup"><span data-stu-id="0f51f-130">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="0f51f-131">Například: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="0f51f-131">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0f51f-132">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="0f51f-132">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="0f51f-133">Při hledání novějších balíčků bere v úvahu jenom balíčky s porovnávacím číslem hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="0f51f-133">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="0f51f-134">Vyžaduje možnost `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="0f51f-134">Requires the `--outdated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="0f51f-135">Při hledání novějších balíčků bere v úvahu jenom balíčky s porovnávacími čísly hlavní verze a podverze.</span><span class="sxs-lookup"><span data-stu-id="0f51f-135">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="0f51f-136">Vyžaduje možnost `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="0f51f-136">Requires the `--outdated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="0f51f-137">Při hledání novějších balíčků bere v úvahu balíčky s předběžnou verzí.</span><span class="sxs-lookup"><span data-stu-id="0f51f-137">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="0f51f-138">Vyžaduje možnost `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="0f51f-138">Requires the `--outdated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="0f51f-139">Vypisuje přenositelné balíčky kromě balíčků nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="0f51f-139">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="0f51f-140">Když zadáte tuto možnost, zobrazí se seznam balíčků, na kterých jsou závislé balíčky na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="0f51f-140">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="0f51f-141">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="0f51f-141">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="0f51f-142">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f51f-142">For example, to complete authentication.</span></span> <span data-ttu-id="0f51f-143">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="0f51f-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="0f51f-144">Vypíše balíčky s dostupnými novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="0f51f-144">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="0f51f-145">Zdroje NuGet, které se mají použít při hledání novějších balíčků</span><span class="sxs-lookup"><span data-stu-id="0f51f-145">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="0f51f-146">Vyžaduje možnost `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="0f51f-146">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="0f51f-147">Příklady</span><span class="sxs-lookup"><span data-stu-id="0f51f-147">Examples</span></span>

- <span data-ttu-id="0f51f-148">Výpis odkazů na balíčky určitého projektu:</span><span class="sxs-lookup"><span data-stu-id="0f51f-148">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="0f51f-149">Vypíše odkazy na balíčky s dostupnými novějšími verzemi, včetně předprodejních verzí:</span><span class="sxs-lookup"><span data-stu-id="0f51f-149">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="0f51f-150">Vypíše odkazy na balíčky pro konkrétní cílové rozhraní:</span><span class="sxs-lookup"><span data-stu-id="0f51f-150">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
