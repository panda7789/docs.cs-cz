---
title: "CorBindToRuntimeEx – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeEx
helpviewer_keywords: CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type: apiref
caps.latest.revision: "41"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c0080e5a01c8e856c2862182ba06096fdc9385c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="c748f-102">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="c748f-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="c748f-103">Umožňuje nespravované hostitelé načíst modul CLR (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="c748f-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="c748f-104">[Corbindtoruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) a `CorBindToRuntimeEx` funkce provádět stejné operace, ale `CorBindToRuntimeEx` funkce vám umožní nastavit příznaky určit způsob chování modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c748f-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="c748f-105">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c748f-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
 <span data-ttu-id="c748f-106">Tato funkce přebírá sadu parametrů umožňujících hostitele provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="c748f-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
-   <span data-ttu-id="c748f-107">Zadejte verzi modulu runtime, který bude načten.</span><span class="sxs-lookup"><span data-stu-id="c748f-107">Specify the version of the runtime that will be loaded.</span></span>  
  
-   <span data-ttu-id="c748f-108">Označuje, zda se mají načíst sestavení serveru nebo pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="c748f-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
-   <span data-ttu-id="c748f-109">Řídí, zda se provádí souběžné uvolňování paměti nebo nesouběžného uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c748f-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c748f-110">Souběžné uvolňování není podporována v aplikacích spuštěných WOW64 x86 emulátoru na 64bitových systémech, které implementují architektuře Intel Itanium (dříve se označovaly jako platformu IA-64).</span><span class="sxs-lookup"><span data-stu-id="c748f-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="c748f-111">Další informace o používání WOW64 v 64bitových systémech Windows najdete v tématu [spuštění 32bitové aplikace](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="c748f-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>  
  
-   <span data-ttu-id="c748f-112">Řídí, zda jsou načteny sestavení jako domény jazykově neutrální.</span><span class="sxs-lookup"><span data-stu-id="c748f-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
-   <span data-ttu-id="c748f-113">Získání ukazatele rozhraní k [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) , lze nastavit další možnosti pro konfiguraci instanci modulu CLR, než je spuštěno.</span><span class="sxs-lookup"><span data-stu-id="c748f-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c748f-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c748f-114">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c748f-115">Parametry</span><span class="sxs-lookup"><span data-stu-id="c748f-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="c748f-116">[v] Řetězec popisující verzi modulu CLR, které se má zatížení.</span><span class="sxs-lookup"><span data-stu-id="c748f-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="c748f-117">Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí, které jsou odděleny tečkami: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="c748f-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="c748f-118">Řetězec předány jako `pwszVersion` musí začínat znak "v" následované první tři části číslo verze (například "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="c748f-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="c748f-119">Některé verze modulu CLR jsou nainstalovány s prohlášení o zásadách, která určuje kompatibility s předchozími verzemi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c748f-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="c748f-120">Ve výchozím nastavení, vyhodnotí shim spuštění `pwszVersion` proti příkazy zásad a zatížením nejnovější verzi modulu runtime, je kompatibilní s požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="c748f-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="c748f-121">Hostitel může vynutit shim přeskočit vyhodnocení zásad a načíst přesné verze zadaná v `pwszVersion` předáním hodnotu `STARTUP_LOADER_SAFEMODE` pro `startupFlags` parametr, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="c748f-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="c748f-122">Pokud má volající Určuje hodnotu null pro `pwszVersion`, `CorBindToRuntimeEx` identifikuje sadu nainstalované moduly runtime, jejichž čísla verzí jsou nižší než modul runtime rozhraní .NET Framework 4 a načte nejnovější verzi modulu runtime z této sady.</span><span class="sxs-lookup"><span data-stu-id="c748f-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="c748f-123">Pokud je nainstalovaná starší verze ho nebude načtena rozhraní .NET Framework 4 nebo novější a selže.</span><span class="sxs-lookup"><span data-stu-id="c748f-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="c748f-124">Všimněte si, že předávání null dává hostitele žádnou kontrolu nad niž je načíst verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c748f-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="c748f-125">I když tento přístup může být vhodné v některých scénářích, důrazně doporučujeme, aby hostitel zadat konkrétní verzi načíst.</span><span class="sxs-lookup"><span data-stu-id="c748f-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="c748f-126">[v] Řetězec, který určuje, jestli zatížení serveru nebo pracovní stanice sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="c748f-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="c748f-127">Platné hodnoty jsou `svr` a `wks`.</span><span class="sxs-lookup"><span data-stu-id="c748f-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="c748f-128">Sestavení serveru je optimalizovaná tak, aby využít výhod více procesorů pro kolekce a sestavení pracovní stanici je optimalizovaná pro klientské aplikace spuštěné na počítač s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="c748f-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="c748f-129">Pokud `pwszBuildFlavor` je nastaven na hodnotu null, je načíst sestavení pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="c748f-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="c748f-130">Při spuštění na počítač s jedním procesorem, je vždy načteno sestavení pracovní stanice, i když `pwszBuildFlavor` je nastaven na `svr`.</span><span class="sxs-lookup"><span data-stu-id="c748f-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="c748f-131">Ale pokud `pwszBuildFlavor` je nastaven na `svr` a je zadána souběžné uvolňování (naleznete v popisu `startupFlags` parametr), je načíst sestavení serveru.</span><span class="sxs-lookup"><span data-stu-id="c748f-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="c748f-132">[v] Kombinace hodnot, které [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="c748f-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="c748f-133">Tyto příznaky řízení souběžné uvolňování domény neutrální kód a chování `pwszVersion` parametr.</span><span class="sxs-lookup"><span data-stu-id="c748f-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="c748f-134">Výchozí hodnota je jedinou doménu, pokud žádné příznak nastaven.</span><span class="sxs-lookup"><span data-stu-id="c748f-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="c748f-135">Platné jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="c748f-135">The following values are valid:</span></span>  
  
-   `STARTUP_CONCURRENT_GC`  
  
-   `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
-   `STARTUP_LOADER_SAFEMODE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_LOADER_SETPREFERENCE`  
  
-   `STARTUP_SERVER_GC`  
  
-   `STARTUP_HOARD_GC_VM`  
  
-   `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
-   `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="c748f-136">Popis tyto příznaky najdete v tématu [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="c748f-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="c748f-137">[v] `CLSID` Coclass, který implementuje buď [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c748f-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="c748f-138">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="c748f-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="c748f-139">[v] `IID` Požadované rozhraní z `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="c748f-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="c748f-140">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="c748f-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="c748f-141">[out] Vrácený rozhraní ukazatel na `riid`.</span><span class="sxs-lookup"><span data-stu-id="c748f-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c748f-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c748f-142">Remarks</span></span>  
 <span data-ttu-id="c748f-143">Pokud `pwszVersion` Určuje verzi modulu runtime, který ještě neexistuje, `CorBindToRuntimeEx` vrátí hodnotu HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="c748f-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="c748f-144">Kontext spuštění a toku identitu systému Windows</span><span class="sxs-lookup"><span data-stu-id="c748f-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="c748f-145">Ve verzi modulu CLR, 1 <xref:System.Security.Principal.WindowsIdentity> objekt nepostupuje napříč asynchronní bodů například Nová vlákna, fondy vláken nebo zpětná volání časovače.</span><span class="sxs-lookup"><span data-stu-id="c748f-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="c748f-146">Ve verzi 2.0 modulu CLR <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně spuštěném vlákno a jeho toků mezi kdykoli asynchronní, ale není napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c748f-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="c748f-147">Podobně <xref:System.Security.Principal.WindowsIdentity> objekt také přeteče kdykoli asynchronní.</span><span class="sxs-lookup"><span data-stu-id="c748f-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="c748f-148">Proto aktuální zosobnění na vlákno, pokud existuje, toky příliš.</span><span class="sxs-lookup"><span data-stu-id="c748f-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="c748f-149">Chcete-li změnit toku dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="c748f-149">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="c748f-150">Změnou <xref:System.Threading.ExecutionContext> nastavení potlačit toku na základě vlákna (najdete v článku <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, a <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).</span><span class="sxs-lookup"><span data-stu-id="c748f-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="c748f-151">Změnou výchozí režim proces na režim kompatibility verze 1, kde <xref:System.Security.Principal.WindowsIdentity> bez ohledu na to není tok objektů mezi kdykoli asynchronní <xref:System.Threading.ExecutionContext> nastavení na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="c748f-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="c748f-152">Jak změnit výchozí režim, závisí na ať už používáte spravované spustitelný soubor nebo nespravované rozhraní hostingu načíst modul CLR:</span><span class="sxs-lookup"><span data-stu-id="c748f-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="c748f-153">Pro spravované spustitelné soubory, je potřeba nastavit `enabled` atribut [ \<legacyimpersonationpolicy – >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element `true`.</span><span class="sxs-lookup"><span data-stu-id="c748f-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="c748f-154">Nespravované rozhraní hostování, nastavit `STARTUP_LEGACY_IMPERSONATION` příznak v `startupFlags` parametr při volání metody `CorBindToRuntimeEx` funkce.</span><span class="sxs-lookup"><span data-stu-id="c748f-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="c748f-155">Režim kompatibility verze 1 platí pro celý proces a všechny domény aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="c748f-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c748f-156">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c748f-156">Requirements</span></span>  
 <span data-ttu-id="c748f-157">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c748f-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c748f-158">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c748f-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c748f-159">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c748f-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c748f-160">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c748f-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c748f-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="c748f-161">See Also</span></span>  
 [<span data-ttu-id="c748f-162">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="c748f-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="c748f-163">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="c748f-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="c748f-164">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="c748f-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="c748f-165">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="c748f-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="c748f-166">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c748f-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="c748f-167">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="c748f-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
