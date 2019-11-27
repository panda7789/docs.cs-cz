---
title: Nasazení aplikací .NET Core pomocí sady Visual Studio
description: Naučte se nasadit aplikaci .NET Core pomocí sady Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f80b483fedc600a1e1a48d36ce9b7b95c6de9f27
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428893"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a><span data-ttu-id="315d0-103">Nasazení aplikací .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="315d0-103">Deploy .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="315d0-104">Můžete nasadit aplikaci .NET Core buď jako *nasazení závislé na rozhraní*, které zahrnuje binární soubory aplikace, ale závisí na přítomnosti .NET Core v cílovém systému nebo jako *samostatné nasazení*, které zahrnuje jak vaše aplikace, tak binární soubory .NET Core.</span><span class="sxs-lookup"><span data-stu-id="315d0-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="315d0-105">Přehled nasazení aplikace .NET Core najdete v tématu [nasazení aplikace .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="315d0-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="315d0-106">Následující části ukazují, jak pomocí Microsoft Visual Studio vytvořit následující typy nasazení:</span><span class="sxs-lookup"><span data-stu-id="315d0-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="315d0-107">Nasazení závisí na architektuře</span><span class="sxs-lookup"><span data-stu-id="315d0-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="315d0-108">Nasazení závislé na rozhraní se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="315d0-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="315d0-109">Samostatná nasazení</span><span class="sxs-lookup"><span data-stu-id="315d0-109">Self-contained deployment</span></span>
- <span data-ttu-id="315d0-110">Samostatné nasazení s závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="315d0-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="315d0-111">Informace o použití sady Visual Studio pro vývoj aplikací .NET Core najdete v tématu [závislosti a požadavky .NET Core](../install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="315d0-111">For information on using Visual Studio to develop .NET Core applications, see [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="315d0-112">Nasazení závisí na architektuře</span><span class="sxs-lookup"><span data-stu-id="315d0-112">Framework-dependent deployment</span></span>

<span data-ttu-id="315d0-113">Nasazení závislé na rozhraní bez závislostí třetí strany zahrnuje sestavování, testování a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="315d0-114">Jednoduchý příklad napsaný v C# tomto příkladu znázorňuje proces.</span><span class="sxs-lookup"><span data-stu-id="315d0-114">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="315d0-115">Vytvořte projekt.</span><span class="sxs-lookup"><span data-stu-id="315d0-115">Create the project.</span></span>

   <span data-ttu-id="315d0-116">Vyberte **soubor** > **Nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="315d0-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="315d0-117">V dialogovém okně **Nový projekt** rozbalte v podokně **nainstalované** typy projektůC# kategorii projektu (nebo Visual Basic) vašeho jazyka, zvolte možnost **.NET Core**a potom v prostředním podokně vyberte šablonu **Konzolová aplikace (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="315d0-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="315d0-118">Do textového pole **název** zadejte název projektu, například "FDD".</span><span class="sxs-lookup"><span data-stu-id="315d0-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="315d0-119">Klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="315d0-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="315d0-120">Přidejte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-120">Add the application's source code.</span></span>

   <span data-ttu-id="315d0-121">V editoru otevřete soubor *program.cs* nebo *program. vb* a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="315d0-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="315d0-122">Vyzve uživatele, aby zadal text a zobrazil jednotlivá slova zadaná uživatelem.</span><span class="sxs-lookup"><span data-stu-id="315d0-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="315d0-123">Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.</span><span class="sxs-lookup"><span data-stu-id="315d0-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="315d0-124">Vytvořte ladicí sestavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="315d0-125">Vyberte **sestavení** **řešení**Build > .</span><span class="sxs-lookup"><span data-stu-id="315d0-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="315d0-126">Můžete také zkompilovat a **Spustit ladicí sestavení** vaší aplikace, a to tak, že vyberete ladění > **Spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="315d0-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="315d0-127">Nasaďte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="315d0-127">Deploy your app.</span></span>

   <span data-ttu-id="315d0-128">Po ladění a otestování programu vytvořte soubory, které mají být nasazeny s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="315d0-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="315d0-129">Chcete-li publikovat ze sady Visual Studio, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="315d0-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="315d0-130">Změňte konfiguraci řešení z **Debug** na **release** na panelu nástrojů a sestavte verzi (nikoli ladění) vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="315d0-131">V **Průzkumník řešení** klikněte pravým tlačítkem na projekt (ne řešení) a vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="315d0-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="315d0-132">Na kartě **publikovat** vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="315d0-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="315d0-133">Visual Studio zapisuje soubory, které tvoří vaši aplikaci, do místního systému souborů.</span><span class="sxs-lookup"><span data-stu-id="315d0-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="315d0-134">Na kartě **publikovat** se teď zobrazí jeden profil, **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="315d0-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="315d0-135">Nastavení konfigurace profilu se zobrazí v části **Souhrn** na kartě.</span><span class="sxs-lookup"><span data-stu-id="315d0-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="315d0-136">Výsledné soubory jsou umístěny v adresáři s názvem `Publish` v systému Windows a `publish` v systémech UNIX, které jsou v podadresáři podadresáře projektu *.\bin\release\netcoreapp2.1* .</span><span class="sxs-lookup"><span data-stu-id="315d0-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="315d0-137">Spolu se soubory vaší aplikace proces publikování generuje soubor databáze programu (PDB), který obsahuje informace o ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="315d0-138">Soubor je vhodný hlavně pro ladění výjimek.</span><span class="sxs-lookup"><span data-stu-id="315d0-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="315d0-139">Můžete se rozhodnout, že ho nechcete zabalit do souborů vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="315d0-140">Měli byste ji však uložit v případě, že chcete ladit sestavení pro vydání aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="315d0-141">Nasaďte kompletní sadu souborů aplikace jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="315d0-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="315d0-142">Můžete je například zabalit do souboru zip, použít jednoduchý příkaz `copy`, nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="315d0-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="315d0-143">Po instalaci pak uživatelé můžou aplikaci spustit pomocí příkazu `dotnet` a zadáním názvu souboru aplikace, jako je například `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="315d0-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="315d0-144">Kromě binárních souborů aplikace by měl instalační program také buď seskupit rozhraní Shared Framework Installer, nebo ověřit, že je součástí instalace aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="315d0-145">Instalace sdíleného rozhraní vyžaduje přístup správce nebo root, protože se jedná o počítač v rámci počítače.</span><span class="sxs-lookup"><span data-stu-id="315d0-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="315d0-146">Nasazení závislé na rozhraní se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="315d0-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="315d0-147">Nasazení rozhraní závislého na rozhraní s jednou nebo více závislostmi třetí strany vyžaduje, aby byly všechny závislosti k dispozici pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="315d0-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="315d0-148">Předtím, než budete moci sestavit aplikaci, jsou vyžadovány tyto další kroky:</span><span class="sxs-lookup"><span data-stu-id="315d0-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="315d0-149">Pomocí **Správce balíčků NuGet** přidejte do svého projektu odkaz na balíček NuGet; a pokud balíček ještě není ve vašem systému k dispozici, nainstalujte ho.</span><span class="sxs-lookup"><span data-stu-id="315d0-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="315d0-150">Správce balíčků otevřete tak, že vyberete **nástroje** > **správce balíčků NuGet** > **Spravovat balíčky NuGet pro řešení**.</span><span class="sxs-lookup"><span data-stu-id="315d0-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="315d0-151">Ověřte, zda jsou v systému nainstalovány závislosti jiných výrobců (například `Newtonsoft.Json`), a pokud nejsou, nainstalujte je.</span><span class="sxs-lookup"><span data-stu-id="315d0-151">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="315d0-152">Karta **Installed (instalovat** ) obsahuje seznam balíčků NuGet nainstalovaných ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="315d0-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="315d0-153">Pokud zde `Newtonsoft.Json` není uveden, vyberte kartu **Procházet** a do vyhledávacího pole zadejte "Newtonsoft. JSON".</span><span class="sxs-lookup"><span data-stu-id="315d0-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="315d0-154">Vyberte `Newtonsoft.Json` a v pravém podokně vyberte svůj projekt před výběrem možnosti **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="315d0-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="315d0-155">Pokud je v systému už `Newtonsoft.Json` nainstalovaná, přidejte ho do svého projektu tak, že ho vyberete v pravém podokně na kartě **Spravovat balíčky pro řešení** .</span><span class="sxs-lookup"><span data-stu-id="315d0-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="315d0-156">Všimněte si, že nasazení závislé na rozhraní se závislostmi třetích stran je pouze přenosné jako své závislosti třetích stran.</span><span class="sxs-lookup"><span data-stu-id="315d0-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="315d0-157">Pokud například knihovna třetí strany podporuje jenom macOS, aplikace není přenosná na systémy Windows.</span><span class="sxs-lookup"><span data-stu-id="315d0-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="315d0-158">K tomu dojde v případě, že závislost třetí strany závisí na nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="315d0-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="315d0-159">Dobrým příkladem je [Kestrel Server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), který vyžaduje nativní závislost na [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="315d0-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="315d0-160">Pokud je vytvořen FDD pro aplikaci s tímto druhem závislosti třetí strany, publikovaný výstup obsahuje složku pro každý [identifikátor modulu runtime (RID)](../rid-catalog.md) , který nativní závislost podporuje (a který existuje v jeho balíčku NuGet).</span><span class="sxs-lookup"><span data-stu-id="315d0-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a><span data-ttu-id="315d0-161">Samostatné nasazení bez závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="315d0-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="315d0-162">Nasazení samostatného nasazení bez závislostí třetích stran zahrnuje vytvoření projektu, úpravu souboru *csproj* , sestavování, testování a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="315d0-163">Jednoduchý příklad napsaný v C# tomto příkladu znázorňuje proces.</span><span class="sxs-lookup"><span data-stu-id="315d0-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="315d0-164">Začněte tím, že vytvoříte, zakódujete a otestujete projekt stejně jako nasazení závislé na rozhraní:</span><span class="sxs-lookup"><span data-stu-id="315d0-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="315d0-165">Vytvořte projekt.</span><span class="sxs-lookup"><span data-stu-id="315d0-165">Create the project.</span></span>

   <span data-ttu-id="315d0-166">Vyberte **soubor** > **Nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="315d0-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="315d0-167">V dialogovém okně **Nový projekt** rozbalte v podokně **nainstalované** typy projektůC# kategorii projektu (nebo Visual Basic) vašeho jazyka, zvolte možnost **.NET Core**a potom v prostředním podokně vyberte šablonu **Konzolová aplikace (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="315d0-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="315d0-168">Do textového pole **název** zadejte název projektu, například "SCD", a klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="315d0-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="315d0-169">Přidejte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-169">Add the application's source code.</span></span>

   <span data-ttu-id="315d0-170">V editoru otevřete soubor *program.cs* nebo *program. vb* a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="315d0-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="315d0-171">Vyzve uživatele, aby zadal text a zobrazil jednotlivá slova zadaná uživatelem.</span><span class="sxs-lookup"><span data-stu-id="315d0-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="315d0-172">Používá regulární výraz `\w+` k oddělení slov ve vstupním textu.</span><span class="sxs-lookup"><span data-stu-id="315d0-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="315d0-173">Určete, zda chcete použít invariantní režim globalizace.</span><span class="sxs-lookup"><span data-stu-id="315d0-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="315d0-174">Zejména v případě, že je vaše aplikace cílena na Linux, můžete snížit celkovou velikost svého nasazení využitím [režimu invariantování globalizace](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="315d0-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="315d0-175">Režim invariantní globalizace je vhodný pro aplikace, které nejsou globálně závislé a které mohou použít konvence formátování, konvence velikosti písmen a pořadí řazení [invariantní jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="315d0-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="315d0-176">Chcete-li povolit režim invariant, klikněte pravým tlačítkem myši na projekt (ne řešení) v **Průzkumník řešení**a vyberte **Upravit SCD. csproj** nebo **upravte SCD. vbproj**.</span><span class="sxs-lookup"><span data-stu-id="315d0-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="315d0-177">Pak přidejte do souboru následující zvýrazněné řádky:</span><span class="sxs-lookup"><span data-stu-id="315d0-177">Then add the following highlighted lines to the file:</span></span>

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. <span data-ttu-id="315d0-178">Vytvořte sestavení pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="315d0-179">Vyberte **sestavení** **řešení**Build > .</span><span class="sxs-lookup"><span data-stu-id="315d0-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="315d0-180">Můžete také zkompilovat a **Spustit ladicí sestavení** vaší aplikace, a to tak, že vyberete ladění > **Spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="315d0-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="315d0-181">Tento krok ladění vám umožní identifikovat problémy s vaší aplikací, když běží na hostitelské platformě.</span><span class="sxs-lookup"><span data-stu-id="315d0-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="315d0-182">Pořád ho budete muset otestovat na každé cílové platformě.</span><span class="sxs-lookup"><span data-stu-id="315d0-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="315d0-183">Pokud jste povolili režim invariantní globalizace, měli byste se zejména ujistit, zda neexistují data citlivá na jazykovou verzi vhodná pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="315d0-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="315d0-184">Po dokončení ladění můžete publikovat samostatně zahrnuté nasazení:</span><span class="sxs-lookup"><span data-stu-id="315d0-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="315d0-185">Visual Studio 15,6 a starší</span><span class="sxs-lookup"><span data-stu-id="315d0-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="315d0-186">Po ladění a otestování programu vytvořte soubory, které mají být nasazeny s vaší aplikací pro každou platformu, na kterou cílíte.</span><span class="sxs-lookup"><span data-stu-id="315d0-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="315d0-187">Pokud chcete svou aplikaci publikovat ze sady Visual Studio, udělejte toto:</span><span class="sxs-lookup"><span data-stu-id="315d0-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="315d0-188">Definujte platformy, na které bude vaše aplikace cílit.</span><span class="sxs-lookup"><span data-stu-id="315d0-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="315d0-189">V **Průzkumník řešení** klikněte pravým tlačítkem na projekt (ne řešení) a vyberte **Upravit SCD. csproj**.</span><span class="sxs-lookup"><span data-stu-id="315d0-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="315d0-190">Vytvořte značku `<RuntimeIdentifiers>` v oddílu `<PropertyGroup>` souboru *csproj* , který definuje platformy, na které vaše aplikace cílí, a určete identifikátor modulu runtime (RID) pro každou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="315d0-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="315d0-191">Všimněte si, že je také nutné přidat středník pro oddělení identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="315d0-191">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="315d0-192">Seznam identifikátorů modulu runtime najdete v tématu [katalog identifikátorů modulu runtime](../rid-catalog.md) .</span><span class="sxs-lookup"><span data-stu-id="315d0-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="315d0-193">Například následující příklad označuje, že aplikace běží na 64 operačních systémech Windows 10 a 64 operačním systému OS X verze 10,11.</span><span class="sxs-lookup"><span data-stu-id="315d0-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="315d0-194">Všimněte si, že `<RuntimeIdentifiers>` element může přejít do jakékoli `<PropertyGroup>`, kterou máte v souboru *csproj* .</span><span class="sxs-lookup"><span data-stu-id="315d0-194">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="315d0-195">V této části se zobrazí kompletní vzorový soubor *csproj* .</span><span class="sxs-lookup"><span data-stu-id="315d0-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="315d0-196">Publikujte svoji aplikaci.</span><span class="sxs-lookup"><span data-stu-id="315d0-196">Publish your app.</span></span>

   <span data-ttu-id="315d0-197">Po ladění a otestování programu vytvořte soubory, které mají být nasazeny s vaší aplikací pro každou platformu, na kterou cílíte.</span><span class="sxs-lookup"><span data-stu-id="315d0-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="315d0-198">Pokud chcete svou aplikaci publikovat ze sady Visual Studio, udělejte toto:</span><span class="sxs-lookup"><span data-stu-id="315d0-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="315d0-199">Změňte konfiguraci řešení z **Debug** na **release** na panelu nástrojů a sestavte verzi (nikoli ladění) vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="315d0-200">V **Průzkumník řešení** klikněte pravým tlačítkem na projekt (ne řešení) a vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="315d0-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="315d0-201">Na kartě **publikovat** vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="315d0-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="315d0-202">Visual Studio zapisuje soubory, které tvoří vaši aplikaci, do místního systému souborů.</span><span class="sxs-lookup"><span data-stu-id="315d0-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="315d0-203">Na kartě **publikovat** se teď zobrazí jeden profil, **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="315d0-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="315d0-204">Nastavení konfigurace profilu se zobrazí v části **Souhrn** na kartě. **cílový modul runtime** určuje, který modul runtime byl publikován a **cílové umístění** identifikuje, kde byly zapsány soubory pro nasazení, které jsou samostatně obsaženy.</span><span class="sxs-lookup"><span data-stu-id="315d0-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="315d0-205">Visual Studio ve výchozím nastavení zapisuje všechny publikované soubory do jednoho adresáře.</span><span class="sxs-lookup"><span data-stu-id="315d0-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="315d0-206">Pro usnadnění práce je nejlepší vytvořit samostatné profily pro každý cílový modul runtime a umístit publikované soubory do adresáře specifického pro platformu.</span><span class="sxs-lookup"><span data-stu-id="315d0-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="315d0-207">To zahrnuje vytvoření samostatného profilu publikování pro každou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="315d0-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="315d0-208">Takže teď aplikaci pro každou platformu znovu sestavíte následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="315d0-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="315d0-209">V dialogovém okně **publikovat** vyberte **vytvořit nový profil** .</span><span class="sxs-lookup"><span data-stu-id="315d0-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="315d0-210">V dialogovém okně **vybrat cíl publikování** změňte umístění **složky** na *bin\Release\PublishOutput\win10-x64*.</span><span class="sxs-lookup"><span data-stu-id="315d0-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="315d0-211">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="315d0-211">Select **OK**.</span></span>

         1. <span data-ttu-id="315d0-212">V seznamu profilů vyberte nový profil (**FolderProfile1**) a ujistěte se, že je **cílový modul runtime** `win10-x64`.</span><span class="sxs-lookup"><span data-stu-id="315d0-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="315d0-213">Pokud není, vyberte **Nastavení**.</span><span class="sxs-lookup"><span data-stu-id="315d0-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="315d0-214">V dialogovém okně **nastavení profilu** změňte **cílový modul runtime** na `win10-x64` a vyberte **Uložit**.</span><span class="sxs-lookup"><span data-stu-id="315d0-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="315d0-215">V opačném případě vyberte **Zrušit**.</span><span class="sxs-lookup"><span data-stu-id="315d0-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="315d0-216">Vyberte **publikovat** a publikujte svou aplikaci pro 64 platformy Windows 10.</span><span class="sxs-lookup"><span data-stu-id="315d0-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="315d0-217">Pomocí předchozích kroků znovu vytvořte profil pro `osx.10.11-x64` platformu.</span><span class="sxs-lookup"><span data-stu-id="315d0-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="315d0-218">**Cílové umístění** je *Bin\Release\PublishOutput\osx.10.11-x64*a **cílový modul runtime** je `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="315d0-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="315d0-219">Název, který Visual Studio přiřadí k tomuto profilu, je **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="315d0-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="315d0-220">Všimněte si, že každé cílové umístění obsahuje kompletní sadu souborů (jak soubory aplikace, tak všechny soubory .NET Core) potřebné ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-220">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="315d0-221">Spolu se soubory vaší aplikace proces publikování generuje soubor databáze programu (PDB), který obsahuje informace o ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="315d0-222">Soubor je vhodný hlavně pro ladění výjimek.</span><span class="sxs-lookup"><span data-stu-id="315d0-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="315d0-223">Můžete se rozhodnout, že ho nechcete zabalit do souborů vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="315d0-224">Měli byste ji však uložit v případě, že chcete ladit sestavení pro vydání aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="315d0-225">Nasaďte publikované soubory jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="315d0-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="315d0-226">Můžete je například zabalit do souboru zip, použít jednoduchý příkaz `copy`, nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="315d0-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="315d0-227">Následuje úplný soubor *csproj* pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="315d0-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="315d0-228">Visual Studio 15,7 a novější</span><span class="sxs-lookup"><span data-stu-id="315d0-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="315d0-229">Po ladění a otestování programu vytvořte soubory, které mají být nasazeny s vaší aplikací pro každou platformu, na kterou cílíte.</span><span class="sxs-lookup"><span data-stu-id="315d0-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="315d0-230">To zahrnuje vytvoření samostatného profilu pro každou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="315d0-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="315d0-231">Pro každou platformu, na kterou vaše aplikace cílí, udělejte toto:</span><span class="sxs-lookup"><span data-stu-id="315d0-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="315d0-232">Vytvořte profil pro cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="315d0-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="315d0-233">Pokud se jedná o první profil, který jste vytvořili, klikněte pravým tlačítkem na projekt (ne řešení) v **Průzkumník řešení** a vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="315d0-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="315d0-234">Pokud jste už profil vytvořili, klikněte pravým tlačítkem na projekt a otevřete dialog **publikovat** , pokud už není otevřený.</span><span class="sxs-lookup"><span data-stu-id="315d0-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="315d0-235">Pak vyberte **Nový profil**.</span><span class="sxs-lookup"><span data-stu-id="315d0-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="315d0-236">Otevře se dialogové okno **vybrat cíl publikování** .</span><span class="sxs-lookup"><span data-stu-id="315d0-236">The **Pick a Publish Target** dialog box opens.</span></span>
  
1. <span data-ttu-id="315d0-237">Vyberte umístění, kde aplikace Visual Studio publikuje vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="315d0-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="315d0-238">Pokud publikujete pouze na jednu platformu, můžete přijmout výchozí hodnotu v textovém poli **Zvolit složku** ; Tím se publikuje nasazení aplikace závislé na rozhraní do adresáře *\<projekt-adresář > \bin\Release\netcoreapp2.1\publish* .</span><span class="sxs-lookup"><span data-stu-id="315d0-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish* directory.</span></span>

   <span data-ttu-id="315d0-239">Pokud publikujete na více než jednu platformu, přidejte řetězec, který identifikuje cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="315d0-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="315d0-240">Například pokud připojíte řetězec "Linux" do cesty k souboru, aplikace Visual Studio publikuje nasazení závislého rozhraní aplikace do adresáře *\<projekt-adresář > \bin\Release\netcoreapp2.1\publish\linux* .</span><span class="sxs-lookup"><span data-stu-id="315d0-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="315d0-241">Vytvořte profil tak, že vyberete ikonu rozevíracího seznamu vedle tlačítka **publikovat** a vyberete **vytvořit profil**.</span><span class="sxs-lookup"><span data-stu-id="315d0-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="315d0-242">Pak vyberte tlačítko **vytvořit profil** a vytvořte profil.</span><span class="sxs-lookup"><span data-stu-id="315d0-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="315d0-243">Uveďte, že publikujete samostatné nasazení a definujete platformu, na kterou bude vaše aplikace cílit.</span><span class="sxs-lookup"><span data-stu-id="315d0-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="315d0-244">V dialogovém okně **publikovat** vyberte odkaz **Konfigurovat** a otevřete dialogové okno **nastavení profilu** .</span><span class="sxs-lookup"><span data-stu-id="315d0-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="315d0-245">V seznamu **režim nasazení** vyberte možnost **samostatné – obsaženo** .</span><span class="sxs-lookup"><span data-stu-id="315d0-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="315d0-246">V rozevíracím seznamu **cílový modul runtime** vyberte jednu z platforem, na kterou vaše aplikace cílí.</span><span class="sxs-lookup"><span data-stu-id="315d0-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="315d0-247">Vyberte **Uložit** a potvrďte provedené změny a zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="315d0-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="315d0-248">Pojmenujte profil.</span><span class="sxs-lookup"><span data-stu-id="315d0-248">Name your profile.</span></span>

   1. <span data-ttu-id="315d0-249">Vyberte **akce** > **Přejmenovat profil** pro pojmenování profilu.</span><span class="sxs-lookup"><span data-stu-id="315d0-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="315d0-250">Přiřaďte profilu název, který identifikuje cílovou platformu, a pak vyberte \**Uložit*.</span><span class="sxs-lookup"><span data-stu-id="315d0-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="315d0-251">Zopakováním těchto kroků definujte všechny další cílové platformy, na které vaše aplikace cílí.</span><span class="sxs-lookup"><span data-stu-id="315d0-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="315d0-252">Nakonfigurovali jste profily a teď jste připraveni publikovat svou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="315d0-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="315d0-253">Použijte následující postup:</span><span class="sxs-lookup"><span data-stu-id="315d0-253">To do this:</span></span>

   1. <span data-ttu-id="315d0-254">Pokud okno **publikovat** není momentálně otevřené, klikněte pravým tlačítkem myši na projekt (ne řešení) v **Průzkumník řešení** a vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="315d0-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="315d0-255">Vyberte profil, který chcete publikovat, a pak vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="315d0-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="315d0-256">Udělejte to pro každý profil, který se má publikovat.</span><span class="sxs-lookup"><span data-stu-id="315d0-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="315d0-257">Všimněte si, že každé cílové umístění (v případě našeho příkladu bin\release\netcoreapp2.1\publish\\*Profile-název* obsahuje úplnou sadu souborů (jak soubory aplikace, tak všechny soubory .NET Core) potřebné ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-257">Note that each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="315d0-258">Spolu se soubory vaší aplikace proces publikování generuje soubor databáze programu (PDB), který obsahuje informace o ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="315d0-259">Soubor je vhodný hlavně pro ladění výjimek.</span><span class="sxs-lookup"><span data-stu-id="315d0-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="315d0-260">Můžete se rozhodnout, že ho nechcete zabalit do souborů vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="315d0-261">Měli byste ji však uložit v případě, že chcete ladit sestavení pro vydání aplikace.</span><span class="sxs-lookup"><span data-stu-id="315d0-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="315d0-262">Nasaďte publikované soubory jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="315d0-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="315d0-263">Můžete je například zabalit do souboru zip, použít jednoduchý příkaz `copy`, nebo je nasadit s libovolným instalačním balíčkem podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="315d0-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="315d0-264">Následuje úplný soubor *csproj* pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="315d0-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="315d0-265">Kromě toho Visual Studio vytvoří samostatný profil publikování (\*. pubxml) pro každou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="315d0-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="315d0-266">Například soubor pro náš profil Linux (Linux. pubxml) se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="315d0-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

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

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="315d0-267">Samostatné nasazení s závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="315d0-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="315d0-268">Nasazení samostatně uzavřeného nasazení s jednou nebo více závislostmi třetích stran zahrnuje přidání závislostí.</span><span class="sxs-lookup"><span data-stu-id="315d0-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="315d0-269">Předtím, než budete moci sestavit aplikaci, jsou vyžadovány tyto další kroky:</span><span class="sxs-lookup"><span data-stu-id="315d0-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="315d0-270">Pomocí **Správce balíčků NuGet** přidejte do svého projektu odkaz na balíček NuGet; a pokud balíček ještě není ve vašem systému k dispozici, nainstalujte ho.</span><span class="sxs-lookup"><span data-stu-id="315d0-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="315d0-271">Správce balíčků otevřete tak, že vyberete **nástroje** > **správce balíčků NuGet** > **Spravovat balíčky NuGet pro řešení**.</span><span class="sxs-lookup"><span data-stu-id="315d0-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="315d0-272">Ověřte, zda jsou v systému nainstalovány závislosti jiných výrobců (například `Newtonsoft.Json`), a pokud nejsou, nainstalujte je.</span><span class="sxs-lookup"><span data-stu-id="315d0-272">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="315d0-273">Karta **Installed (instalovat** ) obsahuje seznam balíčků NuGet nainstalovaných ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="315d0-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="315d0-274">Pokud zde `Newtonsoft.Json` není uveden, vyberte kartu **Procházet** a do vyhledávacího pole zadejte "Newtonsoft. JSON".</span><span class="sxs-lookup"><span data-stu-id="315d0-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="315d0-275">Vyberte `Newtonsoft.Json` a v pravém podokně vyberte svůj projekt před výběrem možnosti **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="315d0-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="315d0-276">Pokud je v systému už `Newtonsoft.Json` nainstalovaná, přidejte ho do svého projektu tak, že ho vyberete v pravém podokně na kartě **Spravovat balíčky pro řešení** .</span><span class="sxs-lookup"><span data-stu-id="315d0-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="315d0-277">Následuje kompletní soubor *csproj* pro tento projekt:</span><span class="sxs-lookup"><span data-stu-id="315d0-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="315d0-278">Visual Studio 15,6 a starší</span><span class="sxs-lookup"><span data-stu-id="315d0-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

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

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="315d0-279">Visual Studio 15,7 a novější</span><span class="sxs-lookup"><span data-stu-id="315d0-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

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

<span data-ttu-id="315d0-280">Při nasazení aplikace jsou také součástí souborů aplikace všechny závislosti třetích stran používané ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="315d0-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="315d0-281">V systému, ve kterém je aplikace spuštěná, se nevyžadují knihovny třetích stran.</span><span class="sxs-lookup"><span data-stu-id="315d0-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="315d0-282">Mějte na paměti, že můžete nasadit samostatné nasazení s knihovnou třetích stran do platforem podporovaných v této knihovně.</span><span class="sxs-lookup"><span data-stu-id="315d0-282">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="315d0-283">To se podobá tomu, že se závislosti třetích stran s nativními závislostmi v nasazení závislém na rozhraní, kde nativní závislosti neexistují na cílové platformě, pokud se tam dříve nenainstalovaly.</span><span class="sxs-lookup"><span data-stu-id="315d0-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="315d0-284">Viz také:</span><span class="sxs-lookup"><span data-stu-id="315d0-284">See also</span></span>

- [<span data-ttu-id="315d0-285">Nasazení aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="315d0-285">.NET Core Application Deployment</span></span>](index.md)
- [<span data-ttu-id="315d0-286">Katalog identifikátorů runtime .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="315d0-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
