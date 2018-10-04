---
title: Nasazení aplikace .NET core pomocí nástrojů CLI
description: Zjistěte, nasazení aplikace .NET Core pomocí nástrojů rozhraní příkazového řádku (CLI)
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
ms.openlocfilehash: a7e810372d831699eae777186385e45fe65cdf45
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266578"
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="dceaf-103">Nasazení aplikace .NET Core pomocí nástrojů rozhraní příkazového řádku (CLI)</span><span class="sxs-lookup"><span data-stu-id="dceaf-103">Deploying .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="dceaf-104">Můžete nasadit aplikaci .NET Core buď jako *nasazení závisí na architektuře*, který obsahuje binární soubory vaší aplikace, ale závisí na přítomnosti .NET Core v cílovém systému, nebo jako *samostatná nasazení*, což zahrnuje aplikace a binární soubory .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dceaf-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="dceaf-105">Přehled najdete v tématu [nasazení aplikace .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="dceaf-105">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="dceaf-106">Následující části vysvětlují, jak používat [nástroje rozhraní příkazového řádku .NET Core](../tools/index.md) vytvořit následující typy nasazení:</span><span class="sxs-lookup"><span data-stu-id="dceaf-106">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="dceaf-107">Nasazení závisí na architektuře</span><span class="sxs-lookup"><span data-stu-id="dceaf-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="dceaf-108">Nasazení závisí na architektuře s závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="dceaf-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="dceaf-109">Samostatná nasazení</span><span class="sxs-lookup"><span data-stu-id="dceaf-109">Self-contained deployment</span></span>
- <span data-ttu-id="dceaf-110">Samostatná nasazení s závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="dceaf-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="dceaf-111">Při práci z příkazového řádku, můžete program editoru podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="dceaf-111">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="dceaf-112">Pokud je váš program editor [Visual Studio Code](https://code.visualstudio.com), nástroje command console v prostředí Visual Studio Code můžete otevřít tak, že vyberete **zobrazení** > **integrovaný terminál**.</span><span class="sxs-lookup"><span data-stu-id="dceaf-112">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="dceaf-113">Nasazení závisí na architektuře</span><span class="sxs-lookup"><span data-stu-id="dceaf-113">Framework-dependent deployment</span></span>

<span data-ttu-id="dceaf-114">Nasazení závisí na architektuře bez závislostí třetích stran zahrnuje vytváření, testování a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-114">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="dceaf-115">Jednoduchý příklad napsané v jazyce C# znázorňuje proces.</span><span class="sxs-lookup"><span data-stu-id="dceaf-115">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="dceaf-116">Vytvořte adresář projektu.</span><span class="sxs-lookup"><span data-stu-id="dceaf-116">Create a project directory.</span></span>

   <span data-ttu-id="dceaf-117">Vytvořte adresář pro váš projekt a nastavte ji váš aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="dceaf-117">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="dceaf-118">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="dceaf-118">Create the project.</span></span>

   <span data-ttu-id="dceaf-119">Z příkazového řádku, zadejte [dotnet nové konzoly](../tools/dotnet-new.md) vytvořte nový projekt konzoly C# nebo [dotnet nové konzoly - lang vb](../tools/dotnet-new.md) vytvoříte nový projekt konzoly jazyka Visual Basic v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="dceaf-119">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project or [dotnet new console -lang vb](../tools/dotnet-new.md) to create a new Visual Basic console project in that directory.</span></span>

1. <span data-ttu-id="dceaf-120">Přidejte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-120">Add the application's source code.</span></span>

   <span data-ttu-id="dceaf-121">Otevřít *Program.cs* nebo *soubor Program.vb* souboru ve svém editoru a automaticky vygenerovaném kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="dceaf-121">Open the *Program.cs* or *Program.vb* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="dceaf-122">Se zobrazí výzva k zadání textu a zobrazuje jednotlivá slova zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="dceaf-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="dceaf-123">Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.</span><span class="sxs-lookup"><span data-stu-id="dceaf-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="dceaf-124">Aktualizujte závislosti projektu a nástroje.</span><span class="sxs-lookup"><span data-stu-id="dceaf-124">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="dceaf-125">Spustit [dotnet restore](../tools/dotnet-restore.md) ([viz Poznámka](#dotnet-restore-note)) příkaz pro obnovení závislosti zadaný ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="dceaf-125">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="dceaf-126">Vytvořte sestavení pro ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-126">Create a Debug build of your app.</span></span>

   <span data-ttu-id="dceaf-127">Použití [dotnet sestavení](../tools/dotnet-build.md) příkazu k sestavení aplikace nebo [dotnet spustit](../tools/dotnet-run.md) příkazu sestavit a spustit ho.</span><span class="sxs-lookup"><span data-stu-id="dceaf-127">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="dceaf-128">Nasazení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-128">Deploy your app.</span></span>

   <span data-ttu-id="dceaf-129">Po ladit a testovat program, vytvořte nasazení pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="dceaf-129">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp2.1 -c Release
      ```
   <span data-ttu-id="dceaf-130">Tím se vytvoří vydanou verzi (místo ladění) verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-130">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="dceaf-131">Výsledné soubory jsou umístěny v adresáři s názvem *publikovat* , který je v podadresáři vašeho projektu *bin* adresáře.</span><span class="sxs-lookup"><span data-stu-id="dceaf-131">The resulting files are placed in a directory named *publish*      that's in a subdirectory of your project's *bin* directory.</span></span>

   <span data-ttu-id="dceaf-132">Proces publikování spolu se soubory vaší aplikace, generuje soubor databáze (PDB) programu, který obsahuje ladicí informace o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dceaf-132">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="dceaf-133">Soubor je užitečné hlavně pro ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="dceaf-133">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="dceaf-134">Můžete nechcete distribuovat s vaší aplikace soubory.</span><span class="sxs-lookup"><span data-stu-id="dceaf-134">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="dceaf-135">Měli byste, však uložit ho v případě, že chcete ladit sestavení pro vydání aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-135">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

   <span data-ttu-id="dceaf-136">Můžete nasadit kompletní sadu souborů aplikace žádným způsobem, který vám vyhovuje.</span><span class="sxs-lookup"><span data-stu-id="dceaf-136">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="dceaf-137">Například lze zabalit jako soubor Zip, použít jednoduchý `copy` příkazu, nebo je nasadit v balíčcích instalace podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="dceaf-137">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

1. <span data-ttu-id="dceaf-138">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="dceaf-138">Run your app</span></span>

   <span data-ttu-id="dceaf-139">Po instalaci se uživatelé můžou spustit vaši aplikaci pomocí `dotnet` příkazu a poskytuje název souboru aplikace, jako například `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="dceaf-139">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

   <span data-ttu-id="dceaf-140">Kromě binární soubory aplikace Instalační program by měl také vytvoření balíčku Instalační služby sdílené architektuře nebo vyhledat jako předpoklad jako součást instalace aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-140">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="dceaf-141">Instalace rozhraní sdílené vyžaduje přístup správce/root.</span><span class="sxs-lookup"><span data-stu-id="dceaf-141">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="dceaf-142">Nasazení závisí na architektuře s závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="dceaf-142">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="dceaf-143">Nasazení závisí na architektuře se jeden nebo více závislostí třetích stran vyžaduje, aby tyto závislosti k dispozici pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="dceaf-143">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="dceaf-144">Další dva kroky jsou požadovány, než můžete spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz:</span><span class="sxs-lookup"><span data-stu-id="dceaf-144">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="dceaf-145">Přidat odkazy na požadované knihovny třetích stran `<ItemGroup>` část vaší *csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="dceaf-145">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="dceaf-146">Následující `<ItemGroup>` oddíl obsahuje závislost na [Json.NET](http://www.newtonsoft.com/json) jako knihovny třetích stran:</span><span class="sxs-lookup"><span data-stu-id="dceaf-146">The following `<ItemGroup>` section contains a dependency on [Json.NET](http://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="dceaf-147">Pokud jste tak dosud neučinili, stáhněte si balíček NuGet obsahující závislostí třetích stran.</span><span class="sxs-lookup"><span data-stu-id="dceaf-147">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="dceaf-148">Pokud chcete stáhnout balíček, spusťte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz po přidání závislosti.</span><span class="sxs-lookup"><span data-stu-id="dceaf-148">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="dceaf-149">Protože závislost vyřeší z místní mezipaměti NuGet na čas publikování, musí být k dispozici ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="dceaf-149">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="dceaf-150">Všimněte si, že nasazení závisí na architektuře závislostí třetích stran je pouze jako přenosný jeho závislostí třetích stran.</span><span class="sxs-lookup"><span data-stu-id="dceaf-150">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="dceaf-151">Například pokud knihovny třetí strany pouze podporuje macOS, aplikace není přenosný do systémů Windows.</span><span class="sxs-lookup"><span data-stu-id="dceaf-151">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="dceaf-152">To se stane, když závislostí třetích stran, samotný závisí na nativní kód.</span><span class="sxs-lookup"><span data-stu-id="dceaf-152">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="dceaf-153">Dobrým příkladem tohoto je [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), což vyžaduje nativní závislost na [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="dceaf-153">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="dceaf-154">Po vytvoření disketové jednotky pro aplikace s tímto druhem závislostí třetích stran publikovaný výstup obsahuje složku pro každý [identifikátor modulu Runtime (RID)](../rid-catalog.md) podporující nativní závislostí (a, která existuje v jeho balíček NuGet).</span><span class="sxs-lookup"><span data-stu-id="dceaf-154">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="dceaf-155">Samostatná nasazení bez závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="dceaf-155">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="dceaf-156">Samostatná nasazení bez závislostí třetích stran zahrnuje vytvoření projektu, úpravy *csproj* souboru, sestavování, testování a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-156">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="dceaf-157">Jednoduchý příklad napsané v jazyce C# znázorňuje proces.</span><span class="sxs-lookup"><span data-stu-id="dceaf-157">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="dceaf-158">Tento příklad ukazuje, jak vytvořit samostatná nasazení pomocí [nástrojů dotnet](../tools/dotnet.md) z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="dceaf-158">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="dceaf-159">Vytvořte adresář pro projekt.</span><span class="sxs-lookup"><span data-stu-id="dceaf-159">Create a directory for the project.</span></span>

   <span data-ttu-id="dceaf-160">Vytvořte adresář pro váš projekt a nastavte ji váš aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="dceaf-160">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="dceaf-161">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="dceaf-161">Create the project.</span></span>

   <span data-ttu-id="dceaf-162">Z příkazového řádku, zadejte [nové konzoly dotnet](../tools/dotnet-new.md) v tomto adresáři vytvořte nový projekt konzoly C#.</span><span class="sxs-lookup"><span data-stu-id="dceaf-162">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="dceaf-163">Přidejte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-163">Add the application's source code.</span></span>

   <span data-ttu-id="dceaf-164">Otevřít *Program.cs* souboru ve svém editoru a automaticky vygenerovaném kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="dceaf-164">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="dceaf-165">Se zobrazí výzva k zadání textu a zobrazuje jednotlivá slova zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="dceaf-165">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="dceaf-166">Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.</span><span class="sxs-lookup"><span data-stu-id="dceaf-166">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]
1. <span data-ttu-id="dceaf-167">Definování platformy, které se zaměří na vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dceaf-167">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="dceaf-168">Vytvoření `<RuntimeIdentifiers>` značku `<PropertyGroup>` část vaší *csproj* soubor, který definuje platformy, zaměřuje a zadejte identifikátor modulu runtime (RID) pro každou platformu, která je cílem vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-168">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="dceaf-169">Všimněte si, že budete také muset přidat středníkem k oddělení identifikátory RID.</span><span class="sxs-lookup"><span data-stu-id="dceaf-169">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="dceaf-170">Zobrazit [katalog identifikátorů modulu Runtime](../rid-catalog.md) seznam identifikátorů modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="dceaf-170">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="dceaf-171">Například následující `<PropertyGroup>` části označuje, že aplikace běží na 64bitová verze Windows 10 operačních systémů a operačním systému OS 10.11 verze X 64-bit.</span><span class="sxs-lookup"><span data-stu-id="dceaf-171">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="dceaf-172">Všimněte si, že `<RuntimeIdentifiers>` element lze použít v libovolném `<PropertyGroup>` ve vašich *csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="dceaf-172">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="dceaf-173">Úplnou ukázku *csproj* souboru se zobrazí později v této části.</span><span class="sxs-lookup"><span data-stu-id="dceaf-173">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="dceaf-174">Aktualizujte závislosti projektu a nástroje.</span><span class="sxs-lookup"><span data-stu-id="dceaf-174">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="dceaf-175">Spustit [dotnet restore](../tools/dotnet-restore.md) ([viz Poznámka](#dotnet-restore-note)) příkaz pro obnovení závislosti zadaný ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="dceaf-175">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="dceaf-176">Určete, jestli chcete použít režim globalizace invariantní.</span><span class="sxs-lookup"><span data-stu-id="dceaf-176">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="dceaf-177">Zejména v případě, že vaše aplikace cílí na Linux, můžete snížit celkovou velikost vašeho nasazení s využitím [invariantní režimu globalizace](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="dceaf-177">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="dceaf-178">Globalizace invariantní režim je užitečný pro aplikace, které nejsou globální a které používají konvence formátování, konvence malých a velkých písmen a řetězec porovnání a řazení pořadí [invariantní jazyková verze](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="dceaf-178">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="dceaf-179">Výchozí režim povolit, klikněte pravým tlačítkem na projekt (nikoli řešení) v **Průzkumníka řešení**a vyberte **upravit SCD.csproj** nebo **upravit SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="dceaf-179">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="dceaf-180">Pak přidejte následující zvýrazněný řádky do souboru:</span><span class="sxs-lookup"><span data-stu-id="dceaf-180">Then add the following highlighted lines to the file:</span></span>

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. <span data-ttu-id="dceaf-181">Vytvořte sestavení pro ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-181">Create a Debug build of your app.</span></span>

   <span data-ttu-id="dceaf-182">Z příkazového řádku, použijte [dotnet sestavení](../tools/dotnet-build.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="dceaf-182">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="dceaf-183">Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací pro každou platformu, zaměřuje.</span><span class="sxs-lookup"><span data-stu-id="dceaf-183">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="dceaf-184">Použití `dotnet publish` příkaz pro obě cílových platforem následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="dceaf-184">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="dceaf-185">Tím se vytvoří vydanou verzi (místo ladění) verze vaší aplikace pro každou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="dceaf-185">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="dceaf-186">Výsledné soubory jsou umístěny v podadresáři s názvem *publikovat* , který je v podadresáři vašeho projektu *.\bin\Release\netcoreapp2.1\<runtime_identifier >* podadresáře.</span><span class="sxs-lookup"><span data-stu-id="dceaf-186">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp2.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="dceaf-187">Všimněte si, že každý podadresář obsahuje kompletní sadu souborů (soubory aplikace a všechny soubory .NET Core) potřebné pro spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-187">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="dceaf-188">Proces publikování spolu se soubory vaší aplikace, generuje soubor databáze (PDB) programu, který obsahuje ladicí informace o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dceaf-188">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="dceaf-189">Soubor je užitečné hlavně pro ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="dceaf-189">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="dceaf-190">Můžete není balíček se soubory vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-190">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="dceaf-191">Měli byste, však uložit ho v případě, že chcete ladit sestavení pro vydání aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-191">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="dceaf-192">Nasaďte publikované soubory žádným způsobem, který vám vyhovuje.</span><span class="sxs-lookup"><span data-stu-id="dceaf-192">Deploy the published files in any way you like.</span></span> <span data-ttu-id="dceaf-193">Například lze zabalit jako soubor Zip, použít jednoduchý `copy` příkazu, nebo je nasadit v balíčcích instalace podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="dceaf-193">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="dceaf-194">Tady je úplný *csproj* souboru pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="dceaf-194">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="dceaf-195">Samostatná nasazení s závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="dceaf-195">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="dceaf-196">Samostatná nasazení s jeden nebo více závislostí třetích stran, zahrnuje přidání závislosti.</span><span class="sxs-lookup"><span data-stu-id="dceaf-196">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="dceaf-197">Další dva kroky jsou požadovány, než můžete spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz:</span><span class="sxs-lookup"><span data-stu-id="dceaf-197">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="dceaf-198">Přidat odkazy na žádné knihovny třetích stran `<ItemGroup>` část vaší *csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="dceaf-198">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="dceaf-199">Následující `<ItemGroup>` části používá technologii Json.NET jako knihovny třetí strany.</span><span class="sxs-lookup"><span data-stu-id="dceaf-199">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="dceaf-200">Pokud jste tak dosud neučinili, stáhněte si balíček NuGet obsahující závislostí třetích stran do vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="dceaf-200">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="dceaf-201">Pokud chcete zpřístupnit závislost do aplikace, spusťte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) příkaz po přidání závislosti.</span><span class="sxs-lookup"><span data-stu-id="dceaf-201">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="dceaf-202">Protože závislost vyřeší z místní mezipaměti NuGet na čas publikování, musí být k dispozici ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="dceaf-202">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="dceaf-203">Tady je úplný *csproj* souboru pro tento projekt:</span><span class="sxs-lookup"><span data-stu-id="dceaf-203">The following is the complete *csproj* file for this project:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="dceaf-204">Při nasazení vaší aplikace jsou také obsažena případných závislostí třetích stran používají ve vaší aplikaci se soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="dceaf-204">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="dceaf-205">V systému, na kterém běží aplikace nejsou vyžadovány knihovny třetích stran.</span><span class="sxs-lookup"><span data-stu-id="dceaf-205">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="dceaf-206">Všimněte si, že lze nasadit pouze samostatná nasazení pomocí knihovny třetí strany na platformách podporovaných aplikací tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="dceaf-206">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="dceaf-207">Toto je podobný s tím, že závislostí třetích stran s nativní závislosti v nasazení závisí na architektuře, kde musí být kompatibilní s platformou, do kterého byla nasazena aplikace, nativní závislosti.</span><span class="sxs-lookup"><span data-stu-id="dceaf-207">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

## <a name="see-also"></a><span data-ttu-id="dceaf-208">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dceaf-208">See also</span></span>

* [<span data-ttu-id="dceaf-209">Nasazení aplikace .NET core</span><span class="sxs-lookup"><span data-stu-id="dceaf-209">.NET Core Application Deployment</span></span>](index.md)
* [<span data-ttu-id="dceaf-210">.NET core Runtime identifikátor (RID) katalogu</span><span class="sxs-lookup"><span data-stu-id="dceaf-210">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
