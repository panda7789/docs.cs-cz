---
title: 'Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework'
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c558c744ee31d8e8299da87e6c2715875dd2dcd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973561"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="fc519-102">Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc519-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="fc519-103">Uživatelé můžou [nainstalovat](https://docs.microsoft.com/dotnet/framework/install) a spuštění několika verzí rozhraní .NET Framework na svých počítačích.</span><span class="sxs-lookup"><span data-stu-id="fc519-103">Users can [install](https://docs.microsoft.com/dotnet/framework/install) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="fc519-104">Při vývoji nebo nasazení vaší aplikace, můžete potřebovat vědět, jaké verze rozhraní .NET Framework jsou nainstalovány v počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="fc519-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span>

<span data-ttu-id="fc519-105">Rozhraní .NET Framework obsahuje dvě hlavní součásti, které mají samostatné verze:</span><span class="sxs-lookup"><span data-stu-id="fc519-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="fc519-106">Sadu sestavení, která jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc519-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="fc519-107">Rozhraní .NET Framework a sestavení sdílejí stejné číslo verze.</span><span class="sxs-lookup"><span data-stu-id="fc519-107">The .NET Framework and assemblies share the same version number.</span></span>

- <span data-ttu-id="fc519-108">Modul CLR (CLR), jež spravuje a spouští kód vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc519-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="fc519-109">CLR je identifikováno svým vlastním číslem verze (viz [verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="fc519-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="fc519-110">Každá nová verze rozhraní .NET Framework zachovává funkce předchozích verzí a přidává nové funkce.</span><span class="sxs-lookup"><span data-stu-id="fc519-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="fc519-111">Více verzí rozhraní .NET Framework v jednom počítači můžete načíst ve stejnou dobu, což znamená, že můžete nainstalovat rozhraní .NET Framework bez odinstalování předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="fc519-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="fc519-112">Obecně platí že byste neměli odinstalovávat předchozích verzích rozhraní .NET Framework, protože na konkrétní verzi může záviset aplikace, které používáte a mohou přestat fungovat, pokud je verze odebrána.</span><span class="sxs-lookup"><span data-stu-id="fc519-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="fc519-113">Existuje rozdíl mezi verzí rozhraní .NET Framework a verzi modulu CLR:</span><span class="sxs-lookup"><span data-stu-id="fc519-113">There is a difference between the .NET Framework version and the CLR version:</span></span>
> - <span data-ttu-id="fc519-114">Verze rozhraní .NET Framework je založená na sadu sestavení, které tvoří knihovny tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc519-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="fc519-115">Například zahrnují verze rozhraní .NET Framework 4.5, 4.6.1 a 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="fc519-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>
>- <span data-ttu-id="fc519-116">Verze CLR je založená na modulu runtime, na kterém aplikace rozhraní .NET Framework jsou spouštěny.</span><span class="sxs-lookup"><span data-stu-id="fc519-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="fc519-117">Jedna verze modulu CLR obvykle podporuje více verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc519-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="fc519-118">Například verze modulu CLR 4.0.30319. *xxxxx* podporuje rozhraní .NET Framework verze 4 prostřednictvím 4.5.2 a 4.0.30319.42000 podporuje od verze rozhraní .NET Framework 4.6 verze rozhraní .NET Framework verze CLR.</span><span class="sxs-lookup"><span data-stu-id="fc519-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2 and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>
>
> <span data-ttu-id="fc519-119">Další informace o verzích, najdete v části [rozhraní .NET Framework verze a závislosti](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="fc519-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>

<span data-ttu-id="fc519-120">Pokud chcete získat seznam verzí rozhraní .NET Framework nainstalované na počítači, máte přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="fc519-120">To get a list of the .NET Framework versions installed on a computer, you access the registry.</span></span> <span data-ttu-id="fc519-121">Editor registru můžete použít buď k zobrazení registru nebo ji dotazovat s pomocí kódu:</span><span class="sxs-lookup"><span data-stu-id="fc519-121">You can either use the Registry Editor to view the registry or use code to query it:</span></span>

- <span data-ttu-id="fc519-122">Najdete novější verze rozhraní .NET Framework (4.5 a novější):</span><span class="sxs-lookup"><span data-stu-id="fc519-122">Find newer .NET Framework versions (4.5 and later):</span></span>
  - [<span data-ttu-id="fc519-123">Pomocí Editoru registru vyhledejte verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc519-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)
  - [<span data-ttu-id="fc519-124">Použít kód k dotazování registru pro verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc519-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)
  - [<span data-ttu-id="fc519-125">Použití Powershellu k dotazování registru pro verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc519-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)
- <span data-ttu-id="fc519-126">Najít starší verze rozhraní .NET Framework (1&#8211;4):</span><span class="sxs-lookup"><span data-stu-id="fc519-126">Find older .NET Framework versions (1&#8211;4):</span></span>
  - [<span data-ttu-id="fc519-127">Pomocí Editoru registru vyhledejte verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc519-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
  - [<span data-ttu-id="fc519-128">Použít kód k dotazování registru pro verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc519-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)

<span data-ttu-id="fc519-129">Pokud chcete získat seznam verzí modulu CLR nainstalované v počítači, pomocí nástroje nebo kódu:</span><span class="sxs-lookup"><span data-stu-id="fc519-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>

- [<span data-ttu-id="fc519-130">Použití nástroje Clrver</span><span class="sxs-lookup"><span data-stu-id="fc519-130">Use the Clrver tool</span></span>](#clr_a)
- [<span data-ttu-id="fc519-131">Dotaz na třídu prostředí pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="fc519-131">Use code to query the Environment class</span></span>](#clr_b)

<span data-ttu-id="fc519-132">Informace o zjišťování nainstalovaných aktualizací pro každou verzi rozhraní .NET Framework najdete v tématu [jak: Zjištění nainstalovaných aktualizací rozhraní .NET Framework](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="fc519-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="fc519-133">Najít novější verze rozhraní .NET Framework (4.5 a novější)</span><span class="sxs-lookup"><span data-stu-id="fc519-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<a name="net_b"></a>

### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="fc519-134">Najít rozhraní .NET Framework verze 4.5 a vyšší v registru</span><span class="sxs-lookup"><span data-stu-id="fc519-134">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="fc519-135">Z **Start** nabídce zvolte **spustit**, zadejte *regedit*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc519-135">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="fc519-136">Musíte mít pověření správce, chcete-li spustit program regedit.</span><span class="sxs-lookup"><span data-stu-id="fc519-136">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="fc519-137">V editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="fc519-137">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="fc519-138">Pokud **úplné** podklíč není k dispozici a není k dispozici rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="fc519-138">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc519-139">**NET Framework Setup** složky v registru neodpovídá *není* nezačíná tečkou.</span><span class="sxs-lookup"><span data-stu-id="fc519-139">The **NET Framework Setup** folder in the registry does *not* begin with a period.</span></span>

3. <span data-ttu-id="fc519-140">Vyhledejte položku DWORD s názvem **vydání**.</span><span class="sxs-lookup"><span data-stu-id="fc519-140">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="fc519-141">Pokud existuje, pak je nutné rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="fc519-141">If it exists, then you have .NET Framework 4.5 or later versions installed.</span></span> <span data-ttu-id="fc519-142">Jeho hodnota je verze klíče, který odpovídá konkrétní verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc519-142">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="fc519-143">Na následujícím obrázku, například hodnoty **Release** položka je *378389*, což je verze klíč pro rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="fc519-143">In the following figure, for example, the value of the **Release** entry is *378389*, which is the release key for .NET Framework 4.5.</span></span>

     <span data-ttu-id="fc519-144">![Položky registru pro rozhraní .NET Framework 4.5](media/clr-installdir.png "položky registru pro rozhraní .NET Framework 4.5")</span><span class="sxs-lookup"><span data-stu-id="fc519-144">![Registry entry for the .NET Framework 4.5](media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="fc519-145">V následující tabulce jsou uvedeny hodnoty **vydání** typu DWORD v jednotlivých operačních systémech pro rozhraní .NET Framework 4.5 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="fc519-145">The following table lists the value of the **Release** DWORD on individual operating systems for .NET Framework 4.5 and later versions.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="fc519-146">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc519-146">.NET Framework version</span></span>|<span data-ttu-id="fc519-147">Hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="fc519-147">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="fc519-148">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="fc519-148">.NET Framework 4.5</span></span>|<span data-ttu-id="fc519-149">Všechny operační systémy Windows: 378389</span><span class="sxs-lookup"><span data-stu-id="fc519-149">All Windows operating systems: 378389</span></span>|
|<span data-ttu-id="fc519-150">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="fc519-150">.NET Framework 4.5.1</span></span>|<span data-ttu-id="fc519-151">Na Windows 8.1 a Windows Server 2012 R2: 378675</span><span class="sxs-lookup"><span data-stu-id="fc519-151">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="fc519-152">Na všechny ostatní Windows operační systémy: 378758</span><span class="sxs-lookup"><span data-stu-id="fc519-152">On all other Windows operating systems: 378758</span></span>|
|<span data-ttu-id="fc519-153">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="fc519-153">.NET Framework 4.5.2</span></span>|<span data-ttu-id="fc519-154">Všechny operační systémy Windows: 379893</span><span class="sxs-lookup"><span data-stu-id="fc519-154">All Windows operating systems: 379893</span></span>|
|<span data-ttu-id="fc519-155">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="fc519-155">.NET Framework 4.6</span></span>|<span data-ttu-id="fc519-156">On Windows 10: 393295</span><span class="sxs-lookup"><span data-stu-id="fc519-156">On Windows 10: 393295</span></span><br /><span data-ttu-id="fc519-157">Na všechny ostatní Windows operační systémy: 393297</span><span class="sxs-lookup"><span data-stu-id="fc519-157">On all other Windows operating systems: 393297</span></span>|
|<span data-ttu-id="fc519-158">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="fc519-158">.NET Framework 4.6.1</span></span>|<span data-ttu-id="fc519-159">V systémech Windows 10. listopadu Update: 394254</span><span class="sxs-lookup"><span data-stu-id="fc519-159">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="fc519-160">Na všechny ostatní Windows operačních systémů (včetně Windows 10): 394271</span><span class="sxs-lookup"><span data-stu-id="fc519-160">On all other Windows operating systems (including Windows 10): 394271</span></span>|
|<span data-ttu-id="fc519-161">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="fc519-161">.NET Framework 4.6.2</span></span>|<span data-ttu-id="fc519-162">V systému Windows 10 Anniversary Update a Windows Server 2016: 394802</span><span class="sxs-lookup"><span data-stu-id="fc519-162">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="fc519-163">Na všechny ostatní Windows operačních systémů (včetně jiných operačních systémech Windows 10): 394806</span><span class="sxs-lookup"><span data-stu-id="fc519-163">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span>|
|<span data-ttu-id="fc519-164">Rozhraní .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="fc519-164">.NET Framework 4.7</span></span>|<span data-ttu-id="fc519-165">Na Windows 10 Creators Update: 460798</span><span class="sxs-lookup"><span data-stu-id="fc519-165">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="fc519-166">Na všechny ostatní Windows operačních systémů (včetně jiných operačních systémech Windows 10): 460805</span><span class="sxs-lookup"><span data-stu-id="fc519-166">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span>|
|<span data-ttu-id="fc519-167">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="fc519-167">.NET Framework 4.7.1</span></span>|<span data-ttu-id="fc519-168">V systému Windows Server verze 1709 a Windows 10 Fall Creators Update: 461308</span><span class="sxs-lookup"><span data-stu-id="fc519-168">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="fc519-169">Na všechny ostatní Windows operačních systémů (včetně jiných operačních systémech Windows 10): 461310</span><span class="sxs-lookup"><span data-stu-id="fc519-169">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span>|
|<span data-ttu-id="fc519-170">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="fc519-170">.NET Framework 4.7.2</span></span>|<span data-ttu-id="fc519-171">Ve Windows 10. dubna 2018 Update a Windows Server verze 1803: 461808</span><span class="sxs-lookup"><span data-stu-id="fc519-171">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="fc519-172">Ve všech operačních systémech Windows než Windows 10. dubna 2018 Update a Windows Server verze 1803: 461814</span><span class="sxs-lookup"><span data-stu-id="fc519-172">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span>|
|<span data-ttu-id="fc519-173">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="fc519-173">.NET Framework 4.8</span></span>|<span data-ttu-id="fc519-174">Při aktualizaci Windows 10. května 2019: 528040</span><span class="sxs-lookup"><span data-stu-id="fc519-174">On Windows 10 May 2019 Update: 528040</span></span><br/><span data-ttu-id="fc519-175">Na všechny ostatní operační systémy Windows (včetně jiných operačních systémech Windows 10): 528049</span><span class="sxs-lookup"><span data-stu-id="fc519-175">On all others Windows operating systems (including other Windows 10 operating systems): 528049</span></span>|

<span data-ttu-id="fc519-176">Tyto hodnoty můžete použít takto:</span><span class="sxs-lookup"><span data-stu-id="fc519-176">You can use these values as follows:</span></span>

- <span data-ttu-id="fc519-177">K určení, zda konkrétní verzi rozhraní .NET Framework je nainstalována na konkrétní verzi operačního systému Windows, otestovat, jestli **vydání** hodnotu DWORD *rovna* hodnota uvedená ve v tabulce.</span><span class="sxs-lookup"><span data-stu-id="fc519-177">To determine whether a specific version of the .NET Framework is installed on a particular version of the Windows operating system, test whether the **Release** DWORD value is *equal to* the value listed in the table.</span></span> <span data-ttu-id="fc519-178">Například, pokud chcete zjistit, zda rozhraní .NET Framework 4.6 je k dispozici v systému Windows 10, test pro v **vydání** hodnotu *rovna* 393295.</span><span class="sxs-lookup"><span data-stu-id="fc519-178">For example, to determine whether .NET Framework 4.6 is present on a Windows 10 system, test for the a **Release** value that is *equal to* 393295.</span></span>

- <span data-ttu-id="fc519-179">Chcete-li zjistit, zda je k dispozici minimální verzi rozhraní .NET Framework, použijte menší **vydání** hodnotu DWORD pro tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="fc519-179">To determine whether a minimum version of the .NET Framework is present, use the smaller **RELEASE** DWORD value for that version.</span></span> <span data-ttu-id="fc519-180">Například pokud je aplikace spuštěná v rámci rozhraní .NET Framework 4.6 nebo novější verze, testování **vydání** hodnotu DWORD *větší než nebo rovna hodnotě* 393295.</span><span class="sxs-lookup"><span data-stu-id="fc519-180">For example, if your application runs under .NET Framework 4.6 or a later version, test for a **RELEASE** DWORD value that is *greater than or equal to* 393295.</span></span> <span data-ttu-id="fc519-181">Pro tabulku, která obsahuje pouze minimální **vydání** hodnotu DWORD pro každou verzi rozhraní .NET Framework naleznete v tématu [minimální hodnoty DWORD verze rozhraní .NET Framework 4.5 a novější verze](minimum-release-dword.md).</span><span class="sxs-lookup"><span data-stu-id="fc519-181">For a table that lists only the minimum **RELEASE** DWORD value for each .NET Framework version, see [The minimum values of the Release DWORD for .NET Framework 4.5 and later versions](minimum-release-dword.md).</span></span>

- <span data-ttu-id="fc519-182">Pokud chcete testovat více verzí, začněte tím, že testování na hodnotu, která je *větší než nebo rovna hodnotě* na menší hodnotu DWORD pro nejnovější verzi rozhraní .NET Framework a pak porovnat hodnotu s menší hodnotu DWORD pro každou po sobě jdoucích starší verze.</span><span class="sxs-lookup"><span data-stu-id="fc519-182">To test for multiple versions, begin by testing for a value that is *greater than or equal to* the smaller DWORD value for the latest .NET Framework version, and then compare the value with the smaller DWORD value for each successive earlier version.</span></span> <span data-ttu-id="fc519-183">Například pokud vaše aplikace vyžaduje rozhraní .NET Framework 4.7 nebo novější a chcete zjistit, konkrétní verzi rozhraní .NET Framework, které jsou k dispozici, spusťte testováním **vydání** hodnotu DWORD *víc než nebo rovno*  k 461808 (menší hodnota DWORD pro rozhraní .NET Framework 4.7.2).</span><span class="sxs-lookup"><span data-stu-id="fc519-183">For example, if your application requires .NET Framework 4.7 or later and you want to determine the specific version of .NET Framework present, start by testing for a **RELEASE** DWORD value that is *great than or equal to* to 461808 (the smaller DWORD value for .NET Framework 4.7.2).</span></span> <span data-ttu-id="fc519-184">Pak porovnat **vydání** hodnotu DWORD s menší hodnotu pro každou novější verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc519-184">Then compare the **RELEASE** DWORD value with the smaller value for each later .NET Framework version.</span></span> <span data-ttu-id="fc519-185">Pro tabulku, která obsahuje pouze minimální **vydání** hodnotu DWORD pro každou verzi rozhraní .NET Framework naleznete v tématu [minimální hodnoty DWORD verze rozhraní .NET Framework 4.5 a novější verze](minimum-release-dword.md).</span><span class="sxs-lookup"><span data-stu-id="fc519-185">For a table that lists only the minimum **RELEASE** DWORD value for each .NET Framework version, see [The minimum values of the Release DWORD for .NET Framework 4.5 and later versions](minimum-release-dword.md).</span></span>

<a name="net_d"></a>

### <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="fc519-186">Najít rozhraní .NET Framework verze 4.5 a vyšší s kódem</span><span class="sxs-lookup"><span data-stu-id="fc519-186">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="fc519-187">Použití <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> metody pro přístup k **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** podklíčů v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="fc519-187">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

    <span data-ttu-id="fc519-188">Existence **vydání** položku DWORD v **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** podklíč označuje, že je rozhraní .NET Framework 4.5 nebo novější verze počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="fc519-188">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span>

2. <span data-ttu-id="fc519-189">Zkontrolujte hodnotu **vydání** položku k určení Instalovatelné verze.</span><span class="sxs-lookup"><span data-stu-id="fc519-189">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="fc519-190">Aby dopřednou vyhledejte hodnotu větší než nebo rovno hodnota uvedená ve [tabulku verzí rozhraní .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="fc519-190">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="fc519-191">Následující příklad zkontroluje hodnotu vlastnosti **vydání** záznam v registru najít rozhraní .NET Framework 4.5 a novější verze, které jsou nainstalovány:</span><span class="sxs-lookup"><span data-stu-id="fc519-191">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="fc519-192">V tomto příkladu následuje doporučený postup pro kontrolu verzí:</span><span class="sxs-lookup"><span data-stu-id="fc519-192">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="fc519-193">Zkontroluje, zda hodnota **Release** položka je *větší než nebo rovna hodnotě* hodnotu klíče známé verze.</span><span class="sxs-lookup"><span data-stu-id="fc519-193">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="fc519-194">Zkontroluje, aby nejstarší verzi z nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="fc519-194">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a>

### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="fc519-195">Vyhledejte minimální požadovaná rozhraní .NET Framework verze (4.5 a novější) pomocí Powershellu</span><span class="sxs-lookup"><span data-stu-id="fc519-195">Check for a minimum-required .NET Framework version (4.5 and later) with PowerShell</span></span>

- <span data-ttu-id="fc519-196">Zkontrolovat hodnoty pomocí příkazů Powershellu **vydání** vstupu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** podklíči.</span><span class="sxs-lookup"><span data-stu-id="fc519-196">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="fc519-197">Následující příklady kontrolu hodnoty **vydání** položku k určení, zda rozhraní .NET Framework 4.6.2 nebo novější nainstalován.</span><span class="sxs-lookup"><span data-stu-id="fc519-197">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="fc519-198">Tento kód vrátí `True` je-li nainstalován a `False` jinak.</span><span class="sxs-lookup"><span data-stu-id="fc519-198">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 }
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

<span data-ttu-id="fc519-199">Vyhledat jinou verzi rozhraní .NET Framework minimální požadovaná, nahraďte *394802* v těchto příkladech se **vydání** hodnotu [tabulku verzí rozhraní .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="fc519-199">To check for a different minimum-required .NET Framework version, replace *394802* in these examples with a **Release** value from the [.NET Framework version table](#version_table).</span></span>

## <a name="find-older-net-framework-versions-182114"></a><span data-ttu-id="fc519-200">Najít starší verze rozhraní .NET Framework (1&#8211;4)</span><span class="sxs-lookup"><span data-stu-id="fc519-200">Find older .NET Framework versions (1&#8211;4)</span></span>

<a name="net_a"></a>

### <a name="find-net-framework-versions-182114-in-the-registry"></a><span data-ttu-id="fc519-201">Najít rozhraní .NET Framework verze 1&#8211;4 v registru</span><span class="sxs-lookup"><span data-stu-id="fc519-201">Find .NET Framework versions 1&#8211;4 in the registry</span></span>

1. <span data-ttu-id="fc519-202">Z **Start** nabídce zvolte **spustit**, zadejte *regedit*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc519-202">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="fc519-203">Musíte mít pověření správce, chcete-li spustit program regedit.</span><span class="sxs-lookup"><span data-stu-id="fc519-203">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="fc519-204">V editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="fc519-204">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>

    - <span data-ttu-id="fc519-205">Pro rozhraní .NET Framework verze 1.1 až 3.5, každý nainstalovaná verze je uveden jako podklíč **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** podklíči.</span><span class="sxs-lookup"><span data-stu-id="fc519-205">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="fc519-206">Například **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="fc519-206">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="fc519-207">Číslo verze je uloženo jako hodnota v podklíči verze **verze** položka.</span><span class="sxs-lookup"><span data-stu-id="fc519-207">The version number is stored as a value in the version subkey's **Version** entry.</span></span>

    - <span data-ttu-id="fc519-208">Pro rozhraní .NET Framework 4 **verze** položka je v části **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** podklíči **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\NET Framework Setup\NDP\v4.0\Full** podklíče, nebo pod oběma podklíči.</span><span class="sxs-lookup"><span data-stu-id="fc519-208">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc519-209">**NET Framework Setup** složky v registru nezačíná tečkou.</span><span class="sxs-lookup"><span data-stu-id="fc519-209">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="fc519-210">Následující obrázek znázorňuje podklíče a jeho **verze** položku pro rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="fc519-210">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="fc519-211">![Položky registru pro rozhraní .NET Framework 3.5. ](media/net-4-and-earlier.png "Rozhraní .NET framework 3.5 a starší")</span><span class="sxs-lookup"><span data-stu-id="fc519-211">![The registry entry for the .NET Framework 3.5.](media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a>

### <a name="find-net-framework-versions-182114-with-code"></a><span data-ttu-id="fc519-212">Najít rozhraní .NET Framework verze 1&#8211;4 s kódem</span><span class="sxs-lookup"><span data-stu-id="fc519-212">Find .NET Framework versions 1&#8211;4 with code</span></span>

- <span data-ttu-id="fc519-213">Použití <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> třídy k přístupu **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** podklíčů v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="fc519-213">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="fc519-214">Následující příklad vyhledá rozhraní .NET Framework 1&#8211;4 verze, které jsou nainstalovány:</span><span class="sxs-lookup"><span data-stu-id="fc519-214">The following example finds the .NET Framework 1&#8211;4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="fc519-215">Najít verze CLR</span><span class="sxs-lookup"><span data-stu-id="fc519-215">Find CLR versions</span></span>

<a name="clr_a"></a>

### <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="fc519-216">Vyhledání aktuální verze modulu CLR s Clrver.exe</span><span class="sxs-lookup"><span data-stu-id="fc519-216">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="fc519-217">Použití [nástroj CLR Version (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) k určení, jaké verze modulu CLR jsou nainstalovány v počítači:</span><span class="sxs-lookup"><span data-stu-id="fc519-217">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="fc519-218">Z [Developer Command Prompt pro sadu Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), zadejte `clrver`.</span><span class="sxs-lookup"><span data-stu-id="fc519-218">From a [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), enter `clrver`.</span></span>

    <span data-ttu-id="fc519-219">Ukázkový výstup:</span><span class="sxs-lookup"><span data-stu-id="fc519-219">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="fc519-220">Vyhledání aktuální verze modulu CLR s třídou prostředí</span><span class="sxs-lookup"><span data-stu-id="fc519-220">Find the current CLR version with the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fc519-221">Pro rozhraní .NET Framework 4.5 a novější verze, nepoužívejte <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost zjistit verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="fc519-221">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="fc519-222">Místo toho dotazu registru, jak je popsáno v [najít rozhraní .NET Framework verze 4.5 a vyšší s kódem](#net_d).</span><span class="sxs-lookup"><span data-stu-id="fc519-222">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="fc519-223">Dotaz <xref:System.Environment.Version?displayProperty=nameWithType> vlastnost pro načtení <xref:System.Version> objektu.</span><span class="sxs-lookup"><span data-stu-id="fc519-223">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

    <span data-ttu-id="fc519-224">Vrácený `System.Version` objekt určuje verzi modulu runtime, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="fc519-224">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="fc519-225">Nevrací se verze sestavení ani jiné verze modulu runtime, který byl nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="fc519-225">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="fc519-226">Pro rozhraní .NET Framework verze 4, 4.5, 4.5.1 a 4.5.2, řetězcovou reprezentaci vráceného <xref:System.Version> objektu má tvar 4.0.30319. *xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="fc519-226">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*.</span></span> <span data-ttu-id="fc519-227">Pro rozhraní .NET Framework 4.6 a novějším má formulář 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="fc519-227">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

2. <span data-ttu-id="fc519-228">Až budete mít `Version` objektu, dotaz následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fc519-228">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="fc519-229">Pro hlavní verzi identifikátor (například *4* pro verzi 4.0), použijte <xref:System.Version.Major%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fc519-229">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="fc519-230">Nezletilý release identifikátor (například *0* pro verzi 4.0), použijte <xref:System.Version.Minor%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fc519-230">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="fc519-231">Pro celého řetězci verze (například *4.0.30319.18010*), použijte <xref:System.Version.ToString%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="fc519-231">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fc519-232">Tato metoda vrátí jednu hodnotu, která odpovídá verzi modulu runtime, který se spouští kód.</span><span class="sxs-lookup"><span data-stu-id="fc519-232">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="fc519-233">Nevrací se verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="fc519-233">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

<span data-ttu-id="fc519-234">V následujícím příkladu <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro načtení informací o verzi modulu CLR:</span><span class="sxs-lookup"><span data-stu-id="fc519-234">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="fc519-235">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc519-235">See also</span></span>

- [<span data-ttu-id="fc519-236">Postupy: Zjištění nainstalovaných aktualizací rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc519-236">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="fc519-237">Instalace rozhraní .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="fc519-237">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="fc519-238">Rozhraní .NET framework verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="fc519-238">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
