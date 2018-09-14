---
title: Předpoklady pro .NET Core ve Windows
description: Informace v závislosti na vaší Windows potřebujete počítač pro vývoj a spouštění aplikací .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 08/31/2018
ms.openlocfilehash: 63c0de2b413f38458dba89506f4070760b3f53f8
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594760"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="9e681-103">Předpoklady pro .NET Core ve Windows</span><span class="sxs-lookup"><span data-stu-id="9e681-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="9e681-104">Tento článek popisuje závislosti, které potřebujete pro vývoj aplikací .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="9e681-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="9e681-105">Podporované verze operačního systému a závislostech, které následují platí na tři způsoby, jak vyvíjet aplikace .NET Core ve Windows:</span><span class="sxs-lookup"><span data-stu-id="9e681-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="9e681-106">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="9e681-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="9e681-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9e681-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="9e681-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9e681-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="9e681-109">.NET core podporované verze Windows</span><span class="sxs-lookup"><span data-stu-id="9e681-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="9e681-110">.NET core je podporována v následujících verzích:</span><span class="sxs-lookup"><span data-stu-id="9e681-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="9e681-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="9e681-111">Windows 7 SP1</span></span>
* <span data-ttu-id="9e681-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="9e681-112">Windows 8.1</span></span>
* <span data-ttu-id="9e681-113">Windows 10 Anniversary Update (verze 1607) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="9e681-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="9e681-114">Windows Server 2008 R2 SP1 (plnou instalaci systému Server nebo Server Core)</span><span class="sxs-lookup"><span data-stu-id="9e681-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="9e681-115">Windows Server 2012 SP1 (plnou instalaci systému Server nebo Server Core)</span><span class="sxs-lookup"><span data-stu-id="9e681-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="9e681-116">Windows Server 2012 R2 (úplná Server nebo Server Core)</span><span class="sxs-lookup"><span data-stu-id="9e681-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="9e681-117">Windows Server 2016 nebo novější verze (plnou instalaci systému Server, Server Core nebo Nano Server)</span><span class="sxs-lookup"><span data-stu-id="9e681-117">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="9e681-118">.NET core podporované operační systémy</span><span class="sxs-lookup"><span data-stu-id="9e681-118">.NET Core supported operating systems</span></span>

