---
title: ICorProfilerInfo2::GetContextStaticAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
ms.openlocfilehash: d5d7da343148d5f1c2aa9b2b639b094f8269199b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433199"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="fcea9-102">ICorProfilerInfo2::GetContextStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="fcea9-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="fcea9-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span><span class="sxs-lookup"><span data-stu-id="fcea9-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcea9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcea9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcea9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcea9-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="fcea9-106">[in] The ID of the class that contains the requested context-static field.</span><span class="sxs-lookup"><span data-stu-id="fcea9-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="fcea9-107">[in] The metadata token for the requested context-static field.</span><span class="sxs-lookup"><span data-stu-id="fcea9-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="fcea9-108">[in] The ID of the context that is the scope for the requested context-static field.</span><span class="sxs-lookup"><span data-stu-id="fcea9-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="fcea9-109">[out] A pointer to the address of the static field that is within the specified context.</span><span class="sxs-lookup"><span data-stu-id="fcea9-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcea9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fcea9-110">Remarks</span></span>  
 <span data-ttu-id="fcea9-111">The `GetContextStaticAddress` method may return one of the following:</span><span class="sxs-lookup"><span data-stu-id="fcea9-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="fcea9-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span><span class="sxs-lookup"><span data-stu-id="fcea9-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="fcea9-113">The addresses of objects that may be in the garbage collection heap.</span><span class="sxs-lookup"><span data-stu-id="fcea9-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="fcea9-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span><span class="sxs-lookup"><span data-stu-id="fcea9-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="fcea9-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span><span class="sxs-lookup"><span data-stu-id="fcea9-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcea9-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fcea9-116">Requirements</span></span>  
 <span data-ttu-id="fcea9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcea9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcea9-118">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fcea9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fcea9-119">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcea9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcea9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcea9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcea9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcea9-121">See also</span></span>

- [<span data-ttu-id="fcea9-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fcea9-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="fcea9-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fcea9-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
