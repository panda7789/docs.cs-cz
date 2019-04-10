---
title: ICorProfilerCallback::RuntimeThreadResumed – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 810875d1b91265fe886ce3cd11970cad7fee122d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228858"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="8be2f-102">ICorProfilerCallback::RuntimeThreadResumed – metoda</span><span class="sxs-lookup"><span data-stu-id="8be2f-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="8be2f-103">Oznámí profileru, že zadaný podproces obnovila po pozastavuje.</span><span class="sxs-lookup"><span data-stu-id="8be2f-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8be2f-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8be2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8be2f-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="8be2f-106">[in] ID podprocesu, který byl obnoven.</span><span class="sxs-lookup"><span data-stu-id="8be2f-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8be2f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8be2f-107">Requirements</span></span>  
 <span data-ttu-id="8be2f-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8be2f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8be2f-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8be2f-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8be2f-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8be2f-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8be2f-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8be2f-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8be2f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8be2f-112">See also</span></span>

- [<span data-ttu-id="8be2f-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8be2f-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="8be2f-114">RuntimeThreadSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="8be2f-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
