---
title: Model rozšíření rozhraní příkazového řádku .NET core
description: Zjistěte, jak můžete rozšířit nástroje rozhraní příkazového řádku (CLI).
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.openlocfilehash: a9cfebbeddbedc329432c805c5956b382a726a77
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45592059"
---
# <a name="net-core-cli-tools-extensibility-model"></a><span data-ttu-id="01e0a-103">Model rozšiřitelnosti nástrojů rozhraní příkazového řádku .NET core</span><span class="sxs-lookup"><span data-stu-id="01e0a-103">.NET Core CLI tools extensibility model</span></span>

<span data-ttu-id="01e0a-104">Tento dokument popisuje různé způsoby, můžete rozšířit nástroje .NET Core rozhraní příkazového řádku (CLI) a popisují scénáře, které řídí každém z nich.</span><span class="sxs-lookup"><span data-stu-id="01e0a-104">This document covers the different ways you can extend the .NET Core Command-line Interface (CLI) tools and explain the scenarios that drive each one of them.</span></span>
<span data-ttu-id="01e0a-105">Uvidíte jak používat nástroje, jakož i jak vytvářet různé typy nástrojů.</span><span class="sxs-lookup"><span data-stu-id="01e0a-105">You'll see how to consume the tools as well as how to build the different types of tools.</span></span>

## <a name="how-to-extend-cli-tools"></a><span data-ttu-id="01e0a-106">Rozšíření nástrojů rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="01e0a-106">How to extend CLI tools</span></span>
<span data-ttu-id="01e0a-107">Nástroje rozhraní příkazového řádku je možné rozšířit třemi hlavními způsoby:</span><span class="sxs-lookup"><span data-stu-id="01e0a-107">The CLI tools can be extended in three main ways:</span></span>

