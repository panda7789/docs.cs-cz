---
title: "ICorProfilerInfo4::RequestRevert – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.RequestRevert
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f0bf926bc6ba458745231bc17ce20dbe5cdbd1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="41f24-102">ICorProfilerInfo4::RequestRevert – metoda</span><span class="sxs-lookup"><span data-stu-id="41f24-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="41f24-103">Vrátí všechny výskyty určených funkcí jejich původní verze.</span><span class="sxs-lookup"><span data-stu-id="41f24-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41f24-104">Syntax</span></span>  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41f24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41f24-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="41f24-106">[v] Počet funkcí vrátit zpátky.</span><span class="sxs-lookup"><span data-stu-id="41f24-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="41f24-107">[v] Určuje, `moduleId` část (`module`, `methodDef`) páry, které identifikují funkce se vrátí zpátky.</span><span class="sxs-lookup"><span data-stu-id="41f24-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="41f24-108">[v] Určuje, `methodId` část (`module`, `methodDef`) páry, které identifikují funkce se vrátí zpátky.</span><span class="sxs-lookup"><span data-stu-id="41f24-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="41f24-109">[out] Pole hodnoty HRESULT uvedené v části "Hodnoty HRESULT stav" dál v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="41f24-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="41f24-110">Každý HRESULT udává úspěch nebo selhání pokouší obnovit jednotlivé funkce zadané v poli paralelní `moduleIds` a `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="41f24-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41f24-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="41f24-111">Return Value</span></span>  
 <span data-ttu-id="41f24-112">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="41f24-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="41f24-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41f24-113">HRESULT</span></span>|<span data-ttu-id="41f24-114">Popis</span><span class="sxs-lookup"><span data-stu-id="41f24-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41f24-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="41f24-115">S_OK</span></span>|<span data-ttu-id="41f24-116">Došlo pokusu o vrátit zpět všechny požadavky; pole vrácené stav však musí být kontrolované k určení, funkcích, které byly úspěšně vráceny zpět.</span><span class="sxs-lookup"><span data-stu-id="41f24-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="41f24-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="41f24-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="41f24-118">Musí implementovat profileru [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní pro toto volání podporovaná.</span><span class="sxs-lookup"><span data-stu-id="41f24-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="41f24-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="41f24-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="41f24-120">JIT rekompilace nebylo povoleno.</span><span class="sxs-lookup"><span data-stu-id="41f24-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="41f24-121">Je nutné povolit JIT rekompilace během inicializace s použitím [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodu a nastavit `COR_PRF_ENABLE_REJIT` příznak.</span><span class="sxs-lookup"><span data-stu-id="41f24-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="41f24-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="41f24-122">E_INVALIDARG</span></span>|<span data-ttu-id="41f24-123">`cFunctions`0, nebo `moduleIds` nebo `methodIds` je `NULL`.</span><span class="sxs-lookup"><span data-stu-id="41f24-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="41f24-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="41f24-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="41f24-125">Modul CLR se nepodařilo dokončit požadavek, protože nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="41f24-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="41f24-126">Stav hodnoty HRESULT</span><span class="sxs-lookup"><span data-stu-id="41f24-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="41f24-127">Stav pole HRESULT</span><span class="sxs-lookup"><span data-stu-id="41f24-127">Status array HRESULT</span></span>|<span data-ttu-id="41f24-128">Popis</span><span class="sxs-lookup"><span data-stu-id="41f24-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="41f24-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="41f24-129">S_OK</span></span>|<span data-ttu-id="41f24-130">Odpovídající funkce byla úspěšně obnovena.</span><span class="sxs-lookup"><span data-stu-id="41f24-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="41f24-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="41f24-131">E_INVALIDARG</span></span>|<span data-ttu-id="41f24-132">`moduleID` Nebo `methodDef` parametr `NULL`.</span><span class="sxs-lookup"><span data-stu-id="41f24-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="41f24-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="41f24-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="41f24-134">Modul ještě není úplným načtením nebo je právě odpojení.</span><span class="sxs-lookup"><span data-stu-id="41f24-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="41f24-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="41f24-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="41f24-136">Zadaný modul dynamicky vygenerovalo (například podle `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="41f24-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="41f24-137">Proto není podporována touto metodou.</span><span class="sxs-lookup"><span data-stu-id="41f24-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="41f24-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="41f24-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="41f24-139">Modul CLR nelze vrátit zadané funkce, protože nebyl nalezen odpovídající active rekompilace požadavek.</span><span class="sxs-lookup"><span data-stu-id="41f24-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="41f24-140">Buď nikdy obdržel požadavek opětovnou kompilaci nebo funkce, byl již vrácen.</span><span class="sxs-lookup"><span data-stu-id="41f24-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="41f24-141">Ostatní</span><span class="sxs-lookup"><span data-stu-id="41f24-141">Other</span></span>|<span data-ttu-id="41f24-142">Operační systém vrátil chybu mimo kontrolu modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="41f24-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="41f24-143">Například pokud selže volání systému změnit ochranu přístupu ke stránce paměti, se zobrazí chyba operačního systému.</span><span class="sxs-lookup"><span data-stu-id="41f24-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41f24-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41f24-144">Remarks</span></span>  
 <span data-ttu-id="41f24-145">Při příštím žádné instance funkce revereted se nazývají, původní verze funkcí se spustí.</span><span class="sxs-lookup"><span data-stu-id="41f24-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="41f24-146">Pokud funkce je již spuštěna, bude dokončen provádění na verzi, která je spuštěná.</span><span class="sxs-lookup"><span data-stu-id="41f24-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41f24-147">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41f24-147">Requirements</span></span>  
 <span data-ttu-id="41f24-148">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41f24-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41f24-149">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="41f24-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41f24-150">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41f24-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41f24-151">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41f24-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f24-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="41f24-152">See Also</span></span>  
 [<span data-ttu-id="41f24-153">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41f24-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="41f24-154">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="41f24-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="41f24-155">Profilace</span><span class="sxs-lookup"><span data-stu-id="41f24-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
