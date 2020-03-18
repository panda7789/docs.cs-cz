---
title: Nasazení aplikací .NET Core pomocí Sady Visual Studio
description: Naučte se nasadit aplikaci .NET Core pomocí Sady Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 11a322278ce3ff38964fe2fa389e0b4a58897ec4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449020"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a><span data-ttu-id="14e5b-103">Nasazení aplikací .NET Core pomocí Sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="14e5b-103">Deploy .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="14e5b-104">Můžete nasadit aplikaci .NET Core buď jako *nasazení závislé na rámci*, která zahrnuje binární soubory aplikace, ale závisí na přítomnosti .NET Core v cílovém systému, nebo jako samostatné *nasazení*, které zahrnuje obě aplikace a binární soubory .NET Core.</span><span class="sxs-lookup"><span data-stu-id="14e5b-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="14e5b-105">Přehled nasazení aplikace .NET Core naleznete v tématu [.NET Core Application Deployment](index.md).</span><span class="sxs-lookup"><span data-stu-id="14e5b-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="14e5b-106">Následující části ukazují, jak pomocí sady Microsoft Visual Studio vytvořit následující typy nasazení:</span><span class="sxs-lookup"><span data-stu-id="14e5b-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="14e5b-107">Nasazení závislé na rámci</span><span class="sxs-lookup"><span data-stu-id="14e5b-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="14e5b-108">Nasazení závislé na rámci se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="14e5b-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="14e5b-109">Samostatné nasazení</span><span class="sxs-lookup"><span data-stu-id="14e5b-109">Self-contained deployment</span></span>
- <span data-ttu-id="14e5b-110">Samostatné nasazení se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="14e5b-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="14e5b-111">Informace o vývoji základních aplikací .NET pomocí sady Visual Studio naleznete v [tématu .NET Core závislostí a požadavků](../install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="14e5b-111">For information on using Visual Studio to develop .NET Core applications, see [.NET Core dependencies and requirements](../install/dependencies.md?pivots=os-windows).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="14e5b-112">Nasazení závislé na rámci</span><span class="sxs-lookup"><span data-stu-id="14e5b-112">Framework-dependent deployment</span></span>

