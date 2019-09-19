---
title: příkaz dotnet list Package
description: Příkaz dotnet list Package nabízí pohodlný možnost zobrazit seznam odkazů na balíčky pro projekt nebo řešení.
ms.date: 06/26/2019
ms.openlocfilehash: fe95f3898c5bd85956f4312eb4d20259227e9ff0
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117725"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="8dde6-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="8dde6-103">dotnet list package</span></span>

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a><span data-ttu-id="8dde6-104">Name</span><span class="sxs-lookup"><span data-stu-id="8dde6-104">Name</span></span>

<span data-ttu-id="8dde6-105">`dotnet list package`– Obsahuje odkazy na balíčky pro projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="8dde6-105">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8dde6-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="8dde6-106">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="8dde6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8dde6-107">Description</span></span>

<span data-ttu-id="8dde6-108">`dotnet list package` Příkaz nabízí pohodlný možnost zobrazit seznam všech odkazů balíčků NuGet pro konkrétní projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="8dde6-108">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="8dde6-109">Nejprve je třeba sestavit projekt, aby bylo možné pro tento příkaz zpracovat potřebné prostředky.</span><span class="sxs-lookup"><span data-stu-id="8dde6-109">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="8dde6-110">Následující příklad ukazuje výstup `dotnet list package` příkazu pro projekt [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) :</span><span class="sxs-lookup"><span data-stu-id="8dde6-110">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="8dde6-111">**Požadovaný** sloupec odkazuje na verzi balíčku zadanou v souboru projektu a může být rozsahem.</span><span class="sxs-lookup"><span data-stu-id="8dde6-111">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="8dde6-112">Sloupec **vyřešený** obsahuje verzi, kterou projekt aktuálně používá, a je vždy jednou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="8dde6-112">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="8dde6-113">Balíčky zobrazující `(A)` právo vedle jejich názvů představují [Implicitní odkazy na balíčky](csproj.md#implicit-package-references) , které jsou odvozeny z nastavení projektu (`Sdk` typ, `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost atd.).</span><span class="sxs-lookup"><span data-stu-id="8dde6-113">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="8dde6-114">`--outdated` Pomocí možnosti zjistíte, jestli jsou v projektech k dispozici novější verze balíčků, které používáte.</span><span class="sxs-lookup"><span data-stu-id="8dde6-114">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="8dde6-115">Ve výchozím nastavení `--outdated` zobrazí seznam nejnovějších stabilních balíčků, pokud není přeložená verze zároveň předprodejní verze.</span><span class="sxs-lookup"><span data-stu-id="8dde6-115">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="8dde6-116">Pokud chcete při výpisu novějších verzí zahrnout předběžné verze, zadejte `--include-prerelease` také možnost.</span><span class="sxs-lookup"><span data-stu-id="8dde6-116">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="8dde6-117">Následující příklady ukazují výstup `dotnet list package --outdated --include-prerelease` příkazu pro stejný projekt jako předchozí příklad:</span><span class="sxs-lookup"><span data-stu-id="8dde6-117">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

<span data-ttu-id="8dde6-118">Pokud potřebujete zjistit, zda má váš projekt přenositelné závislosti, použijte `--include-transitive` možnost.</span><span class="sxs-lookup"><span data-stu-id="8dde6-118">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="8dde6-119">K přenosným závislostem dochází při přidávání balíčku do projektu, který se následně spoléhá na jiný balíček.</span><span class="sxs-lookup"><span data-stu-id="8dde6-119">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="8dde6-120">Následující příklad ukazuje výstup z spuštění `dotnet list package --include-transitive` příkazu pro projekt [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) , který zobrazuje balíčky nejvyšší úrovně a balíčky, na kterých jsou závislé:</span><span class="sxs-lookup"><span data-stu-id="8dde6-120">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Top-level Package                      Requested                    Resolved
   > Microsoft.NETCore.Platforms    (A)   [3.0.0-preview3.19128.7, )   3.0.0-preview3.19128.7
   > Microsoft.WindowsDesktop.App   (A)   [3.0.0-preview3-27504-2, )   3.0.0-preview3-27504-2

   Transitive Package               Resolved
   > Microsoft.NETCore.Targets      2.0.0
   > PluginBase                     1.0.0

(A) : Auto-referenced package.
```

## <a name="arguments"></a><span data-ttu-id="8dde6-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="8dde6-121">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="8dde6-122">Soubor projektu nebo řešení, na kterém chcete pracovat.</span><span class="sxs-lookup"><span data-stu-id="8dde6-122">The project or solution file to operate on.</span></span> <span data-ttu-id="8dde6-123">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="8dde6-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="8dde6-124">Pokud se najde více než jedno řešení nebo projekt, vyvolá se chyba.</span><span class="sxs-lookup"><span data-stu-id="8dde6-124">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="8dde6-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="8dde6-125">Options</span></span>

* **`--config <SOURCE>`**

  <span data-ttu-id="8dde6-126">Zdroje NuGet, které se mají použít při hledání novějších balíčků</span><span class="sxs-lookup"><span data-stu-id="8dde6-126">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="8dde6-127">`--outdated` Vyžaduje možnost.</span><span class="sxs-lookup"><span data-stu-id="8dde6-127">Requires the `--outdated` option.</span></span>

* **`--framework <FRAMEWORK>`**

  <span data-ttu-id="8dde6-128">Zobrazí jenom balíčky, které platí pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="8dde6-128">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="8dde6-129">Pokud chcete zadat více platforem, opakujte možnost několikrát.</span><span class="sxs-lookup"><span data-stu-id="8dde6-129">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="8dde6-130">Například: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="8dde6-130">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="8dde6-131">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="8dde6-131">Prints out a short help for the command.</span></span>

* **`--highest-minor`**

  <span data-ttu-id="8dde6-132">Při hledání novějších balíčků bere v úvahu jenom balíčky s porovnávacím číslem hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="8dde6-132">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="8dde6-133">`--outdated` Vyžaduje možnost.</span><span class="sxs-lookup"><span data-stu-id="8dde6-133">Requires the `--outdated` option.</span></span>

* **`--highest-patch`**

  <span data-ttu-id="8dde6-134">Při hledání novějších balíčků bere v úvahu jenom balíčky s porovnávacími čísly hlavní verze a podverze.</span><span class="sxs-lookup"><span data-stu-id="8dde6-134">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="8dde6-135">`--outdated` Vyžaduje možnost.</span><span class="sxs-lookup"><span data-stu-id="8dde6-135">Requires the `--outdated` option.</span></span>

* **`--include-prerelease`**

  <span data-ttu-id="8dde6-136">Při hledání novějších balíčků bere v úvahu balíčky s předběžnou verzí.</span><span class="sxs-lookup"><span data-stu-id="8dde6-136">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="8dde6-137">`--outdated` Vyžaduje možnost.</span><span class="sxs-lookup"><span data-stu-id="8dde6-137">Requires the `--outdated` option.</span></span>

* **`--include-transitive`**

  <span data-ttu-id="8dde6-138">Vypisuje přenositelné balíčky kromě balíčků nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="8dde6-138">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="8dde6-139">Když zadáte tuto možnost, zobrazí se seznam balíčků, na kterých jsou závislé balíčky na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="8dde6-139">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

* **`--interactive`**

  <span data-ttu-id="8dde6-140">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="8dde6-140">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="8dde6-141">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="8dde6-141">For example, to complete authentication.</span></span> <span data-ttu-id="8dde6-142">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="8dde6-142">Available since .NET Core 3.0 SDK.</span></span>

* **`--outdated`**

  <span data-ttu-id="8dde6-143">Vypíše balíčky s dostupnými novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="8dde6-143">Lists packages that have newer versions available.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="8dde6-144">Zdroje NuGet, které se mají použít při hledání novějších balíčků</span><span class="sxs-lookup"><span data-stu-id="8dde6-144">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="8dde6-145">`--outdated` Vyžaduje možnost.</span><span class="sxs-lookup"><span data-stu-id="8dde6-145">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="8dde6-146">Příklady</span><span class="sxs-lookup"><span data-stu-id="8dde6-146">Examples</span></span>

* <span data-ttu-id="8dde6-147">Výpis odkazů na balíčky určitého projektu:</span><span class="sxs-lookup"><span data-stu-id="8dde6-147">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

* <span data-ttu-id="8dde6-148">Vypíše odkazy na balíčky s dostupnými novějšími verzemi, včetně předprodejních verzí:</span><span class="sxs-lookup"><span data-stu-id="8dde6-148">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

* <span data-ttu-id="8dde6-149">Vypíše odkazy na balíčky pro konkrétní cílové rozhraní:</span><span class="sxs-lookup"><span data-stu-id="8dde6-149">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
