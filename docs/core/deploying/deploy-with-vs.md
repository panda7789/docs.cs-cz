---
title: Nasazení aplikace .NET core pomocí sady Visual Studio
description: Zjistěte, nasazení aplikace .NET Core pomocí sady Visual Studio
author: rpetrusha
ms.author: ronpet
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 7a9410ca99f621ee6d0e8b263354ebc536f71a4a
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46518217"
---
# <a name="deploying-net-core-apps-with-visual-studio"></a><span data-ttu-id="cd0a0-103">Nasazení .NET Core aplikací pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cd0a0-103">Deploying .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="cd0a0-104">Můžete nasadit aplikaci .NET Core buď jako *nasazení závisí na architektuře*, který obsahuje binární soubory vaší aplikace, ale závisí na přítomnosti .NET Core v cílovém systému, nebo jako *samostatná nasazení*, což zahrnuje aplikace a .NET Core binární soubory.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="cd0a0-105">Přehled nasazení aplikace .NET Core, naleznete v tématu [nasazení aplikace .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="cd0a0-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="cd0a0-106">Následující části vysvětlují, jak pomocí sady Microsoft Visual Studio vytvořit následující typy nasazení:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="cd0a0-107">Nasazení závisí na architektuře</span><span class="sxs-lookup"><span data-stu-id="cd0a0-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="cd0a0-108">Nasazení závisí na architektuře s závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="cd0a0-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="cd0a0-109">Samostatná nasazení</span><span class="sxs-lookup"><span data-stu-id="cd0a0-109">Self-contained deployment</span></span>
- <span data-ttu-id="cd0a0-110">Samostatná nasazení s závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="cd0a0-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="cd0a0-111">Informace o používání sady Visual Studio pro vývoj aplikací .NET Core najdete v tématu [předpoklady pro .NET Core ve Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).</span><span class="sxs-lookup"><span data-stu-id="cd0a0-111">For information on using Visual Studio to develop .NET Core applications, see [Prerequisites for .NET Core on Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="cd0a0-112">Nasazení závisí na architektuře</span><span class="sxs-lookup"><span data-stu-id="cd0a0-112">Framework-dependent deployment</span></span>

