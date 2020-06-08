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
ms.openlocfilehash: 70c03d34bdf9bd315994b2bfa09631efac2565ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500218"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="074f8-102">ICorProfilerCallback::ExceptionSearchCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="074f8-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="074f8-103">Upozorní profileru, že ve fázi hledání výjimek byla nalezena obslužná rutina pro vyvolanou výjimku.</span><span class="sxs-lookup"><span data-stu-id="074f8-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="074f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="074f8-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="074f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="074f8-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="074f8-106">\[v] ID funkce, která obsahuje obslužnou rutinu výjimky.</span><span class="sxs-lookup"><span data-stu-id="074f8-106">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="074f8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="074f8-107">Requirements</span></span>  
 <span data-ttu-id="074f8-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="074f8-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="074f8-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="074f8-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="074f8-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="074f8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="074f8-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="074f8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="074f8-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="074f8-112">See also</span></span>

- [<span data-ttu-id="074f8-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="074f8-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
