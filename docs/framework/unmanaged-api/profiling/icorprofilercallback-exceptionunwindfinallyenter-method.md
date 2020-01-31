---
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
ms.openlocfilehash: ab7c8cbc41967af04c4c9a8813f32b9b1f01c6a1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866348"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="3937b-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="3937b-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="3937b-103">Upozorní profileru, že zpětná fáze zpracování výjimek zadává klauzuli `finally` obsaženou v zadané funkci.</span><span class="sxs-lookup"><span data-stu-id="3937b-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3937b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3937b-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3937b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3937b-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="3937b-106">\[in] ID funkce obsahující klauzuli `finally`.</span><span class="sxs-lookup"><span data-stu-id="3937b-106">\[in] The ID of the function that contains the `finally` clause.</span></span>

## <a name="remarks"></a><span data-ttu-id="3937b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3937b-107">Remarks</span></span>  
 <span data-ttu-id="3937b-108">Profiler by neměl při implementaci této metody blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezstavové uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3937b-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="3937b-109">Pokud se tady zablokuje Profiler a dojde k pokusu o uvolnění paměti, modul runtime se zablokuje, dokud toto zpětné volání nevrátí.</span><span class="sxs-lookup"><span data-stu-id="3937b-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="3937b-110">Implementace této metody v profileru by se neměla volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat alokaci spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="3937b-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3937b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3937b-111">Requirements</span></span>  
 <span data-ttu-id="3937b-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3937b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3937b-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3937b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3937b-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3937b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3937b-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3937b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3937b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3937b-116">See also</span></span>

- [<span data-ttu-id="3937b-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3937b-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3937b-118">GetNotifiedExceptionClauseInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="3937b-118">GetNotifiedExceptionClauseInfo Method</span></span>](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="3937b-119">ExceptionUnwindFinallyLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="3937b-119">ExceptionUnwindFinallyLeave Method</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)
