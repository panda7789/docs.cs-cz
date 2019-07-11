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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a6b754e6ceef0c451c38055078d403c0601ce45
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755939"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="49c30-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="49c30-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="49c30-103">Oznámí profileru, který fáze unwind výjimek zpracování není dostupný `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="49c30-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49c30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49c30-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="49c30-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49c30-105">Remarks</span></span>  
 <span data-ttu-id="49c30-106">Profiler by neměl přerušováno během toto volání, protože zásobník nemusí být ve stavu, která umožňuje uvolňování paměti, a proto není možné preemptive uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="49c30-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="49c30-107">Pokud se profiler bloky a uvolnění paměti dojde k pokusu o, modul runtime bude blokovat, dokud tento zpětného volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="49c30-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="49c30-108">Během tohoto volání nesmí také profiler volat, do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="49c30-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49c30-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49c30-109">Requirements</span></span>  
 <span data-ttu-id="49c30-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49c30-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49c30-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="49c30-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="49c30-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49c30-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49c30-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49c30-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49c30-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49c30-114">See also</span></span>

- [<span data-ttu-id="49c30-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49c30-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="49c30-116">ExceptionUnwindFinallyEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="49c30-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
