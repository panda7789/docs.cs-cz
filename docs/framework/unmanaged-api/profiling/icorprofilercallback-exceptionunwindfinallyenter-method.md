---
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e6109796d633c5facf5c0b07e0793cb8f7dc77e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549808"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="c81b8-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="c81b8-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="c81b8-103">Oznámí profileru, který fáze unwind výjimek zpracování přechází `finally` doložky zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="c81b8-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c81b8-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c81b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c81b8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c81b8-106">[in] ID funkce, která obsahuje `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c81b8-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c81b8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c81b8-107">Remarks</span></span>  
 <span data-ttu-id="c81b8-108">Profiler by neměla blokovat v rámci příslušné implementace této metody, protože zásobníku nemusí být ve stavu, která umožňuje uvolňování paměti, a proto není možné preemptive uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c81b8-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="c81b8-109">Pokud profiler blokuje tady a dojde k pokusu o uvolnění paměti, modul runtime bude blokovat, dokud tento zpětného volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="c81b8-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="c81b8-110">Okna profilování implementace této metody by neměla volat do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="c81b8-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c81b8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c81b8-111">Requirements</span></span>  
 <span data-ttu-id="c81b8-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c81b8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c81b8-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c81b8-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c81b8-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c81b8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c81b8-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c81b8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81b8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c81b8-116">See also</span></span>
- [<span data-ttu-id="c81b8-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c81b8-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c81b8-118">GetNotifiedExceptionClauseInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="c81b8-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="c81b8-119">ExceptionUnwindFinallyLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="c81b8-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
