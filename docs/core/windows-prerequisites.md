---
title: Předpoklady pro .NET Core ve Windows
description: Zjistěte, jaké závislosti potřebujete na počítači s Windows pro vývoj a spouštění aplikací .NET Core.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: b1557e6910cb6d0b6d7e2b3ce2aec97d3715fec7
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591675"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="c7dde-103">Předpoklady pro .NET Core ve Windows</span><span class="sxs-lookup"><span data-stu-id="c7dde-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="c7dde-104">Tento článek ukazuje podporované verze operačního systému, aby bylo možné spouštět aplikace .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="c7dde-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="c7dde-105">Podporované verze operačního systému a závislosti, které následují, se vztahují na tři způsoby vývoje aplikací .NET Core v systému Windows:</span><span class="sxs-lookup"><span data-stu-id="c7dde-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="c7dde-106">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="c7dde-106">Command line</span></span>](./tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="c7dde-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c7dde-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [<span data-ttu-id="c7dde-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c7dde-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="c7dde-109">Pokud vyvíjíte v systému Windows pomocí sady Visual Studio, [požadavky pro vývoj aplikací .NET Core pomocí sady Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) jsou podrobněji popsány v článku o minimálních verzích podporovaných pro vývoj pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7dde-109">Also, if you're developing on Windows using Visual Studio, the [Prerequisites to develop .NET Core apps with Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="c7dde-110">Podporované operační systémy .NET Core</span><span class="sxs-lookup"><span data-stu-id="c7dde-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="c7dde-111">Následující články obsahují úplný seznam podporovaných operačních systémů .NET Core na verzi:</span><span class="sxs-lookup"><span data-stu-id="c7dde-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="c7dde-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7dde-112">.NET Core 3.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="c7dde-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="c7dde-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="c7dde-114">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="c7dde-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)

