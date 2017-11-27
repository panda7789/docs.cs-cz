---
title: "ICorProfilerCallback::ExceptionCatcherEnter – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCatcherEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b1605fdca3f5aa13ce4e29c0ff2fb42383512e6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="28d2a-102">ICorProfilerCallback::ExceptionCatcherEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="28d2a-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="28d2a-103">Upozorní profileru, který je předáván ovládacího prvku na příslušné `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="28d2a-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28d2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28d2a-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28d2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28d2a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="28d2a-106">[v] Identifikátor obsahující funkce `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="28d2a-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="28d2a-107">[v] Identifikátor výjimku zpracovanou.</span><span class="sxs-lookup"><span data-stu-id="28d2a-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28d2a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28d2a-108">Remarks</span></span>  
 <span data-ttu-id="28d2a-109">`ExceptionCatcherEnter` Metoda je volána, pouze pokud je bod catch v kódu kompilovat s kompilátoru v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="28d2a-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="28d2a-110">Výjimka, která je zachycena v nespravovaném kódu nebo v interní kódu modulu runtime nebude volat toto oznámení.</span><span class="sxs-lookup"><span data-stu-id="28d2a-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="28d2a-111">`objectId` Hodnota, je předaná znovu, protože kolekce paměti může mít přesunout objekt od `ExceptionThrown` oznámení.</span><span class="sxs-lookup"><span data-stu-id="28d2a-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="28d2a-112">Profileru by neměly blokovat v jeho implementace této metody, protože zásobník nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="28d2a-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="28d2a-113">Pokud zde blokuje profileru a dojde k pokusu o uvolňování paměti, modul runtime se zablokuje, dokud se vrátí tato zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="28d2a-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="28d2a-114">Okna profilování implementace této metody by neměla volání do spravovaného kódu nebo v žádné příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="28d2a-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28d2a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28d2a-115">Requirements</span></span>  
 <span data-ttu-id="28d2a-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28d2a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28d2a-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="28d2a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28d2a-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28d2a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28d2a-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28d2a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d2a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="28d2a-120">See Also</span></span>  
 [<span data-ttu-id="28d2a-121">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28d2a-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="28d2a-122">Exceptioncatcherleave – metoda</span><span class="sxs-lookup"><span data-stu-id="28d2a-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
