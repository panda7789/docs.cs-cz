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
ms.openlocfilehash: 8f5997dddf78dd75d482bc45d2ee730b20d9ab16
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866467"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="8194b-102">ICorProfilerCallback::ExceptionSearchCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="8194b-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="8194b-103">Upozorní profileru, že ve fázi hledání výjimek byla nalezena obslužná rutina pro vyvolanou výjimku.</span><span class="sxs-lookup"><span data-stu-id="8194b-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8194b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8194b-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8194b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8194b-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="8194b-106">\[in] ID funkce, která obsahuje obslužnou rutinu výjimky.</span><span class="sxs-lookup"><span data-stu-id="8194b-106">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="8194b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8194b-107">Requirements</span></span>  
 <span data-ttu-id="8194b-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8194b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8194b-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8194b-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8194b-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8194b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8194b-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8194b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8194b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8194b-112">See also</span></span>

- [<span data-ttu-id="8194b-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8194b-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
