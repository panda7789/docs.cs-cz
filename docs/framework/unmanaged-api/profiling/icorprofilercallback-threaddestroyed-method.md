---
title: ICorProfilerCallback::ThreadDestroyed – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09c2aef9cc27a2e9aba34f36c1fbfd0973d3b0fa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474225"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="88f11-102">ICorProfilerCallback::ThreadDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="88f11-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="88f11-103">Oznámí profileru, že došlo ke zničení vlákno.</span><span class="sxs-lookup"><span data-stu-id="88f11-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88f11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88f11-104">Syntax</span></span>  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88f11-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88f11-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="88f11-106">[in] ID vlákna, která byla zničena.</span><span class="sxs-lookup"><span data-stu-id="88f11-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88f11-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88f11-107">Remarks</span></span>  
 <span data-ttu-id="88f11-108">`threadId` Již není platný v okamžiku tohoto volání.</span><span class="sxs-lookup"><span data-stu-id="88f11-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88f11-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88f11-109">Requirements</span></span>  
 <span data-ttu-id="88f11-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88f11-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88f11-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="88f11-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="88f11-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88f11-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88f11-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88f11-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f11-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88f11-114">See also</span></span>
- [<span data-ttu-id="88f11-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88f11-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="88f11-116">ThreadCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="88f11-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
