---
title: Port aplikace Windows Forms na jádro .NET Core
description: Naučí vás portovat aplikaci .NET Framework Windows Forms do .NET Core pro Windows.
author: Thraka
ms.author: adegeo
ms.date: 01/24/2020
ms.openlocfilehash: 80b4bb225d6a6748743d91a4c70e8b09c10cc94b
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635516"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="1bfe3-103">Jak portovat desktopovou aplikaci pro Windows Forms do jádra .NET Core</span><span class="sxs-lookup"><span data-stu-id="1bfe3-103">How to port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="1bfe3-104">Tento článek popisuje, jak přenést desktopovou aplikaci založenou na formulářích Windows Forms z rozhraní .NET Framework na rozhraní .NET Core 3.0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0 or later.</span></span> <span data-ttu-id="1bfe3-105">Sada SDK .NET Core 3.0 obsahuje podporu aplikací windows forms.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="1bfe3-106">Windows Forms je stále pouze windows framework a běží pouze v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="1bfe3-107">Tento příklad používá rozhraní CLI sady .NET Core SDK k vytvoření a správě projektu.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="1bfe3-108">V tomto článku se různé názvy používají k identifikaci typů souborů používaných pro migraci.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="1bfe3-109">Při migraci projektu budou soubory pojmenovány jinak, takže je mentálně přiřazuje k níže uvedeným:</span><span class="sxs-lookup"><span data-stu-id="1bfe3-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="1bfe3-110">File</span><span class="sxs-lookup"><span data-stu-id="1bfe3-110">File</span></span> | <span data-ttu-id="1bfe3-111">Popis</span><span class="sxs-lookup"><span data-stu-id="1bfe3-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="1bfe3-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-112">**MyApps.sln**</span></span> | <span data-ttu-id="1bfe3-113">Název souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-113">The name of the solution file.</span></span> |
| <span data-ttu-id="1bfe3-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-114">**MyForms.csproj**</span></span> | <span data-ttu-id="1bfe3-115">Název projektu .NET Framework Windows Forms na port.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="1bfe3-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="1bfe3-117">Název nového projektu .NET Core, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="1bfe3-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="1bfe3-119">Spustitelný soubor aplikace .NET Core Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="1bfe3-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1bfe3-120">Prerequisites</span></span>

- <span data-ttu-id="1bfe3-121">[Visual Studio 2019 16.5 Náhled 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) nebo novější pro jakoukoli práci návrháře, kterou chcete dělat.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-121">[Visual Studio 2019 16.5 Preview 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) or later for any designer work you want to do.</span></span> <span data-ttu-id="1bfe3-122">Doporučujeme aktualizovat na nejnovější [verzi aplikace Visual Studio preview](https://visualstudio.microsoft.com/vs/preview/)</span><span class="sxs-lookup"><span data-stu-id="1bfe3-122">We recommend to update to the latest [Preview version of Visual Studio](https://visualstudio.microsoft.com/vs/preview/)</span></span>

  <span data-ttu-id="1bfe3-123">Nainstalujte následující úlohy sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="1bfe3-123">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="1bfe3-124">Vývoj stolních počítačů .NET</span><span class="sxs-lookup"><span data-stu-id="1bfe3-124">.NET desktop development</span></span>
  - <span data-ttu-id="1bfe3-125">Vývoj aplikací pro různé platformy pomocí rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="1bfe3-125">.NET Core cross-platform development</span></span>

- <span data-ttu-id="1bfe3-126">Pracovní Windows Forms projektu v řešení, které se staví a běží bez problémů.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-126">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="1bfe3-127">Projekt kódovaný v c#.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-127">A project coded in C#.</span></span>

