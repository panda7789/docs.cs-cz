---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451880"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="dd7b8-101">Názvy souborů manifestu prostředků</span><span class="sxs-lookup"><span data-stu-id="dd7b8-101">Resource manifest file names</span></span>

<span data-ttu-id="dd7b8-102">Počínaje platformou .NET Core 3,0 se změnil název souboru manifestu generovaného manifestu.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dd7b8-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="dd7b8-103">Version introduced</span></span>

<span data-ttu-id="dd7b8-104">3.0</span><span class="sxs-lookup"><span data-stu-id="dd7b8-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="dd7b8-105">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="dd7b8-105">Change description</span></span>

<span data-ttu-id="dd7b8-106">Před rozhraním .NET Core 3,0 se při nastavení metadat [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) pro soubor prostředků ( *. resx*) v souboru projektu MSBuild vygeneroval název manifestu *Namespace. ClassName. Resources*.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="dd7b8-107">Pokud [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) nebyl nastaven, vygenerovaný název manifestu byl *obor názvů. ClassName. FolderPathRelativeToRoot. Culture. Resources*.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="dd7b8-108">Počínaje platformou .NET Core 3,0 platí, že pokud se soubor *. resx* nachází společně se zdrojovým souborem se stejným názvem, například v model Windows Forms aplikace, název manifestu prostředku je vygenerován z úplného názvu prvního typu ve zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="dd7b8-109">Například pokud je *Type.cs* společně umístěn s *Type. resx*, vygenerovaný název manifestu je Namespace. *ClassName. Resources*.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="dd7b8-110">Nicméně pokud upravíte kterýkoli z atributů vlastnosti `EmbeddedResource` souboru *. resx* , název souboru manifestu se může lišit:</span><span class="sxs-lookup"><span data-stu-id="dd7b8-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="dd7b8-111">Pokud je nastaven atribut `LogicalName` u vlastnosti `EmbeddedResource`, použije se tato hodnota jako název souboru manifestu prostředku.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="dd7b8-112">Příklady:</span><span class="sxs-lookup"><span data-stu-id="dd7b8-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="dd7b8-113">**Vygenerovaný název souboru manifestu prostředku**: *Příklady. Resources* (bez ohledu na název souboru *. resx* nebo jazykovou verzi nebo jiná metadata).</span><span class="sxs-lookup"><span data-stu-id="dd7b8-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="dd7b8-114">Pokud `LogicalName` není nastavena, ale atribut `ManifestResourceName` vlastnosti `EmbeddedResource` je nastaven, jeho hodnota se v kombinaci s příponou souboru *. Resources*používá jako název souboru manifestu prostředku.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="dd7b8-115">Příklady:</span><span class="sxs-lookup"><span data-stu-id="dd7b8-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="dd7b8-116">**Vygenerovaný název souboru manifestu prostředku**: *Příklady. Resources* nebo *SomeName.fr-fr. Resources*.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="dd7b8-117">Pokud předchozí pravidla neplatí a atribut `DependentUpon` elementu `EmbeddedResource` je nastaven na zdrojový soubor, v názvu souboru manifestu prostředků se použije název typu první třídy ve zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="dd7b8-118">Konkrétně název generovaného souboru je *Namespace. Classname\[. Culture]. Resources*.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="dd7b8-119">Příklady:</span><span class="sxs-lookup"><span data-stu-id="dd7b8-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="dd7b8-120">**Vygenerovaný název souboru manifestu prostředku**: *Namespace. ClassName. Resources* nebo *Namespace.ClassName.fr-fr. resources* (kde `Namespace.Classname` je název první třídy v *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="dd7b8-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="dd7b8-121">Pokud se předchozí pravidla nevztahují, `EmbeddedResourceUseDependentUponConvention` je `true` (výchozí pro .NET Core) a existuje zdrojový soubor, který se nachází v souboru *. resx* , který má stejný základní název souboru, pak je soubor *. resx* závislý na odpovídajícím zdrojovém souboru a vygenerovaný název je stejný jako v předchozím pravidle.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="dd7b8-122">Toto je pravidlo "výchozí nastavení" pro projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="dd7b8-123">Příklady:</span><span class="sxs-lookup"><span data-stu-id="dd7b8-123">Examples:</span></span>
  
  <span data-ttu-id="dd7b8-124">Soubory *myTypes.cs* a *myTypes. resx* nebo *myTypes.fr-fr. resx* existují ve stejné složce.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="dd7b8-125">**Vygenerovaný název souboru manifestu prostředku**: *Namespace. ClassName. Resources* nebo *Namespace.ClassName.fr-fr. resources* (kde `Namespace.Classname` je název první třídy v *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="dd7b8-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>
    
- <span data-ttu-id="dd7b8-126">Pokud žádné z předchozích pravidel neplatí, název souboru manifestu prostředku je *RootNamespace. RelativePathWithDotsForSlashes.\[culture.] prostředky*.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="dd7b8-127">Relativní cesta je hodnota atributu `Link` elementu `EmbeddedResource`, pokud je nastavena.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="dd7b8-128">V opačném případě je relativní cesta hodnotou atributu `Identity` `EmbeddedResource` elementu.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="dd7b8-129">V aplikaci Visual Studio se jedná o cestu z kořenového adresáře projektu k souboru v Průzkumník řešení.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dd7b8-130">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="dd7b8-130">Recommended action</span></span>

<span data-ttu-id="dd7b8-131">Pokud nejste spokojeni s generovanými názvy manifestů, můžete:</span><span class="sxs-lookup"><span data-stu-id="dd7b8-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="dd7b8-132">Upravte metadata souboru prostředků podle některého z dříve popsaných pravidel pojmenování.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="dd7b8-133">Nastavte `EmbeddedResourceUseDependentUponConvention` pro `false` v souboru projektu tak, aby se odhlásila od zcela nové smlouvy:</span><span class="sxs-lookup"><span data-stu-id="dd7b8-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="dd7b8-134">Pokud jsou k dispozici atributy `LogicalName` nebo `ManifestResourceName`, budou jejich hodnoty nadále použity pro vygenerovaný název souboru.</span><span class="sxs-lookup"><span data-stu-id="dd7b8-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="dd7b8-135">Kategorie</span><span class="sxs-lookup"><span data-stu-id="dd7b8-135">Category</span></span>

<span data-ttu-id="dd7b8-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="dd7b8-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dd7b8-137">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="dd7b8-137">Affected APIs</span></span>

<span data-ttu-id="dd7b8-138">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="dd7b8-138">N/A</span></span>
