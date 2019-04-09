---
title: Port aplikace WPF až po .NET Core 3.0
description: Vás naučí, jak přenést aplikaci rozhraní .NET Framework Windows Presentation Foundation pro .NET Core 3.0 pro Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 80c55b45067405b1204cad0435b46b376f783c57
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151486"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a><span data-ttu-id="964e6-103">Postupy: Port desktopovou aplikaci WPF až po .NET Core</span><span class="sxs-lookup"><span data-stu-id="964e6-103">How to: Port a WPF desktop app to .NET Core</span></span>

<span data-ttu-id="964e6-104">Tento článek popisuje, jak přenést na základě Windows Presentation Foundation (WPF) aplikaci klasické pracovní plochy z rozhraní .NET Framework do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="964e6-104">This article describes how to port your Windows Presentation Foundation-based (WPF) desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="964e6-105">.NET Core 3.0 SDK obsahuje podporu pro aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="964e6-105">The .NET Core 3.0 SDK includes support for WPF applications.</span></span> <span data-ttu-id="964e6-106">WPF je stále rozhraní jen pro Windows a pouze běží na Windows.</span><span class="sxs-lookup"><span data-stu-id="964e6-106">WPF is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="964e6-107">Tento příklad používá rozhraní příkazového řádku .NET Core SDK k vytváření a správě vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="964e6-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="964e6-108">V tomto článku najdete různé názvy umožňují určit typy souborů se používá pro migraci.</span><span class="sxs-lookup"><span data-stu-id="964e6-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="964e6-109">Při migraci vašeho projektu, soubory budou pojmenované jinak, takže duševně je přizpůsobit uvedené níže:</span><span class="sxs-lookup"><span data-stu-id="964e6-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="964e6-110">Soubor</span><span class="sxs-lookup"><span data-stu-id="964e6-110">File</span></span> | <span data-ttu-id="964e6-111">Popis</span><span class="sxs-lookup"><span data-stu-id="964e6-111">Description</span></span> |
| ---- | ----------- |
| **<span data-ttu-id="964e6-112">MyApps.sln</span><span class="sxs-lookup"><span data-stu-id="964e6-112">MyApps.sln</span></span>** | <span data-ttu-id="964e6-113">Název souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="964e6-113">The name of the solution file.</span></span> |
| **<span data-ttu-id="964e6-114">MyWPF.csproj</span><span class="sxs-lookup"><span data-stu-id="964e6-114">MyWPF.csproj</span></span>** | <span data-ttu-id="964e6-115">Název projektu WPF rozhraní .NET Framework na port.</span><span class="sxs-lookup"><span data-stu-id="964e6-115">The name of the .NET Framework WPF project to port.</span></span> |
| **<span data-ttu-id="964e6-116">MyWPFCore.csproj</span><span class="sxs-lookup"><span data-stu-id="964e6-116">MyWPFCore.csproj</span></span>** | <span data-ttu-id="964e6-117">Název nového projektu .NET Core, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="964e6-117">The name of the new .NET Core project you create.</span></span> |
| **<span data-ttu-id="964e6-118">MyAppCore.exe</span><span class="sxs-lookup"><span data-stu-id="964e6-118">MyAppCore.exe</span></span>** | <span data-ttu-id="964e6-119">Spustitelný soubor aplikace .NET Core WPF.</span><span class="sxs-lookup"><span data-stu-id="964e6-119">The .NET Core WPF app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="964e6-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="964e6-120">Prerequisites</span></span>

- <span data-ttu-id="964e6-121">[Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=wpf+core) pro jakékoli návrháře práce, které chcete provést.</span><span class="sxs-lookup"><span data-stu-id="964e6-121">[Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=wpf+core) for any designer work you want to do.</span></span>

  <span data-ttu-id="964e6-122">Instalace následujících úlohách sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="964e6-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="964e6-123">Vývoj desktopových aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="964e6-123">.NET desktop development</span></span>
  - <span data-ttu-id="964e6-124">Vývoj pro různé platformy .NET</span><span class="sxs-lookup"><span data-stu-id="964e6-124">.NET cross-platform development</span></span>

