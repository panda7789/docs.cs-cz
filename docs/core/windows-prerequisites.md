---
title: Předpoklady pro .NET Core v systému Windows
description: Zjistěte, co závislosti, musíte na váš Windows počítače pro vývoj a spouštění aplikací .NET Core.
author: JRAlexander
ms.author: johalex
ms.date: 04/24/2018
ms.topic: article
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: ac898ea87c0247581154eb7de65e8cbe6ea6ba15
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="9d671-103">Předpoklady pro .NET Core v systému Windows</span><span class="sxs-lookup"><span data-stu-id="9d671-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="9d671-104">Tento článek ukazuje závislosti potřebné k vývoji aplikací .NET Core v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9d671-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="9d671-105">Podporované verze operačního systému a závislosti, které platí na tři způsoby, jak vývoj aplikací .NET Core v systému Windows:</span><span class="sxs-lookup"><span data-stu-id="9d671-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="9d671-106">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="9d671-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="9d671-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9d671-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="9d671-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9d671-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="9d671-109">.NET core podporované verze systému Windows</span><span class="sxs-lookup"><span data-stu-id="9d671-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="9d671-110">.NET core je podporována v následujících verzích:</span><span class="sxs-lookup"><span data-stu-id="9d671-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="9d671-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="9d671-111">Windows 7 SP1</span></span>
* <span data-ttu-id="9d671-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="9d671-112">Windows 8.1</span></span>
* <span data-ttu-id="9d671-113">Windows 10 Anniversary Update (verze 1607) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="9d671-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="9d671-114">Windows Server 2008 R2 SP1 (celého serveru nebo jádra serveru)</span><span class="sxs-lookup"><span data-stu-id="9d671-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="9d671-115">Windows Server 2012 SP1 (celého serveru nebo jádra serveru)</span><span class="sxs-lookup"><span data-stu-id="9d671-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="9d671-116">Windows Server 2012 R2 (celého serveru nebo jádra serveru)</span><span class="sxs-lookup"><span data-stu-id="9d671-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="9d671-117">Windows Server 2016 (celý Server, Server Core nebo Nano Server)</span><span class="sxs-lookup"><span data-stu-id="9d671-117">Windows Server 2016 (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="9d671-118">V tématu [.NET Core 2.x – podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy.</span><span class="sxs-lookup"><span data-stu-id="9d671-118">See [.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems.</span></span>

<span data-ttu-id="9d671-119">V tématu [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy.</span><span class="sxs-lookup"><span data-stu-id="9d671-119">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="9d671-120">.NET core závislosti</span><span class="sxs-lookup"><span data-stu-id="9d671-120">.NET Core dependencies</span></span>

<span data-ttu-id="9d671-121">.NET core 1.1 a starší verze vyžadují Visual C++ Redistributable při spuštění na verzích Windows starších než Windows 10 a Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="9d671-121">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="9d671-122">Tuto závislost automaticky instalovaný s verzí instalačního programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d671-122">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="9d671-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musí ručně nainstalovat při:</span><span class="sxs-lookup"><span data-stu-id="9d671-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="9d671-124">Instalaci .NET Core s [skript instalačního programu](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="9d671-124">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="9d671-125">Nasazení nezávislý aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d671-125">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="9d671-126">Vytváření produktu ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="9d671-126">Building the product from source.</span></span>
* <span data-ttu-id="9d671-127">Instalaci .NET Core prostřednictvím *.zip* souboru.</span><span class="sxs-lookup"><span data-stu-id="9d671-127">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="9d671-128">To může zahrnovat servery sestavení nebo položek konfigurace nebo disku CD.</span><span class="sxs-lookup"><span data-stu-id="9d671-128">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="9d671-129">*Windows 8.1 a starší verze, nebo Windows Server 2012 R2 a starších verzích:* Ujistěte se, že je aktuální instalace systému Windows a zahrnuje [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) který lze nainstalovat pomocí služby Windows Update.</span><span class="sxs-lookup"><span data-stu-id="9d671-129">*For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:* Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) which can be installed through Windows Update.</span></span> <span data-ttu-id="9d671-130">Pokud nemáte k dispozici tato aktualizace instalována, zobrazí chybu při spuštění aplikace .NET Core takto: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`.</span><span class="sxs-lookup"><span data-stu-id="9d671-130">If you don't have this update installed, you'll see an error when you launch a .NET Core application like the following: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="9d671-131">Požadavky s Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9d671-131">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="9d671-132">K vývoji aplikací .NET Core pomocí sady .NET Core SDK můžete použít všechny editor.</span><span class="sxs-lookup"><span data-stu-id="9d671-132">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="9d671-133">[Visual Studio 2017](#visual-studio-2017) poskytuje integrované vývojové prostředí pro aplikace .NET Core v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9d671-133">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="9d671-134">Další informace o změnách ve Visual Studio 2017 v [poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="9d671-134">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="9d671-135">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="9d671-135">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="9d671-136">K vývoji aplikací .NET Core 2.x ve Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="9d671-136">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="9d671-137">[Stáhněte a nainstalujte Visual Studio 2017 verze 15.3.0 nebo vyšší](/visualstudio/install/install-visual-studio) s **vývoj pro různé platformy .NET Core** zatížení (v **ostatní modulové** část) vybrané.</span><span class="sxs-lookup"><span data-stu-id="9d671-137">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Snímek obrazovky nástroje Visual Studio 2017 instalace se zatížením "Vývoj pro různé platformy .NET Core" vybrali](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="9d671-139">Po **vývoj pro různé platformy .NET Core** je nainstalovaná sada nástrojů, Visual Studio 2017 používá .NET Core 1.x ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="9d671-139">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="9d671-140">Instalace .NET Core 2.x SDK získat podporu 2.x .NET Core v Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="9d671-140">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="9d671-141">Nainstalujte [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="9d671-141">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="9d671-142">Změňte cíl existující nebo nové projekty 1.x .NET Core na .NET Core 2.x pomocí následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="9d671-142">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="9d671-143">Na **projektu** nabídce zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="9d671-143">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="9d671-144">V **cílové rozhraní** výběr nabídky, nastavte hodnotu na **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="9d671-144">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Snímek obrazovky nástroje Visual Studio 2017 aplikace projektu vlastnost s nabídky ".NET Core 2.0" Target framework vybrané položce](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="9d671-146">Jednou .NET Core 2.x SDK je nainstalovaná, Visual Studio 2017 používá rozhraní .NET Core SDK 2.x ve výchozím nastavení a podporuje následující akce:</span><span class="sxs-lookup"><span data-stu-id="9d671-146">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

* <span data-ttu-id="9d671-147">Otevřete, sestavte a spusťte existující projekty 1.x .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d671-147">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="9d671-148">Změňte cíl .NET Core 1.x projekty 2.x, sestavení a spuštění .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d671-148">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
* <span data-ttu-id="9d671-149">Vytvořte nové projekty 2.x .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d671-149">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9d671-150">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="9d671-150">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="9d671-151">Vývoj aplikací .NET Core 1.x v sadě Visual Studio, [stáhněte a nainstalujte Visual Studio 2017 RTM (verze 15.0.26228.4) nebo vyšší](/visualstudio/install/install-visual-studio) s **"Vývoj pro různé platformy .NET Core"** zatížení (v  **Ostatní modulové** část) vybrané.</span><span class="sxs-lookup"><span data-stu-id="9d671-151">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Snímek obrazovky nástroje Visual Studio 2017 instalace se zatížením "Vývoj pro různé platformy .NET Core" vybrali](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="9d671-153">Je možné použít Visual Studio 2015 pro vývoj 1.x .NET Core, ale nedoporučuje z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="9d671-153">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="9d671-154">Nástrojů .NET Core je ve verzi preview, což není podporováno.</span><span class="sxs-lookup"><span data-stu-id="9d671-154">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="9d671-155">Projekty jsou založené na souboru project.json, který je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="9d671-155">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="9d671-156">Další informace o změnách formátu projektu najdete v tématu [přehled změn](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="9d671-156">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

> [!TIP]
> <span data-ttu-id="9d671-157">Chcete-li ověřit vaši verzi Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="9d671-157">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="9d671-158">Na **pomoci** nabídce zvolte **o sadě Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9d671-158">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="9d671-159">V **o sadě Microsoft Visual Studio** dialogové okno, zkontrolujte číslo verze.</span><span class="sxs-lookup"><span data-stu-id="9d671-159">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="9d671-160">Pro aplikace .NET Core 2.1 Preview 1, Visual Studio 2017 15,6 operací verze Preview 6 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9d671-160">For .NET Core 2.1 Preview 1 apps, Visual Studio 2017 version 15.6 Preview 6 or higher.</span></span>
>   * <span data-ttu-id="9d671-161">Pro aplikace .NET Core 2.0, Visual Studio 2017 verze 15.3 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9d671-161">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="9d671-162">Pro aplikace .NET Core 1.x, Visual Studio 2017 verze 15,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9d671-162">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