> [!NOTE]
> <span data-ttu-id="1bfe3-128">Projekty .NET Core 3.0 jsou podporovány pouze v **sadě Visual Studio 2019** nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-128">.NET Core 3.0 projects are only supported in **Visual Studio 2019** or a later version.</span></span> <span data-ttu-id="1bfe3-129">Počínaje **Visual Studio 2019 verze 16.5 Náhled 1**, návrhář .NET Core Windows Forms je také podporována.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-129">Starting with **Visual Studio 2019 version 16.5 Preview 1**, the .NET Core Windows Forms designer is also supported.</span></span>
>
> <span data-ttu-id="1bfe3-130">Pokud chcete návrháře povolit, **přejděte** > na Nástroje**Možnosti** > **prostředí** > **Preview a** vyberte možnost Použít **návrháře Windows Forms pro aplikace .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-130">To enable the designer, go to **Tools** > **Options** > **Environment** > **Preview Features** and select the **Use the preview Windows Forms designer for .NET Core apps** option.</span></span>

### <a name="consider"></a><span data-ttu-id="1bfe3-131">Zvážit</span><span class="sxs-lookup"><span data-stu-id="1bfe3-131">Consider</span></span>

<span data-ttu-id="1bfe3-132">Při přenosu aplikace .NET Framework Windows Forms je třeba zvážit několik věcí.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="1bfe3-133">Zkontrolujte, zda je vaše aplikace dobrým kandidátem pro migraci.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="1bfe3-134">Pomocí [analyzátoru přenosové schopnosti rozhraní .NET určete,](../../standard/analyzers/portability-analyzer.md) zda bude projekt migrovat na rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="1bfe3-135">Pokud váš projekt má problémy s .NET Core 3.0, analyzátor vám pomůže identifikovat tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="1bfe3-136">Používáte jinou verzi Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="1bfe3-137">Když byl vydán .NET Core 3.0 Preview 1, Windows Forms šel open source na GitHub.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="1bfe3-138">Kód pro .NET Core Windows Forms je rozpaky z codebase .NET Framework Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="1bfe3-139">Je možné, že existují určité rozdíly a vaše aplikace se nepřenese.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="1bfe3-140">[Sada Kompatibilita systému Windows][compat-pack] vám může pomoci s migrací.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="1bfe3-141">Některá rozhraní API, která jsou k dispozici v rozhraní .NET Framework, nejsou k dispozici v rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="1bfe3-142">[Sada Windows Compatibility Pack][compat-pack] přidá mnoho z těchto rozhraní API a může pomoci vaší aplikaci Windows Forms stát se kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="1bfe3-143">Aktualizujte balíčky NuGet používané vaším projektem.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="1bfe3-144">Je vždy vhodné použít nejnovější verze balíčků NuGet před jakoukoli migrací.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="1bfe3-145">Pokud vaše aplikace odkazuje na všechny balíčky NuGet, aktualizujte je na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="1bfe3-146">Ujistěte se, že vaše aplikace úspěšně sestavení.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="1bfe3-147">Po upgradu, pokud existují nějaké chyby balíčku, downgrade balíček na nejnovější verzi, která nepřeruší váš kód.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="1bfe3-148">Vytvoření nového projektu sady SDK</span><span class="sxs-lookup"><span data-stu-id="1bfe3-148">Create a new SDK project</span></span>

<span data-ttu-id="1bfe3-149">Nový projekt .NET Core 3.0, který vytvoříte, musí být v jiném adresáři než projekt rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-149">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="1bfe3-150">Pokud jsou oba ve stejném adresáři, může dojít ke konfliktu se soubory, které jsou generovány v adresáři **obj.**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-150">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="1bfe3-151">V tomto příkladu vytvoříme adresář s názvem **MyFormsAppCore** v adresáři **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-151">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="1bfe3-152">Dále je třeba vytvořit projekt **MyFormsCore.csproj** v adresáři **MyFormsAppCore.**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-152">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="1bfe3-153">Tento soubor můžete vytvořit ručně pomocí textového editoru.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-153">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="1bfe3-154">Vložte do následujícího xml:</span><span class="sxs-lookup"><span data-stu-id="1bfe3-154">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="1bfe3-155">Pokud nechcete vytvořit soubor projektu ručně, můžete ke generování projektu použít Visual Studio nebo .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-155">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="1bfe3-156">Je však nutné odstranit všechny ostatní soubory generované šablonou projektu s výjimkou souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-156">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="1bfe3-157">Chcete-li použít sadu SDK, spusťte z adresáře **SolutionFolder** následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1bfe3-157">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="1bfe3-158">Po vytvoření **souboru MyFormsCore.csproj**by měla adresářová struktura vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1bfe3-158">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="1bfe3-159">Přidejte projekt **MyFormsCore.csproj** do **služby MyApps.sln** pomocí sady Visual Studio nebo rozhraní CLI jádra .NET z adresáře **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-159">Add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="1bfe3-160">Oprava generování informací o sestavě</span><span class="sxs-lookup"><span data-stu-id="1bfe3-160">Fix assembly info generation</span></span>

