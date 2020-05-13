---
title: Jak nástroj MSBuild generuje názvy souborů manifestu
description: Popisuje faktory, které ovlivňují název názvu souboru manifestu prostředku, který je generován nástrojem MSBuild v době kompilace.
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 383bf6a077b0631e70ddaa4721b20e992127a73c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83232324"
---
# <a name="how-resource-manifest-files-are-named"></a><span data-ttu-id="b612e-103">Jak se nazývají soubory manifestu prostředků</span><span class="sxs-lookup"><span data-stu-id="b612e-103">How resource manifest files are named</span></span>

<span data-ttu-id="b612e-104">Když nástroj MSBuild zkompiluje projekt .NET Core, soubory prostředků XML, které mají příponu souboru *. resx* , jsou převedeny do binárních souborů *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="b612e-104">When MSBuild compiles a .NET Core project, XML resource files, which have the *.resx* file extension, are converted into binary *.resources* files.</span></span> <span data-ttu-id="b612e-105">Binární soubory jsou vloženy do výstupu kompilátoru a lze je číst pomocí <xref:System.Resources.ResourceManager> .</span><span class="sxs-lookup"><span data-stu-id="b612e-105">The binary files are embedded into the output of the compiler and can be read by the <xref:System.Resources.ResourceManager>.</span></span> <span data-ttu-id="b612e-106">Tento článek popisuje, jak nástroj MSBuild zvolí název pro každý soubor *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="b612e-106">This article describes how MSBuild chooses a name for each *.resources* file.</span></span>

