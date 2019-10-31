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
ms.openlocfilehash: 9d4b8bb7d5b3da15f665849c8d18c3a10dbe600b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138313"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="140c2-102">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="140c2-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="140c2-103">Umožňuje nespravovaným hostitelům načíst modul CLR (Common Language Runtime) do procesu.</span><span class="sxs-lookup"><span data-stu-id="140c2-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="140c2-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="140c2-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="140c2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="140c2-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="140c2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="140c2-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="140c2-107">pro Řetězec popisující verzi modulu CLR, kterou chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="140c2-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="140c2-108">Číslo verze v .NET Framework se skládá ze čtyř částí oddělených tečkami: *hlavní_verze. podverze. sestavení. revize*.</span><span class="sxs-lookup"><span data-stu-id="140c2-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="140c2-109">Řetězec předaný jako `pwszVersion` musí začínat znakem "v" následovaný prvními třemi částmi čísla verze (například "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="140c2-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="140c2-110">Některé verze modulu CLR jsou nainstalovány s příkazem zásad, který určuje kompatibilitu s předchozími verzemi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="140c2-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="140c2-111">Ve výchozím nastavení překrytí po spuštění vyhodnocuje `pwszVersion` proti příkazům zásad a načte nejnovější verzi modulu runtime, která je kompatibilní s požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="140c2-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="140c2-112">Hostitel může vynutit překrytí, aby přeskočil vyhodnocení zásad a načetlo přesnou verzi určenou v `pwszVersion` předáním hodnoty `STARTUP_LOADER_SAFEMODE` parametru `flags`, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="140c2-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="140c2-113">Pokud volající pro `pwszVersion`zadá hodnotu null, je načtena nejnovější verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="140c2-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="140c2-114">Předání hodnoty null dává hostiteli žádnou kontrolu nad tím, která verze modulu runtime je načtena.</span><span class="sxs-lookup"><span data-stu-id="140c2-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="140c2-115">I když tento přístup může být v některých scénářích vhodný, důrazně doporučujeme, aby hostitel zadal konkrétní verzi, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="140c2-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="140c2-116">pro Řetězec, který určuje, zda má být načten Server nebo pracovní stanice sestavení modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="140c2-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="140c2-117">Platné hodnoty jsou `svr` a `wks`.</span><span class="sxs-lookup"><span data-stu-id="140c2-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="140c2-118">Sestavení serveru je optimalizované tak, aby využívalo více procesorů pro uvolňování paměti a aby bylo sestavení pracovní stanice optimalizované pro klientské aplikace běžící na počítači s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="140c2-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="140c2-119">Pokud je `pwszBuildFlavor` nastaveno na hodnotu null, je načteno sestavení pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="140c2-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="140c2-120">Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno, i když je `pwszBuildFlavor` nastaveno na `svr`.</span><span class="sxs-lookup"><span data-stu-id="140c2-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="140c2-121">Pokud je však `pwszBuildFlavor` nastavena na `svr` a je-li zadáno souběžné uvolňování paměti (viz popis `flags` parametr), je sestavení serveru načteno.</span><span class="sxs-lookup"><span data-stu-id="140c2-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="140c2-122">pro `CLSID` třídy coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="140c2-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="140c2-123">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="140c2-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="140c2-124">pro `IID` z vyžádaného rozhraní z `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="140c2-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="140c2-125">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="140c2-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="140c2-126">mimo Vrácený ukazatel rozhraní na `riid`.</span><span class="sxs-lookup"><span data-stu-id="140c2-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="140c2-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="140c2-127">Remarks</span></span>  
 <span data-ttu-id="140c2-128">Pokud `pwszVersion` určuje verzi modulu runtime, která neexistuje, `CorBindToRuntimeEx` vrátí hodnotu HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="140c2-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="140c2-129">Kontext spuštění a tok identity Windows</span><span class="sxs-lookup"><span data-stu-id="140c2-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="140c2-130">Ve verzi 1 modulu CLR objekt <xref:System.Security.Principal.WindowsIdentity> neprovádí tok mezi asynchronními body, jako jsou nová vlákna, fondy vláken nebo zpětná volání časovače.</span><span class="sxs-lookup"><span data-stu-id="140c2-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="140c2-131">Ve verzi 2,0 CLR objekt <xref:System.Threading.ExecutionContext> zalomí některé informace o aktuálně zpracovávaném vlákně a natéká ho napříč jakýmkoli asynchronním bodem, ale ne napříč hranicemi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="140c2-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="140c2-132">Podobně objekt <xref:System.Security.Principal.WindowsIdentity> také toků napříč jakýmkoli asynchronním bodem.</span><span class="sxs-lookup"><span data-stu-id="140c2-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="140c2-133">Proto aktuální zosobnění ve vlákně, pokud nějaký existuje, je také toků.</span><span class="sxs-lookup"><span data-stu-id="140c2-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="140c2-134">Tok můžete změnit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="140c2-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="140c2-135">Změnou nastavení <xref:System.Threading.ExecutionContext> pro potlačení toku na základě jednotlivých vláken (viz metody <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>a <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>).</span><span class="sxs-lookup"><span data-stu-id="140c2-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="140c2-136">Změnou výchozího režimu procesu na režim kompatibility verze 1, kde objekt <xref:System.Security.Principal.WindowsIdentity> neprovádí tok napříč žádným asynchronním bodem bez ohledu na nastavení <xref:System.Threading.ExecutionContext> v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="140c2-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="140c2-137">Způsob změny výchozího režimu závisí na tom, zda používáte spravovaný spustitelný soubor nebo nespravované rozhraní hostování pro načtení modulu CLR:</span><span class="sxs-lookup"><span data-stu-id="140c2-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="140c2-138">U spravovaných spustitelných souborů je nutné nastavit atribut `enabled` elementu [\<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) na `true`.</span><span class="sxs-lookup"><span data-stu-id="140c2-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="140c2-139">U nespravovaných hostitelských rozhraní nastavte příznak `STARTUP_LEGACY_IMPERSONATION` v parametru `flags` při volání funkce `CorBindToRuntimeEx`.</span><span class="sxs-lookup"><span data-stu-id="140c2-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="140c2-140">Režim kompatibility verze 1 se vztahuje na celý proces a na všechny domény aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="140c2-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="140c2-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="140c2-141">Remarks</span></span>  
 <span data-ttu-id="140c2-142">[CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a `CorBindToRuntime` provádí stejnou operaci, ale funkce `CorBindToRuntimeEx` umožňuje nastavit příznaky pro určení chování modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="140c2-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="140c2-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="140c2-143">Requirements</span></span>  
 <span data-ttu-id="140c2-144">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="140c2-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="140c2-145">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="140c2-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="140c2-146">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="140c2-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="140c2-147">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="140c2-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="140c2-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="140c2-148">See also</span></span>

- [<span data-ttu-id="140c2-149">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="140c2-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="140c2-150">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="140c2-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="140c2-151">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="140c2-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="140c2-152">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="140c2-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="140c2-153">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="140c2-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="140c2-154">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="140c2-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
