---
title: "FunctionIDMapper – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionIDMapper
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionIDMapper
helpviewer_keywords: FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24e48ecb551a5faacc7da94b857b2e260f5aeca0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="functionidmapper-function"></a><span data-ttu-id="5449b-102">FunctionIDMapper – funkce</span><span class="sxs-lookup"><span data-stu-id="5449b-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="5449b-103">Profileru upozorní, že daným identifikátorem funkce může namapovat na alternativní ID, které má být používány [functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), a [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětných volání pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="5449b-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="5449b-104">`FunctionIDMapper`taky umožňuje profileru indikující, zda chce dostávat zpětných volání pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="5449b-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5449b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5449b-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5449b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5449b-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="5449b-107">[v] Identifikátor funkce přemapování.</span><span class="sxs-lookup"><span data-stu-id="5449b-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="5449b-108">[out] Ukazatel na hodnotu, která nastaví profileru `true` Pokud chce dostávat `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` zpětná volání; jinak, nastaví tato hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="5449b-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5449b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5449b-109">Return Value</span></span>  
 <span data-ttu-id="5449b-110">Profileru vrátí hodnotu, která modul provádění používá jako identifikátor alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="5449b-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="5449b-111">Návratová hodnota nemůže být null. Pokud `false` je vrácený v `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="5449b-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="5449b-112">Návratovou hodnotou null, jinak bude mít nepředvídatelné výsledky, včetně pravděpodobně zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="5449b-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5449b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5449b-113">Remarks</span></span>  
 <span data-ttu-id="5449b-114">`FunctionIDMapper` Je funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="5449b-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="5449b-115">Je implementováno profileru přemapování funkce ID na některé identifikátor, který je užitečnější pro profileru.</span><span class="sxs-lookup"><span data-stu-id="5449b-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="5449b-116">`FunctionIDMapper` Vrátí alternativní ID, který se má použít pro jakékoli dané funkce.</span><span class="sxs-lookup"><span data-stu-id="5449b-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="5449b-117">Spouštěcí modul potom splňuje požadavek profileru pomocí předání této alternativní ID, kromě ID tradiční funkce profileru v `clientData` parametr `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` háky k identifikaci Funkce, pro kterou je volána hák.</span><span class="sxs-lookup"><span data-stu-id="5449b-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="5449b-118">Můžete použít [icorprofilerinfo::setfunctionidmapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metoda k určení implementace `FunctionIDMapper` funkce.</span><span class="sxs-lookup"><span data-stu-id="5449b-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="5449b-119">Můžete volat `ICorProfilerInfo::SetFunctionIDMapper` metoda jenom jednou a My doporučujeme, abyste provedli takže v [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="5449b-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="5449b-120">Ve výchozím nastavení, se předpokládá, že profileru, který nastavuje příznak COR_PRF_MONITOR_ENTERLEAVE pomocí [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), a který nastaví háky prostřednictvím [icorprofilerinfo::setenterleavefunctionhooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) nebo [ICorProfilerInfo2::setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), mělo by se zobrazit `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` zpětných volání pro každou funkci.</span><span class="sxs-lookup"><span data-stu-id="5449b-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="5449b-121">Však může implementovat profilery `FunctionIDMapper` selektivně tomu, aby tyto zpětných volání pro určité funkce nastavením `pbHookFunction` k `false`.</span><span class="sxs-lookup"><span data-stu-id="5449b-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="5449b-122">Profilery by měl být odolný vůči chybám případů, kdy několik vláken PROFILOVANÉHO aplikace jsou volání stejné metody nebo funkce současně.</span><span class="sxs-lookup"><span data-stu-id="5449b-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="5449b-123">V takových případech profileru obdržet více `FunctionIDMapper` zpětných volání pro stejné `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="5449b-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="5449b-124">Profileru by měl být jistý, vrácení stejné hodnoty z této zpětného volání při volání víckrát se stejným `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="5449b-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5449b-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5449b-125">Requirements</span></span>  
 <span data-ttu-id="5449b-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5449b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5449b-127">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5449b-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5449b-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5449b-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5449b-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5449b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5449b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="5449b-130">See Also</span></span>  
 [<span data-ttu-id="5449b-131">SetFunctionIDMapper – metoda</span><span class="sxs-lookup"><span data-stu-id="5449b-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="5449b-132">FunctionIDMapper2 – funkce</span><span class="sxs-lookup"><span data-stu-id="5449b-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 [<span data-ttu-id="5449b-133">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="5449b-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="5449b-134">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="5449b-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="5449b-135">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="5449b-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="5449b-136">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5449b-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
