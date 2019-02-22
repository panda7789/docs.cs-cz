---
title: 'Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework'
ms.date: 02/20/2019
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
ms.openlocfilehash: d7661b3ebaa8f29d6d3b2adbc56c405c8f0945f3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584171"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="b76e4-102">Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b76e4-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="b76e4-103">Mohou uživatelé nainstalovat a spustit více verzí rozhraní .NET Framework na svých počítačích.</span><span class="sxs-lookup"><span data-stu-id="b76e4-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="b76e4-104">Při vývoji nebo nasazení vaší aplikace, můžete potřebovat vědět, jaké verze rozhraní .NET Framework jsou nainstalovány v počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="b76e4-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="b76e4-105">Všimněte si, že rozhraní .NET Framework obsahuje dvě hlavní součásti, které mají samostatné verze:</span><span class="sxs-lookup"><span data-stu-id="b76e4-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
- <span data-ttu-id="b76e4-106">Sadu sestavení, která jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="b76e4-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="b76e4-107">Rozhraní .NET Framework a sestavení sdílejí stejné číslo verze.</span><span class="sxs-lookup"><span data-stu-id="b76e4-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
- <span data-ttu-id="b76e4-108">Modul CLR (CLR), jež spravuje a spouští kód vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b76e4-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="b76e4-109">CLR je identifikováno svým vlastním číslem verze (viz [verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="b76e4-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
<span data-ttu-id="b76e4-110">Pokud chcete získat přesné seznam verzí rozhraní .NET Framework nainstalované na počítači, můžete zobrazit registru nebo dotazovat na registr v kódu:</span><span class="sxs-lookup"><span data-stu-id="b76e4-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="b76e4-111">V registru najít rozhraní .NET Framework verze 1 – 4</span><span class="sxs-lookup"><span data-stu-id="b76e4-111">Find .NET Framework versions 1-4 in the registry</span></span>](#net_a)  
 [<span data-ttu-id="b76e4-112">Najít rozhraní .NET Framework verze 4.5 a vyšší v registru)</span><span class="sxs-lookup"><span data-stu-id="b76e4-112">Find .NET Framework versions 4.5 and later in the registry)</span></span>](#net_b)  
 [<span data-ttu-id="b76e4-113">Použití kódu k registru (verze 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="b76e4-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="b76e4-114">Použití kódu k registru (verze 4.5 a novější)</span><span class="sxs-lookup"><span data-stu-id="b76e4-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="b76e4-115">Použití Powershellu k registru (verze 4.5 a novější)</span><span class="sxs-lookup"><span data-stu-id="b76e4-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  

 <span data-ttu-id="b76e4-116">Pokud chcete zjistit verzi modulu CLR, můžete použít nástroj nebo kódu:</span><span class="sxs-lookup"><span data-stu-id="b76e4-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="b76e4-117">Pomocí nástroje Clrver</span><span class="sxs-lookup"><span data-stu-id="b76e4-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="b76e4-118">Dotaz na třídu System.Environment pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="b76e4-118">Using code to query the System.Environment class</span></span>](#clr_b)  

> [!NOTE]
> <span data-ttu-id="b76e4-119">Existuje rozdíl mezi verzí rozhraní .NET Framework a společné jazykové verzi modulu runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b76e4-119">There is a difference between the .NET Framework version and the common language runtime (CLR) version.</span></span> <span data-ttu-id="b76e4-120">Rozhraní .NET Framework se systémovou správou verzí podle sadu sestavení, které tvoří knihovny tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b76e4-120">The .NET Framework is versioned based on the set of assemblies that form the .NET Framework Class Library.</span></span> <span data-ttu-id="b76e4-121">Například zahrnují verze rozhraní .NET Framework 4.5, 4.6.1 a 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="b76e4-121">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span> <span data-ttu-id="b76e4-122">Modul CLR se systémovou správou verzí podle modulu runtime, na které rozhraní .NET Framework aplikace jsou spouštěny a jedna verze modulu CLR obvykle podporuje více verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b76e4-122">The CLR is versioned based on the runtime on which .NET Framework applications execute, and a single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="b76e4-123">Verze 4.30319 modulu CLR. *xxxxx* podporuje rozhraní .NET Framework verze 4 až 4.5.2; Modul CLR verze 4.30319.42000 podporuje verze rozhraní .NET Framework počínaje .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="b76e4-123">CLR version 4.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2; CLR version 4.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span> <span data-ttu-id="b76e4-124">Další informace najdete v tématu <xref:System.Environment.Version?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b76e4-124">For more information, see the <xref:System.Environment.Version?displayProperty=nameWithType> property.</span></span>

 <span data-ttu-id="b76e4-125">Informace o zjišťování nainstalovaných aktualizací pro každou verzi rozhraní .NET Framework najdete v tématu [jak: Zjištění nainstalovaných aktualizací rozhraní .NET Framework](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="b76e4-125">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="b76e4-126">Informace o instalaci rozhraní .NET Framework najdete v tématu [nainstalovat rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="b76e4-126">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="find-net-framework-versions-1-4-in-the-registry"></a><span data-ttu-id="b76e4-127">V registru najít rozhraní .NET Framework verze 1 – 4</span><span class="sxs-lookup"><span data-stu-id="b76e4-127">Find .NET Framework versions 1-4 in the registry</span></span> 
  
1.  <span data-ttu-id="b76e4-128">Na **Start** nabídce zvolte **spustit**.</span><span class="sxs-lookup"><span data-stu-id="b76e4-128">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="b76e4-129">V **otevřít** zadejte **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="b76e4-129">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="b76e4-130">Ke spuštění souboru regedit.exe musíte mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="b76e4-130">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="b76e4-131">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="b76e4-131">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="b76e4-132">Pro rozhraní .NET Framework verze 1.1 až 3.5, nainstalované verze jsou uvedeny jako podklíče pod `NDP` podklíči.</span><span class="sxs-lookup"><span data-stu-id="b76e4-132">For .NET Framework versions 1.1 through 3.5, the installed versions are listed as subkeys under the `NDP` subkey.</span></span> <span data-ttu-id="b76e4-133">Číslo verze je uloženo v podklíči verze **verze** položka.</span><span class="sxs-lookup"><span data-stu-id="b76e4-133">The version number is stored in the version subkey's **Version** entry.</span></span> 
     
     <span data-ttu-id="b76e4-134">Pro rozhraní .NET Framework 4 **verze** položka je v části `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` podklíči `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` podklíče, nebo pod oběma podklíči.</span><span class="sxs-lookup"><span data-stu-id="b76e4-134">For .NET Framework 4, the **Version** entry is under the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` subkey, the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b76e4-135">Složka „NET Framework Setup“ v registru nezačíná tečkou.</span><span class="sxs-lookup"><span data-stu-id="b76e4-135">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="b76e4-136">Následující obrázek ukazuje, že podklíč pro rozhraní .NET Framework 3.5 spolu s jeho **verze** položka.</span><span class="sxs-lookup"><span data-stu-id="b76e4-136">The following figure shows that the subkey for the .NET Framework 3.5 along with its **Version** entry.</span></span>

     <span data-ttu-id="b76e4-137">![Položky registru pro rozhraní .NET Framework 3.5. ](../../../docs/framework/migration-guide/media/net-4-and-earlier.png "Rozhraní .NET framework 4 a dřívějších verzích")</span><span class="sxs-lookup"><span data-stu-id="b76e4-137">![The registry entry for the .NET Framework 3.5.](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET Framework 4 and earlier versions")</span></span>

<a name="net_b"></a> 
## <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="b76e4-138">Najít rozhraní .NET Framework verze 4.5 a vyšší v registru</span><span class="sxs-lookup"><span data-stu-id="b76e4-138">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="b76e4-139">Na **Start** nabídce zvolte **spustit**.</span><span class="sxs-lookup"><span data-stu-id="b76e4-139">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="b76e4-140">V **otevřít** zadejte **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="b76e4-140">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="b76e4-141">Ke spuštění souboru regedit.exe musíte mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="b76e4-141">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="b76e4-142">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="b76e4-142">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="b76e4-143">Všimněte si, že cesta k `Full` podklíč zahrnuje podklíče `Net Framework` spíše než `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="b76e4-143">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b76e4-144">Pokud `Full` podklíč není k dispozici a není nutné rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b76e4-144">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="b76e4-145">Vyhledejte hodnotu DWORD s názvem `Release`.</span><span class="sxs-lookup"><span data-stu-id="b76e4-145">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="b76e4-146">Existence `Release` DWORD označuje, že byla v počítači nainstalováno rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b76e4-146">The existence of the `Release` DWORD indicates that .NET Framework 4.5 or later has been installed on that computer.</span></span> <span data-ttu-id="b76e4-147">Jeho hodnota je verze klíče, který odpovídá konkrétní verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b76e4-147">Its value is a release key that corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="b76e4-148">Na následujícím obrázku, například hodnoty `Release` DWORD je 378389, což je verze klíč pro rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="b76e4-148">In the following figure, for example, the value of the `Release` DWORD is 378389, which is the release key for .NET Framework 4.5.</span></span> 

     <span data-ttu-id="b76e4-149">![Položky registru pro rozhraní .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="b76e4-149">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

<span data-ttu-id="b76e4-150">V následující tabulce jsou uvedeny minimální hodnota `Release` DWORD pro každou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b76e4-150">The following table lists the minimum value of the `Release` DWORD for each .NET Framework version.</span></span> <span data-ttu-id="b76e4-151">Tyto hodnoty můžete použít takto:</span><span class="sxs-lookup"><span data-stu-id="b76e4-151">You can use these values as follows:</span></span>

- <span data-ttu-id="b76e4-152">Pokud chcete zjistit, zda je k dispozici minimální verze rozhraní .NET Framework, otestovat, zda `Release` v registru byla nalezena hodnota DWORD je *větší než nebo rovna hodnotě* hodnota uvedená v tabulce.</span><span class="sxs-lookup"><span data-stu-id="b76e4-152">To determine whether a minimum .NET Framework version is present, test whether the `Release` DWORD value found in the registry is *greater than or equal to* the value listed in the table.</span></span> <span data-ttu-id="b76e4-153">Například pokud vaše aplikace vyžaduje rozhraní .NET Framework 4.7 nebo novější, byste testovali pro hodnotu klíče minimální verzi 460798.</span><span class="sxs-lookup"><span data-stu-id="b76e4-153">For example, if your application requires .NET Framework 4.7 or later, you would test for a minimum release key value of 460798.</span></span>

- <span data-ttu-id="b76e4-154">Pokud chcete otestovat více verzí, začněte s nejnovější verzí rozhraní .NET Framework a pak test pro každou po sobě jdoucích starší verzi.</span><span class="sxs-lookup"><span data-stu-id="b76e4-154">To test for multiple versions, begin with the latest .NET Framework version, and then test for each successive earlier version.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|<span data-ttu-id="b76e4-155">Verze rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="b76e4-155">.NET Framework Version</span></span>|<span data-ttu-id="b76e4-156">Hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="b76e4-156">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="b76e4-157">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b76e4-157">.NET Framework 4.5</span></span>|<span data-ttu-id="b76e4-158">378389</span><span class="sxs-lookup"><span data-stu-id="b76e4-158">378389</span></span>|
|<span data-ttu-id="b76e4-159">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="b76e4-159">.NET Framework 4.5.1</span></span>|<span data-ttu-id="b76e4-160">378675</span><span class="sxs-lookup"><span data-stu-id="b76e4-160">378675</span></span>|
|<span data-ttu-id="b76e4-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="b76e4-161">.NET Framework 4.5.2</span></span>|<span data-ttu-id="b76e4-162">379893</span><span class="sxs-lookup"><span data-stu-id="b76e4-162">379893</span></span>|
|<span data-ttu-id="b76e4-163">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="b76e4-163">.NET Framework 4.6</span></span>|<span data-ttu-id="b76e4-164">393295</span><span class="sxs-lookup"><span data-stu-id="b76e4-164">393295</span></span>|
|<span data-ttu-id="b76e4-165">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="b76e4-165">.NET Framework 4.6.1</span></span>|<span data-ttu-id="b76e4-166">394254</span><span class="sxs-lookup"><span data-stu-id="b76e4-166">394254</span></span>|
|<span data-ttu-id="b76e4-167">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b76e4-167">.NET Framework 4.6.2</span></span>|<span data-ttu-id="b76e4-168">394802</span><span class="sxs-lookup"><span data-stu-id="b76e4-168">394802</span></span>|
|<span data-ttu-id="b76e4-169">Rozhraní .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="b76e4-169">.NET Framework 4.7</span></span>|<span data-ttu-id="b76e4-170">460798</span><span class="sxs-lookup"><span data-stu-id="b76e4-170">460798</span></span>|
|<span data-ttu-id="b76e4-171">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="b76e4-171">.NET Framework 4.7.1</span></span>|<span data-ttu-id="b76e4-172">461308</span><span class="sxs-lookup"><span data-stu-id="b76e4-172">461308</span></span>|
|<span data-ttu-id="b76e4-173">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="b76e4-173">.NET Framework 4.7.2</span></span>|<span data-ttu-id="b76e4-174">461808</span><span class="sxs-lookup"><span data-stu-id="b76e4-174">461808</span></span>|

<span data-ttu-id="b76e4-175">Kompletní tabulku verze klíče pro rozhraní .NET Framework pro konkrétní verze operačního systému Windows, naleznete v tématu [klíče rozhraní .NET Framework verze a verze operačního systému Windows](release-keys-and-os-versions.md).</span><span class="sxs-lookup"><span data-stu-id="b76e4-175">For a complete table of release keys for the .NET Framework for specific Windows operating system versions, see [.NET Framework release keys and Windows operating system versions](release-keys-and-os-versions.md).</span></span>

<a name="net_c"></a> 
## <a name="find-net-framework-versions-1-4-with-code"></a><span data-ttu-id="b76e4-176">Najít rozhraní .NET Framework verze 1 – 4 s kódem</span><span class="sxs-lookup"><span data-stu-id="b76e4-176">Find .NET Framework versions 1-4 with code</span></span>

- <span data-ttu-id="b76e4-177">Použití <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> třídy k přístupu `Software\Microsoft\NET Framework Setup\NDP\` podklíče pod `HKEY_LOCAL_MACHINE` větve v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="b76e4-177">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the `Software\Microsoft\NET Framework Setup\NDP\` subkey under `HKEY_LOCAL_MACHINE` branch in the Windows registry.</span></span>

     <span data-ttu-id="b76e4-178">Následující kód ukazuje příklad tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="b76e4-178">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b76e4-179">Tento kód neukazuje k zjištění rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b76e4-179">This code does not show how to detect .NET Framework 4.5 or later.</span></span> <span data-ttu-id="b76e4-180">Zkontrolujte, `Release` DWORD a VYHLEDEJTE tyto verze, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="b76e4-180">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="b76e4-181">Kód, který zjistí rozhraní .NET Framework 4.5 nebo novější verze najdete v další části v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="b76e4-181">For code that detects .NET Framework 4.5 or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

<a name="net_d"></a> 
## <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="b76e4-182">Najít rozhraní .NET Framework verze 4.5 a vyšší s kódem</span><span class="sxs-lookup"><span data-stu-id="b76e4-182">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="b76e4-183">Existence `Release` typu DWORD v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíče označuje, že je na počítači nainstalované rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b76e4-183">The existence of the `Release` DWORD in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key indicates that the .NET Framework 4.5 or later is installed on a computer.</span></span> <span data-ttu-id="b76e4-184">Hodnota klíčového slova označuje nainstalovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="b76e4-184">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="b76e4-185">Chcete-li zkontrolovat toto klíčové slovo, použijte <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> metody pro přístup k podklíči registru Windows.</span><span class="sxs-lookup"><span data-stu-id="b76e4-185">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the subkey in the Windows registry.</span></span>

2. <span data-ttu-id="b76e4-186">Zkontrolujte hodnotu `Release` – klíčové slovo k určení Instalovatelné verze.</span><span class="sxs-lookup"><span data-stu-id="b76e4-186">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="b76e4-187">Bude dopřednou, můžete zkontrolovat hodnotu větší než nebo rovna hodnotě uvedené v tabulce [najít rozhraní .NET Framework verze 4.5 a vyšší v registru](#net_b) oddílu.</span><span class="sxs-lookup"><span data-stu-id="b76e4-187">To be forward-compatible, you can check for a value greater than or equal to the value listed in the table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section.</span></span>

<span data-ttu-id="b76e4-188">Následující příklad kontroly `Release` hodnoty v registru k určení, jestli je nainstalované rozhraní .NET Framework 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b76e4-188">The following example checks the `Release` value in the registry to determine whether .NET Framework 4.5 or a later version is installed.</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="b76e4-189">V tomto příkladu následuje doporučený postup pro kontrolu verzí:</span><span class="sxs-lookup"><span data-stu-id="b76e4-189">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="b76e4-190">Zkontroluje, zda hodnota `Release` položka je *větší než nebo rovna hodnotě* hodnotu klíče známé verze.</span><span class="sxs-lookup"><span data-stu-id="b76e4-190">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="b76e4-191">Zkontroluje, aby nejstarší verzi z nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="b76e4-191">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="b76e4-192">Vyhledejte minimální požadované rozhraní .NET Framework verze (4.5 a novější) pomocí Powershellu</span><span class="sxs-lookup"><span data-stu-id="b76e4-192">Check for a minimum required .NET Framework version (4.5 and later) with PowerShell</span></span>

<span data-ttu-id="b76e4-193">Následující příklad zkontroluje hodnotu vlastnosti `Release` – klíčové slovo k určení, zda rozhraní .NET Framework 4.6.2 nebo novější je nainstalována (vrácení `True` Pokud se jedná a `False` jinak).</span><span class="sxs-lookup"><span data-stu-id="b76e4-193">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    You can replace `394802` in the previous example with another value from the following table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section to check for a different minimum required .NET Framework version.
  
<a name="clr_a"></a> 
## <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="b76e4-194">Vyhledání aktuální verze modulu CLR s Clrver.exe</span><span class="sxs-lookup"><span data-stu-id="b76e4-194">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="b76e4-195">Chcete-li zjistit, jaké verze Common Language Runtime jsou nainstalovány v počítači, použijte nástroj CLR Version Tool (Clrver.exe).</span><span class="sxs-lookup"><span data-stu-id="b76e4-195">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

<span data-ttu-id="b76e4-196">Z příkazový řádek vývojáře pro sadu Visual Studio, zadejte `clrver`.</span><span class="sxs-lookup"><span data-stu-id="b76e4-196">From a Developer Command Prompt for Visual Studio, enter `clrver`.</span></span> <span data-ttu-id="b76e4-197">Tento příkaz vytváří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="b76e4-197">This command produces output similar to the following:</span></span>

```console
Versions installed on the machine:
v2.0.50727
v4.0.30319
```

<span data-ttu-id="b76e4-198">Další informace o použití tohoto nástroje najdete v tématu [Clrver.exe (nástroj verze CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b76e4-198">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="b76e4-199">Vyhledání aktuální verze modulu CLR s třídou prostředí</span><span class="sxs-lookup"><span data-stu-id="b76e4-199">Find the current CLR version with the Environment class</span></span>

<span data-ttu-id="b76e4-200">Můžete načíst hodnotu <xref:System.Environment.Version?displayProperty=nameWithType> vlastnost pro načtení <xref:System.Version> objekt, který určuje verzi modulu runtime, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="b76e4-200">You can retrieve the value of the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="b76e4-201">Tato vlastnost vrátí jednu hodnotu, která odpovídá verzi modulu runtime, který aktuálně spouští kód; nevrací se verze sestavení ani jiné verze modulu runtime, který byl nainstalován v počítači. Můžete použít <xref:System.Version.Major%2A?displayProperty=nameWithType> vlastnost k získání hlavního identifikátoru verze (například "4" pro verzi 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> vlastnost k získání identifikátoru verze (například "0" pro verzi 4.0), nebo <xref:System.Version.ToString%2A?displayProperty=nameWithType> metodu k získání celého verze řetězec (například "4.0.30319.18010", jak je znázorněno v následujícím kódu).</span><span class="sxs-lookup"><span data-stu-id="b76e4-201">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> 

<span data-ttu-id="b76e4-202">Pro rozhraní .NET Framework verze 4, 4.5, 4.5.1 a 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> vrátí vlastnost <xref:System.Version> objekt, jehož řetězcové vyjádření má tvar `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="b76e4-202">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="b76e4-203">Pro rozhraní .NET Framework 4.6 nebo novější, má tvar `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="b76e4-203">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b76e4-204">Pro rozhraní .NET Framework 4.5 nebo novější, nedoporučujeme používat <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost zjistit verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b76e4-204">For the .NET Framework 4.5 and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="b76e4-205">Namísto toho doporučujeme dotazování registru, jak je popsáno v [k vyhledání verze rozhraní .NET Framework dotazem na registr v kódu (.NET Framework 4.5 nebo novější)](#net_d) dříve v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="b76e4-205">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

<span data-ttu-id="b76e4-206">Následující příklad použitý <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro načtení informací o verzi modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="b76e4-206">The following example used the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve runtime version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="b76e4-207">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b76e4-207">See also</span></span>

- [<span data-ttu-id="b76e4-208">Postupy: Zjištění nainstalovaných aktualizací rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b76e4-208">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="b76e4-209">Instalace rozhraní .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b76e4-209">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)
- [<span data-ttu-id="b76e4-210">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="b76e4-210">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)
