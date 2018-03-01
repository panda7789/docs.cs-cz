---
title: "ICorProfilerCallback::ExceptionUnwindFinallyLeave – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 969bc0723929dffd16b3119a9c9b74499f35b0e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="bd37c-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="bd37c-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="bd37c-103">Upozorní profileru, který fázi unwind výjimky zpracování opustil `finally` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bd37c-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd37c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd37c-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd37c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd37c-105">Remarks</span></span>  
 <span data-ttu-id="bd37c-106">Profileru by neměly blokovat během toto volání, protože zásobníku nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="bd37c-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="bd37c-107">Pokud na profileru bloky a uvolnění paměti dojde k pokusu o, modul runtime zablokuje, dokud vrátí tuto zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="bd37c-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="bd37c-108">Navíc během tohoto hovoru profileru nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="bd37c-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd37c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd37c-109">Requirements</span></span>  
 <span data-ttu-id="bd37c-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd37c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd37c-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd37c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd37c-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd37c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd37c-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd37c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd37c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd37c-114">See Also</span></span>  
 [<span data-ttu-id="bd37c-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd37c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="bd37c-116">ExceptionUnwindFinallyEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="bd37c-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
