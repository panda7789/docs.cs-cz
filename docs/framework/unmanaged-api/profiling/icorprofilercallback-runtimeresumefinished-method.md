---
title: ICorProfilerCallback::RuntimeResumeFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
ms.openlocfilehash: 5cafbca75992a5fe8a7d3d95628e0018f1a2e8fa
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865945"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="0b5d9-102">ICorProfilerCallback::RuntimeResumeFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="0b5d9-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="0b5d9-103">Upozorní profileru, že modul runtime obnovil všechna běhová vlákna a vrátil se do normálního provozu.</span><span class="sxs-lookup"><span data-stu-id="0b5d9-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b5d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b5d9-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0b5d9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b5d9-105">Remarks</span></span>  
 <span data-ttu-id="0b5d9-106">`RuntimeResumeFinished` zpětné volání není zaručeno, že by mělo být ve stejném vlákně jako zpětné volání [ICorProfilerCallback:: runtimesuspendstarted –](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0b5d9-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="0b5d9-107">Je však zaručeno, že dojde ve stejném vlákně jako zpětné volání [ICorProfilerCallback:: RuntimeResumeStarted –](icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0b5d9-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b5d9-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b5d9-108">Requirements</span></span>  
 <span data-ttu-id="0b5d9-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b5d9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b5d9-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0b5d9-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0b5d9-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0b5d9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b5d9-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b5d9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5d9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b5d9-113">See also</span></span>

- [<span data-ttu-id="0b5d9-114">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b5d9-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
