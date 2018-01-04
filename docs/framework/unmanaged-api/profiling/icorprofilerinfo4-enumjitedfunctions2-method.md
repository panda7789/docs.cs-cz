---
title: "ICorProfilerInfo4::EnumJITedFunctions2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.EnumJITedFunctions2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7dc381848307ea0606f6989d6946c11aa5ef9a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="6711a-102">ICorProfilerInfo4::EnumJITedFunctions2 – metoda</span><span class="sxs-lookup"><span data-stu-id="6711a-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="6711a-103">Vrátí enumerátor pro všechny funkce, které byly dříve kompilována a překompilovat JIT.</span><span class="sxs-lookup"><span data-stu-id="6711a-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="6711a-104">Nahradí tato metoda [icorprofilerinfo3::enumjitedfunctions –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metodu, která není výčet překompilovat JIT ID.</span><span class="sxs-lookup"><span data-stu-id="6711a-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6711a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6711a-105">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6711a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6711a-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="6711a-107">[out] Ukazatel [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerátor.</span><span class="sxs-lookup"><span data-stu-id="6711a-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6711a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6711a-108">Remarks</span></span>  
 <span data-ttu-id="6711a-109">Tato metoda se mohou překrývat s `JITCompilation` zpětná volání, jako [icorprofilercallback::jitcompilationstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="6711a-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="6711a-110">Vrácený výčtu obsahuje hodnoty pro `COR_PRF_FUNCTION::reJitId` pole.</span><span class="sxs-lookup"><span data-stu-id="6711a-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="6711a-111">[Icorprofilerinfo3::enumjitedfunctions –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metodu, která nahradí tato metoda není výčet překompilovat JIT ID, protože `COR_PRF_FUNCTION::reJitId` pole je vždycky nastavený na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="6711a-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="6711a-112">`ICorProfilerInfo4::EnumJITedFunctions` Metoda výčet překompilovat JIT ID, protože `COR_PRF_FUNCTION::reJitId` pole je správně nastaveno.</span><span class="sxs-lookup"><span data-stu-id="6711a-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="6711a-113">Všimněte si, že [icorprofilerinfo4::enumjitedfunctions2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) metoda můžete aktivovat uvolňování paměti, zatímco [icorprofilerinfo3::enumjitedfunctions – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) nikoli.</span><span class="sxs-lookup"><span data-stu-id="6711a-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="6711a-114">Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="6711a-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6711a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6711a-115">Requirements</span></span>  
 <span data-ttu-id="6711a-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6711a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6711a-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6711a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6711a-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6711a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6711a-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6711a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6711a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6711a-120">See Also</span></span>  
 [<span data-ttu-id="6711a-121">EnumJITedFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="6711a-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)  
 [<span data-ttu-id="6711a-122">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6711a-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="6711a-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6711a-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="6711a-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="6711a-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
