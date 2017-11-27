---
title: "ICorProfilerCallback::RuntimeThreadResumed – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeThreadResumed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b460f87ead93c5f375c758a5547c0ae0be2b5691
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="a6e49-102">ICorProfilerCallback::RuntimeThreadResumed – metoda</span><span class="sxs-lookup"><span data-stu-id="a6e49-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="a6e49-103">Upozorní profileru, že zadaný vlákno obnovil po bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="a6e49-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6e49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6e49-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6e49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6e49-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="a6e49-106">[v] ID podprocesu, který byl obnoven.</span><span class="sxs-lookup"><span data-stu-id="a6e49-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6e49-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6e49-107">Requirements</span></span>  
 <span data-ttu-id="a6e49-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6e49-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6e49-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6e49-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6e49-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6e49-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6e49-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6e49-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e49-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6e49-112">See Also</span></span>  
 [<span data-ttu-id="a6e49-113">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a6e49-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a6e49-114">Runtimethreadsuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="a6e49-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