- <span data-ttu-id="964e6-125">Projekt WPF práci v řešení, které vytvoří a spustí bez problému.</span><span class="sxs-lookup"><span data-stu-id="964e6-125">A working WPF project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="964e6-126">Váš projekt musí být zakódované v C#.</span><span class="sxs-lookup"><span data-stu-id="964e6-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="964e6-127">Nainstalujte nejnovější [.NET Core 3.0](https://aka.ms/netcore3download) ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="964e6-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="964e6-128">**Visual Studio 2017** nepodporuje projekty .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="964e6-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="964e6-129">**Visual Studio. 2019 ve verzi Preview nebo RC** podporuje projekty .NET Core 3.0, ale zatím nepodporuje vizuálního návrháře pro projekty .NET Core 3.0 WPF.</span><span class="sxs-lookup"><span data-stu-id="964e6-129">**Visual Studio 2019 Preview/RC** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 WPF projects.</span></span> <span data-ttu-id="964e6-130">Do vizuálního návrháře použít, musí mít projekt .NET WPF ve vašem řešení, která sdílí soubory s projektem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="964e6-130">To use the visual designer, you must have a .NET WPF project in your solution that shares its files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="964e6-131">Vezměte v úvahu</span><span class="sxs-lookup"><span data-stu-id="964e6-131">Consider</span></span>

<span data-ttu-id="964e6-132">Při přenesení aplikace rozhraní .NET Framework WPF, existuje několik věcí, které musíte zvážit.</span><span class="sxs-lookup"><span data-stu-id="964e6-132">When porting a .NET Framework WPF application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="964e6-133">Zkontrolujte, že vaše aplikace je vhodným kandidátem pro migraci.</span><span class="sxs-lookup"><span data-stu-id="964e6-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="964e6-134">Použití [.NET Portability Analyzeru](../../standard/analyzers/portability-analyzer.md) chcete ověřit, jestli váš projekt bude migrovat na rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="964e6-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="964e6-135">Pokud váš projekt obsahuje problémy s .NET Core 3.0, analyzátor vám pomůže určit tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="964e6-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="964e6-136">Používáte jinou verzi WPF.</span><span class="sxs-lookup"><span data-stu-id="964e6-136">You're using a different version of WPF.</span></span>

    <span data-ttu-id="964e6-137">Pokud byla vydána .NET Core 3.0 ve verzi Preview 1, WPF se nepovedlo open source na Githubu.</span><span class="sxs-lookup"><span data-stu-id="964e6-137">When .NET Core 3.0 Preview 1 was released, WPF went open-source on GitHub.</span></span> <span data-ttu-id="964e6-138">Kód pro .NET Core WPF je základ kódu rozhraní .NET Framework WPF.</span><span class="sxs-lookup"><span data-stu-id="964e6-138">The code for .NET Core WPF is a fork of the .NET Framework WPF code base.</span></span> <span data-ttu-id="964e6-139">Je možné, existují určité rozdíly a vaše aplikace nebude portu.</span><span class="sxs-lookup"><span data-stu-id="964e6-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="964e6-140">[Windows Compatibility Pack] [ compat-pack] můžete migrovat.</span><span class="sxs-lookup"><span data-stu-id="964e6-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="964e6-141">Některá rozhraní API, které jsou k dispozici v rozhraní .NET Framework nejsou k dispozici v rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="964e6-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="964e6-142">[Windows Compatibility Pack] [ compat-pack] přidá mnohé z těchto rozhraní API a může pomoct vaší aplikace WPF, budou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="964e6-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your WPF app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="964e6-143">Aktualizujte balíčky NuGet používané vaším projektem.</span><span class="sxs-lookup"><span data-stu-id="964e6-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="964e6-144">Je vždy vhodné použít nejnovější verzi balíčků NuGet před nějaká migrace.</span><span class="sxs-lookup"><span data-stu-id="964e6-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="964e6-145">Pokud aplikace odkazuje na všechny balíčky NuGet, můžete je aktualizujte na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="964e6-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="964e6-146">Zajistěte, aby že vaše aplikace sestavena úspěšně.</span><span class="sxs-lookup"><span data-stu-id="964e6-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="964e6-147">Po upgradu, pokud nejsou žádné chyby balíčku, provést downgrade balíčku na nejnovější verzi, která nedojde k narušení kódu.</span><span class="sxs-lookup"><span data-stu-id="964e6-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="964e6-148">Visual Studio. 2019 ve verzi Preview nebo RC zatím nepodporuje WPF Designer pro .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="964e6-148">Visual Studio 2019 Preview/RC doesn't yet support the WPF Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="964e6-149">V současné době je potřeba nechat existující soubor projektu WPF rozhraní .NET Framework, pokud chcete použít Návrhář WPF v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="964e6-149">Currently, you need to keep your existing .NET Framework WPF project file if you want to use the WPF Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="964e6-150">Vytvořte nový projekt sady SDK</span><span class="sxs-lookup"><span data-stu-id="964e6-150">Create a new SDK project</span></span>

