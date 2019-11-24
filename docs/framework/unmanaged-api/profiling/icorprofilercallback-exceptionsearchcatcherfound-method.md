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
ms.openlocfilehash: 080777b656e1c3df1cc4170fe1dff6de6ddb41fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445390"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="36cab-102">ICorProfilerCallback::ExceptionSearchCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="36cab-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="36cab-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span><span class="sxs-lookup"><span data-stu-id="36cab-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36cab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36cab-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36cab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36cab-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="36cab-106">[in] The ID of the function that contains the exception handler.</span><span class="sxs-lookup"><span data-stu-id="36cab-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36cab-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36cab-107">Requirements</span></span>  
 <span data-ttu-id="36cab-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36cab-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36cab-109">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36cab-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36cab-110">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36cab-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36cab-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36cab-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36cab-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36cab-112">See also</span></span>

- [<span data-ttu-id="36cab-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36cab-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
