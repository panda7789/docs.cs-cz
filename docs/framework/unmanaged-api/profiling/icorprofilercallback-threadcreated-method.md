---
title: "ICorProfilerCallback::ThreadCreated – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadCreated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b62d5d1129bb71a95ac4e98624558272b08f0683
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="fc31c-102">ICorProfilerCallback::ThreadCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="fc31c-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="fc31c-103">Upozorní profileru vytvořený vlákna.</span><span class="sxs-lookup"><span data-stu-id="fc31c-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc31c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc31c-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc31c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc31c-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="fc31c-106">[v] ID podprocesu, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="fc31c-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc31c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc31c-107">Remarks</span></span>  
 <span data-ttu-id="fc31c-108">`threadId` Hodnota je hned platná.</span><span class="sxs-lookup"><span data-stu-id="fc31c-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc31c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc31c-109">Requirements</span></span>  
 <span data-ttu-id="fc31c-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc31c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc31c-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc31c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc31c-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc31c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc31c-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc31c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc31c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc31c-114">See Also</span></span>  
 [<span data-ttu-id="fc31c-115">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc31c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="fc31c-116">Threaddestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="fc31c-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
