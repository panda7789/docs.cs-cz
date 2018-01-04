---
title: "ICorProfilerCallback::ExceptionUnwindFinallyEnter – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3480761c2708fa2f15454a7a99c34e84ee34eb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="9d73d-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="9d73d-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="9d73d-103">Upozorní profileru, který fázi unwind výjimky je zpracování zadání `finally` klauzule obsažené v zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="9d73d-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d73d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d73d-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d73d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d73d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9d73d-106">[v] ID funkce, která obsahuje `finally` klauzule.</span><span class="sxs-lookup"><span data-stu-id="9d73d-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d73d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d73d-107">Remarks</span></span>  
 <span data-ttu-id="9d73d-108">Profileru by neměly blokovat v jeho implementace této metody, protože zásobník nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9d73d-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9d73d-109">Pokud zde blokuje profileru a dojde k pokusu o uvolňování paměti, modul runtime se zablokuje, dokud se vrátí tato zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9d73d-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9d73d-110">Okna profilování implementace této metody by neměla volání do spravovaného kódu nebo v žádné příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="9d73d-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d73d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d73d-111">Requirements</span></span>  
 <span data-ttu-id="9d73d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d73d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d73d-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9d73d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d73d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d73d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d73d-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d73d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d73d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d73d-116">See Also</span></span>  
 [<span data-ttu-id="9d73d-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d73d-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="9d73d-118">GetNotifiedExceptionClauseInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="9d73d-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)  
 [<span data-ttu-id="9d73d-119">ExceptionUnwindFinallyLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="9d73d-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
