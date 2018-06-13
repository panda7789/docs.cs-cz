---
title: Profilace výčtů
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 996352637f34b0b6c0d12e611a6d9e70ab85230e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461757"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="4beab-102">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="4beab-102">Profiling Enumerations</span></span>
<span data-ttu-id="4beab-103">Tato část popisuje nespravovaná vyčíslení, které používá profilaci API.</span><span class="sxs-lookup"><span data-stu-id="4beab-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4beab-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4beab-104">In This Section</span></span>  
 [<span data-ttu-id="4beab-105">COR_PRF_CLAUSE_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="4beab-106">Určuje typ výjimky klauzuli, který právě zadán kód nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="4beab-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="4beab-107">COR_PRF_CODEGEN_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="4beab-108">Definuje příznaky generování kódu, které lze nastavit pomocí [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="4beab-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="4beab-109">COR_PRF_FINALIZER_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="4beab-110">Popisuje finalizační metodu pro objekt.</span><span class="sxs-lookup"><span data-stu-id="4beab-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="4beab-111">COR_PRF_GC_GENERATION – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="4beab-112">Určuje kolekci generace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4beab-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="4beab-113">COR_PRF_GC_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="4beab-114">Určuje, z důvodu probíhající uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4beab-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="4beab-115">COR_PRF_GC_ROOT_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="4beab-116">Určuje vlastnosti root systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4beab-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="4beab-117">COR_PRF_GC_ROOT_KIND – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="4beab-118">Určuje druh kořenové systém uvolňování paměti, který je zveřejněný prostřednictvím [icorprofilercallback2::rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="4beab-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="4beab-119">COR_PRF_HIGH_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="4beab-120">Poskytuje příznaky kromě těch, které v nalezen [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet, který můžete vybrat profileru [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda při jeho načítání.</span><span class="sxs-lookup"><span data-stu-id="4beab-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="4beab-121">COR_PRF_JIT_CACHE – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="4beab-122">Určuje výsledky hledání v mezipaměti funkce.</span><span class="sxs-lookup"><span data-stu-id="4beab-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="4beab-123">COR_PRF_MISC – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="4beab-124">Obsahuje konstantní hodnoty, které určují speciální identifikátory.</span><span class="sxs-lookup"><span data-stu-id="4beab-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="4beab-125">COR_PRF_MODULE_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="4beab-126">Určuje vlastnosti modulu.</span><span class="sxs-lookup"><span data-stu-id="4beab-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="4beab-127">COR_PRF_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="4beab-128">Obsahuje hodnoty, které se používají k určení chování, možnosti nebo události, u kterých chce profileru přihlášení k odběru.</span><span class="sxs-lookup"><span data-stu-id="4beab-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="4beab-129">COR_PRF_RUNTIME_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="4beab-130">Obsahuje hodnoty, které označují verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="4beab-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="4beab-131">COR_PRF_SNAPSHOT_INFO – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="4beab-132">Určuje, kolik zpět předání dat s více snímků při každém volání do okna profilování `StackSnapshotCallback` funkce.</span><span class="sxs-lookup"><span data-stu-id="4beab-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="4beab-133">COR_PRF_STATIC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="4beab-134">Určuje, jestli je statická pole a pokud ano, statické kvality, která platí pro pole.</span><span class="sxs-lookup"><span data-stu-id="4beab-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="4beab-135">COR_PRF_SUSPEND_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="4beab-136">Určuje, z důvodu, že byl pozastaven modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="4beab-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="4beab-137">COR_PRF_TRANSITION_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="4beab-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="4beab-138">Označuje důvod pro přechod ze spravovaného na nespravovaný kód nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="4beab-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4beab-139">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4beab-139">Related Sections</span></span>  
 [<span data-ttu-id="4beab-140">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="4beab-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="4beab-141">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4beab-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="4beab-142">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4beab-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="4beab-143">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4beab-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
