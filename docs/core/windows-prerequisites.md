---
title: Předpoklady pro .NET Core ve Windows
description: Zjistěte, jaké závislosti potřebujete na počítači s Windows pro vývoj a spouštění aplikací .NET Core.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: c46a1f12ca20c0e21ee205e409a2a5a89e3389b3
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214547"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="cb947-103">Předpoklady pro .NET Core ve Windows</span><span class="sxs-lookup"><span data-stu-id="cb947-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="cb947-104">Tento článek ukazuje podporované verze operačního systému, aby bylo možné spouštět aplikace .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="cb947-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="cb947-105">Podporované verze operačního systému a závislosti, které následují, se vztahují na tři způsoby vývoje aplikací .NET Core v systému Windows:</span><span class="sxs-lookup"><span data-stu-id="cb947-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="cb947-106">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="cb947-106">Command line</span></span>](./tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="cb947-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cb947-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [<span data-ttu-id="cb947-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cb947-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="cb947-109">Pokud vyvíjíte v systému Windows pomocí sady Visual Studio, [požadavky pro vývoj aplikací .NET Core pomocí sady Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) jsou podrobněji popsány v článku o minimálních verzích podporovaných pro vývoj pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb947-109">Also, if you're developing on Windows using Visual Studio, the [Prerequisites to develop .NET Core apps with Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="cb947-110">Podporované operační systémy .NET Core</span><span class="sxs-lookup"><span data-stu-id="cb947-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="cb947-111">Následující články obsahují úplný seznam podporovaných operačních systémů .NET Core na verzi:</span><span class="sxs-lookup"><span data-stu-id="cb947-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="cb947-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="cb947-112">.NET Core 3.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="cb947-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="cb947-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="cb947-114">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="cb947-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="cb947-115">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="cb947-115">.NET Core 1.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

<span data-ttu-id="cb947-116">Odkazy ke stažení a další informace najdete v tématu stažení z [rozhraní .NET](https://dotnet.microsoft.com/download) pro stažení nejnovější verze nebo [archivu ke stažení](https://dotnet.microsoft.com/download/archives#dotnet-core) pro starší verze.</span><span class="sxs-lookup"><span data-stu-id="cb947-116">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="cb947-117">Závislosti .NET Core</span><span class="sxs-lookup"><span data-stu-id="cb947-117">.NET Core dependencies</span></span>

<span data-ttu-id="cb947-118">.NET Core 1,1 a starší verze vyžadují při spuštění C++ ve verzích Windows starších než Windows 10 a windows Server 2016 vizuál Redistributable.</span><span class="sxs-lookup"><span data-stu-id="cb947-118">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="cb947-119">Tato závislost je automaticky nainstalována instalačním programem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb947-119">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="cb947-120">[Distribuovatelné C++ součásti Microsoft Visual 2015 Update 3](https://www.microsoft.com/download/details.aspx?id=52685) je třeba nainstalovat ručně v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="cb947-120">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="cb947-121">Instalace .NET Core pomocí [skriptu instalačního programu](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="cb947-121">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="cb947-122">Nasazení samostatně obsažené aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb947-122">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="cb947-123">Sestavuje se produkt ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="cb947-123">Building the product from source.</span></span>
* <span data-ttu-id="cb947-124">Instalace .NET Core přes soubor *. zip* .</span><span class="sxs-lookup"><span data-stu-id="cb947-124">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="cb947-125">To může zahrnovat servery sestavení/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="cb947-125">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="cb947-126">**Pro Windows 8.1 a starší verze nebo Windows Server 2012 R2 a starší verze:**</span><span class="sxs-lookup"><span data-stu-id="cb947-126">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="cb947-127">Ujistěte se, že je instalace Windows aktuální a zahrnuje [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), která se dá nainstalovat prostřednictvím web Windows Update.</span><span class="sxs-lookup"><span data-stu-id="cb947-127">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="cb947-128">Pokud tuto aktualizaci nemáte nainstalovanou, při spuštění aplikace .NET Core se zobrazí chybová zpráva podobná následující:`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="cb947-128">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="cb947-129">**Pro Windows 7 nebo Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="cb947-129">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="cb947-130">Kromě KB2999226 se ujistěte, že máte nainstalovanou také [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) .</span><span class="sxs-lookup"><span data-stu-id="cb947-130">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="cb947-131">Pokud tuto aktualizaci nemáte nainstalovanou, při spuštění aplikace .NET Core se zobrazí chybová zpráva podobná následující: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="cb947-131">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a><span data-ttu-id="cb947-132">Předpoklady pro vývoj aplikací .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cb947-132">Prerequisites to develop .NET Core apps with Visual Studio</span></span>
    
<span data-ttu-id="cb947-133">I když můžete použít libovolný editor pro vývoj aplikací .NET Core pomocí .NET Core SDK, Visual Studio 2017 a novější verze poskytují integrované vývojové prostředí pro aplikace .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="cb947-133">Even though you can use any editor to develop .NET Core applications using the .NET Core SDK, Visual Studio 2017 and later versions provide an integrated development environment for .NET Core apps on Windows.</span></span>

<a name="vs-mapping"></a>

<span data-ttu-id="cb947-134">Pro každou verzi .NET Core je vyžadována minimální verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb947-134">Each .NET Core version has a minimum version of Visual Studio required.</span></span> <span data-ttu-id="cb947-135">Ověření verze sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="cb947-135">To verify your Visual Studio version:</span></span>

* <span data-ttu-id="cb947-136">V nabídce **help (nápovědu** ) vyberte **informace o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="cb947-136">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
* <span data-ttu-id="cb947-137">V dialogovém okně **o Microsoft Visual Studio** ověřte číslo verze.</span><span class="sxs-lookup"><span data-stu-id="cb947-137">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>

<span data-ttu-id="cb947-138">Následující tabulka uvádí minimální verzi pro jednotlivé sady SDK:</span><span class="sxs-lookup"><span data-stu-id="cb947-138">The following table lists the minimum version for each SDK:</span></span>

| <span data-ttu-id="cb947-139">Verze .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="cb947-139">.NET Core SDK version</span></span> | <span data-ttu-id="cb947-140">Verze sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cb947-140">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="cb947-141">3.0</span><span class="sxs-lookup"><span data-stu-id="cb947-141">3.0</span></span>                   | <span data-ttu-id="cb947-142">Visual Studio 2019 verze 16,3 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="cb947-142">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="cb947-143">2.2</span><span class="sxs-lookup"><span data-stu-id="cb947-143">2.2</span></span>                   | <span data-ttu-id="cb947-144">Visual Studio 2017 verze 15,9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="cb947-144">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="cb947-145">2.1</span><span class="sxs-lookup"><span data-stu-id="cb947-145">2.1</span></span>                   | <span data-ttu-id="cb947-146">Visual Studio 2017 verze 15,7 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="cb947-146">Visual Studio 2017 version 15.7 or higher.</span></span> |
| <span data-ttu-id="cb947-147">verze</span><span class="sxs-lookup"><span data-stu-id="cb947-147">1.x</span></span>                   | <span data-ttu-id="cb947-148">Visual Studio 2017 verze 15,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="cb947-148">Visual Studio 2017 version 15.0 or higher.</span></span> |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="cb947-149">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="cb947-149">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="cb947-150">Vývoj aplikací .NET Core v sadě Visual Studio 2019 pomocí sady .NET Core 3,0 SDK:</span><span class="sxs-lookup"><span data-stu-id="cb947-150">To develop .NET Core apps in Visual Studio 2019 using the .NET Core 3.0 SDK:</span></span>

* <span data-ttu-id="cb947-151">[Stáhněte a nainstalujte sadu Visual Studio 2019 verze 16,3 nebo vyšší](/visualstudio/install/install-visual-studio) a vyberte jednu z následujících úloh, které zahrnují .NET Core SDK v závislosti na druhu aplikace, kterou sestavujete:</span><span class="sxs-lookup"><span data-stu-id="cb947-151">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) and select one of the following workloads that includes the .NET Core SDK, depending on the kind of application you're building:</span></span>

  * <span data-ttu-id="cb947-152">Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="cb947-152">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
  * <span data-ttu-id="cb947-153">Úlohy **vývoje ASP.NET a webu** v části **web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="cb947-153">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
  * <span data-ttu-id="cb947-154">Pracovní proces **vývoje pro NET Desktop** v části **Windows** .</span><span class="sxs-lookup"><span data-stu-id="cb947-154">The **NET desktop development** workload in the **Windows** section.</span></span>

<span data-ttu-id="cb947-155">Na následujícím obrázku vidíte úlohy **vývoje .NET Core pro různé platformy** vybrané v uživatelském rozhraní sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="cb947-155">The following image shows the **.NET Core cross-platform development** workload selected in the Visual Studio UI:</span></span>

![Snímek obrazovky s instalací sady Visual Studio 2019 se zvolenou úlohou "vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-2019-workloads.jpg)

<span data-ttu-id="cb947-157">Sada Visual Studio 2019 16,3 po instalaci kterékoli z těchto úloh používá standardně sadu .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="cb947-157">Visual Studio 2019 16.3 uses .NET Core 3.0 SDK by default after any of these workloads are installed.</span></span>

<span data-ttu-id="cb947-158">Pokud chcete, aby existující projekty používaly nejnovější modul runtime .NET Core, proveďte cílení každého existujícího projektu .NET Core na .NET Core 3,0 pomocí následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="cb947-158">If you want your existing projects to use the latest .NET Core runtime, retarget each existing .NET Core project to .NET Core 3.0 using the following instructions:</span></span>

* <span data-ttu-id="cb947-159">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="cb947-159">On the **Project** menu, choose **Properties**.</span></span>
* <span data-ttu-id="cb947-160">V nabídce Výběr **cílového rozhraní** nastavte hodnotu na **.NET Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="cb947-160">In the **Target framework** selection menu, set the value to **.NET Core 3.0**.</span></span>

![Snímek vlastnosti projektu aplikace sady Visual Studio 2019 s vybranou položkou nabídky cílové rozhraní .NET Core 3,0](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

<span data-ttu-id="cb947-162">Jakmile máte sadu Visual Studio nakonfigurovanou pomocí sady .NET Core 3,0 SDK, můžete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="cb947-162">Once you have Visual Studio configured with .NET Core 3.0 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="cb947-163">Otevřete, sestavte a spusťte existující projekty .NET Core 1. x a 2. x.</span><span class="sxs-lookup"><span data-stu-id="cb947-163">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="cb947-164">Proveďte změny cílení na projekty .NET Core 1. x a 2. x na .NET Core 3,0, sestavte a spusťte.</span><span class="sxs-lookup"><span data-stu-id="cb947-164">Retarget .NET Core 1.x and 2.x projects to .NET Core 3.0, build, and run.</span></span>
* <span data-ttu-id="cb947-165">Vytvořte nové projekty .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="cb947-165">Create new .NET Core 3.0 projects.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="cb947-166">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="cb947-166">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="cb947-167">Vývoj aplikací .NET Core v sadě Visual Studio 2017 pomocí sady .NET Core 2,2 SDK:</span><span class="sxs-lookup"><span data-stu-id="cb947-167">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

* <span data-ttu-id="cb947-168">[Stáhněte a nainstalujte si sadu Visual Studio 2017 verze 15.9.0 nebo novější](/visualstudio/install/install-visual-studio) pomocí úlohy **vývoje .NET Core pro různé platformy** (v části **jiné sady nástrojů** ).</span><span class="sxs-lookup"><span data-stu-id="cb947-168">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Snímek obrazovky s instalací sady Visual Studio 2017 se zvolenou úlohou "vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="cb947-170">Po instalaci sady nástrojů pro **vývoj pro různé platformy .NET Core** se v sadě Visual Studio obvykle nainstaluje předchozí verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="cb947-170">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="cb947-171">Sada Visual Studio 2017 15,9 například po instalaci úlohy používá .NET Core 2,1 SDK ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="cb947-171">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="cb947-172">Aktualizace sady Visual Studio tak, aby používala sadu .NET Core 2,2 SDK:</span><span class="sxs-lookup"><span data-stu-id="cb947-172">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="cb947-173">Nainstalujte [sadu .NET Core 2,2 SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="cb947-173">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="cb947-174">Pokud chcete, aby váš projekt používal nejnovější modul runtime .NET Core, přecílíte všechny existující nebo nové projekty .NET Core na .NET Core 2,2 pomocí následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="cb947-174">If you want your project to use the latest .NET Core runtime, retarget each existing or new .NET Core project to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="cb947-175">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="cb947-175">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="cb947-176">V nabídce Výběr **cílového rozhraní** nastavte hodnotu na **.NET Core 2,2**.</span><span class="sxs-lookup"><span data-stu-id="cb947-176">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Snímek vlastnosti projektu aplikace sady Visual Studio 2017 s vybranou položkou nabídky cílové rozhraní .NET Core 2,2](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="cb947-178">Jakmile máte sadu Visual Studio nakonfigurovanou pomocí sady .NET Core 2,2 SDK, můžete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="cb947-178">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="cb947-179">Otevřete, sestavte a spusťte existující projekty .NET Core 1. x a 2. x.</span><span class="sxs-lookup"><span data-stu-id="cb947-179">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="cb947-180">Proveďte změny cílení na projekty .NET Core 1. x a 2. x na .NET Core 2,2, sestavte a spusťte.</span><span class="sxs-lookup"><span data-stu-id="cb947-180">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="cb947-181">Vytvořte nové projekty .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="cb947-181">Create new .NET Core 2.2 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cb947-182">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cb947-182">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="cb947-183">Pro vývoj aplikací .NET Core 1. x v sadě Visual Studio [Stáhněte a nainstalujte sadu Visual Studio 2017](/visualstudio/install/install-visual-studio) s úlohou **"vývoj pro různé sady nástrojů .NET Core"** (v části **ostatní sady nástrojů** ).</span><span class="sxs-lookup"><span data-stu-id="cb947-183">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Snímek obrazovky s instalací sady Visual Studio 2017 se zvolenou úlohou "vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="cb947-185">Je možné použít Visual Studio 2015 pro vývoj pro .NET Core 1. x, ale nedoporučuje se z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="cb947-185">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
>
> * <span data-ttu-id="cb947-186">Nástroje .NET Core jsou verze Preview, což není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cb947-186">The .NET Core tooling is a preview version, which is not supported.</span></span>
> * <span data-ttu-id="cb947-187">Projekty jsou založené na projektu Project. JSON, který je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="cb947-187">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="cb947-188">Další informace o změnách formátu projektu naleznete v části [Přehled změn na nejvyšší úrovni](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="cb947-188">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

---
