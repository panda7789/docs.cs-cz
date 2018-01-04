---
title: "Model rozšiřitelnosti .NET core rozhraní příkazového řádku"
description: "Zjistěte, jak můžete rozšířit nástroje rozhraní příkazového řádku (CLI)."
keywords: "Rozhraní příkazového řádku, rozšiřitelnosti, vlastní příkazy, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fffc3400-aeb9-4c07-9fea-83bc8dbdcbf3
ms.workload: dotnetcore
ms.openlocfilehash: 0d273510903c888f3212a57f4c28b118b73cab5c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-cli-tools-extensibility-model"></a><span data-ttu-id="7476e-104">Model rozšiřitelnosti nástrojů .NET core rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="7476e-104">.NET Core CLI tools extensibility model</span></span>

<span data-ttu-id="7476e-105">Tento dokument popisuje různé způsoby můžete rozšířit nástroje .NET Core rozhraní příkazového řádku (CLI) a popisují scénáře, které jednotka každém z nich.</span><span class="sxs-lookup"><span data-stu-id="7476e-105">This document covers the different ways you can extend the .NET Core Command-line Interface (CLI) tools and explain the scenarios that drive each one of them.</span></span>
<span data-ttu-id="7476e-106">Uvidíte, jak používat nástroje a také jak vytvářet různé typy nástroje.</span><span class="sxs-lookup"><span data-stu-id="7476e-106">You'll see how to consume the tools as well as how to build the different types of tools.</span></span>

## <a name="how-to-extend-cli-tools"></a><span data-ttu-id="7476e-107">Postup rozšíření nástrojů příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="7476e-107">How to extend CLI tools</span></span>
<span data-ttu-id="7476e-108">Nástroje příkazového řádku lze rozšířit třemi hlavními způsoby:</span><span class="sxs-lookup"><span data-stu-id="7476e-108">The CLI tools can be extended in three main ways:</span></span>

