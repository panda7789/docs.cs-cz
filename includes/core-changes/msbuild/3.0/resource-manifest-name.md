---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968237"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="45ee3-101">Názvy souborů manifestu prostředků</span><span class="sxs-lookup"><span data-stu-id="45ee3-101">Resource manifest file names</span></span>

<span data-ttu-id="45ee3-102">Počínaje rozhraním .NET Core 3.0 byl změněn název souboru manifestu generovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="45ee3-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="45ee3-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="45ee3-103">Version introduced</span></span>

<span data-ttu-id="45ee3-104">3.0</span><span class="sxs-lookup"><span data-stu-id="45ee3-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="45ee3-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="45ee3-105">Change description</span></span>

<span data-ttu-id="45ee3-106">Před rozhraním .NET Core 3.0, kdy byla metadata [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) nastavena pro soubor prostředku (*.resx)* v souboru projektu MSBuild, byl vygenerovaný název manifestu *Namespace.Classname.resources*.</span><span class="sxs-lookup"><span data-stu-id="45ee3-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="45ee3-107">Pokud [dependentupon](/visualstudio/msbuild/common-msbuild-project-items#compile) nebyl nastaven, generovaný název manifestu byl *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span><span class="sxs-lookup"><span data-stu-id="45ee3-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="45ee3-108">Počínaje rozhraním .NET Core 3.0 je soubor *RESX* umístěn společně se stejným zdrojovým souborem, například v aplikacích windows forms, je název manifestu prostředků generován z úplného názvu prvního typu ve zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="45ee3-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="45ee3-109">Pokud je například *Type.cs* společně umístěn s *Type.resx*, je vygenerovaný název manifestu *Namespace.Classname.resources*.</span><span class="sxs-lookup"><span data-stu-id="45ee3-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="45ee3-110">Pokud však změníte některý z `EmbeddedResource` atributů vlastnosti souboru *Resx,* může se název generovaného souboru manifestu lišit:</span><span class="sxs-lookup"><span data-stu-id="45ee3-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="45ee3-111">Pokud `LogicalName` je atribut `EmbeddedResource` vlastnosti nastaven, tato hodnota se používá jako název souboru manifestu prostředku.</span><span class="sxs-lookup"><span data-stu-id="45ee3-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="45ee3-112">Příklady:</span><span class="sxs-lookup"><span data-stu-id="45ee3-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="45ee3-113">**Název souboru manifestu generovaného prostředku**: *SomeName.resources* (bez ohledu na název souboru *resx* nebo jazykovou verzi nebo jiná metadata).</span><span class="sxs-lookup"><span data-stu-id="45ee3-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="45ee3-114">Pokud `LogicalName` není nastavena, `ManifestResourceName` ale `EmbeddedResource` atribut na vlastnost je nastavena, jeho hodnota, v kombinaci s příponou *.resources*, se používá jako název souboru manifestu prostředku.</span><span class="sxs-lookup"><span data-stu-id="45ee3-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="45ee3-115">Příklady:</span><span class="sxs-lookup"><span data-stu-id="45ee3-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="45ee3-116">**Název souboru manifestu generovaného prostředku**: *SomeName.resources* nebo *SomeName.fr-FR.resources*.</span><span class="sxs-lookup"><span data-stu-id="45ee3-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="45ee3-117">Pokud předchozí pravidla neplatí a `DependentUpon` atribut `EmbeddedResource` prvku je nastaven na zdrojový soubor, použije se v názvu souboru manifestu prostředku název typu první třídy ve zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="45ee3-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="45ee3-118">Konkrétně je název generovaného souboru *\[Namespace.Classname . Jazyková verze].zdroje*.</span><span class="sxs-lookup"><span data-stu-id="45ee3-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="45ee3-119">Příklady:</span><span class="sxs-lookup"><span data-stu-id="45ee3-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="45ee3-120">**Název souboru manifestu generovaného prostředku**: *Namespace.Classname.resources* nebo *Namespace.Classname.fr-FR.resources* (kde `Namespace.Classname` je název první třídy v *MyTypes.cs).*</span><span class="sxs-lookup"><span data-stu-id="45ee3-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="45ee3-121">Pokud předchozí pravidla neplatí, `EmbeddedResourceUseDependentUponConvention` `true` je (výchozí pro .NET Core) a je zdrojový soubor spoluumístěný se souborem *.resx,* který má stejný název základního souboru, soubor *Resx* je závislý na odpovídajícím zdrojovém souboru a generovaný název je stejný jako v předchozím pravidle.</span><span class="sxs-lookup"><span data-stu-id="45ee3-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="45ee3-122">Toto je pravidlo "výchozí nastavení" pro projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45ee3-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="45ee3-123">Příklady:</span><span class="sxs-lookup"><span data-stu-id="45ee3-123">Examples:</span></span>
  
  <span data-ttu-id="45ee3-124">Soubory *MyTypes.cs* a *MyTypes.resx* nebo *MyTypes.fr-FR.resx* existují ve stejné složce.</span><span class="sxs-lookup"><span data-stu-id="45ee3-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="45ee3-125">**Název souboru manifestu generovaného prostředku**: *Namespace.Classname.resources* nebo *Namespace.Classname.fr-FR.resources* (kde `Namespace.Classname` je název první třídy v *MyTypes.cs).*</span><span class="sxs-lookup"><span data-stu-id="45ee3-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="45ee3-126">Pokud neplatí žádná z předchozích pravidel, je název souboru manifestu generovaného prostředku *RootNamespace.RelativePathWithDotsForSlashes.\[ Jazyková verze.] zdrojů*.</span><span class="sxs-lookup"><span data-stu-id="45ee3-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="45ee3-127">Relativní cesta je hodnota `Link` atributu `EmbeddedResource` prvku, pokud je nastavena.</span><span class="sxs-lookup"><span data-stu-id="45ee3-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="45ee3-128">V opačném případě relativní cesta `Identity` je hodnota `EmbeddedResource` atributu prvku.</span><span class="sxs-lookup"><span data-stu-id="45ee3-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="45ee3-129">V sadě Visual Studio se jedná o cestu z kořenového adresáře projektu k souboru v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="45ee3-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="45ee3-130">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="45ee3-130">Recommended action</span></span>

<span data-ttu-id="45ee3-131">Pokud nejste spokojeni s generovanými názvy manifestů, můžete:</span><span class="sxs-lookup"><span data-stu-id="45ee3-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="45ee3-132">Upravte metadata souboru prostředků podle jednoho z dříve popsaných pravidel pojmenování.</span><span class="sxs-lookup"><span data-stu-id="45ee3-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="45ee3-133">Chcete-li `EmbeddedResourceUseDependentUponConvention` se zcela odhlásit z nové konvence, nastavte `false` v souboru projektu možnost odhlásit se z nové konvence:</span><span class="sxs-lookup"><span data-stu-id="45ee3-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="45ee3-134">Pokud `LogicalName` jsou `ManifestResourceName` k dispozici atributy nebo, jejich hodnoty budou stále použity pro název generovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="45ee3-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="45ee3-135">Kategorie</span><span class="sxs-lookup"><span data-stu-id="45ee3-135">Category</span></span>

<span data-ttu-id="45ee3-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="45ee3-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="45ee3-137">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="45ee3-137">Affected APIs</span></span>

<span data-ttu-id="45ee3-138">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="45ee3-138">N/A</span></span>
