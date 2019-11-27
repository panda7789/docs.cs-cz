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
ms.openlocfilehash: 4068c8fee13a6086bc6b48bcc6d4117357062747
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449782"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="caa7a-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="caa7a-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="caa7a-103">Určuje funkce implementované profilerem, které mají být volány v aktualizovaných verzích zapojování spravovaných funkcí "Enter", "opustit" a "Tailcall".</span><span class="sxs-lookup"><span data-stu-id="caa7a-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caa7a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caa7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="caa7a-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="caa7a-106">pro Ukazatel na implementaci, která se má použít jako [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="caa7a-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="caa7a-107">pro Ukazatel na implementaci, která se má použít jako [FunctionLeave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="caa7a-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="caa7a-108">pro Ukazatel na implementaci, která se má použít jako [FunctionTailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="caa7a-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="caa7a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="caa7a-109">Remarks</span></span>  
 <span data-ttu-id="caa7a-110">Metoda `SetEnterLeaveFunctionHooks2` je podobná metodě [ICorProfilerInfo:: SetEnterLeaveFunctionHooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="caa7a-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="caa7a-111">Použijte předchozí, pokud chcete určit funkce, které mají být použity jako novější verze zpětných volání ENTER/opustit/Tailcall, a druhý pro určení funkcí, které mají být použity jako starší verze zpětných volání ENTER/opustit/Tailcall.</span><span class="sxs-lookup"><span data-stu-id="caa7a-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="caa7a-112">V jednom okamžiku může být aktivní jenom jedna sada zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="caa7a-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="caa7a-113">Proto pokud profiler zavolá jak `ICorProfilerInfo::SetEnterLeaveFunctionHooks`, tak `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` se používá.</span><span class="sxs-lookup"><span data-stu-id="caa7a-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="caa7a-114">Metodu `SetEnterLeaveFunctionHooks2` lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="caa7a-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caa7a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="caa7a-115">Requirements</span></span>  
 <span data-ttu-id="caa7a-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caa7a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caa7a-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="caa7a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="caa7a-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="caa7a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caa7a-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caa7a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa7a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="caa7a-120">See also</span></span>

- [<span data-ttu-id="caa7a-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="caa7a-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="caa7a-122">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="caa7a-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
