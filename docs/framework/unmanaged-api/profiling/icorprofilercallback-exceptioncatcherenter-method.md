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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb31da8b3fb9148bb41cf7216b44e7cbf610eaee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671613"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="4f338-102">ICorProfilerCallback::ExceptionCatcherEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="4f338-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="4f338-103">Oznámí profileru, který ovládací prvek je předávaný do příslušné `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="4f338-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f338-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f338-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f338-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f338-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="4f338-106">[in] Funkce obsahující identifikátor `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="4f338-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="4f338-107">[in] Identifikátor zpracovávanou výjimku.</span><span class="sxs-lookup"><span data-stu-id="4f338-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f338-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f338-108">Remarks</span></span>  
 <span data-ttu-id="4f338-109">`ExceptionCatcherEnter` Metoda je volána, pouze pokud je bod catch v kódu zkompilovaném pomocí kompilátor just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="4f338-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="4f338-110">Výjimka, která je zachycena v nespravovaném kódu nebo vnitřní kód modulu runtime nebude volat toto oznámení.</span><span class="sxs-lookup"><span data-stu-id="4f338-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="4f338-111">`objectId` Hodnota předána znovu, protože uvolňování paměti může mít přesunout objekt od `ExceptionThrown` oznámení.</span><span class="sxs-lookup"><span data-stu-id="4f338-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="4f338-112">Profiler by neměla blokovat v rámci příslušné implementace této metody, protože zásobníku nemusí být ve stavu, která umožňuje uvolňování paměti, a proto není možné preemptive uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4f338-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="4f338-113">Pokud profiler blokuje tady a dojde k pokusu o uvolnění paměti, modul runtime bude blokovat, dokud tento zpětného volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="4f338-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="4f338-114">Okna profilování implementace této metody by neměla volat do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="4f338-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f338-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f338-115">Requirements</span></span>  
 <span data-ttu-id="4f338-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f338-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f338-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4f338-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f338-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f338-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f338-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f338-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f338-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f338-120">See also</span></span>
- [<span data-ttu-id="4f338-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f338-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="4f338-122">ExceptionCatcherLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="4f338-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
