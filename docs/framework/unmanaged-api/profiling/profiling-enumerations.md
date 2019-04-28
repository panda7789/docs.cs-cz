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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757570"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="111e4-102">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="111e4-102">Profiling Enumerations</span></span>
<span data-ttu-id="111e4-103">Tato část popisuje nespravované výčty, které používá profilování API.</span><span class="sxs-lookup"><span data-stu-id="111e4-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="111e4-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="111e4-104">In This Section</span></span>  
 [<span data-ttu-id="111e4-105">COR_PRF_CLAUSE_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="111e4-106">Určuje typ výjimky klauzuli, která je právě zadali kód nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="111e4-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="111e4-107">COR_PRF_CODEGEN_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="111e4-108">Definuje příznaky generování kódu, které lze nastavit [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="111e4-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="111e4-109">COR_PRF_FINALIZER_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="111e4-110">Popisuje finalizační metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="111e4-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="111e4-111">COR_PRF_GC_GENERATION – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="111e4-112">Identifikuje generaci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="111e4-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="111e4-113">COR_PRF_GC_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="111e4-114">Označuje, že uvolňování paměti dochází důvod.</span><span class="sxs-lookup"><span data-stu-id="111e4-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="111e4-115">COR_PRF_GC_ROOT_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="111e4-116">Určuje vlastnosti root systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="111e4-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="111e4-117">COR_PRF_GC_ROOT_KIND – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="111e4-118">Označuje druh kořenové systému uvolňování paměti, který je zveřejněný prostřednictvím [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="111e4-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="111e4-119">COR_PRF_HIGH_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="111e4-120">Poskytuje příznaky kromě v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet, který lze vybrat profiler [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda při jeho načítání.</span><span class="sxs-lookup"><span data-stu-id="111e4-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="111e4-121">COR_PRF_JIT_CACHE – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="111e4-122">Určuje výsledky hledání funkce uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="111e4-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="111e4-123">COR_PRF_MISC – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="111e4-124">Obsahuje konstantní hodnoty, které určují speciální identifikátory.</span><span class="sxs-lookup"><span data-stu-id="111e4-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="111e4-125">COR_PRF_MODULE_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="111e4-126">Určuje vlastnosti modulu.</span><span class="sxs-lookup"><span data-stu-id="111e4-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="111e4-127">COR_PRF_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="111e4-128">Obsahuje hodnoty, které se používají k určení chování, funkce nebo události, ke kterým profileru chce odběru.</span><span class="sxs-lookup"><span data-stu-id="111e4-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="111e4-129">COR_PRF_RUNTIME_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="111e4-130">Obsahuje hodnoty, které označují verzi modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="111e4-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="111e4-131">COR_PRF_SNAPSHOT_INFO – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="111e4-132">Určuje, kolik předání dat zpět se zásobník snímků v každé volání profileru `StackSnapshotCallback` funkce.</span><span class="sxs-lookup"><span data-stu-id="111e4-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="111e4-133">COR_PRF_STATIC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="111e4-134">Určuje, jestli je statická pole, a pokud ano, statické kvality platí pro pole.</span><span class="sxs-lookup"><span data-stu-id="111e4-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="111e4-135">COR_PRF_SUSPEND_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="111e4-136">Označuje, že byl pozastaven modulem důvod.</span><span class="sxs-lookup"><span data-stu-id="111e4-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="111e4-137">COR_PRF_TRANSITION_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="111e4-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="111e4-138">Označuje důvod pro přechod ze spravovaného do nespravovaného kódu a naopak.</span><span class="sxs-lookup"><span data-stu-id="111e4-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="111e4-139">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="111e4-139">Related Sections</span></span>  
 [<span data-ttu-id="111e4-140">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="111e4-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="111e4-141">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="111e4-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="111e4-142">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="111e4-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="111e4-143">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="111e4-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
