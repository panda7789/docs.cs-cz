---
title: ICorProfilerCallback::ThreadCreated – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42be5fdef22f5cbffb3dc933bad84987d4a576a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451818"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="e4cc2-102">ICorProfilerCallback::ThreadCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="e4cc2-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="e4cc2-103">Upozorní profileru vytvořený vlákna.</span><span class="sxs-lookup"><span data-stu-id="e4cc2-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4cc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4cc2-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4cc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4cc2-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="e4cc2-106">[v] ID podprocesu, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="e4cc2-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4cc2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4cc2-107">Remarks</span></span>  
 <span data-ttu-id="e4cc2-108">`threadId` Hodnota je hned platná.</span><span class="sxs-lookup"><span data-stu-id="e4cc2-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4cc2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4cc2-109">Requirements</span></span>  
 <span data-ttu-id="e4cc2-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4cc2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4cc2-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4cc2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4cc2-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4cc2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4cc2-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4cc2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4cc2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4cc2-114">See Also</span></span>  
 [<span data-ttu-id="e4cc2-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4cc2-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="e4cc2-116">ThreadDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="e4cc2-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
