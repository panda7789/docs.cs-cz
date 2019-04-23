---
title: ICorProfilerCallback::RuntimeSuspendFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 07e2ebe8afe6002dee6c45f56fa1f11a4083d6bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145597"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="334e1-102">ICorProfilerCallback::RuntimeSuspendFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="334e1-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="334e1-103">Oznámí profileru, že modul runtime dokončil pozastavení všechna vlákna modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="334e1-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="334e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="334e1-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="334e1-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="334e1-105">Remarks</span></span>  
 <span data-ttu-id="334e1-106">Všechna vlákna modulu runtime, které jsou v nespravovaném kódu se může pokračovat, spuštění, dokud se pokusí znovu zadat modul runtime.</span><span class="sxs-lookup"><span data-stu-id="334e1-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="334e1-107">V tomto okamžiku se bude také být pozastaveno, dokud modul runtime bude pokračovat.</span><span class="sxs-lookup"><span data-stu-id="334e1-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="334e1-108">To platí i pro nová vlákna, které zadejte modul runtime.</span><span class="sxs-lookup"><span data-stu-id="334e1-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="334e1-109">Všechna vlákna v modulu runtime jsou že buď pozastaveno okamžitě, pokud jsou již v paralelní kód, nebo mu zobrazit výzva k pozastavení, když dosáhnou paralelní kód.</span><span class="sxs-lookup"><span data-stu-id="334e1-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="334e1-110">`RuntimeSuspendFinished` Zpětného volání je zaručeno, ke kterým dochází ve stejném vlákně jako [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="334e1-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="334e1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="334e1-111">Requirements</span></span>  
 <span data-ttu-id="334e1-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="334e1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="334e1-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="334e1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="334e1-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="334e1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="334e1-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="334e1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="334e1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="334e1-116">See also</span></span>

- [<span data-ttu-id="334e1-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="334e1-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="334e1-118">RuntimeSuspendAborted – metoda</span><span class="sxs-lookup"><span data-stu-id="334e1-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
