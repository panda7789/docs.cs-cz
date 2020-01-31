---
title: Profilace globálních statických funkcí
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 20ee2a9e045d839aa8ac043e035c438986b987ef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860863"
---
# <a name="profiling-global-static-functions"></a><span data-ttu-id="b5516-102">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="b5516-102">Profiling Global Static Functions</span></span>
<span data-ttu-id="b5516-103">Tato část popisuje nespravované funkce rozhraní API, které používá profilování API.</span><span class="sxs-lookup"><span data-stu-id="b5516-103">This section describes the unmanaged API functions that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5516-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b5516-104">In This Section</span></span>  
  
## <a name="net-framework-version-1-profiling-functions"></a><span data-ttu-id="b5516-105">Funkce profilování pro .NET Framework verze 1</span><span class="sxs-lookup"><span data-stu-id="b5516-105">.NET Framework version 1 Profiling Functions</span></span>  
 [<span data-ttu-id="b5516-106">FunctionEnter – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-106">FunctionEnter Function</span></span>](functionenter-function.md)  
 <span data-ttu-id="b5516-107">Upozorňuje profileru, že řízení je předáno funkci.</span><span class="sxs-lookup"><span data-stu-id="b5516-107">Notifies the profiler that control is being passed to a function.</span></span> <span data-ttu-id="b5516-108">Zastaralé v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b5516-108">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="b5516-109">FunctionLeave – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-109">FunctionLeave Function</span></span>](functionleave-function.md)  
 <span data-ttu-id="b5516-110">Upozorní profileru, že se chystá návrat funkce k volajícímu.</span><span class="sxs-lookup"><span data-stu-id="b5516-110">Notifies the profiler that a function is about to return to the caller.</span></span> <span data-ttu-id="b5516-111">Zastaralé v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b5516-111">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="b5516-112">FunctionTailcall – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-112">FunctionTailcall Function</span></span>](functiontailcall-function.md)  
 <span data-ttu-id="b5516-113">Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce.</span><span class="sxs-lookup"><span data-stu-id="b5516-113">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span> <span data-ttu-id="b5516-114">Zastaralé v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b5516-114">Deprecated in the .NET Framework 2.0.</span></span>  
  
