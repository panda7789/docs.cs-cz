---
title: Portování aplikace WPF na .NET Core 3,0
description: Naučíte se, jak portovat .NET Framework Windows Presentation Foundation aplikace do .NET Core 3,0 pro Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 9885f666e68b795b9b6aba9cf31f9750e30fd170
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512287"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a><span data-ttu-id="476cc-103">Postupy: Port desktopové aplikace WPF na .NET Core</span><span class="sxs-lookup"><span data-stu-id="476cc-103">How to: Port a WPF desktop app to .NET Core</span></span>

<span data-ttu-id="476cc-104">Tento článek popisuje, jak přenést vaši desktopovou aplikaci založenou na Windows Presentation Foundation (WPF) z .NET Framework na .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="476cc-104">This article describes how to port your Windows Presentation Foundation-based (WPF) desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="476cc-105">Sada .NET Core 3,0 SDK obsahuje podporu pro aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="476cc-105">The .NET Core 3.0 SDK includes support for WPF applications.</span></span> <span data-ttu-id="476cc-106">WPF je stále rozhraním jenom pro Windows a běží jenom v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="476cc-106">WPF is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="476cc-107">V tomto příkladu se k vytvoření a správě projektu používá rozhraní příkazového řádku .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="476cc-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="476cc-108">V tomto článku se k identifikaci typů souborů používaných k migraci používají různé názvy.</span><span class="sxs-lookup"><span data-stu-id="476cc-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="476cc-109">Při migraci projektu budou soubory pojmenovány jinak, takže je bude možné navzájem narovnávat na ty, které jsou uvedeny níže:</span><span class="sxs-lookup"><span data-stu-id="476cc-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="476cc-110">Soubor</span><span class="sxs-lookup"><span data-stu-id="476cc-110">File</span></span> | <span data-ttu-id="476cc-111">Popis</span><span class="sxs-lookup"><span data-stu-id="476cc-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="476cc-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="476cc-112">**MyApps.sln**</span></span> | <span data-ttu-id="476cc-113">Název souboru řešení</span><span class="sxs-lookup"><span data-stu-id="476cc-113">The name of the solution file.</span></span> |
| <span data-ttu-id="476cc-114">**MyWPF.csproj**</span><span class="sxs-lookup"><span data-stu-id="476cc-114">**MyWPF.csproj**</span></span> | <span data-ttu-id="476cc-115">Název .NET Frameworkho projektu WPF na port.</span><span class="sxs-lookup"><span data-stu-id="476cc-115">The name of the .NET Framework WPF project to port.</span></span> |
| <span data-ttu-id="476cc-116">**MyWPFCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="476cc-116">**MyWPFCore.csproj**</span></span> | <span data-ttu-id="476cc-117">Název nového projektu .NET Core, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="476cc-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="476cc-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="476cc-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="476cc-119">Spustitelný soubor aplikace WPF .NET Core</span><span class="sxs-lookup"><span data-stu-id="476cc-119">The .NET Core WPF app executable.</span></span> |

>[!IMPORTANT]
><span data-ttu-id="476cc-120">I když tento článek používá C# jako cílový jazyk, postup je stejný pro VB.NET, s tím rozdílem, že VB.NET používá soubory *. vbproj* a. *VB* namísto souborů *. csproj* a *. cs* v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="476cc-120">Even though this article uses C# as the target language, the steps are the same for VB.NET, except that VB.NET uses *.vbproj* and *.vb* files instead of *.csproj* and *.cs* files, respectively.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="476cc-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="476cc-121">Prerequisites</span></span>

- <span data-ttu-id="476cc-122">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pro každou práci návrháře, kterou chcete provést.</span><span class="sxs-lookup"><span data-stu-id="476cc-122">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="476cc-123">Nainstalujte následující úlohy sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="476cc-123">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="476cc-124">Vývoj desktopových aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="476cc-124">.NET desktop development</span></span>
  - <span data-ttu-id="476cc-125">Vývoj pro různé platformy .NET</span><span class="sxs-lookup"><span data-stu-id="476cc-125">.NET cross-platform development</span></span>