<span data-ttu-id="14e5b-113">Nasazení nasazení závislé na rámci bez závislostí třetích stran jednoduše zahrnuje vytváření, testování a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="14e5b-114">Jednoduchý příklad napsaný v C# ilustruje proces.</span><span class="sxs-lookup"><span data-stu-id="14e5b-114">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="14e5b-115">Vytvořte projekt.</span><span class="sxs-lookup"><span data-stu-id="14e5b-115">Create the project.</span></span>

   <span data-ttu-id="14e5b-116">Vyberte **Soubor** > **nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="14e5b-117">V dialogovém okně **Nový projekt** rozbalte kategorie projektu jazyka (C# nebo Visual Basic) v podokně **Nainstalované** typy projektů, zvolte **.NET Core**a v prostředním podokně vyberte šablonu **Konzola Aplikace (.NET Core).**</span><span class="sxs-lookup"><span data-stu-id="14e5b-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="14e5b-118">Do textového pole **Název** zadejte název projektu, například FDD.</span><span class="sxs-lookup"><span data-stu-id="14e5b-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="14e5b-119">Vyberte tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="14e5b-120">Přidejte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-120">Add the application's source code.</span></span>

   <span data-ttu-id="14e5b-121">Otevřete soubor *Program.cs* nebo *Program.vb* v editoru a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="14e5b-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="14e5b-122">Vyzve uživatele k zadání textu a zobrazí jednotlivá slova zadaná uživatelem.</span><span class="sxs-lookup"><span data-stu-id="14e5b-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="14e5b-123">Používá regulární `\w+` výraz k oddělení slov ve vstupním textu.</span><span class="sxs-lookup"><span data-stu-id="14e5b-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="14e5b-124">Vytvořte sestavení ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="14e5b-125">Vyberte **sestavení** > **sestavení řešení**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="14e5b-126">Můžete také zkompilovat a spustit sestavení ladění aplikace výběrem ladění **ladění** > **start**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="14e5b-127">Nasaďte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="14e5b-127">Deploy your app.</span></span>

   <span data-ttu-id="14e5b-128">Po odladění a testování programu vytvořte soubory, které se mají nasadit s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="14e5b-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="14e5b-129">Chcete-li publikovat z visual studia, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="14e5b-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="14e5b-130">Změňte konfiguraci řešení z **Ladění** na **uvolnění** na panelu nástrojů a vytvořte verzi aplikace release (namísto ladění).</span><span class="sxs-lookup"><span data-stu-id="14e5b-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="14e5b-131">Klikněte pravým tlačítkem myši na projekt (ne na řešení) v **Průzkumníku řešení** a vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="14e5b-132">Na kartě **Publikovat** vyberte **Publikovat**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="14e5b-133">Visual Studio zapisuje soubory, které tvoří vaši aplikaci do místního systému souborů.</span><span class="sxs-lookup"><span data-stu-id="14e5b-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="14e5b-134">Na kartě **Publikovat** se nyní zobrazuje jeden profil **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="14e5b-135">Nastavení konfigurace profilu se zobrazí v části **Souhrn** na kartě.</span><span class="sxs-lookup"><span data-stu-id="14e5b-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="14e5b-136">Výsledné soubory jsou umístěny v `Publish` adresáři `publish` pojmenovaném v systému Windows a v systémech Unix, který je umístěn v podadresáři podadresáře projektu *.\bin\release\netcoreapp2.1.*</span><span class="sxs-lookup"><span data-stu-id="14e5b-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="14e5b-137">Spolu se soubory vaší aplikace vydává proces publikování soubor databáze programů (.pdb), který obsahuje informace o ladění o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="14e5b-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="14e5b-138">Soubor je užitečný především pro ladění výjimek.</span><span class="sxs-lookup"><span data-stu-id="14e5b-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="14e5b-139">Můžete se rozhodnout, že ji nezabalíte se soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="14e5b-140">Měli byste ji však uložit v případě, že chcete ladit sestavení verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="14e5b-141">Nasaďte celou sadu souborů aplikací jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="14e5b-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="14e5b-142">Můžete je například zabalit do souboru `copy` ZIP, použít jednoduchý příkaz nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="14e5b-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="14e5b-143">Po instalaci mohou uživatelé spustit aplikaci pomocí příkazu `dotnet` a poskytnutím názvu souboru aplikace, například `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="14e5b-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="14e5b-144">Kromě binárních souborů aplikace by měl instalační program také sdružovat instalační program sdílené ho rozhraní nebo jej zkontrolovat jako předpoklad v rámci instalace aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="14e5b-145">Instalace sdílené ho rozhraní vyžaduje přístup správce/root, protože je celopočítačová.</span><span class="sxs-lookup"><span data-stu-id="14e5b-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="14e5b-146">Nasazení závislé na rámci se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="14e5b-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="14e5b-147">Nasazení nasazení závislé na rozhraní s jednou nebo více závislostmi třetích stran vyžaduje, aby všechny závislosti být k dispozici pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="14e5b-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="14e5b-148">Před vytvořením aplikace jsou vyžadovány následující další kroky:</span><span class="sxs-lookup"><span data-stu-id="14e5b-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="14e5b-149">Pomocí **Správce balíčků NuGet** přidat odkaz na balíček NuGet do projektu; a pokud balíček ještě není ve vašem systému k dispozici, nainstalujte jej.</span><span class="sxs-lookup"><span data-stu-id="14e5b-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="14e5b-150">Chcete-li otevřít správce balíčků, vyberte **nástroje, které** > **spravují správce** > balíčků**NuGet, pro řešení**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="14e5b-151">Zkontrolujte, zda jsou v systému `Newtonsoft.Json`nainstalovány vaše závislosti třetích stran (například) a pokud nejsou, nainstalujte je.</span><span class="sxs-lookup"><span data-stu-id="14e5b-151">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="14e5b-152">Na kartě **Nainstalováno** jsou uvedeny balíčky NuGet nainstalované v systému.</span><span class="sxs-lookup"><span data-stu-id="14e5b-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="14e5b-153">Pokud `Newtonsoft.Json` zde není uvedena, vyberte kartu **Procházet** a do vyhledávacího pole zadejte "Newtonsoft.Json".</span><span class="sxs-lookup"><span data-stu-id="14e5b-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="14e5b-154">Vyberte `Newtonsoft.Json` a v pravém podokně vyberte projekt před výběrem **možnosti Instalovat**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="14e5b-155">Pokud `Newtonsoft.Json` je již v systému nainstalován, přidejte jej do projektu výběrem projektu v pravém podokně na kartě **Spravovat balíčky pro řešení.**</span><span class="sxs-lookup"><span data-stu-id="14e5b-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="14e5b-156">Nasazení závislé na rámci se závislostmi třetích stran je pouze tak přenosné jako jeho závislosti třetích stran.</span><span class="sxs-lookup"><span data-stu-id="14e5b-156">A framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="14e5b-157">Pokud například knihovna jiného výrobce podporuje jenom macOS, aplikace není přenosná do systémů Windows.</span><span class="sxs-lookup"><span data-stu-id="14e5b-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="14e5b-158">K tomu dochází, pokud závislost jiného výrobce sama o sobě závisí na nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="14e5b-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="14e5b-159">Dobrým příkladem je [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), který vyžaduje nativní závislost na [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="14e5b-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="14e5b-160">Při vytvoření FDD pro aplikaci s tímto druhem závislosti třetí strany, publikovaný výstup obsahuje složku pro každý [identifikátor runtime (RID),](../rid-catalog.md) který podporuje nativní závislost (a která existuje v jeho balíčku NuGet).</span><span class="sxs-lookup"><span data-stu-id="14e5b-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a><span data-ttu-id="14e5b-161">Samostatné nasazení bez závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="14e5b-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="14e5b-162">Nasazení samostatného nasazení bez závislostí třetích stran zahrnuje vytvoření projektu, úpravu souboru *csproj,* sestavení, testování a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="14e5b-163">Jednoduchý příklad napsaný v C# ilustruje proces.</span><span class="sxs-lookup"><span data-stu-id="14e5b-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="14e5b-164">Začnete vytvořením, kódováním a testováním projektu stejně jako nasazení závislé na rámci:</span><span class="sxs-lookup"><span data-stu-id="14e5b-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="14e5b-165">Vytvořte projekt.</span><span class="sxs-lookup"><span data-stu-id="14e5b-165">Create the project.</span></span>

   <span data-ttu-id="14e5b-166">Vyberte **Soubor** > **nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="14e5b-167">V dialogovém okně **Nový projekt** rozbalte kategorie projektu jazyka (C# nebo Visual Basic) v podokně **Nainstalované** typy projektů, zvolte **.NET Core**a v prostředním podokně vyberte šablonu **Konzola Aplikace (.NET Core).**</span><span class="sxs-lookup"><span data-stu-id="14e5b-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="14e5b-168">Do textového pole **Název** zadejte název projektu, například "SCD", a vyberte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="14e5b-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="14e5b-169">Přidejte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-169">Add the application's source code.</span></span>

   <span data-ttu-id="14e5b-170">Otevřete soubor *Program.cs* nebo *Program.vb* v editoru a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="14e5b-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="14e5b-171">Vyzve uživatele k zadání textu a zobrazí jednotlivá slova zadaná uživatelem.</span><span class="sxs-lookup"><span data-stu-id="14e5b-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="14e5b-172">Používá regulární `\w+` výraz k oddělení slov ve vstupním textu.</span><span class="sxs-lookup"><span data-stu-id="14e5b-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="14e5b-173">Určete, zda chcete použít režim globalizace invariantní.</span><span class="sxs-lookup"><span data-stu-id="14e5b-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="14e5b-174">Zejména v případě, že vaše aplikace cíle Linux, můžete snížit celkovou velikost vašeho nasazení s využitím [globalizace invariantní režim](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="14e5b-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span> <span data-ttu-id="14e5b-175">Režim invariantizace je užitečné pro aplikace, které nejsou globálně vědomi a které můžete použít konvence formátování, konvencí caseing a porovnání řetězců a pořadí řazení [invariantní jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="14e5b-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="14e5b-176">Chcete-li povolit invariantní režim, klepněte pravým tlačítkem myši na projekt (nikoli na řešení) v **Průzkumníku řešení**a vyberte **možnost Upravit Soubor SCD.csproj** nebo **Upravit Soubor SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="14e5b-177">Pak do souboru přidejte následující zvýrazněné řádky:</span><span class="sxs-lookup"><span data-stu-id="14e5b-177">Then add the following highlighted lines to the file:</span></span>

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. <span data-ttu-id="14e5b-178">Vytvořte sestavení ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="14e5b-179">Vyberte **sestavení** > **sestavení řešení**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="14e5b-180">Můžete také zkompilovat a spustit sestavení ladění aplikace výběrem ladění **ladění** > **start**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="14e5b-181">Tento krok ladění umožňuje identifikovat problémy s vaší aplikací, když je spuštěna na hostitelské platformě.</span><span class="sxs-lookup"><span data-stu-id="14e5b-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="14e5b-182">Stále budete muset vyzkoušet na každé z vašich cílových platforem.</span><span class="sxs-lookup"><span data-stu-id="14e5b-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="14e5b-183">Pokud jste povolili globalizace invariantní režim, nezapomeňte zejména otestovat, zda absence dat citlivých na jazykovou verzi je vhodný pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="14e5b-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="14e5b-184">Po dokončení ladění můžete publikovat samostatné nasazení:</span><span class="sxs-lookup"><span data-stu-id="14e5b-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="14e5b-185">Visual Studio 15.6 a starší</span><span class="sxs-lookup"><span data-stu-id="14e5b-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="14e5b-186">Po odladění a testování programu vytvořte soubory, které se mají nasadit s vaší aplikací pro každou platformu, na kterou cílí.</span><span class="sxs-lookup"><span data-stu-id="14e5b-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="14e5b-187">Pokud chcete aplikaci publikovat z Visual Studia, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="14e5b-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="14e5b-188">Definujte platformy, na které bude vaše aplikace cílit.</span><span class="sxs-lookup"><span data-stu-id="14e5b-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="14e5b-189">Klikněte pravým tlačítkem myši na projekt (ne na řešení) v **Průzkumníku řešení** a vyberte **upravit Soubor SCD.csproj**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="14e5b-190">Vytvořte `<RuntimeIdentifiers>` značku `<PropertyGroup>` v části souboru *csproj,* která definuje platformy, na které vaše aplikace cílí, a zadejte identifikátor runtime (RID) každé platformy, na kterou cílíte.</span><span class="sxs-lookup"><span data-stu-id="14e5b-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="14e5b-191">Musíte také přidat středník oddělit RIDs.</span><span class="sxs-lookup"><span data-stu-id="14e5b-191">You also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="14e5b-192">Seznam identifikátorů modulu [runtime IDentifier](../rid-catalog.md) naleznete v části Katalog runtime iDentifier.</span><span class="sxs-lookup"><span data-stu-id="14e5b-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="14e5b-193">Například následující příklad označuje, že aplikace běží na 64bitových operačních systémech Windows 10 a 64bitovém operačním systému OS X verze 10.11.</span><span class="sxs-lookup"><span data-stu-id="14e5b-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="14e5b-194">Prvek `<RuntimeIdentifiers>` může jít `<PropertyGroup>` do jakéhokoli, které máte ve vašem *souboru csproj.*</span><span class="sxs-lookup"><span data-stu-id="14e5b-194">The `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="14e5b-195">Kompletní ukázkový *soubor csproj* se zobrazí dále v této části.</span><span class="sxs-lookup"><span data-stu-id="14e5b-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="14e5b-196">Publikujte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="14e5b-196">Publish your app.</span></span>

   <span data-ttu-id="14e5b-197">Po odladění a testování programu vytvořte soubory, které se mají nasadit s vaší aplikací pro každou platformu, na kterou cílí.</span><span class="sxs-lookup"><span data-stu-id="14e5b-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="14e5b-198">Pokud chcete aplikaci publikovat z Visual Studia, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="14e5b-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="14e5b-199">Změňte konfiguraci řešení z **Ladění** na **uvolnění** na panelu nástrojů a vytvořte verzi aplikace release (namísto ladění).</span><span class="sxs-lookup"><span data-stu-id="14e5b-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="14e5b-200">Klikněte pravým tlačítkem myši na projekt (ne na řešení) v **Průzkumníku řešení** a vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="14e5b-201">Na kartě **Publikovat** vyberte **Publikovat**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="14e5b-202">Visual Studio zapisuje soubory, které tvoří vaši aplikaci do místního systému souborů.</span><span class="sxs-lookup"><span data-stu-id="14e5b-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="14e5b-203">Na kartě **Publikovat** se nyní zobrazuje jeden profil **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="14e5b-204">Nastavení konfigurace profilu jsou zobrazeny v části **Souhrn** na **Target Location** kartě. **Target Runtime**</span><span class="sxs-lookup"><span data-stu-id="14e5b-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="14e5b-205">Visual Studio ve výchozím nastavení zapíše všechny publikované soubory do jednoho adresáře.</span><span class="sxs-lookup"><span data-stu-id="14e5b-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="14e5b-206">Pro větší pohodlí je nejlepší vytvořit samostatné profily pro každý cílový běh a umístit publikované soubory do adresáře specifického pro platformu.</span><span class="sxs-lookup"><span data-stu-id="14e5b-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="14e5b-207">To zahrnuje vytvoření samostatného profilu publikování pro každou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="14e5b-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="14e5b-208">Takže nyní znovu aplikaci pro každou platformu tímto způsobem postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="14e5b-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="14e5b-209">V dialogovém okně **Publikovat** vyberte **Vytvořit nový profil.**</span><span class="sxs-lookup"><span data-stu-id="14e5b-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="14e5b-210">V **dialogovém** okně Vybrat cíl publikování změňte možnost Vybrat umístění **složky** do *přihrádky\Release\PublishOutput\win10-x64*.</span><span class="sxs-lookup"><span data-stu-id="14e5b-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="14e5b-211">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-211">Select **OK**.</span></span>

         1. <span data-ttu-id="14e5b-212">Vyberte nový profil **(FolderProfile1**) v seznamu profilů a ujistěte se, že **cílový runtime** je `win10-x64`.</span><span class="sxs-lookup"><span data-stu-id="14e5b-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="14e5b-213">Pokud tomu tak není, vyberte **Nastavení**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="14e5b-214">V dialogovém okně **Nastavení profilu** změňte **cílovou dobu běhu** na `win10-x64` položku **Uložit**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="14e5b-215">V opačném případě vyberte **zrušit**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="14e5b-216">Vyberte **Publikovat,** abyste publikovali aplikaci pro 64bitové platformy Windows 10.</span><span class="sxs-lookup"><span data-stu-id="14e5b-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="14e5b-217">Chcete-li vytvořit profil pro platformu, postupujte znovu podle předchozích `osx.10.11-x64` kroků.</span><span class="sxs-lookup"><span data-stu-id="14e5b-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="14e5b-218">**Cílové umístění** je *bin\Release\PublishOutput\osx.10.11-x64*a cílový `osx.10.11-x64`běh **runtime** je .</span><span class="sxs-lookup"><span data-stu-id="14e5b-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="14e5b-219">Název, který Visual Studio přiřadí tomuto profilu, je **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="14e5b-220">Každé cílové umístění obsahuje úplnou sadu souborů (soubory aplikace i všechny soubory .NET Core), které jsou potřeba ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-220">Each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="14e5b-221">Spolu se soubory vaší aplikace vydává proces publikování soubor databáze programů (.pdb), který obsahuje informace o ladění o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="14e5b-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="14e5b-222">Soubor je užitečný především pro ladění výjimek.</span><span class="sxs-lookup"><span data-stu-id="14e5b-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="14e5b-223">Můžete se rozhodnout, že ji nezabalíte se soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="14e5b-224">Měli byste ji však uložit v případě, že chcete ladit sestavení verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="14e5b-225">Nasadit publikované soubory jakýmkoli způsobem se vám líbí.</span><span class="sxs-lookup"><span data-stu-id="14e5b-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="14e5b-226">Můžete je například zabalit do souboru `copy` ZIP, použít jednoduchý příkaz nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="14e5b-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="14e5b-227">Následuje kompletní *csproj* soubor pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="14e5b-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="14e5b-228">Visual Studio 15.7 a novější</span><span class="sxs-lookup"><span data-stu-id="14e5b-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="14e5b-229">Po odladění a testování programu vytvořte soubory, které se mají nasadit s vaší aplikací pro každou platformu, na kterou cílí.</span><span class="sxs-lookup"><span data-stu-id="14e5b-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="14e5b-230">To zahrnuje vytvoření samostatného profilu pro každou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="14e5b-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="14e5b-231">Pro každou platformu, na kterou vaše aplikace cílí, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="14e5b-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="14e5b-232">Vytvořte profil pro cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="14e5b-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="14e5b-233">Pokud se jedná o první profil, který jste vytvořili, klikněte pravým tlačítkem myši na projekt (ne na řešení) v **Průzkumníku řešení** a vyberte **Publikovat**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="14e5b-234">Pokud jste profil už vytvořili, klikněte pravým tlačítkem myši na projekt a otevřete dialogové okno **Publikovat,** pokud ještě není otevřený.</span><span class="sxs-lookup"><span data-stu-id="14e5b-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="14e5b-235">Pak vyberte **Nový profil**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="14e5b-236">Otevře se dialogové okno **Vybrat cíl publikování.**</span><span class="sxs-lookup"><span data-stu-id="14e5b-236">The **Pick a Publish Target** dialog box opens.</span></span>

1. <span data-ttu-id="14e5b-237">Vyberte umístění, kde Visual Studio publikuje vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="14e5b-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="14e5b-238">Pokud publikujete jenom na jedné platformě, můžete přijmout výchozí hodnotu v textovém poli **Zvolit složku.** To publikuje nasazení aplikace závislé na rámci do \* \<adresáře>\bin\Release\netcoreapp2.1\publish.\*</span><span class="sxs-lookup"><span data-stu-id="14e5b-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish* directory.</span></span>

   <span data-ttu-id="14e5b-239">Pokud publikujete na více než jedné platformě, připojujte řetězec, který identifikuje cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="14e5b-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="14e5b-240">Pokud například připojíte řetězec "linux" k cestě k souboru, aplikace Visual Studio publikuje nasazení aplikace závislé na rámci do \* \<adresáře projektu>\bin\Release\netcoreapp2.1\publish\linux.\*</span><span class="sxs-lookup"><span data-stu-id="14e5b-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="14e5b-241">Profil vytvořte tak, že vedle tlačítka **Publikovat** vyberete ikonu rozevíracího seznamu a vyberete **Vytvořit profil**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="14e5b-242">Pak vyberte tlačítko **Vytvořit profil** a vytvořte profil.</span><span class="sxs-lookup"><span data-stu-id="14e5b-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="14e5b-243">Označte, že publikujete samostatné nasazení a definujte platformu, na kterou bude vaše aplikace cílit.</span><span class="sxs-lookup"><span data-stu-id="14e5b-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="14e5b-244">V dialogovém okně **Publikovat** vyberte odkaz **Konfigurovat** a otevřete dialogové okno **Nastavení profilu.**</span><span class="sxs-lookup"><span data-stu-id="14e5b-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="14e5b-245">V seznamu **Režim nasazení** vyberte **Samostatný.**</span><span class="sxs-lookup"><span data-stu-id="14e5b-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="14e5b-246">V seznamu **Cílový běh ový čas** vyberte jednu z platforem, na které vaše aplikace cílí.</span><span class="sxs-lookup"><span data-stu-id="14e5b-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="14e5b-247">Vyberte **Uložit,** chcete-li přijmout změny a zavřít dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="14e5b-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="14e5b-248">Pojmenujte svůj profil.</span><span class="sxs-lookup"><span data-stu-id="14e5b-248">Name your profile.</span></span>

   1. <span data-ttu-id="14e5b-249">Vyberte **Akce** > **Přejmenovat profil,** abyste svůj profil pojmenovali.</span><span class="sxs-lookup"><span data-stu-id="14e5b-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="14e5b-250">Přiřaďte svému profilu název, který identifikuje cílovou platformu, a pak vyberte \**Uložit*.</span><span class="sxs-lookup"><span data-stu-id="14e5b-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="14e5b-251">Opakujte tyto kroky a definujte všechny další cílové platformy, na které vaše aplikace cílí.</span><span class="sxs-lookup"><span data-stu-id="14e5b-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="14e5b-252">Nakonfigurovali jste profily a jste připraveni publikovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="14e5b-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="14e5b-253">Použijte následující postup:</span><span class="sxs-lookup"><span data-stu-id="14e5b-253">To do this:</span></span>

   1. <span data-ttu-id="14e5b-254">Pokud okno **Publikovat** není aktuálně otevřené, klikněte pravým tlačítkem myši na projekt (ne na řešení) v **Průzkumníku řešení** a vyberte **Publikovat**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="14e5b-255">Vyberte profil, který chcete publikovat, a pak vyberte **Publikovat**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="14e5b-256">Proveďte to pro každý profil, který má být publikován.</span><span class="sxs-lookup"><span data-stu-id="14e5b-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="14e5b-257">Každé cílové umístění (v případě našeho příkladu bin\release\netcoreapp2.1\publish\\*profile-name* obsahuje úplnou sadu souborů (soubory aplikace i všechny soubory .NET Core) potřebné ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-257">Each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="14e5b-258">Spolu se soubory vaší aplikace vydává proces publikování soubor databáze programů (.pdb), který obsahuje informace o ladění o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="14e5b-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="14e5b-259">Soubor je užitečný především pro ladění výjimek.</span><span class="sxs-lookup"><span data-stu-id="14e5b-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="14e5b-260">Můžete se rozhodnout, že ji nezabalíte se soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="14e5b-261">Měli byste ji však uložit v případě, že chcete ladit sestavení verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="14e5b-262">Nasadit publikované soubory jakýmkoli způsobem se vám líbí.</span><span class="sxs-lookup"><span data-stu-id="14e5b-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="14e5b-263">Můžete je například zabalit do souboru `copy` ZIP, použít jednoduchý příkaz nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="14e5b-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="14e5b-264">Následuje kompletní *csproj* soubor pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="14e5b-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="14e5b-265">Kromě toho Visual Studio vytvoří samostatný\*profil publikování ( .pubxml) pro každou platformu, na kterou cílíte.</span><span class="sxs-lookup"><span data-stu-id="14e5b-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="14e5b-266">Například soubor pro náš linuxový profil (linux.pubxml) se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="14e5b-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

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

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="14e5b-267">Samostatné nasazení se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="14e5b-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="14e5b-268">Nasazení samostatného nasazení s jednou nebo více závislostmi třetích stran zahrnuje přidání závislostí.</span><span class="sxs-lookup"><span data-stu-id="14e5b-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="14e5b-269">Před vytvořením aplikace jsou vyžadovány následující další kroky:</span><span class="sxs-lookup"><span data-stu-id="14e5b-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="14e5b-270">Pomocí **Správce balíčků NuGet** přidat odkaz na balíček NuGet do projektu; a pokud balíček ještě není ve vašem systému k dispozici, nainstalujte jej.</span><span class="sxs-lookup"><span data-stu-id="14e5b-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="14e5b-271">Chcete-li otevřít správce balíčků, vyberte **nástroje, které** > **spravují správce** > balíčků**NuGet, pro řešení**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="14e5b-272">Zkontrolujte, zda jsou v systému `Newtonsoft.Json`nainstalovány vaše závislosti třetích stran (například) a pokud nejsou, nainstalujte je.</span><span class="sxs-lookup"><span data-stu-id="14e5b-272">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="14e5b-273">Na kartě **Nainstalováno** jsou uvedeny balíčky NuGet nainstalované v systému.</span><span class="sxs-lookup"><span data-stu-id="14e5b-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="14e5b-274">Pokud `Newtonsoft.Json` zde není uvedena, vyberte kartu **Procházet** a do vyhledávacího pole zadejte "Newtonsoft.Json".</span><span class="sxs-lookup"><span data-stu-id="14e5b-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="14e5b-275">Vyberte `Newtonsoft.Json` a v pravém podokně vyberte projekt před výběrem **možnosti Instalovat**.</span><span class="sxs-lookup"><span data-stu-id="14e5b-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="14e5b-276">Pokud `Newtonsoft.Json` je již v systému nainstalován, přidejte jej do projektu výběrem projektu v pravém podokně na kartě **Spravovat balíčky pro řešení.**</span><span class="sxs-lookup"><span data-stu-id="14e5b-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="14e5b-277">Následuje kompletní *csproj* soubor pro tento projekt:</span><span class="sxs-lookup"><span data-stu-id="14e5b-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="14e5b-278">Visual Studio 15.6 a starší</span><span class="sxs-lookup"><span data-stu-id="14e5b-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

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

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="14e5b-279">Visual Studio 15.7 a novější</span><span class="sxs-lookup"><span data-stu-id="14e5b-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

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

<span data-ttu-id="14e5b-280">Při nasazení aplikace jsou všechny závislosti třetích stran používané ve vaší aplikaci také obsaženy se soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="14e5b-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="14e5b-281">Knihovny třetích stran nejsou vyžadovány v systému, ve kterém je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="14e5b-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="14e5b-282">Samostatné nasazení můžete nasadit pouze s knihovnou třetí strany na platformy podporované tou knihovnou.</span><span class="sxs-lookup"><span data-stu-id="14e5b-282">You can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="14e5b-283">To je podobné s závislostí třetích stran s nativní závislosti v nasazení závislé na rámci, kde nativní závislosti nebude existovat na cílové platformě, pokud byly dříve nainstalovány tam.</span><span class="sxs-lookup"><span data-stu-id="14e5b-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="14e5b-284">Viz také</span><span class="sxs-lookup"><span data-stu-id="14e5b-284">See also</span></span>

- [<span data-ttu-id="14e5b-285">Nasazení základní aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="14e5b-285">.NET Core Application Deployment</span></span>](index.md)
- [<span data-ttu-id="14e5b-286">Katalog IDentifier (RID) modulu .NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="14e5b-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