<span data-ttu-id="9e681-119">Následující články obsahují úplný seznam operačních systémů nepodporuje .NET Core na verze:</span><span class="sxs-lookup"><span data-stu-id="9e681-119">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="9e681-120">.NET core 2.1 – podporované verze operačního systému</span><span class="sxs-lookup"><span data-stu-id="9e681-120">.NET Core 2.1 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="9e681-121">.NET core 2.0 – podporované verze operačního systému</span><span class="sxs-lookup"><span data-stu-id="9e681-121">.NET Core 2.0 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [<span data-ttu-id="9e681-122">.NET core 1.x – verze podporovaný operační systém</span><span class="sxs-lookup"><span data-stu-id="9e681-122">.NET Core 1.x - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

## <a name="net-core-dependencies"></a><span data-ttu-id="9e681-123">.NET core závislosti</span><span class="sxs-lookup"><span data-stu-id="9e681-123">.NET Core dependencies</span></span>

<span data-ttu-id="9e681-124">Při spuštění na verzích Windows starších než Windows 10 a Windows serveru 2016 vyžadují Visual C++ Redistributable .NET core 1.1 a staršími verzemi.</span><span class="sxs-lookup"><span data-stu-id="9e681-124">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="9e681-125">Tato závislost je automaticky nainstalován pomocí instalačního programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e681-125">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="9e681-126">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musí ručně doinstalovat při:</span><span class="sxs-lookup"><span data-stu-id="9e681-126">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="9e681-127">Instalace .NET Core s [skript instalačního programu](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="9e681-127">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="9e681-128">Nasazení samostatné aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e681-128">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="9e681-129">Sestavení produktu ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="9e681-129">Building the product from source.</span></span>
* <span data-ttu-id="9e681-130">Instalace .NET Core prostřednictvím *ZIP* souboru.</span><span class="sxs-lookup"><span data-stu-id="9e681-130">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="9e681-131">To může zahrnovat servery sestavení/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="9e681-131">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="9e681-132">**Pro Windows 8.1 a starší verze, nebo Windows Server 2012 R2 a dřívějších verzích:**</span><span class="sxs-lookup"><span data-stu-id="9e681-132">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="9e681-133">Ujistěte se, že instalace systému Windows je aktuální a zahrnuje [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), kterou je možné nainstalovat prostřednictvím služby Windows Update.</span><span class="sxs-lookup"><span data-stu-id="9e681-133">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="9e681-134">Pokud nemáte k dispozici tato aktualizace instalována, zobrazí se vám chyba následujícím postupem při spuštění aplikace rozhraní .NET Core: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="9e681-134">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="9e681-135">**Pro Windows 7 nebo Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="9e681-135">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="9e681-136">Kromě KB2999226, ujistěte se, že budete mít taky [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) nainstalované.</span><span class="sxs-lookup"><span data-stu-id="9e681-136">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="9e681-137">Pokud nemáte k dispozici tato aktualizace instalována, zobrazí se zpráva podobná následující při spuštění aplikace rozhraní .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="9e681-137">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="9e681-138">Požadavky sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9e681-138">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="9e681-139">Můžete použít libovolný editor k vývoji aplikací .NET Core pomocí sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="9e681-139">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="9e681-140">Visual Studio 2017 poskytuje integrované vývojové prostředí pro aplikace .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="9e681-140">Visual Studio 2017 provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="9e681-141">Další informace o změnách v sadě Visual Studio 2017 v [poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="9e681-141">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9e681-142">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="9e681-142">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="9e681-143">Můžete vyvíjet aplikace .NET Core 2.1 v sadě Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="9e681-143">To develop .NET Core 2.1 apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="9e681-144">[Stažení a instalace sady Visual Studio 2017 verze 15.7.0 nebo vyšší](/visualstudio/install/install-visual-studio) s **vývoj pro různé platformy .NET Core** úloh (v **další sady nástrojů** části) vybrané.</span><span class="sxs-lookup"><span data-stu-id="9e681-144">[Download and install Visual Studio 2017 version 15.7.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Instalace – snímek obrazovky sady Visual Studio 2017 s vybranou úlohou "Vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-15-8-workloads.jpg)

<span data-ttu-id="9e681-146">Po **vývoj pro různé platformy .NET Core** sada nástrojů je ve výchozím nastavení nainstalované, Visual Studio 2017 15.7 používá .NET Core 2.0 SDK a Visual Studio 2017 15.8 používá sadu SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="9e681-146">After the **.NET Core cross-platform development** toolset is installed, by default, Visual Studio 2017 15.7 uses .NET Core 2.0 SDK and Visual Studio 2017 15.8 uses 2.1 SDK.</span></span>

 2. <span data-ttu-id="9e681-147">Pokud používáte Visual Studio 2017 15.7, nainstalujte [sady SDK .NET Core 2.1](https://www.microsoft.com/net/download/core) nebo upgrade na Visual Studio 2017 15.8.</span><span class="sxs-lookup"><span data-stu-id="9e681-147">If you're using Visual Studio 2017 15.7, install the [.NET Core 2.1 SDK](https://www.microsoft.com/net/download/core) or upgrade to Visual Studio 2017 15.8.</span></span>

 3. <span data-ttu-id="9e681-148">Změnit cíl existující nebo nové projekty .NET Core na .NET Core 2.1 pomocí následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="9e681-148">Retarget existing or new .NET Core projects to .NET Core 2.1 using the following instructions:</span></span>
    * <span data-ttu-id="9e681-149">Na **projektu** nabídce zvolit **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="9e681-149">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="9e681-150">V **Cílová architektura** nabídce pro výběr, nastavte hodnotu na **.NET Core 2.1**.</span><span class="sxs-lookup"><span data-stu-id="9e681-150">In the **Target framework** selection menu, set the value to **.NET Core 2.1**.</span></span>

![Snímek obrazovky sady Visual Studio 2017 aplikace vlastnost projektu pomocí nabídky ".NET Core 2.0" Target framework vybrané položky](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="9e681-152">Jakmile budete mít nakonfigurované pomocí sady SDK .NET Core 2.1 sady Visual Studio, můžete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="9e681-152">Once you have Visual Studio configured with .NET Core 2.1 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="9e681-153">Otevřete, sestavte a spusťte existující projekty .NET Core 1.x a 2.x.</span><span class="sxs-lookup"><span data-stu-id="9e681-153">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="9e681-154">Změnit cíl .NET Core 1.x a 2.0 projekty .NET Core 2.1, sestavit a spustit.</span><span class="sxs-lookup"><span data-stu-id="9e681-154">Retarget .NET Core 1.x and 2.0 projects to .NET Core 2.1, build, and run.</span></span>
* <span data-ttu-id="9e681-155">Vytvořte nové projekty .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="9e681-155">Create new .NET Core 2.1 projects.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9e681-156">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="9e681-156">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="9e681-157">Můžete vyvíjet aplikace .NET Core 2.0 v sadě Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="9e681-157">To develop .NET Core 2.0 apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="9e681-158">[Stáhněte a nainstalujte Visual Studio 2017 verze 15.3.0 nebo vyšší](/visualstudio/install/install-visual-studio) s **vývoj pro různé platformy .NET Core** úloh (v **další sady nástrojů** části) vybrané.</span><span class="sxs-lookup"><span data-stu-id="9e681-158">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Instalace – snímek obrazovky sady Visual Studio 2017 s vybranou úlohou "Vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="9e681-160">Po **vývoj pro různé platformy .NET Core** je nainstalovaná sada nástrojů, Visual Studio 2017 používá .NET Core 1.x ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="9e681-160">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="9e681-161">Instalace .NET Core 2.0 SDK potřebujete podporu .NET Core 2.0 v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="9e681-161">Install the .NET Core 2.0 SDK to get .NET Core 2.0 support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="9e681-162">Nainstalujte [.NET Core 2.0 SDK](https://www.microsoft.com/net/download/dotnet-core/2.0).</span><span class="sxs-lookup"><span data-stu-id="9e681-162">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/download/dotnet-core/2.0).</span></span>
 3. <span data-ttu-id="9e681-163">Změnit cíl stávajícího nebo nového .NET Core 1.x projekty .NET Core 2.0 pomocí následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="9e681-163">Retarget existing or new .NET Core 1.x projects to .NET Core 2.0 using the following instructions:</span></span>
    * <span data-ttu-id="9e681-164">Na **projektu** nabídce zvolit **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="9e681-164">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="9e681-165">V **Cílová architektura** nabídce pro výběr, nastavte hodnotu na **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="9e681-165">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Snímek obrazovky sady Visual Studio 2017 aplikace vlastnost projektu pomocí nabídky ".NET Core 2.0" Target framework vybrané položky](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="9e681-167">Po instalaci rozhraní .NET Core 2.0 SDK je Visual Studio 2017 ve výchozím nastavení používá rozhraní .NET Core SDK 2.0 a podporuje následující akce:</span><span class="sxs-lookup"><span data-stu-id="9e681-167">Once the .NET Core 2.0 SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.0 by default, and supports the following actions:</span></span>

* <span data-ttu-id="9e681-168">Otevřete, sestavte a spusťte existující projekty .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="9e681-168">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="9e681-169">Změnit cíl projektů .NET Core 1.x do .NET Core 2.0, sestavení a spusťte.</span><span class="sxs-lookup"><span data-stu-id="9e681-169">Retarget .NET Core 1.x projects to .NET Core 2.0, build, and run.</span></span>
* <span data-ttu-id="9e681-170">Vytvořte nové projekty .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="9e681-170">Create new .NET Core 2.0 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9e681-171">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="9e681-171">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="9e681-172">Můžete vyvíjet aplikace .NET Core 1.x v sadě Visual Studio [stáhnout a nainstalovat sadu Visual Studio 2017](/visualstudio/install/install-visual-studio) s **"Vývoj pro různé platformy .NET Core"** úloh (v **další sady nástrojů**části) vybrané.</span><span class="sxs-lookup"><span data-stu-id="9e681-172">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Instalace – snímek obrazovky sady Visual Studio 2017 s vybranou úlohou "Vývoj pro různé platformy .NET Core"](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="9e681-174">Je možné použít Visual Studio 2015 pro vývoj v .NET Core 1.x, ale nedoporučuje z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="9e681-174">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="9e681-175">Nástroje .NET Core je verze preview, což není podporováno.</span><span class="sxs-lookup"><span data-stu-id="9e681-175">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="9e681-176">Projekty, které jsou založeny na project.json, který je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="9e681-176">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="9e681-177">Další informace o změnách formát projektu naleznete v tématu [podrobný přehled změn](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="9e681-177">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="9e681-178">Pokud chcete ověřit vaši verzi sady Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="9e681-178">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="9e681-179">Na **pomáhají** nabídce zvolte **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9e681-179">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="9e681-180">V **o Microsoft Visual Studio** dialogového okna, zkontrolujte číslo verze.</span><span class="sxs-lookup"><span data-stu-id="9e681-180">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="9e681-181">Pro aplikace .NET Core 2.2 ve verzi Preview 1, Visual Studio 2017 (aktuálně ve verzi Preview) verzi 15.9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9e681-181">For .NET Core 2.2 Preview 1 apps, Visual Studio 2017 version 15.9 (currently in Preview) or higher.</span></span>
>   * <span data-ttu-id="9e681-182">Pro aplikace .NET Core 2.1, Visual Studio 2017 verze 15.7 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="9e681-182">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="9e681-183">Pro aplikace .NET Core 2.0, Visual Studio 2017 verze 15.3 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="9e681-183">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="9e681-184">Pro aplikace .NET Core 1.x, Visual Studio 2017 verze 15,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9e681-184">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