## <a name="net-framework-version-2-profiling-functions"></a><span data-ttu-id="b5516-115">Funkce profilace .NET Framework verze 2</span><span class="sxs-lookup"><span data-stu-id="b5516-115">.NET Framework version 2 Profiling Functions</span></span>  
 [<span data-ttu-id="b5516-116">FunctionIDMapper – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-116">FunctionIDMapper Function</span></span>](functionidmapper-function.md)  
 <span data-ttu-id="b5516-117">Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které má být použito v zpětných voláních [FunctionEnter2](functionenter2-function.md), [FunctionLeave2 –](functionleave2-function.md)a [FunctionTailcall2 –](functiontailcall2-function.md) pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="b5516-117">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="b5516-118">Také umožňuje profileru označit, zda chce přijímat zpětná volání pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="b5516-118">Also enables the profiler to indicate whether it wants to receive callbacks for that function</span></span>  
  
 [<span data-ttu-id="b5516-119">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-119">FunctionEnter2 Function</span></span>](functionenter2-function.md)  
 <span data-ttu-id="b5516-120">Upozorňuje profileru, že řízení je předáno funkci a poskytuje informace o bloku zásobníku a argumentech funkce.</span><span class="sxs-lookup"><span data-stu-id="b5516-120">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="b5516-121">Zastaralé v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b5516-121">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="b5516-122">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-122">FunctionLeave2 Function</span></span>](functionleave2-function.md)  
 <span data-ttu-id="b5516-123">Upozorní profileru, že se chystá návrat funkce k volajícímu a poskytuje informace o bloku zásobníku a návratové hodnotě funkce.</span><span class="sxs-lookup"><span data-stu-id="b5516-123">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span> <span data-ttu-id="b5516-124">Zastaralé v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b5516-124">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="b5516-125">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-125">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)  
 <span data-ttu-id="b5516-126">Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce a poskytuje informace o bloku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b5516-126">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span> <span data-ttu-id="b5516-127">Zastaralé v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b5516-127">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="b5516-128">StackSnapshotCallback – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-128">StackSnapshotCallback Function</span></span>](stacksnapshotcallback-function.md)  
 <span data-ttu-id="b5516-129">Poskytuje Profiler s informacemi o každém spravovaném snímku a každém spuštění nespravovaných snímků v zásobníku během průchodu zásobníku, který je iniciován metodou [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b5516-129">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="net-framework-version-4-profiling-functions"></a><span data-ttu-id="b5516-130">Funkce profilování pro .NET Framework verze 4</span><span class="sxs-lookup"><span data-stu-id="b5516-130">.NET Framework version 4 Profiling Functions</span></span>  
 [<span data-ttu-id="b5516-131">FunctionIDMapper2 – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-131">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)  
 <span data-ttu-id="b5516-132">Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které se má použít v [FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md), nebo[Functionenter3withinfo –](functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](functionleave3withinfo-function.md)a zpětná volání [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md) pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="b5516-132">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="b5516-133">Také umožňuje profileru označit, zda chce přijímat zpětná volání této funkce.</span><span class="sxs-lookup"><span data-stu-id="b5516-133">Also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
 <span data-ttu-id="b5516-134">`FunctionIDMapper2` rozšiřuje funkci [FunctionIDMapper –](functionidmapper-function.md) s parametrem `clientData`, které profilery mohou použít k jednoznačnému rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="b5516-134">`FunctionIDMapper2` extends the [FunctionIDMapper](functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
 [<span data-ttu-id="b5516-135">FunctionEnter3 – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-135">FunctionEnter3 Function</span></span>](functionenter3-function.md)  
 <span data-ttu-id="b5516-136">Upozorňuje profileru, že řízení je předáno funkci.</span><span class="sxs-lookup"><span data-stu-id="b5516-136">Notifies the profiler that control is being passed to a function.</span></span>  
  
 [<span data-ttu-id="b5516-137">FunctionEnter3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-137">FunctionEnter3WithInfo Function</span></span>](functionenter3withinfo-function.md)  
 <span data-ttu-id="b5516-138">Upozorňuje profileru, že řízení je předáno funkci, a poskytuje popisovač, který může být předán do [ICorProfilerInfo3:: GetFunctionEnter3Info –](icorprofilerinfo3-getfunctionenter3info-method.md) za účelem načtení rámce zásobníku a argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="b5516-138">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
 [<span data-ttu-id="b5516-139">FunctionLeave3 – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-139">FunctionLeave3 Function</span></span>](functionleave3-function.md)  
 <span data-ttu-id="b5516-140">Upozorní profiler, že se vrací řízení z funkce.</span><span class="sxs-lookup"><span data-stu-id="b5516-140">Notifies the profiler that control is being returned from a function.</span></span>  
  
 [<span data-ttu-id="b5516-141">FunctionLeave3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-141">FunctionLeave3WithInfo Function</span></span>](functionleave3withinfo-function.md)  
 <span data-ttu-id="b5516-142">Upozorní profiler, že je vrácen ovládací prvek z funkce, a poskytuje popisovač, který může být předán do [ICorProfilerInfo3:: GetFunctionLeave3Info –](icorprofilerinfo3-getfunctionleave3info-method.md) , aby získal rámec zásobníku a vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b5516-142">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
 [<span data-ttu-id="b5516-143">FunctionTailcall3 – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-143">FunctionTailcall3 Function</span></span>](functiontailcall3-function.md)  
 <span data-ttu-id="b5516-144">Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce.</span><span class="sxs-lookup"><span data-stu-id="b5516-144">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
 [<span data-ttu-id="b5516-145">FunctionTailcall3WithInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="b5516-145">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)  
 <span data-ttu-id="b5516-146">Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce a poskytuje popisovač, který může být předán do [ICorProfilerInfo3:: GetFunctionTailcall3Info –](icorprofilerinfo3-getfunctiontailcall3info-method.md) , aby mohl načíst rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b5516-146">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b5516-147">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b5516-147">Related Sections</span></span>  
 [<span data-ttu-id="b5516-148">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="b5516-148">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="b5516-149">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b5516-149">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="b5516-150">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b5516-150">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="b5516-151">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b5516-151">Profiling Structures</span></span>](profiling-structures.md)
