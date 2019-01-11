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
ms.openlocfilehash: d1a0ee772618b89d3b8cf6efc9400e3dcf4804da
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223179"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="15d75-102">Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="15d75-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="15d75-103">Mohou uživatelé nainstalovat a spustit více verzí rozhraní .NET Framework na svých počítačích.</span><span class="sxs-lookup"><span data-stu-id="15d75-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="15d75-104">Při vývoji nebo nasazení vaší aplikace, můžete potřebovat vědět, jaké verze rozhraní .NET Framework jsou nainstalovány v počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="15d75-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="15d75-105">Všimněte si, že rozhraní .NET Framework obsahuje dvě hlavní součásti, které mají samostatné verze:</span><span class="sxs-lookup"><span data-stu-id="15d75-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="15d75-106">Sadu sestavení, která jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="15d75-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="15d75-107">Rozhraní .NET Framework a sestavení sdílejí stejné číslo verze.</span><span class="sxs-lookup"><span data-stu-id="15d75-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="15d75-108">Modul CLR (CLR), jež spravuje a spouští kód vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="15d75-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="15d75-109">CLR je identifikováno svým vlastním číslem verze (viz [verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="15d75-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="15d75-110">Pokud chcete získat přesné seznam verzí rozhraní .NET Framework nainstalované na počítači, můžete zobrazit registru nebo dotazovat na registr v kódu:</span><span class="sxs-lookup"><span data-stu-id="15d75-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="15d75-111">Zobrazení registru (verze 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="15d75-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="15d75-112">Zobrazení registru (verze 4.5 a novější)</span><span class="sxs-lookup"><span data-stu-id="15d75-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="15d75-113">Použití kódu k registru (verze 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="15d75-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="15d75-114">Použití kódu k registru (verze 4.5 a novější)</span><span class="sxs-lookup"><span data-stu-id="15d75-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="15d75-115">Použití Powershellu k registru (verze 4.5 a novější)</span><span class="sxs-lookup"><span data-stu-id="15d75-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  
  
 <span data-ttu-id="15d75-116">Pokud chcete zjistit verzi modulu CLR, můžete použít nástroj nebo kódu:</span><span class="sxs-lookup"><span data-stu-id="15d75-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="15d75-117">Pomocí nástroje Clrver</span><span class="sxs-lookup"><span data-stu-id="15d75-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="15d75-118">Dotaz na třídu System.Environment pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="15d75-118">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="15d75-119">Informace o zjišťování nainstalovaných aktualizací pro každou verzi rozhraní .NET Framework najdete v tématu [jak: Zjištění nainstalovaných aktualizací rozhraní .NET Framework](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="15d75-119">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="15d75-120">Informace o instalaci rozhraní .NET Framework najdete v tématu [nainstalovat rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="15d75-120">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="15d75-121">K vyhledání verze rozhraní .NET Framework zobrazením registru (.NET Framework 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="15d75-121">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="15d75-122">Na **Start** nabídce zvolte **spustit**.</span><span class="sxs-lookup"><span data-stu-id="15d75-122">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="15d75-123">V **otevřít** zadejte **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="15d75-123">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="15d75-124">Ke spuštění souboru regedit.exe musíte mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="15d75-124">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="15d75-125">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="15d75-125">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="15d75-126">Nainstalované verze jsou uvedeny v podklíči NDP.</span><span class="sxs-lookup"><span data-stu-id="15d75-126">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="15d75-127">Číslo verze je uloženo v **verze** položka.</span><span class="sxs-lookup"><span data-stu-id="15d75-127">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="15d75-128">Pro [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **verze** položka je pod klientem nebo úplným podklíčem (pod NDP) nebo pod oběma podklíči.</span><span class="sxs-lookup"><span data-stu-id="15d75-128">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="15d75-129">Složka „NET Framework Setup“ v registru nezačíná tečkou.</span><span class="sxs-lookup"><span data-stu-id="15d75-129">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="15d75-130">K vyhledání verze rozhraní .NET Framework zobrazením registru (.NET Framework 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="15d75-130">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="15d75-131">Na **Start** nabídce zvolte **spustit**.</span><span class="sxs-lookup"><span data-stu-id="15d75-131">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="15d75-132">V **otevřít** zadejte **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="15d75-132">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="15d75-133">Ke spuštění souboru regedit.exe musíte mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="15d75-133">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="15d75-134">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="15d75-134">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="15d75-135">Všimněte si, že cesta k `Full` podklíč zahrnuje podklíče `Net Framework` spíše než `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="15d75-135">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="15d75-136">Pokud `Full` podklíč není k dispozici a není nutné rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="15d75-136">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="15d75-137">Vyhledejte hodnotu DWORD s názvem `Release`.</span><span class="sxs-lookup"><span data-stu-id="15d75-137">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="15d75-138">Existence `Release` DWORD označuje, že [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější je nainstalovaný na tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="15d75-138">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="15d75-139">![Položky registru pro rozhraní .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="15d75-139">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="15d75-140">Hodnota `Release` DWORD označuje, která verze rozhraní .NET Framework je nainstalována.</span><span class="sxs-lookup"><span data-stu-id="15d75-140">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="15d75-141">Hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="15d75-141">Value of the Release DWORD</span></span>|<span data-ttu-id="15d75-142">Version</span><span class="sxs-lookup"><span data-stu-id="15d75-142">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="15d75-143">378389</span><span class="sxs-lookup"><span data-stu-id="15d75-143">378389</span></span>|<span data-ttu-id="15d75-144">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="15d75-144">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="15d75-145">378675</span><span class="sxs-lookup"><span data-stu-id="15d75-145">378675</span></span>|<span data-ttu-id="15d75-146">Rozhraní .NET framework 4.5.1 nainstalovaná s Windows 8.1 nebo Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="15d75-146">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="15d75-147">378758</span><span class="sxs-lookup"><span data-stu-id="15d75-147">378758</span></span>|<span data-ttu-id="15d75-148">Rozhraní .NET framework 4.5.1 nainstalované ve Windows 8, Windows 7 SP1 nebo Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="15d75-148">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="15d75-149">379893</span><span class="sxs-lookup"><span data-stu-id="15d75-149">379893</span></span>|<span data-ttu-id="15d75-150">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="15d75-150">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="15d75-151">Na pouze systémy Windows 10: 393295</span><span class="sxs-lookup"><span data-stu-id="15d75-151">On Windows 10 systems only: 393295</span></span><br /><br /> <span data-ttu-id="15d75-152">Na všech ostatních verzí operačního systému: 393297</span><span class="sxs-lookup"><span data-stu-id="15d75-152">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="15d75-153">Jenom Windows 10. listopadu Update systémů: 394254</span><span class="sxs-lookup"><span data-stu-id="15d75-153">On Windows 10 November Update systems only: 394254</span></span><br /><br /> <span data-ttu-id="15d75-154">Na všech ostatních verzí operačního systému: 394271</span><span class="sxs-lookup"><span data-stu-id="15d75-154">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="15d75-155">V systému Windows 10 Anniversary Update a Windows Server 2016: 394802</span><span class="sxs-lookup"><span data-stu-id="15d75-155">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><br /> <span data-ttu-id="15d75-156">Na všech ostatních verzí operačního systému: 394806</span><span class="sxs-lookup"><span data-stu-id="15d75-156">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="15d75-157">Jenom na Windows 10 Creators Update: 460798</span><span class="sxs-lookup"><span data-stu-id="15d75-157">On Windows 10 Creators Update only: 460798</span></span><br/><br/> <span data-ttu-id="15d75-158">Na všech ostatních verzí operačního systému: 460805</span><span class="sxs-lookup"><span data-stu-id="15d75-158">On all other OS versions: 460805</span></span> | <span data-ttu-id="15d75-159">Rozhraní .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="15d75-159">.NET Framework 4.7</span></span> |
    |<span data-ttu-id="15d75-160">Na Windows 10 Fall Creators Update pouze: 461308</span><span class="sxs-lookup"><span data-stu-id="15d75-160">On Windows 10 Fall Creators Update only: 461308</span></span><br/><br/> <span data-ttu-id="15d75-161">Na všech ostatních verzí operačního systému: 461310</span><span class="sxs-lookup"><span data-stu-id="15d75-161">On all other OS versions: 461310</span></span> | <span data-ttu-id="15d75-162">Rozhraní .NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="15d75-162">.NET Framework 4.7.1</span></span> |
    |<span data-ttu-id="15d75-163">Na webu Windows 10. dubna 2018 Update pouze: 461808</span><span class="sxs-lookup"><span data-stu-id="15d75-163">On Windows 10 April 2018 Update only: 461808</span></span><br/><br/> <span data-ttu-id="15d75-164">Na všech ostatních verzí operačního systému, včetně Windows 10. října 2018 Update: 461814</span><span class="sxs-lookup"><span data-stu-id="15d75-164">On all other OS versions, including Windows 10 October 2018 Update: 461814</span></span>| <span data-ttu-id="15d75-165">Rozhraní .NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="15d75-165">.NET Framework 4.7.2</span></span> |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="15d75-166">K vyhledání verze rozhraní .NET Framework dotazem na registr v kódu (.NET Framework 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="15d75-166">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="15d75-167">Použití <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> pro přístup k podklíči Software\Microsoft\NET Framework setup\ndp\ pod klíčem HKEY_LOCAL_MACHINE v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="15d75-167">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="15d75-168">Následující kód ukazuje příklad tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="15d75-168">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="15d75-169">Tento kód neukazuje, jak detekovat [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější.</span><span class="sxs-lookup"><span data-stu-id="15d75-169">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="15d75-170">Zkontrolujte, `Release` DWORD a VYHLEDEJTE tyto verze, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="15d75-170">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="15d75-171">Pro kód, který zjistí, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější verze, najdete v další části v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="15d75-171">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     <span data-ttu-id="15d75-172">Vzorové postupy budou mít výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="15d75-172">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="15d75-173">K vyhledání verze rozhraní .NET Framework dotazem na registr v kódu (.NET Framework 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="15d75-173">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="15d75-174">Existence `Release` DWORD označuje, zda v počítači byla nainstalována rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="15d75-174">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="15d75-175">Hodnota klíčového slova označuje nainstalovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="15d75-175">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="15d75-176">Chcete-li zkontrolovat toto klíčové slovo, použijte <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> pro přístup k podklíči Software\Microsoft\NET Framework Setup\NDP\v4\Full podklíče pod klíčem HKEY_LOCAL_MACHINE v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="15d75-176">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="15d75-177">Zkontrolujte hodnotu `Release` – klíčové slovo k určení Instalovatelné verze.</span><span class="sxs-lookup"><span data-stu-id="15d75-177">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="15d75-178">Aby dopřednou můžete vyhledat hodnotu větší než nebo rovna hodnotě jsou hodnoty uvedené v tabulce.</span><span class="sxs-lookup"><span data-stu-id="15d75-178">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="15d75-179">Zde jsou verze rozhraní .NET Framework a přidružených `Release` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="15d75-179">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="15d75-180">Version</span><span class="sxs-lookup"><span data-stu-id="15d75-180">Version</span></span>|<span data-ttu-id="15d75-181">Hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="15d75-181">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="15d75-182">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="15d75-182">.NET Framework 4.5</span></span>|<span data-ttu-id="15d75-183">378389</span><span class="sxs-lookup"><span data-stu-id="15d75-183">378389</span></span>|
    |<span data-ttu-id="15d75-184">Rozhraní .NET framework 4.5.1 nainstalovaná s Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="15d75-184">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="15d75-185">378675</span><span class="sxs-lookup"><span data-stu-id="15d75-185">378675</span></span>|
    |<span data-ttu-id="15d75-186">Rozhraní .NET framework 4.5.1 nainstalované ve Windows 8, Windows 7 SP1 nebo Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="15d75-186">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="15d75-187">378758</span><span class="sxs-lookup"><span data-stu-id="15d75-187">378758</span></span>|
    |<span data-ttu-id="15d75-188">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="15d75-188">.NET Framework 4.5.2</span></span>|<span data-ttu-id="15d75-189">379893</span><span class="sxs-lookup"><span data-stu-id="15d75-189">379893</span></span>|
    |<span data-ttu-id="15d75-190">Rozhraní .NET framework 4.6 nainstalovaná se systémem Windows 10</span><span class="sxs-lookup"><span data-stu-id="15d75-190">.NET Framework 4.6 installed with Windows 10</span></span>|<span data-ttu-id="15d75-191">393295</span><span class="sxs-lookup"><span data-stu-id="15d75-191">393295</span></span>|
    |<span data-ttu-id="15d75-192">Rozhraní .NET framework 4.6 nainstalovaný na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="15d75-192">.NET Framework 4.6 installed on all other Windows OS versions</span></span>|<span data-ttu-id="15d75-193">393297</span><span class="sxs-lookup"><span data-stu-id="15d75-193">393297</span></span>|
    |<span data-ttu-id="15d75-194">Rozhraní .NET framework 4.6.1, které jsou nainstalované ve Windows 10</span><span class="sxs-lookup"><span data-stu-id="15d75-194">.NET Framework 4.6.1 installed on Windows 10</span></span>|<span data-ttu-id="15d75-195">394254</span><span class="sxs-lookup"><span data-stu-id="15d75-195">394254</span></span>|
    |<span data-ttu-id="15d75-196">Rozhraní .NET framework 4.6.1, které jsou nainstalované na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="15d75-196">.NET Framework 4.6.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="15d75-197">394271</span><span class="sxs-lookup"><span data-stu-id="15d75-197">394271</span></span>|
    |<span data-ttu-id="15d75-198">Rozhraní .NET framework 4.6.2 nainstalovaný na Windows serveru 2016 a Windows 10 Anniversary Update</span><span class="sxs-lookup"><span data-stu-id="15d75-198">.NET Framework 4.6.2 installed on Windows 10 Anniversary Update and Windows Server 2016</span></span>|<span data-ttu-id="15d75-199">394802</span><span class="sxs-lookup"><span data-stu-id="15d75-199">394802</span></span>|
    |<span data-ttu-id="15d75-200">Rozhraní .NET framework 4.6.2 nainstalovaný na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="15d75-200">.NET Framework 4.6.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="15d75-201">394806</span><span class="sxs-lookup"><span data-stu-id="15d75-201">394806</span></span>|
    |<span data-ttu-id="15d75-202">Rozhraní .NET framework 4.7 nainstalované ve Windows 10 Creators Update</span><span class="sxs-lookup"><span data-stu-id="15d75-202">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="15d75-203">460798</span><span class="sxs-lookup"><span data-stu-id="15d75-203">460798</span></span>|
    |<span data-ttu-id="15d75-204">Rozhraní .NET framework 4.7 nainstalovaný na všech ostatních verzí operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="15d75-204">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="15d75-205">460805</span><span class="sxs-lookup"><span data-stu-id="15d75-205">460805</span></span>|
    |<span data-ttu-id="15d75-206">Rozhraní .NET framework 4.7.1 nainstalovat na Windows 10 Fall Creators Update</span><span class="sxs-lookup"><span data-stu-id="15d75-206">.NET Framework 4.7.1 installed on Windows 10 Fall Creators Update</span></span>|<span data-ttu-id="15d75-207">461308</span><span class="sxs-lookup"><span data-stu-id="15d75-207">461308</span></span>|
    |<span data-ttu-id="15d75-208">Rozhraní .NET framework 4.7.1 nainstalovat na všechny ostatní verze operačního systému Windows</span><span class="sxs-lookup"><span data-stu-id="15d75-208">.NET Framework 4.7.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="15d75-209">461310</span><span class="sxs-lookup"><span data-stu-id="15d75-209">461310</span></span>|
    |<span data-ttu-id="15d75-210">Rozhraní .NET framework 4.7.2 nainstalované ve Windows 10. října 2018 aktualizovat</span><span class="sxs-lookup"><span data-stu-id="15d75-210">.NET Framework 4.7.2 installed on Windows 10 October 2018 Update</span></span>|<span data-ttu-id="15d75-211">461814</span><span class="sxs-lookup"><span data-stu-id="15d75-211">461814</span></span>|
    |<span data-ttu-id="15d75-212">Rozhraní .NET framework 4.7.2 nainstalované ve Windows 10. dubna 2018 aktualizovat</span><span class="sxs-lookup"><span data-stu-id="15d75-212">.NET Framework 4.7.2 installed on Windows 10 April 2018 Update</span></span>|<span data-ttu-id="15d75-213">461808</span><span class="sxs-lookup"><span data-stu-id="15d75-213">461808</span></span>|
    |<span data-ttu-id="15d75-214">Rozhraní .NET framework 4.7.2 nainstalovaný na Windows 10 Fall Creators Update a dřívějších verzích operačních systémů</span><span class="sxs-lookup"><span data-stu-id="15d75-214">.NET Framework 4.7.2 installed on Windows 10 Fall Creators Update and earlier OS versions</span></span>|<span data-ttu-id="15d75-215">461814</span><span class="sxs-lookup"><span data-stu-id="15d75-215">461814</span></span>|
    
     <span data-ttu-id="15d75-216">Následující příklad kontroly `Release` hodnoty v registru k určení, zda [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo je nainstalovaná novější verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15d75-216">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     <span data-ttu-id="15d75-217">V tomto příkladu následuje doporučený postup pro kontrolu verzí:</span><span class="sxs-lookup"><span data-stu-id="15d75-217">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="15d75-218">Zkontroluje, zda hodnota `Release` položka je *větší než nebo rovna hodnotě* hodnotu klíče známé verze.</span><span class="sxs-lookup"><span data-stu-id="15d75-218">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="15d75-219">Zkontroluje, aby nejstarší verzi z nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="15d75-219">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a><span data-ttu-id="15d75-220">Chcete-li zkontrolovat minimální požadovaná verze rozhraní .NET Framework dotazem na registr v prostředí PowerShell (.NET Framework 4.5 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="15d75-220">To check for a minimum-required .NET Framework version by querying the registry in PowerShell (.NET Framework 4.5 and later)</span></span>

- <span data-ttu-id="15d75-221">Následující příklad zkontroluje hodnotu vlastnosti `Release` – klíčové slovo k určení, zda rozhraní .NET Framework 4.6.2 nebo novější je nainstalovaný, bez ohledu na verzi operačního systému Windows (vrácení `True` Pokud se jedná a `False` jinak).</span><span class="sxs-lookup"><span data-stu-id="15d75-221">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed, regardless of Windows OS version (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    <span data-ttu-id="15d75-222">Můžete nahradit `394802` v předchozím příkladu s jinou hodnotou z následující tabulky pro kontrolu pro jinou verzi rozhraní .NET Framework minimální požadovaná.</span><span class="sxs-lookup"><span data-stu-id="15d75-222">You can replace `394802` in the previous example with another value from the following table to check for a different minimum-required .NET Framework version.</span></span>
  
    |<span data-ttu-id="15d75-223">Version</span><span class="sxs-lookup"><span data-stu-id="15d75-223">Version</span></span>|<span data-ttu-id="15d75-224">Minimální hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="15d75-224">Minimum value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="15d75-225">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="15d75-225">.NET Framework 4.5</span></span>|<span data-ttu-id="15d75-226">378389</span><span class="sxs-lookup"><span data-stu-id="15d75-226">378389</span></span>|
    |<span data-ttu-id="15d75-227">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="15d75-227">.NET Framework 4.5.1</span></span>|<span data-ttu-id="15d75-228">378675</span><span class="sxs-lookup"><span data-stu-id="15d75-228">378675</span></span>|
    |<span data-ttu-id="15d75-229">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="15d75-229">.NET Framework 4.5.2</span></span>|<span data-ttu-id="15d75-230">379893</span><span class="sxs-lookup"><span data-stu-id="15d75-230">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|<span data-ttu-id="15d75-231">393295</span><span class="sxs-lookup"><span data-stu-id="15d75-231">393295</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|<span data-ttu-id="15d75-232">394254</span><span class="sxs-lookup"><span data-stu-id="15d75-232">394254</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|<span data-ttu-id="15d75-233">394802</span><span class="sxs-lookup"><span data-stu-id="15d75-233">394802</span></span>|
    |<span data-ttu-id="15d75-234">Rozhraní .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="15d75-234">.NET Framework 4.7</span></span>|<span data-ttu-id="15d75-235">460798</span><span class="sxs-lookup"><span data-stu-id="15d75-235">460798</span></span>|
    |<span data-ttu-id="15d75-236">Rozhraní .NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="15d75-236">.NET Framework 4.7.1</span></span>|<span data-ttu-id="15d75-237">461308</span><span class="sxs-lookup"><span data-stu-id="15d75-237">461308</span></span>|
    |<span data-ttu-id="15d75-238">Rozhraní .NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="15d75-238">.NET Framework 4.7.2</span></span>|<span data-ttu-id="15d75-239">461808</span><span class="sxs-lookup"><span data-stu-id="15d75-239">461808</span></span>|

<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="15d75-240">Vyhledání aktuální verze modulu runtime s použitím nástroje Clrver</span><span class="sxs-lookup"><span data-stu-id="15d75-240">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="15d75-241">Chcete-li zjistit, jaké verze Common Language Runtime jsou nainstalovány v počítači, použijte nástroj CLR Version Tool (Clrver.exe).</span><span class="sxs-lookup"><span data-stu-id="15d75-241">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="15d75-242">Z příkazový řádek vývojáře pro sadu Visual Studio, zadejte `clrver`.</span><span class="sxs-lookup"><span data-stu-id="15d75-242">From a Developer Command Prompt for Visual Studio, enter `clrver`.</span></span> <span data-ttu-id="15d75-243">Tento příkaz vytváří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="15d75-243">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="15d75-244">Další informace o použití tohoto nástroje najdete v tématu [Clrver.exe (nástroj verze CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="15d75-244">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="15d75-245">Vyhledání aktuální verze modulu runtime pomocí dotazu na třídu prostředí v kódu</span><span class="sxs-lookup"><span data-stu-id="15d75-245">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="15d75-246">Dotaz <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro načtení <xref:System.Version> objekt, který určuje verzi modulu runtime, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="15d75-246">Query the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="15d75-247">Můžete použít <xref:System.Version.Major%2A?displayProperty=nameWithType> vlastnost k získání hlavního identifikátoru verze (například "4" pro verzi 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> vlastnost k získání identifikátoru verze (například "0" pro verzi 4.0), nebo <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodu k získání celého verze řetězec (například "4.0.30319.18010", jak je znázorněno v následujícím kódu).</span><span class="sxs-lookup"><span data-stu-id="15d75-247">You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="15d75-248">Tato vlastnost vrátí jednu hodnotu, která odpovídá verzi modulu runtime, který momentálně spouští kód; nevrací se verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="15d75-248">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="15d75-249">Pro rozhraní .NET Framework verze 4, 4.5, 4.5.1 a 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> vrátí vlastnost <xref:System.Version> objekt, jehož řetězcové vyjádření má tvar `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="15d75-249">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="15d75-250">Pro rozhraní .NET Framework 4.6 nebo novější, má tvar `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="15d75-250">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="15d75-251">Pro [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a později, nedoporučujeme používat <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost zjistit verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="15d75-251">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="15d75-252">Namísto toho doporučujeme dotazování registru, jak je popsáno v [k vyhledání verze rozhraní .NET Framework dotazem na registr v kódu (.NET Framework 4.5 nebo novější)](#net_d) dříve v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="15d75-252">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="15d75-253">Tady je příklad dotazování <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro informace o verzi modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="15d75-253">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property for runtime version information:</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     <span data-ttu-id="15d75-254">Vzorové postupy budou mít výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="15d75-254">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="15d75-255">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15d75-255">See also</span></span>

[<span data-ttu-id="15d75-256">Postupy: Zjištění nainstalovaných aktualizací rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="15d75-256">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[<span data-ttu-id="15d75-257">Instalace rozhraní .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="15d75-257">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="15d75-258">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="15d75-258">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)  
