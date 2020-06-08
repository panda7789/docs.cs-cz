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
ms.openlocfilehash: 8bc97bb0d36a046353587a95aa2b79eff12866e0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499880"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="21b19-102">ICorProfilerCallback::RuntimeResumeFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="21b19-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="21b19-103">Upozorní profileru, že modul runtime obnovil všechna běhová vlákna a vrátil se do normálního provozu.</span><span class="sxs-lookup"><span data-stu-id="21b19-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21b19-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="21b19-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21b19-105">Remarks</span></span>  
 <span data-ttu-id="21b19-106">`RuntimeResumeFinished`Zpětné volání není zaručeno ke stejnému vláknu jako zpětné volání [ICorProfilerCallback:: runtimesuspendstarted –](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="21b19-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="21b19-107">Je však zaručeno, že dojde ve stejném vlákně jako zpětné volání [ICorProfilerCallback:: RuntimeResumeStarted –](icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="21b19-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21b19-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21b19-108">Requirements</span></span>  
 <span data-ttu-id="21b19-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21b19-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21b19-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="21b19-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21b19-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="21b19-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21b19-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21b19-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b19-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21b19-113">See also</span></span>

- [<span data-ttu-id="21b19-114">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21b19-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
