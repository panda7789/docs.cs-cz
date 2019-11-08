---
title: Určit, které verze .NET Framework jsou nainstalovány
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: b860aac01780acb67c53e822eff478b78198996b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738186"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="1728c-102">Postupy: určení, které verze .NET Framework jsou nainstalovány</span><span class="sxs-lookup"><span data-stu-id="1728c-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="1728c-103">Uživatelé mohou na svých počítačích [instalovat](../install/index.md) a spouštět více verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1728c-103">Users can [install](../install/index.md) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="1728c-104">Když vyvíjíte nebo nasazujete aplikaci, možná budete potřebovat informace o tom, které verze .NET Framework jsou nainstalovány v počítači uživatele.</span><span class="sxs-lookup"><span data-stu-id="1728c-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span>

<span data-ttu-id="1728c-105">.NET Framework se skládá ze dvou hlavních součástí, které jsou ve verzi samostatně:</span><span class="sxs-lookup"><span data-stu-id="1728c-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="1728c-106">Sada sestavení, což jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="1728c-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="1728c-107">.NET Framework a sestavení sdílejí stejné číslo verze.</span><span class="sxs-lookup"><span data-stu-id="1728c-107">The .NET Framework and assemblies share the same version number.</span></span>

- <span data-ttu-id="1728c-108">Modul CLR (Common Language Runtime), který spravuje a spouští kód vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="1728c-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="1728c-109">Modul CLR je identifikován vlastním číslem verze (viz [verze a závislosti](versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="1728c-109">The CLR is identified by its own version number (see [Versions and dependencies](versions-and-dependencies.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="1728c-110">Každá nová verze rozhraní .NET Framework zachovává funkce předchozích verzí a přidává nové funkce.</span><span class="sxs-lookup"><span data-stu-id="1728c-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="1728c-111">V jednom počítači můžete načíst několik verzí .NET Framework současně, což znamená, že můžete nainstalovat .NET Framework bez nutnosti odinstalování předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="1728c-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="1728c-112">Obecně platí, že byste neměli odinstalovat předchozí verze .NET Framework, protože na konkrétní verzi může záviset aplikace, kterou používáte, a v případě, že je tato verze odebrána, může dojít k přerušení.</span><span class="sxs-lookup"><span data-stu-id="1728c-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="1728c-113">Existuje rozdíl mezi verzí .NET Framework a verzí CLR:</span><span class="sxs-lookup"><span data-stu-id="1728c-113">There is a difference between the .NET Framework version and the CLR version:</span></span>
>
> - <span data-ttu-id="1728c-114">Verze .NET Framework je založena na sadě sestavení, které tvoří knihovnu tříd .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1728c-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="1728c-115">Například verze .NET Framework zahrnují 4,5, 4.6.1 a 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="1728c-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>
> - <span data-ttu-id="1728c-116">Verze CLR je založená na modulu runtime, ve kterém se .NET Framework aplikace spouštějí.</span><span class="sxs-lookup"><span data-stu-id="1728c-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="1728c-117">Jedna verze modulu CLR obvykle podporuje více .NET Framework verzí.</span><span class="sxs-lookup"><span data-stu-id="1728c-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="1728c-118">Například CLR verze 4.0.30319. *xxxxx* podporuje .NET Framework verze 4 až 4.5.2, kde *xxxxx* je méně než 42000 a CLR verze 4.0.30319.42000 podporuje .NET Framework verze počínaje .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="1728c-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2, where *xxxxx* is less than 42000, and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>
>
> <span data-ttu-id="1728c-119">Další informace o verzích najdete v tématu [.NET Framework verze a závislosti](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="1728c-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>

<span data-ttu-id="1728c-120">Registr obsahuje seznam verzí .NET Framework nainstalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="1728c-120">The registry contains a list of the .NET Framework versions installed on a computer.</span></span> <span data-ttu-id="1728c-121">Můžete použít Editor registru k zobrazení registru nebo k jeho dotazování s kódem:</span><span class="sxs-lookup"><span data-stu-id="1728c-121">You can either use the Registry Editor to view the registry or query it with code:</span></span>

- <span data-ttu-id="1728c-122">Najít novější verze .NET Framework (4,5 a novější):</span><span class="sxs-lookup"><span data-stu-id="1728c-122">Find newer .NET Framework versions (4.5 and later):</span></span>

  - [<span data-ttu-id="1728c-123">Vyhledání verzí .NET Framework pomocí Editoru registru</span><span class="sxs-lookup"><span data-stu-id="1728c-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)
  - [<span data-ttu-id="1728c-124">Použití kódu k dotazování registru pro .NET Framework verze</span><span class="sxs-lookup"><span data-stu-id="1728c-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)
  - [<span data-ttu-id="1728c-125">Použití PowerShellu k dotazování registru pro .NET Framework verze</span><span class="sxs-lookup"><span data-stu-id="1728c-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)

- <span data-ttu-id="1728c-126">Najít starší verze .NET Framework (1 až 4):</span><span class="sxs-lookup"><span data-stu-id="1728c-126">Find older .NET Framework versions (1 through 4):</span></span>

  - [<span data-ttu-id="1728c-127">Vyhledání verzí .NET Framework pomocí Editoru registru</span><span class="sxs-lookup"><span data-stu-id="1728c-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
  - [<span data-ttu-id="1728c-128">Použití kódu k dotazování registru pro .NET Framework verze</span><span class="sxs-lookup"><span data-stu-id="1728c-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)

<span data-ttu-id="1728c-129">Chcete-li získat seznam verzí modulu CLR nainstalovaných v počítači, použijte nástroj nebo kód:</span><span class="sxs-lookup"><span data-stu-id="1728c-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>

- [<span data-ttu-id="1728c-130">Použití nástroje Clrver</span><span class="sxs-lookup"><span data-stu-id="1728c-130">Use the Clrver tool</span></span>](#clr_a)
- [<span data-ttu-id="1728c-131">Použití kódu pro dotazování třídy prostředí</span><span class="sxs-lookup"><span data-stu-id="1728c-131">Use code to query the Environment class</span></span>](#clr_b)

<span data-ttu-id="1728c-132">Informace o zjišťování nainstalovaných aktualizací pro každou verzi .NET Framework najdete v tématu [How to: Určete, které .NET Framework aktualizace se mají nainstalovat](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="1728c-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="1728c-133">Najít novější verze .NET Framework (4,5 a novější)</span><span class="sxs-lookup"><span data-stu-id="1728c-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<span data-ttu-id="1728c-134">Editor registru můžete použít k vyhledání informací o verzi v registru nebo k zaregistrování registru prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="1728c-134">You can use Registry Editor to find version information in the registry, or you can query the registry programmatically.</span></span>

<a name="net_b"></a>

### <a name="use-registry-editor"></a><span data-ttu-id="1728c-135">Použití Editoru registru</span><span class="sxs-lookup"><span data-stu-id="1728c-135">Use Registry Editor</span></span>

1. <span data-ttu-id="1728c-136">V nabídce **Start** klikněte na příkaz **Spustit**, zadejte *příkaz regedit*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="1728c-136">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="1728c-137">Chcete-li spustit nástroj Regedit, musíte mít pověření správce.</span><span class="sxs-lookup"><span data-stu-id="1728c-137">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="1728c-138">V editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="1728c-138">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="1728c-139">Pokud není přítomen **úplný** podklíč, nemáte nainstalovanou .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="1728c-139">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1728c-140">Složka pro **instalaci rozhraní .NET Framework** v registru *nezačíná tečkou* .</span><span class="sxs-lookup"><span data-stu-id="1728c-140">The **NET Framework Setup** folder in the registry does *not* begin with a period.</span></span>

3. <span data-ttu-id="1728c-141">Vyhledejte položku DWORD s názvem **release**.</span><span class="sxs-lookup"><span data-stu-id="1728c-141">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="1728c-142">Pokud existuje, budete mít nainstalované .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="1728c-142">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="1728c-143">Jeho hodnota je klíč verze, který odpovídá konkrétní verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1728c-143">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="1728c-144">Na následujícím obrázku je například hodnota položky **release** 378389, což je klíč verze .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="1728c-144">In the following figure, for example, the value of the **Release** entry is 378389, which is the release key for .NET Framework 4.5.</span></span>

   <span data-ttu-id="1728c-145">![Položka registru pro .NET Framework 4,5](./media/clr-installdir.png "Položka registru pro .NET Framework 4,5")</span><span class="sxs-lookup"><span data-stu-id="1728c-145">![Registry entry for the .NET Framework 4.5](./media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="1728c-146">V následující tabulce je uvedena hodnota DWORD **verze** v jednotlivých operačních systémech .NET Framework 4,5 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="1728c-146">The following table lists the value of the **Release** DWORD on individual operating systems for .NET Framework 4.5 and later versions.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="1728c-147">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1728c-147">.NET Framework version</span></span>|<span data-ttu-id="1728c-148">Hodnota DWORD verze</span><span class="sxs-lookup"><span data-stu-id="1728c-148">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="1728c-149">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="1728c-149">.NET Framework 4.5</span></span>|<span data-ttu-id="1728c-150">Všechny operační systémy Windows: 378389</span><span class="sxs-lookup"><span data-stu-id="1728c-150">All Windows operating systems: 378389</span></span>|
|<span data-ttu-id="1728c-151">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="1728c-151">.NET Framework 4.5.1</span></span>|<span data-ttu-id="1728c-152">V Windows 8.1 a Windows Server 2012 R2:378675</span><span class="sxs-lookup"><span data-stu-id="1728c-152">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="1728c-153">Ve všech ostatních operačních systémech Windows: 378758</span><span class="sxs-lookup"><span data-stu-id="1728c-153">On all other Windows operating systems: 378758</span></span>|
|<span data-ttu-id="1728c-154">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="1728c-154">.NET Framework 4.5.2</span></span>|<span data-ttu-id="1728c-155">Všechny operační systémy Windows: 379893</span><span class="sxs-lookup"><span data-stu-id="1728c-155">All Windows operating systems: 379893</span></span>|
|<span data-ttu-id="1728c-156">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="1728c-156">.NET Framework 4.6</span></span>|<span data-ttu-id="1728c-157">Ve Windows 10:393295</span><span class="sxs-lookup"><span data-stu-id="1728c-157">On Windows 10: 393295</span></span><br /><span data-ttu-id="1728c-158">Ve všech ostatních operačních systémech Windows: 393297</span><span class="sxs-lookup"><span data-stu-id="1728c-158">On all other Windows operating systems: 393297</span></span>|
|<span data-ttu-id="1728c-159">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="1728c-159">.NET Framework 4.6.1</span></span>|<span data-ttu-id="1728c-160">V systémech Windows 10 listopad Update: 394254</span><span class="sxs-lookup"><span data-stu-id="1728c-160">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="1728c-161">Ve všech ostatních operačních systémech Windows (včetně Windows 10): 394271</span><span class="sxs-lookup"><span data-stu-id="1728c-161">On all other Windows operating systems (including Windows 10): 394271</span></span>|
|<span data-ttu-id="1728c-162">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="1728c-162">.NET Framework 4.6.2</span></span>|<span data-ttu-id="1728c-163">Ve Windows 10 – aktualizace pro výročí a Windows Server 2016:394802</span><span class="sxs-lookup"><span data-stu-id="1728c-163">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="1728c-164">Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 394806</span><span class="sxs-lookup"><span data-stu-id="1728c-164">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span>|
|<span data-ttu-id="1728c-165">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="1728c-165">.NET Framework 4.7</span></span>|<span data-ttu-id="1728c-166">Ve Windows 10 Creators Update: 460798</span><span class="sxs-lookup"><span data-stu-id="1728c-166">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="1728c-167">Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 460805</span><span class="sxs-lookup"><span data-stu-id="1728c-167">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span>|
|<span data-ttu-id="1728c-168">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="1728c-168">.NET Framework 4.7.1</span></span>|<span data-ttu-id="1728c-169">V systému Windows 10 patří mezi tvůrci aktualizace a Windows Server verze 1709:461308</span><span class="sxs-lookup"><span data-stu-id="1728c-169">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="1728c-170">Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 461310</span><span class="sxs-lookup"><span data-stu-id="1728c-170">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span>|
|<span data-ttu-id="1728c-171">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="1728c-171">.NET Framework 4.7.2</span></span>|<span data-ttu-id="1728c-172">Ve Windows 10. dubna 2018 Update a Windows Server verze 1803:461808</span><span class="sxs-lookup"><span data-stu-id="1728c-172">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="1728c-173">Ve všech operačních systémech Windows s výjimkou Windows 10 dubna 2018 Update a Windows Server verze 1803:461814</span><span class="sxs-lookup"><span data-stu-id="1728c-173">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span>|
|<span data-ttu-id="1728c-174">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="1728c-174">.NET Framework 4.8</span></span>|<span data-ttu-id="1728c-175">Ve Windows 10 května 2019 Update a Windows 10 listopadu 2019 Update: 528040</span><span class="sxs-lookup"><span data-stu-id="1728c-175">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="1728c-176">Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 528049</span><span class="sxs-lookup"><span data-stu-id="1728c-176">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span>|

#### <a name="specific-version"></a><span data-ttu-id="1728c-177">Specific version (Konkrétní verze)</span><span class="sxs-lookup"><span data-stu-id="1728c-177">Specific version</span></span>

<span data-ttu-id="1728c-178">Chcete-li zjistit, zda je v konkrétní verzi operačního systému Windows nainstalována *konkrétní* verze .NET Framework, proveďte test, zda je hodnota DWORD **verze** *shodná s* hodnotou uvedenou v tabulce.</span><span class="sxs-lookup"><span data-stu-id="1728c-178">To determine whether a *specific* version of the .NET Framework is installed on a particular version of the Windows operating system, test whether the **Release** DWORD value is *equal to* the value listed in the table.</span></span> <span data-ttu-id="1728c-179">Chcete-li například zjistit, zda je v systému Windows 10 .NET Framework 4,6, proveďte test na hodnotu **verze** , která se *rovná* 393295.</span><span class="sxs-lookup"><span data-stu-id="1728c-179">For example, to determine whether .NET Framework 4.6 is present on a Windows 10 system, test for the a **Release** value that is *equal to* 393295.</span></span>

#### <a name="minimum-version"></a><span data-ttu-id="1728c-180">Minimální verze</span><span class="sxs-lookup"><span data-stu-id="1728c-180">Minimum version</span></span>

<span data-ttu-id="1728c-181">Chcete-li určit, zda je k dispozici *minimální* verze .NET Framework, použijte **hodnotu DWORD nejnižší verze pro** tuto verzi z předchozí tabulky.</span><span class="sxs-lookup"><span data-stu-id="1728c-181">To determine whether a *minimum* version of the .NET Framework is present, use the smallest **RELEASE** DWORD value for that version from the previous table.</span></span> <span data-ttu-id="1728c-182">(Pro usnadnění práce jsou uvedeny také minimální hodnoty v tabulce, která následuje.)</span><span class="sxs-lookup"><span data-stu-id="1728c-182">(For convenience, the minimum values are also listed in the table that follows.)</span></span>

<span data-ttu-id="1728c-183">Například pokud vaše aplikace běží pod .NET Framework 4,8 nebo novější verzí, otestujte hodnotu DWORD **verze** , která je *větší nebo rovna* 528040.</span><span class="sxs-lookup"><span data-stu-id="1728c-183">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **RELEASE** DWORD value that is *greater than or equal to* 528040.</span></span>

|<span data-ttu-id="1728c-184">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1728c-184">.NET Framework version</span></span>|<span data-ttu-id="1728c-185">Minimální hodnota pro DWORD verze</span><span class="sxs-lookup"><span data-stu-id="1728c-185">Minimum value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="1728c-186">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="1728c-186">.NET Framework 4.5</span></span>|<span data-ttu-id="1728c-187">378389</span><span class="sxs-lookup"><span data-stu-id="1728c-187">378389</span></span>|
|<span data-ttu-id="1728c-188">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="1728c-188">.NET Framework 4.5.1</span></span>|<span data-ttu-id="1728c-189">378675</span><span class="sxs-lookup"><span data-stu-id="1728c-189">378675</span></span>|
|<span data-ttu-id="1728c-190">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="1728c-190">.NET Framework 4.5.2</span></span>|<span data-ttu-id="1728c-191">379893</span><span class="sxs-lookup"><span data-stu-id="1728c-191">379893</span></span>|
|<span data-ttu-id="1728c-192">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="1728c-192">.NET Framework 4.6</span></span>|<span data-ttu-id="1728c-193">393295</span><span class="sxs-lookup"><span data-stu-id="1728c-193">393295</span></span>|
|<span data-ttu-id="1728c-194">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="1728c-194">.NET Framework 4.6.1</span></span>|<span data-ttu-id="1728c-195">394254</span><span class="sxs-lookup"><span data-stu-id="1728c-195">394254</span></span>|
|<span data-ttu-id="1728c-196">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="1728c-196">.NET Framework 4.6.2</span></span>|<span data-ttu-id="1728c-197">394802</span><span class="sxs-lookup"><span data-stu-id="1728c-197">394802</span></span>|
|<span data-ttu-id="1728c-198">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="1728c-198">.NET Framework 4.7</span></span>|<span data-ttu-id="1728c-199">460798</span><span class="sxs-lookup"><span data-stu-id="1728c-199">460798</span></span>|
|<span data-ttu-id="1728c-200">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="1728c-200">.NET Framework 4.7.1</span></span>|<span data-ttu-id="1728c-201">461308</span><span class="sxs-lookup"><span data-stu-id="1728c-201">461308</span></span>|
|<span data-ttu-id="1728c-202">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="1728c-202">.NET Framework 4.7.2</span></span>|<span data-ttu-id="1728c-203">461808</span><span class="sxs-lookup"><span data-stu-id="1728c-203">461808</span></span>|
|<span data-ttu-id="1728c-204">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="1728c-204">.NET Framework 4.8</span></span>|<span data-ttu-id="1728c-205">528040</span><span class="sxs-lookup"><span data-stu-id="1728c-205">528040</span></span>|

#### <a name="multiple-versions"></a><span data-ttu-id="1728c-206">Více verzí</span><span class="sxs-lookup"><span data-stu-id="1728c-206">Multiple versions</span></span>

<span data-ttu-id="1728c-207">Chcete-li otestovat více verzí, začněte testováním na hodnotu, která je *větší nebo rovna* menší hodnotě DWORD pro nejnovější verzi .NET Framework, a pak porovnejte hodnotu s menší hodnotou DWORD pro každou následnou dřívější verzi.</span><span class="sxs-lookup"><span data-stu-id="1728c-207">To test for multiple versions, begin by testing for a value that is *greater than or equal to* the smaller DWORD value for the latest .NET Framework version, and then compare the value with the smaller DWORD value for each successive earlier version.</span></span> <span data-ttu-id="1728c-208">Například pokud vaše aplikace vyžaduje .NET Framework 4,7 nebo novější a chcete určit konkrétní verzi .NET Framework přítomná, začněte testováním hodnoty DWORD **verze** , která je *větší nebo rovna* 461808 (menší hodnota DWORD hodnota pro .NET Framework 4.7.2).</span><span class="sxs-lookup"><span data-stu-id="1728c-208">For example, if your application requires .NET Framework 4.7 or later and you want to determine the specific version of .NET Framework present, start by testing for a **RELEASE** DWORD value that is *great than or equal to* to 461808 (the smaller DWORD value for .NET Framework 4.7.2).</span></span> <span data-ttu-id="1728c-209">Pak porovnejte hodnotu DWORD **verze** s menší hodnotou pro každou pozdější .NET Framework verzi.</span><span class="sxs-lookup"><span data-stu-id="1728c-209">Then compare the **RELEASE** DWORD value with the smaller value for each later .NET Framework version.</span></span>

<a name="net_d"></a>

### <a name="query-the-registry-using-code"></a><span data-ttu-id="1728c-210">Dotazování registru pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="1728c-210">Query the registry using code</span></span>

1. <span data-ttu-id="1728c-211">Použijte metody <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> pro přístup k podklíči **Setup\NDP\v4\Full rozhraní HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework** v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1728c-211">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

   <span data-ttu-id="1728c-212">Existence položky DWORD **verze** v podklíči **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** označuje, že v počítači je nainstalována .NET Framework 4,5 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="1728c-212">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span>

2. <span data-ttu-id="1728c-213">Zkontrolujte hodnotu položky **release** a určete nainstalovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="1728c-213">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="1728c-214">Chcete-li být kompatibilní s přesměrováním, vyhledejte hodnotu větší nebo rovnou hodnotě uvedené v [tabulce verze .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="1728c-214">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="1728c-215">Následující příklad zkontroluje hodnotu položky **release** v registru, aby bylo možné najít .NET Framework 4,5 a novější verze, které jsou nainstalovány:</span><span class="sxs-lookup"><span data-stu-id="1728c-215">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="1728c-216">Tento příklad se skládá z doporučené praxe pro kontrolu verzí:</span><span class="sxs-lookup"><span data-stu-id="1728c-216">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="1728c-217">Kontroluje, zda je hodnota položky **verze** *větší než nebo rovna* hodnotě známých klíčů pro vydání.</span><span class="sxs-lookup"><span data-stu-id="1728c-217">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="1728c-218">Kontroluje v pořadí od nejnovější verze k nejstarší verzi.</span><span class="sxs-lookup"><span data-stu-id="1728c-218">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a>

### <a name="use-powershell-to-check-for-a-minimum-required-version"></a><span data-ttu-id="1728c-219">Použití PowerShellu k vyhledání minimální požadované verze</span><span class="sxs-lookup"><span data-stu-id="1728c-219">Use PowerShell to check for a minimum-required version</span></span>

<span data-ttu-id="1728c-220">Pomocí příkazů PowerShellu zkontrolujete hodnotu položky **release** podklíče **Setup\NDP\v4\Full HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework** .</span><span class="sxs-lookup"><span data-stu-id="1728c-220">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="1728c-221">Následující příklady kontrolují hodnotu položky **verze** , abyste zjistili, jestli je nainstalovaná .NET Framework 4.6.2 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="1728c-221">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="1728c-222">Tento kód vrátí `True`, pokud je nainstalován, a `False` jinak.</span><span class="sxs-lookup"><span data-stu-id="1728c-222">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

<span data-ttu-id="1728c-223">Chcete-li vyhledat jinou minimální požadovanou verzi .NET Framework, nahraďte `394802` v příkladu hodnotou z [tabulky verze .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="1728c-223">To check for a different minimum-required .NET Framework version, replace `394802` in the example with a value from the [.NET Framework version table](#version_table).</span></span> <span data-ttu-id="1728c-224">Použijte nejnižší hodnotu zobrazenou pro tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="1728c-224">Use the smallest value shown for that version.</span></span>

## <a name="find-older-net-framework-versions-1-through-4"></a><span data-ttu-id="1728c-225">Najít starší verze .NET Framework (1 až 4)</span><span class="sxs-lookup"><span data-stu-id="1728c-225">Find older .NET Framework versions (1 through 4)</span></span>

<a name="net_a"></a>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="1728c-226">Použití Editoru registru (starší verze rozhraní)</span><span class="sxs-lookup"><span data-stu-id="1728c-226">Use Registry Editor (older framework versions)</span></span>

1. <span data-ttu-id="1728c-227">V nabídce **Start** klikněte na příkaz **Spustit**, zadejte *příkaz regedit*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="1728c-227">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="1728c-228">Chcete-li spustit nástroj Regedit, musíte mít pověření správce.</span><span class="sxs-lookup"><span data-stu-id="1728c-228">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="1728c-229">V editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="1728c-229">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>

    - <span data-ttu-id="1728c-230">Pro .NET Framework verze 1,1 až 3,5 je každá nainstalovaná verze uvedena jako podklíč v podklíči **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** .</span><span class="sxs-lookup"><span data-stu-id="1728c-230">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="1728c-231">Například **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="1728c-231">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="1728c-232">Číslo verze je uloženo jako hodnota v položce **verze** podklíče verze.</span><span class="sxs-lookup"><span data-stu-id="1728c-232">The version number is stored as a value in the version subkey's **Version** entry.</span></span>

    - <span data-ttu-id="1728c-233">V případě .NET Framework 4 je položka **verze** pod podklíčem **Setup\NDP\v4.0\Client rozhraní HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework** , **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** podklíče nebo pod oběma podklíči.</span><span class="sxs-lookup"><span data-stu-id="1728c-233">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1728c-234">Složka pro **instalaci rozhraní .NET Framework** v registru nezačíná tečkou.</span><span class="sxs-lookup"><span data-stu-id="1728c-234">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="1728c-235">Následující obrázek ukazuje podklíč a jeho položku **verze** pro .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="1728c-235">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="1728c-236">![Položka registru pro .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 a starší verze")</span><span class="sxs-lookup"><span data-stu-id="1728c-236">![The registry entry for the .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="1728c-237">Dotazování registru pomocí kódu (starší verze rozhraní)</span><span class="sxs-lookup"><span data-stu-id="1728c-237">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="1728c-238">Použijte třídu <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> pro přístup k podklíči **Setup\NDP rozhraní HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework** v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1728c-238">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="1728c-239">Následující příklad vyhledá .NET Framework 1 až 4 verze, které jsou nainstalovány:</span><span class="sxs-lookup"><span data-stu-id="1728c-239">The following example finds the .NET Framework 1 through 4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="1728c-240">Najít verze CLR</span><span class="sxs-lookup"><span data-stu-id="1728c-240">Find CLR versions</span></span>

<a name="clr_a"></a>

### <a name="use-clrverexe"></a><span data-ttu-id="1728c-241">Použití Clrver. exe</span><span class="sxs-lookup"><span data-stu-id="1728c-241">Use Clrver.exe</span></span>

<span data-ttu-id="1728c-242">K určení, které verze modulu CLR jsou nainstalovány v počítači, použijte [Nástroj verze CLR (Clrver. exe)](../tools/clrver-exe-clr-version-tool.md) :</span><span class="sxs-lookup"><span data-stu-id="1728c-242">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="1728c-243">Z [Developer Command Prompt pro Visual Studio](../tools/developer-command-prompt-for-vs.md)zadejte `clrver`.</span><span class="sxs-lookup"><span data-stu-id="1728c-243">From a [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), enter `clrver`.</span></span>

    <span data-ttu-id="1728c-244">Ukázkový výstup:</span><span class="sxs-lookup"><span data-stu-id="1728c-244">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="use-the-environment-class"></a><span data-ttu-id="1728c-245">Použití třídy Environment</span><span class="sxs-lookup"><span data-stu-id="1728c-245">Use the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1728c-246">U .NET Framework 4,5 a novějších verzí nepoužívejte vlastnost <xref:System.Environment.Version%2A?displayProperty=nameWithType> k detekci verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="1728c-246">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="1728c-247">Místo toho proveďte dotaz na registr, jak je popsáno v části [Find .NET Framework verze 4,5 a novější s kódem](#net_d).</span><span class="sxs-lookup"><span data-stu-id="1728c-247">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="1728c-248">Pomocí dotazu na vlastnost <xref:System.Environment.Version?displayProperty=nameWithType> načtěte objekt <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="1728c-248">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

    <span data-ttu-id="1728c-249">Vrácený objekt `System.Version` identifikuje verzi modulu runtime, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="1728c-249">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="1728c-250">Nevrací verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="1728c-250">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="1728c-251">Pro .NET Framework verze 4, 4,5, 4.5.1 a 4.5.2 má řetězcová reprezentace vráceného objektu <xref:System.Version> formu 4.0.30319. *xxxxx*, kde *xxxxx* je menší než 42000.</span><span class="sxs-lookup"><span data-stu-id="1728c-251">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="1728c-252">U .NET Framework 4,6 a novějších verzí má formulář 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="1728c-252">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

2. <span data-ttu-id="1728c-253">Až budete mít objekt `Version`, proveďte dotazování následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1728c-253">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="1728c-254">Pro hlavní identifikátor vydaných verzí (například *4* pro verzi 4,0) použijte vlastnost <xref:System.Version.Major%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1728c-254">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="1728c-255">Pro dílčí identifikátor vydání (například *0* pro verzi 4,0) použijte vlastnost <xref:System.Version.Minor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1728c-255">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="1728c-256">Pro celý řetězec verze (například *4.0.30319.18010*) použijte metodu <xref:System.Version.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1728c-256">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1728c-257">Tato metoda vrátí jednu hodnotu, která odráží verzi modulu runtime, který spouští kód.</span><span class="sxs-lookup"><span data-stu-id="1728c-257">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="1728c-258">Nevrací verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="1728c-258">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

<span data-ttu-id="1728c-259">Následující příklad používá vlastnost <xref:System.Environment.Version%2A?displayProperty=nameWithType> pro načtení informací o verzi CLR:</span><span class="sxs-lookup"><span data-stu-id="1728c-259">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="1728c-260">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1728c-260">See also</span></span>

- [<span data-ttu-id="1728c-261">Postupy: určení nainstalovaných aktualizací .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1728c-261">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="1728c-262">Instalace .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="1728c-262">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="1728c-263">.NET Framework verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="1728c-263">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
