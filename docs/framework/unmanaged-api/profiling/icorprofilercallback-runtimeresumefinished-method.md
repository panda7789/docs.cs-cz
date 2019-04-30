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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c7b3c3ea5e976645c265b34327caa38ef6a28fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914781"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="c1150-102">ICorProfilerCallback::RuntimeResumeFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="c1150-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="c1150-103">Profiler upozorní, že modul runtime obnovila všechna vlákna modulu runtime a se vrátí do normálního provozu.</span><span class="sxs-lookup"><span data-stu-id="c1150-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1150-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1150-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c1150-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1150-105">Remarks</span></span>  
 <span data-ttu-id="c1150-106">`RuntimeResumeFinished` Zpětného volání není zaručeno, ke kterým dochází ve stejném vlákně jako [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="c1150-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="c1150-107">Ale je zaručeno, že ke kterým dochází ve stejném vlákně jako [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="c1150-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1150-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1150-108">Requirements</span></span>  
 <span data-ttu-id="c1150-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1150-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1150-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c1150-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1150-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1150-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1150-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1150-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1150-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1150-113">See also</span></span>

- [<span data-ttu-id="c1150-114">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1150-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
