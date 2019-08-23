---
title: 'Postupy: Určit, které verze .NET Framework jsou nainstalovány'
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
ms.openlocfilehash: 5ead6db2c3df3662c4d689bd6ac2466c99b02a15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968267"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="4e42f-102">Postupy: Určit, které verze .NET Framework jsou nainstalovány</span><span class="sxs-lookup"><span data-stu-id="4e42f-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="4e42f-103">Uživatelé mohou na svých počítačích [instalovat](https://docs.microsoft.com/dotnet/framework/install) a spouštět více verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e42f-103">Users can [install](https://docs.microsoft.com/dotnet/framework/install) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="4e42f-104">Když vyvíjíte nebo nasazujete aplikaci, možná budete potřebovat informace o tom, které verze .NET Framework jsou nainstalovány v počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="4e42f-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span>

<span data-ttu-id="4e42f-105">.NET Framework se skládá ze dvou hlavních součástí, které jsou ve verzi samostatně:</span><span class="sxs-lookup"><span data-stu-id="4e42f-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="4e42f-106">Sada sestavení, což jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="4e42f-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="4e42f-107">.NET Framework a sestavení sdílejí stejné číslo verze.</span><span class="sxs-lookup"><span data-stu-id="4e42f-107">The .NET Framework and assemblies share the same version number.</span></span>

- <span data-ttu-id="4e42f-108">Modul CLR (Common Language Runtime), který spravuje a spouští kód vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4e42f-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="4e42f-109">Modul CLR je identifikován vlastním číslem verze (viz [verze a závislosti](versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="4e42f-109">The CLR is identified by its own version number (see [Versions and Dependencies](versions-and-dependencies.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="4e42f-110">Každá nová verze rozhraní .NET Framework zachovává funkce předchozích verzí a přidává nové funkce.</span><span class="sxs-lookup"><span data-stu-id="4e42f-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="4e42f-111">V jednom počítači můžete načíst několik verzí .NET Framework současně, což znamená, že můžete nainstalovat .NET Framework bez nutnosti odinstalování předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="4e42f-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="4e42f-112">Obecně platí, že byste neměli odinstalovat předchozí verze .NET Framework, protože na konkrétní verzi může záviset aplikace, kterou používáte, a v případě, že je tato verze odebrána, může dojít k přerušení.</span><span class="sxs-lookup"><span data-stu-id="4e42f-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="4e42f-113">Existuje rozdíl mezi verzí .NET Framework a verzí CLR:</span><span class="sxs-lookup"><span data-stu-id="4e42f-113">There is a difference between the .NET Framework version and the CLR version:</span></span>
> - <span data-ttu-id="4e42f-114">Verze .NET Framework je založena na sadě sestavení, které tvoří knihovnu tříd .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e42f-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="4e42f-115">Například verze .NET Framework zahrnují 4,5, 4.6.1 a 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="4e42f-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>
>- <span data-ttu-id="4e42f-116">Verze CLR je založená na modulu runtime, ve kterém se .NET Framework aplikace spouštějí.</span><span class="sxs-lookup"><span data-stu-id="4e42f-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="4e42f-117">Jedna verze modulu CLR obvykle podporuje více .NET Framework verzí.</span><span class="sxs-lookup"><span data-stu-id="4e42f-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="4e42f-118">Například CLR verze 4.0.30319. *xxxxx* podporuje .NET Framework verze 4 až 4.5.2, kde *xxxxx* je méně než 42000 a CLR verze 4.0.30319.42000 podporuje .NET Framework verze počínaje .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="4e42f-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2, where *xxxxx* is less than 42000, and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>
>
> <span data-ttu-id="4e42f-119">Další informace o verzích najdete v tématu [.NET Framework verze a závislosti](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="4e42f-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>

<span data-ttu-id="4e42f-120">Chcete-li získat seznam verzí .NET Framework nainstalovaných v počítači, získáte přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="4e42f-120">To get a list of the .NET Framework versions installed on a computer, you access the registry.</span></span> <span data-ttu-id="4e42f-121">K zobrazení registru nebo použití kódu k dotazování můžete použít Editor registru:</span><span class="sxs-lookup"><span data-stu-id="4e42f-121">You can either use the Registry Editor to view the registry or use code to query it:</span></span>

- <span data-ttu-id="4e42f-122">Najít novější verze .NET Framework (4,5 a novější):</span><span class="sxs-lookup"><span data-stu-id="4e42f-122">Find newer .NET Framework versions (4.5 and later):</span></span>
  - [<span data-ttu-id="4e42f-123">Vyhledání verzí .NET Framework pomocí Editoru registru</span><span class="sxs-lookup"><span data-stu-id="4e42f-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)
  - [<span data-ttu-id="4e42f-124">Použití kódu k dotazování registru pro .NET Framework verze</span><span class="sxs-lookup"><span data-stu-id="4e42f-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)
  - [<span data-ttu-id="4e42f-125">Použití PowerShellu k dotazování registru pro .NET Framework verze</span><span class="sxs-lookup"><span data-stu-id="4e42f-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)
- <span data-ttu-id="4e42f-126">Najít starší verze .NET Framework (1&#8211;4):</span><span class="sxs-lookup"><span data-stu-id="4e42f-126">Find older .NET Framework versions (1&#8211;4):</span></span>
  - [<span data-ttu-id="4e42f-127">Vyhledání verzí .NET Framework pomocí Editoru registru</span><span class="sxs-lookup"><span data-stu-id="4e42f-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
  - [<span data-ttu-id="4e42f-128">Použití kódu k dotazování registru pro .NET Framework verze</span><span class="sxs-lookup"><span data-stu-id="4e42f-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)

<span data-ttu-id="4e42f-129">Chcete-li získat seznam verzí modulu CLR nainstalovaných v počítači, použijte nástroj nebo kód:</span><span class="sxs-lookup"><span data-stu-id="4e42f-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>

- [<span data-ttu-id="4e42f-130">Použití nástroje Clrver</span><span class="sxs-lookup"><span data-stu-id="4e42f-130">Use the Clrver tool</span></span>](#clr_a)
- [<span data-ttu-id="4e42f-131">Použití kódu pro dotazování třídy prostředí</span><span class="sxs-lookup"><span data-stu-id="4e42f-131">Use code to query the Environment class</span></span>](#clr_b)

<span data-ttu-id="4e42f-132">Informace o zjišťování nainstalovaných aktualizací pro každou verzi .NET Framework najdete v tématu [How to: Určete, které aktualizace .NET Framework jsou](how-to-determine-which-net-framework-updates-are-installed.md)nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="4e42f-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="4e42f-133">Najít novější verze .NET Framework (4,5 a novější)</span><span class="sxs-lookup"><span data-stu-id="4e42f-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<a name="net_b"></a>

### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="4e42f-134">Najít .NET Framework verze 4,5 a novější v registru</span><span class="sxs-lookup"><span data-stu-id="4e42f-134">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="4e42f-135">V nabídce **Start** klikněte na příkaz **Spustit**, zadejte *příkaz regedit*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="4e42f-135">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="4e42f-136">Chcete-li spustit nástroj Regedit, musíte mít pověření správce.</span><span class="sxs-lookup"><span data-stu-id="4e42f-136">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="4e42f-137">V editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="4e42f-137">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="4e42f-138">Pokud není přítomen **úplný** podklíč, nemáte nainstalovanou .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="4e42f-138">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4e42f-139">Složka pro **instalaci rozhraní .NET Framework** v registru nezačíná tečkou.</span><span class="sxs-lookup"><span data-stu-id="4e42f-139">The **NET Framework Setup** folder in the registry does *not* begin with a period.</span></span>

3. <span data-ttu-id="4e42f-140">Vyhledejte položku DWORD s názvem **release**.</span><span class="sxs-lookup"><span data-stu-id="4e42f-140">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="4e42f-141">Pokud existuje, budete mít nainstalované .NET Framework 4,5 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="4e42f-141">If it exists, then you have .NET Framework 4.5 or later versions installed.</span></span> <span data-ttu-id="4e42f-142">Jeho hodnota je klíč verze, který odpovídá konkrétní verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e42f-142">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="4e42f-143">Na následujícím obrázku je například hodnota položky **release** *378389*, což je klíč verze .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="4e42f-143">In the following figure, for example, the value of the **Release** entry is *378389*, which is the release key for .NET Framework 4.5.</span></span>

     <span data-ttu-id="4e42f-144">![Položka registru pro .NET Framework 4,5](media/clr-installdir.png "Položka registru pro .NET Framework 4,5")</span><span class="sxs-lookup"><span data-stu-id="4e42f-144">![Registry entry for the .NET Framework 4.5](media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="4e42f-145">V následující tabulce je uvedena hodnota DWORD **verze** v jednotlivých operačních systémech .NET Framework 4,5 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="4e42f-145">The following table lists the value of the **Release** DWORD on individual operating systems for .NET Framework 4.5 and later versions.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="4e42f-146">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4e42f-146">.NET Framework version</span></span>|<span data-ttu-id="4e42f-147">Hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="4e42f-147">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="4e42f-148">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="4e42f-148">.NET Framework 4.5</span></span>|<span data-ttu-id="4e42f-149">Všechny operační systémy Windows: 378389</span><span class="sxs-lookup"><span data-stu-id="4e42f-149">All Windows operating systems: 378389</span></span>|
|<span data-ttu-id="4e42f-150">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="4e42f-150">.NET Framework 4.5.1</span></span>|<span data-ttu-id="4e42f-151">V Windows 8.1 a Windows Server 2012 R2: 378675</span><span class="sxs-lookup"><span data-stu-id="4e42f-151">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="4e42f-152">Ve všech ostatních operačních systémech Windows: 378758</span><span class="sxs-lookup"><span data-stu-id="4e42f-152">On all other Windows operating systems: 378758</span></span>|
|<span data-ttu-id="4e42f-153">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="4e42f-153">.NET Framework 4.5.2</span></span>|<span data-ttu-id="4e42f-154">Všechny operační systémy Windows: 379893</span><span class="sxs-lookup"><span data-stu-id="4e42f-154">All Windows operating systems: 379893</span></span>|
|<span data-ttu-id="4e42f-155">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="4e42f-155">.NET Framework 4.6</span></span>|<span data-ttu-id="4e42f-156">Ve Windows 10: 393295</span><span class="sxs-lookup"><span data-stu-id="4e42f-156">On Windows 10: 393295</span></span><br /><span data-ttu-id="4e42f-157">Ve všech ostatních operačních systémech Windows: 393297</span><span class="sxs-lookup"><span data-stu-id="4e42f-157">On all other Windows operating systems: 393297</span></span>|
|<span data-ttu-id="4e42f-158">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="4e42f-158">.NET Framework 4.6.1</span></span>|<span data-ttu-id="4e42f-159">V systémech Windows 10 listopad Update: 394254</span><span class="sxs-lookup"><span data-stu-id="4e42f-159">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="4e42f-160">Ve všech ostatních operačních systémech Windows (včetně Windows 10): 394271</span><span class="sxs-lookup"><span data-stu-id="4e42f-160">On all other Windows operating systems (including Windows 10): 394271</span></span>|
|<span data-ttu-id="4e42f-161">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="4e42f-161">.NET Framework 4.6.2</span></span>|<span data-ttu-id="4e42f-162">Ve Windows 10 – aktualizace pro výročí a Windows Server 2016: 394802</span><span class="sxs-lookup"><span data-stu-id="4e42f-162">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="4e42f-163">Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 394806</span><span class="sxs-lookup"><span data-stu-id="4e42f-163">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span>|
|<span data-ttu-id="4e42f-164">Rozhraní .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="4e42f-164">.NET Framework 4.7</span></span>|<span data-ttu-id="4e42f-165">Ve Windows 10 Creators Update: 460798</span><span class="sxs-lookup"><span data-stu-id="4e42f-165">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="4e42f-166">Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 460805</span><span class="sxs-lookup"><span data-stu-id="4e42f-166">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span>|
|<span data-ttu-id="4e42f-167">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="4e42f-167">.NET Framework 4.7.1</span></span>|<span data-ttu-id="4e42f-168">V systému Windows 10 patří mezi tvůrci aktualizace a Windows Server verze 1709: 461308</span><span class="sxs-lookup"><span data-stu-id="4e42f-168">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="4e42f-169">Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 461310</span><span class="sxs-lookup"><span data-stu-id="4e42f-169">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span>|
|<span data-ttu-id="4e42f-170">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="4e42f-170">.NET Framework 4.7.2</span></span>|<span data-ttu-id="4e42f-171">Ve Windows 10. dubna 2018 Update a Windows Server verze 1803: 461808</span><span class="sxs-lookup"><span data-stu-id="4e42f-171">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="4e42f-172">Ve všech operačních systémech Windows s výjimkou Windows 10 dubna 2018 Update a Windows Server verze 1803: 461814</span><span class="sxs-lookup"><span data-stu-id="4e42f-172">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span>|
|<span data-ttu-id="4e42f-173">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="4e42f-173">.NET Framework 4.8</span></span>|<span data-ttu-id="4e42f-174">Ve Windows 10 může aktualizace 2019: 528040</span><span class="sxs-lookup"><span data-stu-id="4e42f-174">On Windows 10 May 2019 Update: 528040</span></span><br/><span data-ttu-id="4e42f-175">Pro všechny ostatní operační systémy Windows (včetně dalších operačních systémů Windows 10): 528049</span><span class="sxs-lookup"><span data-stu-id="4e42f-175">On all others Windows operating systems (including other Windows 10 operating systems): 528049</span></span>|

<span data-ttu-id="4e42f-176">Tyto hodnoty můžete použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4e42f-176">You can use these values as follows:</span></span>

- <span data-ttu-id="4e42f-177">Chcete-li zjistit, zda je v konkrétní verzi operačního systému Windows nainstalována konkrétní verze .NET Framework, proveďte test, zda je hodnota DWORD **verze** *shodná s* hodnotou uvedenou v tabulce.</span><span class="sxs-lookup"><span data-stu-id="4e42f-177">To determine whether a specific version of the .NET Framework is installed on a particular version of the Windows operating system, test whether the **Release** DWORD value is *equal to* the value listed in the table.</span></span> <span data-ttu-id="4e42f-178">Chcete-li například zjistit, zda je v systému Windows 10 .NET Framework 4,6, proveďte test na hodnotu **verze** , která se *rovná* 393295.</span><span class="sxs-lookup"><span data-stu-id="4e42f-178">For example, to determine whether .NET Framework 4.6 is present on a Windows 10 system, test for the a **Release** value that is *equal to* 393295.</span></span>

- <span data-ttu-id="4e42f-179">Chcete-li zjistit, zda je k dispozici minimální verze .NET Framework, použijte pro tuto verzi hodnotu DWORD s nižší verzí.</span><span class="sxs-lookup"><span data-stu-id="4e42f-179">To determine whether a minimum version of the .NET Framework is present, use the smaller **RELEASE** DWORD value for that version.</span></span> <span data-ttu-id="4e42f-180">Například pokud vaše aplikace běží pod .NET Framework 4,6 nebo novější verzí, otestujte hodnotu DWORD **verze** , která je *větší nebo rovna* 393295.</span><span class="sxs-lookup"><span data-stu-id="4e42f-180">For example, if your application runs under .NET Framework 4.6 or a later version, test for a **RELEASE** DWORD value that is *greater than or equal to* 393295.</span></span> <span data-ttu-id="4e42f-181">Tabulku, která obsahuje pouze minimální hodnotu DWORD verze pro každou .NET Framework verzi, naleznete v části [minimální hodnoty dword verze pro .NET Framework 4,5 a novější verze](minimum-release-dword.md).</span><span class="sxs-lookup"><span data-stu-id="4e42f-181">For a table that lists only the minimum **RELEASE** DWORD value for each .NET Framework version, see [The minimum values of the Release DWORD for .NET Framework 4.5 and later versions](minimum-release-dword.md).</span></span>

- <span data-ttu-id="4e42f-182">Chcete-li otestovat více verzí, začněte testováním na hodnotu, která je *větší nebo rovna* menší hodnotě DWORD pro nejnovější verzi .NET Framework, a pak porovnejte hodnotu s menší hodnotou DWORD pro každou následnou dřívější verzi.</span><span class="sxs-lookup"><span data-stu-id="4e42f-182">To test for multiple versions, begin by testing for a value that is *greater than or equal to* the smaller DWORD value for the latest .NET Framework version, and then compare the value with the smaller DWORD value for each successive earlier version.</span></span> <span data-ttu-id="4e42f-183">Například pokud vaše aplikace vyžaduje .NET Framework 4,7 nebo novější a chcete určit konkrétní verzi .NET Framework přítomná, začněte testováním hodnoty DWORD **verze** , která je *větší nebo rovna* 461808 (menší hodnota DWORD hodnota pro .NET Framework 4.7.2).</span><span class="sxs-lookup"><span data-stu-id="4e42f-183">For example, if your application requires .NET Framework 4.7 or later and you want to determine the specific version of .NET Framework present, start by testing for a **RELEASE** DWORD value that is *great than or equal to* to 461808 (the smaller DWORD value for .NET Framework 4.7.2).</span></span> <span data-ttu-id="4e42f-184">Pak porovnejte hodnotu DWORD **verze** s menší hodnotou pro každou pozdější .NET Framework verzi.</span><span class="sxs-lookup"><span data-stu-id="4e42f-184">Then compare the **RELEASE** DWORD value with the smaller value for each later .NET Framework version.</span></span> <span data-ttu-id="4e42f-185">Tabulku, která obsahuje pouze minimální hodnotu DWORD verze pro každou .NET Framework verzi, naleznete v části [minimální hodnoty dword verze pro .NET Framework 4,5 a novější verze](minimum-release-dword.md).</span><span class="sxs-lookup"><span data-stu-id="4e42f-185">For a table that lists only the minimum **RELEASE** DWORD value for each .NET Framework version, see [The minimum values of the Release DWORD for .NET Framework 4.5 and later versions](minimum-release-dword.md).</span></span>

<a name="net_d"></a>

### <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="4e42f-186">Najít .NET Framework verze 4,5 a novější s kódem</span><span class="sxs-lookup"><span data-stu-id="4e42f-186">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="4e42f-187">Použijte metody <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType>apro přístup k podklíči **Setup\NDP\v4\Full rozhraní HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework** v registru systému Windows. <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4e42f-187">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

    <span data-ttu-id="4e42f-188">Existence položky DWORD **verze** v podklíči **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** označuje, že v počítači je nainstalována .NET Framework 4,5 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="4e42f-188">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span>

2. <span data-ttu-id="4e42f-189">Zkontrolujte hodnotu položky **release** a určete nainstalovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="4e42f-189">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="4e42f-190">Chcete-li být kompatibilní s přesměrováním, vyhledejte hodnotu větší nebo rovnou hodnotě uvedené v [tabulce verze .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="4e42f-190">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="4e42f-191">Následující příklad zkontroluje hodnotu položky **release** v registru, aby bylo možné najít .NET Framework 4,5 a novější verze, které jsou nainstalovány:</span><span class="sxs-lookup"><span data-stu-id="4e42f-191">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="4e42f-192">Tento příklad se skládá z doporučené praxe pro kontrolu verzí:</span><span class="sxs-lookup"><span data-stu-id="4e42f-192">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="4e42f-193">Kontroluje, zda je hodnota položky **verze** *větší než nebo rovna* hodnotě známých klíčů pro vydání.</span><span class="sxs-lookup"><span data-stu-id="4e42f-193">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="4e42f-194">Kontroluje v pořadí od nejnovější verze k nejstarší verzi.</span><span class="sxs-lookup"><span data-stu-id="4e42f-194">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a>

### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="4e42f-195">Vyhledání minimální požadované verze .NET Framework (4,5 a novější) pomocí prostředí PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e42f-195">Check for a minimum-required .NET Framework version (4.5 and later) with PowerShell</span></span>

- <span data-ttu-id="4e42f-196">Pomocí příkazů PowerShellu zkontrolujete hodnotu položky **release** podklíče **Setup\NDP\v4\Full HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework** .</span><span class="sxs-lookup"><span data-stu-id="4e42f-196">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="4e42f-197">Následující příklady kontrolují hodnotu položky **verze** , abyste zjistili, jestli je nainstalovaná .NET Framework 4.6.2 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="4e42f-197">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="4e42f-198">Tento kód se `True` vrátí, pokud je nainstalován `False` , a jinak.</span><span class="sxs-lookup"><span data-stu-id="4e42f-198">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 }
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

<span data-ttu-id="4e42f-199">Chcete-li vyhledat jinou minimální požadovanou verzi .NET Framework, nahraďte *394802* v těchto příkladech hodnotou **Release** z [tabulky .NET Framework verze](#version_table).</span><span class="sxs-lookup"><span data-stu-id="4e42f-199">To check for a different minimum-required .NET Framework version, replace *394802* in these examples with a **Release** value from the [.NET Framework version table](#version_table).</span></span>

## <a name="find-older-net-framework-versions-182114"></a><span data-ttu-id="4e42f-200">Najít starší verze .NET Frameworku (&#8211;1 4)</span><span class="sxs-lookup"><span data-stu-id="4e42f-200">Find older .NET Framework versions (1&#8211;4)</span></span>

<a name="net_a"></a>

### <a name="find-net-framework-versions-182114-in-the-registry"></a><span data-ttu-id="4e42f-201">Najít .NET Framework verze 1&#8211;4 v registru</span><span class="sxs-lookup"><span data-stu-id="4e42f-201">Find .NET Framework versions 1&#8211;4 in the registry</span></span>

1. <span data-ttu-id="4e42f-202">V nabídce **Start** klikněte na příkaz **Spustit**, zadejte *příkaz regedit*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="4e42f-202">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="4e42f-203">Chcete-li spustit nástroj Regedit, musíte mít pověření správce.</span><span class="sxs-lookup"><span data-stu-id="4e42f-203">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="4e42f-204">V editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="4e42f-204">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>

    - <span data-ttu-id="4e42f-205">Pro .NET Framework verze 1,1 až 3,5 je každá nainstalovaná verze uvedena jako podklíč v podklíči **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** .</span><span class="sxs-lookup"><span data-stu-id="4e42f-205">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="4e42f-206">Například **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="4e42f-206">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="4e42f-207">Číslo verze je uloženo jako hodnota v položce **verze** podklíče verze.</span><span class="sxs-lookup"><span data-stu-id="4e42f-207">The version number is stored as a value in the version subkey's **Version** entry.</span></span>

    - <span data-ttu-id="4e42f-208">V případě .NET Framework 4 je položka **verze** pod podklíčem **Setup\NDP\v4.0\Client rozhraní HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework** , **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** podklíče nebo pod oběma podklíči.</span><span class="sxs-lookup"><span data-stu-id="4e42f-208">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4e42f-209">Složka pro **instalaci rozhraní .NET Framework** v registru nezačíná tečkou.</span><span class="sxs-lookup"><span data-stu-id="4e42f-209">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="4e42f-210">Následující obrázek ukazuje podklíč a jeho položku **verze** pro .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="4e42f-210">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="4e42f-211">![Položka registru pro .NET Framework 3,5.](media/net-4-and-earlier.png ".NET Framework 3,5 a starší verze")</span><span class="sxs-lookup"><span data-stu-id="4e42f-211">![The registry entry for the .NET Framework 3.5.](media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a>

### <a name="find-net-framework-versions-182114-with-code"></a><span data-ttu-id="4e42f-212">Najít .NET Framework verze 1&#8211;4 s kódem</span><span class="sxs-lookup"><span data-stu-id="4e42f-212">Find .NET Framework versions 1&#8211;4 with code</span></span>

- <span data-ttu-id="4e42f-213">Použijte třídu pro přístup k podklíči **Setup\NDP rozhraní HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework** v registru systému Windows. <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4e42f-213">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="4e42f-214">Následující příklad najde nainstalované verze .NET Framework 1&#8211;4:</span><span class="sxs-lookup"><span data-stu-id="4e42f-214">The following example finds the .NET Framework 1&#8211;4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="4e42f-215">Najít verze CLR</span><span class="sxs-lookup"><span data-stu-id="4e42f-215">Find CLR versions</span></span>

<a name="clr_a"></a>

### <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="4e42f-216">Vyhledat aktuální verzi CLR pomocí nástroje Clrver. exe</span><span class="sxs-lookup"><span data-stu-id="4e42f-216">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="4e42f-217">K určení, které verze modulu CLR jsou nainstalovány v počítači, použijte [Nástroj verze CLR (Clrver. exe)](../tools/clrver-exe-clr-version-tool.md) :</span><span class="sxs-lookup"><span data-stu-id="4e42f-217">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="4e42f-218">Z [Developer Command Prompt pro Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs)zadejte `clrver`.</span><span class="sxs-lookup"><span data-stu-id="4e42f-218">From a [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), enter `clrver`.</span></span>

    <span data-ttu-id="4e42f-219">Ukázkový výstup:</span><span class="sxs-lookup"><span data-stu-id="4e42f-219">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="4e42f-220">Vyhledat aktuální verzi CLR pomocí třídy Environment</span><span class="sxs-lookup"><span data-stu-id="4e42f-220">Find the current CLR version with the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e42f-221">U .NET Framework 4,5 a novějších verzí Nepoužívejte <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost k detekci verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="4e42f-221">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="4e42f-222">Místo toho proveďte dotaz na registr, jak je popsáno v části [Find .NET Framework verze 4,5 a novější s kódem](#net_d).</span><span class="sxs-lookup"><span data-stu-id="4e42f-222">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="4e42f-223">Dotaz na <xref:System.Environment.Version?displayProperty=nameWithType> vlastnost pro <xref:System.Version> načtení objektu.</span><span class="sxs-lookup"><span data-stu-id="4e42f-223">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

    <span data-ttu-id="4e42f-224">Vrácený `System.Version` objekt identifikuje verzi modulu runtime, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="4e42f-224">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="4e42f-225">Nevrací verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="4e42f-225">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="4e42f-226">Pro .NET Framework verze 4, 4,5, 4.5.1 a 4.5.2 má řetězcová reprezentace vráceného <xref:System.Version> objektu formu 4.0.30319. *xxxxx*, kde *xxxxx* je menší než 42000.</span><span class="sxs-lookup"><span data-stu-id="4e42f-226">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="4e42f-227">U .NET Framework 4,6 a novějších verzí má formulář 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="4e42f-227">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

2. <span data-ttu-id="4e42f-228">Po provedení tohoto `Version` objektu se proveďte dotazování následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4e42f-228">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="4e42f-229">Pro hlavní identifikátor vydaných verzí (například *4* pro verzi 4,0) použijte <xref:System.Version.Major%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4e42f-229">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="4e42f-230">V případě identifikátoru podverze (například *0* pro verzi 4,0) použijte <xref:System.Version.Minor%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4e42f-230">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="4e42f-231">Pro celý řetězec verze (například *4.0.30319.18010*) použijte <xref:System.Version.ToString%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="4e42f-231">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4e42f-232">Tato metoda vrátí jednu hodnotu, která odráží verzi modulu runtime, který spouští kód.</span><span class="sxs-lookup"><span data-stu-id="4e42f-232">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="4e42f-233">Nevrací verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="4e42f-233">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

<span data-ttu-id="4e42f-234">Následující příklad používá <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost k načtení informací o verzi CLR:</span><span class="sxs-lookup"><span data-stu-id="4e42f-234">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="4e42f-235">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e42f-235">See also</span></span>

- [<span data-ttu-id="4e42f-236">Postupy: Určení nainstalovaných aktualizací .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4e42f-236">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="4e42f-237">Instalace .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="4e42f-237">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="4e42f-238">.NET Framework verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="4e42f-238">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
