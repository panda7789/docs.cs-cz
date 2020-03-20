---
title: ICorProfilerCallback::ThreadCreated – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
ms.openlocfilehash: 7fb58c0eb2446253bd658434fc9d68bb857fe0e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175119"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="3b609-102">ICorProfilerCallback::ThreadCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="3b609-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="3b609-103">Upozorní profiler, že vlákno bylo vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="3b609-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b609-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b609-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="3b609-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b609-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="3b609-106">[v] ID vlákno, které bylo vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="3b609-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b609-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b609-107">Remarks</span></span>  
 <span data-ttu-id="3b609-108">Hodnota `threadId` je okamžitě platná.</span><span class="sxs-lookup"><span data-stu-id="3b609-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b609-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b609-109">Requirements</span></span>  
 <span data-ttu-id="3b609-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b609-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b609-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3b609-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b609-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b609-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b609-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b609-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b609-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b609-114">See also</span></span>

- [<span data-ttu-id="3b609-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b609-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3b609-116">ThreadDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="3b609-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
