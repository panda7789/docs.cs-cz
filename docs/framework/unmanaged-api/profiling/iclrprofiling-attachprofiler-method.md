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
ms.openlocfilehash: 25c208c98802be540bde7532c53798e6f7b35446
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445948"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="7358c-102">ICLRProfiling::AttachProfiler – metoda</span><span class="sxs-lookup"><span data-stu-id="7358c-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="7358c-103">Připojí zadaný profiler k zadanému procesu.</span><span class="sxs-lookup"><span data-stu-id="7358c-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7358c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7358c-104">Syntax</span></span>  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="7358c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7358c-105">Parameters</span></span>  
 `dwProfileeProcessID`  
 <span data-ttu-id="7358c-106">pro ID procesu procesu, ke kterému má být profiler připojen.</span><span class="sxs-lookup"><span data-stu-id="7358c-106">[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="7358c-107">Na 64ovém počítači musí bitová verze procesu profilace odpovídat bitová verze procesu triggeru, který volá `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="7358c-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="7358c-108">Pokud uživatelský účet, pod kterým je `AttachProfiler` volána, má oprávnění správce, cílový proces může být jakýkoli proces v systému.</span><span class="sxs-lookup"><span data-stu-id="7358c-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="7358c-109">Jinak cílový proces musí být vlastněn stejným uživatelským účtem.</span><span class="sxs-lookup"><span data-stu-id="7358c-109">Otherwise, the target process must be owned by the same user account.</span></span>  
  
 `dwMillisecondsMax`  
 <span data-ttu-id="7358c-110">pro Doba, po kterou se `AttachProfiler` dokončí v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="7358c-110">[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="7358c-111">Proces triggeru by měl projít časovým limitem, který by měl být dostatečný pro konkrétní profiler k dokončení inicializace.</span><span class="sxs-lookup"><span data-stu-id="7358c-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>  
  
 `pClsidProfiler`  
 <span data-ttu-id="7358c-112">pro Ukazatel na identifikátor CLSID profileru, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="7358c-112">[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="7358c-113">Proces triggeru může tuto paměť znovu použít po vrácení `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="7358c-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>  
  
 `wszProfilerPath`  
 <span data-ttu-id="7358c-114">pro Úplná cesta k souboru DLL profileru, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="7358c-114">[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="7358c-115">Řetězec nesmí obsahovat více než 260 znaků, včetně ukončovacího znaku null.</span><span class="sxs-lookup"><span data-stu-id="7358c-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="7358c-116">Pokud je `wszProfilerPath` null nebo prázdný řetězec, modul CLR (Common Language Runtime) se pokusí najít umístění souboru DLL profileru hledáním v registru pro identifikátor CLSID, na který `pClsidProfiler` odkazuje.</span><span class="sxs-lookup"><span data-stu-id="7358c-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="7358c-117">pro Ukazatel na data, která mají být předána do profileru metodou [ICorProfilerCallback3:: InitializeForAttach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7358c-117">[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="7358c-118">Proces triggeru může tuto paměť znovu použít po vrácení `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="7358c-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="7358c-119">Pokud je `pvClientData` null, `cbClientData` musí mít hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="7358c-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="7358c-120">pro Velikost dat, která `pvClientData` odkazuje, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="7358c-120">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7358c-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7358c-121">Return Value</span></span>  
 <span data-ttu-id="7358c-122">Tato metoda vrací následující hodnoty HRESULT.</span><span class="sxs-lookup"><span data-stu-id="7358c-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="7358c-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7358c-123">HRESULT</span></span>|<span data-ttu-id="7358c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="7358c-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7358c-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="7358c-125">S_OK</span></span>|<span data-ttu-id="7358c-126">Zadaný Profiler byl úspěšně připojen k cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="7358c-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="7358c-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="7358c-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="7358c-128">Profiler je již aktivní nebo se k cílovému procesu připojuje.</span><span class="sxs-lookup"><span data-stu-id="7358c-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="7358c-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="7358c-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="7358c-130">Zadaný Profiler nepodporuje přílohu.</span><span class="sxs-lookup"><span data-stu-id="7358c-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="7358c-131">Aktivační proces se může pokusit připojit k jinému profileru.</span><span class="sxs-lookup"><span data-stu-id="7358c-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="7358c-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="7358c-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="7358c-133">Nelze vyžádat přílohu profileru, protože verze cílového procesu není kompatibilní s aktuálním procesem, který volá `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="7358c-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="7358c-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="7358c-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="7358c-135">Uživatel procesu triggeru nemá přístup k cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="7358c-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="7358c-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="7358c-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="7358c-137">Uživatel procesu triggeru nemá oprávnění potřebná k připojení profileru k danému cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="7358c-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="7358c-138">Protokol událostí aplikace může obsahovat více informací.</span><span class="sxs-lookup"><span data-stu-id="7358c-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="7358c-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="7358c-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="7358c-140">Při komunikaci s cílovým procesem došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="7358c-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="7358c-141">K tomu obvykle dochází v případě, že se cílový proces vypíná.</span><span class="sxs-lookup"><span data-stu-id="7358c-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="7358c-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="7358c-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="7358c-143">Cílový proces neexistuje nebo není spuštěn modul CLR, který podporuje přílohu.</span><span class="sxs-lookup"><span data-stu-id="7358c-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="7358c-144">To může znamenat, že modul CLR byl uvolněn od volání metody výčtu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7358c-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="7358c-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="7358c-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="7358c-146">Vypršel časový limit bez začátku načítání profileru.</span><span class="sxs-lookup"><span data-stu-id="7358c-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="7358c-147">Operaci připojení můžete opakovat.</span><span class="sxs-lookup"><span data-stu-id="7358c-147">You can retry the attach operation.</span></span> <span data-ttu-id="7358c-148">K vypršení časového limitu dojde, když finalizační metoda v cílovém procesu běží delší dobu než hodnota časového limitu.</span><span class="sxs-lookup"><span data-stu-id="7358c-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="7358c-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7358c-149">E_INVALIDARG</span></span>|<span data-ttu-id="7358c-150">Jeden nebo více parametrů má neplatné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7358c-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="7358c-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7358c-151">E_FAIL</span></span>|<span data-ttu-id="7358c-152">V některých případech došlo k nespecifikovanému selhání.</span><span class="sxs-lookup"><span data-stu-id="7358c-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="7358c-153">Další kódy chyb</span><span class="sxs-lookup"><span data-stu-id="7358c-153">Other error codes</span></span>|<span data-ttu-id="7358c-154">Pokud metoda [ICorProfilerCallback3:: InitializeForAttach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) profileru vrátí hodnotu HRESULT, která indikuje chybu, `AttachProfiler` vrátí stejnou hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="7358c-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="7358c-155">V tomto případě je E_NOTIMPL převést na CORPROF_E_PROFILER_NOT_ATTACHABLE.</span><span class="sxs-lookup"><span data-stu-id="7358c-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7358c-156">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7358c-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="7358c-157">Správa paměti</span><span class="sxs-lookup"><span data-stu-id="7358c-157">Memory Management</span></span>  
 <span data-ttu-id="7358c-158">V souladu s konvencemi COM je volajícím `AttachProfiler` (například aktivační kód vytvořený vývojářem profileru) zodpovědný za přidělení a zrušení přidělení paměti pro data, na která parametr `pvClientData` odkazuje.</span><span class="sxs-lookup"><span data-stu-id="7358c-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="7358c-159">Když CLR spustí `AttachProfiler` volání, vytvoří kopii paměti, na kterou `pvClientData` odkazuje, a přenáší ji do cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="7358c-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="7358c-160">Když CLR uvnitř cílového procesu obdrží svou vlastní kopii `pvClientData` bloku, předá blok do profileru prostřednictvím metody `InitializeForAttach` a poté zruší přidělení kopie `pvClientData` bloku z cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="7358c-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7358c-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7358c-161">Requirements</span></span>  
 <span data-ttu-id="7358c-162">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7358c-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7358c-163">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7358c-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7358c-164">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7358c-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7358c-165">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7358c-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7358c-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7358c-166">See also</span></span>

- [<span data-ttu-id="7358c-167">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7358c-167">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7358c-168">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7358c-168">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="7358c-169">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7358c-169">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="7358c-170">Profilace</span><span class="sxs-lookup"><span data-stu-id="7358c-170">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
