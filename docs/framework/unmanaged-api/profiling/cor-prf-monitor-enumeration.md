---
title: COR_PRF_MONITOR – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
ms.openlocfilehash: 2d7984ce109fb2bac5a36ab5e4c83f386de5a488
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867097"
---
# <a name="cor_prf_monitor-enumeration"></a><span data-ttu-id="60bfb-102">COR_PRF_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="60bfb-102">COR_PRF_MONITOR Enumeration</span></span>
<span data-ttu-id="60bfb-103">Obsahuje hodnoty, které slouží k určení chování, schopností nebo událostí, ke kterým se chce Profiler přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="60bfb-103">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60bfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60bfb-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |   
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |   
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="60bfb-105">Členové</span><span class="sxs-lookup"><span data-stu-id="60bfb-105">Members</span></span>  
 <span data-ttu-id="60bfb-106">Následující části uvádějí `COR_PRF_MONITOR` členů výčtu podle kategorie.</span><span class="sxs-lookup"><span data-stu-id="60bfb-106">The following sections list `COR_PRF_MONITOR` enumeration members by category.</span></span> <span data-ttu-id="60bfb-107">Kategorie jsou:</span><span class="sxs-lookup"><span data-stu-id="60bfb-107">The categories are:</span></span>  
  
- [<span data-ttu-id="60bfb-108">Nejsou nastavené žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="60bfb-108">No flags set</span></span>](#None)  
  
- [<span data-ttu-id="60bfb-109">Příznaky zpětného volání</span><span class="sxs-lookup"><span data-stu-id="60bfb-109">Callback flags</span></span>](#Callback)  
  
- [<span data-ttu-id="60bfb-110">Funkce – aktivace příznaků</span><span class="sxs-lookup"><span data-stu-id="60bfb-110">Feature-enabling flags</span></span>](#Feature)  
  
- [<span data-ttu-id="60bfb-111">Příznaky konfigurace</span><span class="sxs-lookup"><span data-stu-id="60bfb-111">Configuration flags</span></span>](#Config)  
  
- [<span data-ttu-id="60bfb-112">Složené příznaky</span><span class="sxs-lookup"><span data-stu-id="60bfb-112">Composite flags</span></span>](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a><span data-ttu-id="60bfb-113">Nejsou nastavené žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="60bfb-113">No flags set</span></span>  
  
|<span data-ttu-id="60bfb-114">Člen</span><span class="sxs-lookup"><span data-stu-id="60bfb-114">Member</span></span>|<span data-ttu-id="60bfb-115">Popis</span><span class="sxs-lookup"><span data-stu-id="60bfb-115">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|<span data-ttu-id="60bfb-116">Nejsou nastavené žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="60bfb-116">No flags are set.</span></span>|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a><span data-ttu-id="60bfb-117">Příznaky zpětného volání</span><span class="sxs-lookup"><span data-stu-id="60bfb-117">Callback flags</span></span>  
  
|<span data-ttu-id="60bfb-118">Člen</span><span class="sxs-lookup"><span data-stu-id="60bfb-118">Member</span></span>|<span data-ttu-id="60bfb-119">Popis</span><span class="sxs-lookup"><span data-stu-id="60bfb-119">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="60bfb-120">Povolí všechny události zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="60bfb-120">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|<span data-ttu-id="60bfb-121">Řídí `AppDomainCreation*` a `AppDomainShutdown*` zpětná volání v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-121">Controls the `AppDomainCreation*` and `AppDomainShutdown*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|<span data-ttu-id="60bfb-122">Řídí `AssemblyLoad*` a `AssemblyUnload*` zpětná volání v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-122">Controls the `AssemblyLoad*` and `AssemblyUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|<span data-ttu-id="60bfb-123">Řídí zpětná volání `JITCachedFunctionSearch*` v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-123">Controls the `JITCachedFunctionSearch*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span><br /><br /> <span data-ttu-id="60bfb-124">Chování tohoto příznaku se změní v .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="60bfb-124">The behavior of this flag is changed in the .NET Framework version 2.0.</span></span>|  
|`COR_PRF_MONITOR_CCW`|<span data-ttu-id="60bfb-125">Řídí zpětná volání `COMClassicVTable*` v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-125">Controls the `COMClassicVTable*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLASS_LOADS`|<span data-ttu-id="60bfb-126">Řídí `ClassLoad*` a `ClassUnload*` zpětná volání v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-126">Controls the `ClassLoad*` and `ClassUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|<span data-ttu-id="60bfb-127">Řídí zpětná volání `ExceptionCLRCatcher*` v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-127">Controls the `ExceptionCLRCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|<span data-ttu-id="60bfb-128">Řídí zpětná volání [UnmanagedToManagedTransition –](icorprofilercallback-unmanagedtomanagedtransition-method.md) a [ManagedToUnmanagedTransition –](icorprofilercallback-managedtounmanagedtransition-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-128">Controls the [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) and [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface</span></span>|  
|`COR_PRF_MONITOR_ENTERLEAVE`|<span data-ttu-id="60bfb-129">Řídí [globální statické funkce profilace](profiling-global-static-functions.md)`FunctionEnter*`, `FunctionLeave*`a `FunctionTailCall*`.</span><span class="sxs-lookup"><span data-stu-id="60bfb-129">Controls the `FunctionEnter*`,  `FunctionLeave*`, and `FunctionTailCall*`[profiling global static functions](profiling-global-static-functions.md).</span></span>|  
|`COR_PRF_MONITOR_EXCEPTIONS`|<span data-ttu-id="60bfb-130">Řídí zpětné volání [exceptionthrown –](icorprofilercallback-exceptionthrown-method.md) a `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`a `ExceptionCatcher*` zpětných volání v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-130">Controls the [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) callback and the `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, and `ExceptionCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|<span data-ttu-id="60bfb-131">Řídí zpětné volání [functionunloadstarted –](icorprofilercallback-functionunloadstarted-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-131">Controls the [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_GC`|<span data-ttu-id="60bfb-132">Řídí [GarbageCollectionStarted –](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences –](icorprofilercallback-movedreferences-method.md), [MovedReferences2 –](icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences –](icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2 –](icorprofilercallback4-survivingreferences2-method.md), [objectReferences –](icorprofilercallback-objectreferences-method.md), [objectsallocatedbyclass –](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences –](icorprofilercallback-rootreferences-method.md), [RootReferences2 –](icorprofilercallback2-rootreferences2-method.md), [HandleCreated –](icorprofilercallback2-handlecreated-method.md), [HandleDestroyed –](icorprofilercallback2-handledestroyed-method.md)a zpětná volání [FinalizeableObjectQueued –](icorprofilercallback2-finalizeableobjectqueued-method.md) v rozhraních `ICorProfilerCallback*`.</span><span class="sxs-lookup"><span data-stu-id="60bfb-132">Controls the [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md),   [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md),  [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md),    [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md),  [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md),   [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md),  [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md),  [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md), and [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) callbacks in the `ICorProfilerCallback*` interfaces.</span></span> <span data-ttu-id="60bfb-133">Při přidělení `COR_PRF_MONITOR_GC` je souběžné uvolňování paměti vypnuto.</span><span class="sxs-lookup"><span data-stu-id="60bfb-133">When `COR_PRF_MONITOR_GC` is allocated, concurrent garbage collection is turned off.</span></span>|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|<span data-ttu-id="60bfb-134">Řídí zpětná volání `JITCompilation*`, [jitfunctionpitched –](icorprofilercallback-jitfunctionpitched-method.md)a [JITInlining –](icorprofilercallback-jitinlining-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-134">Controls the `JITCompilation*`, [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md), and [JITInlining](icorprofilercallback-jitinlining-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_MODULE_LOADS`|<span data-ttu-id="60bfb-135">Řídí `ModuleLoad*`, `ModuleUnload*`a zpětná volání [ModuleAttachedToAssembly –](icorprofilercallback-moduleattachedtoassembly-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-135">Controls the `ModuleLoad*`,  `ModuleUnload*`, and [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|<span data-ttu-id="60bfb-136">Řídí zpětné volání [ObjectAllocated –](icorprofilercallback-objectallocated-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-136">Controls the [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING`|<span data-ttu-id="60bfb-137">Řídí zpětná volání `Remoting*` v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-137">Controls the `Remoting*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|<span data-ttu-id="60bfb-138">Určuje, zda `Remoting*` zpětná volání budou monitorovat asynchronní události.</span><span class="sxs-lookup"><span data-stu-id="60bfb-138">Controls whether the `Remoting*` callbacks will monitor asynchronous events.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|<span data-ttu-id="60bfb-139">Určuje, zda je soubor cookie předán `Remoting*`ovým zpětným voláním.</span><span class="sxs-lookup"><span data-stu-id="60bfb-139">Controls whether a cookie is passed to the `Remoting*` callbacks.</span></span>|  
|`COR_PRF_MONITOR_SUSPENDS`|<span data-ttu-id="60bfb-140">Řídí zpětná volání `RuntimeSuspend*`, `RuntimeResume*`, [runtimethreadsuspended –](icorprofilercallback-runtimethreadsuspended-method.md)a [Runtimethreadresumed –](icorprofilercallback-runtimethreadresumed-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-140">Controls the `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md), and [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_THREADS`|<span data-ttu-id="60bfb-141">Řídí zpětná volání [ThreadCreated –](icorprofilercallback-threadcreated-method.md), [ThreadDestroyed –](icorprofilercallback-threaddestroyed-method.md), [threadassignedtoosthread –](icorprofilercallback-threadassignedtoosthread-method.md)a [threadnamechanged –](icorprofilercallback2-threadnamechanged-method.md) v rozhraních [ICorProfilerCallback](icorprofilercallback-interface.md) a [ICorProfilerCallback2](icorprofilercallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-141">Controls the [ThreadCreated](icorprofilercallback-threadcreated-method.md),  [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md),  [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md), and [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) and [ICorProfilerCallback2](icorprofilercallback2-interface.md) interfaces.</span></span>|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a><span data-ttu-id="60bfb-142">Funkce – aktivace příznaků</span><span class="sxs-lookup"><span data-stu-id="60bfb-142">Feature-enabling flags</span></span>  
  
|<span data-ttu-id="60bfb-143">Člen</span><span class="sxs-lookup"><span data-stu-id="60bfb-143">Member</span></span>|<span data-ttu-id="60bfb-144">Popis</span><span class="sxs-lookup"><span data-stu-id="60bfb-144">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|<span data-ttu-id="60bfb-145">Umožňuje načtení přesného `ClassID` pro obecnou funkci voláním metody [GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) s hodnotou `COR_PRF_FRAME_INFO` vrácenou zpětným voláním [FunctionEnter2](functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-145">Enables the retrieval of an exact `ClassID` for a generic function by calling the [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method with a `COR_PRF_FRAME_INFO` value returned by the [FunctionEnter2](functionenter2-function.md) callback.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|<span data-ttu-id="60bfb-146">Povolí trasování argumentů pomocí zpětného volání [FunctionEnter2](functionenter2-function.md) nebo zpětného volání [Functionenter3withinfo –](functionenter3withinfo-function.md) a metody [GetFunctionEnter3Info –](icorprofilerinfo3-getfunctionenter3info-method.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-146">Enables argument tracing using the [FunctionEnter2](functionenter2-function.md) callback or the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) callback and the [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|<span data-ttu-id="60bfb-147">Umožňuje trasování vrácených hodnot pomocí zpětného volání [FunctionLeave2 –](functionleave2-function.md) nebo metody zpětného volání [FunctionLeave3WithInfo –](functionleave3withinfo-function.md) a [GetFunctionLeave3Info –](icorprofilerinfo3-getfunctionleave3info-method.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-147">Enables tracing of return values by using the [FunctionLeave2](functionleave2-function.md) callback or the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) callback and [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|<span data-ttu-id="60bfb-148">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="60bfb-148">Deprecated.</span></span><br /><br /> <span data-ttu-id="60bfb-149">V procesu ladění není podporováno.</span><span class="sxs-lookup"><span data-stu-id="60bfb-149">In process debugging is not supported.</span></span> <span data-ttu-id="60bfb-150">Tento příznak nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="60bfb-150">This flag has no effect.</span></span>|  
|`COR_PRF_ENABLE_JIT_MAPS`|<span data-ttu-id="60bfb-151">Zastaralé</span><span class="sxs-lookup"><span data-stu-id="60bfb-151">Deprecated.</span></span><br /><br /> <span data-ttu-id="60bfb-152">Umožňuje profileru získat pomocí [GetILToNativeMapping –](icorprofilerinfo-getiltonativemapping-method.md)mapy Il-to-Native.</span><span class="sxs-lookup"><span data-stu-id="60bfb-152">Allows the profiler to obtain IL-to-native maps by using [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md).</span></span> <span data-ttu-id="60bfb-153">Počínaje .NET Framework 2,0, modul runtime vždycky sleduje mapy IL-to-Native; Proto je tento příznak vždy považován za nastavený.</span><span class="sxs-lookup"><span data-stu-id="60bfb-153">Starting with the .NET Framework 2.0, the runtime always tracks IL-to-native maps; therefore, this flag is always considered to be set.</span></span>|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|<span data-ttu-id="60bfb-154">Informuje modul runtime o tom, že Profiler může chtít oznámení o přidělení objektů.</span><span class="sxs-lookup"><span data-stu-id="60bfb-154">Informs the runtime that the profiler may want object allocation notifications.</span></span> <span data-ttu-id="60bfb-155">Tento příznak musí být nastaven během inicializace.</span><span class="sxs-lookup"><span data-stu-id="60bfb-155">This flag must be set during initialization.</span></span> <span data-ttu-id="60bfb-156">Umožňuje profileru později použít příznak `COR_PRF_MONITOR_OBJECT_ALLOCATED` pro příjem zpětných volání [ObjectAllocated –](icorprofilercallback-objectallocated-method.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-156">It allows the profiler to subsequently use the `COR_PRF_MONITOR_OBJECT_ALLOCATED` flag to receive [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callbacks.</span></span>|  
|`COR_PRF_ENABLE_REJIT`|<span data-ttu-id="60bfb-157">Povoluje volání metod [RequestReJIT –](icorprofilerinfo4-requestrejit-method.md) a [RequestRevert –](icorprofilerinfo4-requestrevert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-157">Enables calls to the [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) and [RequestRevert](icorprofilerinfo4-requestrevert-method.md) methods.</span></span> <span data-ttu-id="60bfb-158">Profiler musí při spuštění tento příznak nastavit.</span><span class="sxs-lookup"><span data-stu-id="60bfb-158">The profiler must set this flag on startup.</span></span>  <span data-ttu-id="60bfb-159">Pokud profiler tento příznak určuje, musí také zadat `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span><span class="sxs-lookup"><span data-stu-id="60bfb-159">If the profiler specifies this flag, it must also specify `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span></span>|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|<span data-ttu-id="60bfb-160">Povoluje volání metody [DoStackSnapshot –](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="60bfb-160">Enables calls to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a><span data-ttu-id="60bfb-161">Příznaky konfigurace</span><span class="sxs-lookup"><span data-stu-id="60bfb-161">Configuration flags</span></span>  
  
|<span data-ttu-id="60bfb-162">Člen</span><span class="sxs-lookup"><span data-stu-id="60bfb-162">Member</span></span>|<span data-ttu-id="60bfb-163">Popis</span><span class="sxs-lookup"><span data-stu-id="60bfb-163">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|<span data-ttu-id="60bfb-164">Zabraňuje načtení všech nativních imagí (včetně imagí s rozšířeným profilerem).</span><span class="sxs-lookup"><span data-stu-id="60bfb-164">Prevents all native images (including profiler-enhanced images) from loading.</span></span>  <span data-ttu-id="60bfb-165">Je-li tento příznak a příznak `COR_PRF_USE_PROFILE_IMAGES` zadán, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` použito.</span><span class="sxs-lookup"><span data-stu-id="60bfb-165">If this flag and the `COR_PRF_USE_PROFILE_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
|`COR_PRF_DISABLE_INLINING`|<span data-ttu-id="60bfb-166">Zakáže veškeré vkládání.</span><span class="sxs-lookup"><span data-stu-id="60bfb-166">Disables all inlining.</span></span>|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|<span data-ttu-id="60bfb-167">Zakáže všechny optimalizace kódu.</span><span class="sxs-lookup"><span data-stu-id="60bfb-167">Disables all code optimizations.</span></span>|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|<span data-ttu-id="60bfb-168">Zakáže kontroly transparentnosti zabezpečení, které se obvykle provádějí během kompilace JIT (just-in-time) a načítání tříd pro sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="60bfb-168">Disables security transparency checks that are normally done during just-in-time (JIT) compilation and class loading for full-trust assemblies.</span></span> <span data-ttu-id="60bfb-169">Díky tomu je možné usnadnit provádění některých instrumentace.</span><span class="sxs-lookup"><span data-stu-id="60bfb-169">This can make some instrumentation easier to perform.</span></span>|  
|`COR_PRF_USE_PROFILE_IMAGES`|<span data-ttu-id="60bfb-170">Způsobí, že vyhledávání nativních imagí vyhledá obrázky vylepšené v profileru.</span><span class="sxs-lookup"><span data-stu-id="60bfb-170">Causes the native image search to look for profiler-enhanced images.</span></span> <span data-ttu-id="60bfb-171">Pokud se pro dané sestavení nenajde žádná image s rozšířeným profilerem, modul CLR (Common Language Runtime) přejde zpět na JIT pro toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="60bfb-171">If no profiler-enhanced image is found for a given assembly, the common language runtime falls back to JIT for that assembly.</span></span> <span data-ttu-id="60bfb-172">Je-li tento příznak a příznak `COR_PRF_DISABLE_ALL_NGEN_IMAGES` zadán, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` použito.</span><span class="sxs-lookup"><span data-stu-id="60bfb-172">If this flag and the `COR_PRF_DISABLE_ALL_NGEN_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a><span data-ttu-id="60bfb-173">Složené příznaky</span><span class="sxs-lookup"><span data-stu-id="60bfb-173">Composite flags</span></span>  
  
|<span data-ttu-id="60bfb-174">Člen</span><span class="sxs-lookup"><span data-stu-id="60bfb-174">Member</span></span>|<span data-ttu-id="60bfb-175">Popis</span><span class="sxs-lookup"><span data-stu-id="60bfb-175">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ALL`|<span data-ttu-id="60bfb-176">Představuje všechny hodnoty příznaků `COR_PRF_MONITOR`.</span><span class="sxs-lookup"><span data-stu-id="60bfb-176">Represents all `COR_PRF_MONITOR` flag values.</span></span>|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="60bfb-177">Představuje všechny příznaky `COR_PRF_MONITOR`, které lze nastavit po připojení profileru ke spuštěné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="60bfb-177">Represents all `COR_PRF_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span> <span data-ttu-id="60bfb-178">Oddíl syntax označuje jednotlivé příznaky, které jsou k dispozici v této maskování.</span><span class="sxs-lookup"><span data-stu-id="60bfb-178">The syntax section indicates the individual flags that are present in this bitmask.</span></span>|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="60bfb-179">Povolí všechny události zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="60bfb-179">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_IMMUTABLE`|<span data-ttu-id="60bfb-180">Představuje všechny příznaky `COR_PRF_MONITOR`, které lze nastavit pouze během inicializace.</span><span class="sxs-lookup"><span data-stu-id="60bfb-180">Represents all `COR_PRF_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="60bfb-181">Pokus o změnu některého z těchto příznaků po inicializaci vrátí `HRESULT` hodnotu, která označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="60bfb-181">Trying to change any of these flags after initialization returns an `HRESULT` value that indicates failure.</span></span>|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="60bfb-182">Představuje všechny příznaky `COR_PRF_MONITOR`, které vyžadují image s rozšířeným profilem.</span><span class="sxs-lookup"><span data-stu-id="60bfb-182">Represents all `COR_PRF_MONITOR` flags that require profile-enhanced images.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60bfb-183">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60bfb-183">Remarks</span></span>  
 <span data-ttu-id="60bfb-184">Hodnota `COR_PRF_MONITOR` se používá s metodami [ICorProfilerInfo:: GetEventMask –](icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) k definování oznámení události, které modul CLR (Common Language Runtime) provede v profileru.</span><span class="sxs-lookup"><span data-stu-id="60bfb-184">A `COR_PRF_MONITOR` value is used with the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods to define the event notifications that the common language runtime makes to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60bfb-185">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60bfb-185">Requirements</span></span>  
 <span data-ttu-id="60bfb-186">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60bfb-186">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60bfb-187">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="60bfb-187">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60bfb-188">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="60bfb-188">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60bfb-189">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60bfb-189">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60bfb-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60bfb-190">See also</span></span>

- [<span data-ttu-id="60bfb-191">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="60bfb-191">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="60bfb-192">GetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="60bfb-192">GetEventMask Method</span></span>](icorprofilerinfo-geteventmask-method.md)
- [<span data-ttu-id="60bfb-193">SetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="60bfb-193">SetEventMask Method</span></span>](icorprofilerinfo-seteventmask-method.md)
