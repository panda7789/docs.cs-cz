---
title: FunctionIDMapper – funkce
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 23c6f0a29160b6e1dc194cf360c07374c565522b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440700"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="c6546-102">FunctionIDMapper – funkce</span><span class="sxs-lookup"><span data-stu-id="c6546-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="c6546-103">Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které má být použito v zpětných voláních [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)a [FunctionTailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="c6546-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="c6546-104">`FunctionIDMapper` také umožňuje profileru označit, zda chce přijímat zpětná volání této funkce.</span><span class="sxs-lookup"><span data-stu-id="c6546-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6546-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6546-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6546-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6546-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="c6546-107">pro Identifikátor funkce, která má být přemapována.</span><span class="sxs-lookup"><span data-stu-id="c6546-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="c6546-108">mimo Ukazatel na hodnotu, kterou Profiler nastaví, aby `true`, pokud chce přijímat `FunctionEnter2`, `FunctionLeave2`a zpětná volání `FunctionTailcall2`; v opačném případě nastaví tuto hodnotu na `false`.</span><span class="sxs-lookup"><span data-stu-id="c6546-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6546-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c6546-109">Return Value</span></span>  
 <span data-ttu-id="c6546-110">Profiler vrátí hodnotu, kterou spouštěcí modul používá jako alternativní identifikátor funkce.</span><span class="sxs-lookup"><span data-stu-id="c6546-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="c6546-111">Návratová hodnota nemůže být null, pokud není vráceno `false` v `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="c6546-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="c6546-112">V opačném případě návratová hodnota null vytvoří nepředvídatelné výsledky, včetně možného zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="c6546-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6546-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6546-113">Remarks</span></span>  
 <span data-ttu-id="c6546-114">Funkce `FunctionIDMapper` je zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="c6546-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="c6546-115">Je implementován profilerem k přemapování ID funkce na jiný identifikátor, který je užitečnější pro Profiler.</span><span class="sxs-lookup"><span data-stu-id="c6546-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="c6546-116">`FunctionIDMapper` vrátí alternativní ID, které se má použít pro libovolnou danou funkci.</span><span class="sxs-lookup"><span data-stu-id="c6546-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="c6546-117">Spouštěcí modul pak dodrží požadavek profileru tím, že předá toto alternativní ID k tradičnímu ID funkce zpět do profileru v parametru `clientData` `FunctionEnter2`, `FunctionLeave2`a `FunctionTailcall2`, aby identifikoval funkci, pro kterou je zavěšeno volání.</span><span class="sxs-lookup"><span data-stu-id="c6546-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="c6546-118">K určení implementace funkce `FunctionIDMapper` lze použít metodu [ICorProfilerInfo:: SetFunctionIDMapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c6546-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="c6546-119">Metodu `ICorProfilerInfo::SetFunctionIDMapper` lze volat pouze jednou a doporučujeme, abyste tak učinili v rámci zpětného volání [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c6546-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="c6546-120">Ve výchozím nastavení se předpokládá, že Profiler, který nastaví příznak COR_PRF_MONITOR_ENTERLEAVE pomocí [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)a který nastavuje háky prostřednictvím [ICorProfilerInfo:: SetEnterLeaveFunctionHooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) nebo [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), by měl přijímat zpětná volání `FunctionEnter2`, `FunctionLeave2`a `FunctionTailcall2` pro každou funkci.</span><span class="sxs-lookup"><span data-stu-id="c6546-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="c6546-121">Profilery ale mohou implementovat `FunctionIDMapper` pro selektivní zamezení příjmu těchto zpětných volání pro určité funkce nastavením `pbHookFunction` na `false`.</span><span class="sxs-lookup"><span data-stu-id="c6546-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="c6546-122">Profilery by měly být odolné vůči případům, kdy více vláken profilované aplikace volá stejnou metodu/funkci současně.</span><span class="sxs-lookup"><span data-stu-id="c6546-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="c6546-123">V takových případech může Profiler získat více `FunctionIDMapper`ch zpětného volání pro stejný `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="c6546-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="c6546-124">Profiler by měl být jistý, aby vracel stejné hodnoty z tohoto zpětného volání, pokud je volán několikrát se stejným `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="c6546-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6546-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6546-125">Requirements</span></span>  
 <span data-ttu-id="c6546-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6546-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6546-127">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="c6546-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c6546-128">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c6546-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6546-129">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6546-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6546-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6546-130">See also</span></span>

- [<span data-ttu-id="c6546-131">SetFunctionIDMapper – metoda</span><span class="sxs-lookup"><span data-stu-id="c6546-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="c6546-132">FunctionIDMapper2 – funkce</span><span class="sxs-lookup"><span data-stu-id="c6546-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [<span data-ttu-id="c6546-133">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="c6546-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="c6546-134">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="c6546-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="c6546-135">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="c6546-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="c6546-136">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c6546-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