1. [<span data-ttu-id="7476e-109">Pomocí balíčků NuGet při jednotlivých projektů</span><span class="sxs-lookup"><span data-stu-id="7476e-109">Via NuGet packages on a per-project basis</span></span>](#per-project-based-extensibility)

  <span data-ttu-id="7476e-110">Nástroje pro projekt jsou obsažené v kontextu projektu, ale umožňují snadno instalace prostřednictvím obnovení.</span><span class="sxs-lookup"><span data-stu-id="7476e-110">Per-project tools are contained within the project's context, but they allow easy installation through restoration.</span></span>

2. [<span data-ttu-id="7476e-111">Pomocí balíčků NuGet s vlastní cíle</span><span class="sxs-lookup"><span data-stu-id="7476e-111">Via NuGet packages with custom targets</span></span>](#custom-targets)

  <span data-ttu-id="7476e-112">Vlastní cíle umožňují snadno rozšířit procesu sestavení vlastní úlohy.</span><span class="sxs-lookup"><span data-stu-id="7476e-112">Custom targets allow you to easily extend the build process with custom tasks.</span></span>

3. [<span data-ttu-id="7476e-113">Prostřednictvím systémové cesty</span><span class="sxs-lookup"><span data-stu-id="7476e-113">Via the system's PATH</span></span>](#path-based-extensibility)

  <span data-ttu-id="7476e-114">Na základě cesty nástroje jsou vhodné pro obecné, mezi projekty nástroje, které lze použít na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="7476e-114">PATH-based tools are good for general, cross-project tools that are usable on a single machine.</span></span>

<span data-ttu-id="7476e-115">Tři rozšiřitelnost mechanismy uvedených výše se nevylučují.</span><span class="sxs-lookup"><span data-stu-id="7476e-115">The three extensibility mechanisms outlined above are not exclusive.</span></span> <span data-ttu-id="7476e-116">Můžete použít jednu, nebo všechny, nebo jejich kombinaci.</span><span class="sxs-lookup"><span data-stu-id="7476e-116">You can use one, or all, or a combination of them.</span></span> <span data-ttu-id="7476e-117">Které z nich vybrat závislá převážně na cíl, který se pokoušíte dosáhnout s rozšíření.</span><span class="sxs-lookup"><span data-stu-id="7476e-117">Which one to pick depends largely on the goal you are trying to achieve with your extension.</span></span>

## <a name="per-project-based-extensibility"></a><span data-ttu-id="7476e-118">Rozšiřitelnost na základě za projektů</span><span class="sxs-lookup"><span data-stu-id="7476e-118">Per-project based extensibility</span></span>
<span data-ttu-id="7476e-119">Projekt nástroje jsou [nasazení závislé na framework](../deploying/index.md#framework-dependent-deployments-fdd) , distribuované jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="7476e-119">Per-project tools are [framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) that are distributed as NuGet packages.</span></span> <span data-ttu-id="7476e-120">Nástroje jsou dostupné jenom v kontextu projektu, který odkazuje na jejich a pro které jsou obnoveny.</span><span class="sxs-lookup"><span data-stu-id="7476e-120">Tools are only available in the context of the project that references them and for which they are restored.</span></span> <span data-ttu-id="7476e-121">Volání mimo kontext projektu (například mimo adresář, který obsahuje projekt) se nezdaří, protože příkaz nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="7476e-121">Invocation outside of the context of the project (for example, outside of the directory that contains the project) will fail because the command cannot be found.</span></span>

<span data-ttu-id="7476e-122">Tyto nástroje jsou ideální pro servery sestavení, protože nic mimo souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="7476e-122">These tools are perfect for build servers, since nothing outside of the project file is needed.</span></span> <span data-ttu-id="7476e-123">Spustí proces sestavení obnovit pro projekt sestavení a nástroje bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7476e-123">The build process runs restore for the project it builds and tools will be available.</span></span> <span data-ttu-id="7476e-124">Jazyk projektech, jako jsou F # jsou také v této kategorii, vzhledem k tomu, že každý projekt lze zapsat pouze v jedné konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="7476e-124">Language projects, such as F#, are also in this category since each project can only be written in one specific language.</span></span>

<span data-ttu-id="7476e-125">Tento model rozšiřitelnosti navíc poskytuje podporu pro vytvoření nástrojů, které potřebují přístup k integrovaný výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="7476e-125">Finally, this extensibility model provides support for creation of tools that need access to the built output of the project.</span></span> <span data-ttu-id="7476e-126">Pro instanci nástroje pro v různých zobrazení syntaxe Razor [ASP.NET](https://www.asp.net/) do této kategorie patří aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="7476e-126">For instance, various Razor view tools in [ASP.NET](https://www.asp.net/) MVC applications fall into this category.</span></span>

### <a name="consuming-per-project-tools"></a><span data-ttu-id="7476e-127">Použití nástroje pro projekt</span><span class="sxs-lookup"><span data-stu-id="7476e-127">Consuming per-project tools</span></span>
<span data-ttu-id="7476e-128">Využívání těchto nástrojů vyžaduje můžete přidat `<DotNetCliToolReference>` element se v souboru projektu pro jednotlivé nástroje, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="7476e-128">Consuming these tools requires you to add a `<DotNetCliToolReference>` element to your project file for each tool you want to use.</span></span> <span data-ttu-id="7476e-129">Uvnitř `<DotNetCliToolReference>` elementu odkazují na balíček, ve které tento nástroj se nachází a zadejte verzi budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="7476e-129">Inside the `<DotNetCliToolReference>` element, you reference the package in which the tool resides and specify the version you need.</span></span> <span data-ttu-id="7476e-130">Po spuštění [ `dotnet restore` ](dotnet-restore.md), nástroje a jeho závislosti jsou obnoveny.</span><span class="sxs-lookup"><span data-stu-id="7476e-130">After running [`dotnet restore`](dotnet-restore.md), the tool and its dependencies are restored.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="7476e-131">Nástroje, které je potřeba načíst výstup sestavení projektu pro spuštění je obvykle jiné závislost, která je uvedena pod regulární závislosti v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="7476e-131">For tools that need to load the build output of the project for execution, there is usually another dependency which is listed under the regular dependencies in the project file.</span></span> <span data-ttu-id="7476e-132">Vzhledem k tomu, že rozhraní příkazového řádku používá MSBuild jako jeho modul sestavení, doporučujeme, aby tyto části nástroje pro zapsání jako vlastní MSBuild [cíle](/visualstudio/msbuild/msbuild-targets) a [úlohy](/visualstudio/msbuild/msbuild-tasks), protože se pak může trvat část v celkovém procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="7476e-132">Since CLI uses MSBuild as its build engine, we recommend that these parts of the tool be written as custom MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and [tasks](/visualstudio/msbuild/msbuild-tasks), since they can then take part in the overall build process.</span></span> <span data-ttu-id="7476e-133">Také můžete získat všech dat snadno vytvořený prostřednictvím sestavení, jako je například umístění výstupní soubory aktuální konfiguraci sestavuje atd. Všechny tyto informace k sadu vlastnosti nástroje MSBuild, které lze číst z žádné cíle.</span><span class="sxs-lookup"><span data-stu-id="7476e-133">Also, they can get any and all data easily that is produced via the build, such as the location of the output files, the current configuration being built, etc. All this information becomes a set of MSBuild properties that can be read from any target.</span></span> <span data-ttu-id="7476e-134">Uvidíte, jak přidat vlastní cíl pomocí nástroje NuGet později v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7476e-134">You can see how to add a custom target using NuGet later in this document.</span></span>

<span data-ttu-id="7476e-135">Pojďme si příklad jednoduchého nástroje jen nástroje pro přidání na jednoduchý projekt.</span><span class="sxs-lookup"><span data-stu-id="7476e-135">Let's review an example of adding a simple tools-only tool to a simple project.</span></span> <span data-ttu-id="7476e-136">Zadaný příkaz příklad názvem `dotnet-api-search` , které umožňuje hledat prostřednictvím balíčky NuGet pro rozhraní API zadaná, zde je souboru projektu konzolové aplikace, který používá tohoto nástroje:</span><span class="sxs-lookup"><span data-stu-id="7476e-136">Given an example command called `dotnet-api-search` that allows you to search through the NuGet packages for the specified API, here is a console application's project file that uses that tool:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="7476e-137">`<DotNetCliToolReference>` Element strukturovaná podobně jako `<PackageReference>` elementu.</span><span class="sxs-lookup"><span data-stu-id="7476e-137">The `<DotNetCliToolReference>` element is structured in a similar way as the `<PackageReference>` element.</span></span> <span data-ttu-id="7476e-138">Musí být schopni obnovit ID balíčku balíčku, který obsahuje nástroje a její verzi.</span><span class="sxs-lookup"><span data-stu-id="7476e-138">It needs the package ID of the package containing the tool and its version to be able to restore.</span></span>

### <a name="building-tools"></a><span data-ttu-id="7476e-139">Nástroje pro sestavení</span><span class="sxs-lookup"><span data-stu-id="7476e-139">Building tools</span></span>
<span data-ttu-id="7476e-140">Jak je uvedeno, nástroje jsou právě přenosné konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="7476e-140">As mentioned, tools are just portable console applications.</span></span> <span data-ttu-id="7476e-141">Nástroje sestavení, jako by sestavení jiných konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="7476e-141">You build tools as you would build any other console application.</span></span>
<span data-ttu-id="7476e-142">Když ho vytvoříte, můžete použít [ `dotnet pack` ](dotnet-pack.md) příkaz k vytvoření balíčku NuGet (souboru .nupkg), který obsahuje kód, informace o jeho závislé součásti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="7476e-142">After you build it, you use the [`dotnet pack`](dotnet-pack.md) command to create a NuGet package (.nupkg file) that contains your code, information about its dependencies, and so on.</span></span> <span data-ttu-id="7476e-143">Můžete přiřadit libovolný název balíčku, ale aplikace uvnitř nástroj Skutečná binární, má tak, aby odpovídala konvence `dotnet-<command>` v pořadí pro `dotnet` být schopni ji použít.</span><span class="sxs-lookup"><span data-stu-id="7476e-143">You can give any name to the package, but the application inside, the actual tool binary, has to conform to the convention of `dotnet-<command>` in order for `dotnet` to be able to invoke it.</span></span>

> [!NOTE]
> <span data-ttu-id="7476e-144">V RC3 předběžné verze nástroje příkazového řádku .NET Core `dotnet pack` příkaz měl chyb, která způsobila, že `runtime.config.json` nesmí být zabalena pomocí nástroje.</span><span class="sxs-lookup"><span data-stu-id="7476e-144">In pre-RC3 versions of the .NET Core command-line tools, the `dotnet pack` command had a bug that caused the `runtime.config.json` to not be packed with the tool.</span></span> <span data-ttu-id="7476e-145">Postrádá tohoto souboru za následek chyby za běhu.</span><span class="sxs-lookup"><span data-stu-id="7476e-145">Lacking that file results in errors at runtime.</span></span> <span data-ttu-id="7476e-146">Pokud narazíte na toto chování, nezapomeňte aktualizovat na nejnovější nástroje a potom `dotnet pack` znovu.</span><span class="sxs-lookup"><span data-stu-id="7476e-146">If you encounter this behavior, be sure to update to the latest tooling and try the `dotnet pack` again.</span></span>

<span data-ttu-id="7476e-147">Vzhledem k tomu, že jsou nástroje přenosné aplikace, musí mít uživatel využívají nástroj verzi knihovny .NET Core, které nástroj byl sestaven proti, aby bylo možné spustit nástroj.</span><span class="sxs-lookup"><span data-stu-id="7476e-147">Since tools are portable applications, the user consuming the tool must have the version of the .NET Core libraries that the tool was built against in order to run the tool.</span></span> <span data-ttu-id="7476e-148">Žádné další závislosti, používá nástroj a že není zahrnutá do knihovny .NET Core je obnovena a uložena v mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="7476e-148">Any other dependency that the tool uses and that is not contained within the .NET Core libraries is restored and placed in the NuGet cache.</span></span> <span data-ttu-id="7476e-149">Nástroj pro celý se proto spustit pomocí sestavení z knihoven .NET Core a také sestavení z mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="7476e-149">The entire tool is, therefore, run using the assemblies from the .NET Core libraries as well as assemblies from the NuGet cache.</span></span>

<span data-ttu-id="7476e-150">Tyto druhy nástroje mít graf závislostí, který je zcela oddělenou z grafu závislostí projektu, který používá.</span><span class="sxs-lookup"><span data-stu-id="7476e-150">These kinds of tools have a dependency graph that is completely separate from the dependency graph of the project that uses them.</span></span> <span data-ttu-id="7476e-151">Proces obnovení nejprve obnoví závislosti projektu a potom obnoví všechny nástroje a jejich závislosti.</span><span class="sxs-lookup"><span data-stu-id="7476e-151">The restore process first restores the project's dependencies and then restores each of the tools and their dependencies.</span></span>

<span data-ttu-id="7476e-152">Můžete najít bohatší příklady a různé kombinace to [úložišti .NET Core rozhraní příkazového řádku](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestProjects).</span><span class="sxs-lookup"><span data-stu-id="7476e-152">You can find richer examples and different combinations of this in the [.NET Core CLI repo](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestProjects).</span></span>
<span data-ttu-id="7476e-153">Můžete také zjistit [implementace nástroje používané](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestPackages) ve stejném úložišti.</span><span class="sxs-lookup"><span data-stu-id="7476e-153">You can also see the [implementation of tools used](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestPackages) in the same repo.</span></span>

### <a name="custom-targets"></a><span data-ttu-id="7476e-154">Vlastní cíle</span><span class="sxs-lookup"><span data-stu-id="7476e-154">Custom targets</span></span>
<span data-ttu-id="7476e-155">NuGet má schopnost [balíček vlastní MSBuild cíle a soubory props](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="7476e-155">NuGet has the capability to [package custom MSBuild targets and props files](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span></span> <span data-ttu-id="7476e-156">S přechodem .NET Core rozhraní příkazového řádku nástroje pro použití nástroje MSBuild shodný mechanismus rozšiřitelnosti teď vztahují na projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7476e-156">With the move of the .NET Core CLI tools to use MSBuild, the same mechanism of extensibility now applies to .NET Core projects.</span></span> <span data-ttu-id="7476e-157">Tento typ rozšíření by použijte, pokud chcete rozšířit procesu sestavení nebo pokud chcete získat přístup k žádnému artefaktů v procesu sestavení, jako jsou například generované soubory, nebo chcete prohlédnout konfiguraci, pod kterým je volána sestavení , atd.</span><span class="sxs-lookup"><span data-stu-id="7476e-157">You would use this type of extensibility when you want to extend the build process, or when you want to access any of the artifacts in the build process, such as generated files, or you want to inspect the configuration under which the build is invoked, etc.</span></span>

<span data-ttu-id="7476e-158">V následujícím příkladu se zobrazí cílové složky projektu soubor pomocí `csproj` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="7476e-158">In the following example, you can see the target's project file using the `csproj` syntax.</span></span> <span data-ttu-id="7476e-159">Tím se nastaví [ `dotnet pack` ](dotnet-pack.md) příkaz co do balíčku, umístění souborů cíle, jakož i sestavení do *sestavení* složky uvnitř balíčku.</span><span class="sxs-lookup"><span data-stu-id="7476e-159">This instructs the [`dotnet pack`](dotnet-pack.md) command what to package, placing the targets files as well as the assemblies into the *build* folder inside the package.</span></span> <span data-ttu-id="7476e-160">Upozornění `<ItemGroup>` element, který má `Label` vlastnost nastavena na hodnotu `dotnet pack instructions`, a cíl definován pod ní.</span><span class="sxs-lookup"><span data-stu-id="7476e-160">Notice the `<ItemGroup>` element that has the `Label` property set to `dotnet pack instructions`, and the Target defined beneath it.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="7476e-161">Použití vlastní cíle se provádí zadáním `<PackageReference>` který odkazuje na balíček a jeho verze uvnitř projekt, který je právě rozšířeno.</span><span class="sxs-lookup"><span data-stu-id="7476e-161">Consuming custom targets is done by providing a `<PackageReference>` that points to the package and its version inside the project that is being extended.</span></span> <span data-ttu-id="7476e-162">Na rozdíl od nástroje získat balíček vlastní cíle zahrnut do uzavření závislostí náročné projektu.</span><span class="sxs-lookup"><span data-stu-id="7476e-162">Unlike the tools, the custom targets package does get included into the consuming project's dependency closure.</span></span>

<span data-ttu-id="7476e-163">Pomocí vlastních cíl závisí výhradně na tom, jak nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="7476e-163">Using the custom target depends solely on how you configure it.</span></span> <span data-ttu-id="7476e-164">Vzhledem k tomu, že je cíl MSBuild, může záviset na daný cíl, spusťte po jiný cíl a můžete také být vyvolána ručně pomocí `dotnet msbuild /t:<target-name>` příkaz.</span><span class="sxs-lookup"><span data-stu-id="7476e-164">Since it's an MSBuild target, it can depend on a given target, run after another target and can also be manually invoked using the `dotnet msbuild /t:<target-name>` command.</span></span>

<span data-ttu-id="7476e-165">Ale pokud chcete zajistit lepší prostředí pro uživatele, můžete kombinovat za projektu nástroje a vlastní cíle.</span><span class="sxs-lookup"><span data-stu-id="7476e-165">However, if you want to provide a better user experience to your users, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="7476e-166">V tomto scénáři nástroj projekt by v podstatě právě přijmout ať parametry nejsou potřebné a který se promítne do požadované [ `dotnet msbuild` ](dotnet-msbuild.md) volání, které by provést cíl.</span><span class="sxs-lookup"><span data-stu-id="7476e-166">In this scenario, the per-project tool would essentially just accept whatever needed parameters and would translate that into the required [`dotnet msbuild`](dotnet-msbuild.md) invocation that would execute the target.</span></span> <span data-ttu-id="7476e-167">Uvidíte ukázku tento druh součinnosti na [ukázky MVP schůzce na nejvyšší úrovni 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) v úložišti [ `dotnet-packer` ](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projektu.</span><span class="sxs-lookup"><span data-stu-id="7476e-167">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

### <a name="path-based-extensibility"></a><span data-ttu-id="7476e-168">Na základě CESTU rozšíření</span><span class="sxs-lookup"><span data-stu-id="7476e-168">PATH-based extensibility</span></span>
<span data-ttu-id="7476e-169">Na základě cesty rozšíření se obvykle používá pro vývoj počítače kde je nutné nástroj, který koncepčně obsahuje více než jeden projekt.</span><span class="sxs-lookup"><span data-stu-id="7476e-169">PATH-based extensibility is usually used for development machines where you need a tool that conceptually covers more than a single project.</span></span> <span data-ttu-id="7476e-170">Hlavní nevýhodou tento mechanismus rozšíření je, že jsou spojeny počítač kde nástroj existuje.</span><span class="sxs-lookup"><span data-stu-id="7476e-170">The main drawback of this extension mechanism is that it's tied to the machine where the tool exists.</span></span> <span data-ttu-id="7476e-171">Pokud budete potřebovat na jiném počítači, museli byste ji nasadit.</span><span class="sxs-lookup"><span data-stu-id="7476e-171">If you need it on another machine, you would have to deploy it.</span></span>

<span data-ttu-id="7476e-172">Tento vzor rozšiřitelnost rozhraní příkazového řádku sady nástrojů je velmi jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="7476e-172">This pattern of CLI toolset extensibility is very simple.</span></span> <span data-ttu-id="7476e-173">Jak je popsané v [.NET Core rozhraní příkazového řádku přehled](index.md), `dotnet` ovladač lze spustit všechny příkaz s názvem po `dotnet-<command>` konvence.</span><span class="sxs-lookup"><span data-stu-id="7476e-173">As covered in the [.NET Core CLI overview](index.md), `dotnet` driver can run any command that is named after the `dotnet-<command>` convention.</span></span> <span data-ttu-id="7476e-174">Výchozí logiku řešení nejprve sondy několika umístění a nakonec se vrátí do systému CESTU.</span><span class="sxs-lookup"><span data-stu-id="7476e-174">The default resolution logic first probes several locations and finally falls back to the system PATH.</span></span> <span data-ttu-id="7476e-175">Pokud požadovaný příkaz v systému cesta existuje a je binární soubor, který lze vyvolat, `dotnet` ovladač vyvolá.</span><span class="sxs-lookup"><span data-stu-id="7476e-175">If the requested command exists in the system PATH and is a binary that can be invoked, `dotnet` driver will invoke it.</span></span>

<span data-ttu-id="7476e-176">Soubor musí být spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="7476e-176">The file must be executable.</span></span> <span data-ttu-id="7476e-177">V systémech Unix, to všechno, co má nastaven bit spustit prostřednictvím znamená `chmod +x`.</span><span class="sxs-lookup"><span data-stu-id="7476e-177">On Unix systems, this means anything that has the execute bit set via `chmod +x`.</span></span> <span data-ttu-id="7476e-178">V systému Windows, můžete použít *cmd* soubory.</span><span class="sxs-lookup"><span data-stu-id="7476e-178">On Windows, you can use *cmd* files.</span></span>

<span data-ttu-id="7476e-179">Podívejme se na velmi jednoduché provedení nástroj "Hello World".</span><span class="sxs-lookup"><span data-stu-id="7476e-179">Let's take a look at the very simple implementation of a "Hello World" tool.</span></span> <span data-ttu-id="7476e-180">Budeme používat obě `bash` a `cmd` v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7476e-180">We will use both `bash` and `cmd` on Windows.</span></span>
<span data-ttu-id="7476e-181">Následující příkaz se ke konzole echo jednoduše "Hello World".</span><span class="sxs-lookup"><span data-stu-id="7476e-181">The following command will simply echo "Hello World" to the console.</span></span>

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

<span data-ttu-id="7476e-182">V systému macOS, můžeme uložit tento skript jako `dotnet-hello` a nastavit jeho spustitelné bitové s `chmod +x dotnet-hello`.</span><span class="sxs-lookup"><span data-stu-id="7476e-182">On macOS, we can save this script as `dotnet-hello` and set its executable bit with `chmod +x dotnet-hello`.</span></span> <span data-ttu-id="7476e-183">Pak můžeme vytvořit symbolický odkaz k němu v `/usr/local/bin` pomocí příkazu `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span><span class="sxs-lookup"><span data-stu-id="7476e-183">We can then create a symbolic link to it in `/usr/local/bin` using the command `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span></span> <span data-ttu-id="7476e-184">To bude možné volat pomocí příkazu `dotnet hello` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="7476e-184">This will make it possible to invoke the command using the `dotnet hello` syntax.</span></span>

<span data-ttu-id="7476e-185">V systému Windows, můžeme uložit tento skript jako `dotnet-hello.cmd` a umístí jej do umístění, které je v cestě systému (nebo jim ho přidat ke složce, která je již v cestě).</span><span class="sxs-lookup"><span data-stu-id="7476e-185">On Windows, we can save this script as `dotnet-hello.cmd` and put it in a location that is in a system path (or you can add it to a folder that is already in the path).</span></span> <span data-ttu-id="7476e-186">Poté můžete jednoduše použít `dotnet hello` pro spuštění tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="7476e-186">After this, you can just use `dotnet hello` to run this example.</span></span>
