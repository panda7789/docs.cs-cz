---
title: Port, Windows Forms aplikaci .NET Core 3.0
description: Vás naučí, jak přenést aplikaci formulářů Windows rozhraní .NET Framework 3.0 .NET Core pro Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: aebfaa85338e014ca47256b85a1bd6529ad803bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327162"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="a239e-103">Postupy: Port desktopové aplikace Windows Forms až po .NET Core</span><span class="sxs-lookup"><span data-stu-id="a239e-103">How to: Port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="a239e-104">Tento článek popisuje, jak přenést na základě formulářů Windows desktopové aplikaci z rozhraní .NET Framework do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a239e-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="a239e-105">.NET Core 3.0 SDK obsahuje podporu pro aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a239e-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="a239e-106">Formuláře Windows je stále rozhraní jen pro Windows a pouze běží na Windows.</span><span class="sxs-lookup"><span data-stu-id="a239e-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="a239e-107">Tento příklad používá rozhraní příkazového řádku .NET Core SDK k vytváření a správě vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="a239e-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="a239e-108">V tomto článku najdete různé názvy umožňují určit typy souborů se používá pro migraci.</span><span class="sxs-lookup"><span data-stu-id="a239e-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="a239e-109">Při migraci vašeho projektu, soubory budou pojmenované jinak, takže duševně je přizpůsobit uvedené níže:</span><span class="sxs-lookup"><span data-stu-id="a239e-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="a239e-110">Soubor</span><span class="sxs-lookup"><span data-stu-id="a239e-110">File</span></span> | <span data-ttu-id="a239e-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a239e-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="a239e-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="a239e-112">**MyApps.sln**</span></span> | <span data-ttu-id="a239e-113">Název souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="a239e-113">The name of the solution file.</span></span> |
| <span data-ttu-id="a239e-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="a239e-114">**MyForms.csproj**</span></span> | <span data-ttu-id="a239e-115">Název projektu formulářů Windows rozhraní .NET Framework na port.</span><span class="sxs-lookup"><span data-stu-id="a239e-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="a239e-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="a239e-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="a239e-117">Název nového projektu .NET Core, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="a239e-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="a239e-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="a239e-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="a239e-119">Spustitelný soubor aplikace modelu Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a239e-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="a239e-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a239e-120">Prerequisites</span></span>

- <span data-ttu-id="a239e-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pro jakékoli návrháře práce, které chcete provést.</span><span class="sxs-lookup"><span data-stu-id="a239e-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="a239e-122">Instalace následujících úlohách sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="a239e-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="a239e-123">Vývoj desktopových aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="a239e-123">.NET desktop development</span></span>
  - <span data-ttu-id="a239e-124">Vývoj pro různé platformy .NET</span><span class="sxs-lookup"><span data-stu-id="a239e-124">.NET cross-platform development</span></span>

