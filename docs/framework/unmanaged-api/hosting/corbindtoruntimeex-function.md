---
title: CorBindToRuntimeEx – funkce
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b45efb634ca9b88768d6e30884085f28ad17b7c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490590"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="6fcda-102">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="6fcda-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="6fcda-103">Umožní nespravovaným hostitelům načíst modul CLR (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="6fcda-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="6fcda-104">[Corbindtoruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) a `CorBindToRuntimeEx` funkce provádět stejnou operaci, ale `CorBindToRuntimeEx` funkce umožňuje nastavení příznaků, které určují chování modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6fcda-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="6fcda-105">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6fcda-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="6fcda-106">Tato funkce přebírá sadu parametrů, které umožňují hostitele provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="6fcda-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="6fcda-107">Zadejte verzi modulu runtime, který bude načten.</span><span class="sxs-lookup"><span data-stu-id="6fcda-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="6fcda-108">Označuje, zda se mají načíst sestavení serveru nebo pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="6fcda-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="6fcda-109">Určit, jestli se provádí uvolňování paměti nebo nesouběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6fcda-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fcda-110">Souběžné uvolňování paměti se nepodporuje v aplikacích spuštěných WOW64 x86 emulátor v 64bitových systémech, které implementují Intel Itanium architekturu (dříve označovanou jako IA-64).</span><span class="sxs-lookup"><span data-stu-id="6fcda-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="6fcda-111">Další informace o použití modulu WOW64 v 64bitových systémech Windows najdete v tématu [spuštění 32bitových aplikací](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="6fcda-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="6fcda-112">Řídí, zda sestavení jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="6fcda-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="6fcda-113">Získat ukazatel rozhraní k [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) , který je možné nastavit další možnosti konfigurace instance modulu CLR, před jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="6fcda-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fcda-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fcda-114">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6fcda-115">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fcda-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="6fcda-116">[in] Řetězec, který popisuje verzi modulu CLR, která chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="6fcda-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="6fcda-117">Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí oddělených tečkami: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="6fcda-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="6fcda-118">Řetězec předaný jako `pwszVersion` musí začínat znakem "v" následovaný prvními třemi částmi čísla verze (například "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="6fcda-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="6fcda-119">Některé verze modulu CLR jsou nainstalovány s prohlášením o zásadách, které určuje kompatibilitu s předchozími verzemi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6fcda-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="6fcda-120">Ve výchozím nastavení překrytí spuštění vyhodnotí `pwszVersion` proti prohlášení zásad a načte nejnovější verze modulu runtime, který je kompatibilní s verzí, které jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="6fcda-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="6fcda-121">Hostitel může donutit překrytí, aby přeskočilo hodnocení zásad a načetlo přesnou verzi zadané v `pwszVersion` předáním hodnoty z `STARTUP_LOADER_SAFEMODE` pro `startupFlags` parametru, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="6fcda-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="6fcda-122">Pokud volající zadá hodnotu null pro `pwszVersion`, `CorBindToRuntimeEx` identifikuje sadu instalovaných modulů runtime, jejichž čísla verze nižší než modul runtime rozhraní .NET Framework 4 a načte nejnovější verzi modulu runtime z této sady.</span><span class="sxs-lookup"><span data-stu-id="6fcda-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="6fcda-123">Pokud je nainstalovaná starší verze je nebude načíst rozhraní .NET Framework 4 nebo novější a selže.</span><span class="sxs-lookup"><span data-stu-id="6fcda-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="6fcda-124">Všimněte si, že předávání null poskytuje hostiteli žádnou kontrolu nad tím, které je načtená verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6fcda-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="6fcda-125">Přestože tento přístup může být vhodné v některých scénářích, důrazně doporučujeme, aby hostitel zadat konkrétní verzi, kterou načíst.</span><span class="sxs-lookup"><span data-stu-id="6fcda-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="6fcda-126">[in] Řetězec, který určuje, jestli se má načíst server nebo pracovní stanice sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="6fcda-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="6fcda-127">Platné hodnoty jsou `svr` a `wks`.</span><span class="sxs-lookup"><span data-stu-id="6fcda-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="6fcda-128">Sestavení serveru je optimalizováno pro využití více procesorů pro uvolňování paměti kolekce a sestavení pracovní stanice je optimalizována pro klientské aplikace spuštěné v počítači s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="6fcda-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="6fcda-129">Pokud `pwszBuildFlavor` je nastavena na hodnotu null, je načteno sestavení pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="6fcda-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="6fcda-130">Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno, i když `pwszBuildFlavor` je nastavena na `svr`.</span><span class="sxs-lookup"><span data-stu-id="6fcda-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="6fcda-131">Ale pokud `pwszBuildFlavor` je nastavena na `svr` a souběžné uvolňování je vyznačeno (viz popis `startupFlags` parametr), načte se sestavení serveru.</span><span class="sxs-lookup"><span data-stu-id="6fcda-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="6fcda-132">[in] Kombinace hodnot, které [startup_flags –](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="6fcda-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="6fcda-133">Tyto příznaky řídí souběžné uvolňování paměti, doménově neutrální kód a chování `pwszVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="6fcda-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="6fcda-134">Pokud není nastaven žádný příznak, výchozí hodnota je jedinou doménu.</span><span class="sxs-lookup"><span data-stu-id="6fcda-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="6fcda-135">Platné jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="6fcda-135">The following values are valid:</span></span>  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="6fcda-136">Popisy těchto příznaků, najdete v článku [startup_flags –](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="6fcda-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="6fcda-137">[in] `CLSID` Třídy typu coclass, která implementuje [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6fcda-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="6fcda-138">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="6fcda-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="6fcda-139">[in] `IID` Požadovaná rozhraní z `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="6fcda-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="6fcda-140">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="6fcda-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="6fcda-141">[out] Vrácený ukazatel rozhraní k `riid`.</span><span class="sxs-lookup"><span data-stu-id="6fcda-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fcda-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fcda-142">Remarks</span></span>  
 <span data-ttu-id="6fcda-143">Pokud `pwszVersion` Určuje verzi modulu runtime, který neexistuje, `CorBindToRuntimeEx` vrátí CLR_E_SHIM_RUNTIMELOAD hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6fcda-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="6fcda-144">Kontext spuštění a tok Windows Identity</span><span class="sxs-lookup"><span data-stu-id="6fcda-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="6fcda-145">V modulu CLR verze 1 <xref:System.Security.Principal.WindowsIdentity> objektu není téct přes asynchronní body jako nová vlákna, fondy vláken nebo zpětná volání časovače.</span><span class="sxs-lookup"><span data-stu-id="6fcda-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="6fcda-146">V modulu CLR verze 2.0 <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně spuštěné vlákno a toky ji napříč asynchronní čárky, ale ne přes hranice aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="6fcda-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="6fcda-147">Podobně platí <xref:System.Security.Principal.WindowsIdentity> objekt také průchodu čárky asynchronní.</span><span class="sxs-lookup"><span data-stu-id="6fcda-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="6fcda-148">Proto aktuální zosobnění ve vlákně, pokud existuje, toky příliš.</span><span class="sxs-lookup"><span data-stu-id="6fcda-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="6fcda-149">Je možné změnit toku dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="6fcda-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="6fcda-150">Úpravou <xref:System.Threading.ExecutionContext> nastavení potlačení toku na základě vlákno (najdete v článku <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, a <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).</span><span class="sxs-lookup"><span data-stu-id="6fcda-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="6fcda-151">Změnou výchozí režim procesu na režim kompatibility verze 1, kde <xref:System.Security.Principal.WindowsIdentity> objektu není téct přes asynchronní fázi bez ohledu na to <xref:System.Threading.ExecutionContext> nastavení pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="6fcda-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="6fcda-152">Jak změnit výchozí režim závisí na, jestli používat spravované spustitelný soubor nebo nespravovaných hostitelských rozhraní načíst modul CLR:</span><span class="sxs-lookup"><span data-stu-id="6fcda-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="6fcda-153">Pro spravované spustitelné soubory, je nutné nastavit `enabled` atribut [ \<legacyimpersonationpolicy – >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="6fcda-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="6fcda-154">Pro nespravovaná rozhraní pro hostování, nastavit `STARTUP_LEGACY_IMPERSONATION` příznak v `startupFlags` parametru při volání `CorBindToRuntimeEx` funkce.</span><span class="sxs-lookup"><span data-stu-id="6fcda-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="6fcda-155">Režim kompatibility verze 1 platí pro celý proces a všech doménách aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="6fcda-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fcda-156">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fcda-156">Requirements</span></span>  
 <span data-ttu-id="6fcda-157">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fcda-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fcda-158">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6fcda-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6fcda-159">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6fcda-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6fcda-160">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fcda-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fcda-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fcda-161">See also</span></span>

- [<span data-ttu-id="6fcda-162">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="6fcda-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="6fcda-163">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="6fcda-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="6fcda-164">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="6fcda-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="6fcda-165">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="6fcda-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="6fcda-166">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6fcda-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="6fcda-167">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6fcda-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
