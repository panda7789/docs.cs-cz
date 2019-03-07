---
title: ICorProfilerCallback::ExceptionUnwindFunctionEnter – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 86eec8b80631b7504daea30ad50a5c5e29f00893
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476240"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="f63be-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="f63be-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="f63be-103">Oznámí profileru, že byl zahájen unwind fáze zpracování výjimky k provedení operace unwind funkce.</span><span class="sxs-lookup"><span data-stu-id="f63be-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f63be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f63be-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f63be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f63be-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f63be-106">[in] ID funkce, která je právě zachytila.</span><span class="sxs-lookup"><span data-stu-id="f63be-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f63be-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f63be-107">Remarks</span></span>  
 <span data-ttu-id="f63be-108">Profiler by neměla blokovat v rámci příslušné implementace této metody, protože zásobníku nemusí být ve stavu, která umožňuje uvolňování paměti, a proto není možné preemptive uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f63be-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="f63be-109">Pokud profiler blokuje tady a dojde k pokusu o uvolnění paměti, modul runtime bude blokovat, dokud tento zpětného volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="f63be-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="f63be-110">Okna profilování implementace této metody by neměla volat do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="f63be-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f63be-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f63be-111">Requirements</span></span>  
 <span data-ttu-id="f63be-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f63be-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f63be-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f63be-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f63be-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f63be-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f63be-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f63be-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63be-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f63be-116">See also</span></span>
- [<span data-ttu-id="f63be-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f63be-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f63be-118">ExceptionUnwindFunctionLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="f63be-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
