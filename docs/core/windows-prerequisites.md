---
title: Předpoklady pro .NET Core ve Windows
description: Zjistěte, jaké závislosti potřebujete na počítači s Windows pro vývoj a spouštění aplikací .NET Core.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 82d336bc4efb34d336d5078952683c1673c3fa8a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926041"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="3fbfd-103">Předpoklady pro .NET Core ve Windows</span><span class="sxs-lookup"><span data-stu-id="3fbfd-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="3fbfd-104">Tento článek ukazuje podporované verze operačního systému, aby bylo možné spouštět aplikace .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="3fbfd-105">Podporované verze operačního systému a závislosti, které následují, se vztahují na tři způsoby vývoje aplikací .NET Core v systému Windows:</span><span class="sxs-lookup"><span data-stu-id="3fbfd-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="3fbfd-106">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="3fbfd-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="3fbfd-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3fbfd-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [<span data-ttu-id="3fbfd-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3fbfd-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="3fbfd-109">Pokud vyvíjíte v systému Windows pomocí sady Visual Studio 2017, v části [požadavky se sadou Visual studio 2017](#prerequisites-with-visual-studio-2017) podrobnější informace o minimálních verzích podporovaných pro vývoj pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-109">Also, if you're developing on Windows using Visual Studio 2017, the [Prerequisites with Visual Studio 2017](#prerequisites-with-visual-studio-2017) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="3fbfd-110">Podporované operační systémy .NET Core</span><span class="sxs-lookup"><span data-stu-id="3fbfd-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="3fbfd-111">Následující články obsahují úplný seznam podporovaných operačních systémů .NET Core na verzi:</span><span class="sxs-lookup"><span data-stu-id="3fbfd-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="3fbfd-112">.NET Core 3,0 (Preview)</span><span class="sxs-lookup"><span data-stu-id="3fbfd-112">.NET Core 3.0 (Preview)</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="3fbfd-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="3fbfd-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="3fbfd-114">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="3fbfd-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="3fbfd-115">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="3fbfd-115">.NET Core 1.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

<span data-ttu-id="3fbfd-116">Odkazy ke stažení a další informace najdete v tématu stažení z [rozhraní .NET](https://dotnet.microsoft.com/download) pro stažení nejnovější verze nebo [archivu ke stažení](https://dotnet.microsoft.com/download/archives#dotnet-core) pro starší verze.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-116">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="3fbfd-117">Závislosti .NET Core</span><span class="sxs-lookup"><span data-stu-id="3fbfd-117">.NET Core dependencies</span></span>

<span data-ttu-id="3fbfd-118">.NET Core 1,1 a starší verze vyžadují při spuštění C++ ve verzích Windows starších než Windows 10 a windows Server 2016 vizuál Redistributable.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-118">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="3fbfd-119">Tato závislost je automaticky nainstalována instalačním programem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-119">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="3fbfd-120">[Distribuovatelné C++ součásti Microsoft Visual 2015 Update 3](https://www.microsoft.com/download/details.aspx?id=52685) je třeba nainstalovat ručně v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="3fbfd-120">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="3fbfd-121">Instalace .NET Core pomocí [skriptu instalačního programu](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="3fbfd-121">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="3fbfd-122">Nasazení samostatně obsažené aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-122">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="3fbfd-123">Sestavuje se produkt ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-123">Building the product from source.</span></span>
* <span data-ttu-id="3fbfd-124">Instalace .NET Core přes soubor *. zip* .</span><span class="sxs-lookup"><span data-stu-id="3fbfd-124">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="3fbfd-125">To může zahrnovat servery sestavení/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-125">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="3fbfd-126">**Pro Windows 8.1 a starší verze nebo Windows Server 2012 R2 a starší verze:**</span><span class="sxs-lookup"><span data-stu-id="3fbfd-126">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="3fbfd-127">Ujistěte se, že je instalace Windows aktuální a zahrnuje [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), která se dá nainstalovat prostřednictvím web Windows Update.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-127">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="3fbfd-128">Pokud tuto aktualizaci nemáte nainstalovanou, při spuštění aplikace .NET Core se zobrazí chybová zpráva podobná následující:`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="3fbfd-128">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="3fbfd-129">**Pro Windows 7 nebo Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="3fbfd-129">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="3fbfd-130">Kromě KB2999226 se ujistěte, že máte nainstalovanou také [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) .</span><span class="sxs-lookup"><span data-stu-id="3fbfd-130">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="3fbfd-131">Pokud tuto aktualizaci nemáte nainstalovanou, při spuštění aplikace .NET Core se zobrazí chybová zpráva podobná následující: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-131">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-for-net-core-30-preview-3"></a><span data-ttu-id="3fbfd-132">Předpoklady pro .NET Core 3,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="3fbfd-132">Prerequisites for .NET Core 3.0 Preview 3</span></span>

<span data-ttu-id="3fbfd-133">.NET Core 3,0 Preview 3 má stejné požadavky jako jiné verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-133">.NET Core 3.0 Preview 3 has the same prerequisites as other versions of .NET Core.</span></span> <span data-ttu-id="3fbfd-134">Pokud však chcete použít aplikaci Visual Studio k vytvoření projektu .NET Core 3,0, je nutné použít [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="3fbfd-134">However, if you want to use Visual Studio to create .NET Core 3.0 projects, you must use the [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="3fbfd-135">Sadu Visual Studio 2019 lze nainstalovat souběžně s jinými verzemi sady Visual Studio bez konfliktu.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-135">Visual Studio 2019 can be installed side-by-side with other versions of Visual Studio without conflict.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="3fbfd-136">Požadavky v rámci sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3fbfd-136">Prerequisites with Visual Studio 2017</span></span>
    
<span data-ttu-id="3fbfd-137">K vývoji aplikací .NET Core pomocí .NET Core SDK můžete použít libovolný editor.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-137">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="3fbfd-138">Visual Studio 2017 poskytuje integrované vývojové prostředí pro aplikace .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-138">Visual Studio 2017 provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="3fbfd-139">V poznámkách k [verzi](/visualstudio/releasenotes/vs2017-relnotes)si můžete přečíst další informace o změnách v aplikaci Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-139">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3fbfd-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3fbfd-140">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="3fbfd-141">Vývoj aplikací .NET Core v sadě Visual Studio 2017 pomocí sady .NET Core 2,2 SDK:</span><span class="sxs-lookup"><span data-stu-id="3fbfd-141">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="3fbfd-142">[Stáhněte a nainstalujte si sadu Visual Studio 2017 verze 15.9.0 nebo novější](/visualstudio/install/install-visual-studio) pomocí úlohy **vývoje .NET Core pro různé platformy** (v části **jiné sady nástrojů** ).</span><span class="sxs-lookup"><span data-stu-id="3fbfd-142">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Snímek obrazovky s instalací sady Visual Studio 2017 se zvolenou úlohou "vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="3fbfd-144">Po instalaci sady nástrojů pro **vývoj pro různé platformy .NET Core** se v sadě Visual Studio obvykle nainstaluje předchozí verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-144">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="3fbfd-145">Sada Visual Studio 2017 15,9 například po instalaci úlohy používá .NET Core 2,1 SDK ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-145">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="3fbfd-146">Aktualizace sady Visual Studio tak, aby používala sadu .NET Core 2,2 SDK:</span><span class="sxs-lookup"><span data-stu-id="3fbfd-146">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="3fbfd-147">Nainstalujte [sadu .NET Core 2,2 SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="3fbfd-147">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="3fbfd-148">Pokud chcete, aby váš projekt používal nejnovější modul runtime .NET Core, přecílíte stávající nebo nové projekty .NET Core na .NET Core 2,2 pomocí následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="3fbfd-148">If you want your project to use the latest .NET Core runtime, retarget existing or new .NET Core projects to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="3fbfd-149">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-149">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="3fbfd-150">V nabídce Výběr **cílového rozhraní** nastavte hodnotu na **.NET Core 2,2**.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-150">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Snímek vlastnosti projektu aplikace sady Visual Studio 2017 s vybranou položkou nabídky cílové rozhraní .NET Core 2,2](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="3fbfd-152">Jakmile máte sadu Visual Studio nakonfigurovanou pomocí sady .NET Core 2,2 SDK, můžete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="3fbfd-152">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="3fbfd-153">Otevřete, sestavte a spusťte existující projekty .NET Core 1. x a 2. x.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-153">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="3fbfd-154">Proveďte změny cílení na projekty .NET Core 1. x a 2. x na .NET Core 2,2, sestavte a spusťte.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-154">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="3fbfd-155">Vytvořte nové projekty .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-155">Create new .NET Core 2.2 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3fbfd-156">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3fbfd-156">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="3fbfd-157">Pro vývoj aplikací .NET Core 1. x v sadě Visual Studio [Stáhněte a nainstalujte sadu Visual Studio 2017](/visualstudio/install/install-visual-studio) s úlohou **"vývoj pro různé sady nástrojů .NET Core"** (v části **ostatní sady nástrojů** ).</span><span class="sxs-lookup"><span data-stu-id="3fbfd-157">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Snímek obrazovky s instalací sady Visual Studio 2017 se zvolenou úlohou "vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="3fbfd-159">Je možné použít Visual Studio 2015 pro vývoj pro .NET Core 1. x, ale nedoporučuje se z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="3fbfd-159">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
>
> * <span data-ttu-id="3fbfd-160">Nástroje .NET Core jsou verze Preview, což není podporováno.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-160">The .NET Core tooling is a preview version, which is not supported.</span></span>
> * <span data-ttu-id="3fbfd-161">Projekty jsou založené na projektu Project. JSON, který je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-161">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="3fbfd-162">Další informace o změnách formátu projektu naleznete v části [Přehled změn na nejvyšší úrovni](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="3fbfd-162">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="3fbfd-163">Ověření verze sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="3fbfd-163">To verify your Visual Studio version:</span></span>
>
> * <span data-ttu-id="3fbfd-164">V nabídce **help (nápovědu** ) vyberte **informace o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-164">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="3fbfd-165">V dialogovém okně **o Microsoft Visual Studio** ověřte číslo verze.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-165">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="3fbfd-166">Pro aplikace .NET Core 3,0 Preview 3, Visual Studio 2019 verze 16,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-166">For .NET Core 3.0 Preview 3 apps, Visual Studio 2019 version 16.0 or higher.</span></span>
>   * <span data-ttu-id="3fbfd-167">Pro aplikace .NET Core 2,2, Visual Studio 2017 verze 15,9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-167">For .NET Core 2.2 apps, Visual Studio 2017 version 15.9 or higher.</span></span>
>   * <span data-ttu-id="3fbfd-168">Pro aplikace .NET Core 2,1, Visual Studio 2017 verze 15,7 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-168">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="3fbfd-169">Pro aplikace .NET Core 1. x, Visual Studio 2017 verze 15,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="3fbfd-169">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