1. [<span data-ttu-id="01e0a-108">Prostřednictvím balíčků NuGet na základě jednotlivých projektů</span><span class="sxs-lookup"><span data-stu-id="01e0a-108">Via NuGet packages on a per-project basis</span></span>](#per-project-based-extensibility)

   <span data-ttu-id="01e0a-109">Nástroje na projektu jsou obsaženy v kontextu projektu, ale umožňují snadnou instalaci prostřednictvím obnovení.</span><span class="sxs-lookup"><span data-stu-id="01e0a-109">Per-project tools are contained within the project's context, but they allow easy installation through restoration.</span></span>

2. [<span data-ttu-id="01e0a-110">Prostřednictvím balíčků NuGet s vlastní cíle</span><span class="sxs-lookup"><span data-stu-id="01e0a-110">Via NuGet packages with custom targets</span></span>](#custom-targets)

   <span data-ttu-id="01e0a-111">Vlastní cíle vám umožní snadno rozšířit proces sestavení pomocí vlastní úlohy.</span><span class="sxs-lookup"><span data-stu-id="01e0a-111">Custom targets allow you to easily extend the build process with custom tasks.</span></span>

3. [<span data-ttu-id="01e0a-112">Prostřednictvím systémové cesty</span><span class="sxs-lookup"><span data-stu-id="01e0a-112">Via the system's PATH</span></span>](#path-based-extensibility)

   <span data-ttu-id="01e0a-113">Na základě cest nástroje jsou vhodné pro napříč projekty, obecné nástroje, které lze použít na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="01e0a-113">PATH-based tools are good for general, cross-project tools that are usable on a single machine.</span></span>

<span data-ttu-id="01e0a-114">Tyto tři mechanismy rozšíření uvedených výše se nevylučují.</span><span class="sxs-lookup"><span data-stu-id="01e0a-114">The three extensibility mechanisms outlined above are not exclusive.</span></span> <span data-ttu-id="01e0a-115">Můžete použít jednu nebo všechny, nebo jejich kombinaci.</span><span class="sxs-lookup"><span data-stu-id="01e0a-115">You can use one, or all, or a combination of them.</span></span> <span data-ttu-id="01e0a-116">Který se má vybrat závisí do značné míry na cíl, který se snažíte dosáhnout pomocí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="01e0a-116">Which one to pick depends largely on the goal you are trying to achieve with your extension.</span></span>

## <a name="per-project-based-extensibility"></a><span data-ttu-id="01e0a-117">Rozšíření na základě jednotlivých projektů</span><span class="sxs-lookup"><span data-stu-id="01e0a-117">Per-project based extensibility</span></span>
<span data-ttu-id="01e0a-118">Nástroje na projekt jsou [nasazení závisí na architektuře](../deploying/index.md#framework-dependent-deployments-fdd) , která se distribuují jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="01e0a-118">Per-project tools are [framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) that are distributed as NuGet packages.</span></span> <span data-ttu-id="01e0a-119">Nástroje jsou dostupné jenom v kontextu projektu, který na ně odkazuje, a u kterého se obnoví.</span><span class="sxs-lookup"><span data-stu-id="01e0a-119">Tools are only available in the context of the project that references them and for which they are restored.</span></span> <span data-ttu-id="01e0a-120">Volání mimo kontext projektu (například nachází mimo adresář, který obsahuje projekt) se nezdaří, protože příkaz nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="01e0a-120">Invocation outside of the context of the project (for example, outside of the directory that contains the project) will fail because the command cannot be found.</span></span>

<span data-ttu-id="01e0a-121">Tyto nástroje jsou ideální pro sestavovací servery, protože je potřeba nic mimo rámec souborů projektu.</span><span class="sxs-lookup"><span data-stu-id="01e0a-121">These tools are perfect for build servers, since nothing outside of the project file is needed.</span></span> <span data-ttu-id="01e0a-122">Spuštění procesu sestavení pro projekt ji obnovit sestavení a nástroje budou dostupné.</span><span class="sxs-lookup"><span data-stu-id="01e0a-122">The build process runs restore for the project it builds and tools will be available.</span></span> <span data-ttu-id="01e0a-123">Projekty jazyka, jako je například F #, jsou také v této kategorii, protože každý projekt lze zapsat pouze v jeden konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="01e0a-123">Language projects, such as F#, are also in this category since each project can only be written in one specific language.</span></span>

<span data-ttu-id="01e0a-124">Nakonec tento model rozšiřitelnosti poskytuje podporu pro vytváření nástrojů, které potřebují přístup k sestavení výstupu projektu.</span><span class="sxs-lookup"><span data-stu-id="01e0a-124">Finally, this extensibility model provides support for creation of tools that need access to the built output of the project.</span></span> <span data-ttu-id="01e0a-125">Například různých zobrazení Razor nástroje v [ASP.NET](https://www.asp.net/) do této kategorie patří aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="01e0a-125">For instance, various Razor view tools in [ASP.NET](https://www.asp.net/) MVC applications fall into this category.</span></span>

### <a name="consuming-per-project-tools"></a><span data-ttu-id="01e0a-126">Využívání projektů nástroje</span><span class="sxs-lookup"><span data-stu-id="01e0a-126">Consuming per-project tools</span></span>
<span data-ttu-id="01e0a-127">Využívání těchto nástrojů je potřeba přidat `<DotNetCliToolReference>` element do souboru projektu pro každý nástroj, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="01e0a-127">Consuming these tools requires you to add a `<DotNetCliToolReference>` element to your project file for each tool you want to use.</span></span> <span data-ttu-id="01e0a-128">Uvnitř `<DotNetCliToolReference>` elementu, odkazujte na balíček, ve kterém se nástroj nachází a určit verzi budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="01e0a-128">Inside the `<DotNetCliToolReference>` element, you reference the package in which the tool resides and specify the version you need.</span></span> <span data-ttu-id="01e0a-129">Po spuštění [ `dotnet restore` ](dotnet-restore.md), budou obnoveny nástroj a jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="01e0a-129">After running [`dotnet restore`](dotnet-restore.md), the tool and its dependencies are restored.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="01e0a-130">Pro nástroje, které je potřeba načíst výstupu sestavení projektu pro spuštění je obvykle další závislosti, která je uvedena pod regulární závislosti v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="01e0a-130">For tools that need to load the build output of the project for execution, there is usually another dependency which is listed under the regular dependencies in the project file.</span></span> <span data-ttu-id="01e0a-131">Jelikož rozhraní příkazového řádku používá jako jeho modul sestavení MSBuild, doporučujeme vám, že tyto části nástroje pro zapsání jako vlastní MSBuild [cíle](/visualstudio/msbuild/msbuild-targets) a [úlohy](/visualstudio/msbuild/msbuild-tasks), protože se pak můžou část v celkovém procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="01e0a-131">Since CLI uses MSBuild as its build engine, we recommend that these parts of the tool be written as custom MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and [tasks](/visualstudio/msbuild/msbuild-tasks), since they can then take part in the overall build process.</span></span> <span data-ttu-id="01e0a-132">Navíc můžete získat všechny data snadno, který je vytvořen pomocí sestavení, jako je například umístění výstupních souborů, aktuální konfigurace sestavována atd. Tyto informace se změní sadu vlastnosti nástroje MSBuild, které může číst z žádné cíle.</span><span class="sxs-lookup"><span data-stu-id="01e0a-132">Also, they can get any and all data easily that is produced via the build, such as the location of the output files, the current configuration being built, etc. All this information becomes a set of MSBuild properties that can be read from any target.</span></span> <span data-ttu-id="01e0a-133">Můžete zjistit, jak přidat vlastní cíl pomocí nástroje NuGet dále v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="01e0a-133">You can see how to add a custom target using NuGet later in this document.</span></span>

<span data-ttu-id="01e0a-134">Pojďme se podívat na příklad Přidání jednoduchého nástroje jenom nástroje na jednoduchý projekt.</span><span class="sxs-lookup"><span data-stu-id="01e0a-134">Let's review an example of adding a simple tools-only tool to a simple project.</span></span> <span data-ttu-id="01e0a-135">Zadaný příkaz příklad volá `dotnet-api-search` , který umožňuje prohledávat balíčky NuGet pro zadané rozhraní API, tady je soubor projektu konzolové aplikace, který používá nástroje:</span><span class="sxs-lookup"><span data-stu-id="01e0a-135">Given an example command called `dotnet-api-search` that allows you to search through the NuGet packages for the specified API, here is a console application's project file that uses that tool:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="01e0a-136">`<DotNetCliToolReference>` Element strukturovaná podobně jako `<PackageReference>` elementu.</span><span class="sxs-lookup"><span data-stu-id="01e0a-136">The `<DotNetCliToolReference>` element is structured in a similar way as the `<PackageReference>` element.</span></span> <span data-ttu-id="01e0a-137">Musí být schopni obnovit ID balíčku nástroje balíček, který obsahuje nástroje a její verzi.</span><span class="sxs-lookup"><span data-stu-id="01e0a-137">It needs the package ID of the package containing the tool and its version to be able to restore.</span></span>

### <a name="building-tools"></a><span data-ttu-id="01e0a-138">Nástroje pro sestavování</span><span class="sxs-lookup"><span data-stu-id="01e0a-138">Building tools</span></span>
<span data-ttu-id="01e0a-139">Jak už bylo zmíněno, nástroje jsou pouze přenosných konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="01e0a-139">As mentioned, tools are just portable console applications.</span></span> <span data-ttu-id="01e0a-140">Nástroje sestavení, jako by sestavení jakékoli jiné aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="01e0a-140">You build tools as you would build any other console application.</span></span>
<span data-ttu-id="01e0a-141">Po sestavení, můžete použít [ `dotnet pack` ](dotnet-pack.md) příkaz, který vytvoří balíček NuGet (.nupkg soubor), která obsahuje váš kód, informace o jeho závislosti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="01e0a-141">After you build it, you use the [`dotnet pack`](dotnet-pack.md) command to create a NuGet package (.nupkg file) that contains your code, information about its dependencies, and so on.</span></span> <span data-ttu-id="01e0a-142">Můžete přiřadit libovolný název balíčku, ale aplikace, nástroj Skutečná binární, musí odpovídat konvenci `dotnet-<command>` mohl `dotnet` být schopni ho vyvolat.</span><span class="sxs-lookup"><span data-stu-id="01e0a-142">You can give any name to the package, but the application inside, the actual tool binary, has to conform to the convention of `dotnet-<command>` in order for `dotnet` to be able to invoke it.</span></span>

> [!NOTE]
> <span data-ttu-id="01e0a-143">V RC3 předběžné verze nástroje příkazového řádku .NET Core `dotnet pack` měl příkaz, který způsobil chybu `runtime.config.json` nesmí být zabalena nástrojem.</span><span class="sxs-lookup"><span data-stu-id="01e0a-143">In pre-RC3 versions of the .NET Core command-line tools, the `dotnet pack` command had a bug that caused the `runtime.config.json` to not be packed with the tool.</span></span> <span data-ttu-id="01e0a-144">Chybí tento soubor výsledků chyby za běhu.</span><span class="sxs-lookup"><span data-stu-id="01e0a-144">Lacking that file results in errors at runtime.</span></span> <span data-ttu-id="01e0a-145">Pokud narazíte na toto chování, nezapomeňte aktualizovat na nejnovější nástroje a zkuste to `dotnet pack` znovu.</span><span class="sxs-lookup"><span data-stu-id="01e0a-145">If you encounter this behavior, be sure to update to the latest tooling and try the `dotnet pack` again.</span></span>

<span data-ttu-id="01e0a-146">Vzhledem k tomu, že jsou nástroje přenosné aplikace, musí mít uživatele, nástroj verze knihovny .NET Core, které nástroj byla vytvořena Chcete-li spustit nástroj.</span><span class="sxs-lookup"><span data-stu-id="01e0a-146">Since tools are portable applications, the user consuming the tool must have the version of the .NET Core libraries that the tool was built against in order to run the tool.</span></span> <span data-ttu-id="01e0a-147">Všechny další závislosti, využívá nástroj a, která není zahrnutá do knihovny .NET Core není obnoví a je umístěn v mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="01e0a-147">Any other dependency that the tool uses and that is not contained within the .NET Core libraries is restored and placed in the NuGet cache.</span></span> <span data-ttu-id="01e0a-148">Celý nástroj, proto se spouští pomocí sestavení z knihoven .NET Core a sestavení z mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="01e0a-148">The entire tool is, therefore, run using the assemblies from the .NET Core libraries as well as assemblies from the NuGet cache.</span></span>

<span data-ttu-id="01e0a-149">Tyto druhy nástroje mají graf závislostí, který je zcela oddělená od grafu závislostí projektu, který je využívá.</span><span class="sxs-lookup"><span data-stu-id="01e0a-149">These kinds of tools have a dependency graph that is completely separate from the dependency graph of the project that uses them.</span></span> <span data-ttu-id="01e0a-150">Proces obnovení nejprve obnoví závislosti projektu a poté obnoví všechny nástroje a jejich závislosti.</span><span class="sxs-lookup"><span data-stu-id="01e0a-150">The restore process first restores the project's dependencies and then restores each of the tools and their dependencies.</span></span>

<span data-ttu-id="01e0a-151">Najdete podrobnější příklady a to v různých kombinacích [úložiště .NET Core CLI](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span><span class="sxs-lookup"><span data-stu-id="01e0a-151">You can find richer examples and different combinations of this in the [.NET Core CLI repo](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span></span>
<span data-ttu-id="01e0a-152">Můžete zobrazit také [implementace nástroje používané](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) ve stejném úložišti.</span><span class="sxs-lookup"><span data-stu-id="01e0a-152">You can also see the [implementation of tools used](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) in the same repo.</span></span>

### <a name="custom-targets"></a><span data-ttu-id="01e0a-153">Vlastní cíle</span><span class="sxs-lookup"><span data-stu-id="01e0a-153">Custom targets</span></span>
<span data-ttu-id="01e0a-154">NuGet má schopnost [balíček vlastní MSBuild cíle a soubory vlastností](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="01e0a-154">NuGet has the capability to [package custom MSBuild targets and props files](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span></span> <span data-ttu-id="01e0a-155">S přechodem na nástroje rozhraní příkazového řádku .NET Core pro použití nástroje MSBuild stejný mechanismus rozšiřitelnosti teď platí pro projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="01e0a-155">With the move of the .NET Core CLI tools to use MSBuild, the same mechanism of extensibility now applies to .NET Core projects.</span></span> <span data-ttu-id="01e0a-156">Tento typ rozšíření byste použili, když chcete rozšíření procesu sestavení, nebo když chcete získat přístup k žádnému artefaktů v procesu sestavení, jako je například generované soubory, nebo chcete provést kontrolu konfigurace, pod kterým je vyvolán sestavení , atd.</span><span class="sxs-lookup"><span data-stu-id="01e0a-156">You would use this type of extensibility when you want to extend the build process, or when you want to access any of the artifacts in the build process, such as generated files, or you want to inspect the configuration under which the build is invoked, etc.</span></span>

<span data-ttu-id="01e0a-157">V následujícím příkladu vidíte cílový projekt pomocí souborů `csproj` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="01e0a-157">In the following example, you can see the target's project file using the `csproj` syntax.</span></span> <span data-ttu-id="01e0a-158">Tím se nastaví [ `dotnet pack` ](dotnet-pack.md) příkaz co do balíčku, uvedení soubory cíle a také sestavení do *sestavení* složky uvnitř balíčku.</span><span class="sxs-lookup"><span data-stu-id="01e0a-158">This instructs the [`dotnet pack`](dotnet-pack.md) command what to package, placing the targets files as well as the assemblies into the *build* folder inside the package.</span></span> <span data-ttu-id="01e0a-159">Všimněte si, že `<ItemGroup>` element, který má `Label` nastavenou na `dotnet pack instructions`, a cíl definovaný pod ním.</span><span class="sxs-lookup"><span data-stu-id="01e0a-159">Notice the `<ItemGroup>` element that has the `Label` property set to `dotnet pack instructions`, and the Target defined beneath it.</span></span>

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

<span data-ttu-id="01e0a-160">Použití vlastní cíle se uvede `<PackageReference>` , která odkazuje na balíček a jeho verzi v projektu, který se rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="01e0a-160">Consuming custom targets is done by providing a `<PackageReference>` that points to the package and its version inside the project that is being extended.</span></span> <span data-ttu-id="01e0a-161">Na rozdíl od nástroje získat balíček vlastní cíle zahrnut do uzavření závislostí projektu náročné.</span><span class="sxs-lookup"><span data-stu-id="01e0a-161">Unlike the tools, the custom targets package does get included into the consuming project's dependency closure.</span></span>

<span data-ttu-id="01e0a-162">Použití vlastní cíle závisí výhradně na tom, jak nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="01e0a-162">Using the custom target depends solely on how you configure it.</span></span> <span data-ttu-id="01e0a-163">Protože je cíl nástroje MSBuild, může záviset na daném cíli, spustit po jiném cíli a je také možné ručně vyvolat pomocí `dotnet msbuild /t:<target-name>` příkazu.</span><span class="sxs-lookup"><span data-stu-id="01e0a-163">Since it's an MSBuild target, it can depend on a given target, run after another target and can also be manually invoked using the `dotnet msbuild /t:<target-name>` command.</span></span>

<span data-ttu-id="01e0a-164">Nicméně pokud chcete poskytovat lepší výkon pro vaše uživatele, můžete kombinovat jednotlivých projektů nástroje a vlastní cíle.</span><span class="sxs-lookup"><span data-stu-id="01e0a-164">However, if you want to provide a better user experience to your users, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="01e0a-165">V tomto scénáři nástroj jednotlivých projektů by v podstatě stačí přijmout cokoli, co potřebné parametry a, která převedla do požadované [ `dotnet msbuild` ](dotnet-msbuild.md) volání, které by se spustit cíl.</span><span class="sxs-lookup"><span data-stu-id="01e0a-165">In this scenario, the per-project tool would essentially just accept whatever needed parameters and would translate that into the required [`dotnet msbuild`](dotnet-msbuild.md) invocation that would execute the target.</span></span> <span data-ttu-id="01e0a-166">Můžete zobrazit ukázku, tento druh synergii na [MVP Summit 2016 Hackathon ukázky](https://github.com/dotnet/MVPSummitHackathon2016) úložiště v [ `dotnet-packer` ](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projektu.</span><span class="sxs-lookup"><span data-stu-id="01e0a-166">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

### <a name="path-based-extensibility"></a><span data-ttu-id="01e0a-167">Na základě cest rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="01e0a-167">PATH-based extensibility</span></span>
<span data-ttu-id="01e0a-168">Na základě cest rozšíření se obvykle používá pro vývoj počítače tam, kde potřebujete nástroj, který koncepčně zahrnuje více než jeden projekt.</span><span class="sxs-lookup"><span data-stu-id="01e0a-168">PATH-based extensibility is usually used for development machines where you need a tool that conceptually covers more than a single project.</span></span> <span data-ttu-id="01e0a-169">Tento mechanismus rozšíření Hlavní nevýhodou je, že je spojený s počítači tam, kde existuje nástroj.</span><span class="sxs-lookup"><span data-stu-id="01e0a-169">The main drawback of this extension mechanism is that it's tied to the machine where the tool exists.</span></span> <span data-ttu-id="01e0a-170">Pokud je nutné ji na jiném počítači, je třeba ho nasadit.</span><span class="sxs-lookup"><span data-stu-id="01e0a-170">If you need it on another machine, you would have to deploy it.</span></span>

<span data-ttu-id="01e0a-171">Tento model rozšiřitelnosti nástrojů rozhraní příkazového řádku je velmi snadné.</span><span class="sxs-lookup"><span data-stu-id="01e0a-171">This pattern of CLI toolset extensibility is very simple.</span></span> <span data-ttu-id="01e0a-172">Jak je popsáno v [přehled rozhraní příkazového řádku .NET Core](index.md), `dotnet` ovladač lze spustit jakýkoli příkaz, který má stejný název `dotnet-<command>` konvence.</span><span class="sxs-lookup"><span data-stu-id="01e0a-172">As covered in the [.NET Core CLI overview](index.md), `dotnet` driver can run any command that is named after the `dotnet-<command>` convention.</span></span> <span data-ttu-id="01e0a-173">Výchozí logika řešení nejprve sondy několika míst a nakonec spadne zpět na CESTU systému.</span><span class="sxs-lookup"><span data-stu-id="01e0a-173">The default resolution logic first probes several locations and finally falls back to the system PATH.</span></span> <span data-ttu-id="01e0a-174">Pokud požadovaný příkaz, existuje v systémové CESTĚ a je binární soubor, který může být vyvolána, `dotnet` ovladač vyvolá.</span><span class="sxs-lookup"><span data-stu-id="01e0a-174">If the requested command exists in the system PATH and is a binary that can be invoked, `dotnet` driver will invoke it.</span></span>

<span data-ttu-id="01e0a-175">Soubor musí být spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="01e0a-175">The file must be executable.</span></span> <span data-ttu-id="01e0a-176">V systémech Unix, to znamená cokoliv, co má nastavený bit provést prostřednictvím `chmod +x`.</span><span class="sxs-lookup"><span data-stu-id="01e0a-176">On Unix systems, this means anything that has the execute bit set via `chmod +x`.</span></span> <span data-ttu-id="01e0a-177">Na Windows, můžete použít *cmd* soubory.</span><span class="sxs-lookup"><span data-stu-id="01e0a-177">On Windows, you can use *cmd* files.</span></span>

<span data-ttu-id="01e0a-178">Pojďme se podívat na velmi jednoduchá implementace nástroje "Hello World".</span><span class="sxs-lookup"><span data-stu-id="01e0a-178">Let's take a look at the very simple implementation of a "Hello World" tool.</span></span> <span data-ttu-id="01e0a-179">Použijeme obě `bash` a `cmd` na Windows.</span><span class="sxs-lookup"><span data-stu-id="01e0a-179">We will use both `bash` and `cmd` on Windows.</span></span>
<span data-ttu-id="01e0a-180">Následující příkaz se ke konzole echo jednoduše "Hello World".</span><span class="sxs-lookup"><span data-stu-id="01e0a-180">The following command will simply echo "Hello World" to the console.</span></span>

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

<span data-ttu-id="01e0a-181">V systému macOS, uložíme tento skript jako `dotnet-hello` a nastavte jeho spustitelné bitové s `chmod +x dotnet-hello`.</span><span class="sxs-lookup"><span data-stu-id="01e0a-181">On macOS, we can save this script as `dotnet-hello` and set its executable bit with `chmod +x dotnet-hello`.</span></span> <span data-ttu-id="01e0a-182">Pak vytvoříme symbolický odkaz k tomu `/usr/local/bin` pomocí příkazu `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span><span class="sxs-lookup"><span data-stu-id="01e0a-182">We can then create a symbolic link to it in `/usr/local/bin` using the command `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span></span> <span data-ttu-id="01e0a-183">To znamená, že je to možné, který má být vyvolán pomocí příkazu `dotnet hello` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="01e0a-183">This will make it possible to invoke the command using the `dotnet hello` syntax.</span></span>

<span data-ttu-id="01e0a-184">Na Windows, uložíme tento skript jako `dotnet-hello.cmd` a vložit ho do umístění, které je v systémové cestě (nebo ji můžete přidat do složky, která je již v cestě).</span><span class="sxs-lookup"><span data-stu-id="01e0a-184">On Windows, we can save this script as `dotnet-hello.cmd` and put it in a location that is in a system path (or you can add it to a folder that is already in the path).</span></span> <span data-ttu-id="01e0a-185">Potom můžete použít jenom `dotnet hello` spuštění tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="01e0a-185">After this, you can just use `dotnet hello` to run this example.</span></span>
