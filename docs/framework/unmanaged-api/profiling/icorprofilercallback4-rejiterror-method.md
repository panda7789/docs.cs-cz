---
title: ICorProfilerCallback4::ReJITError – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: 6ea9dee6e83870d1f2e0fdccffa53f16e6f18dba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430104"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="16f90-102">ICorProfilerCallback4::ReJITError – metoda</span><span class="sxs-lookup"><span data-stu-id="16f90-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="16f90-103">Upozorní profileru, že kompilátor JIT (just-in-time) zjistil chybu v procesu opětovné kompilace.</span><span class="sxs-lookup"><span data-stu-id="16f90-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16f90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16f90-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16f90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16f90-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="16f90-106">pro `ModuleID`, ve kterém byl proveden pokus o opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="16f90-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="16f90-107">pro `MethodDef` metody, na které se provedl pokus o opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="16f90-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="16f90-108">pro Instance funkce, která je rekompilována nebo označena pro rekompilaci.</span><span class="sxs-lookup"><span data-stu-id="16f90-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="16f90-109">Tato hodnota může být `NULL`, pokud k selhání došlo na základě jednotlivých metod (například v případě, že Profiler zadal neplatný token metadat pro metodu, která má být zkompilován).</span><span class="sxs-lookup"><span data-stu-id="16f90-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="16f90-110">pro HRESULT, který označuje povahu selhání.</span><span class="sxs-lookup"><span data-stu-id="16f90-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="16f90-111">Seznam hodnot naleznete v části stav HRESULTs.</span><span class="sxs-lookup"><span data-stu-id="16f90-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16f90-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="16f90-112">Return Value</span></span>  
 <span data-ttu-id="16f90-113">Návratové hodnoty z tohoto zpětného volání jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="16f90-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="16f90-114">Stav HRESULTs</span><span class="sxs-lookup"><span data-stu-id="16f90-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="16f90-115">Stavové pole HRESULT</span><span class="sxs-lookup"><span data-stu-id="16f90-115">Status array HRESULT</span></span>|<span data-ttu-id="16f90-116">Popis</span><span class="sxs-lookup"><span data-stu-id="16f90-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="16f90-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="16f90-117">E_INVALIDARG</span></span>|<span data-ttu-id="16f90-118">Token `moduleID` nebo `methodDef` je `NULL`.</span><span class="sxs-lookup"><span data-stu-id="16f90-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="16f90-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="16f90-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="16f90-120">Modul ještě není úplně načtený, nebo se jedná o proces, který se právě načítá.</span><span class="sxs-lookup"><span data-stu-id="16f90-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="16f90-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="16f90-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="16f90-122">Zadaný modul byl dynamicky generován (například `Reflection.Emit`), a proto není touto metodou podporován.</span><span class="sxs-lookup"><span data-stu-id="16f90-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="16f90-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="16f90-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="16f90-124">Metoda je vytvořena do kolekční sestavení, a proto nemůže být znovu zkompilována.</span><span class="sxs-lookup"><span data-stu-id="16f90-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="16f90-125">Všimněte si, že typy a funkce definované v kontextu bez reflexe (například `List<MyCollectibleStruct>`) mohou být vytvořeny do sestavení kolekční.</span><span class="sxs-lookup"><span data-stu-id="16f90-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="16f90-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="16f90-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="16f90-127">Při pokusu o označení zadané metody pro rekompilaci JIT došlo k nedostatku paměti CLR.</span><span class="sxs-lookup"><span data-stu-id="16f90-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="16f90-128">Další</span><span class="sxs-lookup"><span data-stu-id="16f90-128">Other</span></span>|<span data-ttu-id="16f90-129">Operační systém vrátil selhání mimo ovládací prvek CLR.</span><span class="sxs-lookup"><span data-stu-id="16f90-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="16f90-130">Například pokud systémové volání změny ochrany přístupu stránky paměti dojde k chybě, zobrazí se Chyba operačního systému.</span><span class="sxs-lookup"><span data-stu-id="16f90-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16f90-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16f90-131">Requirements</span></span>  
 <span data-ttu-id="16f90-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16f90-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16f90-133">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="16f90-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="16f90-134">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="16f90-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16f90-135">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16f90-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16f90-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16f90-136">See also</span></span>

- [<span data-ttu-id="16f90-137">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16f90-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="16f90-138">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16f90-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
