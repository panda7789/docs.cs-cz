---
title: ICorProfilerInfo4::RequestReJIT – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 20312b80a4882acdaf53d9bcbf95ae2babe0fdca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476700"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="91799-102">ICorProfilerInfo4::RequestReJIT – metoda</span><span class="sxs-lookup"><span data-stu-id="91799-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="91799-103">Požadavků opětovnou kompilaci JIT všechny výskyty zadaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="91799-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91799-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91799-104">Syntax</span></span>  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91799-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91799-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="91799-106">[in] Počet funkcí znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="91799-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="91799-107">[in] Určuje `moduleId` část (`module`, `methodDef`) dvojice, které identifikují funkcí, které mají být překompilovány.</span><span class="sxs-lookup"><span data-stu-id="91799-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="91799-108">[in] Určuje `methodId` část (`module`, `methodDef`) dvojice, které identifikují funkcí, které mají být překompilovány.</span><span class="sxs-lookup"><span data-stu-id="91799-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91799-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="91799-109">Return Value</span></span>  
 <span data-ttu-id="91799-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="91799-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="91799-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91799-111">HRESULT</span></span>|<span data-ttu-id="91799-112">Popis</span><span class="sxs-lookup"><span data-stu-id="91799-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91799-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="91799-113">S_OK</span></span>|<span data-ttu-id="91799-114">Byl proveden pokus o pro označení všech metod rekompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="91799-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="91799-115">Profiler musí implementovat [icorprofilercallback4::rejiterror –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) metodou ke zjištění, které metody byly úspěšně označen pro opětovnou kompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="91799-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="91799-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="91799-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="91799-117">Profiler musí implementovat [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní pro toto volání a proto není podporován.</span><span class="sxs-lookup"><span data-stu-id="91799-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="91799-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="91799-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="91799-119">Rekompilace JIT není povolená.</span><span class="sxs-lookup"><span data-stu-id="91799-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="91799-120">Musíte povolit rekompilace JIT při inicializaci pomocí [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody nastavte `COR_PRF_ENABLE_REJIT` příznak.</span><span class="sxs-lookup"><span data-stu-id="91799-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="91799-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="91799-121">E_INVALIDARG</span></span>|<span data-ttu-id="91799-122">`cFunctions` je 0, nebo `moduleIds` nebo `methodIds` je `NULL`.</span><span class="sxs-lookup"><span data-stu-id="91799-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="91799-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="91799-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="91799-124">Modul CLR nemohl dokončit požadavek, protože mu došla paměť.</span><span class="sxs-lookup"><span data-stu-id="91799-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91799-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91799-125">Remarks</span></span>  
 <span data-ttu-id="91799-126">Volání `RequestReJIT` má modul runtime znovu zkompilovat zadanou sadu funkcí.</span><span class="sxs-lookup"><span data-stu-id="91799-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="91799-127">Profileru kód pak může použít [icorprofilerfunctioncontrol –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) rozhraní a upravte kód, který se vygeneruje, když funkce se překompilují.</span><span class="sxs-lookup"><span data-stu-id="91799-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="91799-128">Toto nastavení neovlivní aktuálně prováděné funkce a volání pouze budoucí funkce.</span><span class="sxs-lookup"><span data-stu-id="91799-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="91799-129">Pokud některý z určené funkce byl dříve překompilován JIT, požaduje Opětovná kompilace je ekvivalentní k vrácení zpět a znovu zkompiluje funkci.</span><span class="sxs-lookup"><span data-stu-id="91799-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="91799-130">Pokud chcete zachovat vratnost, když kompilátor JIT kompilaci původní verzi funkce, považuje pouze původní verze jeho volané pro vkládání rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="91799-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="91799-131">Když kompilátor JIT znovu zkompiluje funkci, považuje za aktuální verze (překompilovanou nebo původní) jeho volané pro vkládání.</span><span class="sxs-lookup"><span data-stu-id="91799-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="91799-132">Profiler volá obvykle `RequestReJIT` v reakci na vstup uživatele požaduje, aby profileru instrumentace jednu nebo více metod.</span><span class="sxs-lookup"><span data-stu-id="91799-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="91799-133">`RequestReJIT` modul runtime, aby bylo možné provést některé své práce a může potenciálně aktivační události uvolňování paměti obvykle pozastaví.</span><span class="sxs-lookup"><span data-stu-id="91799-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="91799-134">V důsledku toho by měly volat profiler `RequestReJIT` z vlákna se dřív vytvořili, a z CLR vytvoří vlákno, které aktuálně nezpracovává zpětného volání profileru.</span><span class="sxs-lookup"><span data-stu-id="91799-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91799-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91799-135">Requirements</span></span>  
 <span data-ttu-id="91799-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91799-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91799-137">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91799-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91799-138">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91799-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91799-139">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91799-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91799-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91799-140">See also</span></span>
- [<span data-ttu-id="91799-141">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91799-141">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="91799-142">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="91799-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="91799-143">Profilace</span><span class="sxs-lookup"><span data-stu-id="91799-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
