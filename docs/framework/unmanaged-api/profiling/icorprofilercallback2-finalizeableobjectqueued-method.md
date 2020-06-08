---
title: ICorProfilerCallback2::FinalizeableObjectQueued – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
ms.openlocfilehash: e2e01c396a67614464e3d4ca50de992388961463
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499817"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="e2e1b-102">ICorProfilerCallback2::FinalizeableObjectQueued – metoda</span><span class="sxs-lookup"><span data-stu-id="e2e1b-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="e2e1b-103">Upozorní profiler kódu, že objekt s finalizační metodou byl zařazen do finalizačního vlákna pro provedení své `Finalize` metody.</span><span class="sxs-lookup"><span data-stu-id="e2e1b-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2e1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2e1b-104">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2e1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2e1b-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="e2e1b-106">pro Hodnota výčtu [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) , která popisuje aspekty finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="e2e1b-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="e2e1b-107">pro ID objektu, který byl zařazen do fronty.</span><span class="sxs-lookup"><span data-stu-id="e2e1b-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2e1b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2e1b-108">Requirements</span></span>  
 <span data-ttu-id="e2e1b-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2e1b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2e1b-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e2e1b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2e1b-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e2e1b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2e1b-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2e1b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e1b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2e1b-113">See also</span></span>

- [<span data-ttu-id="e2e1b-114">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2e1b-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e2e1b-115">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2e1b-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
