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
ms.openlocfilehash: b85a7893cf5271c65bc842bb6ea598c825225376
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495720"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="2c470-102">ICorProfilerInfo4::RequestRevert – metoda</span><span class="sxs-lookup"><span data-stu-id="2c470-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="2c470-103">Vrátí všechny výskyty zadaných funkcí do jejich původních verzí.</span><span class="sxs-lookup"><span data-stu-id="2c470-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c470-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c470-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c470-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c470-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="2c470-106">pro Počet funkcí, které mají být vráceny.</span><span class="sxs-lookup"><span data-stu-id="2c470-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="2c470-107">pro Určuje `moduleId` část `module` párů (, `methodDef` ), které identifikují funkce, které mají být vráceny.</span><span class="sxs-lookup"><span data-stu-id="2c470-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="2c470-108">pro Určuje `methodId` část `module` párů (, `methodDef` ), které identifikují funkce, které mají být vráceny.</span><span class="sxs-lookup"><span data-stu-id="2c470-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="2c470-109">mimo Pole HRESULTs uvedené v části stav HRESULTs dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="2c470-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="2c470-110">Každá hodnota HRESULT indikuje úspěch nebo neúspěch při pokusu o vrácení všech funkcí určených v paralelních polích `moduleIds` a `methodIds` .</span><span class="sxs-lookup"><span data-stu-id="2c470-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c470-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2c470-111">Return Value</span></span>  
 <span data-ttu-id="2c470-112">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="2c470-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2c470-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c470-113">HRESULT</span></span>|<span data-ttu-id="2c470-114">Description</span><span class="sxs-lookup"><span data-stu-id="2c470-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c470-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c470-115">S_OK</span></span>|<span data-ttu-id="2c470-116">Byl proveden pokus o vrácení všech požadavků. aby bylo možné zjistit, které funkce byly úspěšně vráceny, je však nutné zkontrolovat vrácené pole stavu.</span><span class="sxs-lookup"><span data-stu-id="2c470-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="2c470-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="2c470-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="2c470-118">Aby bylo toto volání podporováno, Profiler musí implementovat rozhraní [ICorProfilerCallback4](icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2c470-118">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="2c470-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="2c470-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="2c470-120">Opětovná kompilace JIT není povolená.</span><span class="sxs-lookup"><span data-stu-id="2c470-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="2c470-121">Je nutné povolit opětovnou kompilaci JIT během inicializace pomocí metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení `COR_PRF_ENABLE_REJIT` příznaku.</span><span class="sxs-lookup"><span data-stu-id="2c470-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="2c470-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2c470-122">E_INVALIDARG</span></span>|<span data-ttu-id="2c470-123">`cFunctions`je 0 nebo `moduleIds` nebo `methodIds` `NULL` .</span><span class="sxs-lookup"><span data-stu-id="2c470-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="2c470-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2c470-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2c470-125">Modul CLR nemohl dokončit požadavek, protože nemá dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="2c470-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="2c470-126">Stav HRESULTs</span><span class="sxs-lookup"><span data-stu-id="2c470-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="2c470-127">Stavové pole HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c470-127">Status array HRESULT</span></span>|<span data-ttu-id="2c470-128">Description</span><span class="sxs-lookup"><span data-stu-id="2c470-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="2c470-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c470-129">S_OK</span></span>|<span data-ttu-id="2c470-130">Odpovídající funkce byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2c470-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="2c470-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2c470-131">E_INVALIDARG</span></span>|<span data-ttu-id="2c470-132">`moduleID`Parametr nebo `methodDef` je `NULL` .</span><span class="sxs-lookup"><span data-stu-id="2c470-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="2c470-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="2c470-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="2c470-134">Modul ještě není úplně načtený, nebo se jedná o proces, který se právě načítá.</span><span class="sxs-lookup"><span data-stu-id="2c470-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="2c470-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="2c470-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="2c470-136">Zadaný modul byl dynamicky generován (například podle `Reflection.Emit` ).</span><span class="sxs-lookup"><span data-stu-id="2c470-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="2c470-137">Proto není touto metodou podporována.</span><span class="sxs-lookup"><span data-stu-id="2c470-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="2c470-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="2c470-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="2c470-139">CLR nemůže vrátit zadanou funkci, protože se nenašla odpovídající aktivní požadavek na opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="2c470-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="2c470-140">Buď není požadavek na opětovnou kompilaci, nebo již byla funkce vrácena.</span><span class="sxs-lookup"><span data-stu-id="2c470-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="2c470-141">Ostatní</span><span class="sxs-lookup"><span data-stu-id="2c470-141">Other</span></span>|<span data-ttu-id="2c470-142">Operační systém vrátil selhání mimo ovládací prvek CLR.</span><span class="sxs-lookup"><span data-stu-id="2c470-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="2c470-143">Pokud například systémové volání změny ochrany přístupu stránky paměti selže, zobrazí se Chyba operačního systému.</span><span class="sxs-lookup"><span data-stu-id="2c470-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c470-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c470-144">Remarks</span></span>  
 <span data-ttu-id="2c470-145">Při příštím volání všech instancí funkcí revereted se spustí původní verze funkcí.</span><span class="sxs-lookup"><span data-stu-id="2c470-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="2c470-146">Pokud už je funkce spuštěná, dokončí se spuštění verze, která je spuštěná.</span><span class="sxs-lookup"><span data-stu-id="2c470-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c470-147">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c470-147">Requirements</span></span>  
 <span data-ttu-id="2c470-148">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c470-148">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c470-149">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2c470-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c470-150">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2c470-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c470-151">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c470-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c470-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c470-152">See also</span></span>

- [<span data-ttu-id="2c470-153">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c470-153">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="2c470-154">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2c470-154">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2c470-155">Profilace</span><span class="sxs-lookup"><span data-stu-id="2c470-155">Profiling</span></span>](index.md)
