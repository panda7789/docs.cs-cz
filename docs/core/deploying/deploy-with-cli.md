---
title: Nasazení aplikace .NET core pomocí nástrojů příkazového řádku
description: Další nasazení aplikace .NET Core pomocí nástrojů rozhraní příkazového řádku (CLI)
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 21e824e6092b0d30e0499ff05c5471a291c8d269
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="7691f-103">Nasazení aplikací .NET Core pomocí nástrojů rozhraní příkazového řádku (CLI)</span><span class="sxs-lookup"><span data-stu-id="7691f-103">Deploying .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="7691f-104">Můžete nasadit aplikaci .NET Core buď jako *nasazení závislé na framework*, který obsahuje binární soubory vaší aplikace, ale závisí na přítomnost .NET Core v cílovém systému, nebo jako *samostatný nasazení*, což zahrnuje aplikace a binární soubory .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7691f-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="7691f-105">Přehled najdete v tématu [nasazení aplikace .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="7691f-105">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="7691f-106">Následující části vysvětlují, jak používat [.NET Core rozhraní příkazového řádku nástroje](../tools/index.md) vytvořit následující typy nasazení:</span><span class="sxs-lookup"><span data-stu-id="7691f-106">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="7691f-107">Nasazení závislé na Framework</span><span class="sxs-lookup"><span data-stu-id="7691f-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="7691f-108">Nasazení závislé na Framework se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="7691f-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="7691f-109">Samostatná nasazení</span><span class="sxs-lookup"><span data-stu-id="7691f-109">Self-contained deployment</span></span>
- <span data-ttu-id="7691f-110">Samostatná nasazení se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="7691f-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="7691f-111">Při práci z příkazového řádku, můžete použít program editor podle svého výběru.</span><span class="sxs-lookup"><span data-stu-id="7691f-111">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="7691f-112">Pokud je váš program editor [Visual Studio Code](https://code.visualstudio.com), nástroje command console můžete otevřít v prostředí Visual Studio Code výběrem **zobrazení** > **integrované Terminálové**.</span><span class="sxs-lookup"><span data-stu-id="7691f-112">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="7691f-113">Nasazení závislé na Framework</span><span class="sxs-lookup"><span data-stu-id="7691f-113">Framework-dependent deployment</span></span>

<span data-ttu-id="7691f-114">Nasazení závislé na framework nasazení nemá žádné závislosti třetích stran zahrnuje vytváření, testování a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-114">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="7691f-115">Jednoduchý příklad napsané v C# znázorňuje proces.</span><span class="sxs-lookup"><span data-stu-id="7691f-115">A simple example written in C# illustrates the process.</span></span> 

1. <span data-ttu-id="7691f-116">Vytvořte adresář projektu.</span><span class="sxs-lookup"><span data-stu-id="7691f-116">Create a project directory.</span></span>

   <span data-ttu-id="7691f-117">Vytvořte adresář pro svůj projekt a nastavit jej jako aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="7691f-117">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="7691f-118">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="7691f-118">Create the project.</span></span>

   <span data-ttu-id="7691f-119">Z příkazového řádku, zadejte [novou konzolu pro dotnet](../tools/dotnet-new.md) vytvořit nový projekt konzolové C# v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="7691f-119">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="7691f-120">Přidejte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-120">Add the application's source code.</span></span>

   <span data-ttu-id="7691f-121">Otevřete *Program.cs* souboru ve svém editoru a automaticky vygenerovaný kód nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="7691f-121">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="7691f-122">Se zobrazí výzvu k zadání textu a zobrazí jednotlivých slov zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7691f-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="7691f-123">Používá regulární výraz `\w+` slov v vstupního textu.</span><span class="sxs-lookup"><span data-stu-id="7691f-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="7691f-124">Aktualizujte závislosti projektu a nástroje.</span><span class="sxs-lookup"><span data-stu-id="7691f-124">Update the project's dependencies and tools.</span></span>
 
   <span data-ttu-id="7691f-125">Spustit [dotnet obnovení](../tools/dotnet-restore.md) ([viz Poznámka](#dotnet-restore-note)) příkazu obnovte závislosti zadaný ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="7691f-125">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="7691f-126">Vytvořte sestavení ladicí verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-126">Create a Debug build of your app.</span></span>

   <span data-ttu-id="7691f-127">Použití [dotnet sestavení](../tools/dotnet-build.md) k vytvoření aplikace nebo [dotnet. Spusťte](../tools/dotnet-run.md) příkazu sestavit a spustit ho.</span><span class="sxs-lookup"><span data-stu-id="7691f-127">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="7691f-128">Nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-128">Deploy your app.</span></span>

   <span data-ttu-id="7691f-129">Po ladit a testovat program, vytvořte nasazení pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="7691f-129">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   <span data-ttu-id="7691f-130">Tím se vytvoří verze (a nikoli ladění) verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-130">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="7691f-131">Výsledné soubory jsou umístěny v adresáři s názvem *publikování* , je v podadresáři vašeho projektu *bin* adresáře.</span><span class="sxs-lookup"><span data-stu-id="7691f-131">The resulting files are placed in a directory named *publish* that's in a subdirectory of your project's *bin* directory.</span></span>

<span data-ttu-id="7691f-132">Proces publikování společně se soubory aplikace vysílá soubor databáze (.pdb) program, který obsahuje ladicí informace o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7691f-132">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="7691f-133">Soubor je užitečné především pro ladění výjimek.</span><span class="sxs-lookup"><span data-stu-id="7691f-133">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="7691f-134">Můžete se distribuovat soubory vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-134">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="7691f-135">Ale uložte jej v případě, že chcete ladit sestavení pro vydání vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-135">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="7691f-136">Můžete nasadit kompletní sadu aplikací, které chcete systém souborů.</span><span class="sxs-lookup"><span data-stu-id="7691f-136">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="7691f-137">Například můžete balíček je v souboru Zip, pomocí jednoduché `copy` příkaz nebo nasadit pomocí jakékoli instalačního balíčku podle svého výběru.</span><span class="sxs-lookup"><span data-stu-id="7691f-137">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="7691f-138">Po instalaci, mohou uživatelé provádět vaší aplikace pomocí `dotnet` příkaz a poskytnutí názvu souboru, jako například `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="7691f-138">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="7691f-139">Kromě binární soubory aplikace instalačním programem vaší by také buď vytvořit balíček instalačního programu sdílený framework nebo kontrolovat předpokladem je jako součást instalace aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-139">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="7691f-140">Instalace sdílený framework vyžaduje správce nebo kořenový přístup.</span><span class="sxs-lookup"><span data-stu-id="7691f-140">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="7691f-141">Nasazení závislé na Framework se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="7691f-141">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="7691f-142">Nasazení nasazení framework závislé na jeden nebo více třetích stran závislosti vyžaduje, aby tyto závislosti projektu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7691f-142">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="7691f-143">Dva další kroky jsou požadovány, než můžete spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz:</span><span class="sxs-lookup"><span data-stu-id="7691f-143">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="7691f-144">Přidejte odkazy na požadované knihovny třetích stran `<ItemGroup>` část vaší *csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="7691f-144">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="7691f-145">Následující `<ItemGroup>` část obsahuje závislost na [Json.NET](http://www.newtonsoft.com/json) jako knihovnu třetí strany:</span><span class="sxs-lookup"><span data-stu-id="7691f-145">The following `<ItemGroup>` section contains a dependency on [Json.NET](http://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="7691f-146">Pokud jste tak ještě neučinili, stáhněte si balíček NuGet obsahující závislost třetích stran.</span><span class="sxs-lookup"><span data-stu-id="7691f-146">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="7691f-147">Chcete-li stáhnout balíček, spusťte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz po přidání závislost.</span><span class="sxs-lookup"><span data-stu-id="7691f-147">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="7691f-148">Protože závislost vyřešen z místní mezipaměti NuGet v publikovat čas, musí být k dispozici v systému.</span><span class="sxs-lookup"><span data-stu-id="7691f-148">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="7691f-149">Upozorňujeme, že nasazení závislé na framework se závislostmi třetí strany se pouze jako přenosný jeho závislé součásti třetích stran.</span><span class="sxs-lookup"><span data-stu-id="7691f-149">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="7691f-150">Například pokud knihovnu třetích stran podporuje pouze systému macOS, aplikace není přenosné pro systémy Windows.</span><span class="sxs-lookup"><span data-stu-id="7691f-150">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="7691f-151">To se stane, když závislost třetích stran, samotné závisí na nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="7691f-151">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="7691f-152">Dobrým příkladem tohoto objektu je [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), který vyžaduje nativní závislost na [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="7691f-152">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="7691f-153">Když disketové jednotky se vytvoří pro aplikace s tímto typem závislosti třetích stran, publikované výstup obsahuje složku pro každý [identifikátor Runtime (RID)](../rid-catalog.md) podporující nativní závislost (a která existuje v jeho balíčku NuGet).</span><span class="sxs-lookup"><span data-stu-id="7691f-153">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="7691f-154">Samostatná nasazení bez závislosti na třetích stran</span><span class="sxs-lookup"><span data-stu-id="7691f-154">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="7691f-155">Nasazení samostatná nasazení bez závislosti na třetích stran zahrnuje vytvoření projektu, úprava *csproj* souborů, vytváření, testování a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-155">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="7691f-156">Jednoduchý příklad napsané v C# znázorňuje proces.</span><span class="sxs-lookup"><span data-stu-id="7691f-156">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="7691f-157">Tento příklad ukazuje, jak vytvořit samostatný nasazení pomocí [dotnet nástroj](../tools/dotnet.md) z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7691f-157">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="7691f-158">Vytvořte adresář pro projekt.</span><span class="sxs-lookup"><span data-stu-id="7691f-158">Create a directory for the project.</span></span>

   <span data-ttu-id="7691f-159">Vytvořte adresář pro svůj projekt a nastavte jej aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="7691f-159">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="7691f-160">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="7691f-160">Create the project.</span></span>

   <span data-ttu-id="7691f-161">Z příkazového řádku, zadejte [novou konzolu pro dotnet](../tools/dotnet-new.md) vytvořit nový projekt konzolové C# v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="7691f-161">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="7691f-162">Přidejte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-162">Add the application's source code.</span></span>

   <span data-ttu-id="7691f-163">Otevřete *Program.cs* souboru ve svém editoru a automaticky vygenerovaný kód nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="7691f-163">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="7691f-164">Se zobrazí výzvu k zadání textu a zobrazí jednotlivých slov zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7691f-164">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="7691f-165">Používá regulární výraz `\w+` slov v vstupního textu.</span><span class="sxs-lookup"><span data-stu-id="7691f-165">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="7691f-166">Definujte platformy, které se zaměří na vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7691f-166">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="7691f-167">Vytvoření `<RuntimeIdentifiers>` značky v `<PropertyGroup>` část vaší *csproj* soubor, který definuje platformy vaší aplikace cílí a zadejte runtime identifikátorů (RID) pro každou platformu, která cílí.</span><span class="sxs-lookup"><span data-stu-id="7691f-167">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="7691f-168">Všimněte si, že je také nutné přidat středníkem k oddělení identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="7691f-168">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="7691f-169">V tématu [Runtime identifikátor katalogu](../rid-catalog.md) seznam identifikátorů modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7691f-169">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span> 

   <span data-ttu-id="7691f-170">Například následující `<PropertyGroup>` části udává, že se aplikace spouští na 64bitové verze Windows 10 operační systémy a operační systém 10.11 verze OS X 64-bit.</span><span class="sxs-lookup"><span data-stu-id="7691f-170">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="7691f-171">Všimněte si, že `<RuntimeIdentifiers>` element může vyskytovat v žádném `<PropertyGroup>` ve vaší *csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="7691f-171">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="7691f-172">Ucelenou ukázku *csproj* souboru se zobrazí později v této části.</span><span class="sxs-lookup"><span data-stu-id="7691f-172">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="7691f-173">Aktualizujte závislosti projektu a nástroje.</span><span class="sxs-lookup"><span data-stu-id="7691f-173">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="7691f-174">Spustit [dotnet obnovení](../tools/dotnet-restore.md) ([viz Poznámka](#dotnet-restore-note)) příkazu obnovte závislosti zadaný ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="7691f-174">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="7691f-175">Vytvořte sestavení ladicí verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-175">Create a Debug build of your app.</span></span>

   <span data-ttu-id="7691f-176">Z příkazového řádku, použijte [dotnet sestavení](../tools/dotnet-build.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="7691f-176">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="7691f-177">Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací pro každou platformu, cílem.</span><span class="sxs-lookup"><span data-stu-id="7691f-177">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="7691f-178">Použití `dotnet publish` příkaz pro obě platformy cílí následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7691f-178">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="7691f-179">Tím se vytvoří verze (a nikoli ladění) verzi aplikace pro každou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="7691f-179">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="7691f-180">Výsledné soubory jsou umístěny v podadresáři s názvem *publikování* , je v podadresáři vašeho projektu *.\bin\Release\netcoreapp1.1\<runtime_identifier >* podadresáři.</span><span class="sxs-lookup"><span data-stu-id="7691f-180">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp1.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="7691f-181">Všimněte si, že každý podadresář obsahuje kompletní sadu souborů (soubory aplikace a všechny soubory .NET Core) potřebné ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-181">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="7691f-182">Proces publikování společně se soubory aplikace vysílá soubor databáze (.pdb) program, který obsahuje ladicí informace o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7691f-182">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="7691f-183">Soubor je užitečné především pro ladění výjimek.</span><span class="sxs-lookup"><span data-stu-id="7691f-183">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="7691f-184">Je možné, není-li vytvořit balíček s soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-184">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="7691f-185">Ale uložte jej v případě, že chcete ladit sestavení pro vydání vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-185">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="7691f-186">Publikované soubory žádným způsobem, který chcete nasaďte.</span><span class="sxs-lookup"><span data-stu-id="7691f-186">Deploy the published files in any way you like.</span></span> <span data-ttu-id="7691f-187">Například můžete balíček je v souboru Zip, pomocí jednoduché `copy` příkaz nebo nasadit pomocí jakékoli instalačního balíčku podle svého výběru.</span><span class="sxs-lookup"><span data-stu-id="7691f-187">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="7691f-188">Toto je kompletní *csproj* souboru pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="7691f-188">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="7691f-189">Samostatná nasazení se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="7691f-189">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="7691f-190">Nasazení samostatná nasazení s jeden nebo více závislostí třetí strany vyžaduje přidání závislosti.</span><span class="sxs-lookup"><span data-stu-id="7691f-190">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="7691f-191">Dva další kroky jsou požadovány, než můžete spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz:</span><span class="sxs-lookup"><span data-stu-id="7691f-191">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="7691f-192">Přidejte odkazy na všechny knihovny třetích stran `<ItemGroup>` část vaší *csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="7691f-192">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="7691f-193">Následující `<ItemGroup>` část používá technologii Json.NET jako knihovnu třetích stran.</span><span class="sxs-lookup"><span data-stu-id="7691f-193">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="7691f-194">Pokud jste tak ještě neučinili, stáhněte si balíček NuGet obsahující závislost třetích stran k vašemu systému.</span><span class="sxs-lookup"><span data-stu-id="7691f-194">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="7691f-195">Chcete-li zpřístupnit závislost do vaší aplikace, spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz po přidání závislost.</span><span class="sxs-lookup"><span data-stu-id="7691f-195">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="7691f-196">Protože závislost vyřešen z místní mezipaměti NuGet v publikovat čas, musí být k dispozici v systému.</span><span class="sxs-lookup"><span data-stu-id="7691f-196">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="7691f-197">Toto je kompletní *csproj* souboru pro tento projekt:</span><span class="sxs-lookup"><span data-stu-id="7691f-197">The following is the complete *csproj* file for this project:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="7691f-198">Když nasadíte aplikaci, všechny závislosti třetích stran používají ve vaší aplikaci jsou také obsažena s soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="7691f-198">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="7691f-199">Knihovny jiných výrobců nemusí na serveru, na kterém aplikace běží.</span><span class="sxs-lookup"><span data-stu-id="7691f-199">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="7691f-200">Všimněte si, že lze nasadit pouze samostatná nasazení s knihovnou třetích stran na platformách podporovaných aplikací této knihovny.</span><span class="sxs-lookup"><span data-stu-id="7691f-200">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="7691f-201">Toto je podobná s závislosti třetích stran s nativní závislosti v nasazení závislé na framework, kde musí být kompatibilní s platformou, pro které je aplikace nasazená nativní závislosti.</span><span class="sxs-lookup"><span data-stu-id="7691f-201">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a><span data-ttu-id="7691f-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="7691f-202">See also</span></span>

<span data-ttu-id="7691f-203">[Nasazení aplikace .NET core](index.md) </span><span class="sxs-lookup"><span data-stu-id="7691f-203">[.NET Core Application Deployment](index.md) </span></span>  
[<span data-ttu-id="7691f-204">Katalog .NET core Runtime identifikátor (RID)</span><span class="sxs-lookup"><span data-stu-id="7691f-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)   

