---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206205"
---
### <a name="resource-manifest-file-name-change"></a><span data-ttu-id="017a3-101">Název souboru manifestu prostředku – změna</span><span class="sxs-lookup"><span data-stu-id="017a3-101">Resource manifest file name change</span></span>

<span data-ttu-id="017a3-102">Počínaje platformou .NET Core 3,0 ve výchozím případě nástroj MSBuild generuje pro soubory prostředků jiný název souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="017a3-102">Starting in .NET Core 3.0, in the default case, MSBuild generates a different manifest file name for resource files.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="017a3-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="017a3-103">Version introduced</span></span>

<span data-ttu-id="017a3-104">3.0</span><span class="sxs-lookup"><span data-stu-id="017a3-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="017a3-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="017a3-105">Change description</span></span>

<span data-ttu-id="017a3-106">Před rozhraním .NET Core 3,0, pokud `LogicalName` `ManifestResourceName` nebyla zadána žádná, nebo `DependentUpon` metadata pro `EmbeddedResource` položku v souboru projektu, nástroj MSBuild vygeneroval ve vzoru název souboru manifestu `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` .</span><span class="sxs-lookup"><span data-stu-id="017a3-106">Prior to .NET Core 3.0, if no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata was specified for an `EmbeddedResource` item in the project file, MSBuild generated a manifest file name in the pattern `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources`.</span></span> <span data-ttu-id="017a3-107">Pokud `RootNamespace` není v souboru projektu definován, je výchozím názvem projektu.</span><span class="sxs-lookup"><span data-stu-id="017a3-107">If `RootNamespace` is not defined in the project file, it defaults to the project name.</span></span> <span data-ttu-id="017a3-108">Například vygenerovaný název manifestu pro soubor prostředků s názvem *Form1. resx* v kořenovém adresáři projektu byl *MyProject. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="017a3-108">For example, the generated manifest name for a resource file named *Form1.resx* in the root project directory was *MyProject.Form1.resources*.</span></span>

<span data-ttu-id="017a3-109">Počínaje platformou .NET Core 3,0 platí, že pokud se soubor prostředků nachází společně se zdrojovým souborem se stejným názvem (například *Form1. resx* a *Form1.cs*), nástroj MSBuild používá informace o typu ze zdrojového souboru pro vygenerování názvu souboru manifestu ve vzoru `<Namespace>.<ClassName>.resources` .</span><span class="sxs-lookup"><span data-stu-id="017a3-109">Starting in .NET Core 3.0, if a resource file is colocated with a source file of the same name (for example, *Form1.resx* and *Form1.cs*), MSBuild uses type information from the source file to generate the manifest file name in the pattern `<Namespace>.<ClassName>.resources`.</span></span> <span data-ttu-id="017a3-110">Obor názvů a název třídy jsou extrahovány z prvního typu v společně umístěném zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="017a3-110">The namespace and class name are extracted from the first type in the colocated source file.</span></span> <span data-ttu-id="017a3-111">Například vygenerovaný název manifestu pro soubor prostředků s názvem *Form1. resx* , který je společně umístěn pomocí zdrojového souboru s názvem *Form1.cs* , je *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="017a3-111">For example, the generated manifest name for a resource file named *Form1.resx* that's colocated with a source file named *Form1.cs* is *MyNamespace.Form1.resources*.</span></span> <span data-ttu-id="017a3-112">Klíčovým poznámku je, že první část názvu souboru se liší od předchozích verzí .NET Core (*MyNamespace* místo *MyProject*).</span><span class="sxs-lookup"><span data-stu-id="017a3-112">The key thing to note is that the first part of the file name is different to prior versions of .NET Core (*MyNamespace* instead of *MyProject*).</span></span>

> [!NOTE]
> <span data-ttu-id="017a3-113">Pokud máte `LogicalName` metadata, `ManifestResourceName` nebo `DependentUpon` zadaná pro `EmbeddedResource` položku v souboru projektu, pak tato změna nemá vliv na daný soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="017a3-113">If you have `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata specified on an `EmbeddedResource` item in the project file, then this change does not affect that resource file.</span></span>

<span data-ttu-id="017a3-114">Tato Průlomová změna byla představena s přidáním `EmbeddedResourceUseDependentUponConvention` vlastnosti do projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="017a3-114">This breaking change was introduced with the addition of the `EmbeddedResourceUseDependentUponConvention` property to .NET Core projects.</span></span> <span data-ttu-id="017a3-115">Ve výchozím nastavení nejsou soubory prostředků explicitně uvedeny v souboru projektu .NET Core, takže nemají žádná `DependentUpon` metadata pro určení způsobu pojmenování vygenerovaného souboru *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="017a3-115">By default, resource files aren't explicitly listed in a .NET Core project file, so they have no `DependentUpon` metadata to specify how to name the generated *.resources* file.</span></span> <span data-ttu-id="017a3-116">Pokud `EmbeddedResourceUseDependentUponConvention` je nastaven na `true` , což je výchozí, MSBuild hledá umístěný zdrojový soubor a z něj extrahuje obor názvů a název třídy.</span><span class="sxs-lookup"><span data-stu-id="017a3-116">When `EmbeddedResourceUseDependentUponConvention` is set to `true`, which is the default, MSBuild looks for a colocated source file and extracts a namespace and class name from that file.</span></span> <span data-ttu-id="017a3-117">Pokud nastavíte `EmbeddedResourceUseDependentUponConvention` na `false` , nástroj MSBuild vygeneruje název manifestu podle předchozího chování, které kombinuje `RootNamespace` a relativní cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="017a3-117">If you set `EmbeddedResourceUseDependentUponConvention` to `false`, MSBuild generates the manifest name according to the previous behavior, which combines `RootNamespace` and the relative file path.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="017a3-118">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="017a3-118">Recommended action</span></span>

<span data-ttu-id="017a3-119">Ve většině případů není nutná žádná akce v rámci vývojáře a vaše aplikace by měla fungovat i nadále.</span><span class="sxs-lookup"><span data-stu-id="017a3-119">In most cases, no action is required on the part of the developer, and your app should continue to work.</span></span> <span data-ttu-id="017a3-120">Pokud však tato změna poškodí vaši aplikaci, můžete:</span><span class="sxs-lookup"><span data-stu-id="017a3-120">However, if this change breaks your app, you can either:</span></span>

- <span data-ttu-id="017a3-121">Změňte kód tak, aby očekával nový název manifestu.</span><span class="sxs-lookup"><span data-stu-id="017a3-121">Change your code to expect the new manifest name.</span></span>

- <span data-ttu-id="017a3-122">Odsouhlasit nové zásady vytváření názvů nastavením `EmbeddedResourceUseDependentUponConvention` na `false` v souboru projektu</span><span class="sxs-lookup"><span data-stu-id="017a3-122">Opt out of the new naming convention by setting `EmbeddedResourceUseDependentUponConvention` to `false` in your project file.</span></span>

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="017a3-123">Kategorie</span><span class="sxs-lookup"><span data-stu-id="017a3-123">Category</span></span>

<span data-ttu-id="017a3-124">MSBuild</span><span class="sxs-lookup"><span data-stu-id="017a3-124">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="017a3-125">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="017a3-125">Affected APIs</span></span>

<span data-ttu-id="017a3-126">–</span><span class="sxs-lookup"><span data-stu-id="017a3-126">N/A</span></span>
