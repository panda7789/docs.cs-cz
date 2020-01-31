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
ms.openlocfilehash: 7eac42e1d8132ca9e6d6c6b43efd43b88c1e5d3d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868574"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="eafee-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="eafee-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="eafee-103">Určuje funkce implementované profilerem, které mají být volány v aktualizovaných verzích zapojování spravovaných funkcí "Enter", "opustit" a "Tailcall".</span><span class="sxs-lookup"><span data-stu-id="eafee-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eafee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eafee-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eafee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eafee-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="eafee-106">pro Ukazatel na implementaci, která se má použít jako [FunctionEnter2](functionenter2-function.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="eafee-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="eafee-107">pro Ukazatel na implementaci, která se má použít jako [FunctionLeave2 –](functionleave2-function.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="eafee-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="eafee-108">pro Ukazatel na implementaci, která se má použít jako [FunctionTailcall2 –](functiontailcall2-function.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="eafee-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eafee-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eafee-109">Remarks</span></span>  
 <span data-ttu-id="eafee-110">Metoda `SetEnterLeaveFunctionHooks2` je podobná metodě [ICorProfilerInfo:: SetEnterLeaveFunctionHooks –](icorprofilerinfo-setenterleavefunctionhooks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="eafee-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="eafee-111">Použijte předchozí, pokud chcete určit funkce, které mají být použity jako novější verze zpětných volání ENTER/opustit/Tailcall, a druhý pro určení funkcí, které mají být použity jako starší verze zpětných volání ENTER/opustit/Tailcall.</span><span class="sxs-lookup"><span data-stu-id="eafee-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="eafee-112">V jednom okamžiku může být aktivní jenom jedna sada zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="eafee-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="eafee-113">Proto pokud profiler zavolá jak `ICorProfilerInfo::SetEnterLeaveFunctionHooks`, tak `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` se používá.</span><span class="sxs-lookup"><span data-stu-id="eafee-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="eafee-114">Metodu `SetEnterLeaveFunctionHooks2` lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="eafee-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eafee-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eafee-115">Requirements</span></span>  
 <span data-ttu-id="eafee-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eafee-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eafee-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eafee-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eafee-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eafee-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eafee-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eafee-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eafee-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eafee-120">See also</span></span>

- [<span data-ttu-id="eafee-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eafee-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="eafee-122">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eafee-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
