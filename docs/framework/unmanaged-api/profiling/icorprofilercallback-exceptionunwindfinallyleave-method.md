---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: 8da9098e882dd4b4c1f60e4428ebe68421e629e1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500140"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="3b2dd-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="3b2dd-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="3b2dd-103">Upozorní profileru, že zpětná fáze zpracování výjimek opustila `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b2dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b2dd-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3b2dd-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b2dd-105">Remarks</span></span>  
 <span data-ttu-id="3b2dd-106">Profiler by neměl během tohoto volání blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezkontaktní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="3b2dd-107">Pokud profiler zablokuje a dojde k pokusu o uvolnění paměti, modul runtime zablokuje dokud toto zpětné volání nevrátí.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="3b2dd-108">Během tohoto volání nesmí Profiler volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b2dd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b2dd-109">Requirements</span></span>  
 <span data-ttu-id="3b2dd-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b2dd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b2dd-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3b2dd-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b2dd-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3b2dd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b2dd-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b2dd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b2dd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-114">See also</span></span>

- [<span data-ttu-id="3b2dd-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b2dd-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3b2dd-116">ExceptionUnwindFinallyEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="3b2dd-116">ExceptionUnwindFinallyEnter Method</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)
