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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7f1b2756dd180cb0a701429978a34ea80447a86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598005"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="21272-102">ICorProfilerCallback::ExceptionCatcherLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="21272-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="21272-103">Oznámí profileru, který se předává řízení mimo odpovídající `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="21272-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21272-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21272-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="21272-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21272-105">Remarks</span></span>  
 <span data-ttu-id="21272-106">Profiler by neměla blokovat v rámci příslušné implementace této metody, protože zásobníku nemusí být ve stavu, která umožňuje uvolňování paměti, a proto není možné preemptive uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="21272-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="21272-107">Pokud profiler blokuje tady a dojde k pokusu o uvolnění paměti, modul runtime bude blokovat, dokud tento zpětného volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="21272-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="21272-108">Okna profilování implementace této metody by neměla volat do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="21272-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21272-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21272-109">Requirements</span></span>  
 <span data-ttu-id="21272-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21272-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21272-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21272-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21272-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21272-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21272-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21272-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21272-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21272-114">See also</span></span>

- [<span data-ttu-id="21272-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21272-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="21272-116">ExceptionCatcherEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="21272-116">ExceptionCatcherEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
