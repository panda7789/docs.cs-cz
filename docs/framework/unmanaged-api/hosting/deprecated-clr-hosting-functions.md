---
title: Zastaralé funkce hostování CLR
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 083d0ff285abb4a99ad05c791bc504ff7f282c6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504365"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="4f361-102">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="4f361-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="4f361-103">Tato část popisuje nespravované globální statické funkce, které používají starší verze rozhraní API pro hostování.</span><span class="sxs-lookup"><span data-stu-id="4f361-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="4f361-104">S výjimkou funkcí infrastruktury ( `_Cor*` funkcí), které jsou používány pouze .NET Framework, jsou tyto funkce zastaralé v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4f361-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="4f361-105">Aktivační funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-105">Activation functions</span></span>  
 [<span data-ttu-id="4f361-106">ClrCreateManagedInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-106">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="4f361-107">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-107">Deprecated.</span></span> <span data-ttu-id="4f361-108">Vytvoří instanci zadaného spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="4f361-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="4f361-109">CoInitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-109">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="4f361-110">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="4f361-110">Obsolete.</span></span> <span data-ttu-id="4f361-111">Chcete-li inicializovat modul CLR (Common Language Runtime), použijte buď [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) nebo [CorBindToCurrentRuntime –](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="4f361-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="4f361-112">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-112">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="4f361-113">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-113">Deprecated.</span></span> <span data-ttu-id="4f361-114">Zajišťuje, aby byl spouštěcí modul modulu CLR načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="4f361-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="4f361-115">Místo toho použijte metodu [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4f361-115">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="4f361-116">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-116">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="4f361-117">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-117">Deprecated.</span></span> <span data-ttu-id="4f361-118">Načte modul CLR (Common Language Runtime) do procesu pomocí informací o verzi uložených v souboru XML.</span><span class="sxs-lookup"><span data-stu-id="4f361-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="4f361-119">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-119">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="4f361-120">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-120">Deprecated.</span></span> <span data-ttu-id="4f361-121">Umožňuje nespravovaným hostitelům načíst modul CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="4f361-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="4f361-122">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-122">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="4f361-123">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-123">Deprecated.</span></span> <span data-ttu-id="4f361-124">Načte CLR do procesu pomocí informací o verzi načtených ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="4f361-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="4f361-125">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-125">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="4f361-126">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-126">Deprecated.</span></span> <span data-ttu-id="4f361-127">Umožňuje nespravovaným hostitelům načíst modul CLR do procesu a umožňuje nastavit příznaky pro určení chování modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="4f361-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="4f361-128">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="4f361-129">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-129">Deprecated.</span></span> <span data-ttu-id="4f361-130">Umožňuje hostitelům načíst zadanou verzi modulu CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="4f361-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="4f361-131">GetCORRequiredVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-131">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="4f361-132">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-132">Deprecated.</span></span> <span data-ttu-id="4f361-133">Získá požadované číslo verze CLR.</span><span class="sxs-lookup"><span data-stu-id="4f361-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="4f361-134">GetCORSystemDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-134">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="4f361-135">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-135">Deprecated.</span></span> <span data-ttu-id="4f361-136">Vrátí instalační adresář modulu CLR, který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="4f361-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="4f361-137">GetRealProcAddress – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-137">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="4f361-138">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-138">Deprecated.</span></span> <span data-ttu-id="4f361-139">Získá adresu zadané funkce, která je exportována z nejnovější nainstalované verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="4f361-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="4f361-140">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-140">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="4f361-141">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-141">Deprecated.</span></span> <span data-ttu-id="4f361-142">Získá informace o verzi a adresáři modulu CLR, který požaduje aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f361-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="4f361-143">Funkce verze CLR</span><span class="sxs-lookup"><span data-stu-id="4f361-143">CLR version functions</span></span>  
 <span data-ttu-id="4f361-144">Funkce v této části vrátí verzi CLR; neaktivují modul CLR.</span><span class="sxs-lookup"><span data-stu-id="4f361-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="4f361-145">GetCORVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-145">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="4f361-146">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-146">Deprecated.</span></span> <span data-ttu-id="4f361-147">Vrátí číslo verze modulu CLR, který je spuštěn v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="4f361-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="4f361-148">GetFileVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-148">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="4f361-149">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-149">Deprecated.</span></span> <span data-ttu-id="4f361-150">Získá informace o verzi CLR zadaného souboru pomocí zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4f361-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="4f361-151">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-151">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="4f361-152">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-152">Deprecated.</span></span> <span data-ttu-id="4f361-153">Získá číslo verze modulu CLR požadované zadanou aplikací.</span><span class="sxs-lookup"><span data-stu-id="4f361-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="4f361-154">Pokud tato verze není nainstalovaná, získá nejnovější verzi, která je nainstalovaná před požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="4f361-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="4f361-155">GetRequestedRuntimeVersionForCLSID – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="4f361-156">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-156">Deprecated.</span></span> <span data-ttu-id="4f361-157">Získá příslušné informace o verzi CLR pro třídu se zadaným identifikátorem CLSID.</span><span class="sxs-lookup"><span data-stu-id="4f361-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="4f361-158">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-158">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="4f361-159">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-159">Deprecated.</span></span> <span data-ttu-id="4f361-160">Získá číslo verze modulu CLR, který je spojen se zadaným popisovačem procesu.</span><span class="sxs-lookup"><span data-stu-id="4f361-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="4f361-161">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-161">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="4f361-162">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-162">Deprecated.</span></span> <span data-ttu-id="4f361-163">Umožňuje hostiteli určit, která verze modulu CLR bude použita v rámci procesu před explicitním inicializací modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="4f361-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="4f361-164">Hostování funkcí</span><span class="sxs-lookup"><span data-stu-id="4f361-164">Hosting functions</span></span>  
 [<span data-ttu-id="4f361-165">CallFunctionShim – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-165">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="4f361-166">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-166">Deprecated.</span></span> <span data-ttu-id="4f361-167">Provede volání funkce, která má zadaný název a parametry v zadané knihovně.</span><span class="sxs-lookup"><span data-stu-id="4f361-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="4f361-168">CoEEShutDownCOM – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-168">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="4f361-169">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-169">Deprecated.</span></span> <span data-ttu-id="4f361-170">Uvolní sestavení modelu COM z procesu.</span><span class="sxs-lookup"><span data-stu-id="4f361-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="4f361-171">CorExitProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-171">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="4f361-172">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-172">Deprecated.</span></span> <span data-ttu-id="4f361-173">Ukončí aktuální nespravovaný proces.</span><span class="sxs-lookup"><span data-stu-id="4f361-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="4f361-174">CorLaunchApplication – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-174">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="4f361-175">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-175">Deprecated.</span></span> <span data-ttu-id="4f361-176">Spustí aplikaci v zadané síťové cestě s použitím zadaných manifestů a dalších aplikačních dat.</span><span class="sxs-lookup"><span data-stu-id="4f361-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="4f361-177">CorMarkThreadInThreadPool – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-177">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="4f361-178">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-178">Deprecated.</span></span> <span data-ttu-id="4f361-179">Označuje aktuálně spuštěné vlákno fondu vláken pro spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="4f361-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="4f361-180">Od verze .NET Framework 2,0 Tato funkce nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="4f361-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="4f361-181">Není požadován a lze jej odebrat z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="4f361-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="4f361-182">CoUninitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-182">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="4f361-183">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="4f361-183">Obsolete.</span></span> <span data-ttu-id="4f361-184">Modul CLR nelze z procesu uvolnit.</span><span class="sxs-lookup"><span data-stu-id="4f361-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="4f361-185">CoUninitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-185">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="4f361-186">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="4f361-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="4f361-187">CreateDebuggingInterfaceFromVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-187">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="4f361-188">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-188">Deprecated.</span></span> <span data-ttu-id="4f361-189">Vytvoří objekt [ICorDebug](../debugging/icordebug-interface.md) na základě zadaných informací o verzi.</span><span class="sxs-lookup"><span data-stu-id="4f361-189">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="4f361-190">CreateICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-190">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="4f361-191">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-191">Deprecated.</span></span> <span data-ttu-id="4f361-192">Vytvoří objekt [ICeeFileGen –](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="4f361-192">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="4f361-193">DestroyICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-193">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="4f361-194">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-194">Deprecated.</span></span> <span data-ttu-id="4f361-195">Odstraní objekt [ICeeFileGen –](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="4f361-195">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="4f361-196">FExecuteInAppDomainCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="4f361-196">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="4f361-197">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-197">Deprecated.</span></span> <span data-ttu-id="4f361-198">Odkazuje na funkci, kterou modul CLR volá ke spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="4f361-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="4f361-199">FLockClrVersionCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="4f361-199">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="4f361-200">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-200">Deprecated.</span></span> <span data-ttu-id="4f361-201">Odkazuje na funkci, kterou modul CLR volá, aby upozornil hostitele, že se inicializace spustila nebo je dokončená.</span><span class="sxs-lookup"><span data-stu-id="4f361-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="4f361-202">GetCLRIdentityManager – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-202">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="4f361-203">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-203">Deprecated.</span></span> <span data-ttu-id="4f361-204">Získá ukazatel na rozhraní, které umožňuje CLR spravovat identity.</span><span class="sxs-lookup"><span data-stu-id="4f361-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="4f361-205">LoadLibraryShim – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-205">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="4f361-206">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-206">Deprecated.</span></span> <span data-ttu-id="4f361-207">Načte zadanou verzi knihovny DLL .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f361-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="4f361-208">LoadStringRC – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-208">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="4f361-209">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-209">Deprecated.</span></span> <span data-ttu-id="4f361-210">Přeloží hodnotu HRESULT na chybovou zprávu pomocí výchozí jazykové verze aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="4f361-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="4f361-211">LoadStringRCEx – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-211">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="4f361-212">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-212">Deprecated.</span></span> <span data-ttu-id="4f361-213">Přeloží hodnotu HRESULT na příslušnou chybovou zprávu pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="4f361-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="4f361-214">LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="4f361-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="4f361-215">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-215">Deprecated.</span></span> <span data-ttu-id="4f361-216">Odkazuje na funkci, která upozorňuje hostitele, když je dokončeno překrytí (tj. asynchronní) vstupně-výstupní operace se zařízením.</span><span class="sxs-lookup"><span data-stu-id="4f361-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="4f361-217">LPTHREAD_START_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="4f361-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="4f361-218">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-218">Deprecated.</span></span> <span data-ttu-id="4f361-219">Odkazuje na funkci, která upozorňuje hostitele na spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="4f361-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="4f361-220">RunDll32ShimW – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-220">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="4f361-221">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-221">Deprecated.</span></span> <span data-ttu-id="4f361-222">Provede zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="4f361-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="4f361-223">WAITORTIMERCALLBACK – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="4f361-223">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="4f361-224">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="4f361-224">Deprecated.</span></span> <span data-ttu-id="4f361-225">Odkazuje na funkci, která upozorňuje hostitele na to, že došlo k signalizaci nebo vypršel časový limit čekání.</span><span class="sxs-lookup"><span data-stu-id="4f361-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="4f361-226">Funkce infrastruktury</span><span class="sxs-lookup"><span data-stu-id="4f361-226">Infrastructure functions</span></span>  
 <span data-ttu-id="4f361-227">Funkce v této části jsou používány pouze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f361-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="4f361-228">_CorDllMain – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-228">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="4f361-229">Inicializuje modul CLR, vyhledá spravovaný vstupní bod v záhlaví modulu CLR sestavení knihovny DLL a zahájí provádění.</span><span class="sxs-lookup"><span data-stu-id="4f361-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="4f361-230">_CorExeMain – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-230">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="4f361-231">Inicializuje modul CLR, vyhledá spravovaný vstupní bod v záhlaví modulu CLR spustitelného sestavení a zahájí provádění.</span><span class="sxs-lookup"><span data-stu-id="4f361-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="4f361-232">_CorExeMain2 – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-232">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="4f361-233">Provede vstupní bod v zadaném kódu mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="4f361-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="4f361-234">Tato funkce je volána zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="4f361-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="4f361-235">_CorImageUnloading – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-235">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="4f361-236">Upozorní zavaděče na Nenačtené bitové kopie spravovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="4f361-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="4f361-237">_CorValidateImage – funkce</span><span class="sxs-lookup"><span data-stu-id="4f361-237">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="4f361-238">Ověří bitové kopie spravovaného modulu a upozorní zavaděče operačního systému poté, co byly načteny.</span><span class="sxs-lookup"><span data-stu-id="4f361-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f361-239">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f361-239">See also</span></span>

- [<span data-ttu-id="4f361-240">Globální statické funkce .NET Framework 4 pro hostování</span><span class="sxs-lookup"><span data-stu-id="4f361-240">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
