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
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176497"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="6266c-102">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="6266c-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="6266c-103">Umožňuje nespravovaným hostitelům načíst běžný jazyk runtime (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="6266c-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="6266c-104">[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) a `CorBindToRuntimeEx` funkce provádět stejnou operaci, ale `CorBindToRuntimeEx` funkce umožňuje nastavit příznaky určit chování CLR.</span><span class="sxs-lookup"><span data-stu-id="6266c-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="6266c-105">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="6266c-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="6266c-106">Tato funkce přebírá sadu parametrů, které umožňují hostiteli provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="6266c-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="6266c-107">Zadejte verzi runtime, která bude načtena.</span><span class="sxs-lookup"><span data-stu-id="6266c-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="6266c-108">Určete, zda má být načteno sestavení serveru nebo pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="6266c-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="6266c-109">Určit, zda je provedeno souběžné uvolňování paměti nebo nesouběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6266c-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6266c-110">Souběžné uvolňování paměti není podporováno v aplikacích se systémem WOW64 x86 emulátoru na 64bitové systémy, které implementují architekturu Intel Itanium (dříve nazývané IA-64).</span><span class="sxs-lookup"><span data-stu-id="6266c-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="6266c-111">Další informace o používání wow64 v 64bitových systémech Windows naleznete v [tématu Spuštění 32bitových aplikací](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="6266c-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="6266c-112">Určit, zda sestavení jsou načteny jako neutrální domény.</span><span class="sxs-lookup"><span data-stu-id="6266c-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="6266c-113">Získejte ukazatel rozhraní na [ICorRuntimeHost,](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) který lze použít k nastavení dalších možností pro konfiguraci instance CLR před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="6266c-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6266c-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6266c-114">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,
    [in]  LPCWSTR      pwszBuildFlavor,
    [in]  DWORD        startupFlags,
    [in]  REFCLSID     rclsid,
    [in]  REFIID       riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6266c-115">Parametry</span><span class="sxs-lookup"><span data-stu-id="6266c-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="6266c-116">[v] Řetězec popisující verzi CLR, kterou chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="6266c-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="6266c-117">Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí oddělených tečkami: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="6266c-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="6266c-118">Řetězec předán `pwszVersion` jako musí začínat znak "v" následuje první tři části číslo verze (například "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="6266c-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="6266c-119">Některé verze clr jsou nainstalovány s prohlášením zásad, které určuje kompatibilitu s předchozími verzemi CLR.</span><span class="sxs-lookup"><span data-stu-id="6266c-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="6266c-120">Ve výchozím nastavení překrytí `pwszVersion` při spuštění vyhodnocuje příkazy zásad a načte nejnovější verzi běhu, který je kompatibilní s požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="6266c-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="6266c-121">Hostitel může vynutit překrytí přeskočit vyhodnocení zásad a `pwszVersion` načíst přesnou `startupFlags` verzi zadanou v souboru předáním hodnoty parametru, `STARTUP_LOADER_SAFEMODE` jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="6266c-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="6266c-122">Pokud volající určuje hodnotu null for `pwszVersion`, `CorBindToRuntimeEx` identifikuje sadu nainstalovaných runtime, jejichž čísla verzí jsou nižší než runtime rozhraní .NET Framework 4, a načte nejnovější verzi runtime z této sady.</span><span class="sxs-lookup"><span data-stu-id="6266c-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="6266c-123">Nenačte rozhraní .NET Framework 4 nebo novější a selže, pokud není nainstalována žádná starší verze.</span><span class="sxs-lookup"><span data-stu-id="6266c-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="6266c-124">Všimněte si, že předávání null dává hostiteli žádnou kontrolu nad tím, která verze runtime je načten.</span><span class="sxs-lookup"><span data-stu-id="6266c-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="6266c-125">Ačkoli tento přístup může být vhodné v některých scénářích, důrazně doporučujeme, aby hostitel dodat konkrétní verzi načíst.</span><span class="sxs-lookup"><span data-stu-id="6266c-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="6266c-126">[v] Řetězec, který určuje, zda má být server nebo sestavení pracovní stanice CLR načíst.</span><span class="sxs-lookup"><span data-stu-id="6266c-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="6266c-127">Platné hodnoty `svr` `wks`jsou a .</span><span class="sxs-lookup"><span data-stu-id="6266c-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="6266c-128">Sestavení serveru je optimalizováno tak, aby využívalo více procesorů pro uvolňování paměti, a sestavení pracovní stanice je optimalizováno pro klientské aplikace spuštěné v počítači s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="6266c-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="6266c-129">Pokud `pwszBuildFlavor` je nastavena na hodnotu null, sestavení pracovní stanice je načten.</span><span class="sxs-lookup"><span data-stu-id="6266c-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="6266c-130">Při spuštění na počítači s jedním procesorem je sestavení `pwszBuildFlavor` pracovní `svr`stanice vždy načteno, i když je nastaveno na .</span><span class="sxs-lookup"><span data-stu-id="6266c-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="6266c-131">Však `pwszBuildFlavor` pokud je `svr` nastavena a souběžné uvolňování paměti `startupFlags` je zadán (viz popis parametru), sestavení serveru je načten.</span><span class="sxs-lookup"><span data-stu-id="6266c-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="6266c-132">[v] Kombinace hodnot [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="6266c-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="6266c-133">Tyto příznaky řídí souběžné uvolňování paměti, kód neutrální `pwszVersion` z domény a chování parametru.</span><span class="sxs-lookup"><span data-stu-id="6266c-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="6266c-134">Výchozí hodnota je jedna doména, pokud není nastaven žádný příznak.</span><span class="sxs-lookup"><span data-stu-id="6266c-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="6266c-135">Následující hodnoty jsou platné:</span><span class="sxs-lookup"><span data-stu-id="6266c-135">The following values are valid:</span></span>  
  
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
  
 <span data-ttu-id="6266c-136">Popis těchto příznaků naleznete ve [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="6266c-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="6266c-137">[v] Coclass, `CLSID` která implementuje buď [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6266c-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="6266c-138">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="6266c-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="6266c-139">[v] Požadované `IID` rozhraní od `rclsid`aplikace .</span><span class="sxs-lookup"><span data-stu-id="6266c-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="6266c-140">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="6266c-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="6266c-141">[out] Vrácený ukazatel `riid`rozhraní na .</span><span class="sxs-lookup"><span data-stu-id="6266c-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6266c-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6266c-142">Remarks</span></span>  
 <span data-ttu-id="6266c-143">Pokud `pwszVersion` určuje verzi runtime, která `CorBindToRuntimeEx` neexistuje, vrátí hodnotu HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="6266c-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="6266c-144">Kontext spuštění a tok identity systému Windows</span><span class="sxs-lookup"><span data-stu-id="6266c-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="6266c-145">Ve verzi 1 CLR <xref:System.Security.Principal.WindowsIdentity> objekt netokuje přes asynchronní body, jako jsou nová vlákna, fondy vláken nebo zpětná volání časovače.</span><span class="sxs-lookup"><span data-stu-id="6266c-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="6266c-146">Ve verzi 2.0 CLR <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně spuštěném vlákně a nateče přes libovolný asynchronní bod, ale ne přes hranice domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6266c-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="6266c-147">Podobně <xref:System.Security.Principal.WindowsIdentity> objekt také toky přes všechny asynchronní bod.</span><span class="sxs-lookup"><span data-stu-id="6266c-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="6266c-148">Proto aktuální zosobnění ve vlákně, pokud existuje, toky příliš.</span><span class="sxs-lookup"><span data-stu-id="6266c-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="6266c-149">Tok můžete změnit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="6266c-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="6266c-150">Úpravou <xref:System.Threading.ExecutionContext> nastavení potlačit tok na základě vlákno (viz <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> , a metody).</span><span class="sxs-lookup"><span data-stu-id="6266c-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="6266c-151">Změnou výchozího režimu procesu na režim <xref:System.Security.Principal.WindowsIdentity> kompatibility verze 1, kde objekt neprobíhá <xref:System.Threading.ExecutionContext> přes žádný asynchronní bod, bez ohledu na nastavení v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="6266c-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="6266c-152">Způsob změny výchozího režimu závisí na tom, zda k načtení příkazu CLR načtete spravované spustitelné nebo nespravované hostitelské rozhraní:</span><span class="sxs-lookup"><span data-stu-id="6266c-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="6266c-153">U spravovaných spustitelných `enabled` souborů je nutné nastavit atribut [ \<staršího prvku ImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) na `true`.</span><span class="sxs-lookup"><span data-stu-id="6266c-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="6266c-154">Pro nespravované hostitelské rozhraní `STARTUP_LEGACY_IMPERSONATION` nastavte příznak `startupFlags` v parametru při volání `CorBindToRuntimeEx` funkce.</span><span class="sxs-lookup"><span data-stu-id="6266c-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="6266c-155">Režim kompatibility verze 1 se vztahuje na celý proces a na všechny aplikační domény v procesu.</span><span class="sxs-lookup"><span data-stu-id="6266c-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6266c-156">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6266c-156">Requirements</span></span>  
 <span data-ttu-id="6266c-157">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6266c-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6266c-158">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6266c-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6266c-159">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6266c-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6266c-160">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6266c-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6266c-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="6266c-161">See also</span></span>

- [<span data-ttu-id="6266c-162">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="6266c-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="6266c-163">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="6266c-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="6266c-164">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="6266c-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="6266c-165">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="6266c-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="6266c-166">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6266c-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="6266c-167">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6266c-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
