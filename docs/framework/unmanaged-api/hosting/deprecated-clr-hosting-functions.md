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
ms.openlocfilehash: aa84ca0defd173563817673aad183a8b64226d41
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135799"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="5337d-102">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="5337d-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="5337d-103">Tato část popisuje nespravované globální statické funkce, které používají starší verze hostujícího rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5337d-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="5337d-104">Kromě funkcí infrastruktury (`_Cor*` funkce), které jsou používány pouze rozhraní .NET Framework, tyto funkce se již nepoužívají v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5337d-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="5337d-105">Aktivace funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-105">Activation functions</span></span>  
 [<span data-ttu-id="5337d-106">ClrCreateManagedInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-106">ClrCreateManagedInstance Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="5337d-107">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-107">Deprecated.</span></span> <span data-ttu-id="5337d-108">Vytvoří instanci určeného spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="5337d-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="5337d-109">CoInitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-109">CoInitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 <span data-ttu-id="5337d-110">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="5337d-110">Obsolete.</span></span> <span data-ttu-id="5337d-111">Chcete-li inicializovat common language runtime (CLR), použijte buď [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="5337d-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="5337d-112">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-112">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 <span data-ttu-id="5337d-113">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-113">Deprecated.</span></span> <span data-ttu-id="5337d-114">Zajišťuje, že prováděcí modul CLR je zavedeno do procesu.</span><span class="sxs-lookup"><span data-stu-id="5337d-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="5337d-115">Použití [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="5337d-115">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="5337d-116">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-116">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 <span data-ttu-id="5337d-117">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-117">Deprecated.</span></span> <span data-ttu-id="5337d-118">Načte modul CLR (CLR) do procesu pomocí informací o verzi uložených v souboru XML.</span><span class="sxs-lookup"><span data-stu-id="5337d-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="5337d-119">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-119">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 <span data-ttu-id="5337d-120">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-120">Deprecated.</span></span> <span data-ttu-id="5337d-121">Umožní nespravovaným hostitelům načíst modul CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="5337d-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="5337d-122">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-122">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="5337d-123">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-123">Deprecated.</span></span> <span data-ttu-id="5337d-124">Načte modul CLR do procesu pomocí informací o verzi, která je pro čtení ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="5337d-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="5337d-125">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-125">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 <span data-ttu-id="5337d-126">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-126">Deprecated.</span></span> <span data-ttu-id="5337d-127">Umožňuje nespravovaným hostitelům načíst modul CLR do procesu a umožňuje nastavení příznaků, které určují chování modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="5337d-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="5337d-128">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 <span data-ttu-id="5337d-129">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-129">Deprecated.</span></span> <span data-ttu-id="5337d-130">Umožňuje hostitelům načíst zadanou verzi modulu CLR do procesu.</span><span class="sxs-lookup"><span data-stu-id="5337d-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="5337d-131">GetCORRequiredVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-131">GetCORRequiredVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 <span data-ttu-id="5337d-132">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-132">Deprecated.</span></span> <span data-ttu-id="5337d-133">Získá požadované číslo verze CLR.</span><span class="sxs-lookup"><span data-stu-id="5337d-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="5337d-134">GetCORSystemDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-134">GetCORSystemDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 <span data-ttu-id="5337d-135">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-135">Deprecated.</span></span> <span data-ttu-id="5337d-136">Vrátí instalační adresář modulu CLR, který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="5337d-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="5337d-137">GetRealProcAddress – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-137">GetRealProcAddress Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 <span data-ttu-id="5337d-138">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-138">Deprecated.</span></span> <span data-ttu-id="5337d-139">Získá adresu zadané funkce, která je exportována z poslední instalované verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="5337d-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="5337d-140">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-140">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="5337d-141">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-141">Deprecated.</span></span> <span data-ttu-id="5337d-142">Získá informace o modulu CLR požadovaný aplikací verzi a adresář.</span><span class="sxs-lookup"><span data-stu-id="5337d-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="5337d-143">Funkce verze CLR</span><span class="sxs-lookup"><span data-stu-id="5337d-143">CLR version functions</span></span>  
 <span data-ttu-id="5337d-144">Funkce v této části vrací verzi CLR; neaktivovat CLR.</span><span class="sxs-lookup"><span data-stu-id="5337d-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="5337d-145">GetCORVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-145">GetCORVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 <span data-ttu-id="5337d-146">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-146">Deprecated.</span></span> <span data-ttu-id="5337d-147">Vrátí číslo verze modulu CLR, na kterém běží v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="5337d-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="5337d-148">GetFileVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-148">GetFileVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 <span data-ttu-id="5337d-149">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-149">Deprecated.</span></span> <span data-ttu-id="5337d-150">Získá informace o verzi CLR zadaného souboru pomocí zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5337d-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="5337d-151">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-151">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 <span data-ttu-id="5337d-152">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-152">Deprecated.</span></span> <span data-ttu-id="5337d-153">Získá číslo verze modulu CLR požadované určenou aplikací.</span><span class="sxs-lookup"><span data-stu-id="5337d-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="5337d-154">Pokud není nainstalována verze, získá nejnovější verzi, která je nainstalována před požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="5337d-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="5337d-155">GetRequestedRuntimeVersionForCLSID – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="5337d-156">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-156">Deprecated.</span></span> <span data-ttu-id="5337d-157">Získá odpovídající informace o verzi CLR pro třídu se zadaným identifikátorem CLSID.</span><span class="sxs-lookup"><span data-stu-id="5337d-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="5337d-158">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-158">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 <span data-ttu-id="5337d-159">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-159">Deprecated.</span></span> <span data-ttu-id="5337d-160">Získá číslo verze modulu CLR, který je spojen s obslužnou rutinou určeného procesu.</span><span class="sxs-lookup"><span data-stu-id="5337d-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="5337d-161">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-161">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 <span data-ttu-id="5337d-162">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-162">Deprecated.</span></span> <span data-ttu-id="5337d-163">Umožňuje hostiteli zjistit, která verze modulu CLR se použije v rámci procesu před explicitní inicializací modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="5337d-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="5337d-164">Funkce pro hostování</span><span class="sxs-lookup"><span data-stu-id="5337d-164">Hosting functions</span></span>  
 [<span data-ttu-id="5337d-165">CallFunctionShim – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-165">CallFunctionShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 <span data-ttu-id="5337d-166">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-166">Deprecated.</span></span> <span data-ttu-id="5337d-167">Provede volání funkce, která má zadaný název a parametry v určené knihovně.</span><span class="sxs-lookup"><span data-stu-id="5337d-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="5337d-168">CoEEShutDownCOM – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-168">CoEEShutDownCOM Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 <span data-ttu-id="5337d-169">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-169">Deprecated.</span></span> <span data-ttu-id="5337d-170">Uvolní sestavení modelu COM z procesu.</span><span class="sxs-lookup"><span data-stu-id="5337d-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="5337d-171">CorExitProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-171">CorExitProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 <span data-ttu-id="5337d-172">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-172">Deprecated.</span></span> <span data-ttu-id="5337d-173">Ukončí aktuální nespravovaný proces.</span><span class="sxs-lookup"><span data-stu-id="5337d-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="5337d-174">CorLaunchApplication – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-174">CorLaunchApplication Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 <span data-ttu-id="5337d-175">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-175">Deprecated.</span></span> <span data-ttu-id="5337d-176">Spustí aplikaci v zadané síťové cestě pomocí zadaných manifestů a dalších dat aplikací.</span><span class="sxs-lookup"><span data-stu-id="5337d-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="5337d-177">CorMarkThreadInThreadPool – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-177">CorMarkThreadInThreadPool Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="5337d-178">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-178">Deprecated.</span></span> <span data-ttu-id="5337d-179">Označuje aktuálně prováděné vláken fondu vláken pro spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5337d-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="5337d-180">Od verze rozhraní .NET Framework verze 2.0, tato funkce nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="5337d-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="5337d-181">Není potřeba a můžete odebrat z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="5337d-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="5337d-182">CoUninitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-182">CoUninitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 <span data-ttu-id="5337d-183">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="5337d-183">Obsolete.</span></span> <span data-ttu-id="5337d-184">CLR nemůže být uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="5337d-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="5337d-185">CoUninitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-185">CoUninitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 <span data-ttu-id="5337d-186">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="5337d-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="5337d-187">CreateDebuggingInterfaceFromVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-187">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="5337d-188">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-188">Deprecated.</span></span> <span data-ttu-id="5337d-189">Vytvoří [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objektu na základě zadané verze informací.</span><span class="sxs-lookup"><span data-stu-id="5337d-189">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="5337d-190">CreateICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-190">CreateICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 <span data-ttu-id="5337d-191">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-191">Deprecated.</span></span> <span data-ttu-id="5337d-192">Vytvoří [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="5337d-192">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="5337d-193">DestroyICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-193">DestroyICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 <span data-ttu-id="5337d-194">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-194">Deprecated.</span></span> <span data-ttu-id="5337d-195">Zničí [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="5337d-195">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="5337d-196">FExecuteInAppDomainCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="5337d-196">FExecuteInAppDomainCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="5337d-197">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-197">Deprecated.</span></span> <span data-ttu-id="5337d-198">Odkazuje na funkci, kterou volá CLR pro spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5337d-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="5337d-199">FLockClrVersionCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="5337d-199">FLockClrVersionCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="5337d-200">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-200">Deprecated.</span></span> <span data-ttu-id="5337d-201">Odkazuje na funkci, kterou volá CLR aby upozornil hostitele, že inicializace buď zahájeno nebo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="5337d-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="5337d-202">GetCLRIdentityManager – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-202">GetCLRIdentityManager Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 <span data-ttu-id="5337d-203">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-203">Deprecated.</span></span> <span data-ttu-id="5337d-204">Získá ukazatel na rozhraní umožňující CLR spravovat identity.</span><span class="sxs-lookup"><span data-stu-id="5337d-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="5337d-205">LoadLibraryShim – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-205">LoadLibraryShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 <span data-ttu-id="5337d-206">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-206">Deprecated.</span></span> <span data-ttu-id="5337d-207">Načte zadanou verzi knihovny DLL .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5337d-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="5337d-208">LoadStringRC – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-208">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 <span data-ttu-id="5337d-209">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-209">Deprecated.</span></span> <span data-ttu-id="5337d-210">Převede hodnotu HRESULT na chybovou zprávu pomocí výchozí jazykové verze aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="5337d-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="5337d-211">LoadStringRCEx – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-211">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 <span data-ttu-id="5337d-212">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-212">Deprecated.</span></span> <span data-ttu-id="5337d-213">Převede hodnotu HRESULT na příslušnou chybovou zprávu pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="5337d-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="5337d-214">LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="5337d-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="5337d-215">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-215">Deprecated.</span></span> <span data-ttu-id="5337d-216">Odkazuje na funkci, která upozorňuje hostitele, pokud překrytí (tj, asynchronní) vstupně-výstupních operací na zařízení byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="5337d-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="5337d-217">LPTHREAD_START_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="5337d-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="5337d-218">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-218">Deprecated.</span></span> <span data-ttu-id="5337d-219">Odkazuje na funkci, která upozorňuje hostitele na spuštěný podproces ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="5337d-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="5337d-220">RunDll32ShimW – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-220">RunDll32ShimW Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 <span data-ttu-id="5337d-221">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-221">Deprecated.</span></span> <span data-ttu-id="5337d-222">Provede zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="5337d-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="5337d-223">WAITORTIMERCALLBACK – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="5337d-223">WAITORTIMERCALLBACK Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 <span data-ttu-id="5337d-224">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="5337d-224">Deprecated.</span></span> <span data-ttu-id="5337d-225">Odkazuje na funkci, která upozorňuje hostitele, že popisovač čekání buď byl signalizován nebo vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="5337d-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="5337d-226">Funkce infrastruktury</span><span class="sxs-lookup"><span data-stu-id="5337d-226">Infrastructure functions</span></span>  
 <span data-ttu-id="5337d-227">Funkce v této části se používají pouze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5337d-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="5337d-228">_CorDllMain – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-228">_CorDllMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 <span data-ttu-id="5337d-229">Inicializuje modul CLR, vyhledá spravovaný vstupní bod v záhlaví modulu CLR sestavení DLL a zahájí vykonávání.</span><span class="sxs-lookup"><span data-stu-id="5337d-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="5337d-230">_CorExeMain – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-230">_CorExeMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 <span data-ttu-id="5337d-231">Inicializuje modul CLR, vyhledá spravovaný vstupní bod v záhlaví spustitelného sestavení modulu CLR a zahájí vykonávání.</span><span class="sxs-lookup"><span data-stu-id="5337d-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="5337d-232">_CorExeMain2 – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-232">_CorExeMain2 Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 <span data-ttu-id="5337d-233">Spustí vstupní bod v zadané kódu mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="5337d-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="5337d-234">Tato funkce je volána zavaděčem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="5337d-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="5337d-235">_CorImageUnloading – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-235">_CorImageUnloading Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 <span data-ttu-id="5337d-236">Upozorní zavaděč na bitové kopie spravovaného modulu jsou uvolněna.</span><span class="sxs-lookup"><span data-stu-id="5337d-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="5337d-237">_CorValidateImage – funkce</span><span class="sxs-lookup"><span data-stu-id="5337d-237">_CorValidateImage Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 <span data-ttu-id="5337d-238">Ověřuje bitové kopie spravovaného modulu a upozorní zavaděč operačního systému po jejich načtení.</span><span class="sxs-lookup"><span data-stu-id="5337d-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5337d-239">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5337d-239">See also</span></span>

- [<span data-ttu-id="5337d-240">Globální statické funkce .NET Framework 4 pro hostování</span><span class="sxs-lookup"><span data-stu-id="5337d-240">.NET Framework 4 Hosting Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md)