<span data-ttu-id="964e6-151">Nový projekt .NET Core 3.0, které vytvoříte, musí být v jiném adresáři z rozhraní .NET Framework projektu.</span><span class="sxs-lookup"><span data-stu-id="964e6-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="964e6-152">Pokud jsou oba ve stejném adresáři, můžete jej spustit do je v konfliktu se soubory, které jsou generovány v **obj** adresáře.</span><span class="sxs-lookup"><span data-stu-id="964e6-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="964e6-153">V tomto příkladu vytvoříte adresář s názvem **MyWPFAppCore** v **SolutionFolder** adresáře:</span><span class="sxs-lookup"><span data-stu-id="964e6-153">In this example, you'll create a directory named **MyWPFAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

<span data-ttu-id="964e6-154">V dalším kroku je potřeba vytvořit **MyWPFCore.csproj** projekt **MyWPFAppCore** adresáře.</span><span class="sxs-lookup"><span data-stu-id="964e6-154">Next, you need to create the **MyWPFCore.csproj** project in the **MyWPFAppCore** directory.</span></span> <span data-ttu-id="964e6-155">Můžete tento soubor můžete vytvořit ručně pomocí text editoru.</span><span class="sxs-lookup"><span data-stu-id="964e6-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="964e6-156">Vložte následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="964e6-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="964e6-157">Pokud nechcete vytvořit soubor projektu ručně, můžete použít ke generování projektu sady Visual Studio nebo .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="964e6-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="964e6-158">Nicméně je nutné odstranit všechny ostatní soubory vygenerovaná šablona projektu s výjimkou souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="964e6-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="964e6-159">Použití sady SDK, spusťte následující příkaz z **SolutionFolder** adresáře:</span><span class="sxs-lookup"><span data-stu-id="964e6-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

<span data-ttu-id="964e6-160">Po vytvoření **MyWPFCore.csproj**, strukturu by měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="964e6-160">After you create the **MyWPFCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

<span data-ttu-id="964e6-161">Bude potřeba přidat **MyWPFCore.csproj** projekt k **MyApps.sln** sadou Visual Studio nebo rozhraní příkazového řádku .NET Core z **SolutionFolder** adresáře:</span><span class="sxs-lookup"><span data-stu-id="964e6-161">You'll want to add the **MyWPFCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="964e6-162">Oprava generování informací o sestavení</span><span class="sxs-lookup"><span data-stu-id="964e6-162">Fix assembly info generation</span></span>

<span data-ttu-id="964e6-163">Windows Presentation Foundation projekty, které byly vytvořeny pomocí rozhraní .NET Framework zahrnují `AssemblyInfo.cs` soubor, který obsahuje sestavení atributům, jako je verze sestavení, které má být vygenerována.</span><span class="sxs-lookup"><span data-stu-id="964e6-163">Windows Presentation Foundation projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="964e6-164">Projekty založenými na sadě SDK automaticky vygenerovat tyto informace vám na základě souboru projektu sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="964e6-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="964e6-165">Oba typy "informace o sestavení" způsobí konflikt.</span><span class="sxs-lookup"><span data-stu-id="964e6-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="964e6-166">Tento problém vyřešit tím, že zakážete automatické generování, která vynutí projekt, který používá vaše existující `AssemblyInfo.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="964e6-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="964e6-167">Existují tři nastavení, chcete-li přidat hlavní `<PropertyGroup>` uzlu.</span><span class="sxs-lookup"><span data-stu-id="964e6-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- **<span data-ttu-id="964e6-168">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="964e6-168">GenerateAssemblyInfo</span></span>**\
<span data-ttu-id="964e6-169">Pokud nastavíte tuto vlastnost na `false`, nevygeneruje atributů sestavení.</span><span class="sxs-lookup"><span data-stu-id="964e6-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="964e6-170">Tím předejdete konfliktu s existujícím `AssemblyInfo.cs` soubor z rozhraní .NET Framework projektu.</span><span class="sxs-lookup"><span data-stu-id="964e6-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- **<span data-ttu-id="964e6-171">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="964e6-171">AssemblyName</span></span>**\
<span data-ttu-id="964e6-172">Hodnota této vlastnosti je binární výstup vytvořený při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="964e6-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="964e6-173">Název nemusí rozšíření do ní přidá.</span><span class="sxs-lookup"><span data-stu-id="964e6-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="964e6-174">Například použití `MyCoreApp` vytváří `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="964e6-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- **<span data-ttu-id="964e6-175">RootNamespace</span><span class="sxs-lookup"><span data-stu-id="964e6-175">RootNamespace</span></span>**\
<span data-ttu-id="964e6-176">Výchozí obor názvů použitou vaším projektem.</span><span class="sxs-lookup"><span data-stu-id="964e6-176">The default namespace used by your project.</span></span> <span data-ttu-id="964e6-177">Ten by měl odpovídat výchozí obor názvů rozhraní .NET Framework projektu.</span><span class="sxs-lookup"><span data-stu-id="964e6-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="964e6-178">Přidejte tyto tři prvky, aby `<PropertyGroup>` uzlu `MyWPFCore.csproj` souboru:</span><span class="sxs-lookup"><span data-stu-id="964e6-178">Add these three elements to the `<PropertyGroup>` node in the `MyWPFCore.csproj` file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a><span data-ttu-id="964e6-179">Přidejte zdrojový kód</span><span class="sxs-lookup"><span data-stu-id="964e6-179">Add source code</span></span>
<span data-ttu-id="964e6-180">Právě teď **MyWPFCore.csproj** projekt nebude kompilovat žádný kód.</span><span class="sxs-lookup"><span data-stu-id="964e6-180">Right now, the **MyWPFCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="964e6-181">Ve výchozím nastavení projekty .NET Core automaticky zahrnout všechny zdrojového kódu v aktuálním adresáři a všechny podřízené adresáře.</span><span class="sxs-lookup"><span data-stu-id="964e6-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="964e6-182">Je nutné nakonfigurovat projekt tak, aby zahrnout kód z rozhraní .NET Framework projektu pomocí relativní cesty.</span><span class="sxs-lookup"><span data-stu-id="964e6-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="964e6-183">Pokud rozhraní .NET Framework projekt používá **RESX** soubory ikon a materiály pro windows a ovládací prvky, budete muset zahrnout ty příliš.</span><span class="sxs-lookup"><span data-stu-id="964e6-183">If your .NET Framework project used **.resx** files for icons and resources for your windows and controls, you'll need to include those too.</span></span> 

