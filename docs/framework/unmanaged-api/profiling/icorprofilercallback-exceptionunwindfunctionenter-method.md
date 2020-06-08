---
title: ICorProfilerCallback::ExceptionUnwindFunctionEnter – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
ms.openlocfilehash: 5e50255342abae43565fd3556964c24ba4385eb8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500127"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="807cc-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="807cc-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="807cc-103">Upozorní profileru, že zpětná fáze zpracování výjimek začala odvinout funkci.</span><span class="sxs-lookup"><span data-stu-id="807cc-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="807cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="807cc-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="807cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="807cc-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="807cc-106">\[v] ID funkce, která se má oddělit.</span><span class="sxs-lookup"><span data-stu-id="807cc-106">\[in] The ID of the function that is being unwound.</span></span>

## <a name="remarks"></a><span data-ttu-id="807cc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="807cc-107">Remarks</span></span>  
 <span data-ttu-id="807cc-108">Profiler by neměl při implementaci této metody blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezstavové uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="807cc-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="807cc-109">Pokud se tady zablokuje Profiler a dojde k pokusu o uvolnění paměti, modul runtime se zablokuje, dokud toto zpětné volání nevrátí.</span><span class="sxs-lookup"><span data-stu-id="807cc-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="807cc-110">Implementace této metody v profileru by se neměla volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat alokaci spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="807cc-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="807cc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="807cc-111">Requirements</span></span>  
 <span data-ttu-id="807cc-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="807cc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="807cc-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="807cc-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="807cc-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="807cc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="807cc-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="807cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="807cc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="807cc-116">See also</span></span>

- [<span data-ttu-id="807cc-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="807cc-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="807cc-118">ExceptionUnwindFunctionLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="807cc-118">ExceptionUnwindFunctionLeave Method</span></span>](icorprofilercallback-exceptionunwindfunctionleave-method.md)
