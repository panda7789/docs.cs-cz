---
title: ICorProfilerInfo4::EnumJITedFunctions2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92bc16091abd3e21ebd226fb13dd47b55b0c9cc4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166826"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="83d0d-102">ICorProfilerInfo4::EnumJITedFunctions2 – metoda</span><span class="sxs-lookup"><span data-stu-id="83d0d-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="83d0d-103">Vrátí enumerátor pro všechny funkce, které byly dříve zkompilován JIT Kompilátorem a překompilován JIT.</span><span class="sxs-lookup"><span data-stu-id="83d0d-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="83d0d-104">Tato metoda nahrazuje [icorprofilerinfo3::enumjitedfunctions –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metodu, která není výčet ID překompilován JIT.</span><span class="sxs-lookup"><span data-stu-id="83d0d-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d0d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83d0d-105">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83d0d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="83d0d-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="83d0d-107">[out] Ukazatel [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerátor.</span><span class="sxs-lookup"><span data-stu-id="83d0d-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83d0d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83d0d-108">Remarks</span></span>  
 <span data-ttu-id="83d0d-109">Tato metoda se mohly překrývat s `JITCompilation` zpětná volání, jako [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="83d0d-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="83d0d-110">Vrácené výčet obsahuje hodnoty `COR_PRF_FUNCTION::reJitId` pole.</span><span class="sxs-lookup"><span data-stu-id="83d0d-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="83d0d-111">[Icorprofilerinfo3::enumjitedfunctions –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metodu, která nahradí tato metoda neprovede výčet překompilován JIT ID, protože `COR_PRF_FUNCTION::reJitId` pole je vždycky nastavený na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="83d0d-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="83d0d-112">`ICorProfilerInfo4::EnumJITedFunctions` Metoda výčet překompilován JIT ID, protože `COR_PRF_FUNCTION::reJitId` pole nastavena správně.</span><span class="sxs-lookup"><span data-stu-id="83d0d-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="83d0d-113">Všimněte si, že [icorprofilerinfo4::enumjitedfunctions2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) metoda můžete aktivovat kolekce uvolnění paměti, že [icorprofilerinfo3::enumjitedfunctions – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) se tak nestane.</span><span class="sxs-lookup"><span data-stu-id="83d0d-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="83d0d-114">Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="83d0d-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83d0d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83d0d-115">Requirements</span></span>  
 <span data-ttu-id="83d0d-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83d0d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83d0d-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83d0d-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83d0d-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83d0d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83d0d-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83d0d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d0d-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83d0d-120">See also</span></span>

- [<span data-ttu-id="83d0d-121">EnumJITedFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="83d0d-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="83d0d-122">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83d0d-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="83d0d-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="83d0d-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="83d0d-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="83d0d-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
