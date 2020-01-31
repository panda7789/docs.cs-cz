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
ms.openlocfilehash: d5bf6626e2c6ba15fa9a5da08bcf2d9052866750
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866941"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="af09a-102">FunctionIDMapper – funkce</span><span class="sxs-lookup"><span data-stu-id="af09a-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="af09a-103">Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které má být použito v zpětných voláních [FunctionEnter2](functionenter2-function.md), [FunctionLeave2 –](functionleave2-function.md)a [FunctionTailcall2 –](functiontailcall2-function.md) pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="af09a-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="af09a-104">`FunctionIDMapper` také umožňuje profileru označit, zda chce přijímat zpětná volání této funkce.</span><span class="sxs-lookup"><span data-stu-id="af09a-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af09a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af09a-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af09a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="af09a-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="af09a-107">\[v] identifikátor funkce, který se má přemapovat.</span><span class="sxs-lookup"><span data-stu-id="af09a-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="af09a-108">\[] ukazatel na hodnotu, kterou Profiler nastaví na `true`, pokud chce přijímat zpětná volání `FunctionEnter2`, `FunctionLeave2`a `FunctionTailcall2`; v opačném případě nastaví tuto hodnotu na `false`.</span><span class="sxs-lookup"><span data-stu-id="af09a-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="af09a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="af09a-109">Return Value</span></span>  
 <span data-ttu-id="af09a-110">Profiler vrátí hodnotu, kterou spouštěcí modul používá jako alternativní identifikátor funkce.</span><span class="sxs-lookup"><span data-stu-id="af09a-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="af09a-111">Návratová hodnota nemůže být null, pokud není vráceno `false` v `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="af09a-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="af09a-112">V opačném případě návratová hodnota null vytvoří nepředvídatelné výsledky, včetně možného zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="af09a-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af09a-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af09a-113">Remarks</span></span>  
 <span data-ttu-id="af09a-114">Funkce `FunctionIDMapper` je zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="af09a-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="af09a-115">Je implementován profilerem k přemapování ID funkce na jiný identifikátor, který je užitečnější pro Profiler.</span><span class="sxs-lookup"><span data-stu-id="af09a-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="af09a-116">`FunctionIDMapper` vrátí alternativní ID, které se má použít pro libovolnou danou funkci.</span><span class="sxs-lookup"><span data-stu-id="af09a-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="af09a-117">Spouštěcí modul pak dodrží požadavek profileru tím, že předá toto alternativní ID k tradičnímu ID funkce zpět do profileru v parametru `clientData` `FunctionEnter2`, `FunctionLeave2`a `FunctionTailcall2`, aby identifikoval funkci, pro kterou je zavěšeno volání.</span><span class="sxs-lookup"><span data-stu-id="af09a-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="af09a-118">K určení implementace funkce `FunctionIDMapper` lze použít metodu [ICorProfilerInfo:: SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md) .</span><span class="sxs-lookup"><span data-stu-id="af09a-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="af09a-119">Metodu `ICorProfilerInfo::SetFunctionIDMapper` lze volat pouze jednou a doporučujeme, abyste tak učinili v rámci zpětného volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="af09a-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="af09a-120">Ve výchozím nastavení se předpokládá, že Profiler, který nastaví příznak COR_PRF_MONITOR_ENTERLEAVE pomocí [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)a který nastavuje háky prostřednictvím [ICorProfilerInfo:: SetEnterLeaveFunctionHooks –](icorprofilerinfo-setenterleavefunctionhooks-method.md) nebo [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 –](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), by měl přijímat zpětná volání `FunctionEnter2`, `FunctionLeave2`a `FunctionTailcall2` pro každou funkci.</span><span class="sxs-lookup"><span data-stu-id="af09a-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="af09a-121">Profilery ale mohou implementovat `FunctionIDMapper` pro selektivní zamezení příjmu těchto zpětných volání pro určité funkce nastavením `pbHookFunction` na `false`.</span><span class="sxs-lookup"><span data-stu-id="af09a-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="af09a-122">Profilery by měly být odolné vůči případům, kdy více vláken profilované aplikace volá stejnou metodu/funkci současně.</span><span class="sxs-lookup"><span data-stu-id="af09a-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="af09a-123">V takových případech může Profiler získat více `FunctionIDMapper`ch zpětného volání pro stejný `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="af09a-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="af09a-124">Profiler by měl být jistý, aby vracel stejné hodnoty z tohoto zpětného volání, pokud je volán několikrát se stejným `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="af09a-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af09a-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af09a-125">Requirements</span></span>  
 <span data-ttu-id="af09a-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af09a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af09a-127">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="af09a-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="af09a-128">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="af09a-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af09a-129">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af09a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af09a-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af09a-130">See also</span></span>

- [<span data-ttu-id="af09a-131">SetFunctionIDMapper – metoda</span><span class="sxs-lookup"><span data-stu-id="af09a-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="af09a-132">FunctionIDMapper2 – funkce</span><span class="sxs-lookup"><span data-stu-id="af09a-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="af09a-133">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="af09a-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="af09a-134">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="af09a-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="af09a-135">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="af09a-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="af09a-136">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="af09a-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
