---
title: ICorProfilerCallback::ExceptionCatcherLeave – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
ms.openlocfilehash: cff2dd9fdb05ea4dd160dfa57df6f047beb57f69
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500296"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="28f3e-102">ICorProfilerCallback::ExceptionCatcherLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="28f3e-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="28f3e-103">Upozorňuje profileru, že řízení se předává z příslušného `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="28f3e-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28f3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28f3e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="28f3e-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28f3e-105">Remarks</span></span>  
 <span data-ttu-id="28f3e-106">Profiler by neměl při implementaci této metody blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezstavové uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="28f3e-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="28f3e-107">Pokud se tady zablokuje Profiler a dojde k pokusu o uvolnění paměti, modul runtime se zablokuje, dokud toto zpětné volání nevrátí.</span><span class="sxs-lookup"><span data-stu-id="28f3e-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="28f3e-108">Implementace této metody v profileru by se neměla volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat alokaci spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="28f3e-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28f3e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28f3e-109">Requirements</span></span>  
 <span data-ttu-id="28f3e-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28f3e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28f3e-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="28f3e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28f3e-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="28f3e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28f3e-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28f3e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f3e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28f3e-114">See also</span></span>

- [<span data-ttu-id="28f3e-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28f3e-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="28f3e-116">ExceptionCatcherEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="28f3e-116">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
