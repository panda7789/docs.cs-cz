---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9f95a404ce7124a76ee527cdc70ccccf103838b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076793"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="2095f-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="2095f-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="2095f-103">Určuje funkce implementované profileru mají být volány v aktualizované verze "zadejte", "ponechte" a "tailcall" háky spravované funkce.</span><span class="sxs-lookup"><span data-stu-id="2095f-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2095f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2095f-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2095f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2095f-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="2095f-106">[in] Ukazatel na implementaci pro použití jako [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2095f-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="2095f-107">[in] Ukazatel na implementaci pro použití jako [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2095f-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="2095f-108">[in] Ukazatel na implementaci pro použití jako [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2095f-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2095f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2095f-109">Remarks</span></span>  
 <span data-ttu-id="2095f-110">`SetEnterLeaveFunctionHooks2` Metoda je podobná [icorprofilerinfo::setenterleavefunctionhooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2095f-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="2095f-111">Použijte nejprve zadat jako novější verze enter/ponechání a koncové volání zpětná volání a jeho použití k určení funkce má být použit jako starší verze zpětná volání enter/ponechání a koncové volání funkcí.</span><span class="sxs-lookup"><span data-stu-id="2095f-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="2095f-112">Najednou může být aktivní pouze jednu sadu zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="2095f-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="2095f-113">Proto pokud profiler volá obě `ICorProfilerInfo::SetEnterLeaveFunctionHooks` a `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` se používá.</span><span class="sxs-lookup"><span data-stu-id="2095f-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="2095f-114">`SetEnterLeaveFunctionHooks2` Metoda může volat pouze z okna profilování [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2095f-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2095f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2095f-115">Requirements</span></span>  
 <span data-ttu-id="2095f-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2095f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2095f-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2095f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2095f-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2095f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2095f-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2095f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2095f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2095f-120">See also</span></span>

- [<span data-ttu-id="2095f-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2095f-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="2095f-122">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2095f-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
