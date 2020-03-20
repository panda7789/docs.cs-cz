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
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175171"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="3be85-102">FunctionIDMapper – funkce</span><span class="sxs-lookup"><span data-stu-id="3be85-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="3be85-103">Upozorní profiler, že daný identifikátor funkce může být přemapován na alternativní ID, které má být použito v [funkcích FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)a [FunctionTailcall2](functiontailcall2-function.md) pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="3be85-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="3be85-104">`FunctionIDMapper`také umožňuje profiler k označení, zda chce přijímat zpětná volání pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="3be85-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3be85-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3be85-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3be85-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3be85-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="3be85-107">\[in] Identifikátor funkce, který má být přemapován.</span><span class="sxs-lookup"><span data-stu-id="3be85-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="3be85-108">\[out] Ukazatel na hodnotu, kterou `true` nastaví profiler, `FunctionLeave2`pokud `FunctionTailcall2` chce přijímat `FunctionEnter2`, a zpětná volání; v opačném případě nastaví tuto hodnotu na `false`.</span><span class="sxs-lookup"><span data-stu-id="3be85-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="3be85-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3be85-109">Return Value</span></span>  
 <span data-ttu-id="3be85-110">Profiler vrátí hodnotu, která používá modul provádění jako alternativní identifikátor funkce.</span><span class="sxs-lookup"><span data-stu-id="3be85-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="3be85-111">Vrácená hodnota nemůže `false` být null, pokud není vrácena v `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="3be85-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="3be85-112">V opačném případě null vrácená hodnota bude mít nepředvídatelné výsledky, včetně případné zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="3be85-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3be85-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3be85-113">Remarks</span></span>  
 <span data-ttu-id="3be85-114">Funkce `FunctionIDMapper` je zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="3be85-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="3be85-115">Je implementován profiler přemapovat ID funkce na jiný identifikátor, který je užitečnější pro profiler.</span><span class="sxs-lookup"><span data-stu-id="3be85-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="3be85-116">Vrátí `FunctionIDMapper` alternativní ID, které má být použito pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="3be85-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="3be85-117">Modul provádění pak respektuje profiler požadavek předáním tohoto alternativního ID, kromě tradiční id funkce, `clientData` zpět `FunctionEnter2`do `FunctionLeave2`profileru v parametru , a `FunctionTailcall2` háčky, k identifikaci funkce, pro které je volán hák.</span><span class="sxs-lookup"><span data-stu-id="3be85-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="3be85-118">Metodu [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) můžete použít k určení `FunctionIDMapper` implementace funkce.</span><span class="sxs-lookup"><span data-stu-id="3be85-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="3be85-119">Můžete volat `ICorProfilerInfo::SetFunctionIDMapper` metodu pouze jednou a doporučujeme tak učinit v [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="3be85-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="3be85-120">Ve výchozím nastavení se předpokládá, že profiler, který nastaví příznak COR_PRF_MONITOR_ENTERLEAVE pomocí [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), a který nastaví háčky přes [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) `FunctionEnter2`nebo `FunctionLeave2` [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), by měl přijímat , a `FunctionTailcall2` zpětná volání pro každou funkci.</span><span class="sxs-lookup"><span data-stu-id="3be85-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="3be85-121">Profilovací programy však mohou implementovat `FunctionIDMapper` selektivně vyhnout přijímání `pbHookFunction` `false`těchto zpětná volání pro určité funkce nastavením na .</span><span class="sxs-lookup"><span data-stu-id="3be85-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="3be85-122">Profilovací programy by měly být tolerantní k případům, kdy více vláken profilované aplikace volá stejnou metodu/funkci současně.</span><span class="sxs-lookup"><span data-stu-id="3be85-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="3be85-123">V takových případech profiler může `FunctionIDMapper` přijímat více zpětná volání pro stejné `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="3be85-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="3be85-124">Profiler by měl být jistý vrátit stejné hodnoty z tohoto zpětného `FunctionID`volání, pokud je volána vícekrát se stejným .</span><span class="sxs-lookup"><span data-stu-id="3be85-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3be85-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3be85-125">Requirements</span></span>  
 <span data-ttu-id="3be85-126">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3be85-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3be85-127">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3be85-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3be85-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3be85-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3be85-129">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3be85-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be85-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="3be85-130">See also</span></span>

- [<span data-ttu-id="3be85-131">SetFunctionIDMapper – metoda</span><span class="sxs-lookup"><span data-stu-id="3be85-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="3be85-132">FunctionIDMapper2 – funkce</span><span class="sxs-lookup"><span data-stu-id="3be85-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="3be85-133">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="3be85-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="3be85-134">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="3be85-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="3be85-135">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="3be85-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="3be85-136">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="3be85-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
