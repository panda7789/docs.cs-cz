---
title: ICorProfilerCallback::ExceptionSearchCatcherFound – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e41378b314b91f42fca9d1039d3011b5eaafe502
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598350"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="fcf92-102">ICorProfilerCallback::ExceptionSearchCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="fcf92-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="fcf92-103">Oznámí profileru, že hledání fáze zpracování výjimek pružný obslužnou rutinu, která byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="fcf92-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcf92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcf92-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcf92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcf92-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="fcf92-106">[in] ID funkce, která obsahuje obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="fcf92-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcf92-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fcf92-107">Requirements</span></span>  
 <span data-ttu-id="fcf92-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcf92-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcf92-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fcf92-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fcf92-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcf92-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcf92-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcf92-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf92-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcf92-112">See also</span></span>

- [<span data-ttu-id="fcf92-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fcf92-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
