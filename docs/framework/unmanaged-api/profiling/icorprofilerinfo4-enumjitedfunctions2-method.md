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
ms.openlocfilehash: 2c4a89d5f96ef572518f25bf58a0005454f8e3f0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496123"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="11eba-102">ICorProfilerInfo4::EnumJITedFunctions2 – metoda</span><span class="sxs-lookup"><span data-stu-id="11eba-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="11eba-103">Vrátí enumerátor pro všechny funkce, které byly dříve kompilovány JIT a rekompilovány JIT.</span><span class="sxs-lookup"><span data-stu-id="11eba-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="11eba-104">Tato metoda nahrazuje metodu [ICorProfilerInfo3:: EnumJITedFunctions –](icorprofilerinfo3-enumjitedfunctions-method.md) , která neprovádí výčet znovu kompilovaných ID JIT.</span><span class="sxs-lookup"><span data-stu-id="11eba-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11eba-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11eba-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11eba-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="11eba-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="11eba-107">mimo Ukazatel na enumerátor [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="11eba-107">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11eba-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11eba-108">Remarks</span></span>  
 <span data-ttu-id="11eba-109">Tato metoda se může překrývat s `JITCompilation` zpětnými voláními, jako je například metoda [ICorProfilerCallback:: JITCompilationStarted –](icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="11eba-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="11eba-110">Vrácený výčet obsahuje hodnoty pro `COR_PRF_FUNCTION::reJitId` pole.</span><span class="sxs-lookup"><span data-stu-id="11eba-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="11eba-111">Metoda [ICorProfilerInfo3:: EnumJITedFunctions –](icorprofilerinfo3-enumjitedfunctions-method.md) , kterou tato metoda nahrazuje, nevytváří výčet ID rekompilovaných JIT JIT, protože `COR_PRF_FUNCTION::reJitId` pole je vždy nastaveno na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="11eba-111">The [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="11eba-112">`ICorProfilerInfo4::EnumJITedFunctions`Metoda provede výčet rekompilovaných identifikátorů JIT, protože `COR_PRF_FUNCTION::reJitId` pole je nastaveno správně.</span><span class="sxs-lookup"><span data-stu-id="11eba-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="11eba-113">Všimněte si, že metoda [ICorProfilerInfo4:: EnumJITedFunctions2 –](icorprofilerinfo4-enumjitedfunctions2-method.md) může aktivovat uvolňování paměti, zatímco [Metoda ICorProfilerInfo3:: EnumJITedFunctions –](icorprofilerinfo3-enumjitedfunctions-method.md) nebude.</span><span class="sxs-lookup"><span data-stu-id="11eba-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="11eba-114">Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="11eba-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11eba-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11eba-115">Requirements</span></span>  
 <span data-ttu-id="11eba-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11eba-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11eba-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="11eba-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11eba-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="11eba-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11eba-119">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11eba-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11eba-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11eba-120">See also</span></span>

- [<span data-ttu-id="11eba-121">EnumJITedFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="11eba-121">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="11eba-122">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11eba-122">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="11eba-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="11eba-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="11eba-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="11eba-124">Profiling</span></span>](index.md)
