---
title: "ICorProfilerCallback::ExceptionSearchCatcherFound – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fc226b6102c50b118a4b13f9cd25700dd1ca7301
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="24308-102">ICorProfilerCallback::ExceptionSearchCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="24308-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="24308-103">Upozorní profileru, že vyhledávání fáze zpracování výjimky má umístěný obslužnou rutinu pro výjimku, která byla vyvolána.</span><span class="sxs-lookup"><span data-stu-id="24308-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24308-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24308-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24308-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24308-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="24308-106">[v] ID funkce, která obsahuje obslužná rutina výjimky.</span><span class="sxs-lookup"><span data-stu-id="24308-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24308-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24308-107">Requirements</span></span>  
 <span data-ttu-id="24308-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24308-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24308-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24308-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24308-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24308-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24308-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24308-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24308-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="24308-112">See Also</span></span>  
 [<span data-ttu-id="24308-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24308-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
