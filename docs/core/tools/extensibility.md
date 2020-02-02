---
title: Model rozšiřitelnosti .NET Core CLI
description: Přečtěte si, jak můžete .NET Core CLI rozšiřuje.
ms.date: 04/12/2017
ms.openlocfilehash: 74da895fb3a3f6c77640a2b9a64acdb2894a954b
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920518"
---
# <a name="net-core-cli-extensibility-model"></a><span data-ttu-id="85a9d-103">Model rozšiřitelnosti .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="85a9d-103">.NET Core CLI extensibility model</span></span>

<span data-ttu-id="85a9d-104">Tento článek popisuje různé způsoby, jak .NET Core CLI můžete roztáhnout a vysvětlit scénáře, které jednotlivé jednotky na nich zabírají.</span><span class="sxs-lookup"><span data-stu-id="85a9d-104">This article covers the different ways you can extend the .NET Core CLI and explain the scenarios that drive each one of them.</span></span>
<span data-ttu-id="85a9d-105">Uvidíte, jak tyto nástroje používat a jak vytvořit různé typy nástrojů.</span><span class="sxs-lookup"><span data-stu-id="85a9d-105">You'll see how to consume the tools as well as how to build the different types of tools.</span></span>

## <a name="how-to-extend-the-cli"></a><span data-ttu-id="85a9d-106">Postup rozšiřování rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="85a9d-106">How to extend the CLI</span></span>
<span data-ttu-id="85a9d-107">Rozhraní příkazového řádku lze rozšířit třemi hlavními způsoby:</span><span class="sxs-lookup"><span data-stu-id="85a9d-107">The CLI can be extended in three main ways:</span></span>

