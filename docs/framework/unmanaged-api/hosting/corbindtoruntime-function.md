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
ms.openlocfilehash: 2db9d26ef2dec150977c468b16334a7cb4b3d49c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176510"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="b4b6e-102">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="b4b6e-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="b4b6e-103">Umožňuje nespravovaným hostitelům načíst běžný jazyk runtime (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="b4b6e-104">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b6e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4b6e-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4b6e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4b6e-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="b4b6e-107">[v] Řetězec popisující verzi CLR, kterou chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="b4b6e-108">Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí oddělených tečkami: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="b4b6e-109">Řetězec předán `pwszVersion` jako musí začínat znak "v" následuje první tři části číslo verze (například "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="b4b6e-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="b4b6e-110">Některé verze clr jsou nainstalovány s prohlášením zásad, které určuje kompatibilitu s předchozími verzemi CLR.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="b4b6e-111">Ve výchozím nastavení překrytí `pwszVersion` při spuštění vyhodnocuje příkazy zásad a načte nejnovější verzi běhu, který je kompatibilní s požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="b4b6e-112">Hostitel může vynutit překrytí přeskočit vyhodnocení zásad a `pwszVersion` načíst přesnou `flags` verzi zadanou v souboru předáním hodnoty parametru, `STARTUP_LOADER_SAFEMODE` jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="b4b6e-113">Pokud volající určuje hodnotu null pro `pwszVersion`, je načtena nejnovější verze runtime.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="b4b6e-114">Předávání null dává hostiteli žádnou kontrolu nad tím, která verze runtime je načtena.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="b4b6e-115">Ačkoli tento přístup může být vhodné v některých scénářích, důrazně doporučujeme, aby hostitel dodat konkrétní verzi načíst.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="b4b6e-116">[v] Řetězec, který určuje, zda má být server nebo sestavení pracovní stanice CLR načíst.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="b4b6e-117">Platné hodnoty `svr` `wks`jsou a .</span><span class="sxs-lookup"><span data-stu-id="b4b6e-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="b4b6e-118">Sestavení serveru je optimalizováno tak, aby využívalo více procesorů pro uvolňování paměti, a sestavení pracovní stanice je optimalizováno pro klientské aplikace spuštěné v počítači s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="b4b6e-119">Pokud `pwszBuildFlavor` je nastavena na hodnotu null, sestavení pracovní stanice je načten.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="b4b6e-120">Při spuštění na počítači s jedním procesorem je sestavení `pwszBuildFlavor` pracovní `svr`stanice vždy načteno, i když je nastaveno na .</span><span class="sxs-lookup"><span data-stu-id="b4b6e-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="b4b6e-121">Však `pwszBuildFlavor` pokud je `svr` nastavena a souběžné uvolňování paměti `flags` je zadán (viz popis parametru), sestavení serveru je načten.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="b4b6e-122">[v] Coclass, `CLSID` která implementuje buď [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="b4b6e-123">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="b4b6e-124">[v] Požadované `IID` rozhraní od `rclsid`aplikace .</span><span class="sxs-lookup"><span data-stu-id="b4b6e-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="b4b6e-125">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="b4b6e-126">[out] Vrácený ukazatel `riid`rozhraní na .</span><span class="sxs-lookup"><span data-stu-id="b4b6e-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4b6e-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4b6e-127">Remarks</span></span>  
 <span data-ttu-id="b4b6e-128">Pokud `pwszVersion` určuje verzi runtime, která `CorBindToRuntimeEx` neexistuje, vrátí hodnotu HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="b4b6e-129">Kontext spuštění a tok identity systému Windows</span><span class="sxs-lookup"><span data-stu-id="b4b6e-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="b4b6e-130">Ve verzi 1 CLR <xref:System.Security.Principal.WindowsIdentity> objekt netokuje přes asynchronní body, jako jsou nová vlákna, fondy vláken nebo zpětná volání časovače.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="b4b6e-131">Ve verzi 2.0 CLR <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně spuštěném vlákně a nateče přes libovolný asynchronní bod, ale ne přes hranice domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="b4b6e-132">Podobně <xref:System.Security.Principal.WindowsIdentity> objekt také toky přes všechny asynchronní bod.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="b4b6e-133">Proto aktuální zosobnění ve vlákně, pokud existuje, toky příliš.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="b4b6e-134">Tok můžete změnit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="b4b6e-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="b4b6e-135">Úpravou <xref:System.Threading.ExecutionContext> nastavení potlačit tok na základě vlákno (viz <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> , a metody).</span><span class="sxs-lookup"><span data-stu-id="b4b6e-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="b4b6e-136">Změnou výchozího režimu procesu na režim <xref:System.Security.Principal.WindowsIdentity> kompatibility verze 1, kde objekt neprobíhá <xref:System.Threading.ExecutionContext> přes žádný asynchronní bod, bez ohledu na nastavení v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="b4b6e-137">Způsob změny výchozího režimu závisí na tom, zda k načtení příkazu CLR načtete spravované spustitelné nebo nespravované hostitelské rozhraní:</span><span class="sxs-lookup"><span data-stu-id="b4b6e-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="b4b6e-138">U spravovaných spustitelných `enabled` souborů je nutné nastavit atribut [ \<staršího prvku ImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) na `true`.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="b4b6e-139">Pro nespravované hostitelské rozhraní `STARTUP_LEGACY_IMPERSONATION` nastavte příznak `flags` v parametru při volání `CorBindToRuntimeEx` funkce.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="b4b6e-140">Režim kompatibility verze 1 se vztahuje na celý proces a na všechny aplikační domény v procesu.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4b6e-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4b6e-141">Remarks</span></span>  
 <span data-ttu-id="b4b6e-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `CorBindToRuntime` a provést stejnou operaci, ale `CorBindToRuntimeEx` funkce umožňuje nastavit příznaky určit chování CLR.</span><span class="sxs-lookup"><span data-stu-id="b4b6e-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4b6e-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4b6e-143">Requirements</span></span>  
 <span data-ttu-id="b4b6e-144">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4b6e-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4b6e-145">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4b6e-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4b6e-146">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b4b6e-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4b6e-147">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4b6e-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b6e-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4b6e-148">See also</span></span>

- [<span data-ttu-id="b4b6e-149">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="b4b6e-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="b4b6e-150">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="b4b6e-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="b4b6e-151">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="b4b6e-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="b4b6e-152">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="b4b6e-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="b4b6e-153">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4b6e-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="b4b6e-154">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="b4b6e-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