<span data-ttu-id="1bfe3-161">Projekty Windows Forms, které byly `AssemblyInfo.cs` vytvořeny pomocí rozhraní .NET Framework, obsahují soubor, který obsahuje atributy sestavení, jako je například verze sestavení, které má být generováno.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-161">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="1bfe3-162">Projekty ve stylu sady SDK automaticky generují tyto informace na základě souboru projektu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-162">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="1bfe3-163">S oběma typy "sestavení info" vytvoří konflikt.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-163">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="1bfe3-164">Vyřešte tento problém zakázáním automatického generování, `AssemblyInfo.cs` které vynutí, aby projekt používal existující soubor.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-164">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="1bfe3-165">Existují tři nastavení, která `<PropertyGroup>` chcete přidat do hlavního uzlu.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-165">There are three settings to add to the main `<PropertyGroup>` node.</span></span>

- <span data-ttu-id="1bfe3-166">**Generovat informace o sestavení**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-166">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="1bfe3-167">Když nastavíte `false`tuto vlastnost , nebude generovat atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-167">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="1bfe3-168">Tím se zabrání konfliktu `AssemblyInfo.cs` s existujícísoubor z projektu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-168">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="1bfe3-169">**Assemblyname**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-169">**AssemblyName**</span></span>\
<span data-ttu-id="1bfe3-170">Hodnota této vlastnosti je výstupní binární vytvořené při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-170">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="1bfe3-171">Název nepotřebuje rozšíření, které k němu bylo přidáno.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-171">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="1bfe3-172">Například pomocí `MyCoreApp` produkuje `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-172">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="1bfe3-173">**Rootnamespace**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-173">**RootNamespace**</span></span>\
<span data-ttu-id="1bfe3-174">Výchozí obor názvů používaný projektem.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-174">The default namespace used by your project.</span></span> <span data-ttu-id="1bfe3-175">To by mělo odpovídat výchozí obor názvů projektu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-175">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="1bfe3-176">Přidejte tyto tři `<PropertyGroup>` prvky `MyFormsCore.csproj` do uzlu v souboru:</span><span class="sxs-lookup"><span data-stu-id="1bfe3-176">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="1bfe3-177">Přidání zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="1bfe3-177">Add source code</span></span>

<span data-ttu-id="1bfe3-178">Právě teď projekt **MyFormsCore.csproj** nekompiluje žádný kód.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-178">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="1bfe3-179">Ve výchozím nastavení projekty .NET Core automaticky zahrnují veškerý zdrojový kód v aktuálním adresáři a všechny podřízené adresáře.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-179">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="1bfe3-180">Projekt je nutné nakonfigurovat tak, aby zahrnoval kód z projektu rozhraní .NET Framework pomocí relativní cesty.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-180">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="1bfe3-181">Pokud váš projekt rozhraní .NET Framework používá soubory **.resx** pro ikony a prostředky pro formuláře, budete muset zahrnout i tyto.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-181">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span>

<span data-ttu-id="1bfe3-182">Přidejte `<ItemGroup>` do projektu následující uzel.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-182">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="1bfe3-183">Každý příkaz obsahuje vzor glob souboru, který obsahuje podřízené adresáře.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-183">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="1bfe3-184">Případně můžete vytvořit `<Compile>` položku `<EmbeddedResource>` nebo pro každý soubor v projektu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-184">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="1bfe3-185">Přidání balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="1bfe3-185">Add NuGet packages</span></span>

<span data-ttu-id="1bfe3-186">Přidejte každý balíček NuGet, na který odkazuje projekt rozhraní .NET Framework, do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-186">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span>

<span data-ttu-id="1bfe3-187">S největší pravděpodobností vaše aplikace .NET Framework Windows Forms má soubor **packages.config,** který obsahuje seznam všech balíčků NuGet, na které odkazuje váš projekt.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-187">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="1bfe3-188">Můžete se podívat na tento seznam k určení, které balíčky NuGet přidat do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-188">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="1bfe3-189">Například pokud projekt rozhraní .NET `MetroFramework`Framework `MetroFramework.Design`odkazuje `MetroFramework.Fonts` na balíčky , a NuGet, přidejte každý do projektu pomocí sady Visual Studio nebo rozhraní CLI jádra .NET z adresáře **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-189">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="1bfe3-190">Předchozí příkazy by přidat následující NuGet odkazy na projekt **MyFormsCore.csproj:**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-190">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="1bfe3-191">Knihovny řízení portů</span><span class="sxs-lookup"><span data-stu-id="1bfe3-191">Port control libraries</span></span>

<span data-ttu-id="1bfe3-192">Pokud máte projekt knihovny Windows Forms Controls na port, pokyny jsou stejné jako portování projektu aplikace .NET Framework Windows Forms, s výjimkou několika nastavení.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-192">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="1bfe3-193">A místo kompilace do spustitelného souboru zkompilujete do knihovny.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-193">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="1bfe3-194">Rozdíl mezi spustitelný projekt a projekt knihovny, kromě cesty pro soubor globs, které obsahují zdrojový kód, je minimální.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-194">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="1bfe3-195">Pomocí příkladu předchozího kroku umožňuje rozšířit projekty a soubory, se kterými pracujeme.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-195">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="1bfe3-196">File</span><span class="sxs-lookup"><span data-stu-id="1bfe3-196">File</span></span> | <span data-ttu-id="1bfe3-197">Popis</span><span class="sxs-lookup"><span data-stu-id="1bfe3-197">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="1bfe3-198">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-198">**MyApps.sln**</span></span> | <span data-ttu-id="1bfe3-199">Název souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-199">The name of the solution file.</span></span> |
| <span data-ttu-id="1bfe3-200">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-200">**MyControls.csproj**</span></span> | <span data-ttu-id="1bfe3-201">Název projektu .NET Framework Windows Forms Controls na port.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-201">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="1bfe3-202">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-202">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="1bfe3-203">Název nového projektu knihovny .NET Core, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-203">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="1bfe3-204">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-204">**MyCoreControls.dll**</span></span> | <span data-ttu-id="1bfe3-205">Knihovna .NET Core Windows Forms Controls.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-205">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="1bfe3-206">Zvažte rozdíly mezi `MyControlsCore.csproj` projektem a `MyFormsCore.csproj` dříve vytvořeným projektem.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-206">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="1bfe3-207">Zde je příklad toho, jak by vypadal soubor projektu knihovny .NET Core Windows Forms Controls:</span><span class="sxs-lookup"><span data-stu-id="1bfe3-207">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="1bfe3-208">Jak můžete vidět, `<OutputType>` uzel byl odebrán, což výchozí kompilátor vytvořit knihovnu namísto spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-208">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="1bfe3-209">A `<AssemblyName>` `<RootNamespace>` byly změněny.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-209">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="1bfe3-210">Konkrétně `<RootNamespace>` by se měl shodovat s oborem názvů knihovny Ovládacíprvky systému Windows Forms, kterou portujete.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-210">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="1bfe3-211">A nakonec `<Compile>` byly `<EmbeddedResource>` uzly a byly upraveny tak, aby ukazovaly na složku knihovny ovládacích prvků windows forms, kterou portujete.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-211">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="1bfe3-212">Dále v hlavním projektu .NET Core **MyFormsCore.csproj** přidejte odkaz na novou knihovnu .NET Core Windows Forms Control.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-212">Next, in the main .NET Core **MyFormsCore.csproj** project, add a reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="1bfe3-213">Přidejte odkaz s visual studio nebo rozhraní cli jádra .NET z adresáře **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="1bfe3-213">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="1bfe3-214">Předchozí příkaz přidá do projektu **MyFormsCore.csproj** následující:</span><span class="sxs-lookup"><span data-stu-id="1bfe3-214">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a><span data-ttu-id="1bfe3-215">Problémy s kompilací</span><span class="sxs-lookup"><span data-stu-id="1bfe3-215">Compilation problems</span></span>

<span data-ttu-id="1bfe3-216">Pokud máte problémy s kompilací projektů, je možné, že používáte některá rozhraní API pouze pro systém Windows, která jsou k dispozici v rozhraní .NET Framework, ale nejsou k dispozici v jádru .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-216">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="1bfe3-217">Můžete zkusit přidat balíček [Windows Compatibility Pack][compat-pack] NuGet do projektu.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-217">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="1bfe3-218">Tento balíček běží pouze v systému Windows a přidá přibližně 20 000 rozhraní API systému Windows do projektů .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-218">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="1bfe3-219">Předchozí příkaz přidá do projektu **MyFormsCore.csproj** následující:</span><span class="sxs-lookup"><span data-stu-id="1bfe3-219">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="1bfe3-220">Návrhář formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="1bfe3-220">Windows Forms Designer</span></span>

<span data-ttu-id="1bfe3-221">Jak je podrobně popsáno v tomto článku Visual Studio 2019 podporuje pouze Návrhář formulářů v projektech rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-221">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="1bfe3-222">Vytvořením projektu .NET Core vedle sebe můžete projekt otestovat pomocí .NET Core při použití projektu rozhraní .NET Framework k navrhování formulářů.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-222">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="1bfe3-223">Soubor řešení obsahuje rozhraní .NET Framework i projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-223">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="1bfe3-224">Přidejte a navrhněte formuláře a ovládací prvky v projektu rozhraní .NET Framework a na základě vzorů glob souborů, které jsme přidali do projektů .NET Core, budou všechny nové nebo změněné soubory automaticky zahrnuty do projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-224">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="1bfe3-225">Jakmile Visual Studio 2019 podporuje Návrhář e-Windows Forms, můžete zkopírovat a vložit obsah souboru projektu .NET Core do souboru projektu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-225">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="1bfe3-226">Pak odstraňte vzorky glob `<Source>` souboru přidané s položkami a. `<EmbeddedResource>`</span><span class="sxs-lookup"><span data-stu-id="1bfe3-226">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="1bfe3-227">Opravte cesty k libovolnému odkazu na projekt, který vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-227">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="1bfe3-228">To efektivně upgraduje projekt rozhraní .NET Framework na projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-228">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1bfe3-229">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1bfe3-229">Next steps</span></span>

- <span data-ttu-id="1bfe3-230">Informace o [rozdělení změn z rozhraní .NET Framework na .NET Core](../compatibility/fx-core.md).</span><span class="sxs-lookup"><span data-stu-id="1bfe3-230">Learn about [breaking changes from .NET Framework to .NET Core](../compatibility/fx-core.md).</span></span>
- <span data-ttu-id="1bfe3-231">Přečtěte si další informace o [nástroji Windows Compatibility Pack][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="1bfe3-231">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="1bfe3-232">Podívejte se [na video o přenesení](https://www.youtube.com/watch?v=upVQEUc_KwU) projektu .NET Framework Windows Forms do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1bfe3-232">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