<span data-ttu-id="c7dde-115">Odkazy ke stažení a další informace najdete v tématu stažení z [rozhraní .NET](https://dotnet.microsoft.com/download) pro stažení nejnovější verze nebo [archivu ke stažení](https://dotnet.microsoft.com/download/archives#dotnet-core) pro starší verze.</span><span class="sxs-lookup"><span data-stu-id="c7dde-115">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="c7dde-116">Závislosti .NET Core</span><span class="sxs-lookup"><span data-stu-id="c7dde-116">.NET Core dependencies</span></span>

<span data-ttu-id="c7dde-117">[Distribuovatelné C++ součásti Microsoft Visual 2015 Update 3](https://www.microsoft.com/download/details.aspx?id=52685) je třeba nainstalovat ručně v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="c7dde-117">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="c7dde-118">Instalace .NET Core pomocí [skriptu instalačního programu](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="c7dde-118">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="c7dde-119">Nasazení samostatně obsažené aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7dde-119">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="c7dde-120">Sestavuje se produkt ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="c7dde-120">Building the product from source.</span></span>
* <span data-ttu-id="c7dde-121">Instalace .NET Core přes soubor *. zip* .</span><span class="sxs-lookup"><span data-stu-id="c7dde-121">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="c7dde-122">To může zahrnovat servery sestavení/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="c7dde-122">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="c7dde-123">**Pro Windows 8.1 a starší verze nebo Windows Server 2012 R2 a starší verze:**</span><span class="sxs-lookup"><span data-stu-id="c7dde-123">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="c7dde-124">Ujistěte se, že je instalace Windows aktuální a zahrnuje [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), která se dá nainstalovat prostřednictvím web Windows Update.</span><span class="sxs-lookup"><span data-stu-id="c7dde-124">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="c7dde-125">Pokud tuto aktualizaci nemáte nainstalovanou, při spuštění aplikace .NET Core se zobrazí chybová zpráva podobná následující:`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="c7dde-125">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="c7dde-126">**Pro Windows 7 nebo Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="c7dde-126">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="c7dde-127">Kromě KB2999226 se ujistěte, že máte nainstalovanou také [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) .</span><span class="sxs-lookup"><span data-stu-id="c7dde-127">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="c7dde-128">Pokud tuto aktualizaci nemáte nainstalovanou, při spuštění aplikace .NET Core se zobrazí chybová zpráva podobná následující: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="c7dde-128">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a><span data-ttu-id="c7dde-129">Předpoklady pro vývoj aplikací .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c7dde-129">Prerequisites to develop .NET Core apps with Visual Studio</span></span>
    
<span data-ttu-id="c7dde-130">I když můžete použít libovolný editor pro vývoj aplikací .NET Core pomocí .NET Core SDK, Visual Studio 2017 a novější verze poskytují integrované vývojové prostředí pro aplikace .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="c7dde-130">Even though you can use any editor to develop .NET Core applications using the .NET Core SDK, Visual Studio 2017 and later versions provide an integrated development environment for .NET Core apps on Windows.</span></span>

<a name="vs-mapping"></a>

<span data-ttu-id="c7dde-131">Pro každou verzi .NET Core je vyžadována minimální verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c7dde-131">Each .NET Core version has a minimum version of Visual Studio required.</span></span> <span data-ttu-id="c7dde-132">Ověření verze sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="c7dde-132">To verify your Visual Studio version:</span></span>

* <span data-ttu-id="c7dde-133">V nabídce **help (nápovědu** ) vyberte **informace o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c7dde-133">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
* <span data-ttu-id="c7dde-134">V dialogovém okně **o Microsoft Visual Studio** ověřte číslo verze.</span><span class="sxs-lookup"><span data-stu-id="c7dde-134">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>

<span data-ttu-id="c7dde-135">Následující tabulka uvádí minimální verzi pro jednotlivé sady SDK:</span><span class="sxs-lookup"><span data-stu-id="c7dde-135">The following table lists the minimum version for each SDK:</span></span>

| <span data-ttu-id="c7dde-136">Verze .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c7dde-136">.NET Core SDK version</span></span> | <span data-ttu-id="c7dde-137">Verze Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c7dde-137">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="c7dde-138">3.0</span><span class="sxs-lookup"><span data-stu-id="c7dde-138">3.0</span></span>                   | <span data-ttu-id="c7dde-139">Visual Studio 2019 verze 16,3 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c7dde-139">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="c7dde-140">2.2</span><span class="sxs-lookup"><span data-stu-id="c7dde-140">2.2</span></span>                   | <span data-ttu-id="c7dde-141">Visual Studio 2017 verze 15,9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c7dde-141">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="c7dde-142">2.1</span><span class="sxs-lookup"><span data-stu-id="c7dde-142">2.1</span></span>                   | <span data-ttu-id="c7dde-143">Visual Studio 2017 verze 15,7 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c7dde-143">Visual Studio 2017 version 15.7 or higher.</span></span> |
| <span data-ttu-id="c7dde-144">verze</span><span class="sxs-lookup"><span data-stu-id="c7dde-144">1.x</span></span>                   | <span data-ttu-id="c7dde-145">Visual Studio 2017 verze 15,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c7dde-145">Visual Studio 2017 version 15.0 or higher.</span></span> |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="c7dde-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7dde-146">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="c7dde-147">Vývoj aplikací .NET Core v sadě Visual Studio 2019 pomocí sady .NET Core 3,0 SDK:</span><span class="sxs-lookup"><span data-stu-id="c7dde-147">To develop .NET Core apps in Visual Studio 2019 using the .NET Core 3.0 SDK:</span></span>

* <span data-ttu-id="c7dde-148">[Stáhněte a nainstalujte sadu Visual Studio 2019 verze 16,3 nebo vyšší](/visualstudio/install/install-visual-studio) a vyberte jednu z následujících úloh, které zahrnují .NET Core SDK v závislosti na druhu aplikace, kterou sestavujete:</span><span class="sxs-lookup"><span data-stu-id="c7dde-148">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) and select one of the following workloads that includes the .NET Core SDK, depending on the kind of application you're building:</span></span>

  * <span data-ttu-id="c7dde-149">Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="c7dde-149">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
  * <span data-ttu-id="c7dde-150">Úlohy **vývoje ASP.NET a webu** v části **web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="c7dde-150">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
  * <span data-ttu-id="c7dde-151">Pracovní proces **vývoje pro NET Desktop** v části **Windows** .</span><span class="sxs-lookup"><span data-stu-id="c7dde-151">The **NET desktop development** workload in the **Windows** section.</span></span>

<span data-ttu-id="c7dde-152">Na následujícím obrázku vidíte úlohy **vývoje .NET Core pro různé platformy** vybrané v uživatelském rozhraní sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="c7dde-152">The following image shows the **.NET Core cross-platform development** workload selected in the Visual Studio UI:</span></span>

![Snímek obrazovky s instalací sady Visual Studio 2019 se zvolenou úlohou "vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-2019-workloads.jpg)

<span data-ttu-id="c7dde-154">Sada Visual Studio 2019 16,3 po instalaci kterékoli z těchto úloh používá standardně sadu .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c7dde-154">Visual Studio 2019 16.3 uses .NET Core 3.0 SDK by default after any of these workloads are installed.</span></span>

<span data-ttu-id="c7dde-155">Pokud chcete, aby existující projekty používaly nejnovější modul runtime .NET Core, proveďte cílení každého existujícího projektu .NET Core na .NET Core 3,0 pomocí následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="c7dde-155">If you want your existing projects to use the latest .NET Core runtime, retarget each existing .NET Core project to .NET Core 3.0 using the following instructions:</span></span>

* <span data-ttu-id="c7dde-156">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c7dde-156">On the **Project** menu, choose **Properties**.</span></span>
* <span data-ttu-id="c7dde-157">V nabídce Výběr **cílového rozhraní** nastavte hodnotu na **.NET Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="c7dde-157">In the **Target framework** selection menu, set the value to **.NET Core 3.0**.</span></span>

![Snímek vlastnosti projektu aplikace sady Visual Studio 2019 s vybranou položkou nabídky cílové rozhraní .NET Core 3,0](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

<span data-ttu-id="c7dde-159">Jakmile máte sadu Visual Studio nakonfigurovanou pomocí sady .NET Core 3,0 SDK, můžete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="c7dde-159">Once you have Visual Studio configured with .NET Core 3.0 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="c7dde-160">Otevřete, sestavte a spusťte existující projekty .NET Core 1. x a 2. x.</span><span class="sxs-lookup"><span data-stu-id="c7dde-160">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="c7dde-161">Proveďte změny cílení na projekty .NET Core 1. x a 2. x na .NET Core 3,0, sestavte a spusťte.</span><span class="sxs-lookup"><span data-stu-id="c7dde-161">Retarget .NET Core 1.x and 2.x projects to .NET Core 3.0, build, and run.</span></span>
* <span data-ttu-id="c7dde-162">Vytvořte nové projekty .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="c7dde-162">Create new .NET Core 3.0 projects.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c7dde-163">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c7dde-163">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="c7dde-164">Vývoj aplikací .NET Core v sadě Visual Studio 2017 pomocí sady .NET Core 2,2 SDK:</span><span class="sxs-lookup"><span data-stu-id="c7dde-164">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

* <span data-ttu-id="c7dde-165">[Stáhněte a nainstalujte sadu Visual Studio 2019 verze 16,3 nebo vyšší](/visualstudio/install/install-visual-studio) pomocí úlohy **vývoje .NET Core pro různé platformy** (v části **jiné sady nástrojů** ).</span><span class="sxs-lookup"><span data-stu-id="c7dde-165">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>
* <span data-ttu-id="c7dde-166">[Stáhněte a nainstalujte si sadu Visual Studio 2017 verze 15.9.0 nebo novější](/visualstudio/install/install-visual-studio) pomocí úlohy **vývoje .NET Core pro různé platformy** (v části **jiné sady nástrojů** ).</span><span class="sxs-lookup"><span data-stu-id="c7dde-166">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Snímek obrazovky s instalací sady Visual Studio 2017 se zvolenou úlohou "vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="c7dde-168">Po instalaci sady nástrojů pro **vývoj pro různé platformy .NET Core** se v sadě Visual Studio obvykle nainstaluje předchozí verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c7dde-168">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="c7dde-169">Sada Visual Studio 2017 15,9 například po instalaci úlohy používá .NET Core 2,1 SDK ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c7dde-169">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="c7dde-170">Aktualizace sady Visual Studio tak, aby používala sadu .NET Core 2,2 SDK:</span><span class="sxs-lookup"><span data-stu-id="c7dde-170">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="c7dde-171">Nainstalujte [sadu .NET Core 2,2 SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="c7dde-171">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="c7dde-172">Pokud chcete, aby váš projekt používal nejnovější modul runtime .NET Core, přecílíte všechny existující nebo nové projekty .NET Core na .NET Core 2,2 pomocí následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="c7dde-172">If you want your project to use the latest .NET Core runtime, retarget each existing or new .NET Core project to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="c7dde-173">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c7dde-173">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="c7dde-174">V nabídce Výběr **cílového rozhraní** nastavte hodnotu na **.NET Core 2,2**.</span><span class="sxs-lookup"><span data-stu-id="c7dde-174">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Snímek vlastnosti projektu aplikace sady Visual Studio 2017 s vybranou položkou nabídky cílové rozhraní .NET Core 2,2](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="c7dde-176">Jakmile máte sadu Visual Studio nakonfigurovanou pomocí sady .NET Core 2,2 SDK, můžete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="c7dde-176">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="c7dde-177">Otevřete, sestavte a spusťte existující projekty .NET Core 1. x a 2. x.</span><span class="sxs-lookup"><span data-stu-id="c7dde-177">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="c7dde-178">Proveďte změny cílení na projekty .NET Core 1. x a 2. x na .NET Core 2,2, sestavte a spusťte.</span><span class="sxs-lookup"><span data-stu-id="c7dde-178">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="c7dde-179">Vytvořte nové projekty .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="c7dde-179">Create new .NET Core 2.2 projects.</span></span>

---
