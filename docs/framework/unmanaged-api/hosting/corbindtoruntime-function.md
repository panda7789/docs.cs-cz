---
title: CorBindToRuntime – funkce
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb5c05a88c12b5124c77b0d0a7f834b405dd289f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304620"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="9674c-102">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="9674c-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="9674c-103">Umožní nespravovaným hostitelům načíst modul CLR (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="9674c-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="9674c-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9674c-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9674c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9674c-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9674c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9674c-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="9674c-107">[in] Řetězec, který popisuje verzi modulu CLR, která chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="9674c-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="9674c-108">Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí oddělených tečkami: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="9674c-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="9674c-109">Řetězec předaný jako `pwszVersion` musí začínat znakem "v" následovaný prvními třemi částmi čísla verze (například "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="9674c-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="9674c-110">Některé verze modulu CLR jsou nainstalovány s prohlášením o zásadách, které určuje kompatibilitu s předchozími verzemi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="9674c-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="9674c-111">Ve výchozím nastavení překrytí spuštění vyhodnotí `pwszVersion` proti prohlášení zásad a načte nejnovější verze modulu runtime, který je kompatibilní s verzí, které jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="9674c-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="9674c-112">Hostitel může donutit překrytí, aby přeskočilo hodnocení zásad a načetlo přesnou verzi zadané v `pwszVersion` předáním hodnoty z `STARTUP_LOADER_SAFEMODE` pro `flags` parametru, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="9674c-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="9674c-113">Pokud volající zadá hodnotu null pro `pwszVersion`, načíst nejnovější verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9674c-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="9674c-114">Předání hodnoty null poskytuje hostiteli žádnou kontrolu nad tím, které je načtená verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9674c-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="9674c-115">Přestože tento přístup může být vhodné v některých scénářích, důrazně doporučujeme, aby hostitel zadat konkrétní verzi, kterou načíst.</span><span class="sxs-lookup"><span data-stu-id="9674c-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="9674c-116">[in] Řetězec, který určuje, jestli se má načíst server nebo pracovní stanice sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="9674c-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="9674c-117">Platné hodnoty jsou `svr` a `wks`.</span><span class="sxs-lookup"><span data-stu-id="9674c-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="9674c-118">Sestavení serveru je optimalizováno pro využití více procesorů pro uvolňování paměti kolekce a sestavení pracovní stanice je optimalizována pro klientské aplikace spuštěné v počítači s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="9674c-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="9674c-119">Pokud `pwszBuildFlavor` je nastavena na hodnotu null, je načteno sestavení pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="9674c-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="9674c-120">Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno, i když `pwszBuildFlavor` je nastavena na `svr`.</span><span class="sxs-lookup"><span data-stu-id="9674c-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="9674c-121">Ale pokud `pwszBuildFlavor` je nastavena na `svr` a souběžné uvolňování je vyznačeno (viz popis `flags` parametr), načte se sestavení serveru.</span><span class="sxs-lookup"><span data-stu-id="9674c-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="9674c-122">[in] `CLSID` Třídy typu coclass, která implementuje [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9674c-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="9674c-123">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9674c-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="9674c-124">[in] `IID` Požadovaná rozhraní z `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="9674c-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="9674c-125">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9674c-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9674c-126">[out] Vrácený ukazatel rozhraní k `riid`.</span><span class="sxs-lookup"><span data-stu-id="9674c-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9674c-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9674c-127">Remarks</span></span>  
 <span data-ttu-id="9674c-128">Pokud `pwszVersion` Určuje verzi modulu runtime, který neexistuje, `CorBindToRuntimeEx` vrátí CLR_E_SHIM_RUNTIMELOAD hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="9674c-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="9674c-129">Kontext spuštění a tok Windows Identity</span><span class="sxs-lookup"><span data-stu-id="9674c-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="9674c-130">V modulu CLR verze 1 <xref:System.Security.Principal.WindowsIdentity> objektu není téct přes asynchronní body jako nová vlákna, fondy vláken nebo zpětná volání časovače.</span><span class="sxs-lookup"><span data-stu-id="9674c-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="9674c-131">V modulu CLR verze 2.0 <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně spuštěné vlákno a toky ji napříč asynchronní čárky, ale ne přes hranice aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="9674c-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="9674c-132">Podobně platí <xref:System.Security.Principal.WindowsIdentity> objekt také průchodu čárky asynchronní.</span><span class="sxs-lookup"><span data-stu-id="9674c-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="9674c-133">Proto aktuální zosobnění ve vlákně, pokud existuje, toky příliš.</span><span class="sxs-lookup"><span data-stu-id="9674c-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="9674c-134">Je možné změnit toku dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="9674c-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="9674c-135">Úpravou <xref:System.Threading.ExecutionContext> nastavení potlačení toku na základě vlákno (najdete v článku <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, a <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).</span><span class="sxs-lookup"><span data-stu-id="9674c-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="9674c-136">Změnou výchozí režim procesu na režim kompatibility verze 1, kde <xref:System.Security.Principal.WindowsIdentity> objektu není téct přes asynchronní fázi bez ohledu na to <xref:System.Threading.ExecutionContext> nastavení pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="9674c-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="9674c-137">Jak změnit výchozí režim závisí na, jestli používat spravované spustitelný soubor nebo nespravovaných hostitelských rozhraní načíst modul CLR:</span><span class="sxs-lookup"><span data-stu-id="9674c-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="9674c-138">Pro spravované spustitelné soubory, je nutné nastavit `enabled` atribut [ \<legacyimpersonationpolicy – >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="9674c-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="9674c-139">Pro nespravovaná rozhraní pro hostování, nastavit `STARTUP_LEGACY_IMPERSONATION` příznak v `flags` parametru při volání `CorBindToRuntimeEx` funkce.</span><span class="sxs-lookup"><span data-stu-id="9674c-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="9674c-140">Režim kompatibility verze 1 platí pro celý proces a všech doménách aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="9674c-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9674c-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9674c-141">Remarks</span></span>  
 <span data-ttu-id="9674c-142">[CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a `CorBindToRuntime` provádět stejnou operaci, ale `CorBindToRuntimeEx` funkce umožňuje nastavení příznaků, které určují chování modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="9674c-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9674c-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9674c-143">Requirements</span></span>  
 <span data-ttu-id="9674c-144">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9674c-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9674c-145">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9674c-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9674c-146">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9674c-146">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9674c-147">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9674c-147">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9674c-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9674c-148">See also</span></span>

- [<span data-ttu-id="9674c-149">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="9674c-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="9674c-150">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="9674c-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="9674c-151">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="9674c-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="9674c-152">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="9674c-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="9674c-153">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9674c-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="9674c-154">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="9674c-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
