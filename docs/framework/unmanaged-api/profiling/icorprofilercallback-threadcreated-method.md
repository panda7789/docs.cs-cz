---
title: "ICorProfilerCallback::ThreadCreated – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 01062931e64cf8daa698fd99d4e6318a7a8f6a5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="7cad1-102">ICorProfilerCallback::ThreadCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="7cad1-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="7cad1-103">Upozorní profileru vytvořený vlákna.</span><span class="sxs-lookup"><span data-stu-id="7cad1-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cad1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cad1-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="7cad1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cad1-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="7cad1-106">[v] ID podprocesu, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="7cad1-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cad1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7cad1-107">Remarks</span></span>  
 <span data-ttu-id="7cad1-108">`threadId` Hodnota je hned platná.</span><span class="sxs-lookup"><span data-stu-id="7cad1-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cad1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7cad1-109">Requirements</span></span>  
 <span data-ttu-id="7cad1-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cad1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cad1-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7cad1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cad1-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cad1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cad1-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cad1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cad1-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cad1-114">See Also</span></span>  
 [<span data-ttu-id="7cad1-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cad1-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="7cad1-116">ThreadDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="7cad1-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
