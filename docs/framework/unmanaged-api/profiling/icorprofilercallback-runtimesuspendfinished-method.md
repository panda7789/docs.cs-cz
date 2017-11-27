---
title: "ICorProfilerCallback::RuntimeSuspendFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c922ee4f986df22f213820b8aed60ea28a76377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="781a7-102">ICorProfilerCallback::RuntimeSuspendFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="781a7-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="781a7-103">Upozorní profileru, modul runtime byla dokončena pozastavení všechna vlákna modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="781a7-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="781a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="781a7-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="781a7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="781a7-105">Remarks</span></span>  
 <span data-ttu-id="781a7-106">Všechna vlákna modulu runtime, které jsou v nespravovaném kódu budou moci pokračovat, spuštění, dokud se snaží znovu zadat modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="781a7-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="781a7-107">V tomto bodě se bude také pozastavuje, dokud nebude obnoví modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="781a7-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="781a7-108">To platí také pro nové vláken, která zadejte modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="781a7-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="781a7-109">Všechna vlákna v modulu runtime jsou že buď pozastaveno okamžitě, pokud jsou již v přerušitelné kódu, nebo jsou vyzváni k pozastavení po uplynutí přerušitelné kódu.</span><span class="sxs-lookup"><span data-stu-id="781a7-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="781a7-110">`RuntimeSuspendFinished` Zpětného volání záruku, že dojde k ve stejném vlákně, jako [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="781a7-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="781a7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="781a7-111">Requirements</span></span>  
 <span data-ttu-id="781a7-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="781a7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="781a7-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="781a7-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="781a7-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="781a7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="781a7-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="781a7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="781a7-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="781a7-116">See Also</span></span>  
 [<span data-ttu-id="781a7-117">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="781a7-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="781a7-118">Runtimesuspendaborted – metoda</span><span class="sxs-lookup"><span data-stu-id="781a7-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