1. [<span data-ttu-id="85a9d-108">Přes balíčky NuGet na jednotlivých projektech</span><span class="sxs-lookup"><span data-stu-id="85a9d-108">Via NuGet packages on a per-project basis</span></span>](#per-project-based-extensibility)

   <span data-ttu-id="85a9d-109">Nástroje pro projekty jsou obsaženy v kontextu projektu, ale umožňují snadnou instalaci prostřednictvím obnovení.</span><span class="sxs-lookup"><span data-stu-id="85a9d-109">Per-project tools are contained within the project's context, but they allow easy installation through restoration.</span></span>

2. [<span data-ttu-id="85a9d-110">Přes balíčky NuGet s vlastními cíli</span><span class="sxs-lookup"><span data-stu-id="85a9d-110">Via NuGet packages with custom targets</span></span>](#custom-targets)

   <span data-ttu-id="85a9d-111">Vlastní cíle vám umožňují snadno roztáhnout proces sestavení s vlastními úkoly.</span><span class="sxs-lookup"><span data-stu-id="85a9d-111">Custom targets allow you to easily extend the build process with custom tasks.</span></span>

3. [<span data-ttu-id="85a9d-112">Přes cestu systému</span><span class="sxs-lookup"><span data-stu-id="85a9d-112">Via the system's PATH</span></span>](#path-based-extensibility)

   <span data-ttu-id="85a9d-113">Nástroje založené na cestách jsou vhodné pro obecné nástroje pro více projektů, které jsou použitelné na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="85a9d-113">PATH-based tools are good for general, cross-project tools that are usable on a single machine.</span></span>

<span data-ttu-id="85a9d-114">Tři výše popsané mechanismy rozšíření nejsou exkluzivní.</span><span class="sxs-lookup"><span data-stu-id="85a9d-114">The three extensibility mechanisms outlined above are not exclusive.</span></span> <span data-ttu-id="85a9d-115">Můžete použít jeden nebo všechny nebo jejich kombinaci.</span><span class="sxs-lookup"><span data-stu-id="85a9d-115">You can use one, or all, or a combination of them.</span></span> <span data-ttu-id="85a9d-116">Který z jednoho výběru závisí hlavně na cíli, který se snažíte dosáhnout s vaším rozšířením.</span><span class="sxs-lookup"><span data-stu-id="85a9d-116">Which one to pick depends largely on the goal you are trying to achieve with your extension.</span></span>

## <a name="per-project-based-extensibility"></a><span data-ttu-id="85a9d-117">Rozšiřitelnost na základě projektu</span><span class="sxs-lookup"><span data-stu-id="85a9d-117">Per-project based extensibility</span></span>
<span data-ttu-id="85a9d-118">Nástroje pro jednotlivé projekty jsou [nasazení závislá na rozhraní](../deploying/index.md#framework-dependent-deployments-fdd) , která jsou distribuována jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="85a9d-118">Per-project tools are [framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) that are distributed as NuGet packages.</span></span> <span data-ttu-id="85a9d-119">Nástroje jsou k dispozici pouze v kontextu projektu, který je odkazuje na ně a pro které jsou obnoveny.</span><span class="sxs-lookup"><span data-stu-id="85a9d-119">Tools are only available in the context of the project that references them and for which they are restored.</span></span> <span data-ttu-id="85a9d-120">Volání mimo kontext projektu (například mimo adresář, který obsahuje projekt) selže, protože příkaz nelze nalézt.</span><span class="sxs-lookup"><span data-stu-id="85a9d-120">Invocation outside of the context of the project (for example, outside of the directory that contains the project) will fail because the command cannot be found.</span></span>

<span data-ttu-id="85a9d-121">Tyto nástroje jsou ideální pro servery sestavení, protože není potřeba nic mimo soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="85a9d-121">These tools are perfect for build servers, since nothing outside of the project file is needed.</span></span> <span data-ttu-id="85a9d-122">Proces sestavení spustí obnovení pro sestavení projektu, které bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="85a9d-122">The build process runs restore for the project it builds and tools will be available.</span></span> <span data-ttu-id="85a9d-123">Jazykové projekty, například F#, jsou také v této kategorii, protože každý projekt lze zapsat pouze do jednoho konkrétního jazyka.</span><span class="sxs-lookup"><span data-stu-id="85a9d-123">Language projects, such as F#, are also in this category since each project can only be written in one specific language.</span></span>

<span data-ttu-id="85a9d-124">Nakonec tento model rozšiřitelnosti poskytuje podporu pro vytváření nástrojů, které potřebují přístup k sestavenému výstupu projektu.</span><span class="sxs-lookup"><span data-stu-id="85a9d-124">Finally, this extensibility model provides support for creation of tools that need access to the built output of the project.</span></span> <span data-ttu-id="85a9d-125">Do této kategorie patří například různé nástroje pro zobrazení Razor v aplikacích [ASP.NET](https://www.asp.net/) MVC.</span><span class="sxs-lookup"><span data-stu-id="85a9d-125">For instance, various Razor view tools in [ASP.NET](https://www.asp.net/) MVC applications fall into this category.</span></span>

### <a name="consuming-per-project-tools"></a><span data-ttu-id="85a9d-126">Zpracování nástrojů pro jednotlivé projekty</span><span class="sxs-lookup"><span data-stu-id="85a9d-126">Consuming per-project tools</span></span>
<span data-ttu-id="85a9d-127">Spotřeba těchto nástrojů vyžaduje, abyste přidali `<DotNetCliToolReference>` element do souboru projektu pro každý nástroj, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="85a9d-127">Consuming these tools requires you to add a `<DotNetCliToolReference>` element to your project file for each tool you want to use.</span></span> <span data-ttu-id="85a9d-128">Uvnitř elementu `<DotNetCliToolReference>` odkazujete na balíček, ve kterém se nástroj nachází, a zadejte požadovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="85a9d-128">Inside the `<DotNetCliToolReference>` element, you reference the package in which the tool resides and specify the version you need.</span></span> <span data-ttu-id="85a9d-129">Po spuštění [`dotnet restore`](dotnet-restore.md)se nástroj a jeho závislosti obnoví.</span><span class="sxs-lookup"><span data-stu-id="85a9d-129">After running [`dotnet restore`](dotnet-restore.md), the tool and its dependencies are restored.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="85a9d-130">Pro nástroje, které potřebují načíst výstup sestavení projektu ke spuštění, je obvykle jiná závislost, která je uvedena v rámci normální závislosti v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="85a9d-130">For tools that need to load the build output of the project for execution, there is usually another dependency which is listed under the regular dependencies in the project file.</span></span> <span data-ttu-id="85a9d-131">Vzhledem k tomu, že rozhraní příkazového řádku používá jako modul sestavení MSBuild, doporučujeme, aby tyto části nástroje byly zapsány jako vlastní [cíle](/visualstudio/msbuild/msbuild-targets) a [úkoly](/visualstudio/msbuild/msbuild-tasks)MSBuild, protože mohou být součástí celého procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="85a9d-131">Since CLI uses MSBuild as its build engine, we recommend that these parts of the tool be written as custom MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and [tasks](/visualstudio/msbuild/msbuild-tasks), since they can then take part in the overall build process.</span></span> <span data-ttu-id="85a9d-132">Také mohou získat jakákoli a všechna data, která jsou vytvářena prostřednictvím sestavení, například umístění výstupních souborů, aktuální konfigurace, která je vytvořena a tak dále.</span><span class="sxs-lookup"><span data-stu-id="85a9d-132">Also, they can get any and all data easily that is produced via the build, such as the location of the output files, the current configuration being built, and so on.</span></span> <span data-ttu-id="85a9d-133">Všechny tyto informace se stávají sadou vlastností nástroje MSBuild, které lze číst z libovolného cíle.</span><span class="sxs-lookup"><span data-stu-id="85a9d-133">All this information becomes a set of MSBuild properties that can be read from any target.</span></span> <span data-ttu-id="85a9d-134">Můžete vidět, jak přidat vlastní cíl pomocí NuGetu dále v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="85a9d-134">You can see how to add a custom target using NuGet later in this document.</span></span>

<span data-ttu-id="85a9d-135">Pojďme se podívat na příklad přidání jednoduchého nástroje pouze pro nástroje do jednoduchého projektu.</span><span class="sxs-lookup"><span data-stu-id="85a9d-135">Let's review an example of adding a simple tools-only tool to a simple project.</span></span> <span data-ttu-id="85a9d-136">V případě ukázkového příkazu s názvem `dotnet-api-search`, který umožňuje vyhledat balíčky NuGet pro zadané rozhraní API, je zde soubor projektu aplikace konzoly, který používá tento nástroj:</span><span class="sxs-lookup"><span data-stu-id="85a9d-136">Given an example command called `dotnet-api-search` that allows you to search through the NuGet packages for the specified API, here is a console application's project file that uses that tool:</span></span>

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

<span data-ttu-id="85a9d-137">Element `<DotNetCliToolReference>` je strukturován podobným způsobem jako `<PackageReference>` prvek.</span><span class="sxs-lookup"><span data-stu-id="85a9d-137">The `<DotNetCliToolReference>` element is structured in a similar way as the `<PackageReference>` element.</span></span> <span data-ttu-id="85a9d-138">Potřebuje ID balíčku balíčku, který obsahuje nástroj a jeho verzi, aby se mohl obnovit.</span><span class="sxs-lookup"><span data-stu-id="85a9d-138">It needs the package ID of the package containing the tool and its version to be able to restore.</span></span>

### <a name="building-tools"></a><span data-ttu-id="85a9d-139">Vytváření nástrojů</span><span class="sxs-lookup"><span data-stu-id="85a9d-139">Building tools</span></span>
<span data-ttu-id="85a9d-140">Jak už bylo zmíněno, nástroje jsou jenom přenosné konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="85a9d-140">As mentioned, tools are just portable console applications.</span></span> <span data-ttu-id="85a9d-141">Nástroje sestavíte stejně, jako byste vytvořili jinou konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="85a9d-141">You build tools as you would build any other console application.</span></span>
<span data-ttu-id="85a9d-142">Po sestavení můžete pomocí příkazu [`dotnet pack`](dotnet-pack.md) vytvořit balíček NuGet (soubor. nupkg), který obsahuje váš kód, informace o jeho závislostech atd.</span><span class="sxs-lookup"><span data-stu-id="85a9d-142">After you build it, you use the [`dotnet pack`](dotnet-pack.md) command to create a NuGet package (.nupkg file) that contains your code, information about its dependencies, and so on.</span></span> <span data-ttu-id="85a9d-143">Do balíčku můžete dát libovolný název, ale aplikace uvnitř, skutečný binární soubor nástroje, musí odpovídat konvenci `dotnet-<command>`, aby `dotnet` mohl vyvolat.</span><span class="sxs-lookup"><span data-stu-id="85a9d-143">You can give any name to the package, but the application inside, the actual tool binary, has to conform to the convention of `dotnet-<command>` in order for `dotnet` to be able to invoke it.</span></span>

> [!NOTE]
> <span data-ttu-id="85a9d-144">V RC3 verzích nástrojů příkazového řádku .NET Core měla příkaz `dotnet pack` chybu, která způsobila, že *runtimeconfig. JSON* není zabalený pomocí nástroje.</span><span class="sxs-lookup"><span data-stu-id="85a9d-144">In pre-RC3 versions of the .NET Core command-line tools, the `dotnet pack` command had a bug that caused the *.runtimeconfig.json* to not be packed with the tool.</span></span> <span data-ttu-id="85a9d-145">Při nedostatku tohoto souboru dojde k chybám za běhu.</span><span class="sxs-lookup"><span data-stu-id="85a9d-145">Lacking that file results in errors at runtime.</span></span> <span data-ttu-id="85a9d-146">Pokud narazíte na toto chování, nezapomeňte aktualizovat na nejnovější nástroje a zkuste `dotnet pack` znovu.</span><span class="sxs-lookup"><span data-stu-id="85a9d-146">If you encounter this behavior, be sure to update to the latest tooling and try the `dotnet pack` again.</span></span>

<span data-ttu-id="85a9d-147">Vzhledem k tomu, že nástroje jsou přenosné aplikace, uživatel, který nástroj spotřebovává, musí mít verzi knihoven .NET Core, pro kterou byl nástroj vytvořen, aby mohl nástroj spustit.</span><span class="sxs-lookup"><span data-stu-id="85a9d-147">Since tools are portable applications, the user consuming the tool must have the version of the .NET Core libraries that the tool was built against in order to run the tool.</span></span> <span data-ttu-id="85a9d-148">Všechny ostatní závislosti, které nástroj používá a které nejsou obsaženy v knihovnách .NET Core, se obnoví a umístí do mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="85a9d-148">Any other dependency that the tool uses and that is not contained within the .NET Core libraries is restored and placed in the NuGet cache.</span></span> <span data-ttu-id="85a9d-149">Celý nástroj je proto spouštěn pomocí sestavení z knihoven .NET Core i sestavení z mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="85a9d-149">The entire tool is, therefore, run using the assemblies from the .NET Core libraries as well as assemblies from the NuGet cache.</span></span>

<span data-ttu-id="85a9d-150">Tyto druhy nástrojů mají graf závislosti, který je zcela oddělený od grafu závislostí projektu, který je používá.</span><span class="sxs-lookup"><span data-stu-id="85a9d-150">These kinds of tools have a dependency graph that is completely separate from the dependency graph of the project that uses them.</span></span> <span data-ttu-id="85a9d-151">Proces obnovení nejprve obnoví závislosti projektu a pak obnoví všechny nástroje a jejich závislosti.</span><span class="sxs-lookup"><span data-stu-id="85a9d-151">The restore process first restores the project's dependencies and then restores each of the tools and their dependencies.</span></span>

<span data-ttu-id="85a9d-152">V [úložišti .NET Core CLI](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects)můžete najít bohatší příklady a různé kombinace.</span><span class="sxs-lookup"><span data-stu-id="85a9d-152">You can find richer examples and different combinations of this in the [.NET Core CLI repo](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span></span>
<span data-ttu-id="85a9d-153">Můžete také zobrazit [implementaci nástrojů používaných](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) ve stejném úložišti.</span><span class="sxs-lookup"><span data-stu-id="85a9d-153">You can also see the [implementation of tools used](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) in the same repo.</span></span>

## <a name="custom-targets"></a><span data-ttu-id="85a9d-154">Vlastní cíle</span><span class="sxs-lookup"><span data-stu-id="85a9d-154">Custom targets</span></span>

<span data-ttu-id="85a9d-155">Balíčky NuGet mají možnost [zabalit vlastní cíle a soubory props nástroje MSBuild](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="85a9d-155">NuGet has the capability to [package custom MSBuild targets and props files](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package).</span></span> <span data-ttu-id="85a9d-156">Když přesunete .NET Core pro použití nástroje MSBuild, stejný mechanismus rozšíření teď platí pro projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85a9d-156">With the move of the .NET Core to use MSBuild, the same mechanism of extensibility now applies to .NET Core projects.</span></span> <span data-ttu-id="85a9d-157">Tento typ rozšiřitelnosti byste měli použít, pokud chcete rozšíření procesu sestavení, nebo když chcete získat přístup k jakémukoli artefaktům v procesu sestavení, jako jsou například generované soubory nebo chcete zkontrolovat konfiguraci, pod kterou je vyvoláno sestavení. a tak dále.</span><span class="sxs-lookup"><span data-stu-id="85a9d-157">You would use this type of extensibility when you want to extend the build process, or when you want to access any of the artifacts in the build process, such as generated files, or you want to inspect the configuration under which the build is invoked, and so on.</span></span>

<span data-ttu-id="85a9d-158">V následujícím příkladu se můžete podívat na soubor projektu cíle pomocí syntaxe `csproj`.</span><span class="sxs-lookup"><span data-stu-id="85a9d-158">In the following example, you can see the target's project file using the `csproj` syntax.</span></span> <span data-ttu-id="85a9d-159">Tím se dá pokyn [`dotnet pack`](dotnet-pack.md) příkazu, který se má zabalit, umístit soubory cílů i sestavení do složky *sestavení* uvnitř balíčku.</span><span class="sxs-lookup"><span data-stu-id="85a9d-159">This instructs the [`dotnet pack`](dotnet-pack.md) command what to package, placing the targets files as well as the assemblies into the *build* folder inside the package.</span></span> <span data-ttu-id="85a9d-160">Všimněte si `<ItemGroup>` elementu, který má vlastnost `Label` nastavenou na `dotnet pack instructions`a cíl definovaný pod ním.</span><span class="sxs-lookup"><span data-stu-id="85a9d-160">Notice the `<ItemGroup>` element that has the `Label` property set to `dotnet pack instructions`, and the Target defined beneath it.</span></span>

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

<span data-ttu-id="85a9d-161">Používání vlastních cílů se provádí poskytnutím `<PackageReference>`, které odkazuje na balíček a jeho verzi v projektu, který se rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="85a9d-161">Consuming custom targets is done by providing a `<PackageReference>` that points to the package and its version inside the project that is being extended.</span></span> <span data-ttu-id="85a9d-162">Na rozdíl od nástrojů balíček vlastní cíle zahrnuje do uzavření závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="85a9d-162">Unlike the tools, the custom targets package does get included into the consuming project's dependency closure.</span></span>

<span data-ttu-id="85a9d-163">Použití vlastního cíle závisí výhradně na tom, jak ho nakonfigurujete.</span><span class="sxs-lookup"><span data-stu-id="85a9d-163">Using the custom target depends solely on how you configure it.</span></span> <span data-ttu-id="85a9d-164">Vzhledem k tomu, že se jedná o cíl nástroje MSBuild, může záviset na daném cíli, běžet po jiném cíli a lze jej také ručně vyvolat pomocí příkazu `dotnet msbuild -t:<target-name>`.</span><span class="sxs-lookup"><span data-stu-id="85a9d-164">Since it's an MSBuild target, it can depend on a given target, run after another target and can also be manually invoked using the `dotnet msbuild -t:<target-name>` command.</span></span>

<span data-ttu-id="85a9d-165">Pokud však chcete uživatelům poskytnout lepší uživatelské prostředí, můžete kombinovat nástroje pro jednotlivé projekty a vlastní cíle.</span><span class="sxs-lookup"><span data-stu-id="85a9d-165">However, if you want to provide a better user experience to your users, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="85a9d-166">V tomto scénáři by nástroj na projekt v podstatě přijal libovolné potřebné parametry a převedl to na požadované [`dotnet msbuild`](dotnet-msbuild.md) vyvolání, které by způsobilo provedení cíle.</span><span class="sxs-lookup"><span data-stu-id="85a9d-166">In this scenario, the per-project tool would essentially just accept whatever needed parameters and would translate that into the required [`dotnet msbuild`](dotnet-msbuild.md) invocation that would execute the target.</span></span> <span data-ttu-id="85a9d-167">Ukázku tohoto druhu součinnosti si můžete prohlédnout na úložišti [ukázek MVP 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) v projektu [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) .</span><span class="sxs-lookup"><span data-stu-id="85a9d-167">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="path-based-extensibility"></a><span data-ttu-id="85a9d-168">Rozšiřitelnost na základě cesty</span><span class="sxs-lookup"><span data-stu-id="85a9d-168">PATH-based extensibility</span></span>
<span data-ttu-id="85a9d-169">Rozšíření na základě cesty se obvykle používá ve vývojových počítačích, kde potřebujete nástroj, který koncepčně pokrývá více než jeden projekt.</span><span class="sxs-lookup"><span data-stu-id="85a9d-169">PATH-based extensibility is usually used for development machines where you need a tool that conceptually covers more than a single project.</span></span> <span data-ttu-id="85a9d-170">Hlavní nevýhodou tohoto mechanismu rozšíření je to, že je vázaný na počítač, na kterém nástroj existuje.</span><span class="sxs-lookup"><span data-stu-id="85a9d-170">The main drawback of this extension mechanism is that it's tied to the machine where the tool exists.</span></span> <span data-ttu-id="85a9d-171">Pokud ho potřebujete na jiném počítači, budete ho muset nasadit.</span><span class="sxs-lookup"><span data-stu-id="85a9d-171">If you need it on another machine, you would have to deploy it.</span></span>

<span data-ttu-id="85a9d-172">Tento model rozšiřitelnosti sady nástrojů rozhraní příkazového řádku je velmi jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="85a9d-172">This pattern of CLI toolset extensibility is very simple.</span></span> <span data-ttu-id="85a9d-173">Jak je popsáno v [přehledu .NET Core CLI](index.md), `dotnet` ovladač může spustit jakýkoli příkaz, který se jmenuje po `dotnet-<command>` konvenci.</span><span class="sxs-lookup"><span data-stu-id="85a9d-173">As covered in the [.NET Core CLI overview](index.md), `dotnet` driver can run any command that is named after the `dotnet-<command>` convention.</span></span> <span data-ttu-id="85a9d-174">Výchozí logika rozlišení nejprve vyhledá několik umístění a nakonec se vrátí k systémové cestě.</span><span class="sxs-lookup"><span data-stu-id="85a9d-174">The default resolution logic first probes several locations and finally falls back to the system PATH.</span></span> <span data-ttu-id="85a9d-175">Pokud v systémové cestě existuje požadovaný příkaz a je to binární soubor, který lze vyvolat, `dotnet` ovladač ho vyvolá.</span><span class="sxs-lookup"><span data-stu-id="85a9d-175">If the requested command exists in the system PATH and is a binary that can be invoked, `dotnet` driver will invoke it.</span></span>

<span data-ttu-id="85a9d-176">Soubor musí být spustitelný.</span><span class="sxs-lookup"><span data-stu-id="85a9d-176">The file must be executable.</span></span> <span data-ttu-id="85a9d-177">V systémech UNIX to znamená cokoli, co má nastaven bit spouštění prostřednictvím `chmod +x`.</span><span class="sxs-lookup"><span data-stu-id="85a9d-177">On Unix systems, this means anything that has the execute bit set via `chmod +x`.</span></span> <span data-ttu-id="85a9d-178">Ve Windows můžete použít soubory *cmd* .</span><span class="sxs-lookup"><span data-stu-id="85a9d-178">On Windows, you can use *cmd* files.</span></span>

<span data-ttu-id="85a9d-179">Pojďme se podívat na velmi jednoduchou implementaci nástroje "Hello World".</span><span class="sxs-lookup"><span data-stu-id="85a9d-179">Let's take a look at the very simple implementation of a "Hello World" tool.</span></span> <span data-ttu-id="85a9d-180">Ve Windows budeme používat jak `bash`, tak `cmd`.</span><span class="sxs-lookup"><span data-stu-id="85a9d-180">We will use both `bash` and `cmd` on Windows.</span></span>
<span data-ttu-id="85a9d-181">Následující příkaz jednoduše vrátí "Hello World" do konzoly.</span><span class="sxs-lookup"><span data-stu-id="85a9d-181">The following command will simply echo "Hello World" to the console.</span></span>

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

<span data-ttu-id="85a9d-182">V macOS můžete tento skript Uložit jako `dotnet-hello` a nastavit jeho spustitelný bit pomocí `chmod +x dotnet-hello`.</span><span class="sxs-lookup"><span data-stu-id="85a9d-182">On macOS, we can save this script as `dotnet-hello` and set its executable bit with `chmod +x dotnet-hello`.</span></span> <span data-ttu-id="85a9d-183">V `/usr/local/bin` pak můžeme vytvořit symbolický odkaz pomocí příkazového `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span><span class="sxs-lookup"><span data-stu-id="85a9d-183">We can then create a symbolic link to it in `/usr/local/bin` using the command `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span></span> <span data-ttu-id="85a9d-184">Díky tomu bude možné vyvolat příkaz pomocí syntaxe `dotnet hello`.</span><span class="sxs-lookup"><span data-stu-id="85a9d-184">This will make it possible to invoke the command using the `dotnet hello` syntax.</span></span>

<span data-ttu-id="85a9d-185">Ve Windows můžeme tento skript Uložit jako `dotnet-hello.cmd` a umístit ho do umístění, které je v systémové cestě (nebo ho můžete přidat do složky, která je už v cestě).</span><span class="sxs-lookup"><span data-stu-id="85a9d-185">On Windows, we can save this script as `dotnet-hello.cmd` and put it in a location that is in a system path (or you can add it to a folder that is already in the path).</span></span> <span data-ttu-id="85a9d-186">Za tímto účelem můžete spustit tento příklad jenom pomocí `dotnet hello`.</span><span class="sxs-lookup"><span data-stu-id="85a9d-186">After this, you can just use `dotnet hello` to run this example.</span></span>
