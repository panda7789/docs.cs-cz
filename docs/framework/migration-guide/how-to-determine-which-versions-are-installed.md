---
title: "Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: edd5a8e8cc32037d45d95d544f6eae5097d0c468
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="14261-102">Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="14261-102">How to: Determine Which .NET Framework Versions Are Installed</span></span>
<span data-ttu-id="14261-103">Uživatelé můžou instalovat a spuštění několika verzí rozhraní .NET Framework na svých počítačích.</span><span class="sxs-lookup"><span data-stu-id="14261-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="14261-104">Při vývoji nebo nasazení aplikace, může být potřeba vědět, jaké verze rozhraní .NET Framework, které jsou nainstalovány v počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="14261-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="14261-105">Všimněte si, že rozhraní .NET Framework obsahuje dvě hlavní komponenty, které jsou samostatně verzí:</span><span class="sxs-lookup"><span data-stu-id="14261-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="14261-106">Sadu sestavení, která jsou kolekce typů a prostředky, které poskytují funkce pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="14261-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="14261-107">Rozhraní .NET Framework a sestavení sdílet stejné číslo verze.</span><span class="sxs-lookup"><span data-stu-id="14261-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="14261-108">Modul CLR (CLR), který spravuje a spouští kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="14261-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="14261-109">Modul CLR je určený podle čísla svou vlastní verzi (viz [verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="14261-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="14261-110">Chcete-li získat přesné seznam verze rozhraní .NET Framework nainstalované v počítači, můžete zobrazit registru nebo v registru v kódu:</span><span class="sxs-lookup"><span data-stu-id="14261-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="14261-111">Zobrazení registru (verze 1-4)</span><span class="sxs-lookup"><span data-stu-id="14261-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="14261-112">Zobrazení registru (verze 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="14261-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="14261-113">Pomocí kódu v registru (verze 1-4)</span><span class="sxs-lookup"><span data-stu-id="14261-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="14261-114">Pomocí kódu v registru (verze 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="14261-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="14261-115">Pomocí prostředí PowerShell v registru (verze 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="14261-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  
  
 <span data-ttu-id="14261-116">K vyhledání verze CLR, můžete použít nástroj nebo kódu:</span><span class="sxs-lookup"><span data-stu-id="14261-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="14261-117">Pomocí nástroje Clrver</span><span class="sxs-lookup"><span data-stu-id="14261-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="14261-118">Pomocí kódu k dotazování System.Environment – třída</span><span class="sxs-lookup"><span data-stu-id="14261-118">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="14261-119">Informace o zjišťování nainstalovaných aktualizací pro každou verzi rozhraní .NET Framework najdete v tématu [postupy: určení rozhraní .NET Framework aktualizace jsou nainstalované](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="14261-119">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="14261-120">Informace o instalaci rozhraní .NET Framework najdete v tématu [instalaci rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="14261-120">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="14261-121">Najít rozhraní .NET Framework verze zobrazením registru (rozhraní .NET Framework 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="14261-121">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="14261-122">Na **spustit** nabídce zvolte **spustit**.</span><span class="sxs-lookup"><span data-stu-id="14261-122">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="14261-123">V **otevřete** zadejte **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="14261-123">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="14261-124">Ke spuštění souboru regedit.exe musíte mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="14261-124">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="14261-125">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="14261-125">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="14261-126">Nainstalované verze jsou uvedeny v podklíči NDP.</span><span class="sxs-lookup"><span data-stu-id="14261-126">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="14261-127">Číslo verze je uložené v **verze** položku.</span><span class="sxs-lookup"><span data-stu-id="14261-127">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="14261-128">Pro [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **verze** položka je v rámci klienta nebo úplné podklíčem (v NRP), nebo v obou podklíče.</span><span class="sxs-lookup"><span data-stu-id="14261-128">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="14261-129">Složka „NET Framework Setup“ v registru nezačíná tečkou.</span><span class="sxs-lookup"><span data-stu-id="14261-129">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="14261-130">Najít rozhraní .NET Framework verze zobrazením registru (rozhraní .NET Framework 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="14261-130">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="14261-131">Na **spustit** nabídce zvolte **spustit**.</span><span class="sxs-lookup"><span data-stu-id="14261-131">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="14261-132">V **otevřete** zadejte **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="14261-132">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="14261-133">Ke spuštění souboru regedit.exe musíte mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="14261-133">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="14261-134">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="14261-134">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="14261-135">Všimněte si, že cesta k `Full` podklíč obsahuje podklíč `Net Framework` místo `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="14261-135">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="14261-136">Pokud `Full` podklíč není k dispozici, pak nemají rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="14261-136">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="14261-137">Zkontrolujte hodnotu DWORD s názvem `Release`.</span><span class="sxs-lookup"><span data-stu-id="14261-137">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="14261-138">Existenci `Release` DWORD znamená, že [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější byl na tomto počítači nainstalován.</span><span class="sxs-lookup"><span data-stu-id="14261-138">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="14261-139">![Položky registru pro rozhraní .NET Framework 4.5. ] (../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="14261-139">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="14261-140">Hodnota `Release` DWORD označuje, která verze rozhraní .NET Framework je nainstalovaná.</span><span class="sxs-lookup"><span data-stu-id="14261-140">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    |<span data-ttu-id="14261-141">Hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="14261-141">Value of the Release DWORD</span></span>|<span data-ttu-id="14261-142">Version</span><span class="sxs-lookup"><span data-stu-id="14261-142">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="14261-143">378389</span><span class="sxs-lookup"><span data-stu-id="14261-143">378389</span></span>|<span data-ttu-id="14261-144">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="14261-144">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="14261-145">378675</span><span class="sxs-lookup"><span data-stu-id="14261-145">378675</span></span>|<span data-ttu-id="14261-146">Rozhraní .NET framework 4.5.1 nainstalované s Windows 8.1 nebo Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="14261-146">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="14261-147">378758</span><span class="sxs-lookup"><span data-stu-id="14261-147">378758</span></span>|<span data-ttu-id="14261-148">Rozhraní .NET framework 4.5.1 nainstalovaný na Windows 8, Windows 7 SP1 nebo Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="14261-148">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="14261-149">379893</span><span class="sxs-lookup"><span data-stu-id="14261-149">379893</span></span>|<span data-ttu-id="14261-150">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="14261-150">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="14261-151">V systémech Windows 10: 393295</span><span class="sxs-lookup"><span data-stu-id="14261-151">On Windows 10 systems: 393295</span></span><br /><br /> <span data-ttu-id="14261-152">Na všech ostatních verzí operačního systému: 393297</span><span class="sxs-lookup"><span data-stu-id="14261-152">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="14261-153">V systémech Windows 10 listopadu Update: 394254</span><span class="sxs-lookup"><span data-stu-id="14261-153">On Windows 10 November Update systems: 394254</span></span><br /><br /> <span data-ttu-id="14261-154">Na všech ostatních verzí operačního systému: 394271</span><span class="sxs-lookup"><span data-stu-id="14261-154">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="14261-155">Na Windows 10 Anniversary aktualizace: 394802</span><span class="sxs-lookup"><span data-stu-id="14261-155">On Windows 10 Anniversary Update: 394802</span></span><br /><br /> <span data-ttu-id="14261-156">Na všech ostatních verzí operačního systému: 394806</span><span class="sxs-lookup"><span data-stu-id="14261-156">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="14261-157">Na Windows 10 Creators aktualizace: 460798</span><span class="sxs-lookup"><span data-stu-id="14261-157">On Windows 10 Creators Update: 460798</span></span><br/><br/> <span data-ttu-id="14261-158">Na všech ostatních verzí operačního systému: 460805</span><span class="sxs-lookup"><span data-stu-id="14261-158">On all other OS versions: 460805</span></span> | <span data-ttu-id="14261-159">Rozhraní .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="14261-159">.NET Framework 4.7</span></span> |
    |<span data-ttu-id="14261-160">V systému Windows 10 spadají Creators aktualizace: 461308</span><span class="sxs-lookup"><span data-stu-id="14261-160">On Windows 10 Fall Creators Update: 461308</span></span><br/><br/> <span data-ttu-id="14261-161">Na všech ostatních verzí operačního systému: 461310</span><span class="sxs-lookup"><span data-stu-id="14261-161">On all other OS versions: 461310</span></span> | <span data-ttu-id="14261-162">Rozhraní .NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="14261-162">.NET Framework 4.7.1</span></span> |
<a name="net_c"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="14261-163">Vyhledání verze rozhraní .NET Framework podle v registru v kódu (rozhraní .NET Framework 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="14261-163">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="14261-164">Použití <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> třídy pro přístup k Software\Microsoft\NET Framework Setup\NDP\ podklíčem v HKEY_LOCAL_MACHINE v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="14261-164">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="14261-165">Následující kód ukazuje příklad tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="14261-165">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="14261-166">Tento kód nezobrazuje k zjištění [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější.</span><span class="sxs-lookup"><span data-stu-id="14261-166">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="14261-167">Zkontrolujte `Release` DWORD ke zjištění těchto verzí, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="14261-167">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="14261-168">Pro kód, který zjistí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější verze, najdete v další části v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="14261-168">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     <span data-ttu-id="14261-169">Vzorové postupy budou mít výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="14261-169">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="14261-170">Vyhledání verze rozhraní .NET Framework podle v registru v kódu (rozhraní .NET Framework 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="14261-170">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="14261-171">Existenci `Release` DWORD označuje, zda na počítači byla nainstalována rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="14261-171">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="14261-172">Hodnota klíčového slova označuje, že nainstalovaná verze.</span><span class="sxs-lookup"><span data-stu-id="14261-172">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="14261-173">Chcete-li zkontrolovat toto klíčové slovo, použijte <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> třídy pro přístup k Software\Microsoft\NET Framework Setup\NDP\v4\Full podklíčem v HKEY_LOCAL_MACHINE v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="14261-173">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="14261-174">Zkontrolujte hodnotu `Release` – klíčové slovo určení nainstalované verze.</span><span class="sxs-lookup"><span data-stu-id="14261-174">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="14261-175">Chcete-li být dopřednou, můžete zkontrolovat na hodnotu větší než nebo rovna hodnotě hodnoty uvedené v tabulce.</span><span class="sxs-lookup"><span data-stu-id="14261-175">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="14261-176">Tady jsou verze rozhraní .NET Framework a přidružených `Release` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="14261-176">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    |<span data-ttu-id="14261-177">Version</span><span class="sxs-lookup"><span data-stu-id="14261-177">Version</span></span>|<span data-ttu-id="14261-178">Hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="14261-178">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="14261-179">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="14261-179">.NET Framework 4.5</span></span>|<span data-ttu-id="14261-180">378389</span><span class="sxs-lookup"><span data-stu-id="14261-180">378389</span></span>|
    |<span data-ttu-id="14261-181">Rozhraní .NET framework 4.5.1 nainstalované s Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="14261-181">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="14261-182">378675</span><span class="sxs-lookup"><span data-stu-id="14261-182">378675</span></span>|
    |<span data-ttu-id="14261-183">Rozhraní .NET framework 4.5.1 nainstalovaný na Windows 8, Windows 7 SP1 nebo Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="14261-183">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="14261-184">378758</span><span class="sxs-lookup"><span data-stu-id="14261-184">378758</span></span>|
    |<span data-ttu-id="14261-185">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="14261-185">.NET Framework 4.5.2</span></span>|<span data-ttu-id="14261-186">379893</span><span class="sxs-lookup"><span data-stu-id="14261-186">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<span data-ttu-id="14261-187">nainstalovaná se systémem Windows 10</span><span class="sxs-lookup"><span data-stu-id="14261-187"> installed with Windows 10</span></span>|<span data-ttu-id="14261-188">393295</span><span class="sxs-lookup"><span data-stu-id="14261-188">393295</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<span data-ttu-id="14261-189">nainstalovaná na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="14261-189"> installed on all other Windows OS versions</span></span>|<span data-ttu-id="14261-190">393297</span><span class="sxs-lookup"><span data-stu-id="14261-190">393297</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<span data-ttu-id="14261-191">nainstalovat na Windows 10</span><span class="sxs-lookup"><span data-stu-id="14261-191"> installed on Windows 10</span></span>|<span data-ttu-id="14261-192">394254</span><span class="sxs-lookup"><span data-stu-id="14261-192">394254</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<span data-ttu-id="14261-193">nainstalovaná na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="14261-193"> installed on all other Windows OS versions</span></span>|<span data-ttu-id="14261-194">394271</span><span class="sxs-lookup"><span data-stu-id="14261-194">394271</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<span data-ttu-id="14261-195">nainstalovat na Windows 10 Anniversary aktualizace</span><span class="sxs-lookup"><span data-stu-id="14261-195"> installed on Windows 10 Anniversary Update</span></span>|<span data-ttu-id="14261-196">394802</span><span class="sxs-lookup"><span data-stu-id="14261-196">394802</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<span data-ttu-id="14261-197">nainstalovaná na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="14261-197"> installed on all other Windows OS versions</span></span>|<span data-ttu-id="14261-198">394806</span><span class="sxs-lookup"><span data-stu-id="14261-198">394806</span></span>|
    |<span data-ttu-id="14261-199">Rozhraní .NET framework 4.7 nainstalovaný na Windows 10 Creators Update</span><span class="sxs-lookup"><span data-stu-id="14261-199">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="14261-200">460798</span><span class="sxs-lookup"><span data-stu-id="14261-200">460798</span></span>|
    |<span data-ttu-id="14261-201">4.7 rozhraní .NET framework nainstalované na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="14261-201">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="14261-202">460805</span><span class="sxs-lookup"><span data-stu-id="14261-202">460805</span></span>|
    |<span data-ttu-id="14261-203">Rozhraní .NET framework 4.7.1 nainstalovaný na Windows 10 patří Creators aktualizace</span><span class="sxs-lookup"><span data-stu-id="14261-203">.NET Framework 4.7.1 installed on Windows 10 Fall Creators Update</span></span>|<span data-ttu-id="14261-204">461308</span><span class="sxs-lookup"><span data-stu-id="14261-204">461308</span></span>|
    |<span data-ttu-id="14261-205">Rozhraní .NET framework 4.7.1 nainstalované na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="14261-205">.NET Framework 4.7.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="14261-206">461310</span><span class="sxs-lookup"><span data-stu-id="14261-206">461310</span></span>|

     <span data-ttu-id="14261-207">Následující příklad kontroly `Release` hodnotu v registru na určit, zda [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo je nainstalovaná novější verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="14261-207">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     <span data-ttu-id="14261-208">Tento příklad dodržuje doporučený postup pro kontrolu verzí:</span><span class="sxs-lookup"><span data-stu-id="14261-208">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="14261-209">Zkontroluje, zda hodnota `Release` položka je *větší než nebo rovna hodnotě* hodnotu klíče známé verze.</span><span class="sxs-lookup"><span data-stu-id="14261-209">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="14261-210">Zkontroluje, aby nejstarší verze z nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="14261-210">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
#### <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a><span data-ttu-id="14261-211">Hledání minimální požadovaná verze rozhraní .NET Framework v registru v prostředí PowerShell (rozhraní .NET Framework 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="14261-211">To check for a minimum-required .NET Framework version by querying the registry in PowerShell (.NET Framework 4.5 and later)</span></span>

- <span data-ttu-id="14261-212">Následující příklad kontroluje hodnotu `Release` – klíčové slovo k určení zda rozhraní .NET Framework 4.6.2 nebo vyšší není nainstalovaná, bez ohledu na to verze operačního systému Windows (vrácení `True` Pokud je a `False` jinak).</span><span class="sxs-lookup"><span data-stu-id="14261-212">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed, regardless of Windows OS version (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    <span data-ttu-id="14261-213">Můžete nahradit `394802` v předchozím příkladu s jinou hodnotou z zkontrolujte pro jinou verzi rozhraní .NET Framework minimální požadovaná v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="14261-213">You can replace `394802` in the previous example with another value from the following table to check for a different minimum-required .NET Framework version.</span></span>
  
    |<span data-ttu-id="14261-214">Version</span><span class="sxs-lookup"><span data-stu-id="14261-214">Version</span></span>|<span data-ttu-id="14261-215">Minimální hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="14261-215">Minimum value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="14261-216">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="14261-216">.NET Framework 4.5</span></span>|<span data-ttu-id="14261-217">378389</span><span class="sxs-lookup"><span data-stu-id="14261-217">378389</span></span>|
    |<span data-ttu-id="14261-218">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="14261-218">.NET Framework 4.5.1</span></span>|<span data-ttu-id="14261-219">378675</span><span class="sxs-lookup"><span data-stu-id="14261-219">378675</span></span>|
    |<span data-ttu-id="14261-220">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="14261-220">.NET Framework 4.5.2</span></span>|<span data-ttu-id="14261-221">379893</span><span class="sxs-lookup"><span data-stu-id="14261-221">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|<span data-ttu-id="14261-222">393295</span><span class="sxs-lookup"><span data-stu-id="14261-222">393295</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|<span data-ttu-id="14261-223">394254</span><span class="sxs-lookup"><span data-stu-id="14261-223">394254</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|<span data-ttu-id="14261-224">394802</span><span class="sxs-lookup"><span data-stu-id="14261-224">394802</span></span>|
    |<span data-ttu-id="14261-225">Rozhraní .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="14261-225">.NET Framework 4.7</span></span>|<span data-ttu-id="14261-226">460798</span><span class="sxs-lookup"><span data-stu-id="14261-226">460798</span></span>|
    |<span data-ttu-id="14261-227">Rozhraní .NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="14261-227">.NET Framework 4.7.1</span></span>|<span data-ttu-id="14261-228">461308</span><span class="sxs-lookup"><span data-stu-id="14261-228">461308</span></span>|
    
<a name="clr_a"></a> 
#### <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="14261-229">Pomocí nástroje Clrver najít aktuální verzi modulu runtime</span><span class="sxs-lookup"><span data-stu-id="14261-229">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="14261-230">Chcete-li zjistit, jaké verze Common Language Runtime jsou nainstalovány v počítači, použijte nástroj CLR Version Tool (Clrver.exe).</span><span class="sxs-lookup"><span data-stu-id="14261-230">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="14261-231">Z Visual Studio příkazovém řádku zadejte `clrver`.</span><span class="sxs-lookup"><span data-stu-id="14261-231">From a Visual Studio Command Prompt, enter `clrver`.</span></span> <span data-ttu-id="14261-232">Tento příkaz vytváří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="14261-232">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="14261-233">Další informace o použití tohoto nástroje najdete v tématu [Clrver.exe (nástroj verze CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="14261-233">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
#### <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="14261-234">Vyhledání aktuální verze modulu runtime pomocí dotazu na třídu prostředí v kódu</span><span class="sxs-lookup"><span data-stu-id="14261-234">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="14261-235">Dotaz <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnosti načíst <xref:System.Version> objekt, který určuje verzi modulu runtime, který je aktuálně zpracovávaných kód.</span><span class="sxs-lookup"><span data-stu-id="14261-235">Query the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="14261-236">Můžete použít <xref:System.Version.Major%2A?displayProperty=nameWithType> vlastnost k získání identifikátor hlavní verzi (například "4" pro verzi 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> vlastnost k získání identifikátor dílčí verzi (například "0" pro verzi 4.0), nebo <xref:System.Object.ToString%2A?displayProperty=nameWithType> získat pro celou verzi – metoda řetězec (například "4.0.30319.18010", jak je znázorněno v následujícím kódu).</span><span class="sxs-lookup"><span data-stu-id="14261-236">You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="14261-237">Tato vlastnost vrátí jednu hodnotu, která odpovídá verzi modulu runtime, který momentálně spouští kód; nevrací se verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="14261-237">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="14261-238">Pro rozhraní .NET Framework verze 4, 4.5, 4.5.1 a 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost vrátí <xref:System.Version> objekt, jehož řetězcovou reprezentaci má tvar `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="14261-238">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="14261-239">Pro rozhraní .NET Framework 4.6 a novější, je formulář `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="14261-239">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="14261-240">Pro [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a novější, nedoporučujeme pomocí <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost zjistit verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="14261-240">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="14261-241">Místo toho doporučujeme zadat dotaz registru, jak je popsáno v [vyhledání verze rozhraní .NET Framework podle v registru v kódu (rozhraní .NET Framework 4.5 nebo novější)](#net_d) dříve v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="14261-241">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="14261-242">Tady je příklad dotazu <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro informace o verzi modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="14261-242">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property for runtime version information:</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     <span data-ttu-id="14261-243">Vzorové postupy budou mít výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="14261-243">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="14261-244">Viz také</span><span class="sxs-lookup"><span data-stu-id="14261-244">See Also</span></span>
 [<span data-ttu-id="14261-245">Postupy: zjištění nainstalovaných aktualizací rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="14261-245">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
 [<span data-ttu-id="14261-246">Nainstalujte rozhraní .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="14261-246">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
 [<span data-ttu-id="14261-247">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="14261-247">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)
