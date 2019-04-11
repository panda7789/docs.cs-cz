---
title: příkaz DotNet seznamu balíčků
description: Příkaz "balíčku dotnet seznamu" poskytuje vhodnou možnost zobrazíte odkazy na balíčky pro projekt nebo řešení.
ms.date: 04/09/2019
ms.openlocfilehash: bc38b94201f85ed4b22e11722ef5cabcb6fbf040
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481598"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="c6f0d-103">DotNet seznamu balíčků</span><span class="sxs-lookup"><span data-stu-id="c6f0d-103">dotnet list package</span></span>

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a><span data-ttu-id="c6f0d-104">Name</span><span class="sxs-lookup"><span data-stu-id="c6f0d-104">Name</span></span>

`dotnet list package` <span data-ttu-id="c6f0d-105">-Obsahuje odkazy na balíčky pro projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-105">- Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c6f0d-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="c6f0d-106">Synopsis</span></span>

```
dotnet list [<PROJECT | SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="c6f0d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c6f0d-107">Description</span></span>

<span data-ttu-id="c6f0d-108">`dotnet list package` Příkaz poskytuje vhodnou možnost vypsat všechny odkazy na balíčky NuGet pro konkrétní projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-108">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="c6f0d-109">Musíte nejprve sestavte projekt, aby měla prostředky potřebné pro tento příkaz zpracovat.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-109">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="c6f0d-110">Následující příklad ukazuje výstup `dotnet list package` příkazu [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projektu:</span><span class="sxs-lookup"><span data-stu-id="c6f0d-110">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="c6f0d-111">**Požadovaná** sloupec odkazuje na balíček verze zadaná v souboru projektu a mohou být rozsah.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-111">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="c6f0d-112">**Vyřešeno** sloupce se zobrazí výpis verze, že projekt je aktuálně používá a je vždy jedna hodnota.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-112">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="c6f0d-113">Balíčky zobrazení `(A)` představují vpravo vedle jejich názvů [odkazy na balíček implicitní](csproj.md#implicit-package-references) , které jsou odvozeny z nastavení projektu (`Sdk` typ `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost atd.)</span><span class="sxs-lookup"><span data-stu-id="c6f0d-113">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="c6f0d-114">Použití `--outdated` možnost zjistit, existuje novější verze balíčků, které používáte ve svých projektech.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-114">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="c6f0d-115">Ve výchozím nastavení `--outdated` uvádí nejnovější stabilní balíčky, není-li vyřešit verze je také Předběžná verze.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-115">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="c6f0d-116">Chcete-li zahrnout předběžné verze při výpisu novější verze, určit `--include-prerelease` možnost.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-116">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="c6f0d-117">Následující příklady ukazují výstup `dotnet list package --outdated --include-prerelease` stejný projekt jako předchozí příklad příkazu:</span><span class="sxs-lookup"><span data-stu-id="c6f0d-117">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

<span data-ttu-id="c6f0d-118">Pokud potřebujete zjistit, zda má váš projekt přechodné závislosti, použijte `--include-transitive` možnost.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-118">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="c6f0d-119">Přechodné závislosti dojít, když přidáte balíček do projektu, která zase závisí na jiném balíčku.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-119">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="c6f0d-120">Následující příklad ukazuje výstup z běžící `dotnet list package --include-transitive` příkazu [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projekt, který zobrazí nejvyšší úrovně balíčky a balíčky, které jsou závislé na:</span><span class="sxs-lookup"><span data-stu-id="c6f0d-120">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

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

## <a name="arguments"></a><span data-ttu-id="c6f0d-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="c6f0d-121">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="c6f0d-122">Soubor projektu nebo řešení se má operace provést.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-122">The project or solution file to operate on.</span></span> <span data-ttu-id="c6f0d-123">Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="c6f0d-124">Pokud je nalezen více než jedno řešení nebo projekt, je vržena chyba.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-124">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="c6f0d-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c6f0d-125">Options</span></span>

* **`--config <SOURCE>`**

  <span data-ttu-id="c6f0d-126">NuGet zdroje, které chcete použít při hledání novější balíčky.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-126">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="c6f0d-127">Vyžaduje `--outdated` možnost.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-127">Requires the `--outdated` option.</span></span>

* **`--framework <FRAMEWORK>`**

  <span data-ttu-id="c6f0d-128">Zobrazí jenom balíčky použitelné pro zadaný rozbočovač [Cílová architektura](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c6f0d-128">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="c6f0d-129">Chcete-li zadat více platforem, opakujte možnost více než jednou.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-129">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="c6f0d-130">Například: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-130">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="c6f0d-131">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-131">Prints out a short help for the command.</span></span>

* **`--highest-minor`**

  <span data-ttu-id="c6f0d-132">Bere v úvahu jenom balíčky s odpovídající číslo hlavní verze vyhledávání novější balíčky.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-132">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="c6f0d-133">Vyžaduje `--outdated` možnost.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-133">Requires the `--outdated` option.</span></span>

* **`--highest-patch`**

  <span data-ttu-id="c6f0d-134">Bere v úvahu jenom balíčky k odpovídajícímu hlavní a podverze čísla při hledání novější balíčky.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-134">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="c6f0d-135">Vyžaduje `--outdated` možnost.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-135">Requires the `--outdated` option.</span></span>

* **`--include-prerelease`**

  <span data-ttu-id="c6f0d-136">Při hledání novější balíčky bere v úvahu balíčky s předběžné verze.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-136">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="c6f0d-137">Vyžaduje `--outdated` možnost.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-137">Requires the `--outdated` option.</span></span>

* **`--include-transitive`**

  <span data-ttu-id="c6f0d-138">Zobrazí seznam tranzitivní balíčků, kromě nejvyšší úrovně balíčky.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-138">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="c6f0d-139">Při zadání této možnosti, získání seznamu balíčků, které závisí nejvyšší úrovni balíčky.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-139">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

* **`--outdated`**

  <span data-ttu-id="c6f0d-140">Zobrazí seznam balíčků, které mají k dispozici novější verze.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-140">Lists packages that have newer versions available.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="c6f0d-141">NuGet zdroje, které chcete použít při hledání novější balíčky.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-141">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="c6f0d-142">Vyžaduje `--outdated` možnost.</span><span class="sxs-lookup"><span data-stu-id="c6f0d-142">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="c6f0d-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="c6f0d-143">Examples</span></span>

* <span data-ttu-id="c6f0d-144">Seznam odkazů balíček na určitém projektu:</span><span class="sxs-lookup"><span data-stu-id="c6f0d-144">List package references of a specific project:</span></span>

  ```console
  dotnet list SentimentAnalysis.csproj package
  ```

* <span data-ttu-id="c6f0d-145">Seznam odkazy na balíčky, které mají novější verze, které jsou k dispozici, včetně předběžné verze:</span><span class="sxs-lookup"><span data-stu-id="c6f0d-145">List package references that have newer versions available, including prerelease versions:</span></span>

  ```console
  dotnet list package --outdated --include-prerelease
  ```

* <span data-ttu-id="c6f0d-146">Vypište odkazy na balíček pro konkrétní cílové rozhraní:</span><span class="sxs-lookup"><span data-stu-id="c6f0d-146">List package references for a specific target framework:</span></span>

  ```console
  dotnet list package --framework netcoreapp3.0
  ```