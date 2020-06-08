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
ms.openlocfilehash: 25a4b101388bfc0151ba7c9c52da6561d48f806b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503156"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="74bff-102">ICorProfilerCallback::ThreadCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="74bff-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="74bff-103">Upozorní profileru, že bylo vytvořeno vlákno.</span><span class="sxs-lookup"><span data-stu-id="74bff-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74bff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74bff-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="74bff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74bff-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="74bff-106">pro ID vlákna, které bylo vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="74bff-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74bff-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74bff-107">Remarks</span></span>  
 <span data-ttu-id="74bff-108">`threadId`Hodnota je okamžitě platná.</span><span class="sxs-lookup"><span data-stu-id="74bff-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74bff-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74bff-109">Requirements</span></span>  
 <span data-ttu-id="74bff-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74bff-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74bff-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="74bff-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74bff-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="74bff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74bff-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74bff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74bff-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74bff-114">See also</span></span>

- [<span data-ttu-id="74bff-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74bff-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="74bff-116">ThreadDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="74bff-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
