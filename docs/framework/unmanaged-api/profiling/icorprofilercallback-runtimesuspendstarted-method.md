---
title: "ICorProfilerCallback::RuntimeSuspendStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc1b229a21b59a842a5bcc47620302711cecdc42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="1b58e-102">ICorProfilerCallback::RuntimeSuspendStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="1b58e-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="1b58e-103">Upozorní profileru, že běhové prostředí se chystá pozastavit všechna vlákna modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1b58e-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b58e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b58e-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b58e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b58e-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="1b58e-106">[v] Hodnota [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) výčet, který označuje důvod pro pozastavení.</span><span class="sxs-lookup"><span data-stu-id="1b58e-106">[in] A value of the [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b58e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b58e-107">Remarks</span></span>  
 <span data-ttu-id="1b58e-108">Všechna vlákna modulu runtime, které jsou v nespravovaném kódu budou moci pokračovat, spuštění, dokud se snaží znovu zadat modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1b58e-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="1b58e-109">V tomto bodě se bude také pozastavuje, dokud nebude obnoví modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1b58e-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="1b58e-110">To platí také pro nové vláken, která zadejte modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1b58e-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="1b58e-111">Všechna vlákna v modulu runtime jsou že buď pozastaveno okamžitě, pokud jsou již v přerušitelné kódu, nebo jsou vyzváni k pozastavení po uplynutí přerušitelné kódu.</span><span class="sxs-lookup"><span data-stu-id="1b58e-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b58e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b58e-112">Requirements</span></span>  
 <span data-ttu-id="1b58e-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b58e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b58e-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1b58e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b58e-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b58e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b58e-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b58e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b58e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b58e-117">See Also</span></span>  
 [<span data-ttu-id="1b58e-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b58e-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="1b58e-119">RuntimeSuspendAborted – metoda</span><span class="sxs-lookup"><span data-stu-id="1b58e-119">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)  
 [<span data-ttu-id="1b58e-120">RuntimeSuspendFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="1b58e-120">RuntimeSuspendFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
