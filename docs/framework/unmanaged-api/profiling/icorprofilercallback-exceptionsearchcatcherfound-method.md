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
ms.openlocfilehash: a4dc6b66aff34bae869737591040e5fc1e552834
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499664"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="8fc90-102">ICorProfilerCallback::ExceptionSearchCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="8fc90-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="8fc90-103">Oznámí profileru, že hledání fáze zpracování výjimek pružný obslužnou rutinu, která byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8fc90-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fc90-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fc90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fc90-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8fc90-106">[in] ID funkce, která obsahuje obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="8fc90-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc90-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fc90-107">Requirements</span></span>  
 <span data-ttu-id="8fc90-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fc90-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc90-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8fc90-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8fc90-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fc90-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fc90-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fc90-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc90-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fc90-112">See also</span></span>
- [<span data-ttu-id="8fc90-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fc90-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
