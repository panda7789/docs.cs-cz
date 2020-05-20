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
ms.openlocfilehash: dcf2ce8bdb7cec1f567e548ff3314e160fffe9fd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616629"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="6dbc5-102">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="6dbc5-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="6dbc5-103">Umožňuje nespravovaným hostitelům načíst modul CLR (Common Language Runtime) do procesu.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="6dbc5-104">[CorBindToRuntime](corbindtoruntime-function.md) a `CorBindToRuntimeEx` funkce provádějí stejnou operaci, ale `CorBindToRuntimeEx` funkce vám umožní nastavit příznaky pro určení chování CLR.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-104">The [CorBindToRuntime](corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="6dbc5-105">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="6dbc5-106">Tato funkce přijímá sadu parametrů, které umožní hostiteli provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="6dbc5-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="6dbc5-107">Zadejte verzi modulu runtime, který bude načten.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="6dbc5-108">Označuje, zda má být načteno sestavení serveru nebo pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="6dbc5-109">Určuje, zda je provedeno souběžné uvolňování paměti nebo nesouběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6dbc5-110">Souběžné uvolňování paměti není podporováno v aplikacích spouštějících emulátor WOW64 x86 v 64 systémech, které implementují architekturu Intel Itanium (dříve nazývané IA-64).</span><span class="sxs-lookup"><span data-stu-id="6dbc5-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="6dbc5-111">Další informace o používání WOW64 v systémech s 64 Windows najdete v tématu [spouštění 32 aplikací](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="6dbc5-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="6dbc5-112">Určete, zda jsou sestavení načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="6dbc5-113">Získejte ukazatel rozhraní na [ICorRuntimeHost](icorruntimehost-interface.md) , který lze použít k nastavení dalších možností konfigurace instance CLR před jeho spuštěním.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-113">Obtain an interface pointer to an [ICorRuntimeHost](icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dbc5-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dbc5-114">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6dbc5-115">Parametry</span><span class="sxs-lookup"><span data-stu-id="6dbc5-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="6dbc5-116">pro Řetězec popisující verzi modulu CLR, kterou chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="6dbc5-117">Číslo verze v .NET Framework se skládá ze čtyř částí oddělených tečkami: *hlavní_verze. podverze. sestavení. revize*.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="6dbc5-118">Řetězec předaný jako `pwszVersion` musí začínat znakem "v" následovaný prvními třemi částmi čísla verze (například "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="6dbc5-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="6dbc5-119">Některé verze modulu CLR jsou nainstalovány s příkazem zásad, který určuje kompatibilitu s předchozími verzemi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="6dbc5-120">Ve výchozím nastavení překrytí po spuštění vyhodnocuje `pwszVersion` příkazy zásad a načte nejnovější verzi modulu runtime, která je kompatibilní s požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="6dbc5-121">Hostitel může vynutit překrytí a přeskočit vyhodnocení zásad a načíst přesnou verzi určenou v `pwszVersion` předáním hodnoty `STARTUP_LOADER_SAFEMODE` `startupFlags` parametru, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="6dbc5-122">Pokud volající určí hodnotu null pro `pwszVersion` , `CorBindToRuntimeEx` identifikuje sadu instalovaných modulů runtime, jejichž čísla verzí jsou nižší než runtime .NET Framework 4, a načte nejnovější verzi modulu runtime z této sady.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="6dbc5-123">Nenačte .NET Framework 4 nebo novější a neproběhne úspěšně, pokud není nainstalovaná žádná starší verze.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="6dbc5-124">Všimněte si, že předání hodnoty null dává hostiteli žádnou kontrolu nad tím, která verze modulu runtime je načtena.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="6dbc5-125">I když tento přístup může být v některých scénářích vhodný, důrazně doporučujeme, aby hostitel zadal konkrétní verzi, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="6dbc5-126">pro Řetězec, který určuje, zda má být načten Server nebo pracovní stanice sestavení modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="6dbc5-127">Platné hodnoty jsou `svr` a `wks` .</span><span class="sxs-lookup"><span data-stu-id="6dbc5-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="6dbc5-128">Sestavení serveru je optimalizované tak, aby využívalo více procesorů pro uvolňování paměti a aby bylo sestavení pracovní stanice optimalizované pro klientské aplikace běžící na počítači s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="6dbc5-129">Pokud `pwszBuildFlavor` je nastaven na hodnotu null, je načteno sestavení pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="6dbc5-130">Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno i v případě, že `pwszBuildFlavor` je nastavena na `svr` .</span><span class="sxs-lookup"><span data-stu-id="6dbc5-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="6dbc5-131">Pokud je však `pwszBuildFlavor` nastavena na `svr` a souběžné uvolňování paměti zadáno (viz popis `startupFlags` parametru), je sestavení serveru načteno.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="6dbc5-132">pro Kombinace hodnot [STARTUP_FLAGS](startup-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-132">[in] A combination of values of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="6dbc5-133">Tyto příznaky řídí souběžné uvolňování paměti, doménový neutrální kód a chování `pwszVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="6dbc5-134">Výchozí hodnota je jedna doména, pokud není nastaven žádný příznak.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="6dbc5-135">Platné jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="6dbc5-135">The following values are valid:</span></span>  
  
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
  
 <span data-ttu-id="6dbc5-136">Popisy těchto příznaků naleznete v [STARTUP_FLAGS](startup-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-136">For descriptions of these flags, see the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="6dbc5-137">pro `CLSID`Třída typu coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6dbc5-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="6dbc5-138">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="6dbc5-139">pro Z `IID` vyžádaného rozhraní z `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="6dbc5-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="6dbc5-140">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="6dbc5-141">mimo Vrácený ukazatel rozhraní na `riid` .</span><span class="sxs-lookup"><span data-stu-id="6dbc5-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6dbc5-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6dbc5-142">Remarks</span></span>  
 <span data-ttu-id="6dbc5-143">Pokud `pwszVersion` Určuje verzi modulu runtime, která neexistuje, `CorBindToRuntimeEx` vrátí hodnotu HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="6dbc5-144">Kontext spuštění a tok identity Windows</span><span class="sxs-lookup"><span data-stu-id="6dbc5-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="6dbc5-145">Ve verzi 1 modulu CLR <xref:System.Security.Principal.WindowsIdentity> netok objektu mezi asynchronními body, jako jsou nová vlákna, fondy vláken nebo zpětná volání časovače.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="6dbc5-146">Ve verzi 2,0 CLR <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně zpracovávaném vlákně a natéká ho napříč jakýmkoli asynchronním bodem, ale ne napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="6dbc5-147">Podobně <xref:System.Security.Principal.WindowsIdentity> objekt také toků napříč jakýmkoli asynchronním bodem.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="6dbc5-148">Proto aktuální zosobnění ve vlákně, pokud nějaký existuje, je také toků.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="6dbc5-149">Tok můžete změnit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="6dbc5-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="6dbc5-150">Úpravou <xref:System.Threading.ExecutionContext> nastavení pro potlačení toku na základě jednotlivých vláken (viz <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> metody, a <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> ).</span><span class="sxs-lookup"><span data-stu-id="6dbc5-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="6dbc5-151">Změnou výchozího režimu procesu na režim kompatibility verze 1, kde objekt neprovádí <xref:System.Security.Principal.WindowsIdentity> tok napříč žádným asynchronním bodem bez ohledu na <xref:System.Threading.ExecutionContext> nastavení v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="6dbc5-152">Způsob změny výchozího režimu závisí na tom, zda používáte spravovaný spustitelný soubor nebo nespravované rozhraní hostování pro načtení modulu CLR:</span><span class="sxs-lookup"><span data-stu-id="6dbc5-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="6dbc5-153">U spravovaných spustitelných souborů je nutné nastavit `enabled` atribut prvku [ \< legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) na `true` .</span><span class="sxs-lookup"><span data-stu-id="6dbc5-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="6dbc5-154">U nespravovaných hostitelských rozhraní nastavte `STARTUP_LEGACY_IMPERSONATION` příznak `startupFlags` při volání funkce na parametr `CorBindToRuntimeEx` .</span><span class="sxs-lookup"><span data-stu-id="6dbc5-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="6dbc5-155">Režim kompatibility verze 1 se vztahuje na celý proces a na všechny domény aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="6dbc5-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dbc5-156">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6dbc5-156">Requirements</span></span>  
 <span data-ttu-id="6dbc5-157">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dbc5-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dbc5-158">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6dbc5-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6dbc5-159">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6dbc5-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6dbc5-160">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dbc5-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbc5-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="6dbc5-161">See also</span></span>

- [<span data-ttu-id="6dbc5-162">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="6dbc5-162">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="6dbc5-163">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="6dbc5-163">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="6dbc5-164">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="6dbc5-164">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="6dbc5-165">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="6dbc5-165">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="6dbc5-166">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6dbc5-166">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="6dbc5-167">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6dbc5-167">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
