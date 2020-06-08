---
title: ICorProfilerCallback::RuntimeThreadResumed – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: d3949189a72583ebb50b67a270694a31f1eb23dc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503208"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="756db-102">ICorProfilerCallback::RuntimeThreadResumed – metoda</span><span class="sxs-lookup"><span data-stu-id="756db-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="756db-103">Upozorní profileru, že zadané vlákno bylo po pozastavení obnoveno.</span><span class="sxs-lookup"><span data-stu-id="756db-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="756db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="756db-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="756db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="756db-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="756db-106">pro ID vlákna, které bylo obnoveno.</span><span class="sxs-lookup"><span data-stu-id="756db-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="756db-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="756db-107">Requirements</span></span>  
 <span data-ttu-id="756db-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="756db-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="756db-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="756db-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="756db-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="756db-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="756db-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="756db-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="756db-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="756db-112">See also</span></span>

- [<span data-ttu-id="756db-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="756db-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="756db-114">RuntimeThreadSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="756db-114">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
