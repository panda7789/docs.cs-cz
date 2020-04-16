---
title: Příkaz balíčku seznamu dotnet
description: Příkaz "dotnet list package" poskytuje vhodnou možnost pro seznam odkazů na balíček pro projekt nebo řešení.
ms.date: 02/14/2020
ms.openlocfilehash: 12d64600d178ea8cf490a0d6917e67bd3d8c6d21
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463665"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="d5fb3-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="d5fb3-103">dotnet list package</span></span>

<span data-ttu-id="d5fb3-104">**Tento článek se týká:** ✔️ .NET Core 2.2 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="d5fb3-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d5fb3-105">Název</span><span class="sxs-lookup"><span data-stu-id="d5fb3-105">Name</span></span>

<span data-ttu-id="d5fb3-106">`dotnet list package`- Uvádí odkazy na balíček pro projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d5fb3-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="d5fb3-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>]

dotnet list package -h|--help
```

## <a name="description"></a><span data-ttu-id="d5fb3-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d5fb3-108">Description</span></span>

<span data-ttu-id="d5fb3-109">Příkaz `dotnet list package` poskytuje vhodnou možnost vypsat všechny odkazy na balíček NuGet pro konkrétní projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="d5fb3-110">Nejprve je třeba vytvořit projekt, aby byly prostředky potřebné pro tento příkaz ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="d5fb3-111">Následující příklad ukazuje výstup `dotnet list package` příkazu pro [sentimentanalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projektu:</span><span class="sxs-lookup"><span data-stu-id="d5fb3-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="d5fb3-112">Sloupec **Požadován** odkazuje na verzi balíčku zadanou v souboru projektu a může se týkat oblasti.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="d5fb3-113">Ve sloupci **Vyřešeno** je uvedena verze, kterou projekt aktuálně používá, a je vždy jednou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="d5fb3-114">Balíčky zobrazující `(A)` vpravo vedle jejich názvy představují [implicitní odkazy na balíčky,](csproj.md#implicit-package-references) které jsou odvozeny z nastavení projektu (typ`Sdk` nebo `<TargetFramework>` `<TargetFrameworks>` vlastnost atd.)</span><span class="sxs-lookup"><span data-stu-id="d5fb3-114">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="d5fb3-115">Pomocí `--outdated` této možnosti můžete zjistit, jestli jsou k dispozici novější verze balíčků, které používáte ve svých projektech.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="d5fb3-116">Ve výchozím `--outdated` nastavení uvádí seznam nejnovějších stabilních balíčků, pokud přeložená verze není také předběžnou verzí.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="d5fb3-117">Chcete-li zahrnout předběžné verze při výpisu novějších verzí, zadejte také `--include-prerelease` možnost.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="d5fb3-118">Následující příklady ukazují výstup `dotnet list package --outdated --include-prerelease` příkazu pro stejný projekt jako předchozí příklad:</span><span class="sxs-lookup"><span data-stu-id="d5fb3-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="d5fb3-119">Pokud potřebujete zjistit, zda má projekt přenosné závislosti, `--include-transitive` použijte tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="d5fb3-120">Přenosité závislosti dojít při přidání balíčku do projektu, který zase spoléhá na jiný balíček.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="d5fb3-121">Následující příklad ukazuje výstup ze `dotnet list package --include-transitive` spuštění příkazu pro projekt [HelloPlugin,](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) který zobrazuje balíčky nejvyšší úrovně a balíčky, na kterých závisí:</span><span class="sxs-lookup"><span data-stu-id="d5fb3-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="d5fb3-122">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d5fb3-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="d5fb3-123">Soubor projektu nebo řešení, na kterém chcete pracovat.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-123">The project or solution file to operate on.</span></span> <span data-ttu-id="d5fb3-124">Pokud není zadán, příkaz prohledá aktuální adresář pro jeden.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="d5fb3-125">Pokud je nalezeno více než jedno řešení nebo projekt, je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="d5fb3-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d5fb3-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="d5fb3-127">NuGet zdroje pro použití při hledání novějších balíčků.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="d5fb3-128">Vyžaduje `--outdated` možnost.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-128">Requires the `--outdated` option.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="d5fb3-129">Zobrazí pouze balíčky použitelné pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d5fb3-129">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d5fb3-130">Chcete-li určit více architektur, opakujte možnost vícekrát.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-130">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="d5fb3-131">Například: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-131">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d5fb3-132">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-132">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="d5fb3-133">Bere v úvahu pouze balíčky s odpovídající číslo hlavní verze při hledání novější chbalíčky.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-133">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="d5fb3-134">Vyžaduje `--outdated` možnost.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-134">Requires the `--outdated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="d5fb3-135">Bere v úvahu pouze balíčky s odpovídající hlavní a dílčí čísla verzí při hledání novějších balíčků.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-135">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="d5fb3-136">Vyžaduje `--outdated` možnost.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-136">Requires the `--outdated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="d5fb3-137">Bere v úvahu balíčky s předběžnými verzemi při hledání novějších balíčků.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-137">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="d5fb3-138">Vyžaduje `--outdated` možnost.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-138">Requires the `--outdated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="d5fb3-139">Kromě balíčků nejvyšší úrovně obsahuje seznam přenosných balíčků.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-139">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="d5fb3-140">Při zadávání této možnosti získáte seznam balíčků, na kterých závisí balíčky nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-140">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="d5fb3-141">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-141">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="d5fb3-142">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-142">For example, to complete authentication.</span></span> <span data-ttu-id="d5fb3-143">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="d5fb3-144">Seznam balíčků, které mají k dispozici novější verze.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-144">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="d5fb3-145">NuGet zdroje pro použití při hledání novějších balíčků.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-145">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="d5fb3-146">Vyžaduje `--outdated` možnost.</span><span class="sxs-lookup"><span data-stu-id="d5fb3-146">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="d5fb3-147">Příklady</span><span class="sxs-lookup"><span data-stu-id="d5fb3-147">Examples</span></span>

- <span data-ttu-id="d5fb3-148">Seznam odkazů na balíček konkrétního projektu:</span><span class="sxs-lookup"><span data-stu-id="d5fb3-148">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="d5fb3-149">Seznam odkazů na balíčky, které mají k dispozici novější verze, včetně předběžných verzí:</span><span class="sxs-lookup"><span data-stu-id="d5fb3-149">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="d5fb3-150">Seznam odkazů na balíček pro konkrétní cílový rámec:</span><span class="sxs-lookup"><span data-stu-id="d5fb3-150">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
