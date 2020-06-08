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
ms.openlocfilehash: 244227aadb50720514f7511be563089d520b4bf5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500192"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="d26cf-102">ICorProfilerCallback::ExceptionSearchFunctionEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="d26cf-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="d26cf-103">Upozorní profileru, že ve fázi hledání výjimek bylo zahájeno hledání funkce pro nalezení obslužné rutiny pro aktuální výjimku.</span><span class="sxs-lookup"><span data-stu-id="d26cf-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d26cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d26cf-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d26cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d26cf-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="d26cf-106">\[in] ID funkce, která byla zadána.</span><span class="sxs-lookup"><span data-stu-id="d26cf-106">\[in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="d26cf-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d26cf-107">Requirements</span></span>  
 <span data-ttu-id="d26cf-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d26cf-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d26cf-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d26cf-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d26cf-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d26cf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d26cf-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d26cf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d26cf-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d26cf-112">See also</span></span>

- [<span data-ttu-id="d26cf-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d26cf-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d26cf-114">ExceptionSearchFunctionLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="d26cf-114">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
