---
title: Profilace výčtů
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: 1a9781fa1b4b608152faa7d5edc80bd4866f0c81
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868132"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="d4324-102">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="d4324-102">Profiling Enumerations</span></span>
<span data-ttu-id="d4324-103">Tato část popisuje nespravované výčty, které používá profilování API.</span><span class="sxs-lookup"><span data-stu-id="d4324-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4324-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d4324-104">In This Section</span></span>  
 [<span data-ttu-id="d4324-105">COR_PRF_CLAUSE_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="d4324-106">Určuje typ klauzule Exception, kterou kód právě zadal, nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="d4324-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="d4324-107">COR_PRF_CODEGEN_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="d4324-108">Definuje příznaky generování kódu, které lze nastavit pomocí metody [ICorProfilerFunctionControl:: SetCodegenFlags –](icorprofilerfunctioncontrol-setcodegenflags-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d4324-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="d4324-109">COR_PRF_FINALIZER_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="d4324-110">Popisuje finalizační metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="d4324-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="d4324-111">COR_PRF_GC_GENERATION – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-111">COR_PRF_GC_GENERATION Enumeration</span></span>](cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="d4324-112">Identifikuje generování kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="d4324-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="d4324-113">COR_PRF_GC_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-113">COR_PRF_GC_REASON Enumeration</span></span>](cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="d4324-114">Označuje důvod, proč dochází k uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d4324-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="d4324-115">COR_PRF_GC_ROOT_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="d4324-116">Určuje vlastnosti kořene uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d4324-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="d4324-117">COR_PRF_GC_ROOT_KIND – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="d4324-118">Určuje druh kořene uvolňování paměti, který je vystavený zpětnému volání [ICorProfilerCallback2:: RootReferences2 –](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d4324-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="d4324-119">COR_PRF_HIGH_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="d4324-120">Poskytuje příznaky kromě těch, které se nacházejí v [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) výčtu, které může Profiler zadat do metody [ICorProfilerInfo5:: SetEventMask2 –](icorprofilerinfo5-seteventmask2-method.md) při načítání.</span><span class="sxs-lookup"><span data-stu-id="d4324-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="d4324-121">COR_PRF_JIT_CACHE – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-121">COR_PRF_JIT_CACHE Enumeration</span></span>](cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="d4324-122">Označuje výsledek hledání funkce uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d4324-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="d4324-123">COR_PRF_MISC – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-123">COR_PRF_MISC Enumeration</span></span>](cor-prf-misc-enumeration.md)  
 <span data-ttu-id="d4324-124">Obsahuje konstantní hodnoty, které určují speciální identifikátory.</span><span class="sxs-lookup"><span data-stu-id="d4324-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="d4324-125">COR_PRF_MODULE_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="d4324-126">Určuje vlastnosti modulu.</span><span class="sxs-lookup"><span data-stu-id="d4324-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="d4324-127">COR_PRF_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-127">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="d4324-128">Obsahuje hodnoty, které slouží k určení chování, schopností nebo událostí, ke kterým se chce Profiler přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="d4324-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="d4324-129">COR_PRF_RUNTIME_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="d4324-130">Obsahuje hodnoty, které označují verzi modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="d4324-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="d4324-131">COR_PRF_SNAPSHOT_INFO – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="d4324-132">Určuje, kolik dat se má zpětně předat snímku zásobníku v každém volání funkce `StackSnapshotCallback` profileru.</span><span class="sxs-lookup"><span data-stu-id="d4324-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="d4324-133">COR_PRF_STATIC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="d4324-134">Označuje, zda je pole statické, a pokud ano, statická kvalita, která se vztahuje na pole.</span><span class="sxs-lookup"><span data-stu-id="d4324-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="d4324-135">COR_PRF_SUSPEND_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="d4324-136">Označuje důvod, proč byl modul runtime pozastaven.</span><span class="sxs-lookup"><span data-stu-id="d4324-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="d4324-137">COR_PRF_TRANSITION_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="d4324-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="d4324-138">Označuje důvod přechodu ze spravovaného do nespravovaného kódu nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="d4324-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d4324-139">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d4324-139">Related Sections</span></span>  
 [<span data-ttu-id="d4324-140">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="d4324-140">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="d4324-141">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d4324-141">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="d4324-142">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d4324-142">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="d4324-143">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d4324-143">Profiling Structures</span></span>](profiling-structures.md)
