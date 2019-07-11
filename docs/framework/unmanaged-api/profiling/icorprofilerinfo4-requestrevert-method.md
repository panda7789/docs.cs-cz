---
title: ICorProfilerInfo4::RequestRevert – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e74cb663f968cc9b1b04a912307e3b4a12e86d4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748660"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="ad3f5-102">ICorProfilerInfo4::RequestRevert – metoda</span><span class="sxs-lookup"><span data-stu-id="ad3f5-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="ad3f5-103">Vrátí všechny výskyty zadaných funkcí na jejich původní verze.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad3f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad3f5-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad3f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad3f5-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="ad3f5-106">[in] Počet funkcí, které chcete vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="ad3f5-107">[in] Určuje `moduleId` část (`module`, `methodDef`) dvojice, které identifikují funkcí, které mají být vráceny zpět.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="ad3f5-108">[in] Určuje `methodId` část (`module`, `methodDef`) dvojice, které identifikují funkcí, které mají být vráceny zpět.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="ad3f5-109">[out] Pole HRESULTs uvedených v části "Stav HRESULTs" dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="ad3f5-110">Každý HRESULT označuje úspěšné nebo neúspěšné pokouší obnovit každá funkce zadané v poli paralelní `moduleIds` a `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad3f5-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ad3f5-111">Return Value</span></span>  
 <span data-ttu-id="ad3f5-112">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ad3f5-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad3f5-113">HRESULT</span></span>|<span data-ttu-id="ad3f5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ad3f5-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad3f5-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad3f5-115">S_OK</span></span>|<span data-ttu-id="ad3f5-116">Vrátit zpět všechny požadavky; byl proveden pokus o však musí být zaškrtnuto pole vrácené stav k určení, které funkce byly úspěšně obnovena.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="ad3f5-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="ad3f5-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="ad3f5-118">Profiler musí implementovat [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní pro toto volání a proto není podporován.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="ad3f5-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="ad3f5-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="ad3f5-120">Rekompilace JIT není povolená.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="ad3f5-121">Musíte povolit rekompilace JIT při inicializaci pomocí [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody nastavte `COR_PRF_ENABLE_REJIT` příznak.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="ad3f5-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ad3f5-122">E_INVALIDARG</span></span>|<span data-ttu-id="ad3f5-123">`cFunctions` je 0, nebo `moduleIds` nebo `methodIds` je `NULL`.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="ad3f5-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ad3f5-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ad3f5-125">Modul CLR nemohl dokončit požadavek, protože mu došla paměť.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="ad3f5-126">HRESULT – stav</span><span class="sxs-lookup"><span data-stu-id="ad3f5-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="ad3f5-127">Stav pole HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad3f5-127">Status array HRESULT</span></span>|<span data-ttu-id="ad3f5-128">Popis</span><span class="sxs-lookup"><span data-stu-id="ad3f5-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="ad3f5-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad3f5-129">S_OK</span></span>|<span data-ttu-id="ad3f5-130">Bylo úspěšně vráceno zpět odpovídající funkce.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="ad3f5-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ad3f5-131">E_INVALIDARG</span></span>|<span data-ttu-id="ad3f5-132">`moduleID` Nebo `methodDef` parametr `NULL`.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="ad3f5-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="ad3f5-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="ad3f5-134">Modul dosud není zcela načteno, nebo je právě uvolňován.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="ad3f5-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="ad3f5-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="ad3f5-136">Zadaný modul se generuje dynamicky (například tím, že `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="ad3f5-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="ad3f5-137">Proto není podporována touto metodou.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="ad3f5-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="ad3f5-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="ad3f5-139">CLR nelze vrátit zadanou funkci, protože nebyl nalezen odpovídající požadavek aktivní opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="ad3f5-140">Nikdy byla vyžádána rekompilace nebo již vrácení funkce.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="ad3f5-141">Ostatní</span><span class="sxs-lookup"><span data-stu-id="ad3f5-141">Other</span></span>|<span data-ttu-id="ad3f5-142">Operační systém vrátil chybu mimo ovládací prvek CLR.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="ad3f5-143">Například pokud selže volání systému ke změně ochrany přístupu k paměti stránky, se zobrazí chyba operačního systému.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad3f5-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad3f5-144">Remarks</span></span>  
 <span data-ttu-id="ad3f5-145">Při příštím všechny instance funkce revereted jsou volány, původní verze funkce se spustí.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="ad3f5-146">Pokud funkce je již spuštěn, dokončí provádění verze, na kterém běží.</span><span class="sxs-lookup"><span data-stu-id="ad3f5-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad3f5-147">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad3f5-147">Requirements</span></span>  
 <span data-ttu-id="ad3f5-148">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad3f5-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad3f5-149">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ad3f5-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ad3f5-150">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad3f5-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad3f5-151">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad3f5-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad3f5-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad3f5-152">See also</span></span>

- [<span data-ttu-id="ad3f5-153">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad3f5-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="ad3f5-154">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ad3f5-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ad3f5-155">Profilace</span><span class="sxs-lookup"><span data-stu-id="ad3f5-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
