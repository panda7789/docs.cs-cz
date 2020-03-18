---
title: Port aplikace Windows Forms na jádro .NET Core
description: Naučí vás portovat aplikaci .NET Framework Windows Forms do .NET Core pro Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.openlocfilehash: dbd522851faa0a4fe435199914a034ee230d3455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116021"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="d3879-103">Jak portovat desktopovou aplikaci pro Windows Forms do jádra .NET Core</span><span class="sxs-lookup"><span data-stu-id="d3879-103">How to port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="d3879-104">Tento článek popisuje, jak přenést desktopovou aplikaci založenou na formulářích Windows Forms z rozhraní .NET Framework na rozhraní .NET Core 3.0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="d3879-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0 or later.</span></span> <span data-ttu-id="d3879-105">Sada SDK .NET Core 3.0 obsahuje podporu aplikací windows forms.</span><span class="sxs-lookup"><span data-stu-id="d3879-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="d3879-106">Windows Forms je stále pouze windows framework a běží pouze v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d3879-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="d3879-107">Tento příklad používá rozhraní CLI sady .NET Core SDK k vytvoření a správě projektu.</span><span class="sxs-lookup"><span data-stu-id="d3879-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="d3879-108">V tomto článku se různé názvy používají k identifikaci typů souborů používaných pro migraci.</span><span class="sxs-lookup"><span data-stu-id="d3879-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="d3879-109">Při migraci projektu budou soubory pojmenovány jinak, takže je mentálně přiřazuje k níže uvedeným:</span><span class="sxs-lookup"><span data-stu-id="d3879-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="d3879-110">File</span><span class="sxs-lookup"><span data-stu-id="d3879-110">File</span></span> | <span data-ttu-id="d3879-111">Popis</span><span class="sxs-lookup"><span data-stu-id="d3879-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="d3879-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="d3879-112">**MyApps.sln**</span></span> | <span data-ttu-id="d3879-113">Název souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="d3879-113">The name of the solution file.</span></span> |
| <span data-ttu-id="d3879-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="d3879-114">**MyForms.csproj**</span></span> | <span data-ttu-id="d3879-115">Název projektu .NET Framework Windows Forms na port.</span><span class="sxs-lookup"><span data-stu-id="d3879-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="d3879-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="d3879-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="d3879-117">Název nového projektu .NET Core, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="d3879-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="d3879-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="d3879-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="d3879-119">Spustitelný soubor aplikace .NET Core Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3879-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="d3879-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3879-120">Prerequisites</span></span>

- <span data-ttu-id="d3879-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pro všechny návrháře práce, které chcete udělat.</span><span class="sxs-lookup"><span data-stu-id="d3879-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="d3879-122">Nainstalujte následující úlohy sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="d3879-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="d3879-123">Vývoj stolních počítačů .NET</span><span class="sxs-lookup"><span data-stu-id="d3879-123">.NET desktop development</span></span>
  - <span data-ttu-id="d3879-124">Vývoj aplikací pro různé platformy pomocí rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="d3879-124">.NET Core cross-platform development</span></span>