- <span data-ttu-id="a239e-125">Funkční projektu Windows Forms v řešení, které vytvoří a spustí bez problému.</span><span class="sxs-lookup"><span data-stu-id="a239e-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="a239e-126">Váš projekt musí být zakódované v C#.</span><span class="sxs-lookup"><span data-stu-id="a239e-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="a239e-127">Nainstalujte nejnovější [.NET Core 3.0](https://aka.ms/netcore3download) ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="a239e-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="a239e-128">**Visual Studio 2017** nepodporuje projekty .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a239e-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="a239e-129">**Visual Studio 2019** podporuje projekty .NET Core 3.0, ale zatím nepodporuje vizuálního návrháře pro projekty .NET Core 3.0 Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a239e-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="a239e-130">Do vizuálního návrháře použít, musí mít projekt .NET Windows Forms ve vašem řešení, která sdílí soubory formuláře s projektem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a239e-130">To use the visual designer, you must have a .NET Windows Forms project in your solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="a239e-131">Vezměte v úvahu</span><span class="sxs-lookup"><span data-stu-id="a239e-131">Consider</span></span>

<span data-ttu-id="a239e-132">Při přenesení aplikací rozhraní .NET Framework Windows Forms, existuje několik věcí, které musíte zvážit.</span><span class="sxs-lookup"><span data-stu-id="a239e-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="a239e-133">Zkontrolujte, že vaše aplikace je vhodným kandidátem pro migraci.</span><span class="sxs-lookup"><span data-stu-id="a239e-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="a239e-134">Použití [.NET Portability Analyzeru](../../standard/analyzers/portability-analyzer.md) chcete ověřit, jestli váš projekt bude migrovat na rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a239e-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="a239e-135">Pokud váš projekt obsahuje problémy s .NET Core 3.0, analyzátor vám pomůže určit tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="a239e-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="a239e-136">Používáte jinou verzi Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a239e-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="a239e-137">Pokud byla vydána .NET Core 3.0 ve verzi Preview 1, Windows Forms k nějaké open source na Githubu.</span><span class="sxs-lookup"><span data-stu-id="a239e-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open-source on GitHub.</span></span> <span data-ttu-id="a239e-138">Kód pro .NET Core Windows Forms je základ kódu rozhraní .NET Framework Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a239e-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms code base.</span></span> <span data-ttu-id="a239e-139">Je možné, existují určité rozdíly a vaše aplikace nebude portu.</span><span class="sxs-lookup"><span data-stu-id="a239e-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="a239e-140">[Windows Compatibility Pack] [ compat-pack] můžete migrovat.</span><span class="sxs-lookup"><span data-stu-id="a239e-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="a239e-141">Některá rozhraní API, které jsou k dispozici v rozhraní .NET Framework nejsou k dispozici v rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a239e-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="a239e-142">[Windows Compatibility Pack] [ compat-pack] přidá mnohé z těchto rozhraní API a může pomoct vaší aplikace Windows Forms, budou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a239e-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="a239e-143">Aktualizujte balíčky NuGet používané vaším projektem.</span><span class="sxs-lookup"><span data-stu-id="a239e-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="a239e-144">Je vždy vhodné použít nejnovější verzi balíčků NuGet před nějaká migrace.</span><span class="sxs-lookup"><span data-stu-id="a239e-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="a239e-145">Pokud aplikace odkazuje na všechny balíčky NuGet, můžete je aktualizujte na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="a239e-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="a239e-146">Zajistěte, aby že vaše aplikace sestavena úspěšně.</span><span class="sxs-lookup"><span data-stu-id="a239e-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="a239e-147">Po upgradu, pokud nejsou žádné chyby balíčku, provést downgrade balíčku na nejnovější verzi, která nedojde k narušení kódu.</span><span class="sxs-lookup"><span data-stu-id="a239e-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="a239e-148">Visual Studio 2019 zatím nepodporuje Návrháře formulářů pro .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a239e-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="a239e-149">V současné době je potřeba nechat existující soubor formulářů Windows rozhraní .NET Framework projektu, pokud chcete použít Návrhář formulářů ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a239e-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="a239e-150">Vytvořte nový projekt sady SDK</span><span class="sxs-lookup"><span data-stu-id="a239e-150">Create a new SDK project</span></span>

<span data-ttu-id="a239e-151">Nový projekt .NET Core 3.0, které vytvoříte, musí být v jiném adresáři z rozhraní .NET Framework projektu.</span><span class="sxs-lookup"><span data-stu-id="a239e-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="a239e-152">Pokud jsou oba ve stejném adresáři, můžete jej spustit do je v konfliktu se soubory, které jsou generovány v **obj** adresáře.</span><span class="sxs-lookup"><span data-stu-id="a239e-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="a239e-153">V tomto příkladu vytvoříme adresář s názvem **MyFormsAppCore** v **SolutionFolder** adresáře:</span><span class="sxs-lookup"><span data-stu-id="a239e-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="a239e-154">V dalším kroku je potřeba vytvořit **MyFormsCore.csproj** projekt **MyFormsAppCore** adresáře.</span><span class="sxs-lookup"><span data-stu-id="a239e-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="a239e-155">Můžete tento soubor můžete vytvořit ručně pomocí text editoru.</span><span class="sxs-lookup"><span data-stu-id="a239e-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="a239e-156">Vložte následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="a239e-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="a239e-157">Pokud nechcete vytvořit soubor projektu ručně, můžete použít ke generování projektu sady Visual Studio nebo .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a239e-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="a239e-158">Nicméně je nutné odstranit všechny ostatní soubory vygenerovaná šablona projektu s výjimkou souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="a239e-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="a239e-159">Použití sady SDK, spusťte následující příkaz z **SolutionFolder** adresáře:</span><span class="sxs-lookup"><span data-stu-id="a239e-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="a239e-160">Po vytvoření **MyFormsCore.csproj**, strukturu by měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="a239e-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="a239e-161">Bude potřeba přidat **MyFormsCore.csproj** projekt k **MyApps.sln** sadou Visual Studio nebo rozhraní příkazového řádku .NET Core z **SolutionFolder** adresáře:</span><span class="sxs-lookup"><span data-stu-id="a239e-161">You'll want to add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="a239e-162">Oprava generování informací o sestavení</span><span class="sxs-lookup"><span data-stu-id="a239e-162">Fix assembly info generation</span></span>

<span data-ttu-id="a239e-163">Windows Forms projekty, které byly vytvořeny pomocí rozhraní .NET Framework zahrnují `AssemblyInfo.cs` soubor, který obsahuje sestavení atributům, jako je verze sestavení, které má být vygenerována.</span><span class="sxs-lookup"><span data-stu-id="a239e-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="a239e-164">Projekty založenými na sadě SDK automaticky vygenerovat tyto informace vám na základě souboru projektu sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="a239e-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="a239e-165">Oba typy "informace o sestavení" způsobí konflikt.</span><span class="sxs-lookup"><span data-stu-id="a239e-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="a239e-166">Tento problém vyřešit tím, že zakážete automatické generování, která vynutí projekt, který používá vaše existující `AssemblyInfo.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="a239e-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="a239e-167">Existují tři nastavení, chcete-li přidat hlavní `<PropertyGroup>` uzlu.</span><span class="sxs-lookup"><span data-stu-id="a239e-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="a239e-168">**GenerateAssemblyInfo**\\</span><span class="sxs-lookup"><span data-stu-id="a239e-168">**GenerateAssemblyInfo**\\</span></span>
<span data-ttu-id="a239e-169">Pokud nastavíte tuto vlastnost na `false`, nevygeneruje atributů sestavení.</span><span class="sxs-lookup"><span data-stu-id="a239e-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="a239e-170">Tím předejdete konfliktu s existujícím `AssemblyInfo.cs` soubor z rozhraní .NET Framework projektu.</span><span class="sxs-lookup"><span data-stu-id="a239e-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="a239e-171">**AssemblyName**\\</span><span class="sxs-lookup"><span data-stu-id="a239e-171">**AssemblyName**\\</span></span>
<span data-ttu-id="a239e-172">Hodnota této vlastnosti je binární výstup vytvořený při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="a239e-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="a239e-173">Název nemusí rozšíření do ní přidá.</span><span class="sxs-lookup"><span data-stu-id="a239e-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="a239e-174">Například použití `MyCoreApp` vytváří `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="a239e-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="a239e-175">**RootNamespace**\\</span><span class="sxs-lookup"><span data-stu-id="a239e-175">**RootNamespace**\\</span></span>
<span data-ttu-id="a239e-176">Výchozí obor názvů použitou vaším projektem.</span><span class="sxs-lookup"><span data-stu-id="a239e-176">The default namespace used by your project.</span></span> <span data-ttu-id="a239e-177">Ten by měl odpovídat výchozí obor názvů rozhraní .NET Framework projektu.</span><span class="sxs-lookup"><span data-stu-id="a239e-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="a239e-178">Přidejte tyto tři prvky, aby `<PropertyGroup>` uzlu `MyFormsCore.csproj` souboru:</span><span class="sxs-lookup"><span data-stu-id="a239e-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>WindowsFormsApp1</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a><span data-ttu-id="a239e-179">Přidejte zdrojový kód</span><span class="sxs-lookup"><span data-stu-id="a239e-179">Add source code</span></span>

<span data-ttu-id="a239e-180">Právě teď **MyFormsCore.csproj** projekt nebude kompilovat žádný kód.</span><span class="sxs-lookup"><span data-stu-id="a239e-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="a239e-181">Ve výchozím nastavení projekty .NET Core automaticky zahrnout všechny zdrojového kódu v aktuálním adresáři a všechny podřízené adresáře.</span><span class="sxs-lookup"><span data-stu-id="a239e-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="a239e-182">Je nutné nakonfigurovat projekt tak, aby zahrnout kód z rozhraní .NET Framework projektu pomocí relativní cesty.</span><span class="sxs-lookup"><span data-stu-id="a239e-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="a239e-183">Pokud rozhraní .NET Framework projekt používá **RESX** soubory ikon a prostředky pro vaše formuláře, budete muset zahrnout ty příliš.</span><span class="sxs-lookup"><span data-stu-id="a239e-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span> 

<span data-ttu-id="a239e-184">Přidejte následující `<ItemGroup>` uzlu do projektu.</span><span class="sxs-lookup"><span data-stu-id="a239e-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="a239e-185">Každý výpis obsahuje vzor glob souboru, který obsahuje podadresáře.</span><span class="sxs-lookup"><span data-stu-id="a239e-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="a239e-186">Alternativně můžete vytvořit `<Compile>` nebo `<EmbeddedResource>` položku pro každý soubor v projektu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a239e-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="a239e-187">Přidání balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="a239e-187">Add NuGet packages</span></span>

<span data-ttu-id="a239e-188">Přidejte každý balíček NuGet rozhraní .NET Framework projektu do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a239e-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="a239e-189">Pravděpodobně má vaše aplikace rozhraní .NET Framework Windows Forms **souboru packages.config** soubor, který obsahuje seznam všech balíčků NuGet, na které odkazuje váš projekt.</span><span class="sxs-lookup"><span data-stu-id="a239e-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="a239e-190">Můžete si prohlédnout tento seznam a určit, které balíčky NuGet pro přidání do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a239e-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="a239e-191">Například, pokud rozhraní .NET Framework projektu odkazovat `MetroFramework`, `MetroFramework.Design`, a `MetroFramework.Fonts` balíčky NuGet, přidejte je do projektu pomocí sady Visual Studio nebo rozhraní příkazového řádku .NET Core z **SolutionFolder** adresáře :</span><span class="sxs-lookup"><span data-stu-id="a239e-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="a239e-192">Předchozích příkazů přidejte následující odkazy NuGet **MyFormsCore.csproj** projektu:</span><span class="sxs-lookup"><span data-stu-id="a239e-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="a239e-193">Port ovládacího prvku knihovny</span><span class="sxs-lookup"><span data-stu-id="a239e-193">Port control libraries</span></span>

<span data-ttu-id="a239e-194">Pokud máte projekt knihovny ovládacích prvků Windows Forms k portu, pokynů jsou stejné jako portování projektu aplikace rozhraní .NET Framework Windows Forms, s výjimkou několik nastavení.</span><span class="sxs-lookup"><span data-stu-id="a239e-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="a239e-195">A místo kompilace do spustitelného souboru, kompilaci do knihovny.</span><span class="sxs-lookup"><span data-stu-id="a239e-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="a239e-196">Rozdíl mezi spustitelný projekt a projekt knihovny, kromě cesty k souboru globy, obsahující zdrojový kód, je minimální.</span><span class="sxs-lookup"><span data-stu-id="a239e-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="a239e-197">Použijeme příklad v předchozím kroku, vám umožní rozšířit jaké projekty a soubory spolupracujeme s.</span><span class="sxs-lookup"><span data-stu-id="a239e-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="a239e-198">Soubor</span><span class="sxs-lookup"><span data-stu-id="a239e-198">File</span></span> | <span data-ttu-id="a239e-199">Popis</span><span class="sxs-lookup"><span data-stu-id="a239e-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="a239e-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="a239e-200">**MyApps.sln**</span></span> | <span data-ttu-id="a239e-201">Název souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="a239e-201">The name of the solution file.</span></span> |
| <span data-ttu-id="a239e-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="a239e-202">**MyControls.csproj**</span></span> | <span data-ttu-id="a239e-203">Název projektu .NET Framework Windows Forms ovládací prvky na port.</span><span class="sxs-lookup"><span data-stu-id="a239e-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="a239e-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="a239e-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="a239e-205">Název nového projektu knihovny .NET Core, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="a239e-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="a239e-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="a239e-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="a239e-207">Knihovna ovládacích prvků .NET Core Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a239e-207">The .NET Core Windows Forms Controls library.</span></span> |

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
├───MyFormsAppCore
│   └───MyFormsCore.csproj
│
├───MyFormsControls
│   └───MyControls.csproj
└───MyFormsControlsCore
    └───MyControlsCore.csproj   <--- New project for core controls
```

<span data-ttu-id="a239e-208">Zvažte rozdíly mezi `MyControlsCore.csproj` projektu a dříve vytvořený `MyFormsCore.csproj` projektu.</span><span class="sxs-lookup"><span data-stu-id="a239e-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

```diff
 <Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

   <PropertyGroup>
-    <OutputType>WinExe</OutputType>
     <TargetFramework>netcoreapp3.0</TargetFramework>
     <UseWindowsForms>true</UseWindowsForms>

     <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
-    <AssemblyName>MyCoreApp</AssemblyName>
-    <RootNamespace>WindowsFormsApp1</RootNamespace>
+    <AssemblyName>MyControlsCore</AssemblyName>
+    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
   </PropertyGroup>

   <ItemGroup>
-    <Compile Include="..\MyFormsApp\**\*.cs" />
-    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
+    <Compile Include="..\MyFormsControls\**\*.cs" />
+    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
   </ItemGroup>

 </Project>
```

<span data-ttu-id="a239e-209">Tady je příklad toho, co by vypadat soubor Knihovního projektu .NET Core Windows Forms ovládací prvky:</span><span class="sxs-lookup"><span data-stu-id="a239e-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreControls</AssemblyName>
    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
  </PropertyGroup>
  
  <ItemGroup>
    <Compile Include="..\MyFormsControls\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
  </ItemGroup>
  
</Project>
```

<span data-ttu-id="a239e-210">Jak je vidět, `<OutputType>` byl uzel odebrán, která má výchozí hodnotu kompilátor vytvoří knihovnu místo spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="a239e-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="a239e-211">`<AssemblyName>` a `<RootNamespace>` byly změněny.</span><span class="sxs-lookup"><span data-stu-id="a239e-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="a239e-212">Konkrétně `<RootNamespace>` by měl odpovídat oboru názvů jsou portování knihovny ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a239e-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="a239e-213">A nakonec `<Compile>` a `<EmbeddedResource>` uzly byly upraveny tak, aby odkazoval na složku knihovny ovládacích prvků Windows Forms jsou přenos.</span><span class="sxs-lookup"><span data-stu-id="a239e-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="a239e-214">Další hlavní .NET Core **MyFormsCore.csproj** projektu přidejte odkaz na knihovnu nového ovládacího prvku Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a239e-214">Next, in the main .NET Core **MyFormsCore.csproj** project add reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="a239e-215">Přidání odkazu pomocí sady Visual Studio nebo rozhraní příkazového řádku .NET Core z **SolutionFolder** adresáře:</span><span class="sxs-lookup"><span data-stu-id="a239e-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="a239e-216">Předchozí příkaz přidá následující **MyFormsCore.csproj** projektu:</span><span class="sxs-lookup"><span data-stu-id="a239e-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="a239e-217">Problémy kompilace</span><span class="sxs-lookup"><span data-stu-id="a239e-217">Problems compiling</span></span>

<span data-ttu-id="a239e-218">Pokud máte problémy sestavování vašich projektů, může pomocí některé API jen pro Windows, které jsou k dispozici v rozhraní .NET Framework, ale není k dispozici v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a239e-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="a239e-219">Můžete zkusit přidat [Windows Compatibility Pack] [ compat-pack] do svého projektu balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="a239e-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="a239e-220">Tento balíček pouze běží na Windows a přidá přibližně 20 000 rozhraní Windows API pro projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="a239e-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="a239e-221">Předchozí příkaz přidá následující **MyFormsCore.csproj** projektu:</span><span class="sxs-lookup"><span data-stu-id="a239e-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="a239e-222">Návrhář formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="a239e-222">Windows Forms Designer</span></span>

<span data-ttu-id="a239e-223">Jak je uvedeno v tomto článku Visual Studio 2019 pouze podporuje Návrhář formulářů v projektech .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a239e-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="a239e-224">Tím, že vytvoříte projekt .NET Core vedle sebe, můžete otestovat projekt pomocí .NET Core při použití rozhraní .NET Framework projektu pro návrh formulářů.</span><span class="sxs-lookup"><span data-stu-id="a239e-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="a239e-225">Soubor řešení obsahuje projekty rozhraní .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a239e-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="a239e-226">Přidat a návrh formulářů a ovládacích prvků v rozhraní .NET Framework projektu a na základě na vzory souborů glob jsme přidali do projektů .NET Core, všechny nové nebo změněné soubory se automaticky zahrnou v projektech .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a239e-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="a239e-227">Jakmile Visual Studio 2019 podporuje Návrhář formulářů Windows, můžete zkopírovat a vložit obsah souboru projektu .NET Core do souboru projektu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a239e-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="a239e-228">Odstraňte glob vzory souborů, přidá se `<Source>` a `<EmbeddedResource>` položky.</span><span class="sxs-lookup"><span data-stu-id="a239e-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="a239e-229">Vyřešte cest pro všechny odkazy projektu používají ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a239e-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="a239e-230">To efektivně provede upgrade rozhraní .NET Framework projektu do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a239e-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="a239e-231">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a239e-231">Next steps</span></span>

* <span data-ttu-id="a239e-232">Další informace najdete [Windows Compatibility Pack][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="a239e-232">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
* <span data-ttu-id="a239e-233">Sledování [videa na přenos](https://www.youtube.com/watch?v=upVQEUc_KwU) formulářů Windows rozhraní .NET Framework projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a239e-233">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
