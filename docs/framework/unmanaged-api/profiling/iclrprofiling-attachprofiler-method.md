---
title: ICLRProfiling::AttachProfiler – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efc097fd9b4da668aafce90ce601a3143ea57dc7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763167"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="b7917-102">ICLRProfiling::AttachProfiler – metoda</span><span class="sxs-lookup"><span data-stu-id="b7917-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="b7917-103">Připojí zadaný profiler do určeného procesu.</span><span class="sxs-lookup"><span data-stu-id="b7917-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7917-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7917-104">Syntax</span></span>  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7917-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7917-105">Parameters</span></span>  
 `dwProfileeProcessID`  
 <span data-ttu-id="b7917-106">[in] Proces ID procesu, ke kterému by měl profiler připojen.</span><span class="sxs-lookup"><span data-stu-id="b7917-106">[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="b7917-107">Na 64bitovém počítači profilovaný proces bitové verze musí odpovídat počtu bitů aktivační proces, který volá `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="b7917-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="b7917-108">Pokud uživatelský účet, pod kterým `AttachProfiler` nazývá má oprávnění správce, Cílový proces může být jakýkoli proces v systému.</span><span class="sxs-lookup"><span data-stu-id="b7917-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="b7917-109">V opačném případě cílový proces musí být vlastněno stejným uživatelským účtem.</span><span class="sxs-lookup"><span data-stu-id="b7917-109">Otherwise, the target process must be owned by the same user account.</span></span>  
  
 `dwMillisecondsMax`  
 <span data-ttu-id="b7917-110">[in] Doba trvání v milisekundách pro `AttachProfiler` dokončete.</span><span class="sxs-lookup"><span data-stu-id="b7917-110">[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="b7917-111">Aktivační proces by měla předat vypršení časového limitu, který je znám jako dostatečná pro konkrétní profiler dokončit jeho inicializaci.</span><span class="sxs-lookup"><span data-stu-id="b7917-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>  
  
 `pClsidProfiler`  
 <span data-ttu-id="b7917-112">[in] Ukazatel na identifikátor CLSID profileru, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="b7917-112">[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="b7917-113">Aktivační proces můžete znovu použít tuto paměť po `AttachProfiler` vrátí.</span><span class="sxs-lookup"><span data-stu-id="b7917-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>  
  
 `wszProfilerPath`  
 <span data-ttu-id="b7917-114">[in] Úplná cesta k souboru knihovny DLL profileru, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="b7917-114">[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="b7917-115">Tento řetězec může obsahovat více než 260 znaků včetně ukončovacího znaku null.</span><span class="sxs-lookup"><span data-stu-id="b7917-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="b7917-116">Pokud `wszProfilerPath` má hodnotu null nebo prázdný řetězec, modul CLR (CLR) se pokusí najít vyhledáváním v registru CLSID umístění souboru knihovny DLL profileru, který `pClsidProfiler` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="b7917-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="b7917-117">[in] Ukazatel na data, která má být předán profileru pomocí [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b7917-117">[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="b7917-118">Aktivační proces můžete znovu použít tuto paměť po `AttachProfiler` vrátí.</span><span class="sxs-lookup"><span data-stu-id="b7917-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="b7917-119">Pokud `pvClientData` má hodnotu null, `cbClientData` musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="b7917-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="b7917-120">[in] Velikost v bajtech, dat, která `pvClientData` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="b7917-120">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7917-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b7917-121">Return Value</span></span>  
 <span data-ttu-id="b7917-122">Tato metoda vrátí následující výsledky HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b7917-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="b7917-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7917-123">HRESULT</span></span>|<span data-ttu-id="b7917-124">Popis</span><span class="sxs-lookup"><span data-stu-id="b7917-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7917-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7917-125">S_OK</span></span>|<span data-ttu-id="b7917-126">Zadaný profiler byl úspěšně přiřazen do cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="b7917-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="b7917-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="b7917-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="b7917-128">Už existuje profiler aktivní nebo připojení k cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="b7917-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="b7917-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="b7917-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="b7917-130">Zadaný profiler nepodporuje připojení.</span><span class="sxs-lookup"><span data-stu-id="b7917-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="b7917-131">Aktivační proces může pokusit o připojení různých profileru.</span><span class="sxs-lookup"><span data-stu-id="b7917-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="b7917-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="b7917-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="b7917-133">Nemůže požádat o profileru přílohu, protože verze Cílový proces není kompatibilní s aktuální proces, který volá `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="b7917-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="b7917-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="b7917-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="b7917-135">Uživatel aktivační proces nemá přístup do cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="b7917-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="b7917-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="b7917-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="b7917-137">Uživatel aktivační proces nemá oprávnění potřebná pro připojení profileru k dané cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="b7917-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="b7917-138">V protokolu událostí aplikace může obsahovat další informace.</span><span class="sxs-lookup"><span data-stu-id="b7917-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="b7917-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="b7917-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="b7917-140">Došlo k chybě při komunikaci s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="b7917-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="b7917-141">Běžně se to stane, když Cílový proces se vypíná.</span><span class="sxs-lookup"><span data-stu-id="b7917-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="b7917-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="b7917-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="b7917-143">Cílový proces neexistuje nebo není spuštěn CLR, který podporuje přílohy.</span><span class="sxs-lookup"><span data-stu-id="b7917-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="b7917-144">To může znamenat, že modul CLR byl odpojen od posledního volání enumerační metoda modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b7917-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="b7917-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="b7917-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="b7917-146">Bez začátek načíst profiler vypršel její časový limit.</span><span class="sxs-lookup"><span data-stu-id="b7917-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="b7917-147">Můžete opakovat operaci připojení.</span><span class="sxs-lookup"><span data-stu-id="b7917-147">You can retry the attach operation.</span></span> <span data-ttu-id="b7917-148">Vypršení časového limitu dojde finalizační metody v cílovém procesu běží po dobu delší než hodnota časového limitu.</span><span class="sxs-lookup"><span data-stu-id="b7917-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="b7917-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b7917-149">E_INVALIDARG</span></span>|<span data-ttu-id="b7917-150">Jeden nebo více parametrů obsahuje neplatnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b7917-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="b7917-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b7917-151">E_FAIL</span></span>|<span data-ttu-id="b7917-152">Došlo k selhání některých jiných, Neurčeno.</span><span class="sxs-lookup"><span data-stu-id="b7917-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="b7917-153">Další kódy chyb</span><span class="sxs-lookup"><span data-stu-id="b7917-153">Other error codes</span></span>|<span data-ttu-id="b7917-154">Pokud profiler [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) HRESULT označující selhání, vrátí metoda `AttachProfiler` vrátí to stejné HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b7917-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="b7917-155">V takovém případě E_NOTIMPL je převedena na CORPROF_E_PROFILER_NOT_ATTACHABLE.</span><span class="sxs-lookup"><span data-stu-id="b7917-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7917-156">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7917-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="b7917-157">Správa paměti</span><span class="sxs-lookup"><span data-stu-id="b7917-157">Memory Management</span></span>  
 <span data-ttu-id="b7917-158">V udržení s modelu COM konvence volající `AttachProfiler` (například aktivační kód vytvořené profilerem vývojáře) zodpovídá za přidělování a zrušení přidělení paměti pro data, která `pvClientData` parametr odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="b7917-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="b7917-159">Když modul CLR provede `AttachProfiler` volání, vytvoří kopii paměti, která `pvClientData` odkazuje na a odesílá do cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="b7917-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="b7917-160">Když do cílového procesu CLR obdrží vlastní kopii `pvClientData` bloku, předá bloku do profileru pomocí `InitializeForAttach` metoda a pak zruší přidělení jeho kopii `pvClientData` blok z cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="b7917-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7917-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7917-161">Requirements</span></span>  
 <span data-ttu-id="b7917-162">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7917-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7917-163">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b7917-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b7917-164">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7917-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7917-165">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7917-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7917-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7917-166">See also</span></span>

- [<span data-ttu-id="b7917-167">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7917-167">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b7917-168">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7917-168">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b7917-169">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b7917-169">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b7917-170">Profilace</span><span class="sxs-lookup"><span data-stu-id="b7917-170">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