<span data-ttu-id="cd0a0-113">Nasazení závisí na architektuře bez závislostí třetích stran zahrnuje vytváření, testování a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="cd0a0-114">Jednoduchý příklad napsané v jazyce C# znázorňuje proces.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-114">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="cd0a0-115">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-115">Create the project.</span></span>

   <span data-ttu-id="cd0a0-116">Vyberte **souboru** > **nové** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="cd0a0-117">V **nový projekt** dialogového okna, rozšířit vaše jazyka (C# nebo Visual Basic) kategorie projektů v **nainstalováno** podokně typů projektů, zvolte **.NET Core**a pak vyberte **Konzolová aplikace (.NET Core)** šablon v prostředním podokně.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="cd0a0-118">Zadejte název projektu, jako je například "Chyba" v **název** textového pole.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="cd0a0-119">Vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="cd0a0-120">Přidejte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-120">Add the application's source code.</span></span>

   <span data-ttu-id="cd0a0-121">Otevřít *Program.cs* nebo *soubor Program.vb* souboru v editoru a automaticky vygenerovaném kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="cd0a0-122">Se zobrazí výzva k zadání textu a zobrazuje jednotlivá slova zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="cd0a0-123">Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="cd0a0-124">Vytvořte sestavení pro ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="cd0a0-125">Vyberte **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="cd0a0-126">Můžete také kompilace a spuštění sestavení pro ladění vaší aplikace tak, že vyberete **ladění** > **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="cd0a0-127">Nasazení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-127">Deploy your app.</span></span>

   <span data-ttu-id="cd0a0-128">Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="cd0a0-129">Chcete-li publikovat ze sady Visual Studio, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="cd0a0-130">Změňte konfiguraci řešení z **ladění** k **vydání** na panelu nástrojů k sestavení a vydání (tzn. Ne a ladění) verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="cd0a0-131">Klikněte pravým tlačítkem na projekt (nikoli řešení) v **Průzkumníka řešení** a vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="cd0a0-132">V **publikovat** kartu, vyberte možnost **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="cd0a0-133">Visual Studio zapíše soubory, které tvoří vaši aplikaci do místního systému souborů.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="cd0a0-134">**Publikovat** karta nyní zobrazuje jeden profil, **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="cd0a0-135">Nastavení profilu konfigurace jsou uvedeny v **Souhrn** části karty.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="cd0a0-136">Výsledné soubory jsou umístěny v adresáři s názvem `Publish` na Windows a `publish` v systémech Unix, které je v podadresáři vašeho projektu *.\bin\release\netcoreapp2.1* podadresáře.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="cd0a0-137">Proces publikování spolu se soubory vaší aplikace, generuje soubor databáze (PDB) programu, který obsahuje ladicí informace o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="cd0a0-138">Soubor je užitečné hlavně pro ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="cd0a0-139">Můžete není balíček se soubory vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="cd0a0-140">Měli byste, však uložit ho v případě, že chcete ladit sestavení pro vydání aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="cd0a0-141">Nasaďte kompletní sadu souborů aplikace žádným způsobem, který vám vyhovuje.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="cd0a0-142">Například lze zabalit jako soubor Zip, použít jednoduchý `copy` příkazu, nebo je nasadit v balíčcích instalace podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="cd0a0-143">Po instalaci se uživatelům může pak spustit vaši aplikaci s použitím `dotnet` příkazu a poskytuje název souboru aplikace, jako například `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="cd0a0-144">Kromě binární soubory aplikace Instalační program by měl také vytvoření balíčku Instalační služby sdílené architektuře nebo vyhledat jako předpoklad jako součást instalace aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="cd0a0-145">Instalace rozhraní sdílené vyžaduje přístup správce/root, protože jde o celý počítač.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="cd0a0-146">Nasazení závisí na architektuře s závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="cd0a0-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="cd0a0-147">Nasazení závisí na architektuře se jeden nebo více závislostí třetích stran vyžaduje, aby všechny závislosti k dispozici pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="cd0a0-148">Následující kroky jsou požadovány, než můžete vytvářet aplikace:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="cd0a0-149">Použití **Správce balíčků NuGet** přidejte odkaz na balíček NuGet do projektu, a pokud balíček už není k dispozici ve vašem systému, nainstalujte ho.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="cd0a0-150">Chcete-li spustit nástroj Správce balíčku, vyberte **nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="cd0a0-151">Ujistěte se, že `Newtonsoft.Json` je nainstalovaný ve vašem systému a pokud není, nainstalujte ho.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-151">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="cd0a0-152">**Nainstalováno** karta obsahuje balíčky NuGet ve vašem systému nainstalována.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="cd0a0-153">Pokud `Newtonsoft.Json` není uvedená, vyberte **Procházet** kartu a do vyhledávacího pole zadejte "Newtonsoft.Json".</span><span class="sxs-lookup"><span data-stu-id="cd0a0-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="cd0a0-154">Vyberte `Newtonsoft.Json` a v pravém podokně vyberte svůj projekt před výběrem **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="cd0a0-155">Pokud `Newtonsoft.Json` je už nainstalovaný ve vašem systému, přidejte ho do projektu výběrem projektu v pravém podokně **spravovat balíčky pro řešení** kartu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="cd0a0-156">Všimněte si, že nasazení závisí na architektuře závislostí třetích stran je pouze jako přenosný jeho závislostí třetích stran.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="cd0a0-157">Například pokud knihovny třetí strany pouze podporuje macOS, aplikace není přenosný do systémů Windows.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="cd0a0-158">To se stane, když závislostí třetích stran, samotný závisí na nativní kód.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="cd0a0-159">Dobrým příkladem tohoto je [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), což vyžaduje nativní závislost na [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="cd0a0-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="cd0a0-160">Po vytvoření disketové jednotky pro aplikace s tímto druhem závislostí třetích stran publikovaný výstup obsahuje složku pro každý [identifikátor modulu Runtime (RID)](../rid-catalog.md) podporující nativní závislostí (a, která existuje v jeho balíček NuGet).</span><span class="sxs-lookup"><span data-stu-id="cd0a0-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="cd0a0-161">Samostatná nasazení bez závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="cd0a0-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="cd0a0-162">Samostatná nasazení bez závislostí třetích stran zahrnuje vytvoření projektu, úpravy *csproj* souboru, sestavování, testování a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="cd0a0-163">Jednoduchý příklad napsané v jazyce C# znázorňuje proces.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="cd0a0-164">Začnete vytvořením, kódování a testování projektu stejně, jako byste to závisí na architektuře nasazení:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="cd0a0-165">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-165">Create the project.</span></span>

   <span data-ttu-id="cd0a0-166">Vyberte **souboru** > **nové** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="cd0a0-167">V **nový projekt** dialogového okna, rozšířit vaše jazyka (C# nebo Visual Basic) kategorie projektů v **nainstalováno** podokně typů projektů, zvolte **.NET Core**a pak vyberte **Konzolová aplikace (.NET Core)** šablon v prostředním podokně.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="cd0a0-168">Zadejte název projektu, jako je například "SCD" **název** textového pole a vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="cd0a0-169">Přidejte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-169">Add the application's source code.</span></span>

   <span data-ttu-id="cd0a0-170">Otevřít *Program.cs* nebo souboru v editoru a automaticky vygenerovaném kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-170">Open the *Program.cs* or file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="cd0a0-171">Se zobrazí výzva k zadání textu a zobrazuje jednotlivá slova zadané uživatelem.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="cd0a0-172">Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="cd0a0-173">Určete, jestli chcete použít režim globalizace invariantní.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="cd0a0-174">Zejména v případě, že vaše aplikace cílí na Linux, můžete snížit celkovou velikost vašeho nasazení s využitím [invariantní režimu globalizace](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="cd0a0-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="cd0a0-175">Globalizace invariantní režim je užitečný pro aplikace, které nejsou globální a které používají konvence formátování, konvence malých a velkých písmen a řetězec porovnání a řazení pořadí [invariantní jazyková verze](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="cd0a0-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="cd0a0-176">Výchozí režim povolit, klikněte pravým tlačítkem na projekt (nikoli řešení) v **Průzkumníka řešení**a vyberte **upravit SCD.csproj** nebo **upravit SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="cd0a0-177">Pak přidejte následující zvýrazněný řádky do souboru:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-177">Then add the following highlighted lines to the file:</span></span>

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. <span data-ttu-id="cd0a0-178">Vytvořte sestavení pro ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="cd0a0-179">Vyberte **sestavení** > **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="cd0a0-180">Můžete také kompilace a spuštění sestavení pro ladění vaší aplikace tak, že vyberete **ladění** > **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="cd0a0-181">Tento krok ladění vám umožní identifikovat problémy s vaší aplikací při spuštění na vaší platformě hostitele.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="cd0a0-182">Budete stále muset testování na všech cílových platforem.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="cd0a0-183">Pokud jste povolili invariantní režimu globalizace, ujistěte se, zejména k ověření, zda neexistence dat zohledňující jazykovou verzi je vhodná pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="cd0a0-184">Po dokončení ladění, můžete publikovat samostatná nasazení:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="cd0a0-185">Visual Studio 15.6 a starší</span><span class="sxs-lookup"><span data-stu-id="cd0a0-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="cd0a0-186">Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací pro každou platformu, zaměřuje.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="cd0a0-187">K publikování aplikace ze sady Visual Studio, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="cd0a0-188">Definování platformy, které se zaměří na vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="cd0a0-189">Klikněte pravým tlačítkem na projekt (nikoli řešení) **Průzkumníka řešení** a vyberte **upravit SCD.csproj**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="cd0a0-190">Vytvoření `<RuntimeIdentifiers>` značku `<PropertyGroup>` část vaší *csproj* soubor, který definuje vaše aplikace cílí platformy a zadejte identifikátor modulu runtime (RID) pro každou platformu, která je cílem.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="cd0a0-191">Všimněte si, že budete také muset přidat středníkem k oddělení identifikátory RID.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-191">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="cd0a0-192">Zobrazit [katalog identifikátorů modulu Runtime](../rid-catalog.md) seznam identifikátorů modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="cd0a0-193">Následující příklad například označuje, že aplikace běží na 64bitová verze Windows 10 operačních systémů a operačním systému OS 10.11 verze X 64-bit.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="cd0a0-194">Všimněte si, že `<RuntimeIdentifiers>` element můžete přejít do libovolného `<PropertyGroup>` , kterou máte vaše *csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-194">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="cd0a0-195">Úplnou ukázku *csproj* souboru se zobrazí později v této části.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="cd0a0-196">Publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-196">Publish your app.</span></span>

   <span data-ttu-id="cd0a0-197">Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací pro každou platformu, zaměřuje.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="cd0a0-198">K publikování aplikace ze sady Visual Studio, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="cd0a0-199">Změňte konfiguraci řešení z **ladění** k **vydání** na panelu nástrojů k sestavení a vydání (tzn. Ne a ladění) verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="cd0a0-200">Klikněte pravým tlačítkem na projekt (nikoli řešení) v **Průzkumníka řešení** a vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="cd0a0-201">V **publikovat** kartu, vyberte možnost **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="cd0a0-202">Visual Studio zapíše soubory, které tvoří vaši aplikaci do místního systému souborů.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="cd0a0-203">**Publikovat** karta nyní zobrazuje jeden profil, **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="cd0a0-204">Nastavení profilu konfigurace jsou uvedeny v **Souhrn** části karty. **Cílové prostředí Runtime** identifikuje, které modul runtime byla publikována, a **cílové umístění** identifikuje, ve kterém byly vytvořeny soubory pro samostatné nasazení.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="cd0a0-205">Visual Studio ve výchozím nastavení zapíše že všechny publikované soubory do jednoho adresáře.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="cd0a0-206">Pro usnadnění práce je nejlepší vytvořit samostatné profily pro každý cílový modul runtime a zadávat publikované soubory v adresáři pro konkrétní platformu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="cd0a0-207">To zahrnuje vytvoření samostatný profil publikování pro každou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="cd0a0-208">Takže teď znovu sestavte aplikaci pro každou platformu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="cd0a0-209">Vyberte **vytvořit nový profil** v **publikovat** dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="cd0a0-210">V **vyberte cíl publikování** dialogové okno Změnit **zvolte složku** umístění *bin\Release\PublishOutput\win10 x64*.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="cd0a0-211">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-211">Select **OK**.</span></span>

         1. <span data-ttu-id="cd0a0-212">Vyberte nový profil (**FolderProfile1**) v seznamu profilů a ujistěte se, že **cílový modul Runtime** je `win10-x64`.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="cd0a0-213">Pokud tomu tak není, vyberte **nastavení**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="cd0a0-214">V **nastavení profilu** dialogové okno Změnit **cílový modul Runtime** k `win10-x64` a vyberte **Uložit**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="cd0a0-215">V opačném případě vyberte **zrušit**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="cd0a0-216">Vyberte **publikovat** a publikujte svou aplikaci pro 64bitové platformy Windows 10.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="cd0a0-217">Postupujte podle předchozích kroků znovu vytvořit profil `osx.10.11-x64` platformy.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="cd0a0-218">**Cílové umístění** je *bin\Release\PublishOutput\osx.10.11-x64*a **cílový modul Runtime** je `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="cd0a0-219">Název sady Visual Studio přiřadí k tomuto profilu je **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="cd0a0-220">Všimněte si, že každý cílové umístění obsahuje kompletní sadu souborů (soubory aplikace a všechny soubory .NET Core) potřebné pro spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-220">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="cd0a0-221">Proces publikování spolu se soubory vaší aplikace, generuje soubor databáze (PDB) programu, který obsahuje ladicí informace o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="cd0a0-222">Soubor je užitečné hlavně pro ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="cd0a0-223">Můžete není balíček se soubory vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="cd0a0-224">Měli byste, však uložit ho v případě, že chcete ladit sestavení pro vydání aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="cd0a0-225">Nasaďte publikované soubory žádným způsobem, který vám vyhovuje.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="cd0a0-226">Například lze zabalit jako soubor Zip, použít jednoduchý `copy` příkazu, nebo je nasadit v balíčcích instalace podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="cd0a0-227">Tady je úplný *csproj* souboru pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="cd0a0-228">Visual Studio 15.7 nebo novější</span><span class="sxs-lookup"><span data-stu-id="cd0a0-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="cd0a0-229">Po ladit a testovat program, vytvoření souborů k nasazení s vaší aplikací pro každou platformu, zaměřuje.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="cd0a0-230">To zahrnuje vytvoření samostatný profil pro každou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="cd0a0-231">Pro každou platformu, že vaše aplikace cílí, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="cd0a0-232">Vytvoření profilu pro cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="cd0a0-233">Pokud je toto první profil, který jste vytvořili, klikněte pravým tlačítkem na projekt (nikoli řešení) **Průzkumníka řešení** a vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="cd0a0-234">Pokud už máte vytvořený profil, klikněte pravým tlačítkem na projekt otevřít **publikovat** dialogové okno, pokud ještě není otevřeno.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="cd0a0-235">Potom vyberte **nový profil**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="cd0a0-236">**Vyberte cíl publikování** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-236">The **Pick a Publish Target** dialog box opens.</span></span>
  
1. <span data-ttu-id="cd0a0-237">Vyberte umístění, kde sady Visual Studio publikuje vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="cd0a0-238">Pokud publikujete pouze do jedné platformy, můžete přijmout výchozí hodnotu v **zvolte složku** textové pole; to publikuje nasazení závislé architektury aplikace \*\<adresáře projektu > \ bin\Release\netcoreapp2.1\publish\* adresáře.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the \*\<project-directory>\bin\Release\netcoreapp2.1\publish\* directory.</span></span>

   <span data-ttu-id="cd0a0-239">Pokud publikujete do více než jedné platformě, připojte řetězec, který určuje cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="cd0a0-240">Například pokud připojte řetězec "linux" pro cestu k souboru, Visual Studio publikuje nasazení závislé architektury aplikace  *\<adresáře projektu > \bin\Release\netcoreapp2.1\publish\linux*adresáře.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="cd0a0-241">Vytvoření profilu tak, že vyberete ikonu rozevíracího seznamu vedle položky **publikovat** tlačítko a vyberete **vytvořit profil**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="cd0a0-242">Vyberte **vytvořit profil** pro vytvoření profilu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="cd0a0-243">Označuje, že publikujete samostatná nasazení a definovat platformu, která se zaměří na vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="cd0a0-244">V **publikovat** dialogového okna, vyberte **konfigurovat** odkaz k otevření **nastavení profilu** dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="cd0a0-245">Vyberte **samostatná** v **režim nasazení** pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="cd0a0-246">V **cílový modul Runtime** seznamu, vyberte některou z platforem, které vaše aplikace cílí.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="cd0a0-247">Vyberte **Uložit** potvrďte provedené změny a zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="cd0a0-248">Zadejte název profilu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-248">Name your profile.</span></span>

   1. <span data-ttu-id="cd0a0-249">Vyberte **akce** > **Přejmenovat profil** název profilu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="cd0a0-250">Váš profil přiřadit název k identifikaci cílové platformy a pak vyberte \**Uložit*.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="cd0a0-251">Opakujte tyto kroky, chcete-li definovat žádné další cílové platformy, které vaše aplikace cílí.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="cd0a0-252">Konfigurované profily a jste připraveni publikovat vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="cd0a0-253">To uděláte takto:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-253">To do this:</span></span>

   1. <span data-ttu-id="cd0a0-254">Pokud **publikovat** okno není otevřený, klikněte pravým tlačítkem na projekt (nikoli řešení) v **Průzkumníka řešení** a vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="cd0a0-255">Vyberte profil, který chcete publikovat a pak vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="cd0a0-256">Proveďte pro každý profil, který má být publikován.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="cd0a0-257">Všimněte si, že každý cílové umístění (v případě v našem příkladu bin\release\netcoreapp2.1\publish\\*název profilu* obsahuje kompletní sadu souborů (soubory aplikace a všechny soubory .NET Core) potřebných pro spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-257">Note that each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="cd0a0-258">Proces publikování spolu se soubory vaší aplikace, generuje soubor databáze (PDB) programu, který obsahuje ladicí informace o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="cd0a0-259">Soubor je užitečné hlavně pro ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="cd0a0-260">Můžete není balíček se soubory vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="cd0a0-261">Měli byste, však uložit ho v případě, že chcete ladit sestavení pro vydání aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="cd0a0-262">Nasaďte publikované soubory žádným způsobem, který vám vyhovuje.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="cd0a0-263">Například lze zabalit jako soubor Zip, použít jednoduchý `copy` příkazu, nebo je nasadit v balíčcích instalace podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="cd0a0-264">Tady je úplný *csproj* souboru pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="cd0a0-265">Kromě toho sada Visual Studio vytvoří samostatný profil publikování (\*.pubxml) pro každou platformu, na které cílíte.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="cd0a0-266">Například soubor pro naše profilu linuxu (linux.pubxml) se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121. 
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="cd0a0-267">Samostatná nasazení s závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="cd0a0-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="cd0a0-268">Samostatná nasazení s jeden nebo více závislostí třetích stran, zahrnuje přidání závislosti.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="cd0a0-269">Následující kroky jsou požadovány, než můžete vytvářet aplikace:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="cd0a0-270">Použití **Správce balíčků NuGet** přidejte odkaz na balíček NuGet do projektu, a pokud balíček už není k dispozici ve vašem systému, nainstalujte ho.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="cd0a0-271">Chcete-li spustit nástroj Správce balíčku, vyberte **nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="cd0a0-272">Ujistěte se, že `Newtonsoft.Json` je nainstalovaný ve vašem systému a pokud není, nainstalujte ho.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-272">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="cd0a0-273">**Nainstalováno** karta obsahuje balíčky NuGet ve vašem systému nainstalována.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="cd0a0-274">Pokud `Newtonsoft.Json` není uvedená, vyberte **Procházet** kartu a do vyhledávacího pole zadejte "Newtonsoft.Json".</span><span class="sxs-lookup"><span data-stu-id="cd0a0-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="cd0a0-275">Vyberte `Newtonsoft.Json` a v pravém podokně vyberte svůj projekt před výběrem **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="cd0a0-276">Pokud `Newtonsoft.Json` je už nainstalovaný ve vašem systému, přidejte ho do projektu výběrem projektu v pravém podokně **spravovat balíčky pro řešení** kartu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="cd0a0-277">Tady je úplný *csproj* souboru pro tento projekt:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="cd0a0-278">Visual Studio 15.6 a starší</span><span class="sxs-lookup"><span data-stu-id="cd0a0-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

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

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="cd0a0-279">Visual Studio 15.7 nebo novější</span><span class="sxs-lookup"><span data-stu-id="cd0a0-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

<span data-ttu-id="cd0a0-280">Při nasazení vaší aplikace jsou také obsažena případných závislostí třetích stran používají ve vaší aplikaci se soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="cd0a0-281">V systému, na kterém běží aplikace nejsou vyžadovány knihovny třetích stran.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="cd0a0-282">Všimněte si, že lze nasadit pouze samostatná nasazení pomocí knihovny třetí strany na platformách podporovaných aplikací tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-282">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="cd0a0-283">Toto je podobný s tím, že závislostí třetích stran s nativní závislosti ve vašem nasazení závisí na architektuře, kde neexistují nativní závislosti na cílové platformě, pokud byly dříve nainstalovány existuje.</span><span class="sxs-lookup"><span data-stu-id="cd0a0-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd0a0-284">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd0a0-284">See also</span></span>

* [<span data-ttu-id="cd0a0-285">Nasazení aplikace .NET core</span><span class="sxs-lookup"><span data-stu-id="cd0a0-285">.NET Core Application Deployment</span></span>](index.md)
* [<span data-ttu-id="cd0a0-286">.NET core Runtime identifikátor (RID) katalogu</span><span class="sxs-lookup"><span data-stu-id="cd0a0-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
