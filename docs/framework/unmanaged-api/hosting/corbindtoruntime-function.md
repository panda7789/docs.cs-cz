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
ms.openlocfilehash: 0bcfe42a70d64c091851a1eec81d03e49dbde52b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616659"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="2ee96-102">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="2ee96-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="2ee96-103">Umožňuje nespravovaným hostitelům načíst modul CLR (Common Language Runtime) do procesu.</span><span class="sxs-lookup"><span data-stu-id="2ee96-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="2ee96-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2ee96-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee96-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ee96-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ee96-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ee96-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="2ee96-107">pro Řetězec popisující verzi modulu CLR, kterou chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="2ee96-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="2ee96-108">Číslo verze v .NET Framework se skládá ze čtyř částí oddělených tečkami: *hlavní_verze. podverze. sestavení. revize*.</span><span class="sxs-lookup"><span data-stu-id="2ee96-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="2ee96-109">Řetězec předaný jako `pwszVersion` musí začínat znakem "v" následovaný prvními třemi částmi čísla verze (například "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="2ee96-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="2ee96-110">Některé verze modulu CLR jsou nainstalovány s příkazem zásad, který určuje kompatibilitu s předchozími verzemi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="2ee96-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="2ee96-111">Ve výchozím nastavení překrytí po spuštění vyhodnocuje `pwszVersion` příkazy zásad a načte nejnovější verzi modulu runtime, která je kompatibilní s požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="2ee96-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="2ee96-112">Hostitel může vynutit překrytí a přeskočit vyhodnocení zásad a načíst přesnou verzi určenou v `pwszVersion` předáním hodnoty `STARTUP_LOADER_SAFEMODE` `flags` parametru, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="2ee96-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="2ee96-113">Pokud volající pro je zadána hodnota null `pwszVersion` , je načtena nejnovější verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2ee96-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="2ee96-114">Předání hodnoty null dává hostiteli žádnou kontrolu nad tím, která verze modulu runtime je načtena.</span><span class="sxs-lookup"><span data-stu-id="2ee96-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="2ee96-115">I když tento přístup může být v některých scénářích vhodný, důrazně doporučujeme, aby hostitel zadal konkrétní verzi, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="2ee96-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="2ee96-116">pro Řetězec, který určuje, zda má být načten Server nebo pracovní stanice sestavení modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="2ee96-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="2ee96-117">Platné hodnoty jsou `svr` a `wks` .</span><span class="sxs-lookup"><span data-stu-id="2ee96-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="2ee96-118">Sestavení serveru je optimalizované tak, aby využívalo více procesorů pro uvolňování paměti a aby bylo sestavení pracovní stanice optimalizované pro klientské aplikace běžící na počítači s jedním procesorem.</span><span class="sxs-lookup"><span data-stu-id="2ee96-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="2ee96-119">Pokud `pwszBuildFlavor` je nastaven na hodnotu null, je načteno sestavení pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="2ee96-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="2ee96-120">Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno i v případě, že `pwszBuildFlavor` je nastavena na `svr` .</span><span class="sxs-lookup"><span data-stu-id="2ee96-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="2ee96-121">Pokud je však `pwszBuildFlavor` nastavena na `svr` a souběžné uvolňování paměti zadáno (viz popis `flags` parametru), je sestavení serveru načteno.</span><span class="sxs-lookup"><span data-stu-id="2ee96-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="2ee96-122">pro `CLSID`Třída typu coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2ee96-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="2ee96-123">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="2ee96-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="2ee96-124">pro Z `IID` vyžádaného rozhraní z `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="2ee96-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="2ee96-125">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="2ee96-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="2ee96-126">mimo Vrácený ukazatel rozhraní na `riid` .</span><span class="sxs-lookup"><span data-stu-id="2ee96-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ee96-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ee96-127">Remarks</span></span>  
 <span data-ttu-id="2ee96-128">Pokud `pwszVersion` Určuje verzi modulu runtime, která neexistuje, `CorBindToRuntimeEx` vrátí hodnotu HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="2ee96-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="2ee96-129">Kontext spuštění a tok identity Windows</span><span class="sxs-lookup"><span data-stu-id="2ee96-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="2ee96-130">Ve verzi 1 modulu CLR <xref:System.Security.Principal.WindowsIdentity> netok objektu mezi asynchronními body, jako jsou nová vlákna, fondy vláken nebo zpětná volání časovače.</span><span class="sxs-lookup"><span data-stu-id="2ee96-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="2ee96-131">Ve verzi 2,0 CLR <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně zpracovávaném vlákně a natéká ho napříč jakýmkoli asynchronním bodem, ale ne napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2ee96-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="2ee96-132">Podobně <xref:System.Security.Principal.WindowsIdentity> objekt také toků napříč jakýmkoli asynchronním bodem.</span><span class="sxs-lookup"><span data-stu-id="2ee96-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="2ee96-133">Proto aktuální zosobnění ve vlákně, pokud nějaký existuje, je také toků.</span><span class="sxs-lookup"><span data-stu-id="2ee96-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="2ee96-134">Tok můžete změnit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="2ee96-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="2ee96-135">Úpravou <xref:System.Threading.ExecutionContext> nastavení pro potlačení toku na základě jednotlivých vláken (viz <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> metody, a <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> ).</span><span class="sxs-lookup"><span data-stu-id="2ee96-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="2ee96-136">Změnou výchozího režimu procesu na režim kompatibility verze 1, kde objekt neprovádí <xref:System.Security.Principal.WindowsIdentity> tok napříč žádným asynchronním bodem bez ohledu na <xref:System.Threading.ExecutionContext> nastavení v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="2ee96-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="2ee96-137">Způsob změny výchozího režimu závisí na tom, zda používáte spravovaný spustitelný soubor nebo nespravované rozhraní hostování pro načtení modulu CLR:</span><span class="sxs-lookup"><span data-stu-id="2ee96-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="2ee96-138">U spravovaných spustitelných souborů je nutné nastavit `enabled` atribut prvku [ \< legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) na `true` .</span><span class="sxs-lookup"><span data-stu-id="2ee96-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="2ee96-139">U nespravovaných hostitelských rozhraní nastavte `STARTUP_LEGACY_IMPERSONATION` příznak `flags` při volání funkce na parametr `CorBindToRuntimeEx` .</span><span class="sxs-lookup"><span data-stu-id="2ee96-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="2ee96-140">Režim kompatibility verze 1 se vztahuje na celý proces a na všechny domény aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="2ee96-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ee96-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ee96-141">Remarks</span></span>  
 <span data-ttu-id="2ee96-142">[CorBindToRuntimeEx –](corbindtoruntimeex-function.md) a `CorBindToRuntime` provede stejnou operaci, ale funkce vám `CorBindToRuntimeEx` umožní nastavit příznaky pro určení chování modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="2ee96-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ee96-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ee96-143">Requirements</span></span>  
 <span data-ttu-id="2ee96-144">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ee96-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ee96-145">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2ee96-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ee96-146">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2ee96-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ee96-147">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ee96-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee96-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ee96-148">See also</span></span>

- [<span data-ttu-id="2ee96-149">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="2ee96-149">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="2ee96-150">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="2ee96-150">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="2ee96-151">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="2ee96-151">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="2ee96-152">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="2ee96-152">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="2ee96-153">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ee96-153">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="2ee96-154">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="2ee96-154">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
