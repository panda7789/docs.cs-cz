---
title: "ICorProfilerCallback::ExceptionCatcherLeave – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d5d46b2388621deffdad4b10d7d2376cb42ee262
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="384b7-102">ICorProfilerCallback::ExceptionCatcherLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="384b7-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="384b7-103">Upozorní profileru, který ovládací prvek je předávána mimo odpovídající `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="384b7-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="384b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="384b7-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="384b7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="384b7-105">Remarks</span></span>  
 <span data-ttu-id="384b7-106">Profileru by neměly blokovat v jeho implementace této metody, protože zásobník nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="384b7-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="384b7-107">Pokud zde blokuje profileru a dojde k pokusu o uvolňování paměti, modul runtime se zablokuje, dokud se vrátí tato zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="384b7-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="384b7-108">Okna profilování implementace této metody by neměla volání do spravovaného kódu nebo v žádné příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="384b7-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="384b7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="384b7-109">Requirements</span></span>  
 <span data-ttu-id="384b7-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="384b7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="384b7-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="384b7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="384b7-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="384b7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="384b7-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="384b7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="384b7-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="384b7-114">See Also</span></span>  
 [<span data-ttu-id="384b7-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="384b7-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="384b7-116">ExceptionCatcherEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="384b7-116">ExceptionCatcherEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
