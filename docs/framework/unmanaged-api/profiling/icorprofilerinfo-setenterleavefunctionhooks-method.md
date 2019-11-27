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
ms.openlocfilehash: 45593e7e30e1c8f8036489936aab3c607b01dd52
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438643"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="18a09-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks – metoda</span><span class="sxs-lookup"><span data-stu-id="18a09-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="18a09-103">Určuje funkce implementované profilerem, které mají být volány u funkcí "Enter", "opustit" a "Tailcall" u spravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="18a09-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18a09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18a09-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18a09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18a09-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="18a09-106">pro Ukazatel na implementaci, která se má použít jako [FunctionEnter –](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="18a09-106">[in] A pointer to the implementation to be used as the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="18a09-107">pro Ukazatel na implementaci, která se má použít jako [FunctionLeave –](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="18a09-107">[in] A pointer to the implementation to be used as the [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="18a09-108">pro Ukazatel na implementaci, která se má použít jako [FunctionTailcall –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="18a09-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18a09-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18a09-109">Remarks</span></span>  
 <span data-ttu-id="18a09-110">V .NET Framework verze 1,0 může mít každý ukazatel na funkci hodnotu null, aby bylo toto odpovídající zpětné volání zakázáno.</span><span class="sxs-lookup"><span data-stu-id="18a09-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="18a09-111">V jednom okamžiku může být aktivní jenom jedna sada zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="18a09-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="18a09-112">Proto pokud profiler volá jak `SetEnterLeaveFunctionHooks`, tak [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), má `SetEnterLeaveFunctionHooks2` přednost.</span><span class="sxs-lookup"><span data-stu-id="18a09-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="18a09-113">Metodu `SetEnterLeaveFunctionHooks` lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) v profileru.</span><span class="sxs-lookup"><span data-stu-id="18a09-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18a09-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18a09-114">Requirements</span></span>  
 <span data-ttu-id="18a09-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18a09-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18a09-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="18a09-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="18a09-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="18a09-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18a09-118">**Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18a09-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a09-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18a09-119">See also</span></span>

- [<span data-ttu-id="18a09-120">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18a09-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
