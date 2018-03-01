---
title: "ICLRProfiling::AttachProfiler – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5b364ab407294b20ac2f2f830e3f875169a18b7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="34708-102">ICLRProfiling::AttachProfiler – metoda</span><span class="sxs-lookup"><span data-stu-id="34708-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="34708-103">Připojí zadaný profileru zadaný procesu.</span><span class="sxs-lookup"><span data-stu-id="34708-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34708-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34708-104">Syntax</span></span>  
  
```  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34708-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34708-105">Parameters</span></span>  
 `dwProfileeProcessID`  
 <span data-ttu-id="34708-106">[v] ID procesu procesu, ke které je třeba připojit profileru.</span><span class="sxs-lookup"><span data-stu-id="34708-106">[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="34708-107">Na 64bitový počítač, musí odpovídat počtu bitů PROFILOVANÉHO proces počtu bitů aktivační proces, který volá `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="34708-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="34708-108">Pokud uživatelský účet, pod které `AttachProfiler` nazývá oprávněními pro správu, tento cílový proces může být jakýkoli proces v systému.</span><span class="sxs-lookup"><span data-stu-id="34708-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="34708-109">Tento Cílový proces, jinak hodnota musí být vlastníkem stejným uživatelským účtem.</span><span class="sxs-lookup"><span data-stu-id="34708-109">Otherwise, the target process must be owned by the same user account.</span></span>  
  
 `dwMillisecondsMax`  
 <span data-ttu-id="34708-110">[v] Doba trvání (v milisekundách) pro `AttachProfiler` k dokončení.</span><span class="sxs-lookup"><span data-stu-id="34708-110">[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="34708-111">Proces aktivace by měla předávat vypršení časového limitu, který se označuje dostačující pro konkrétní profileru k dokončení inicializace.</span><span class="sxs-lookup"><span data-stu-id="34708-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>  
  
 `pClsidProfiler`  
 <span data-ttu-id="34708-112">[v] Ukazatel na CLSID profilování má být načten.</span><span class="sxs-lookup"><span data-stu-id="34708-112">[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="34708-113">Proces aktivace můžete znovu použít tuto paměť po `AttachProfiler` vrátí.</span><span class="sxs-lookup"><span data-stu-id="34708-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>  
  
 `wszProfilerPath`  
 <span data-ttu-id="34708-114">[v] Úplná cesta k souboru DLL profileru má být načten.</span><span class="sxs-lookup"><span data-stu-id="34708-114">[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="34708-115">Tento řetězec musí obsahovat více než 260 znaků, včetně ukončení hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="34708-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="34708-116">Pokud `wszProfilerPath` má hodnotu null nebo prázdný řetězec, modul CLR (CLR) pokusí najít umístění souboru DLL profileru tak, že vyhledá v registru CLSID který `pClsidProfiler` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="34708-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="34708-117">[v] Ukazatel na data mají být předány profileru pomocí [icorprofilercallback3::initializeforattach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="34708-117">[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="34708-118">Proces aktivace můžete znovu použít tuto paměť po `AttachProfiler` vrátí.</span><span class="sxs-lookup"><span data-stu-id="34708-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="34708-119">Pokud `pvClientData` má hodnotu null, `cbClientData` musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="34708-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="34708-120">[v] Velikost v bajtech dat, která `pvClientData` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="34708-120">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34708-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="34708-121">Return Value</span></span>  
 <span data-ttu-id="34708-122">Tato metoda vrátí následující hodnoty HRESULT.</span><span class="sxs-lookup"><span data-stu-id="34708-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="34708-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34708-123">HRESULT</span></span>|<span data-ttu-id="34708-124">Popis</span><span class="sxs-lookup"><span data-stu-id="34708-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34708-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="34708-125">S_OK</span></span>|<span data-ttu-id="34708-126">Zadaný profileru se úspěšně připojil k tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="34708-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="34708-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="34708-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="34708-128">Již existuje profileru aktivních nebo připojení pro tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="34708-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="34708-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="34708-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="34708-130">Zadaný profileru nepodporuje připojení.</span><span class="sxs-lookup"><span data-stu-id="34708-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="34708-131">Proces aktivace se pokusit připojit různé profileru.</span><span class="sxs-lookup"><span data-stu-id="34708-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="34708-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="34708-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="34708-133">Nelze požadavek přílohu profileru, protože verze tento cílový proces je kompatibilní s aktuální proces, který volá `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="34708-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="34708-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="34708-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="34708-135">Uživatel aktivační proces nemá přístup k tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="34708-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="34708-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="34708-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="34708-137">Uživatel proces aktivace nemá oprávnění potřebná k připojení profileru k dané Cílový proces.</span><span class="sxs-lookup"><span data-stu-id="34708-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="34708-138">V protokolu událostí aplikace může obsahovat další informace.</span><span class="sxs-lookup"><span data-stu-id="34708-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="34708-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="34708-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="34708-140">Došlo k chybě při komunikaci s tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="34708-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="34708-141">K tomu běžně dochází, pokud byl tento cílový proces vypíná.</span><span class="sxs-lookup"><span data-stu-id="34708-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="34708-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="34708-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="34708-143">Tento Cílový proces neexistuje nebo není spuštěná CLR, který podporuje přílohy.</span><span class="sxs-lookup"><span data-stu-id="34708-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="34708-144">To může znamenat, že modulu CLR byl odpojen od volání metody výčtu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="34708-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="34708-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="34708-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="34708-146">Časový limit platnost bez začátku načíst profileru.</span><span class="sxs-lookup"><span data-stu-id="34708-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="34708-147">Může pokus zopakovat operaci připojení.</span><span class="sxs-lookup"><span data-stu-id="34708-147">You can retry the attach operation.</span></span> <span data-ttu-id="34708-148">Časové limity dojde finalizační metodu v tento cílový proces běží po dobu delší než hodnota časového limitu.</span><span class="sxs-lookup"><span data-stu-id="34708-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="34708-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="34708-149">E_INVALIDARG</span></span>|<span data-ttu-id="34708-150">Jeden nebo více parametrů obsahuje neplatnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="34708-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="34708-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34708-151">E_FAIL</span></span>|<span data-ttu-id="34708-152">Některé jiné, neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="34708-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="34708-153">Další kódy chyb</span><span class="sxs-lookup"><span data-stu-id="34708-153">Other error codes</span></span>|<span data-ttu-id="34708-154">Pokud profileru [icorprofilercallback3::initializeforattach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) HRESULT označující selhání, vrátí metoda `AttachProfiler` vrátí to stejné HRESULT.</span><span class="sxs-lookup"><span data-stu-id="34708-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="34708-155">V takovém případě E_NOTIMPL jsou převedeny na CORPROF_E_PROFILER_NOT_ATTACHABLE.</span><span class="sxs-lookup"><span data-stu-id="34708-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34708-156">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34708-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="34708-157">Správa paměti</span><span class="sxs-lookup"><span data-stu-id="34708-157">Memory Management</span></span>  
 <span data-ttu-id="34708-158">Při ochraně s konvence COM, volající `AttachProfiler` (například kód aktivační události vytvořené profileru vývojáře) zodpovídá za přidělování a zrušte přidělování paměti pro data, `pvClientData` parametr odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="34708-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="34708-159">Když spustí modulu CLR `AttachProfiler` volání, která umožňuje kopírování paměti, `pvClientData` odkazuje na a odesílá na tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="34708-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="34708-160">Když CLR uvnitř tento cílový proces obdrží vlastní kopii `pvClientData` bloku, pak předá bloku profileru prostřednictvím `InitializeForAttach` metoda a pak zruší přidělení jeho kopii `pvClientData` bloku z tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="34708-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34708-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34708-161">Requirements</span></span>  
 <span data-ttu-id="34708-162">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34708-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34708-163">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34708-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34708-164">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34708-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34708-165">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34708-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34708-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="34708-166">See Also</span></span>  
 [<span data-ttu-id="34708-167">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34708-167">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="34708-168">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34708-168">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="34708-169">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="34708-169">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="34708-170">Profilace</span><span class="sxs-lookup"><span data-stu-id="34708-170">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
