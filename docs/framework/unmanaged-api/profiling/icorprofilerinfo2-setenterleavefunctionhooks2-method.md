---
title: "ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c460cfd24a83ca2a6c75e061b7a797c8f455bc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="557aa-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="557aa-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="557aa-103">Určuje implementované profileru funkce k volání na aktualizované verze "zadejte", "nechte" a "tailcall" háky spravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="557aa-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="557aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="557aa-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="557aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="557aa-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="557aa-106">[v] Ukazatel na implementaci má být použit jako [functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="557aa-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="557aa-107">[v] Ukazatel na implementaci má být použit jako [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="557aa-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="557aa-108">[v] Ukazatel na implementaci má být použit jako [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="557aa-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="557aa-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="557aa-109">Remarks</span></span>  
 <span data-ttu-id="557aa-110">`SetEnterLeaveFunctionHooks2` Metoda je podobná [icorprofilerinfo::setenterleavefunctionhooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="557aa-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="557aa-111">Pomocí bývalé můžete určit funkce, které má být použit jako novější verze enter nebo ponechejte/tailcall zpětná volání a k tomu, chcete-li určit funkce, které má být použit jako starší verze enter nebo ponechejte/tailcall zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="557aa-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="557aa-112">Najednou může být aktivní jen jednu sadu zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="557aa-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="557aa-113">Proto pokud profileru volá obě `ICorProfilerInfo::SetEnterLeaveFunctionHooks` a `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` se používá.</span><span class="sxs-lookup"><span data-stu-id="557aa-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="557aa-114">`SetEnterLeaveFunctionHooks2` Metoda může volat pouze z okna profilování [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="557aa-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="557aa-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="557aa-115">Requirements</span></span>  
 <span data-ttu-id="557aa-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="557aa-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="557aa-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="557aa-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="557aa-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="557aa-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="557aa-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="557aa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="557aa-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="557aa-120">See Also</span></span>  
 [<span data-ttu-id="557aa-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="557aa-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="557aa-122">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="557aa-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
