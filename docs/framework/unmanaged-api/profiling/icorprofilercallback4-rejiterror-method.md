---
title: "ICorProfilerCallback4::ReJITError – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITError
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8b1f3c5b206b2e6a108e784a206d597b69fd662
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="6fb70-102">ICorProfilerCallback4::ReJITError – metoda</span><span class="sxs-lookup"><span data-stu-id="6fb70-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="6fb70-103">Aby kompilátoru za běhu (JIT) došlo k chybě při procesu rekompilace upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="6fb70-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fb70-104">Syntax</span></span>  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6fb70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fb70-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="6fb70-106">[v] `ModuleID` Ve které byl proveden pokus o rekompilace se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="6fb70-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="6fb70-107">[v] `MethodDef` Metody, na kterém byl proveden pokus o rekompilace se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="6fb70-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="6fb70-108">[v] Instance funkce, která se Rekompilované nebo označený pro opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="6fb70-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="6fb70-109">Tato hodnota může být `NULL` -li k chybě došlo na základě za metoda místo základ pro vytvoření instance (například pokud profileru zadaný token neplatná metadata metodu zopakovat).</span><span class="sxs-lookup"><span data-stu-id="6fb70-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="6fb70-110">[v] HRESULT, která určuje podstatu tohoto selhání.</span><span class="sxs-lookup"><span data-stu-id="6fb70-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="6fb70-111">Najdete v části hodnoty stavu HRESULT seznam hodnot.</span><span class="sxs-lookup"><span data-stu-id="6fb70-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6fb70-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6fb70-112">Return Value</span></span>  
 <span data-ttu-id="6fb70-113">Návratové hodnoty z této zpětné volání se ignorují.</span><span class="sxs-lookup"><span data-stu-id="6fb70-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="6fb70-114">Stav hodnoty HRESULT</span><span class="sxs-lookup"><span data-stu-id="6fb70-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="6fb70-115">Stav pole HRESULT</span><span class="sxs-lookup"><span data-stu-id="6fb70-115">Status array HRESULT</span></span>|<span data-ttu-id="6fb70-116">Popis</span><span class="sxs-lookup"><span data-stu-id="6fb70-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="6fb70-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6fb70-117">E_INVALIDARG</span></span>|<span data-ttu-id="6fb70-118">`moduleID` Nebo `methodDef` token je `NULL`.</span><span class="sxs-lookup"><span data-stu-id="6fb70-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="6fb70-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="6fb70-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="6fb70-120">Modul ještě není úplným načtením nebo je právě odpojení.</span><span class="sxs-lookup"><span data-stu-id="6fb70-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="6fb70-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="6fb70-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="6fb70-122">Zadaný modul dynamicky vygenerovalo (například `Reflection.Emit`) a proto nepodporuje tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="6fb70-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="6fb70-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="6fb70-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="6fb70-124">Metoda vytvoření instance do collectible sestavení a není proto schopna zopakovat.</span><span class="sxs-lookup"><span data-stu-id="6fb70-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="6fb70-125">Všimněte si, že typy a funkcí definovaných v kontextu jiných reflexe (například `List<MyCollectibleStruct>`) se dá vytvořit instance do collectible sestavení.</span><span class="sxs-lookup"><span data-stu-id="6fb70-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="6fb70-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6fb70-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6fb70-127">Modul CLR nedostatku paměti při pokusu označit zadanou metodu pro opětovnou kompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="6fb70-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="6fb70-128">Ostatní</span><span class="sxs-lookup"><span data-stu-id="6fb70-128">Other</span></span>|<span data-ttu-id="6fb70-129">Operační systém vrátil chybu mimo kontrolu modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6fb70-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="6fb70-130">Například pokud selže volání systému změnit ochranu přístupu ke stránce paměti, se zobrazí chyba operačního systému.</span><span class="sxs-lookup"><span data-stu-id="6fb70-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6fb70-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fb70-131">Requirements</span></span>  
 <span data-ttu-id="6fb70-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fb70-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fb70-133">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6fb70-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6fb70-134">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fb70-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fb70-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb70-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb70-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fb70-136">See Also</span></span>  
 [<span data-ttu-id="6fb70-137">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6fb70-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="6fb70-138">Icorprofilercallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6fb70-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
