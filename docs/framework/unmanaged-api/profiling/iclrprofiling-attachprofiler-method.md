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
ms.openlocfilehash: 48ac09e1862ae58e79707235e891f72920de1251
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500556"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="ab244-102">ICLRProfiling::AttachProfiler – metoda</span><span class="sxs-lookup"><span data-stu-id="ab244-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="ab244-103">Připojí zadaný profiler k zadanému procesu.</span><span class="sxs-lookup"><span data-stu-id="ab244-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab244-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab244-104">Syntax</span></span>  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab244-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab244-105">Parameters</span></span>

- `dwProfileeProcessID`

  <span data-ttu-id="ab244-106">\[v] ID procesu procesu, ke kterému se má profiler připojit.</span><span class="sxs-lookup"><span data-stu-id="ab244-106">\[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="ab244-107">Na 64ovém počítači musí bitová verze procesu profilace odpovídat bitová verze procesu triggeru, který volá `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="ab244-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="ab244-108">Pokud uživatelský účet, pod kterým `AttachProfiler` je volána oprávnění správce, může být cílovým procesem v systému.</span><span class="sxs-lookup"><span data-stu-id="ab244-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="ab244-109">Jinak cílový proces musí být vlastněn stejným uživatelským účtem.</span><span class="sxs-lookup"><span data-stu-id="ab244-109">Otherwise, the target process must be owned by the same user account.</span></span>

- `dwMillisecondsMax`

  <span data-ttu-id="ab244-110">\[in] doba trvání (v milisekundách), po `AttachProfiler` kterou se má dokončit.</span><span class="sxs-lookup"><span data-stu-id="ab244-110">\[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="ab244-111">Proces triggeru by měl projít časovým limitem, který by měl být dostatečný pro konkrétní profiler k dokončení inicializace.</span><span class="sxs-lookup"><span data-stu-id="ab244-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>
  
- `pClsidProfiler`

  <span data-ttu-id="ab244-112">\[in] ukazatel na identifikátor CLSID profileru, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="ab244-112">\[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="ab244-113">Proces triggeru může po vrácení znovu použít tuto paměť `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="ab244-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>

- `wszProfilerPath`

  <span data-ttu-id="ab244-114">\[v] Úplná cesta k souboru DLL profileru, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="ab244-114">\[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="ab244-115">Řetězec nesmí obsahovat více než 260 znaků, včetně ukončovacího znaku null.</span><span class="sxs-lookup"><span data-stu-id="ab244-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="ab244-116">Pokud `wszProfilerPath` je hodnota null nebo prázdný řetězec, modul CLR (Common Language Runtime) se pokusí najít umístění souboru DLL profileru hledáním v registru pro identifikátor CLSID, `pClsidProfiler` na který odkazuje.</span><span class="sxs-lookup"><span data-stu-id="ab244-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>

- `pvClientData`

  <span data-ttu-id="ab244-117">\[v] ukazatel na data, která mají být předána do profileru metodou [ICorProfilerCallback3:: InitializeForAttach –](icorprofilercallback3-initializeforattach-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ab244-117">\[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="ab244-118">Proces triggeru může po vrácení znovu použít tuto paměť `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="ab244-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="ab244-119">Pokud `pvClientData` má hodnotu null, `cbClientData` musí mít hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="ab244-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>

- `cbClientData`

  <span data-ttu-id="ab244-120">\[in] velikost dat, na která odkazuje, v bajtech `pvClientData` .</span><span class="sxs-lookup"><span data-stu-id="ab244-120">\[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>

## <a name="return-value"></a><span data-ttu-id="ab244-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ab244-121">Return Value</span></span>  
 <span data-ttu-id="ab244-122">Tato metoda vrací následující hodnoty HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ab244-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="ab244-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ab244-123">HRESULT</span></span>|<span data-ttu-id="ab244-124">Description</span><span class="sxs-lookup"><span data-stu-id="ab244-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ab244-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="ab244-125">S_OK</span></span>|<span data-ttu-id="ab244-126">Zadaný Profiler byl úspěšně připojen k cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="ab244-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="ab244-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="ab244-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="ab244-128">Profiler je již aktivní nebo se k cílovému procesu připojuje.</span><span class="sxs-lookup"><span data-stu-id="ab244-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="ab244-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="ab244-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="ab244-130">Zadaný Profiler nepodporuje přílohu.</span><span class="sxs-lookup"><span data-stu-id="ab244-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="ab244-131">Aktivační proces se může pokusit připojit k jinému profileru.</span><span class="sxs-lookup"><span data-stu-id="ab244-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="ab244-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="ab244-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="ab244-133">Nelze vyžádat přílohu profileru, protože verze cílového procesu není kompatibilní s aktuálním procesem, který volá `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="ab244-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="ab244-134">HRESULT_FROM_WIN32 (ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="ab244-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="ab244-135">Uživatel procesu triggeru nemá přístup k cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="ab244-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="ab244-136">HRESULT_FROM_WIN32 (ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="ab244-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="ab244-137">Uživatel procesu triggeru nemá oprávnění potřebná k připojení profileru k danému cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="ab244-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="ab244-138">Protokol událostí aplikace může obsahovat více informací.</span><span class="sxs-lookup"><span data-stu-id="ab244-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="ab244-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="ab244-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="ab244-140">Při komunikaci s cílovým procesem došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="ab244-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="ab244-141">K tomu obvykle dochází v případě, že se cílový proces vypíná.</span><span class="sxs-lookup"><span data-stu-id="ab244-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="ab244-142">HRESULT_FROM_WIN32 (ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="ab244-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="ab244-143">Cílový proces neexistuje nebo není spuštěn modul CLR, který podporuje přílohu.</span><span class="sxs-lookup"><span data-stu-id="ab244-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="ab244-144">To může znamenat, že modul CLR byl uvolněn od volání metody výčtu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ab244-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="ab244-145">HRESULT_FROM_WIN32 (ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="ab244-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="ab244-146">Vypršel časový limit bez začátku načítání profileru.</span><span class="sxs-lookup"><span data-stu-id="ab244-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="ab244-147">Operaci připojení můžete opakovat.</span><span class="sxs-lookup"><span data-stu-id="ab244-147">You can retry the attach operation.</span></span> <span data-ttu-id="ab244-148">K vypršení časového limitu dojde, když finalizační metoda v cílovém procesu běží delší dobu než hodnota časového limitu.</span><span class="sxs-lookup"><span data-stu-id="ab244-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="ab244-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ab244-149">E_INVALIDARG</span></span>|<span data-ttu-id="ab244-150">Jeden nebo více parametrů má neplatné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ab244-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="ab244-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ab244-151">E_FAIL</span></span>|<span data-ttu-id="ab244-152">V některých případech došlo k nespecifikovanému selhání.</span><span class="sxs-lookup"><span data-stu-id="ab244-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="ab244-153">Další kódy chyb</span><span class="sxs-lookup"><span data-stu-id="ab244-153">Other error codes</span></span>|<span data-ttu-id="ab244-154">Pokud metoda [ICorProfilerCallback3:: InitializeForAttach –](icorprofilercallback3-initializeforattach-method.md) profileru vrátí hodnotu HRESULT, která označuje selhání, `AttachProfiler` vrátí stejnou hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ab244-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="ab244-155">V tomto případě je E_NOTIMPL převést na CORPROF_E_PROFILER_NOT_ATTACHABLE.</span><span class="sxs-lookup"><span data-stu-id="ab244-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab244-156">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab244-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="ab244-157">Správa paměti</span><span class="sxs-lookup"><span data-stu-id="ab244-157">Memory Management</span></span>  
 <span data-ttu-id="ab244-158">V souladu s konvencemi COM je volajícím `AttachProfiler` (například kód triggeru vytvořený vývojářem profileru) zodpovědný za přidělení a zrušení přidělení paměti pro data, `pvClientData` na která parametr odkazuje.</span><span class="sxs-lookup"><span data-stu-id="ab244-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="ab244-159">Když CLR spustí `AttachProfiler` volání, vytvoří kopii paměti, která `pvClientData` odkazuje na a přenáší ji do cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="ab244-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="ab244-160">Když CLR uvnitř cílového procesu obdrží svou vlastní kopii `pvClientData` bloku, předá ho do profileru prostřednictvím `InitializeForAttach` metody a pak zruší přidělení kopie `pvClientData` bloku z cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="ab244-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab244-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab244-161">Requirements</span></span>  
 <span data-ttu-id="ab244-162">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab244-162">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab244-163">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ab244-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab244-164">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ab244-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab244-165">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab244-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab244-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab244-166">See also</span></span>

- [<span data-ttu-id="ab244-167">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab244-167">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ab244-168">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab244-168">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ab244-169">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ab244-169">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ab244-170">Profilace</span><span class="sxs-lookup"><span data-stu-id="ab244-170">Profiling</span></span>](index.md)
