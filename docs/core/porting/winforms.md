---
title: Port model Windows Forms aplikace do .NET Core 3,0
description: Naučíte se, jak portovat .NET Framework model Windows Forms aplikace do .NET Core 3,0 pro Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: 7480c86af1acd482adff5e3e24dc229f24af0e5b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216317"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="5e388-103">Postupy: Port model Windows Forms desktopové aplikace do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e388-103">How to: Port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="5e388-104">Tento článek popisuje, jak přenést vaši desktopovou aplikaci založenou na model Windows Forms z .NET Framework na .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="5e388-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="5e388-105">Sada .NET Core 3,0 SDK obsahuje podporu pro model Windows Forms aplikace.</span><span class="sxs-lookup"><span data-stu-id="5e388-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="5e388-106">Model Windows Forms je prostředí jenom pro Windows a běží jenom v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5e388-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="5e388-107">V tomto příkladu se k vytvoření a správě projektu používá rozhraní příkazového řádku .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5e388-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="5e388-108">V tomto článku se k identifikaci typů souborů používaných k migraci používají různé názvy.</span><span class="sxs-lookup"><span data-stu-id="5e388-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="5e388-109">Při migraci projektu budou soubory pojmenovány jinak, takže je bude možné navzájem narovnávat na ty, které jsou uvedeny níže:</span><span class="sxs-lookup"><span data-stu-id="5e388-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="5e388-110">Soubor</span><span class="sxs-lookup"><span data-stu-id="5e388-110">File</span></span> | <span data-ttu-id="5e388-111">Popis</span><span class="sxs-lookup"><span data-stu-id="5e388-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="5e388-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="5e388-112">**MyApps.sln**</span></span> | <span data-ttu-id="5e388-113">Název souboru řešení</span><span class="sxs-lookup"><span data-stu-id="5e388-113">The name of the solution file.</span></span> |
| <span data-ttu-id="5e388-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="5e388-114">**MyForms.csproj**</span></span> | <span data-ttu-id="5e388-115">Název projektu .NET Framework model Windows Forms na port.</span><span class="sxs-lookup"><span data-stu-id="5e388-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="5e388-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="5e388-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="5e388-117">Název nového projektu .NET Core, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="5e388-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="5e388-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="5e388-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="5e388-119">Spustitelný soubor aplikace model Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e388-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="5e388-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e388-120">Prerequisites</span></span>

- <span data-ttu-id="5e388-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pro každou práci návrháře, kterou chcete provést.</span><span class="sxs-lookup"><span data-stu-id="5e388-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="5e388-122">Nainstalujte následující úlohy sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="5e388-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="5e388-123">Vývoj desktopových aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="5e388-123">.NET desktop development</span></span>
  - <span data-ttu-id="5e388-124">Vývoj pro různé platformy .NET</span><span class="sxs-lookup"><span data-stu-id="5e388-124">.NET cross-platform development</span></span>

