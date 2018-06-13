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
ms.openlocfilehash: f6b983db7da258fb94f941d01914ece0f7b1359f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453304"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="47430-102">ICorProfilerCallback::RuntimeResumeFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="47430-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="47430-103">Profileru upozorní, že modul runtime obnovil všechna vlákna modulu runtime a vrátila do normálního provozu.</span><span class="sxs-lookup"><span data-stu-id="47430-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47430-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47430-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="47430-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47430-105">Remarks</span></span>  
 <span data-ttu-id="47430-106">`RuntimeResumeFinished` Zpětného volání není zaručena proběhnout ve stejném vlákně, jako [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="47430-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="47430-107">Nicméně je zaručeno proběhnout ve stejném vlákně, jako [icorprofilercallback::runtimeresumestarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="47430-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47430-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47430-108">Requirements</span></span>  
 <span data-ttu-id="47430-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47430-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47430-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="47430-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="47430-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47430-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47430-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47430-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47430-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="47430-113">See Also</span></span>  
 [<span data-ttu-id="47430-114">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47430-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
