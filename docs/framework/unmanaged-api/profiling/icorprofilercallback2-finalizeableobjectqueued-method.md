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
ms.openlocfilehash: b9093f920a8c14247bc51471da3682c7e500afa4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865802"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="5cfac-102">ICorProfilerCallback2::FinalizeableObjectQueued – metoda</span><span class="sxs-lookup"><span data-stu-id="5cfac-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="5cfac-103">Upozorňuje profileru kódu, že objekt s finalizační metodou byl zařazen do finalizačního vlákna ke spuštění metody `Finalize`.</span><span class="sxs-lookup"><span data-stu-id="5cfac-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cfac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cfac-104">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cfac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5cfac-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="5cfac-106">pro Hodnota výčtu [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) , která popisuje aspekty finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="5cfac-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="5cfac-107">pro ID objektu, který byl zařazen do fronty.</span><span class="sxs-lookup"><span data-stu-id="5cfac-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cfac-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cfac-108">Requirements</span></span>  
 <span data-ttu-id="5cfac-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cfac-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cfac-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5cfac-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5cfac-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5cfac-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cfac-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cfac-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cfac-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5cfac-113">See also</span></span>

- [<span data-ttu-id="5cfac-114">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5cfac-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5cfac-115">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5cfac-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
