---
title: "ICorProfilerCallback::ExceptionUnwindFunctionEnter – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc41dc95776ca31178153402d2e145a3d2c13bf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="5f384-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="5f384-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="5f384-103">Upozorní profileru, že se začaly unwind funkci unwind fáze zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="5f384-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f384-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f384-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f384-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f384-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5f384-106">[v] ID funkce, která je právě odděleny.</span><span class="sxs-lookup"><span data-stu-id="5f384-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f384-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f384-107">Remarks</span></span>  
 <span data-ttu-id="5f384-108">Profileru by neměly blokovat v jeho implementace této metody, protože zásobník nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5f384-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="5f384-109">Pokud zde blokuje profileru a dojde k pokusu o uvolňování paměti, modul runtime se zablokuje, dokud se vrátí tato zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="5f384-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="5f384-110">Okna profilování implementace této metody by neměla volání do spravovaného kódu nebo v žádné příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="5f384-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f384-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f384-111">Requirements</span></span>  
 <span data-ttu-id="5f384-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f384-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f384-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f384-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5f384-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f384-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f384-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f384-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f384-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f384-116">See Also</span></span>  
 [<span data-ttu-id="5f384-117">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f384-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="5f384-118">Exceptionunwindfunctionleave – metoda</span><span class="sxs-lookup"><span data-stu-id="5f384-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