> [!TIP]
> <span data-ttu-id="b612e-107">Pokud explicitně přidáte položku prostředku do souboru projektu a je také [zahrnutá ve výchozím nastavení include globy pro .NET Core](../project-sdk/overview.md#default-compilation-includes), zobrazí se chyba buildu.</span><span class="sxs-lookup"><span data-stu-id="b612e-107">If you explicitly add a resource item to your project file, and it's also [included with the default include globs for .NET Core](../project-sdk/overview.md#default-compilation-includes), you will get a build error.</span></span> <span data-ttu-id="b612e-108">Chcete-li soubory prostředků zahrnout jako `EmbeddedResource` položky ručně, nastavte `EnableDefaultEmbeddedResourceItems` vlastnost na hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="b612e-108">To manually include resource files as `EmbeddedResource` items, set the `EnableDefaultEmbeddedResourceItems` property to false.</span></span>

## <a name="default-name"></a><span data-ttu-id="b612e-109">Výchozí název</span><span class="sxs-lookup"><span data-stu-id="b612e-109">Default name</span></span>

<span data-ttu-id="b612e-110">V rozhraní .NET Core 3,0 a novějším je výchozí název pro manifest prostředku použit, pokud jsou splněny obě následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="b612e-110">In .NET Core 3.0 and later, the default name for a resource manifest is used when both of the following conditions are met:</span></span>

- <span data-ttu-id="b612e-111">Soubor prostředků není explicitně obsažen v souboru projektu jako `EmbeddedResource` položka s `LogicalName` `ManifestResourceName` `DependentUpon` metadaty, nebo.</span><span class="sxs-lookup"><span data-stu-id="b612e-111">The resource file is not explicitly included in the project file as an `EmbeddedResource` item with `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata.</span></span>
- <span data-ttu-id="b612e-112">`EmbeddedResourceUseDependentUponConvention`Vlastnost není nastavena na hodnotu `false` v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="b612e-112">The `EmbeddedResourceUseDependentUponConvention` property is not set to `false` in the project file.</span></span> <span data-ttu-id="b612e-113">Ve výchozím nastavení je tato vlastnost nastavena na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="b612e-113">By default, this property is set to `true`.</span></span> <span data-ttu-id="b612e-114">Další informace najdete v tématu [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span><span class="sxs-lookup"><span data-stu-id="b612e-114">For more information, see [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span></span>

<span data-ttu-id="b612e-115">Pokud se soubor prostředků nachází společně se zdrojovým souborem (*. cs* nebo *. vb*) se stejným kořenovým názvem souboru, bude pro název souboru manifestu použit úplný název prvního typu, který je definován ve zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="b612e-115">If the resource file is colocated with a source file (*.cs* or *.vb*) of the same root file name, the full name of the first type that's defined in the source file is used for the manifest file name.</span></span> <span data-ttu-id="b612e-116">Například pokud `MyNamespace.Form1` je první typ definovaný v *Form1.cs*a *Form1.cs* se nachází v souboru *Form1. resx*, vygenerovaný název manifestu pro tento soubor prostředků je *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="b612e-116">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, and *Form1.cs* is colocated with *Form1.resx*, the generated manifest name for that resource file is *MyNamespace.Form1.resources*.</span></span>

## <a name="logicalname-metadata"></a><span data-ttu-id="b612e-117">Logická metadata</span><span class="sxs-lookup"><span data-stu-id="b612e-117">LogicalName metadata</span></span>

<span data-ttu-id="b612e-118">Pokud je soubor prostředků explicitně obsažen v souboru projektu jako `EmbeddedResource` položka s `LogicalName` metadaty, `LogicalName` použije se jako název manifestu hodnota.</span><span class="sxs-lookup"><span data-stu-id="b612e-118">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `LogicalName` metadata, the `LogicalName` value is used as the manifest name.</span></span> <span data-ttu-id="b612e-119">`LogicalName`má přednost před všemi ostatními metadaty nebo nastavením.</span><span class="sxs-lookup"><span data-stu-id="b612e-119">`LogicalName` takes precedence over any other metadata or setting.</span></span>

<span data-ttu-id="b612e-120">Například název manifestu pro soubor prostředků, který je definován v následujícím fragmentu souboru projektu, je příkladem *. Resources*.</span><span class="sxs-lookup"><span data-stu-id="b612e-120">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

<span data-ttu-id="b612e-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="b612e-121">-or-</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a><span data-ttu-id="b612e-122">Metadata ManifestResourceName</span><span class="sxs-lookup"><span data-stu-id="b612e-122">ManifestResourceName metadata</span></span>

<span data-ttu-id="b612e-123">Pokud je soubor prostředků explicitně zahrnutý v souboru projektu jako `EmbeddedResource` položka s `ManifestResourceName` metadaty (a chybí `LogicalName` ), `ManifestResourceName` použije se jako název souboru manifestu hodnota v kombinaci s příponou *. Resources.*</span><span class="sxs-lookup"><span data-stu-id="b612e-123">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `ManifestResourceName` metadata (and `LogicalName` is absent), the `ManifestResourceName` value, combined with the file extension *.resources*, is used as the manifest file name.</span></span>

<span data-ttu-id="b612e-124">Například název manifestu pro soubor prostředků, který je definován v následujícím fragmentu souboru projektu, je příkladem *. Resources*.</span><span class="sxs-lookup"><span data-stu-id="b612e-124">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

<span data-ttu-id="b612e-125">Název manifestu pro soubor prostředků, který je definován v následujícím fragmentu souboru projektu, je *SomeName.fr-fr. Resources*.</span><span class="sxs-lookup"><span data-stu-id="b612e-125">The manifest name for the resource file that's defined in the following project file snippet is *SomeName.fr-FR.resources*.</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a><span data-ttu-id="b612e-126">Metadata DependentUpon</span><span class="sxs-lookup"><span data-stu-id="b612e-126">DependentUpon metadata</span></span>

<span data-ttu-id="b612e-127">Pokud je soubor prostředků explicitně obsažen v souboru projektu jako `EmbeddedResource` položka s `DependentUpon` metadaty (a `LogicalName` `ManifestResourceName` chybí), informace ze zdrojového souboru definovaného pomocí `DependentUpon` se používají pro název souboru manifestu prostředku.</span><span class="sxs-lookup"><span data-stu-id="b612e-127">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `DependentUpon` metadata (and `LogicalName` and `ManifestResourceName` are absent), information from the source file defined by `DependentUpon` is used for the resource manifest file name.</span></span> <span data-ttu-id="b612e-128">Konkrétně název prvního typu, který je definován ve zdrojovém souboru, se používá v názvu manifestu následujícím způsobem: *Namespace. ClassName \[ . Culture]. Resources*.</span><span class="sxs-lookup"><span data-stu-id="b612e-128">Specifically, the name of the first type that's defined in the source file is used in the manifest name as follows: *Namespace.Classname\[.Culture].resources*.</span></span>

<span data-ttu-id="b612e-129">Například název manifestu pro soubor prostředků, který je definován v následujícím fragmentu souboru projektu, je Namespace. *ClassName. Resources* (kde `Namespace.Classname` je první třída definovaná v *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="b612e-129">For example, the manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

<span data-ttu-id="b612e-130">Název manifestu pro soubor prostředků, který je definován v následujícím fragmentu souboru projektu, je *Namespace.ClassName.fr-fr. Resources* (kde `Namespace.Classname` je první třída definovaná v *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="b612e-130">The manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a><span data-ttu-id="b612e-131">Vlastnost EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="b612e-131">EmbeddedResourceUseDependentUponConvention property</span></span>

<span data-ttu-id="b612e-132">Pokud `EmbeddedResourceUseDependentUponConvention` je nastaven na hodnotu `false` v souboru projektu, každý název souboru manifestu prostředku je založen na kořenovém oboru názvů pro projekt a relativní cestu z kořene projektu k souboru *. resx* .</span><span class="sxs-lookup"><span data-stu-id="b612e-132">If `EmbeddedResourceUseDependentUponConvention` is set to `false` in the project file, each resource manifest file name is based off the root namespace for the project and the relative path from the project root to the *.resx* file.</span></span> <span data-ttu-id="b612e-133">Přesněji řečeno, vygenerovaný název souboru manifestu prostředku je *RootNamespace. RelativePathWithDotsForSlashes. \[ Culture.] prostředky*.</span><span class="sxs-lookup"><span data-stu-id="b612e-133">More specifically, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="b612e-134">To je také logika sloužící ke generování názvů manifestu ve verzích .NET Core starších než 3,0.</span><span class="sxs-lookup"><span data-stu-id="b612e-134">This is also the logic used to generate manifest names in .NET Core versions prior to 3.0.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="b612e-135">Pokud `RootNamespace` není definován, použije se výchozí název projektu.</span><span class="sxs-lookup"><span data-stu-id="b612e-135">If `RootNamespace` is not defined, it defaults to the project name.</span></span>
> - <span data-ttu-id="b612e-136">Pokud `LogicalName` `ManifestResourceName` `DependentUpon` jsou zadána metadata pro položku v souboru projektu, nebo jsou uvedena metadata `EmbeddedResource` , toto pravidlo pro pojmenovávání neplatí pro tento soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="b612e-136">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item in the project file, this naming rule does not apply to that resource file.</span></span>

## <a name="see-also"></a><span data-ttu-id="b612e-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="b612e-137">See also</span></span>

- [<span data-ttu-id="b612e-138">Jak funguje vytváření názvů prostředků manifestu</span><span class="sxs-lookup"><span data-stu-id="b612e-138">How Manifest Resource Naming Works</span></span>](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [<span data-ttu-id="b612e-139">Vlastnosti nástroje MSBuild pro projekty .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="b612e-139">MSBuild properties for .NET Core SDK projects</span></span>](../project-sdk/msbuild-props.md)
- [<span data-ttu-id="b612e-140">Nejnovější změny nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="b612e-140">MSBuild breaking changes</span></span>](../compatibility/msbuild.md)
