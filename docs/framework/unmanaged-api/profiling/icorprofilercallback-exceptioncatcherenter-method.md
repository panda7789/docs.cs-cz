---
title: ICorProfilerCallback::ExceptionCatcherEnter – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 534e0672820cc2509f32765274ad970fda69ec5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866504"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="0d4f9-102">ICorProfilerCallback::ExceptionCatcherEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="0d4f9-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="0d4f9-103">Upozorní profiler, že řízení probíhá předává příslušnému `catch`mu bloku.</span><span class="sxs-lookup"><span data-stu-id="0d4f9-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d4f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d4f9-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d4f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d4f9-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="0d4f9-106">\[in] identifikátor funkce obsahující `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="0d4f9-106">\[in] The identifier of the function containing the `catch` block.</span></span>
  
- `objectId`

  <span data-ttu-id="0d4f9-107">\[in] identifikátor zpracovávané výjimky.</span><span class="sxs-lookup"><span data-stu-id="0d4f9-107">\[in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d4f9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d4f9-108">Remarks</span></span>  
 <span data-ttu-id="0d4f9-109">Metoda `ExceptionCatcherEnter` je volána pouze v případě, že je bod catch v kódu kompilován s kompilátorem JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="0d4f9-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="0d4f9-110">Výjimka, která je zachycena v nespravovaném kódu nebo v interním kódu modulu runtime, nebude volat toto oznámení.</span><span class="sxs-lookup"><span data-stu-id="0d4f9-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="0d4f9-111">Hodnota `objectId` je znovu předána, protože uvolňování paměti mohlo přesunout objekt od posledního oznámení `ExceptionThrown`.</span><span class="sxs-lookup"><span data-stu-id="0d4f9-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="0d4f9-112">Profiler by neměl při implementaci této metody blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezstavové uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0d4f9-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="0d4f9-113">Pokud se tady zablokuje Profiler a dojde k pokusu o uvolnění paměti, modul runtime se zablokuje, dokud toto zpětné volání nevrátí.</span><span class="sxs-lookup"><span data-stu-id="0d4f9-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="0d4f9-114">Implementace této metody v profileru by se neměla volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat alokaci spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="0d4f9-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d4f9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d4f9-115">Requirements</span></span>  
 <span data-ttu-id="0d4f9-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d4f9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d4f9-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0d4f9-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d4f9-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0d4f9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d4f9-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d4f9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d4f9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d4f9-120">See also</span></span>

- [<span data-ttu-id="0d4f9-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d4f9-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0d4f9-122">ExceptionCatcherLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="0d4f9-122">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
