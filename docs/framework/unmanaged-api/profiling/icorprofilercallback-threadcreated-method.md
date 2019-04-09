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
ms.openlocfilehash: 5f8eca3e8eb755e31e704e557ae614a6e5c1f534
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107767"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="8ab79-102">ICorProfilerCallback::ThreadCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="8ab79-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="8ab79-103">Oznámí profileru, že vlákno vytvořil.</span><span class="sxs-lookup"><span data-stu-id="8ab79-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ab79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ab79-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="8ab79-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ab79-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="8ab79-106">[in] ID vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="8ab79-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ab79-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ab79-107">Remarks</span></span>  
 <span data-ttu-id="8ab79-108">`threadId` Hodnota je hned platná.</span><span class="sxs-lookup"><span data-stu-id="8ab79-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ab79-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ab79-109">Requirements</span></span>  
 <span data-ttu-id="8ab79-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ab79-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ab79-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8ab79-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ab79-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ab79-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8ab79-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8ab79-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8ab79-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ab79-114">See also</span></span>

- [<span data-ttu-id="8ab79-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ab79-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="8ab79-116">ThreadDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="8ab79-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
