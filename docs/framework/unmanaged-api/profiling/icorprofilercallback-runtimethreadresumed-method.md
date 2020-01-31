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
ms.openlocfilehash: 5a9ca2f4587c4881820e1aa3d4134f90ce47d557
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865893"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="38b80-102">ICorProfilerCallback::RuntimeThreadResumed – metoda</span><span class="sxs-lookup"><span data-stu-id="38b80-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="38b80-103">Upozorní profileru, že zadané vlákno bylo po pozastavení obnoveno.</span><span class="sxs-lookup"><span data-stu-id="38b80-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38b80-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38b80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38b80-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="38b80-106">pro ID vlákna, které bylo obnoveno.</span><span class="sxs-lookup"><span data-stu-id="38b80-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38b80-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38b80-107">Requirements</span></span>  
 <span data-ttu-id="38b80-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38b80-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38b80-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="38b80-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38b80-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="38b80-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38b80-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38b80-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38b80-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38b80-112">See also</span></span>

- [<span data-ttu-id="38b80-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38b80-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="38b80-114">RuntimeThreadSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="38b80-114">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
