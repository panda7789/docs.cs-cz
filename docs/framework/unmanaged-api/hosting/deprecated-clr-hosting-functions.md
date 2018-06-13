---
title: Zastaralé funkce hostování CLR
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d86f9b4903663604094895f6747b1407ff98c990
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435861"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="da587-102">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="da587-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="da587-103">Tato část popisuje nespravované globální statické funkce, které používají starší verze hostování rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="da587-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="da587-104">S výjimkou funkcí infrastruktury (`_Cor*` funkce), které jsou používány pouze rozhraní .NET Framework, tyto funkce jsou zastaralé v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da587-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="da587-105">Aktivace funkce</span><span class="sxs-lookup"><span data-stu-id="da587-105">Activation functions</span></span>  
 [<span data-ttu-id="da587-106">ClrCreateManagedInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-106">ClrCreateManagedInstance Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="da587-107">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-107">Deprecated.</span></span> <span data-ttu-id="da587-108">Vytvoří instanci je určeného spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="da587-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="da587-109">CoInitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-109">CoInitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 <span data-ttu-id="da587-110">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="da587-110">Obsolete.</span></span> <span data-ttu-id="da587-111">Chcete-li inicializovat modul CLR (CLR), použijte buď [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="da587-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="da587-112">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-112">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 <span data-ttu-id="da587-113">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-113">Deprecated.</span></span> <span data-ttu-id="da587-114">Zajišťuje, že je modul CLR provádění načtena do procesu.</span><span class="sxs-lookup"><span data-stu-id="da587-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="da587-115">Použití [iclrruntimehost::Start –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="da587-115">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="da587-116">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-116">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 <span data-ttu-id="da587-117">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-117">Deprecated.</span></span> <span data-ttu-id="da587-118">Načte modul CLR (CLR) do procesu pomocí verze informace uložené v souboru XML.</span><span class="sxs-lookup"><span data-stu-id="da587-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="da587-119">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-119">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 <span data-ttu-id="da587-120">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-120">Deprecated.</span></span> <span data-ttu-id="da587-121">Umožňuje nespravované hostitelé načíst modul CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="da587-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="da587-122">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-122">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="da587-123">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-123">Deprecated.</span></span> <span data-ttu-id="da587-124">Načte modul CLR do procesu pomocí informací o verzi, která je pro čtení ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="da587-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="da587-125">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-125">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 <span data-ttu-id="da587-126">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-126">Deprecated.</span></span> <span data-ttu-id="da587-127">Umožňuje načíst modul CLR do procesu nespravované hostitelům a umožňuje nastavit příznaky určit způsob chování modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="da587-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="da587-128">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 <span data-ttu-id="da587-129">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-129">Deprecated.</span></span> <span data-ttu-id="da587-130">Umožňuje hostitelům načíst zadaná verze modulu CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="da587-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="da587-131">GetCORRequiredVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-131">GetCORRequiredVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 <span data-ttu-id="da587-132">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-132">Deprecated.</span></span> <span data-ttu-id="da587-133">Získá požadované číslo verze CLR.</span><span class="sxs-lookup"><span data-stu-id="da587-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="da587-134">GetCORSystemDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-134">GetCORSystemDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 <span data-ttu-id="da587-135">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-135">Deprecated.</span></span> <span data-ttu-id="da587-136">Vrátí instalační adresář modulu CLR, který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="da587-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="da587-137">GetRealProcAddress – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-137">GetRealProcAddress Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 <span data-ttu-id="da587-138">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-138">Deprecated.</span></span> <span data-ttu-id="da587-139">Získá adresu zadaná funkce, který je exportován z nainstalované verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="da587-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="da587-140">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-140">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="da587-141">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-141">Deprecated.</span></span> <span data-ttu-id="da587-142">Získá informace o modulu CLR požadoval aplikace verzi a adresáře.</span><span class="sxs-lookup"><span data-stu-id="da587-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="da587-143">Funkce verze CLR</span><span class="sxs-lookup"><span data-stu-id="da587-143">CLR version functions</span></span>  
 <span data-ttu-id="da587-144">Funkce v této části vrátit verze CLR; Neaktivujte modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="da587-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="da587-145">GetCORVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-145">GetCORVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 <span data-ttu-id="da587-146">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-146">Deprecated.</span></span> <span data-ttu-id="da587-147">Vrátí číslo verze modulu CLR, který běží v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="da587-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="da587-148">GetFileVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-148">GetFileVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 <span data-ttu-id="da587-149">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-149">Deprecated.</span></span> <span data-ttu-id="da587-150">Získá informace o verzi CLR zadaného souboru, pomocí zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="da587-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="da587-151">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-151">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 <span data-ttu-id="da587-152">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-152">Deprecated.</span></span> <span data-ttu-id="da587-153">Získá číslo verze modulu CLR požadoval zadané aplikace.</span><span class="sxs-lookup"><span data-stu-id="da587-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="da587-154">Pokud není nainstalovaná této verze, získá nejnovější verzi, který se nainstaloval před požadovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="da587-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="da587-155">GetRequestedRuntimeVersionForCLSID – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="da587-156">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-156">Deprecated.</span></span> <span data-ttu-id="da587-157">Získá příslušné informace verze CLR pro třídu s zadaný CLSID.</span><span class="sxs-lookup"><span data-stu-id="da587-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="da587-158">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-158">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 <span data-ttu-id="da587-159">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-159">Deprecated.</span></span> <span data-ttu-id="da587-160">Získá číslo verze modulu CLR, která souvisí s popisovačem určený proces.</span><span class="sxs-lookup"><span data-stu-id="da587-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="da587-161">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-161">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 <span data-ttu-id="da587-162">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-162">Deprecated.</span></span> <span data-ttu-id="da587-163">Umožňuje hostiteli, chcete-li zjistit, kterou verzi modulu CLR se použije v procesu před explicitně inicializace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="da587-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="da587-164">Hostování funkcí</span><span class="sxs-lookup"><span data-stu-id="da587-164">Hosting functions</span></span>  
 [<span data-ttu-id="da587-165">CallFunctionShim – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-165">CallFunctionShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 <span data-ttu-id="da587-166">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-166">Deprecated.</span></span> <span data-ttu-id="da587-167">Zavolá funkci, která má zadaný název a parametry v určené knihovně.</span><span class="sxs-lookup"><span data-stu-id="da587-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="da587-168">CoEEShutDownCOM – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-168">CoEEShutDownCOM Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 <span data-ttu-id="da587-169">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-169">Deprecated.</span></span> <span data-ttu-id="da587-170">Uvolní sestavení modelu COM z procesu.</span><span class="sxs-lookup"><span data-stu-id="da587-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="da587-171">CorExitProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-171">CorExitProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 <span data-ttu-id="da587-172">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-172">Deprecated.</span></span> <span data-ttu-id="da587-173">Ukončí proces aktuální nespravované.</span><span class="sxs-lookup"><span data-stu-id="da587-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="da587-174">CorLaunchApplication – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-174">CorLaunchApplication Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 <span data-ttu-id="da587-175">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-175">Deprecated.</span></span> <span data-ttu-id="da587-176">Spuštění aplikace v zadané síťové cestě, pomocí zadané manifesty a ostatní data aplikací.</span><span class="sxs-lookup"><span data-stu-id="da587-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="da587-177">CorMarkThreadInThreadPool – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-177">CorMarkThreadInThreadPool Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="da587-178">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-178">Deprecated.</span></span> <span data-ttu-id="da587-179">Označí aktuálně prováděné vlákno fondu vláken pro spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="da587-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="da587-180">Od verze rozhraní .NET Framework verze 2.0, tato funkce nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="da587-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="da587-181">Není nutné a může být odebrán z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="da587-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="da587-182">CoUninitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-182">CoUninitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 <span data-ttu-id="da587-183">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="da587-183">Obsolete.</span></span> <span data-ttu-id="da587-184">Modul CLR nemůže být uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="da587-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="da587-185">CoUninitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-185">CoUninitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 <span data-ttu-id="da587-186">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="da587-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="da587-187">CreateDebuggingInterfaceFromVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-187">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="da587-188">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-188">Deprecated.</span></span> <span data-ttu-id="da587-189">Vytvoří [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objekt založený na informacích zadaná verze.</span><span class="sxs-lookup"><span data-stu-id="da587-189">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="da587-190">CreateICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-190">CreateICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 <span data-ttu-id="da587-191">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-191">Deprecated.</span></span> <span data-ttu-id="da587-192">Vytvoří [iceefilegen –](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="da587-192">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="da587-193">DestroyICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-193">DestroyICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 <span data-ttu-id="da587-194">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-194">Deprecated.</span></span> <span data-ttu-id="da587-195">Zničí [iceefilegen –](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="da587-195">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="da587-196">FExecuteInAppDomainCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="da587-196">FExecuteInAppDomainCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="da587-197">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-197">Deprecated.</span></span> <span data-ttu-id="da587-198">Odkazuje na funkci, která volá modulu CLR provést spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="da587-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="da587-199">FLockClrVersionCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="da587-199">FLockClrVersionCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="da587-200">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-200">Deprecated.</span></span> <span data-ttu-id="da587-201">Odkazuje na funkci, která volá modulu CLR oznámit hostitele tohoto inicializace má buď spustit nebo byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="da587-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="da587-202">GetCLRIdentityManager – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-202">GetCLRIdentityManager Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 <span data-ttu-id="da587-203">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-203">Deprecated.</span></span> <span data-ttu-id="da587-204">Získá ukazatel na rozhraní, které umožňuje spravovat identity modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="da587-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="da587-205">LoadLibraryShim – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-205">LoadLibraryShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 <span data-ttu-id="da587-206">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-206">Deprecated.</span></span> <span data-ttu-id="da587-207">Načte zadaný verzi knihovny DLL rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da587-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="da587-208">LoadStringRC – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-208">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 <span data-ttu-id="da587-209">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-209">Deprecated.</span></span> <span data-ttu-id="da587-210">Změní hodnotu HRESULT na chybovou zprávu pomocí výchozí jazykové verze aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="da587-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="da587-211">LoadStringRCEx – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-211">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 <span data-ttu-id="da587-212">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-212">Deprecated.</span></span> <span data-ttu-id="da587-213">Přeloží hodnotou HRESULT odpovídající chybové zprávy pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="da587-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="da587-214">LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="da587-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="da587-215">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-215">Deprecated.</span></span> <span data-ttu-id="da587-216">Odkazuje na funkci, která upozorní hostitele, když překryté (tedy asynchronní) vstupně-výstupních operací na zařízení byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="da587-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="da587-217">LPTHREAD_START_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="da587-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="da587-218">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-218">Deprecated.</span></span> <span data-ttu-id="da587-219">Odkazuje na funkci, která upozorní hostitele, který spustil vlákno k provedení.</span><span class="sxs-lookup"><span data-stu-id="da587-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="da587-220">RunDll32ShimW – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-220">RunDll32ShimW Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 <span data-ttu-id="da587-221">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-221">Deprecated.</span></span> <span data-ttu-id="da587-222">Provede zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="da587-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="da587-223">WAITORTIMERCALLBACK – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="da587-223">WAITORTIMERCALLBACK Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 <span data-ttu-id="da587-224">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="da587-224">Deprecated.</span></span> <span data-ttu-id="da587-225">Odkazuje na funkci, která upozorní hostitele, že popisovač čekání buď byla signál nebo vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="da587-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="da587-226">Funkce infrastruktury</span><span class="sxs-lookup"><span data-stu-id="da587-226">Infrastructure functions</span></span>  
 <span data-ttu-id="da587-227">Funkce v této části jsou pro použití v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da587-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="da587-228">_CorDllMain – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-228">_CorDllMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 <span data-ttu-id="da587-229">Inicializuje modulu CLR, vyhledá spravované vstupní bod v záhlaví modulu CLR sestavení knihoven DLL a zahájí spuštění.</span><span class="sxs-lookup"><span data-stu-id="da587-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="da587-230">_CorExeMain – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-230">_CorExeMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 <span data-ttu-id="da587-231">Inicializuje modulu CLR, vyhledá spravované vstupní bod v záhlaví modulu CLR spustitelný soubor sestavení a zahájí spuštění.</span><span class="sxs-lookup"><span data-stu-id="da587-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="da587-232">_CorExeMain2 – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-232">_CorExeMain2 Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 <span data-ttu-id="da587-233">Vstupní bod se spustí v zadaný kód mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="da587-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="da587-234">Tato funkce je volána zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="da587-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="da587-235">_CorImageUnloading – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-235">_CorImageUnloading Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 <span data-ttu-id="da587-236">Zavaděč upozorní, když jsou obrázky spravovaný modul odpojen.</span><span class="sxs-lookup"><span data-stu-id="da587-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="da587-237">_CorValidateImage – funkce</span><span class="sxs-lookup"><span data-stu-id="da587-237">_CorValidateImage Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 <span data-ttu-id="da587-238">Ověří spravovaný modul bitové kopie a po nějaké době načíst upozorní zavaděč operačního systému.</span><span class="sxs-lookup"><span data-stu-id="da587-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da587-239">Viz také</span><span class="sxs-lookup"><span data-stu-id="da587-239">See Also</span></span>  
 [<span data-ttu-id="da587-240">Globální statické funkce .NET Framework 4 pro hostování</span><span class="sxs-lookup"><span data-stu-id="da587-240">.NET Framework 4 Hosting Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md) 