<span data-ttu-id="964e6-184">První `<ItemGroup>` obsahuje uzel, je třeba přidat do projektu **App.xaml** soubor, který představuje spuštění config a prostředky aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="964e6-184">The first `<ItemGroup>` node you need to add to your project includes the **App.xaml** file that represents the startup config and resources your app uses.</span></span> <span data-ttu-id="964e6-185">**App.xaml** soubor má také je v doprovodné **App.xaml.cs** soubor, ale budou automaticky zahrnuty v jiné `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="964e6-185">The **App.xaml** file also has an accompanying **App.xaml.cs** file, but it will be automatically included in a different `<ItemGroup>`.</span></span>

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

<span data-ttu-id="964e6-186">V dalším kroku přidejte následující `<ItemGroup>` uzlu do projektu.</span><span class="sxs-lookup"><span data-stu-id="964e6-186">Next, add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="964e6-187">Každý výpis obsahuje vzor glob souboru, který obsahuje podadresáře.</span><span class="sxs-lookup"><span data-stu-id="964e6-187">Each statement includes a file glob pattern that includes child directories.</span></span> <span data-ttu-id="964e6-188">Obsahuje zdrojový kód pro váš projekt, všechny soubory nastavení a všechny prostředky.</span><span class="sxs-lookup"><span data-stu-id="964e6-188">It includes the source code for your project, any settings files, and any resources.</span></span> <span data-ttu-id="964e6-189">**Obj** adresář je explicitně vyloučeny.</span><span class="sxs-lookup"><span data-stu-id="964e6-189">The **obj** directory is explicitly excluded.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="964e6-190">V dalším kroku obsahovat jiné `<ItemGroup>` uzel, který obsahuje `<Page>` záznam pro každý **xaml** soubor v projektu s výjimkou **App.xaml** souboru.</span><span class="sxs-lookup"><span data-stu-id="964e6-190">Next, include another `<ItemGroup>` node that contains a `<Page>` entry for every **xaml** file in your project except the **App.xaml** file.</span></span> <span data-ttu-id="964e6-191">Ty obsahují všechny windows, stránek a prostředky, které jsou v **xaml** formátu.</span><span class="sxs-lookup"><span data-stu-id="964e6-191">These contain all of the windows, pages, and resources that are in **xaml** format.</span></span> <span data-ttu-id="964e6-192">Nelze použít model glob tady a musíte přidat záznam pro každý soubor a označení `<Generator>` použít.</span><span class="sxs-lookup"><span data-stu-id="964e6-192">You cannot use a glob pattern here and must add an entry for every file and indicate the `<Generator>` used.</span></span>

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a><span data-ttu-id="964e6-193">Přidání balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="964e6-193">Add NuGet packages</span></span>

<span data-ttu-id="964e6-194">Přidejte každý balíček NuGet rozhraní .NET Framework projektu do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="964e6-194">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="964e6-195">Pravděpodobně má vaše aplikace rozhraní .NET Framework WPF **souboru packages.config** soubor, který obsahuje seznam všech balíčků NuGet, na které odkazuje váš projekt.</span><span class="sxs-lookup"><span data-stu-id="964e6-195">Most likely your .NET Framework WPF app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="964e6-196">Můžete si prohlédnout tento seznam a určit, které balíčky NuGet pro přidání do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="964e6-196">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="964e6-197">Například, pokud rozhraní .NET Framework projekt odkazuje `MahApps.Metro` NuGet balíček, přidejte do projektu pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="964e6-197">For example, if the .NET Framework project references the `MahApps.Metro` NuGet package, add it to the project with Visual Studio.</span></span> <span data-ttu-id="964e6-198">Můžete také přidat odkaz na balíček pomocí rozhraní příkazového řádku .NET Core z **SolutionFolder** adresáře:</span><span class="sxs-lookup"><span data-stu-id="964e6-198">You can also add the package reference with the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

<span data-ttu-id="964e6-199">Předchozí příkaz přidejte následující odkaz NuGet na **MyWPFCore.csproj** projektu:</span><span class="sxs-lookup"><span data-stu-id="964e6-199">The previous command would add the following NuGet reference to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="964e6-200">Problémy kompilace</span><span class="sxs-lookup"><span data-stu-id="964e6-200">Problems compiling</span></span>

<span data-ttu-id="964e6-201">Pokud máte problémy sestavování vašich projektů, může pomocí některé API jen pro Windows, které jsou k dispozici v rozhraní .NET Framework, ale není k dispozici v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="964e6-201">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="964e6-202">Můžete zkusit přidat [Windows Compatibility Pack] [ compat-pack] do svého projektu balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="964e6-202">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="964e6-203">Tento balíček pouze běží na Windows a přidá přibližně 20 000 rozhraní Windows API pro projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="964e6-203">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="964e6-204">Předchozí příkaz přidá následující **MyWPFCore.csproj** projektu:</span><span class="sxs-lookup"><span data-stu-id="964e6-204">The previous command adds the following to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a><span data-ttu-id="964e6-205">návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="964e6-205">WPF Designer</span></span>

<span data-ttu-id="964e6-206">Jak je uvedeno v tomto článku podporuje Visual Studio. 2019 ve verzi Preview nebo RC Návrhář WPF pouze v projektech .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="964e6-206">As detailed in this article, Visual Studio 2019 Preview/RC only supports the WPF Designer in .NET Framework projects.</span></span> <span data-ttu-id="964e6-207">Tím, že vytvoříte projekt .NET Core vedle sebe, můžete otestovat projekt pomocí .NET Core při použití rozhraní .NET Framework projektu pro návrh formulářů.</span><span class="sxs-lookup"><span data-stu-id="964e6-207">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="964e6-208">Soubor řešení obsahuje projekty rozhraní .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="964e6-208">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="964e6-209">Přidat a návrh formulářů a ovládacích prvků v rozhraní .NET Framework projektu a na základě na vzory souborů glob jsme přidali do projektů .NET Core, všechny nové nebo změněné soubory se automaticky zahrnou v projektech .NET Core.</span><span class="sxs-lookup"><span data-stu-id="964e6-209">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="964e6-210">Jakmile Visual Studio 2019 podporuje návrháře WPF, můžete zkopírovat a vložit obsah souboru projektu .NET Core do souboru projektu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="964e6-210">Once Visual Studio 2019 supports the WPF Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="964e6-211">Odstraňte glob vzory souborů, přidá se `<Source>` a `<EmbeddedResource>` položky.</span><span class="sxs-lookup"><span data-stu-id="964e6-211">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="964e6-212">Vyřešte cest pro všechny odkazy projektu používají ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="964e6-212">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="964e6-213">To efektivně provede upgrade rozhraní .NET Framework projektu do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="964e6-213">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="964e6-214">Další kroky</span><span class="sxs-lookup"><span data-stu-id="964e6-214">Next steps</span></span>

* <span data-ttu-id="964e6-215">Další informace najdete [Windows Compatibility Pack][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="964e6-215">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
* <span data-ttu-id="964e6-216">Sledování [videa na přenos](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) WPF rozhraní .NET Framework projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="964e6-216">Watch a [video on porting](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) your .NET Framework WPF project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
