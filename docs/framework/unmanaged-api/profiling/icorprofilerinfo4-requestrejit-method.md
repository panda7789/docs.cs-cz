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
ms.openlocfilehash: d2f8d538adb965864915fb1195bf9f2b8488aac8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868405"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="f2a86-102">ICorProfilerInfo4::RequestReJIT – metoda</span><span class="sxs-lookup"><span data-stu-id="f2a86-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="f2a86-103">Vyžádá rekompilaci JIT všech instancí zadaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="f2a86-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2a86-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2a86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2a86-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="f2a86-106">pro Počet funkcí, které mají být rekompilovány.</span><span class="sxs-lookup"><span data-stu-id="f2a86-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="f2a86-107">pro Určuje `moduleId` část párů (`module`, `methodDef`), které identifikují funkce, které mají být znovu zkompilovány.</span><span class="sxs-lookup"><span data-stu-id="f2a86-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="f2a86-108">pro Určuje `methodId` část párů (`module`, `methodDef`), které identifikují funkce, které mají být znovu zkompilovány.</span><span class="sxs-lookup"><span data-stu-id="f2a86-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2a86-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f2a86-109">Return Value</span></span>  
 <span data-ttu-id="f2a86-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="f2a86-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f2a86-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2a86-111">HRESULT</span></span>|<span data-ttu-id="f2a86-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f2a86-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2a86-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2a86-113">S_OK</span></span>|<span data-ttu-id="f2a86-114">Byl proveden pokus o označení všech metod pro rekompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="f2a86-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="f2a86-115">Profiler musí implementovat metodu [ICorProfilerCallback4:: rejiterror –](icorprofilercallback4-rejiterror-method.md) k určení, které metody byly úspěšně označeny pro rekompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="f2a86-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="f2a86-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="f2a86-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="f2a86-117">Aby bylo toto volání podporováno, Profiler musí implementovat rozhraní [ICorProfilerCallback4](icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f2a86-117">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="f2a86-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="f2a86-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="f2a86-119">Opětovná kompilace JIT není povolená.</span><span class="sxs-lookup"><span data-stu-id="f2a86-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="f2a86-120">Je nutné povolit rekompilaci JIT během inicializace pomocí metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaku `COR_PRF_ENABLE_REJIT`.</span><span class="sxs-lookup"><span data-stu-id="f2a86-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="f2a86-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f2a86-121">E_INVALIDARG</span></span>|<span data-ttu-id="f2a86-122">`cFunctions` je 0 nebo `moduleIds` nebo `methodIds` `NULL`.</span><span class="sxs-lookup"><span data-stu-id="f2a86-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="f2a86-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f2a86-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f2a86-124">Modul CLR nemohl dokončit požadavek, protože nemá dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="f2a86-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2a86-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2a86-125">Remarks</span></span>  
 <span data-ttu-id="f2a86-126">Zavolejte `RequestReJIT`, aby modul runtime znovu zkompiluje zadanou sadu funkcí.</span><span class="sxs-lookup"><span data-stu-id="f2a86-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="f2a86-127">Profiler kódu pak může použít rozhraní [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) k úpravě kódu, který je generován při rekompilaci funkcí.</span><span class="sxs-lookup"><span data-stu-id="f2a86-127">A code profiler can then use the [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="f2a86-128">Tato akce nemá vliv na aktuálně vykonávané funkce, a to pouze na budoucí vyvolání funkce.</span><span class="sxs-lookup"><span data-stu-id="f2a86-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="f2a86-129">Pokud byla kterákoli z určených funkcí dříve znovu zkompilována za běhu, požadavek na opětovnou kompilaci je stejný jako vrácení a opětovné kompilování funkce.</span><span class="sxs-lookup"><span data-stu-id="f2a86-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="f2a86-130">Chcete-li zachovat reversibility, když kompilátor JIT zkompiluje původní verzi funkce, považuje se za rozhodnutí o vkládání pouze původní verze svých volané.</span><span class="sxs-lookup"><span data-stu-id="f2a86-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="f2a86-131">Když kompilátor JIT znovu zkompiluje funkci, považuje aktuální verze (rekompilováno nebo originál) své volané pro vkládání.</span><span class="sxs-lookup"><span data-stu-id="f2a86-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="f2a86-132">Profiler obvykle volá `RequestReJIT` jako odpověď na uživatelský vstup požadující, že Profiler instrumentuje jednu nebo více metod.</span><span class="sxs-lookup"><span data-stu-id="f2a86-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="f2a86-133">`RequestReJIT` obvykle pozastaví modul runtime za účelem provedení některé z jeho práce a může potenciálně aktivovat uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f2a86-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="f2a86-134">Profiler by měl volat `RequestReJIT` z dříve vytvořeného vlákna a nikoli z vlákna vytvořeného modulem CLR, který aktuálně provádí zpětné volání profileru.</span><span class="sxs-lookup"><span data-stu-id="f2a86-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2a86-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2a86-135">Requirements</span></span>  
 <span data-ttu-id="f2a86-136">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2a86-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2a86-137">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f2a86-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2a86-138">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f2a86-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2a86-139">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2a86-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a86-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2a86-140">See also</span></span>

- [<span data-ttu-id="f2a86-141">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2a86-141">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="f2a86-142">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="f2a86-142">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f2a86-143">Profilace</span><span class="sxs-lookup"><span data-stu-id="f2a86-143">Profiling</span></span>](index.md)
