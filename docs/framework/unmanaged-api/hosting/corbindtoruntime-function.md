---
title: "CorBindToRuntime – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorBindToRuntime
helpviewer_keywords: CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a833be39f93082e8d2c0cb28f435f754143721f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="c9c9d-102">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="c9c9d-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="c9c9d-103">Umožňuje nespravované hostitelé načíst modul CLR (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="c9c9d-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9c9d-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9c9d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9c9d-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9c9d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9c9d-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="c9c9d-107">[v] Řetězec popisující verzi modulu CLR, které se má zatížení.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="c9c9d-108">Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí, které jsou odděleny tečkami: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="c9c9d-109">Řetězec předány jako `pwszVersion` musí začínat znak "v" následované první tři části číslo verze (například "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="c9c9d-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="c9c9d-110">Některé verze modulu CLR jsou nainstalovány s prohlášení o zásadách, která určuje kompatibility s předchozími verzemi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="c9c9d-111">Ve výchozím nastavení, vyhodnotí shim spuštění `pwszVersion` proti příkazy zásad a zatížením nejnovější verzi modulu runtime, je kompatibilní s požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="c9c9d-112">Hostitel může vynutit shim přeskočit vyhodnocení zásad a načíst přesné verze zadaná v `pwszVersion` předáním hodnotu `STARTUP_LOADER_SAFEMODE` pro `flags` parametr, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="c9c9d-113">Pokud má volající Určuje hodnotu null pro `pwszVersion`, je-li načíst nejnovější verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="c9c9d-114">Předání hodnotou null dává hostitele žádnou kontrolu nad niž je načíst verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="c9c9d-115">I když tento přístup může být vhodné v některých scénářích, důrazně doporučujeme, aby hostitel zadat konkrétní verzi načíst.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="c9c9d-116">[v] Řetězec, který určuje, jestli zatížení serveru nebo pracovní stanice sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="c9c9d-117">Platné hodnoty jsou `svr` a `wks`.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="c9c9d-118">Sestavení serveru je optimalizovaná tak, aby využít výhod více procesorů pro kolekce a sestavení pracovní stanici je optimalizovaná pro klientské aplikace spuštěné na počítač s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="c9c9d-119">Pokud `pwszBuildFlavor` je nastaven na hodnotu null, je načíst sestavení pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="c9c9d-120">Při spuštění na počítač s jedním procesorem, je vždy načteno sestavení pracovní stanice, i když `pwszBuildFlavor` je nastaven na `svr`.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="c9c9d-121">Ale pokud `pwszBuildFlavor` je nastaven na `svr` a je zadána souběžné uvolňování (naleznete v popisu `flags` parametr), je načíst sestavení serveru.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="c9c9d-122">[v] `CLSID` Coclass, který implementuje buď [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="c9c9d-123">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="c9c9d-124">[v] `IID` Požadované rozhraní z `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="c9c9d-125">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="c9c9d-126">[out] Vrácený rozhraní ukazatel na `riid`.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9c9d-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9c9d-127">Remarks</span></span>  
 <span data-ttu-id="c9c9d-128">Pokud `pwszVersion` Určuje verzi modulu runtime, který ještě neexistuje, `CorBindToRuntimeEx` vrátí hodnotu HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="c9c9d-129">Kontext spuštění a toku identitu systému Windows</span><span class="sxs-lookup"><span data-stu-id="c9c9d-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="c9c9d-130">Ve verzi modulu CLR, 1 <xref:System.Security.Principal.WindowsIdentity> objekt nepostupuje napříč asynchronní bodů například Nová vlákna, fondy vláken nebo zpětná volání časovače.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="c9c9d-131">Ve verzi 2.0 modulu CLR <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně spuštěném vlákno a jeho toků mezi kdykoli asynchronní, ale není napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="c9c9d-132">Podobně <xref:System.Security.Principal.WindowsIdentity> objekt také přeteče kdykoli asynchronní.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="c9c9d-133">Proto aktuální zosobnění na vlákno, pokud existuje, toky příliš.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="c9c9d-134">Chcete-li změnit toku dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="c9c9d-134">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="c9c9d-135">Změnou <xref:System.Threading.ExecutionContext> nastavení potlačit toku na základě vlákna (najdete v článku <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, a <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).</span><span class="sxs-lookup"><span data-stu-id="c9c9d-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="c9c9d-136">Změnou výchozí režim proces na režim kompatibility verze 1, kde <xref:System.Security.Principal.WindowsIdentity> bez ohledu na to není tok objektů mezi kdykoli asynchronní <xref:System.Threading.ExecutionContext> nastavení na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="c9c9d-137">Jak změnit výchozí režim, závisí na ať už používáte spravované spustitelný soubor nebo nespravované rozhraní hostingu načíst modul CLR:</span><span class="sxs-lookup"><span data-stu-id="c9c9d-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="c9c9d-138">Pro spravované spustitelné soubory, je potřeba nastavit `enabled` atribut [ \<legacyimpersonationpolicy – >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element `true`.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="c9c9d-139">Nespravované rozhraní hostování, nastavit `STARTUP_LEGACY_IMPERSONATION` příznak v `flags` parametr při volání metody `CorBindToRuntimeEx` funkce.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="c9c9d-140">Režim kompatibility verze 1 platí pro celý proces a všechny domény aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9c9d-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9c9d-141">Remarks</span></span>  
 <span data-ttu-id="c9c9d-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a `CorBindToRuntime` provádět stejné operace, ale `CorBindToRuntimeEx` funkce vám umožní nastavit příznaky určit způsob chování modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c9c9d-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9c9d-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9c9d-143">Requirements</span></span>  
 <span data-ttu-id="c9c9d-144">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9c9d-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9c9d-145">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c9c9d-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9c9d-146">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9c9d-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9c9d-147">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9c9d-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c9d-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9c9d-148">See Also</span></span>  
 [<span data-ttu-id="c9c9d-149">Corbindtocurrentruntime – funkce</span><span class="sxs-lookup"><span data-stu-id="c9c9d-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="c9c9d-150">Corbindtoruntimebycfg – funkce</span><span class="sxs-lookup"><span data-stu-id="c9c9d-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="c9c9d-151">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="c9c9d-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="c9c9d-152">Corbindtoruntimehost – funkce</span><span class="sxs-lookup"><span data-stu-id="c9c9d-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="c9c9d-153">Icorruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9c9d-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="c9c9d-154">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="c9c9d-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