- <span data-ttu-id="476cc-126">Pracovní projekt WPF v řešení, které sestaví a spouští bez problémů.</span><span class="sxs-lookup"><span data-stu-id="476cc-126">A working WPF project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="476cc-127">Nainstalujte nejnovější verzi [.NET Core 3,0](https://aka.ms/netcore3download) Preview.</span><span class="sxs-lookup"><span data-stu-id="476cc-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="476cc-128">**Visual Studio 2017** nepodporuje projekty .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="476cc-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="476cc-129">**Visual Studio 2019** podporuje projekty .net Core 3,0, ale má omezené podpory pro vizuální návrháře WPF .NET Core.</span><span class="sxs-lookup"><span data-stu-id="476cc-129">**Visual Studio 2019** supports .NET Core 3.0 projects but has limited support for the .NET Core WPF visual designer.</span></span> <span data-ttu-id="476cc-130">Chcete-li použít plně podporovaný vizuální Návrhář, musíte mít ve svém řešení .NET Framework projekt WPF, který sdílí své soubory s projektem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="476cc-130">To use a fully-supported visual designer, you must have a .NET Framework WPF project in your solution that shares its files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="476cc-131">Byste</span><span class="sxs-lookup"><span data-stu-id="476cc-131">Consider</span></span>

<span data-ttu-id="476cc-132">Při přenosu .NET Framework aplikace WPF existuje několik věcí, které je třeba vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="476cc-132">When porting a .NET Framework WPF application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="476cc-133">Ověřte, že je vaše aplikace vhodným kandidátem na migraci.</span><span class="sxs-lookup"><span data-stu-id="476cc-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="476cc-134">Pomocí [analyzátoru přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) určete, jestli se váš projekt migruje na .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="476cc-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="476cc-135">Pokud má váš projekt problémy s rozhraním .NET Core 3,0, analyzátor vám pomůže tyto problémy identifikovat.</span><span class="sxs-lookup"><span data-stu-id="476cc-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="476cc-136">Používáte jinou verzi WPF.</span><span class="sxs-lookup"><span data-stu-id="476cc-136">You're using a different version of WPF.</span></span>

    <span data-ttu-id="476cc-137">Po vydání .NET Core 3,0 Preview 1 se WPF na GitHubu otevře jako zdroj.</span><span class="sxs-lookup"><span data-stu-id="476cc-137">When .NET Core 3.0 Preview 1 was released, WPF went open-source on GitHub.</span></span> <span data-ttu-id="476cc-138">Kód pro .NET Core WPF je rozvětvení .NET Framework základu kódu WPF.</span><span class="sxs-lookup"><span data-stu-id="476cc-138">The code for .NET Core WPF is a fork of the .NET Framework WPF code base.</span></span> <span data-ttu-id="476cc-139">Je možné, že existují nějaké rozdíly a vaše aplikace nebude portem.</span><span class="sxs-lookup"><span data-stu-id="476cc-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="476cc-140">[Sada Windows Compatibility Pack][compat-pack] vám může při migraci trvat.</span><span class="sxs-lookup"><span data-stu-id="476cc-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="476cc-141">V rozhraní .NET Core 3,0 nejsou k dispozici některá rozhraní API, která jsou k dispozici v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="476cc-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="476cc-142">[Sada Windows Compatibility Pack][compat-pack] přidává mnoho těchto rozhraní API a může pomáhat vaší aplikaci WPF bude kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="476cc-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your WPF app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="476cc-143">Aktualizujte balíčky NuGet používané vaším projektem.</span><span class="sxs-lookup"><span data-stu-id="476cc-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="476cc-144">Před migrací je vždycky vhodné použít nejnovější verze balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="476cc-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="476cc-145">Pokud vaše aplikace odkazuje na balíčky NuGet, aktualizujte je na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="476cc-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="476cc-146">Ujistěte se, že vaše aplikace byla úspěšně vytvořena.</span><span class="sxs-lookup"><span data-stu-id="476cc-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="476cc-147">Pokud při upgradu dojde k chybám balíčku, proveďte downgrade balíčku na nejnovější verzi, která nepřerušila váš kód.</span><span class="sxs-lookup"><span data-stu-id="476cc-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="476cc-148">Visual Studio 2019 zatím nepodporuje návrháře WPF pro .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="476cc-148">Visual Studio 2019 doesn't yet support the WPF Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="476cc-149">V současné době je nutné zachovat existující .NET Framework soubor projektu WPF, pokud chcete použít návrháře WPF ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="476cc-149">Currently, you need to keep your existing .NET Framework WPF project file if you want to use the WPF Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="476cc-150">Vytvořit nový projekt SDK</span><span class="sxs-lookup"><span data-stu-id="476cc-150">Create a new SDK project</span></span>

<span data-ttu-id="476cc-151">Nový projekt .NET Core 3,0, který vytvoříte, musí být v jiném adresáři než váš .NET Framework projekt.</span><span class="sxs-lookup"><span data-stu-id="476cc-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="476cc-152">Pokud oba jsou ve stejném adresáři, můžete spustit v konfliktu se soubory, které jsou generovány v adresáři **obj** .</span><span class="sxs-lookup"><span data-stu-id="476cc-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="476cc-153">V tomto příkladu vytvoříte v adresáři **SolutionFolder –** adresář s názvem **MyWPFAppCore** :</span><span class="sxs-lookup"><span data-stu-id="476cc-153">In this example, you'll create a directory named **MyWPFAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

<span data-ttu-id="476cc-154">Dále musíte vytvořit projekt **MyWPFCore. csproj** v adresáři **MyWPFAppCore** .</span><span class="sxs-lookup"><span data-stu-id="476cc-154">Next, you need to create the **MyWPFCore.csproj** project in the **MyWPFAppCore** directory.</span></span> <span data-ttu-id="476cc-155">Tento soubor můžete vytvořit ručně pomocí textového editoru výběru.</span><span class="sxs-lookup"><span data-stu-id="476cc-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="476cc-156">Vložte následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="476cc-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="476cc-157">Pokud nechcete vytvořit soubor projektu ručně, můžete použít aplikaci Visual Studio nebo .NET Core SDK k vygenerování projektu.</span><span class="sxs-lookup"><span data-stu-id="476cc-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="476cc-158">Je však nutné odstranit všechny ostatní soubory vygenerované šablonou projektu s výjimkou souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="476cc-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="476cc-159">Chcete-li použít sadu SDK, spusťte následující příkaz z adresáře **SolutionFolder –** :</span><span class="sxs-lookup"><span data-stu-id="476cc-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

<span data-ttu-id="476cc-160">Po vytvoření **MyWPFCore. csproj**by vaše adresářová struktura měla vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="476cc-160">After you create the **MyWPFCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

<span data-ttu-id="476cc-161">Projekt **MyWPFCore. csproj** budete chtít přidat do aplikace **MyApp. sln** pomocí sady Visual Studio nebo .NET Core CLI z adresáře **SolutionFolder –** :</span><span class="sxs-lookup"><span data-stu-id="476cc-161">You'll want to add the **MyWPFCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="476cc-162">Opravit generování informací o sestavení</span><span class="sxs-lookup"><span data-stu-id="476cc-162">Fix assembly info generation</span></span>

<span data-ttu-id="476cc-163">Windows Presentation Foundation projekty, které byly vytvořeny pomocí .NET Framework obsahují `AssemblyInfo.cs` soubor, který obsahuje atributy sestavení, jako je například verze sestavení, která má být vygenerována.</span><span class="sxs-lookup"><span data-stu-id="476cc-163">Windows Presentation Foundation projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="476cc-164">Projekty ve stylu sady SDK automaticky generují tyto informace na základě souboru projektu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="476cc-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="476cc-165">Pokud má oba typy "informace o sestavení", dojde ke konfliktu.</span><span class="sxs-lookup"><span data-stu-id="476cc-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="476cc-166">Tento problém vyřešíte tak, že zakážete automatické generování, což vynutí `AssemblyInfo.cs` , aby projekt používal existující soubor.</span><span class="sxs-lookup"><span data-stu-id="476cc-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="476cc-167">Existují tři nastavení, která lze přidat do hlavního `<PropertyGroup>` uzlu.</span><span class="sxs-lookup"><span data-stu-id="476cc-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="476cc-168">**GenerateAssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="476cc-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="476cc-169">Pokud nastavíte tuto vlastnost na `false`, nebudou vygenerovány atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="476cc-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="476cc-170">Tím se vyhnete konfliktu se stávajícím `AssemblyInfo.cs` souborem z .NET Framework projektu.</span><span class="sxs-lookup"><span data-stu-id="476cc-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="476cc-171">**Doplňk**</span><span class="sxs-lookup"><span data-stu-id="476cc-171">**AssemblyName**</span></span>\
<span data-ttu-id="476cc-172">Hodnota této vlastnosti je výstupní binární soubor vytvořený při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="476cc-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="476cc-173">Název nepotřebuje přidání rozšíření.</span><span class="sxs-lookup"><span data-stu-id="476cc-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="476cc-174">Například použití `MyCoreApp` služby generuje `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="476cc-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="476cc-175">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="476cc-175">**RootNamespace**</span></span>\
<span data-ttu-id="476cc-176">Výchozí obor názvů používaný vaším projektem.</span><span class="sxs-lookup"><span data-stu-id="476cc-176">The default namespace used by your project.</span></span> <span data-ttu-id="476cc-177">Tato hodnota by měla odpovídat výchozímu oboru názvů projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="476cc-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="476cc-178">Přidejte tyto tři prvky do `<PropertyGroup>` uzlu `MyWPFCore.csproj` v souboru:</span><span class="sxs-lookup"><span data-stu-id="476cc-178">Add these three elements to the `<PropertyGroup>` node in the `MyWPFCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="476cc-179">Přidat zdrojový kód</span><span class="sxs-lookup"><span data-stu-id="476cc-179">Add source code</span></span>
<span data-ttu-id="476cc-180">Nyní projekt **MyWPFCore. csproj** nekompiluje žádný kód.</span><span class="sxs-lookup"><span data-stu-id="476cc-180">Right now, the **MyWPFCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="476cc-181">Projekty .NET Core standardně do aktuálního adresáře a všech podřízených adresářů automaticky zahrnují veškerý zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="476cc-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="476cc-182">Je nutné nakonfigurovat projekt tak, aby zahrnoval kód z .NET Framework projektu pomocí relativní cesty.</span><span class="sxs-lookup"><span data-stu-id="476cc-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="476cc-183">Pokud váš .NET Framework projekt používal pro ikony a prostředky pro vaše Windows a ovládací prvky soubory **. resx** , budete je muset zahrnout.</span><span class="sxs-lookup"><span data-stu-id="476cc-183">If your .NET Framework project used **.resx** files for icons and resources for your windows and controls, you'll need to include those too.</span></span> 

<span data-ttu-id="476cc-184">První `<ItemGroup>` uzel, který je třeba přidat do projektu, zahrnuje soubor **App. XAML** , který představuje spouštěcí konfiguraci a prostředky, které vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="476cc-184">The first `<ItemGroup>` node you need to add to your project includes the **App.xaml** file that represents the startup config and resources your app uses.</span></span> <span data-ttu-id="476cc-185">Soubor **App. XAML** má také doprovodný soubor **App.XAML.cs** , ale bude automaticky zahrnut do jiného `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="476cc-185">The **App.xaml** file also has an accompanying **App.xaml.cs** file, but it will be automatically included in a different `<ItemGroup>`.</span></span>

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

<span data-ttu-id="476cc-186">Dále do svého projektu přidejte `<ItemGroup>` následující uzel.</span><span class="sxs-lookup"><span data-stu-id="476cc-186">Next, add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="476cc-187">Každý příkaz zahrnuje vzor glob souboru, který obsahuje podřízené adresáře.</span><span class="sxs-lookup"><span data-stu-id="476cc-187">Each statement includes a file glob pattern that includes child directories.</span></span> <span data-ttu-id="476cc-188">Obsahuje zdrojový kód pro váš projekt, všechny soubory nastavení a všechny prostředky.</span><span class="sxs-lookup"><span data-stu-id="476cc-188">It includes the source code for your project, any settings files, and any resources.</span></span> <span data-ttu-id="476cc-189">Adresář **obj** je explicitně vyloučený.</span><span class="sxs-lookup"><span data-stu-id="476cc-189">The **obj** directory is explicitly excluded.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="476cc-190">Dále zahrňte jiný `<ItemGroup>` uzel, který `<Page>` obsahuje položku pro každý soubor **XAML** v projektu s výjimkou souboru **App. XAML** .</span><span class="sxs-lookup"><span data-stu-id="476cc-190">Next, include another `<ItemGroup>` node that contains a `<Page>` entry for every **xaml** file in your project except the **App.xaml** file.</span></span> <span data-ttu-id="476cc-191">Ty obsahují všechny systémy Windows, stránky a prostředky, které jsou ve formátu **XAML** .</span><span class="sxs-lookup"><span data-stu-id="476cc-191">These contain all of the windows, pages, and resources that are in **xaml** format.</span></span> <span data-ttu-id="476cc-192">Zde nemůžete použít vzor glob a musíte přidat položku pro každý soubor a označit `<Generator>` použitou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="476cc-192">You cannot use a glob pattern here and must add an entry for every file and indicate the `<Generator>` used.</span></span>

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a><span data-ttu-id="476cc-193">Přidat balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="476cc-193">Add NuGet packages</span></span>

<span data-ttu-id="476cc-194">Přidejte každý balíček NuGet, na který odkazuje .NET Framework projekt, do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="476cc-194">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="476cc-195">Nejpravděpodobnější .NET Framework aplikace WPF má soubor **Packages. config** , který obsahuje seznam všech balíčků NuGet, na které odkazuje váš projekt.</span><span class="sxs-lookup"><span data-stu-id="476cc-195">Most likely your .NET Framework WPF app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="476cc-196">Můžete se podívat na tento seznam a určit, které balíčky NuGet se mají přidat do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="476cc-196">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="476cc-197">Například pokud projekt .NET Framework odkazuje na `MahApps.Metro` balíček NuGet, přidejte ho do projektu pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="476cc-197">For example, if the .NET Framework project references the `MahApps.Metro` NuGet package, add it to the project with Visual Studio.</span></span> <span data-ttu-id="476cc-198">Odkaz na balíček můžete přidat také pomocí .NET Core CLI v adresáři **SolutionFolder –** :</span><span class="sxs-lookup"><span data-stu-id="476cc-198">You can also add the package reference with the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

<span data-ttu-id="476cc-199">Předchozí příkaz přidá následující odkaz NuGet do projektu **MyWPFCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="476cc-199">The previous command would add the following NuGet reference to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="476cc-200">Kompilace problémů</span><span class="sxs-lookup"><span data-stu-id="476cc-200">Problems compiling</span></span>

<span data-ttu-id="476cc-201">Pokud máte problémy s kompilací vašich projektů, můžete používat jenom některá rozhraní API jenom pro Windows, která jsou k dispozici v .NET Framework, ale nejsou dostupná v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="476cc-201">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="476cc-202">Do projektu se můžete pokusit přidat balíček NuGet [sady Windows Compatibility Pack][compat-pack] .</span><span class="sxs-lookup"><span data-stu-id="476cc-202">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="476cc-203">Tento balíček se spouští jenom ve Windows a přidává asi 20 000 rozhraní API Windows do projektů .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="476cc-203">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="476cc-204">Předchozí příkaz přidá následující do projektu **MyWPFCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="476cc-204">The previous command adds the following to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a><span data-ttu-id="476cc-205">návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="476cc-205">WPF Designer</span></span>

<span data-ttu-id="476cc-206">Jak je popsáno v tomto článku, Visual Studio 2019 podporuje pouze návrháře WPF v .NET Frameworkch projektech.</span><span class="sxs-lookup"><span data-stu-id="476cc-206">As detailed in this article, Visual Studio 2019 only supports the WPF Designer in .NET Framework projects.</span></span> <span data-ttu-id="476cc-207">Vytvořením souběžného projektu .NET Core můžete testovat projekt pomocí .NET Core při použití projektu .NET Framework k návrhu formulářů.</span><span class="sxs-lookup"><span data-stu-id="476cc-207">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="476cc-208">Váš soubor řešení zahrnuje projekty .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="476cc-208">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="476cc-209">Přidejte a navrhněte formuláře a ovládací prvky v projektu .NET Framework a na základě vzorů glob souborů, které jsme přidali do projektů .NET Core, budou všechny nové nebo změněné soubory automaticky zahrnuty v projektech .NET Core.</span><span class="sxs-lookup"><span data-stu-id="476cc-209">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="476cc-210">Jakmile aplikace Visual Studio 2019 podporuje návrháře WPF, můžete zkopírovat nebo vložit obsah souboru projektu .NET Core do souboru projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="476cc-210">Once Visual Studio 2019 supports the WPF Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="476cc-211">Pak odstraňte vzory glob souborů přidané s `<Source>` položkami a. `<EmbeddedResource>`</span><span class="sxs-lookup"><span data-stu-id="476cc-211">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="476cc-212">Opravte cesty pro všechny odkazy na projekt, které vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="476cc-212">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="476cc-213">Tím se efektivně upgraduje .NET Framework projekt na projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="476cc-213">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="476cc-214">Další postup</span><span class="sxs-lookup"><span data-stu-id="476cc-214">Next steps</span></span>

- <span data-ttu-id="476cc-215">Přečtěte si další informace o sadě [Windows Compatibility Pack][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="476cc-215">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="476cc-216">Podívejte se [na video o přenosu](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) .NET Frameworkho projektu WPF do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="476cc-216">Watch a [video on porting](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) your .NET Framework WPF project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
