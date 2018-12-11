---
title: 'Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework'
ms.date: 04/10/2018
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
ms.openlocfilehash: 6b77775fdc7f552e6433e6364f153c5bde32d9e0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151041"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="8c4e8-102">Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8c4e8-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="8c4e8-103">Mohou uživatelé nainstalovat a spustit více verzí rozhraní .NET Framework na svých počítačích.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="8c4e8-104">Při vývoji nebo nasazení vaší aplikace, můžete potřebovat vědět, jaké verze rozhraní .NET Framework jsou nainstalovány v počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="8c4e8-105">Všimněte si, že rozhraní .NET Framework obsahuje dvě hlavní součásti, které mají samostatné verze:</span><span class="sxs-lookup"><span data-stu-id="8c4e8-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="8c4e8-106">Sadu sestavení, která jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="8c4e8-107">Rozhraní .NET Framework a sestavení sdílejí stejné číslo verze.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="8c4e8-108">Modul CLR (CLR), jež spravuje a spouští kód vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="8c4e8-109">CLR je identifikováno svým vlastním číslem verze (viz [verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="8c4e8-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="8c4e8-110">Pokud chcete získat přesné seznam verzí rozhraní .NET Framework nainstalované na počítači, můžete zobrazit registru nebo dotazovat na registr v kódu:</span><span class="sxs-lookup"><span data-stu-id="8c4e8-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="8c4e8-111">Zobrazení registru (verze 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="8c4e8-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="8c4e8-112">Zobrazení registru (verze 4.5 a novější)</span><span class="sxs-lookup"><span data-stu-id="8c4e8-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="8c4e8-113">Použití kódu k registru (verze 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="8c4e8-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="8c4e8-114">Použití kódu k registru (verze 4.5 a novější)</span><span class="sxs-lookup"><span data-stu-id="8c4e8-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="8c4e8-115">Použití Powershellu k registru (verze 4.5 a novější)</span><span class="sxs-lookup"><span data-stu-id="8c4e8-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  
  
 <span data-ttu-id="8c4e8-116">Pokud chcete zjistit verzi modulu CLR, můžete použít nástroj nebo kódu:</span><span class="sxs-lookup"><span data-stu-id="8c4e8-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="8c4e8-117">Pomocí nástroje Clrver</span><span class="sxs-lookup"><span data-stu-id="8c4e8-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="8c4e8-118">Dotaz na třídu System.Environment pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="8c4e8-118">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="8c4e8-119">Informace o zjišťování nainstalovaných aktualizací pro každou verzi rozhraní .NET Framework najdete v tématu [jak: Zjištění nainstalovaných aktualizací rozhraní .NET Framework](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="8c4e8-119">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="8c4e8-120">Informace o instalaci rozhraní .NET Framework najdete v tématu [nainstalovat rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="8c4e8-120">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="8c4e8-121">K vyhledání verze rozhraní .NET Framework zobrazením registru (.NET Framework 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="8c4e8-121">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="8c4e8-122">Na **Start** nabídce zvolte **spustit**.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-122">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="8c4e8-123">V **otevřít** zadejte **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-123">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="8c4e8-124">Ke spuštění souboru regedit.exe musíte mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-124">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="8c4e8-125">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="8c4e8-125">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="8c4e8-126">Nainstalované verze jsou uvedeny v podklíči NDP.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-126">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="8c4e8-127">Číslo verze je uloženo v **verze** položka.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-127">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="8c4e8-128">Pro [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **verze** položka je pod klientem nebo úplným podklíčem (pod NDP) nebo pod oběma podklíči.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-128">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="8c4e8-129">Složka „NET Framework Setup“ v registru nezačíná tečkou.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-129">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="8c4e8-130">K vyhledání verze rozhraní .NET Framework zobrazením registru (.NET Framework 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="8c4e8-130">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="8c4e8-131">Na **Start** nabídce zvolte **spustit**.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-131">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="8c4e8-132">V **otevřít** zadejte **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-132">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="8c4e8-133">Ke spuštění souboru regedit.exe musíte mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-133">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="8c4e8-134">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="8c4e8-134">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="8c4e8-135">Všimněte si, že cesta k `Full` podklíč zahrnuje podklíče `Net Framework` spíše než `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-135">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8c4e8-136">Pokud `Full` podklíč není k dispozici a není nutné rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-136">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="8c4e8-137">Vyhledejte hodnotu DWORD s názvem `Release`.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-137">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="8c4e8-138">Existence `Release` DWORD označuje, že [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější je nainstalovaný na tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-138">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="8c4e8-139">![Položky registru pro rozhraní .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="8c4e8-139">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="8c4e8-140">Hodnota `Release` DWORD označuje, která verze rozhraní .NET Framework je nainstalována.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-140">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="8c4e8-141">Hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="8c4e8-141">Value of the Release DWORD</span></span>|<span data-ttu-id="8c4e8-142">Version</span><span class="sxs-lookup"><span data-stu-id="8c4e8-142">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="8c4e8-143">378389</span><span class="sxs-lookup"><span data-stu-id="8c4e8-143">378389</span></span>|<span data-ttu-id="8c4e8-144">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="8c4e8-144">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="8c4e8-145">378675</span><span class="sxs-lookup"><span data-stu-id="8c4e8-145">378675</span></span>|<span data-ttu-id="8c4e8-146">Rozhraní .NET framework 4.5.1 nainstalovaná s Windows 8.1 nebo Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="8c4e8-146">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="8c4e8-147">378758</span><span class="sxs-lookup"><span data-stu-id="8c4e8-147">378758</span></span>|<span data-ttu-id="8c4e8-148">Rozhraní .NET framework 4.5.1 nainstalované ve Windows 8, Windows 7 SP1 nebo Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="8c4e8-148">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="8c4e8-149">379893</span><span class="sxs-lookup"><span data-stu-id="8c4e8-149">379893</span></span>|<span data-ttu-id="8c4e8-150">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="8c4e8-150">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="8c4e8-151">Na pouze systémy Windows 10: 393295</span><span class="sxs-lookup"><span data-stu-id="8c4e8-151">On Windows 10 systems only: 393295</span></span><br /><br /> <span data-ttu-id="8c4e8-152">Na všech ostatních verzí operačního systému: 393297</span><span class="sxs-lookup"><span data-stu-id="8c4e8-152">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="8c4e8-153">Jenom Windows 10. listopadu Update systémů: 394254</span><span class="sxs-lookup"><span data-stu-id="8c4e8-153">On Windows 10 November Update systems only: 394254</span></span><br /><br /> <span data-ttu-id="8c4e8-154">Na všech ostatních verzí operačního systému: 394271</span><span class="sxs-lookup"><span data-stu-id="8c4e8-154">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="8c4e8-155">V systému Windows 10 Anniversary Update a Windows Server 2016: 394802</span><span class="sxs-lookup"><span data-stu-id="8c4e8-155">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><br /> <span data-ttu-id="8c4e8-156">Na všech ostatních verzí operačního systému: 394806</span><span class="sxs-lookup"><span data-stu-id="8c4e8-156">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="8c4e8-157">Jenom na Windows 10 Creators Update: 460798</span><span class="sxs-lookup"><span data-stu-id="8c4e8-157">On Windows 10 Creators Update only: 460798</span></span><br/><br/> <span data-ttu-id="8c4e8-158">Na všech ostatních verzí operačního systému: 460805</span><span class="sxs-lookup"><span data-stu-id="8c4e8-158">On all other OS versions: 460805</span></span> | <span data-ttu-id="8c4e8-159">Rozhraní .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="8c4e8-159">.NET Framework 4.7</span></span> |
    |<span data-ttu-id="8c4e8-160">Na Windows 10 Fall Creators Update pouze: 461308</span><span class="sxs-lookup"><span data-stu-id="8c4e8-160">On Windows 10 Fall Creators Update only: 461308</span></span><br/><br/> <span data-ttu-id="8c4e8-161">Na všech ostatních verzí operačního systému: 461310</span><span class="sxs-lookup"><span data-stu-id="8c4e8-161">On all other OS versions: 461310</span></span> | <span data-ttu-id="8c4e8-162">Rozhraní .NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="8c4e8-162">.NET Framework 4.7.1</span></span> |
    |<span data-ttu-id="8c4e8-163">Na webu Windows 10. října 2018 Update pouze: 461814</span><span class="sxs-lookup"><span data-stu-id="8c4e8-163">On Windows 10 October 2018 Update only: 461814</span></span><br/><br/> <span data-ttu-id="8c4e8-164">Na webu Windows 10. dubna 2018 Update pouze: 461808</span><span class="sxs-lookup"><span data-stu-id="8c4e8-164">On Windows 10 April 2018 Update only: 461808</span></span><br/><br/> <span data-ttu-id="8c4e8-165">Na všech ostatních verzí operačního systému: 461814</span><span class="sxs-lookup"><span data-stu-id="8c4e8-165">On all other OS versions: 461814</span></span>| <span data-ttu-id="8c4e8-166">Rozhraní .NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="8c4e8-166">.NET Framework 4.7.2</span></span> |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="8c4e8-167">K vyhledání verze rozhraní .NET Framework dotazem na registr v kódu (.NET Framework 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="8c4e8-167">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="8c4e8-168">Použití <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> pro přístup k podklíči Software\Microsoft\NET Framework setup\ndp\ pod klíčem HKEY_LOCAL_MACHINE v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-168">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="8c4e8-169">Následující kód ukazuje příklad tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-169">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8c4e8-170">Tento kód neukazuje, jak detekovat [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-170">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="8c4e8-171">Zkontrolujte, `Release` DWORD a VYHLEDEJTE tyto verze, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-171">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="8c4e8-172">Pro kód, který zjistí, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější verze, najdete v další části v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-172">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     <span data-ttu-id="8c4e8-173">Vzorové postupy budou mít výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="8c4e8-173">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="8c4e8-174">K vyhledání verze rozhraní .NET Framework dotazem na registr v kódu (.NET Framework 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="8c4e8-174">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="8c4e8-175">Existence `Release` DWORD označuje, zda v počítači byla nainstalována rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-175">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="8c4e8-176">Hodnota klíčového slova označuje nainstalovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-176">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="8c4e8-177">Chcete-li zkontrolovat toto klíčové slovo, použijte <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> pro přístup k podklíči Software\Microsoft\NET Framework Setup\NDP\v4\Full podklíče pod klíčem HKEY_LOCAL_MACHINE v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-177">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="8c4e8-178">Zkontrolujte hodnotu `Release` – klíčové slovo k určení Instalovatelné verze.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-178">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="8c4e8-179">Aby dopřednou můžete vyhledat hodnotu větší než nebo rovna hodnotě jsou hodnoty uvedené v tabulce.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-179">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="8c4e8-180">Zde jsou verze rozhraní .NET Framework a přidružených `Release` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-180">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="8c4e8-181">Version</span><span class="sxs-lookup"><span data-stu-id="8c4e8-181">Version</span></span>|<span data-ttu-id="8c4e8-182">Hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="8c4e8-182">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="8c4e8-183">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="8c4e8-183">.NET Framework 4.5</span></span>|<span data-ttu-id="8c4e8-184">378389</span><span class="sxs-lookup"><span data-stu-id="8c4e8-184">378389</span></span>|
    |<span data-ttu-id="8c4e8-185">Rozhraní .NET framework 4.5.1 nainstalovaná s Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="8c4e8-185">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="8c4e8-186">378675</span><span class="sxs-lookup"><span data-stu-id="8c4e8-186">378675</span></span>|
    |<span data-ttu-id="8c4e8-187">Rozhraní .NET framework 4.5.1 nainstalované ve Windows 8, Windows 7 SP1 nebo Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="8c4e8-187">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="8c4e8-188">378758</span><span class="sxs-lookup"><span data-stu-id="8c4e8-188">378758</span></span>|
    |<span data-ttu-id="8c4e8-189">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="8c4e8-189">.NET Framework 4.5.2</span></span>|<span data-ttu-id="8c4e8-190">379893</span><span class="sxs-lookup"><span data-stu-id="8c4e8-190">379893</span></span>|
    |<span data-ttu-id="8c4e8-191">Rozhraní .NET framework 4.6 nainstalovaná se systémem Windows 10</span><span class="sxs-lookup"><span data-stu-id="8c4e8-191">.NET Framework 4.6 installed with Windows 10</span></span>|<span data-ttu-id="8c4e8-192">393295</span><span class="sxs-lookup"><span data-stu-id="8c4e8-192">393295</span></span>|
    |<span data-ttu-id="8c4e8-193">Rozhraní .NET framework 4.6 nainstalovaný na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="8c4e8-193">.NET Framework 4.6 installed on all other Windows OS versions</span></span>|<span data-ttu-id="8c4e8-194">393297</span><span class="sxs-lookup"><span data-stu-id="8c4e8-194">393297</span></span>|
    |<span data-ttu-id="8c4e8-195">Rozhraní .NET framework 4.6.1, které jsou nainstalované ve Windows 10</span><span class="sxs-lookup"><span data-stu-id="8c4e8-195">.NET Framework 4.6.1 installed on Windows 10</span></span>|<span data-ttu-id="8c4e8-196">394254</span><span class="sxs-lookup"><span data-stu-id="8c4e8-196">394254</span></span>|
    |<span data-ttu-id="8c4e8-197">Rozhraní .NET framework 4.6.1, které jsou nainstalované na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="8c4e8-197">.NET Framework 4.6.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="8c4e8-198">394271</span><span class="sxs-lookup"><span data-stu-id="8c4e8-198">394271</span></span>|
    |<span data-ttu-id="8c4e8-199">Rozhraní .NET framework 4.6.2 nainstalovaný na Windows serveru 2016 a Windows 10 Anniversary Update</span><span class="sxs-lookup"><span data-stu-id="8c4e8-199">.NET Framework 4.6.2 installed on Windows 10 Anniversary Update and Windows Server 2016</span></span>|<span data-ttu-id="8c4e8-200">394802</span><span class="sxs-lookup"><span data-stu-id="8c4e8-200">394802</span></span>|
    |<span data-ttu-id="8c4e8-201">Rozhraní .NET framework 4.6.2 nainstalovaný na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="8c4e8-201">.NET Framework 4.6.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="8c4e8-202">394806</span><span class="sxs-lookup"><span data-stu-id="8c4e8-202">394806</span></span>|
    |<span data-ttu-id="8c4e8-203">Rozhraní .NET framework 4.7 nainstalované ve Windows 10 Creators Update</span><span class="sxs-lookup"><span data-stu-id="8c4e8-203">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="8c4e8-204">460798</span><span class="sxs-lookup"><span data-stu-id="8c4e8-204">460798</span></span>|
    |<span data-ttu-id="8c4e8-205">Rozhraní .NET framework 4.7 nainstalovaný na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="8c4e8-205">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="8c4e8-206">460805</span><span class="sxs-lookup"><span data-stu-id="8c4e8-206">460805</span></span>|
    |<span data-ttu-id="8c4e8-207">Rozhraní .NET framework 4.7.1 nainstalovat na Windows 10 Fall Creators Update</span><span class="sxs-lookup"><span data-stu-id="8c4e8-207">.NET Framework 4.7.1 installed on Windows 10 Fall Creators Update</span></span>|<span data-ttu-id="8c4e8-208">461308</span><span class="sxs-lookup"><span data-stu-id="8c4e8-208">461308</span></span>|
    |<span data-ttu-id="8c4e8-209">Rozhraní .NET framework 4.7.1 nainstalovat na všechny ostatní verze operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="8c4e8-209">.NET Framework 4.7.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="8c4e8-210">461310</span><span class="sxs-lookup"><span data-stu-id="8c4e8-210">461310</span></span>|
    |<span data-ttu-id="8c4e8-211">Rozhraní .NET framework 4.7.2 nainstalované ve Windows 10. října 2018 aktualizovat</span><span class="sxs-lookup"><span data-stu-id="8c4e8-211">.NET Framework 4.7.2 installed on Windows 10 October 2018 Update</span></span>|<span data-ttu-id="8c4e8-212">461814</span><span class="sxs-lookup"><span data-stu-id="8c4e8-212">461814</span></span>|
    |<span data-ttu-id="8c4e8-213">Rozhraní .NET framework 4.7.2 nainstalované ve Windows 10. dubna 2018 aktualizovat</span><span class="sxs-lookup"><span data-stu-id="8c4e8-213">.NET Framework 4.7.2 installed on Windows 10 April 2018 Update</span></span>|<span data-ttu-id="8c4e8-214">461808</span><span class="sxs-lookup"><span data-stu-id="8c4e8-214">461808</span></span>|
    |<span data-ttu-id="8c4e8-215">Rozhraní .NET framework 4.7.2 nainstalovaný na Windows 10 Fall Creators Update a dřívějších verzích operačních systémů</span><span class="sxs-lookup"><span data-stu-id="8c4e8-215">.NET Framework 4.7.2 installed on Windows 10 Fall Creators Update and earlier OS versions</span></span>|<span data-ttu-id="8c4e8-216">461814</span><span class="sxs-lookup"><span data-stu-id="8c4e8-216">461814</span></span>|
    
     <span data-ttu-id="8c4e8-217">Následující příklad kontroly `Release` hodnoty v registru k určení, zda [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo je nainstalovaná novější verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-217">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     <span data-ttu-id="8c4e8-218">V tomto příkladu následuje doporučený postup pro kontrolu verzí:</span><span class="sxs-lookup"><span data-stu-id="8c4e8-218">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="8c4e8-219">Zkontroluje, zda hodnota `Release` položka je *větší než nebo rovna hodnotě* hodnotu klíče známé verze.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-219">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="8c4e8-220">Zkontroluje, aby nejstarší verzi z nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-220">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a><span data-ttu-id="8c4e8-221">Chcete-li zkontrolovat minimální požadovaná verze rozhraní .NET Framework dotazem na registr v prostředí PowerShell (.NET Framework 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="8c4e8-221">To check for a minimum-required .NET Framework version by querying the registry in PowerShell (.NET Framework 4.5 and later)</span></span>

- <span data-ttu-id="8c4e8-222">Následující příklad zkontroluje hodnotu vlastnosti `Release` – klíčové slovo k určení, zda rozhraní .NET Framework 4.6.2 nebo novější je nainstalovaný, bez ohledu na verzi operačního systému Windows (vrácení `True` Pokud se jedná a `False` jinak).</span><span class="sxs-lookup"><span data-stu-id="8c4e8-222">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed, regardless of Windows OS version (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    <span data-ttu-id="8c4e8-223">Můžete nahradit `394802` v předchozím příkladu s jinou hodnotou z následující tabulky pro kontrolu pro jinou verzi rozhraní .NET Framework minimální požadovaná.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-223">You can replace `394802` in the previous example with another value from the following table to check for a different minimum-required .NET Framework version.</span></span>
  
    |<span data-ttu-id="8c4e8-224">Version</span><span class="sxs-lookup"><span data-stu-id="8c4e8-224">Version</span></span>|<span data-ttu-id="8c4e8-225">Minimální hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="8c4e8-225">Minimum value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="8c4e8-226">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="8c4e8-226">.NET Framework 4.5</span></span>|<span data-ttu-id="8c4e8-227">378389</span><span class="sxs-lookup"><span data-stu-id="8c4e8-227">378389</span></span>|
    |<span data-ttu-id="8c4e8-228">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="8c4e8-228">.NET Framework 4.5.1</span></span>|<span data-ttu-id="8c4e8-229">378675</span><span class="sxs-lookup"><span data-stu-id="8c4e8-229">378675</span></span>|
    |<span data-ttu-id="8c4e8-230">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="8c4e8-230">.NET Framework 4.5.2</span></span>|<span data-ttu-id="8c4e8-231">379893</span><span class="sxs-lookup"><span data-stu-id="8c4e8-231">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|<span data-ttu-id="8c4e8-232">393295</span><span class="sxs-lookup"><span data-stu-id="8c4e8-232">393295</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|<span data-ttu-id="8c4e8-233">394254</span><span class="sxs-lookup"><span data-stu-id="8c4e8-233">394254</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|<span data-ttu-id="8c4e8-234">394802</span><span class="sxs-lookup"><span data-stu-id="8c4e8-234">394802</span></span>|
    |<span data-ttu-id="8c4e8-235">Rozhraní .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="8c4e8-235">.NET Framework 4.7</span></span>|<span data-ttu-id="8c4e8-236">460798</span><span class="sxs-lookup"><span data-stu-id="8c4e8-236">460798</span></span>|
    |<span data-ttu-id="8c4e8-237">Rozhraní .NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="8c4e8-237">.NET Framework 4.7.1</span></span>|<span data-ttu-id="8c4e8-238">461308</span><span class="sxs-lookup"><span data-stu-id="8c4e8-238">461308</span></span>|
    |<span data-ttu-id="8c4e8-239">Rozhraní .NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="8c4e8-239">.NET Framework 4.7.2</span></span>|<span data-ttu-id="8c4e8-240">461808</span><span class="sxs-lookup"><span data-stu-id="8c4e8-240">461808</span></span>|

<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="8c4e8-241">Vyhledání aktuální verze modulu runtime s použitím nástroje Clrver</span><span class="sxs-lookup"><span data-stu-id="8c4e8-241">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="8c4e8-242">Chcete-li zjistit, jaké verze Common Language Runtime jsou nainstalovány v počítači, použijte nástroj CLR Version Tool (Clrver.exe).</span><span class="sxs-lookup"><span data-stu-id="8c4e8-242">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="8c4e8-243">Z příkazového řádku aplikace Visual Studio, zadejte `clrver`.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-243">From a Visual Studio Command Prompt, enter `clrver`.</span></span> <span data-ttu-id="8c4e8-244">Tento příkaz vytváří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="8c4e8-244">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="8c4e8-245">Další informace o použití tohoto nástroje najdete v tématu [Clrver.exe (nástroj verze CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="8c4e8-245">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="8c4e8-246">Vyhledání aktuální verze modulu runtime pomocí dotazu na třídu prostředí v kódu</span><span class="sxs-lookup"><span data-stu-id="8c4e8-246">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="8c4e8-247">Dotaz <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro načtení <xref:System.Version> objekt, který určuje verzi modulu runtime, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-247">Query the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="8c4e8-248">Můžete použít <xref:System.Version.Major%2A?displayProperty=nameWithType> vlastnost k získání hlavního identifikátoru verze (například "4" pro verzi 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> vlastnost k získání identifikátoru verze (například "0" pro verzi 4.0), nebo <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodu k získání celého verze řetězec (například "4.0.30319.18010", jak je znázorněno v následujícím kódu).</span><span class="sxs-lookup"><span data-stu-id="8c4e8-248">You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="8c4e8-249">Tato vlastnost vrátí jednu hodnotu, která odpovídá verzi modulu runtime, který momentálně spouští kód; nevrací se verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-249">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="8c4e8-250">Pro rozhraní .NET Framework verze 4, 4.5, 4.5.1 a 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> vrátí vlastnost <xref:System.Version> objekt, jehož řetězcové vyjádření má tvar `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-250">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="8c4e8-251">Pro rozhraní .NET Framework 4.6 nebo novější, má tvar `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-251">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8c4e8-252">Pro [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a později, nedoporučujeme používat <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost zjistit verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-252">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="8c4e8-253">Namísto toho doporučujeme dotazování registru, jak je popsáno v [k vyhledání verze rozhraní .NET Framework dotazem na registr v kódu (.NET Framework 4.5 nebo novější)](#net_d) dříve v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="8c4e8-253">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="8c4e8-254">Tady je příklad dotazování <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro informace o verzi modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="8c4e8-254">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property for runtime version information:</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     <span data-ttu-id="8c4e8-255">Vzorové postupy budou mít výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="8c4e8-255">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="8c4e8-256">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c4e8-256">See also</span></span>

[<span data-ttu-id="8c4e8-257">Jak: Zjištění nainstalovaných aktualizací rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8c4e8-257">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[<span data-ttu-id="8c4e8-258">Instalace rozhraní .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8c4e8-258">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="8c4e8-259">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="8c4e8-259">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)  
