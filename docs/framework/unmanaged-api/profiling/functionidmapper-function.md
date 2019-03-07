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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0320c831648c15dfec42c1b693be2f13e6888ae9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475161"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="511a1-102">FunctionIDMapper – funkce</span><span class="sxs-lookup"><span data-stu-id="511a1-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="511a1-103">Oznámí profileru, že daný identifikátor funkce může přemapován na alternativní ID se použije v [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), a [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětná volání pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="511a1-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="511a1-104">`FunctionIDMapper` také umožňuje profileru označíte, zda si přeje přijmout zpětná volání pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="511a1-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="511a1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="511a1-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="511a1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="511a1-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="511a1-107">[in] Identifikátor funkce pro přemapování.</span><span class="sxs-lookup"><span data-stu-id="511a1-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="511a1-108">[out] Ukazatel na hodnotu, která profiler nastaví na `true` Pokud chce přijmout `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` zpětná volání; jinak nastaví tuto hodnotu na `false`.</span><span class="sxs-lookup"><span data-stu-id="511a1-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="511a1-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="511a1-109">Return Value</span></span>  
 <span data-ttu-id="511a1-110">Profiler vrací hodnotu, která spouštěcí modul používá jako alternativní identifikátor funkce.</span><span class="sxs-lookup"><span data-stu-id="511a1-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="511a1-111">Návratová hodnota nemůže mít hodnotu null není-li `false` se vrátí v `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="511a1-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="511a1-112">Návratovou hodnotou null, jinak bude mít nepředvídatelné výsledky, včetně případného zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="511a1-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="511a1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="511a1-113">Remarks</span></span>  
 <span data-ttu-id="511a1-114">`FunctionIDMapper` Je funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="511a1-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="511a1-115">Je implementováno pomocí profileru přemapování ID funkce na jiný identifikátor, který je užitečnější profileru.</span><span class="sxs-lookup"><span data-stu-id="511a1-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="511a1-116">`FunctionIDMapper` Vrátí alternativní ID se má použít pro jakékoli dané funkce.</span><span class="sxs-lookup"><span data-stu-id="511a1-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="511a1-117">Prováděcí modul pak respektuje předáním této alternativní ID, kromě ID tradičních funkce zpět do okna profilování v profileru požadavek `clientData` parametr `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` háky k identifikaci Funkce, pro který se nazývá zavěšení.</span><span class="sxs-lookup"><span data-stu-id="511a1-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="511a1-118">Můžete použít [icorprofilerinfo::setfunctionidmapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metodu k určení provádění `FunctionIDMapper` funkce.</span><span class="sxs-lookup"><span data-stu-id="511a1-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="511a1-119">Můžete volat `ICorProfilerInfo::SetFunctionIDMapper` metoda pouze jednou a My doporučujeme, abyste udělali, [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="511a1-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="511a1-120">Ve výchozím nastavení, předpokládá se, že profiler, který nastavuje příznak COR_PRF_MONITOR_ENTERLEAVE pomocí [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), a který nastaví háky prostřednictvím [icorprofilerinfo::setenterleavefunctionhooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) nebo [ICorProfilerInfo2::setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), mělo by se zobrazit `FunctionEnter2`, `FunctionLeave2`, a `FunctionTailcall2` zpětná volání pro každou funkci.</span><span class="sxs-lookup"><span data-stu-id="511a1-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="511a1-121">Však může implementovat profilery `FunctionIDMapper` selektivně zabránili tato zpětná volání pro určité funkce tak, že nastavíte `pbHookFunction` k `false`.</span><span class="sxs-lookup"><span data-stu-id="511a1-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="511a1-122">Profilovací programy by měl být odolný vůči chybám případů, kdy více vláken profilované aplikace jsou volání stejné metody/funkce současně.</span><span class="sxs-lookup"><span data-stu-id="511a1-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="511a1-123">V takových případech může profiler se zobrazit více `FunctionIDMapper` zpětná volání pro stejnou `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="511a1-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="511a1-124">Profiler by měl být určité vrácení stejné hodnoty z této zpětné volání, když je volána více než jednou se stejným `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="511a1-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="511a1-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="511a1-125">Requirements</span></span>  
 <span data-ttu-id="511a1-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="511a1-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="511a1-127">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="511a1-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="511a1-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="511a1-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="511a1-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="511a1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="511a1-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="511a1-130">See also</span></span>
- [<span data-ttu-id="511a1-131">SetFunctionIDMapper – metoda</span><span class="sxs-lookup"><span data-stu-id="511a1-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="511a1-132">FunctionIDMapper2 – funkce</span><span class="sxs-lookup"><span data-stu-id="511a1-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [<span data-ttu-id="511a1-133">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="511a1-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="511a1-134">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="511a1-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="511a1-135">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="511a1-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="511a1-136">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="511a1-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
