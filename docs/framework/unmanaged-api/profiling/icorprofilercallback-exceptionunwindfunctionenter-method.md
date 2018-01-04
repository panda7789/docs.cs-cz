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
ms.workload: dotnet
ms.openlocfilehash: bae438413ad81d556d8aeb0ca4a3526bcd968d67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="9e246-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="9e246-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="9e246-103">Upozorní profileru, že se začaly unwind funkci unwind fáze zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="9e246-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e246-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e246-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e246-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e246-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9e246-106">[v] ID funkce, která je právě odděleny.</span><span class="sxs-lookup"><span data-stu-id="9e246-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e246-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e246-107">Remarks</span></span>  
 <span data-ttu-id="9e246-108">Profileru by neměly blokovat v jeho implementace této metody, protože zásobník nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9e246-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9e246-109">Pokud zde blokuje profileru a dojde k pokusu o uvolňování paměti, modul runtime se zablokuje, dokud se vrátí tato zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9e246-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9e246-110">Okna profilování implementace této metody by neměla volání do spravovaného kódu nebo v žádné příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="9e246-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e246-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e246-111">Requirements</span></span>  
 <span data-ttu-id="9e246-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e246-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e246-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9e246-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e246-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e246-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e246-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e246-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e246-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e246-116">See Also</span></span>  
 [<span data-ttu-id="9e246-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e246-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="9e246-118">ExceptionUnwindFunctionLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="9e246-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
