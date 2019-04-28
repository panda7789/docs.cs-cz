---
title: Předpoklady pro .NET Core ve Windows
description: Informace v závislosti na vaší Windows potřebujete počítač pro vývoj a spouštění aplikací .NET Core.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 2941721dfa4b87d4113e4f4b529845e47f3dc1b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646823"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="d334a-103">Předpoklady pro .NET Core ve Windows</span><span class="sxs-lookup"><span data-stu-id="d334a-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="d334a-104">Tento článek popisuje podporované verze operačního systému, aby bylo možné spustit aplikace .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="d334a-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="d334a-105">Podporované verze operačního systému a závislostech, které následují platí na tři způsoby, jak vyvíjet aplikace .NET Core ve Windows:</span><span class="sxs-lookup"><span data-stu-id="d334a-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="d334a-106">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="d334a-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="d334a-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d334a-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [<span data-ttu-id="d334a-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d334a-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="d334a-109">Také, pokud vyvíjíte ve Windows pomocí sady Visual Studio 2017, [požadavky sady Visual Studio 2017](#prerequisites-with-visual-studio-2017) část ve více podrobností o minimální verze podporované pro vývoj v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d334a-109">Also, if you're developing on Windows using Visual Studio 2017, the [Prerequisites with Visual Studio 2017](#prerequisites-with-visual-studio-2017) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="d334a-110">.NET core podporované verze Windows</span><span class="sxs-lookup"><span data-stu-id="d334a-110">.NET Core supported Windows versions</span></span>

<span data-ttu-id="d334a-111">.NET core je podporována v následujících verzích:</span><span class="sxs-lookup"><span data-stu-id="d334a-111">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="d334a-112">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d334a-112">Windows 7 SP1</span></span>
* <span data-ttu-id="d334a-113">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d334a-113">Windows 8.1</span></span>
* <span data-ttu-id="d334a-114">Windows 10 Anniversary Update (verze 1607) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="d334a-114">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="d334a-115">Windows Server 2008 R2 SP1 (plnou instalaci systému Server nebo Server Core)</span><span class="sxs-lookup"><span data-stu-id="d334a-115">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="d334a-116">Windows Server 2012 SP1 (plnou instalaci systému Server nebo Server Core)</span><span class="sxs-lookup"><span data-stu-id="d334a-116">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="d334a-117">Windows Server 2012 R2 (úplná Server nebo Server Core)</span><span class="sxs-lookup"><span data-stu-id="d334a-117">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="d334a-118">Windows Server 2016 nebo novější verze (plnou instalaci systému Server, Server Core nebo Nano Server)</span><span class="sxs-lookup"><span data-stu-id="d334a-118">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="d334a-119">.NET core podporované operační systémy</span><span class="sxs-lookup"><span data-stu-id="d334a-119">.NET Core supported operating systems</span></span>

<span data-ttu-id="d334a-120">Následující články obsahují úplný seznam operačních systémů nepodporuje .NET Core na verze:</span><span class="sxs-lookup"><span data-stu-id="d334a-120">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="d334a-121">.NET core 3.0 (Preview)</span><span class="sxs-lookup"><span data-stu-id="d334a-121">.NET Core 3.0 (Preview)</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="d334a-122">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="d334a-122">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="d334a-123">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d334a-123">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="d334a-124">.NET core 1.0</span><span class="sxs-lookup"><span data-stu-id="d334a-124">.NET Core 1.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

<span data-ttu-id="d334a-125">Odkazy ke stažení a další informace najdete v tématu [stáhne .NET](https://dotnet.microsoft.com/download) ke stažení nejnovější verze nebo [.NET stáhne archivu](https://dotnet.microsoft.com/download/archives#dotnet-core) pro starší verze.</span><span class="sxs-lookup"><span data-stu-id="d334a-125">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="d334a-126">.NET core závislosti</span><span class="sxs-lookup"><span data-stu-id="d334a-126">.NET Core dependencies</span></span>

<span data-ttu-id="d334a-127">Při spuštění na verzích Windows starších než Windows 10 a Windows serveru 2016 vyžadují Visual C++ Redistributable .NET core 1.1 a staršími verzemi.</span><span class="sxs-lookup"><span data-stu-id="d334a-127">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="d334a-128">Tato závislost je automaticky nainstalován pomocí instalačního programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d334a-128">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="d334a-129">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musí ručně doinstalovat při:</span><span class="sxs-lookup"><span data-stu-id="d334a-129">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="d334a-130">Instalace .NET Core s [skript instalačního programu](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="d334a-130">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="d334a-131">Nasazení samostatné aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d334a-131">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="d334a-132">Sestavení produktu ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="d334a-132">Building the product from source.</span></span>
* <span data-ttu-id="d334a-133">Instalace .NET Core prostřednictvím *ZIP* souboru.</span><span class="sxs-lookup"><span data-stu-id="d334a-133">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="d334a-134">To může zahrnovat servery sestavení/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="d334a-134">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="d334a-135">**Pro Windows 8.1 a starší verze, nebo Windows Server 2012 R2 a dřívějších verzích:**</span><span class="sxs-lookup"><span data-stu-id="d334a-135">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="d334a-136">Ujistěte se, že instalace systému Windows je aktuální a zahrnuje [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), kterou je možné nainstalovat prostřednictvím služby Windows Update.</span><span class="sxs-lookup"><span data-stu-id="d334a-136">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="d334a-137">Pokud nemáte k dispozici tato aktualizace instalována, zobrazí se vám chyba následujícím postupem při spuštění aplikace rozhraní .NET Core: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="d334a-137">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="d334a-138">**Pro Windows 7 nebo Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="d334a-138">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="d334a-139">Kromě KB2999226, ujistěte se, že budete mít taky [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) nainstalované.</span><span class="sxs-lookup"><span data-stu-id="d334a-139">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="d334a-140">Pokud nemáte k dispozici tato aktualizace instalována, zobrazí se zpráva podobná následující při spuštění aplikace rozhraní .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="d334a-140">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-for-net-core-30-preview-3"></a><span data-ttu-id="d334a-141">Předpoklady pro .NET Core 3.0 ve verzi Preview 3</span><span class="sxs-lookup"><span data-stu-id="d334a-141">Prerequisites for .NET Core 3.0 Preview 3</span></span>

<span data-ttu-id="d334a-142">.NET core 3.0 ve verzi Preview 3 má stejné požadavky jako v jiných verzích .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d334a-142">.NET Core 3.0 Preview 3 has the same prerequisites as other versions of .NET Core.</span></span> <span data-ttu-id="d334a-143">Ale pokud budete chtít použít Visual Studio k vytvoření aplikace .NET Core 3.0 projektů, je nutné použít [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="d334a-143">However, if you want to use Visual Studio to create .NET Core 3.0 projects, you must use the [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="d334a-144">Visual Studio 2019 může být nainstalovaná – souběžně s jinými verzemi nástroje Visual Studio bez konfliktu.</span><span class="sxs-lookup"><span data-stu-id="d334a-144">Visual Studio 2019 can be installed side-by-side with other versions of Visual Studio without conflict.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="d334a-145">Požadavky sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d334a-145">Prerequisites with Visual Studio 2017</span></span>
    
<span data-ttu-id="d334a-146">Můžete použít libovolný editor k vývoji aplikací .NET Core pomocí sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d334a-146">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="d334a-147">Visual Studio 2017 poskytuje integrované vývojové prostředí pro aplikace .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="d334a-147">Visual Studio 2017 provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="d334a-148">Další informace o změnách v sadě Visual Studio 2017 v [poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="d334a-148">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d334a-149">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d334a-149">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="d334a-150">Můžete vyvíjet aplikace .NET Core v sadě Visual Studio 2017 pomocí .NET Core 2.2 SDK:</span><span class="sxs-lookup"><span data-stu-id="d334a-150">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="d334a-151">[Stáhněte a nainstalujte Visual Studio 2017 verze 15.9.0 nebo vyšší](/visualstudio/install/install-visual-studio) s **vývoj pro různé platformy .NET Core** úloh (v **další sady nástrojů** části) vybrané.</span><span class="sxs-lookup"><span data-stu-id="d334a-151">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Instalace – snímek obrazovky sady Visual Studio 2017 s vybranou úlohou "Vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="d334a-153">Po **vývoj pro různé platformy .NET Core** je nainstalovaná sada nástrojů, Visual Studio obvykle nainstaluje předchozí verzi .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d334a-153">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="d334a-154">Například Visual Studio 2017 15.9 používá .NET Core 2.1 SDK ve výchozím nastavení po instalaci zatížení.</span><span class="sxs-lookup"><span data-stu-id="d334a-154">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="d334a-155">Aktualizace sady Visual Studio pro použití sady .NET Core 2.2 SDK:</span><span class="sxs-lookup"><span data-stu-id="d334a-155">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="d334a-156">Nainstalujte [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="d334a-156">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="d334a-157">Pokud chcete projekt pro použití nejnovější modul runtime .NET Core, jejich cíl změnit existující nebo nové projekty .NET Core na .NET Core 2.2 využitím následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="d334a-157">If you want your project to use the latest .NET Core runtime, retarget existing or new .NET Core projects to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="d334a-158">Na **projektu** nabídce zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d334a-158">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="d334a-159">V **Cílová architektura** nabídce pro výběr, nastavte hodnotu na **.NET Core 2.2**.</span><span class="sxs-lookup"><span data-stu-id="d334a-159">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Snímek obrazovky sady Visual Studio 2017 aplikace vlastnost projektu pomocí nabídky ".NET Core 2.2" target framework vybrané položky](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="d334a-161">Jakmile budete mít nakonfigurované s .NET Core 2.2 SDK sady Visual Studio, můžete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="d334a-161">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="d334a-162">Otevřete, sestavte a spusťte existující projekty .NET Core 1.x a 2.x.</span><span class="sxs-lookup"><span data-stu-id="d334a-162">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="d334a-163">Změnit cílení projektů .NET Core 1.x a 2.x na .NET Core 2.2, sestavení a spusťte.</span><span class="sxs-lookup"><span data-stu-id="d334a-163">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="d334a-164">Vytvořte nové projekty .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="d334a-164">Create new .NET Core 2.2 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d334a-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d334a-165">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="d334a-166">Můžete vyvíjet aplikace .NET Core 1.x v sadě Visual Studio [stáhnout a nainstalovat sadu Visual Studio 2017](/visualstudio/install/install-visual-studio) s **"Vývoj pro různé platformy .NET Core"** úloh (v **další sady nástrojů**části) vybrané.</span><span class="sxs-lookup"><span data-stu-id="d334a-166">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Instalace – snímek obrazovky sady Visual Studio 2017 s vybranou úlohou "Vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="d334a-168">Je možné použít Visual Studio 2015 pro vývoj v .NET Core 1.x, ale nedoporučuje z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="d334a-168">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="d334a-169">Nástroje .NET Core je verze preview, což není podporováno.</span><span class="sxs-lookup"><span data-stu-id="d334a-169">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="d334a-170">Projekty, které jsou založeny na project.json, který je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="d334a-170">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="d334a-171">Další informace o změnách formát projektu naleznete v tématu [podrobný přehled změn](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="d334a-171">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="d334a-172">Pokud chcete ověřit vaši verzi sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="d334a-172">To verify your Visual Studio version:</span></span>
>
> * <span data-ttu-id="d334a-173">Na **pomáhají** nabídce zvolte **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d334a-173">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="d334a-174">V **o Microsoft Visual Studio** dialogového okna, zkontrolujte číslo verze.</span><span class="sxs-lookup"><span data-stu-id="d334a-174">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="d334a-175">Pro aplikace .NET Core 3.0 ve verzi Preview 3, Visual Studio 2019 verze 16,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="d334a-175">For .NET Core 3.0 Preview 3 apps, Visual Studio 2019 version 16.0 or higher.</span></span>
>   * <span data-ttu-id="d334a-176">Pro aplikace .NET Core 2.2, Visual Studio 2017 verze 15.9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="d334a-176">For .NET Core 2.2 apps, Visual Studio 2017 version 15.9 or higher.</span></span>
>   * <span data-ttu-id="d334a-177">Pro aplikace .NET Core 2.1, Visual Studio 2017 verze 15.7 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="d334a-177">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="d334a-178">Pro aplikace .NET Core 1.x, Visual Studio 2017 verze 15,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="d334a-178">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>