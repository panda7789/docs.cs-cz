---
title: ICorProfilerCallback::ExceptionSearchFunctionEnter – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
ms.openlocfilehash: c09d896e59a6c336fbe4923dbe85f30b039d8c36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866400"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="db85e-102">ICorProfilerCallback::ExceptionSearchFunctionEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="db85e-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="db85e-103">Upozorní profileru, že ve fázi hledání výjimek bylo zahájeno hledání funkce pro nalezení obslužné rutiny pro aktuální výjimku.</span><span class="sxs-lookup"><span data-stu-id="db85e-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db85e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db85e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db85e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db85e-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="db85e-106">\[v] ID funkce, která byla zadána.</span><span class="sxs-lookup"><span data-stu-id="db85e-106">\[in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="db85e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db85e-107">Requirements</span></span>  
 <span data-ttu-id="db85e-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db85e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db85e-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="db85e-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="db85e-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="db85e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db85e-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db85e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db85e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db85e-112">See also</span></span>

- [<span data-ttu-id="db85e-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db85e-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="db85e-114">ExceptionSearchFunctionLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="db85e-114">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
