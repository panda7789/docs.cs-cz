---
title: ICorProfilerCallback::RuntimeSuspendStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5606a556dd7aeafe6d7a6408d236f2bee8dc773
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168971"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="e1eab-102">ICorProfilerCallback::RuntimeSuspendStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="e1eab-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="e1eab-103">Oznámí profileru, že modul runtime Chystáte se pozastavit všechna vlákna modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e1eab-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1eab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1eab-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1eab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1eab-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="e1eab-106">[in] Hodnota [cor_prf_suspend_reason –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) výčet, který označuje důvod pro pozastavení.</span><span class="sxs-lookup"><span data-stu-id="e1eab-106">[in] A value of the [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1eab-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1eab-107">Remarks</span></span>  
 <span data-ttu-id="e1eab-108">Všechna vlákna modulu runtime, které jsou v nespravovaném kódu se může pokračovat, spuštění, dokud se pokusí znovu zadat modul runtime.</span><span class="sxs-lookup"><span data-stu-id="e1eab-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="e1eab-109">V tomto okamžiku se bude také být pozastaveno, dokud modul runtime bude pokračovat.</span><span class="sxs-lookup"><span data-stu-id="e1eab-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="e1eab-110">To platí i pro nová vlákna, které zadejte modul runtime.</span><span class="sxs-lookup"><span data-stu-id="e1eab-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="e1eab-111">Všechna vlákna v modulu runtime jsou že buď pozastaveno okamžitě, pokud jsou již v paralelní kód, nebo mu zobrazit výzva k pozastavení, když dosáhnou paralelní kód.</span><span class="sxs-lookup"><span data-stu-id="e1eab-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1eab-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1eab-112">Requirements</span></span>  
 <span data-ttu-id="e1eab-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1eab-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1eab-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1eab-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1eab-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1eab-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1eab-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1eab-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1eab-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1eab-117">See also</span></span>

- [<span data-ttu-id="e1eab-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1eab-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e1eab-119">RuntimeSuspendAborted – metoda</span><span class="sxs-lookup"><span data-stu-id="e1eab-119">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="e1eab-120">RuntimeSuspendFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="e1eab-120">RuntimeSuspendFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
