---
title: "ICorProfilerCallback::RuntimeResumeFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeResumeFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5d923db2d9614a4cf7ebc4f1d910a86fee85a0bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="6e086-102">ICorProfilerCallback::RuntimeResumeFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="6e086-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="6e086-103">Profileru upozorní, že modul runtime obnovil všechna vlákna modulu runtime a vrátila do normálního provozu.</span><span class="sxs-lookup"><span data-stu-id="6e086-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e086-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e086-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6e086-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e086-105">Remarks</span></span>  
 <span data-ttu-id="6e086-106">`RuntimeResumeFinished` Zpětného volání není zaručena proběhnout ve stejném vlákně, jako [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6e086-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="6e086-107">Nicméně je zaručeno proběhnout ve stejném vlákně, jako [icorprofilercallback::runtimeresumestarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6e086-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e086-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e086-108">Requirements</span></span>  
 <span data-ttu-id="6e086-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e086-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e086-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6e086-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e086-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e086-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e086-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e086-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e086-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e086-113">See Also</span></span>  
 [<span data-ttu-id="6e086-114">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e086-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
