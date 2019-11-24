---
title: ICorProfilerInfo2::GetThreadStaticAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
ms.openlocfilehash: d44eae4da70418e2d4f398b2bacee1fb53d55b60
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443050"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="82857-102">ICorProfilerInfo2::GetThreadStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="82857-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="82857-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span><span class="sxs-lookup"><span data-stu-id="82857-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82857-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82857-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82857-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82857-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="82857-106">[in] The ID of the class that contains the requested thread-static field.</span><span class="sxs-lookup"><span data-stu-id="82857-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="82857-107">[in] The metadata token for the requested thread-static field.</span><span class="sxs-lookup"><span data-stu-id="82857-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="82857-108">[in] The ID of the thread that is the scope for the requested static field.</span><span class="sxs-lookup"><span data-stu-id="82857-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="82857-109">[out] A pointer to the address of the static field that is within the specified thread.</span><span class="sxs-lookup"><span data-stu-id="82857-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82857-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82857-110">Remarks</span></span>  
 <span data-ttu-id="82857-111">The `GetThreadStaticAddress` method may return one of the following:</span><span class="sxs-lookup"><span data-stu-id="82857-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="82857-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span><span class="sxs-lookup"><span data-stu-id="82857-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="82857-113">The addresses of objects that may be in the garbage collection heap.</span><span class="sxs-lookup"><span data-stu-id="82857-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="82857-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span><span class="sxs-lookup"><span data-stu-id="82857-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="82857-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span><span class="sxs-lookup"><span data-stu-id="82857-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82857-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82857-116">Requirements</span></span>  
 <span data-ttu-id="82857-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82857-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82857-118">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="82857-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82857-119">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82857-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82857-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82857-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82857-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82857-121">See also</span></span>

- [<span data-ttu-id="82857-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82857-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="82857-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82857-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
