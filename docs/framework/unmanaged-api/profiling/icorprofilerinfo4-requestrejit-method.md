---
title: "ICorProfilerInfo4::RequestReJIT – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.RequestReJIT
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4da57e95813afa1135482bef7cf6ab50ee6365cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="44e4e-102">ICorProfilerInfo4::RequestReJIT – metoda</span><span class="sxs-lookup"><span data-stu-id="44e4e-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="44e4e-103">Požadavky JIT rekompilace všech instancí určených funkcí.</span><span class="sxs-lookup"><span data-stu-id="44e4e-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44e4e-104">Syntax</span></span>  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44e4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44e4e-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="44e4e-106">[v] Počet funkcí její kompilace.</span><span class="sxs-lookup"><span data-stu-id="44e4e-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="44e4e-107">[v] Určuje, `moduleId` část (`module`, `methodDef`) páry, které identifikují funkce zopakovat.</span><span class="sxs-lookup"><span data-stu-id="44e4e-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="44e4e-108">[v] Určuje, `methodId` část (`module`, `methodDef`) páry, které identifikují funkce zopakovat.</span><span class="sxs-lookup"><span data-stu-id="44e4e-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44e4e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="44e4e-109">Return Value</span></span>  
 <span data-ttu-id="44e4e-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="44e4e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="44e4e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44e4e-111">HRESULT</span></span>|<span data-ttu-id="44e4e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="44e4e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44e4e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="44e4e-113">S_OK</span></span>|<span data-ttu-id="44e4e-114">Došlo pokusu o označte všechny metody pro opětovnou kompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="44e4e-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="44e4e-115">Musí implementovat profileru [icorprofilercallback4::rejiterror –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) metoda k určení, které metody byly úspěšně označen pro opětovnou kompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="44e4e-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="44e4e-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="44e4e-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="44e4e-117">Musí implementovat profileru [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní pro toto volání podporovaná.</span><span class="sxs-lookup"><span data-stu-id="44e4e-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="44e4e-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="44e4e-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="44e4e-119">JIT rekompilace nebylo povoleno.</span><span class="sxs-lookup"><span data-stu-id="44e4e-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="44e4e-120">Je nutné povolit JIT rekompilace během inicializace s použitím [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodu a nastavit `COR_PRF_ENABLE_REJIT` příznak.</span><span class="sxs-lookup"><span data-stu-id="44e4e-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="44e4e-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="44e4e-121">E_INVALIDARG</span></span>|<span data-ttu-id="44e4e-122">`cFunctions`0, nebo `moduleIds` nebo `methodIds` je `NULL`.</span><span class="sxs-lookup"><span data-stu-id="44e4e-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="44e4e-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="44e4e-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="44e4e-124">Modul CLR se nepodařilo dokončit požadavek, protože nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="44e4e-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44e4e-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44e4e-125">Remarks</span></span>  
 <span data-ttu-id="44e4e-126">Volání `RequestReJIT` tak, aby měl modul runtime znovu zkompiluje zadaný sady funkcí.</span><span class="sxs-lookup"><span data-stu-id="44e4e-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="44e4e-127">Pak můžete použít kód profileru [icorprofilerfunctioncontrol –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) rozhraní upravit kód, který se vygeneruje, když jsou překompilovat funkce.</span><span class="sxs-lookup"><span data-stu-id="44e4e-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="44e4e-128">Aktuálně prováděné funkce a volání funkce jenom budoucí to nemá vliv.</span><span class="sxs-lookup"><span data-stu-id="44e4e-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="44e4e-129">Pokud některé z určených funkcí byl dříve JIT překompilovat, požadavku opětovnou kompilaci je ekvivalentní návrat a nutnosti rekompilace funkce.</span><span class="sxs-lookup"><span data-stu-id="44e4e-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="44e4e-130">Pokud chcete zachovat vratnost, když kompilátoru za běhu kompiluje původní verze funkce, považuje pouze původní verze jeho volané pro vložené rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="44e4e-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="44e4e-131">Když JIT kompilátoru znovu zkompiluje funkci, považuje aktuální verze (Rekompilované nebo původní) jeho volané pro vložené.</span><span class="sxs-lookup"><span data-stu-id="44e4e-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="44e4e-132">Obvykle volá profileru `RequestReJIT` v reakci na vstup uživatele, vyžaduje, aby instrumentace profileru jedné nebo několika metod.</span><span class="sxs-lookup"><span data-stu-id="44e4e-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="44e4e-133">`RequestReJIT`obvykle pozastaví modul runtime, aby bylo možné provést některé z svou práci a může potenciálně aktivační události kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="44e4e-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="44e4e-134">Jako takový, by měly volat profileru `RequestReJIT` z vlákna ho dříve vytvořili, a z vlákna vytvořené CLR, aktuálně neprovádí profileru zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="44e4e-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44e4e-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44e4e-135">Requirements</span></span>  
 <span data-ttu-id="44e4e-136">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44e4e-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44e4e-137">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="44e4e-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="44e4e-138">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44e4e-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44e4e-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44e4e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e4e-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="44e4e-140">See Also</span></span>  
 [<span data-ttu-id="44e4e-141">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44e4e-141">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="44e4e-142">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="44e4e-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="44e4e-143">Profilace</span><span class="sxs-lookup"><span data-stu-id="44e4e-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