- <span data-ttu-id="d3879-125">Pracovní Windows Forms projektu v řešení, které se staví a běží bez problémů.</span><span class="sxs-lookup"><span data-stu-id="d3879-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="d3879-126">Projekt kódovaný v c#.</span><span class="sxs-lookup"><span data-stu-id="d3879-126">A project coded in C#.</span></span>
- <span data-ttu-id="d3879-127">[.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="d3879-127">[.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="d3879-128">**Visual Studio 2017** nepodporuje projekty .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d3879-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="d3879-129">**Visual Studio 2019** podporuje projekty .NET Core 3.0, ale ještě nepodporuje vizuální návrháře pro projekty .NET Core 3.0 Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3879-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="d3879-130">Chcete-li použít vizuální návrháře, musíte mít projekt .NET Windows Forms v řešení, které sdílí soubory formulářů s projektem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3879-130">To use the visual designer, you must have a .NET Windows Forms project in a solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="d3879-131">Zvážit</span><span class="sxs-lookup"><span data-stu-id="d3879-131">Consider</span></span>

<span data-ttu-id="d3879-132">Při přenosu aplikace .NET Framework Windows Forms je třeba zvážit několik věcí.</span><span class="sxs-lookup"><span data-stu-id="d3879-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="d3879-133">Zkontrolujte, zda je vaše aplikace dobrým kandidátem pro migraci.</span><span class="sxs-lookup"><span data-stu-id="d3879-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="d3879-134">Pomocí [analyzátoru přenosové schopnosti rozhraní .NET určete,](../../standard/analyzers/portability-analyzer.md) zda bude projekt migrovat na rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d3879-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="d3879-135">Pokud váš projekt má problémy s .NET Core 3.0, analyzátor vám pomůže identifikovat tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="d3879-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="d3879-136">Používáte jinou verzi Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3879-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="d3879-137">Když byl vydán .NET Core 3.0 Preview 1, Windows Forms šel open source na GitHub.</span><span class="sxs-lookup"><span data-stu-id="d3879-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="d3879-138">Kód pro .NET Core Windows Forms je rozpaky z codebase .NET Framework Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3879-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="d3879-139">Je možné, že existují určité rozdíly a vaše aplikace se nepřenese.</span><span class="sxs-lookup"><span data-stu-id="d3879-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="d3879-140">[Sada Kompatibilita systému Windows][compat-pack] vám může pomoci s migrací.</span><span class="sxs-lookup"><span data-stu-id="d3879-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="d3879-141">Některá rozhraní API, která jsou k dispozici v rozhraní .NET Framework, nejsou k dispozici v rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d3879-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="d3879-142">[Sada Windows Compatibility Pack][compat-pack] přidá mnoho z těchto rozhraní API a může pomoci vaší aplikaci Windows Forms stát se kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3879-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="d3879-143">Aktualizujte balíčky NuGet používané vaším projektem.</span><span class="sxs-lookup"><span data-stu-id="d3879-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="d3879-144">Je vždy vhodné použít nejnovější verze balíčků NuGet před jakoukoli migrací.</span><span class="sxs-lookup"><span data-stu-id="d3879-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="d3879-145">Pokud vaše aplikace odkazuje na všechny balíčky NuGet, aktualizujte je na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="d3879-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="d3879-146">Ujistěte se, že vaše aplikace úspěšně sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3879-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="d3879-147">Po upgradu, pokud existují nějaké chyby balíčku, downgrade balíček na nejnovější verzi, která nepřeruší váš kód.</span><span class="sxs-lookup"><span data-stu-id="d3879-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="d3879-148">Visual Studio 2019 ještě nepodporuje Návrhář e-uskutečně pro .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d3879-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="d3879-149">V současné době je třeba zachovat existující soubor projektu .NET Framework Windows Forms, pokud chcete použít Návrhář e-aplikací Z aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d3879-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="d3879-150">Vytvoření nového projektu sady SDK</span><span class="sxs-lookup"><span data-stu-id="d3879-150">Create a new SDK project</span></span>

<span data-ttu-id="d3879-151">Nový projekt .NET Core 3.0, který vytvoříte, musí být v jiném adresáři než projekt rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3879-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="d3879-152">Pokud jsou oba ve stejném adresáři, může dojít ke konfliktu se soubory, které jsou generovány v adresáři **obj.**</span><span class="sxs-lookup"><span data-stu-id="d3879-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="d3879-153">V tomto příkladu vytvoříme adresář s názvem **MyFormsAppCore** v adresáři **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="d3879-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="d3879-154">Dále je třeba vytvořit projekt **MyFormsCore.csproj** v adresáři **MyFormsAppCore.**</span><span class="sxs-lookup"><span data-stu-id="d3879-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="d3879-155">Tento soubor můžete vytvořit ručně pomocí textového editoru.</span><span class="sxs-lookup"><span data-stu-id="d3879-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="d3879-156">Vložte do následujícího xml:</span><span class="sxs-lookup"><span data-stu-id="d3879-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="d3879-157">Pokud nechcete vytvořit soubor projektu ručně, můžete ke generování projektu použít Visual Studio nebo .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d3879-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="d3879-158">Je však nutné odstranit všechny ostatní soubory generované šablonou projektu s výjimkou souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d3879-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="d3879-159">Chcete-li použít sadu SDK, spusťte z adresáře **SolutionFolder** následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d3879-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="d3879-160">Po vytvoření **souboru MyFormsCore.csproj**by měla adresářová struktura vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="d3879-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="d3879-161">Přidejte projekt **MyFormsCore.csproj** do **služby MyApps.sln** pomocí sady Visual Studio nebo rozhraní CLI jádra .NET z adresáře **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="d3879-161">Add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="d3879-162">Oprava generování informací o sestavě</span><span class="sxs-lookup"><span data-stu-id="d3879-162">Fix assembly info generation</span></span>

<span data-ttu-id="d3879-163">Projekty Windows Forms, které byly `AssemblyInfo.cs` vytvořeny pomocí rozhraní .NET Framework, obsahují soubor, který obsahuje atributy sestavení, jako je například verze sestavení, které má být generováno.</span><span class="sxs-lookup"><span data-stu-id="d3879-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="d3879-164">Projekty ve stylu sady SDK automaticky generují tyto informace na základě souboru projektu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="d3879-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="d3879-165">S oběma typy "sestavení info" vytvoří konflikt.</span><span class="sxs-lookup"><span data-stu-id="d3879-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="d3879-166">Vyřešte tento problém zakázáním automatického generování, `AssemblyInfo.cs` které vynutí, aby projekt používal existující soubor.</span><span class="sxs-lookup"><span data-stu-id="d3879-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="d3879-167">Existují tři nastavení, která `<PropertyGroup>` chcete přidat do hlavního uzlu.</span><span class="sxs-lookup"><span data-stu-id="d3879-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span>

- <span data-ttu-id="d3879-168">**Generovat informace o sestavení**</span><span class="sxs-lookup"><span data-stu-id="d3879-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="d3879-169">Když nastavíte `false`tuto vlastnost , nebude generovat atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3879-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="d3879-170">Tím se zabrání konfliktu `AssemblyInfo.cs` s existujícísoubor z projektu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3879-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="d3879-171">**Assemblyname**</span><span class="sxs-lookup"><span data-stu-id="d3879-171">**AssemblyName**</span></span>\
<span data-ttu-id="d3879-172">Hodnota této vlastnosti je výstupní binární vytvořené při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="d3879-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="d3879-173">Název nepotřebuje rozšíření, které k němu bylo přidáno.</span><span class="sxs-lookup"><span data-stu-id="d3879-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="d3879-174">Například pomocí `MyCoreApp` produkuje `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="d3879-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="d3879-175">**Rootnamespace**</span><span class="sxs-lookup"><span data-stu-id="d3879-175">**RootNamespace**</span></span>\
<span data-ttu-id="d3879-176">Výchozí obor názvů používaný projektem.</span><span class="sxs-lookup"><span data-stu-id="d3879-176">The default namespace used by your project.</span></span> <span data-ttu-id="d3879-177">To by mělo odpovídat výchozí obor názvů projektu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3879-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="d3879-178">Přidejte tyto tři `<PropertyGroup>` prvky `MyFormsCore.csproj` do uzlu v souboru:</span><span class="sxs-lookup"><span data-stu-id="d3879-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="d3879-179">Přidání zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="d3879-179">Add source code</span></span>

<span data-ttu-id="d3879-180">Právě teď projekt **MyFormsCore.csproj** nekompiluje žádný kód.</span><span class="sxs-lookup"><span data-stu-id="d3879-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="d3879-181">Ve výchozím nastavení projekty .NET Core automaticky zahrnují veškerý zdrojový kód v aktuálním adresáři a všechny podřízené adresáře.</span><span class="sxs-lookup"><span data-stu-id="d3879-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="d3879-182">Projekt je nutné nakonfigurovat tak, aby zahrnoval kód z projektu rozhraní .NET Framework pomocí relativní cesty.</span><span class="sxs-lookup"><span data-stu-id="d3879-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="d3879-183">Pokud váš projekt rozhraní .NET Framework používá soubory **.resx** pro ikony a prostředky pro formuláře, budete muset zahrnout i tyto.</span><span class="sxs-lookup"><span data-stu-id="d3879-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span>

<span data-ttu-id="d3879-184">Přidejte `<ItemGroup>` do projektu následující uzel.</span><span class="sxs-lookup"><span data-stu-id="d3879-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="d3879-185">Každý příkaz obsahuje vzor glob souboru, který obsahuje podřízené adresáře.</span><span class="sxs-lookup"><span data-stu-id="d3879-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="d3879-186">Případně můžete vytvořit `<Compile>` položku `<EmbeddedResource>` nebo pro každý soubor v projektu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3879-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="d3879-187">Přidání balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="d3879-187">Add NuGet packages</span></span>

<span data-ttu-id="d3879-188">Přidejte každý balíček NuGet, na který odkazuje projekt rozhraní .NET Framework, do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3879-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span>

<span data-ttu-id="d3879-189">S největší pravděpodobností vaše aplikace .NET Framework Windows Forms má soubor **packages.config,** který obsahuje seznam všech balíčků NuGet, na které odkazuje váš projekt.</span><span class="sxs-lookup"><span data-stu-id="d3879-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="d3879-190">Můžete se podívat na tento seznam k určení, které balíčky NuGet přidat do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3879-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="d3879-191">Například pokud projekt rozhraní .NET `MetroFramework`Framework `MetroFramework.Design`odkazuje `MetroFramework.Fonts` na balíčky , a NuGet, přidejte každý do projektu pomocí sady Visual Studio nebo rozhraní CLI jádra .NET z adresáře **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="d3879-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="d3879-192">Předchozí příkazy by přidat následující NuGet odkazy na projekt **MyFormsCore.csproj:**</span><span class="sxs-lookup"><span data-stu-id="d3879-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="d3879-193">Knihovny řízení portů</span><span class="sxs-lookup"><span data-stu-id="d3879-193">Port control libraries</span></span>

<span data-ttu-id="d3879-194">Pokud máte projekt knihovny Windows Forms Controls na port, pokyny jsou stejné jako portování projektu aplikace .NET Framework Windows Forms, s výjimkou několika nastavení.</span><span class="sxs-lookup"><span data-stu-id="d3879-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="d3879-195">A místo kompilace do spustitelného souboru zkompilujete do knihovny.</span><span class="sxs-lookup"><span data-stu-id="d3879-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="d3879-196">Rozdíl mezi spustitelný projekt a projekt knihovny, kromě cesty pro soubor globs, které obsahují zdrojový kód, je minimální.</span><span class="sxs-lookup"><span data-stu-id="d3879-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="d3879-197">Pomocí příkladu předchozího kroku umožňuje rozšířit projekty a soubory, se kterými pracujeme.</span><span class="sxs-lookup"><span data-stu-id="d3879-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="d3879-198">File</span><span class="sxs-lookup"><span data-stu-id="d3879-198">File</span></span> | <span data-ttu-id="d3879-199">Popis</span><span class="sxs-lookup"><span data-stu-id="d3879-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="d3879-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="d3879-200">**MyApps.sln**</span></span> | <span data-ttu-id="d3879-201">Název souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="d3879-201">The name of the solution file.</span></span> |
| <span data-ttu-id="d3879-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="d3879-202">**MyControls.csproj**</span></span> | <span data-ttu-id="d3879-203">Název projektu .NET Framework Windows Forms Controls na port.</span><span class="sxs-lookup"><span data-stu-id="d3879-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="d3879-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="d3879-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="d3879-205">Název nového projektu knihovny .NET Core, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="d3879-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="d3879-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="d3879-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="d3879-207">Knihovna .NET Core Windows Forms Controls.</span><span class="sxs-lookup"><span data-stu-id="d3879-207">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="d3879-208">Zvažte rozdíly mezi `MyControlsCore.csproj` projektem a `MyFormsCore.csproj` dříve vytvořeným projektem.</span><span class="sxs-lookup"><span data-stu-id="d3879-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="d3879-209">Zde je příklad toho, jak by vypadal soubor projektu knihovny .NET Core Windows Forms Controls:</span><span class="sxs-lookup"><span data-stu-id="d3879-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="d3879-210">Jak můžete vidět, `<OutputType>` uzel byl odebrán, což výchozí kompilátor vytvořit knihovnu namísto spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="d3879-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="d3879-211">A `<AssemblyName>` `<RootNamespace>` byly změněny.</span><span class="sxs-lookup"><span data-stu-id="d3879-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="d3879-212">Konkrétně `<RootNamespace>` by se měl shodovat s oborem názvů knihovny Ovládacíprvky systému Windows Forms, kterou portujete.</span><span class="sxs-lookup"><span data-stu-id="d3879-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="d3879-213">A nakonec `<Compile>` byly `<EmbeddedResource>` uzly a byly upraveny tak, aby ukazovaly na složku knihovny ovládacích prvků windows forms, kterou portujete.</span><span class="sxs-lookup"><span data-stu-id="d3879-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="d3879-214">Dále v hlavním projektu .NET Core **MyFormsCore.csproj** přidejte odkaz na novou knihovnu .NET Core Windows Forms Control.</span><span class="sxs-lookup"><span data-stu-id="d3879-214">Next, in the main .NET Core **MyFormsCore.csproj** project, add a reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="d3879-215">Přidejte odkaz s visual studio nebo rozhraní cli jádra .NET z adresáře **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="d3879-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="d3879-216">Předchozí příkaz přidá do projektu **MyFormsCore.csproj** následující:</span><span class="sxs-lookup"><span data-stu-id="d3879-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a><span data-ttu-id="d3879-217">Problémy s kompilací</span><span class="sxs-lookup"><span data-stu-id="d3879-217">Compilation problems</span></span>

<span data-ttu-id="d3879-218">Pokud máte problémy s kompilací projektů, je možné, že používáte některá rozhraní API pouze pro systém Windows, která jsou k dispozici v rozhraní .NET Framework, ale nejsou k dispozici v jádru .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3879-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="d3879-219">Můžete zkusit přidat balíček [Windows Compatibility Pack][compat-pack] NuGet do projektu.</span><span class="sxs-lookup"><span data-stu-id="d3879-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="d3879-220">Tento balíček běží pouze v systému Windows a přidá přibližně 20 000 rozhraní API systému Windows do projektů .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d3879-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="d3879-221">Předchozí příkaz přidá do projektu **MyFormsCore.csproj** následující:</span><span class="sxs-lookup"><span data-stu-id="d3879-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="d3879-222">Návrhář formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="d3879-222">Windows Forms Designer</span></span>

<span data-ttu-id="d3879-223">Jak je podrobně popsáno v tomto článku Visual Studio 2019 podporuje pouze Návrhář formulářů v projektech rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3879-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="d3879-224">Vytvořením projektu .NET Core vedle sebe můžete projekt otestovat pomocí .NET Core při použití projektu rozhraní .NET Framework k navrhování formulářů.</span><span class="sxs-lookup"><span data-stu-id="d3879-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="d3879-225">Soubor řešení obsahuje rozhraní .NET Framework i projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3879-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="d3879-226">Přidejte a navrhněte formuláře a ovládací prvky v projektu rozhraní .NET Framework a na základě vzorů glob souborů, které jsme přidali do projektů .NET Core, budou všechny nové nebo změněné soubory automaticky zahrnuty do projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3879-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="d3879-227">Jakmile Visual Studio 2019 podporuje Návrhář e-Windows Forms, můžete zkopírovat a vložit obsah souboru projektu .NET Core do souboru projektu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3879-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="d3879-228">Pak odstraňte vzorky glob `<Source>` souboru přidané s položkami a. `<EmbeddedResource>`</span><span class="sxs-lookup"><span data-stu-id="d3879-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="d3879-229">Opravte cesty k libovolnému odkazu na projekt, který vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="d3879-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="d3879-230">To efektivně upgraduje projekt rozhraní .NET Framework na projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3879-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d3879-231">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d3879-231">Next steps</span></span>

- <span data-ttu-id="d3879-232">Informace o [rozdělení změn z rozhraní .NET Framework na .NET Core](../compatibility/fx-core.md).</span><span class="sxs-lookup"><span data-stu-id="d3879-232">Learn about [breaking changes from .NET Framework to .NET Core](../compatibility/fx-core.md).</span></span>
- <span data-ttu-id="d3879-233">Přečtěte si další informace o [nástroji Windows Compatibility Pack][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="d3879-233">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="d3879-234">Podívejte se [na video o přenesení](https://www.youtube.com/watch?v=upVQEUc_KwU) projektu .NET Framework Windows Forms do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3879-234">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