- <span data-ttu-id="5e388-125">Pracovní model Windows Forms projekt v řešení, které sestaví a spouští bez problémů.</span><span class="sxs-lookup"><span data-stu-id="5e388-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="5e388-126">Projekt musí být kódován v C#.</span><span class="sxs-lookup"><span data-stu-id="5e388-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="5e388-127">Nainstalujte nejnovější verzi [.NET Core 3,0](https://aka.ms/netcore3download) Preview.</span><span class="sxs-lookup"><span data-stu-id="5e388-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="5e388-128">**Visual Studio 2017** nepodporuje projekty .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="5e388-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="5e388-129">**Visual Studio 2019** podporuje projekty .net Core 3,0, ale ještě nepodporuje Visual Designer pro .net core 3,0 model Windows Forms projekty.</span><span class="sxs-lookup"><span data-stu-id="5e388-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="5e388-130">Chcete-li používat vizuálního návrháře, musíte mít ve svém řešení projekt .NET model Windows Forms, který sdílí soubory formulářů s projektem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e388-130">To use the visual designer, you must have a .NET Windows Forms project in your solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="5e388-131">Byste</span><span class="sxs-lookup"><span data-stu-id="5e388-131">Consider</span></span>

<span data-ttu-id="5e388-132">Při přenosu .NET Framework model Windows Forms aplikace existuje několik věcí, které je potřeba vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="5e388-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="5e388-133">Ověřte, že je vaše aplikace vhodným kandidátem na migraci.</span><span class="sxs-lookup"><span data-stu-id="5e388-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="5e388-134">Pomocí [analyzátoru přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) určete, jestli se váš projekt migruje na .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="5e388-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="5e388-135">Pokud má váš projekt problémy s rozhraním .NET Core 3,0, analyzátor vám pomůže tyto problémy identifikovat.</span><span class="sxs-lookup"><span data-stu-id="5e388-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="5e388-136">Používáte jinou verzi model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5e388-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="5e388-137">Po vydání .NET Core 3,0 Preview 1 model Windows Forms otevřít zdroj na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="5e388-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="5e388-138">Kód pro .NET Core model Windows Forms je rozvětvení .NET Framework model Windows Forms základu kódu.</span><span class="sxs-lookup"><span data-stu-id="5e388-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="5e388-139">Je možné, že existují nějaké rozdíly a vaše aplikace nebude portem.</span><span class="sxs-lookup"><span data-stu-id="5e388-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="5e388-140">[Sada Windows Compatibility Pack][compat-pack] vám může při migraci trvat.</span><span class="sxs-lookup"><span data-stu-id="5e388-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="5e388-141">V rozhraní .NET Core 3,0 nejsou k dispozici některá rozhraní API, která jsou k dispozici v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e388-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="5e388-142">[Sada Windows Compatibility Pack][compat-pack] přidává mnoho z těchto rozhraní API a může pomáhat s tím, že vaše aplikace model Windows Forms bude kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e388-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="5e388-143">Aktualizujte balíčky NuGet používané vaším projektem.</span><span class="sxs-lookup"><span data-stu-id="5e388-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="5e388-144">Před migrací je vždycky vhodné použít nejnovější verze balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="5e388-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="5e388-145">Pokud vaše aplikace odkazuje na balíčky NuGet, aktualizujte je na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="5e388-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="5e388-146">Ujistěte se, že vaše aplikace byla úspěšně vytvořena.</span><span class="sxs-lookup"><span data-stu-id="5e388-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="5e388-147">Pokud při upgradu dojde k chybám balíčku, proveďte downgrade balíčku na nejnovější verzi, která nepřerušila váš kód.</span><span class="sxs-lookup"><span data-stu-id="5e388-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="5e388-148">Visual Studio 2019 zatím nepodporuje Návrháře formulářů pro .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="5e388-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="5e388-149">V současné době je nutné zachovat existující soubor projektu .NET Framework model Windows Forms, pokud chcete použít Návrháře formulářů ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e388-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="5e388-150">Vytvořit nový projekt SDK</span><span class="sxs-lookup"><span data-stu-id="5e388-150">Create a new SDK project</span></span>

<span data-ttu-id="5e388-151">Nový projekt .NET Core 3,0, který vytvoříte, musí být v jiném adresáři než váš .NET Framework projekt.</span><span class="sxs-lookup"><span data-stu-id="5e388-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="5e388-152">Pokud oba jsou ve stejném adresáři, můžete spustit v konfliktu se soubory, které jsou generovány v adresáři **obj** .</span><span class="sxs-lookup"><span data-stu-id="5e388-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="5e388-153">V tomto příkladu vytvoříme v adresáři **SolutionFolder –** adresář s názvem **MyFormsAppCore** :</span><span class="sxs-lookup"><span data-stu-id="5e388-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="5e388-154">Dále musíte vytvořit projekt **MyFormsCore. csproj** v adresáři **MyFormsAppCore** .</span><span class="sxs-lookup"><span data-stu-id="5e388-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="5e388-155">Tento soubor můžete vytvořit ručně pomocí textového editoru výběru.</span><span class="sxs-lookup"><span data-stu-id="5e388-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="5e388-156">Vložte následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="5e388-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="5e388-157">Pokud nechcete vytvořit soubor projektu ručně, můžete použít aplikaci Visual Studio nebo .NET Core SDK k vygenerování projektu.</span><span class="sxs-lookup"><span data-stu-id="5e388-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="5e388-158">Je však nutné odstranit všechny ostatní soubory vygenerované šablonou projektu s výjimkou souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="5e388-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="5e388-159">Chcete-li použít sadu SDK, spusťte následující příkaz z adresáře **SolutionFolder –** :</span><span class="sxs-lookup"><span data-stu-id="5e388-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="5e388-160">Po vytvoření **MyFormsCore. csproj**by vaše adresářová struktura měla vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="5e388-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="5e388-161">Projekt **MyFormsCore. csproj** budete chtít přidat do aplikace **MyApp. sln** pomocí sady Visual Studio nebo .NET Core CLI z adresáře **SolutionFolder –** :</span><span class="sxs-lookup"><span data-stu-id="5e388-161">You'll want to add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="5e388-162">Opravit generování informací o sestavení</span><span class="sxs-lookup"><span data-stu-id="5e388-162">Fix assembly info generation</span></span>

<span data-ttu-id="5e388-163">Model Windows Forms projekty, které byly vytvořeny pomocí .NET Framework obsahují `AssemblyInfo.cs` soubor, který obsahuje atributy sestavení, jako je například verze sestavení, která má být vygenerována.</span><span class="sxs-lookup"><span data-stu-id="5e388-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="5e388-164">Projekty ve stylu sady SDK automaticky generují tyto informace na základě souboru projektu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="5e388-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="5e388-165">Pokud má oba typy "informace o sestavení", dojde ke konfliktu.</span><span class="sxs-lookup"><span data-stu-id="5e388-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="5e388-166">Tento problém vyřešíte tak, že zakážete automatické generování, což vynutí `AssemblyInfo.cs` , aby projekt používal existující soubor.</span><span class="sxs-lookup"><span data-stu-id="5e388-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="5e388-167">Existují tři nastavení, která lze přidat do hlavního `<PropertyGroup>` uzlu.</span><span class="sxs-lookup"><span data-stu-id="5e388-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="5e388-168">**GenerateAssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="5e388-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="5e388-169">Pokud nastavíte tuto vlastnost na `false`, nebudou vygenerovány atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="5e388-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="5e388-170">Tím se vyhnete konfliktu se stávajícím `AssemblyInfo.cs` souborem z .NET Framework projektu.</span><span class="sxs-lookup"><span data-stu-id="5e388-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="5e388-171">**Doplňk**</span><span class="sxs-lookup"><span data-stu-id="5e388-171">**AssemblyName**</span></span>\
<span data-ttu-id="5e388-172">Hodnota této vlastnosti je výstupní binární soubor vytvořený při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="5e388-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="5e388-173">Název nepotřebuje přidání rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5e388-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="5e388-174">Například použití `MyCoreApp` služby generuje `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="5e388-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="5e388-175">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="5e388-175">**RootNamespace**</span></span>\
<span data-ttu-id="5e388-176">Výchozí obor názvů používaný vaším projektem.</span><span class="sxs-lookup"><span data-stu-id="5e388-176">The default namespace used by your project.</span></span> <span data-ttu-id="5e388-177">Tato hodnota by měla odpovídat výchozímu oboru názvů projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e388-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="5e388-178">Přidejte tyto tři prvky do `<PropertyGroup>` uzlu `MyFormsCore.csproj` v souboru:</span><span class="sxs-lookup"><span data-stu-id="5e388-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="5e388-179">Přidat zdrojový kód</span><span class="sxs-lookup"><span data-stu-id="5e388-179">Add source code</span></span>

<span data-ttu-id="5e388-180">Nyní projekt **MyFormsCore. csproj** nekompiluje žádný kód.</span><span class="sxs-lookup"><span data-stu-id="5e388-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="5e388-181">Projekty .NET Core standardně do aktuálního adresáře a všech podřízených adresářů automaticky zahrnují veškerý zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="5e388-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="5e388-182">Je nutné nakonfigurovat projekt tak, aby zahrnoval kód z .NET Framework projektu pomocí relativní cesty.</span><span class="sxs-lookup"><span data-stu-id="5e388-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="5e388-183">Pokud váš .NET Framework projekt používal soubory **. resx** pro ikony a prostředky pro vaše formuláře, budete je muset zahrnout.</span><span class="sxs-lookup"><span data-stu-id="5e388-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span> 

<span data-ttu-id="5e388-184">Do projektu přidejte `<ItemGroup>` následující uzel.</span><span class="sxs-lookup"><span data-stu-id="5e388-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="5e388-185">Každý příkaz zahrnuje vzor glob souboru, který obsahuje podřízené adresáře.</span><span class="sxs-lookup"><span data-stu-id="5e388-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="5e388-186">Alternativně můžete vytvořit `<Compile>` položku nebo `<EmbeddedResource>` pro každý soubor v projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e388-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="5e388-187">Přidat balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="5e388-187">Add NuGet packages</span></span>

<span data-ttu-id="5e388-188">Přidejte každý balíček NuGet, na který odkazuje .NET Framework projekt, do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e388-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="5e388-189">Pravděpodobně vaše aplikace .NET Framework model Windows Forms má soubor **Packages. config** , který obsahuje seznam všech balíčků NuGet, na které odkazuje váš projekt.</span><span class="sxs-lookup"><span data-stu-id="5e388-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="5e388-190">Můžete se podívat na tento seznam a určit, které balíčky NuGet se mají přidat do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e388-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="5e388-191">Pokud například projekt .NET Framework `MetroFramework`odkazoval na `MetroFramework.Design`balíčky NuGet, a `MetroFramework.Fonts` , přidejte do projektu každý z nich pomocí sady Visual Studio nebo .NET Core CLI z adresáře **SolutionFolder –** :</span><span class="sxs-lookup"><span data-stu-id="5e388-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="5e388-192">Předchozí příkazy by přidaly následující odkazy NuGet do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="5e388-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="5e388-193">Knihovny ovládacích prvků portů</span><span class="sxs-lookup"><span data-stu-id="5e388-193">Port control libraries</span></span>

<span data-ttu-id="5e388-194">Pokud máte projekt knihovny ovládacích prvků model Windows Forms pro port, směry jsou stejné jako při přenosu .NET Framework projektu model Windows Forms aplikace s výjimkou několika nastavení.</span><span class="sxs-lookup"><span data-stu-id="5e388-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="5e388-195">A namísto kompilování do spustitelného souboru, kompilujete do knihovny.</span><span class="sxs-lookup"><span data-stu-id="5e388-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="5e388-196">Rozdíl mezi spustitelným projektem a projektem knihovny, kromě cest k souboru globy, který obsahuje váš zdrojový kód, je minimální.</span><span class="sxs-lookup"><span data-stu-id="5e388-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="5e388-197">Pomocí příkladu předchozího kroku umožníte rozbalení projektů a souborů, se kterými pracujete.</span><span class="sxs-lookup"><span data-stu-id="5e388-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="5e388-198">Soubor</span><span class="sxs-lookup"><span data-stu-id="5e388-198">File</span></span> | <span data-ttu-id="5e388-199">Popis</span><span class="sxs-lookup"><span data-stu-id="5e388-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="5e388-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="5e388-200">**MyApps.sln**</span></span> | <span data-ttu-id="5e388-201">Název souboru řešení</span><span class="sxs-lookup"><span data-stu-id="5e388-201">The name of the solution file.</span></span> |
| <span data-ttu-id="5e388-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="5e388-202">**MyControls.csproj**</span></span> | <span data-ttu-id="5e388-203">Název .NET Framework model Windows Forms řídí projekt na port.</span><span class="sxs-lookup"><span data-stu-id="5e388-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="5e388-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="5e388-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="5e388-205">Název nového projektu knihovny .NET Core, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="5e388-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="5e388-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="5e388-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="5e388-207">Knihovna ovládacích prvků model Windows Forms .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e388-207">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="5e388-208">Zvažte rozdíly mezi `MyControlsCore.csproj` projektem a dříve vytvořeným `MyFormsCore.csproj` projektem.</span><span class="sxs-lookup"><span data-stu-id="5e388-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="5e388-209">Tady je příklad toho, co by soubor projektu knihovny ovládacích prvků model Windows Forms .NET Core vypadal jako:</span><span class="sxs-lookup"><span data-stu-id="5e388-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="5e388-210">Jak vidíte, `<OutputType>` uzel byl odebrán, což nastaví výchozí kompilátor k vytvoření knihovny namísto spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="5e388-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="5e388-211">`<AssemblyName>` A`<RootNamespace>` byly změněny.</span><span class="sxs-lookup"><span data-stu-id="5e388-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="5e388-212">`<RootNamespace>` Konkrétně by měl odpovídat oboru názvů knihovny ovládacích prvků model Windows Forms, kterou portuje.</span><span class="sxs-lookup"><span data-stu-id="5e388-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="5e388-213">A nakonec byly upraveny `<EmbeddedResource>` uzly `<Compile>` a tak, aby odkazovaly na složku knihovny ovládacích prvků model Windows Forms, kterou portuje.</span><span class="sxs-lookup"><span data-stu-id="5e388-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="5e388-214">Dále v hlavním projektu .NET Core **MyFormsCore. csproj** přidejte odkaz na novou knihovnu ovládacích prvků .net Core model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5e388-214">Next, in the main .NET Core **MyFormsCore.csproj** project add reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="5e388-215">Přidejte odkaz buď pomocí sady Visual Studio, nebo .NET Core CLI z adresáře **SolutionFolder –** :</span><span class="sxs-lookup"><span data-stu-id="5e388-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="5e388-216">Předchozí příkaz přidá následující do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="5e388-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="5e388-217">Kompilace problémů</span><span class="sxs-lookup"><span data-stu-id="5e388-217">Problems compiling</span></span>

<span data-ttu-id="5e388-218">Pokud máte problémy s kompilací vašich projektů, můžete používat jenom některá rozhraní API jenom pro Windows, která jsou k dispozici v .NET Framework, ale nejsou dostupná v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e388-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="5e388-219">Do projektu se můžete pokusit přidat balíček NuGet [sady Windows Compatibility Pack][compat-pack] .</span><span class="sxs-lookup"><span data-stu-id="5e388-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="5e388-220">Tento balíček se spouští jenom ve Windows a přidává asi 20 000 rozhraní API Windows do projektů .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5e388-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="5e388-221">Předchozí příkaz přidá následující do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="5e388-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="5e388-222">Návrhář formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="5e388-222">Windows Forms Designer</span></span>

<span data-ttu-id="5e388-223">Jak je popsáno v tomto článku, Visual Studio 2019 podporuje pouze Návrháře formulářů v .NET Frameworkch projektech.</span><span class="sxs-lookup"><span data-stu-id="5e388-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="5e388-224">Vytvořením souběžného projektu .NET Core můžete testovat projekt pomocí .NET Core při použití projektu .NET Framework k návrhu formulářů.</span><span class="sxs-lookup"><span data-stu-id="5e388-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="5e388-225">Váš soubor řešení zahrnuje projekty .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e388-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="5e388-226">Přidejte a navrhněte formuláře a ovládací prvky v projektu .NET Framework a na základě vzorů glob souborů, které jsme přidali do projektů .NET Core, budou všechny nové nebo změněné soubory automaticky zahrnuty v projektech .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e388-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="5e388-227">Jakmile aplikace Visual Studio 2019 podporuje Návrhář formulářů, můžete zkopírovat nebo vložit obsah souboru projektu .NET Core do souboru projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e388-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="5e388-228">Pak odstraňte vzory glob souborů přidané s `<Source>` položkami a. `<EmbeddedResource>`</span><span class="sxs-lookup"><span data-stu-id="5e388-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="5e388-229">Opravte cesty pro všechny odkazy na projekt, které vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="5e388-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="5e388-230">Tím se efektivně upgraduje .NET Framework projekt na projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e388-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="5e388-231">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5e388-231">Next steps</span></span>

- <span data-ttu-id="5e388-232">Přečtěte si další informace o sadě [Windows Compatibility Pack][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="5e388-232">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="5e388-233">Podívejte se [na video o přenosu](https://www.youtube.com/watch?v=upVQEUc_KwU) .NET Framework model Windows Forms projektu do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e388-233">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
