---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58e7b3e76d90e9e43f3f5259c52b52cd9f8e1f6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455072"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="868c2-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks – metoda</span><span class="sxs-lookup"><span data-stu-id="868c2-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="868c2-103">Určuje implementované profileru funkce k volání na "zadejte", "nechte" a "tailcall" háky spravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="868c2-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="868c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="868c2-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="868c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="868c2-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="868c2-106">[v] Ukazatel na implementaci má být použit jako [functionenter –](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="868c2-106">[in] A pointer to the implementation to be used as the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="868c2-107">[v] Ukazatel na implementaci má být použit jako [functionleave –](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="868c2-107">[in] A pointer to the implementation to be used as the [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="868c2-108">[v] Ukazatel na implementaci má být použit jako [functiontailcall –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="868c2-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="868c2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="868c2-109">Remarks</span></span>  
 <span data-ttu-id="868c2-110">V rozhraní .NET Framework verze 1.0 může mít hodnotu null zakázat že odpovídající zpětné volání každý ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="868c2-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="868c2-111">Najednou může být aktivní pouze jednu sadu zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="868c2-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="868c2-112">Proto pokud profileru volá obě `SetEnterLeaveFunctionHooks` a [ICorProfilerInfo2::setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), pak `SetEnterLeaveFunctionHooks2` přednost.</span><span class="sxs-lookup"><span data-stu-id="868c2-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="868c2-113">`SetEnterLeaveFunctionHooks` Metodu lze volat pouze z okna profilování [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="868c2-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="868c2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="868c2-114">Requirements</span></span>  
 <span data-ttu-id="868c2-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="868c2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="868c2-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="868c2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="868c2-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="868c2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="868c2-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="868c2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868c2-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="868c2-119">See Also</span></span>  
 [<span data-ttu-id="868c2-120">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="868c2-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
