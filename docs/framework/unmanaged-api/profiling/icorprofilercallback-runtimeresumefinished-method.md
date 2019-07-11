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
ms.openlocfilehash: 883e226042225b63097acf731b13abd69cc757ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750416"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="01a68-102">ICorProfilerCallback::RuntimeResumeFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="01a68-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="01a68-103">Profiler upozorní, že modul runtime obnovila všechna vlákna modulu runtime a se vrátí do normálního provozu.</span><span class="sxs-lookup"><span data-stu-id="01a68-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01a68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01a68-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="01a68-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01a68-105">Remarks</span></span>  
 <span data-ttu-id="01a68-106">`RuntimeResumeFinished` Zpětného volání není zaručeno, ke kterým dochází ve stejném vlákně jako [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="01a68-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="01a68-107">Ale je zaručeno, že ke kterým dochází ve stejném vlákně jako [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="01a68-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01a68-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01a68-108">Requirements</span></span>  
 <span data-ttu-id="01a68-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01a68-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01a68-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01a68-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01a68-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01a68-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01a68-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01a68-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a68-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01a68-113">See also</span></span>

- [<span data-ttu-id="01a68-114">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01a68-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
