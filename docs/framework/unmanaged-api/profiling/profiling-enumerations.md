---
title: "Profilace výčtů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84ac67b35bdbf686edb2fa35cc651aad4c19516b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-enumerations"></a><span data-ttu-id="52451-102">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="52451-102">Profiling Enumerations</span></span>
<span data-ttu-id="52451-103">Tato část popisuje nespravovaná vyčíslení, které používá profilaci API.</span><span class="sxs-lookup"><span data-stu-id="52451-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52451-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="52451-104">In This Section</span></span>  
 [<span data-ttu-id="52451-105">COR_PRF_CLAUSE_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="52451-106">Určuje typ výjimky klauzuli, který právě zadán kód nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="52451-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="52451-107">COR_PRF_CODEGEN_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="52451-108">Definuje příznaky generování kódu, které lze nastavit pomocí [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="52451-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="52451-109">COR_PRF_FINALIZER_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="52451-110">Popisuje finalizační metodu pro objekt.</span><span class="sxs-lookup"><span data-stu-id="52451-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="52451-111">COR_PRF_GC_GENERATION – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="52451-112">Určuje kolekci generace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="52451-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="52451-113">COR_PRF_GC_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="52451-114">Určuje, z důvodu probíhající uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="52451-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="52451-115">COR_PRF_GC_ROOT_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="52451-116">Určuje vlastnosti root systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="52451-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="52451-117">COR_PRF_GC_ROOT_KIND – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="52451-118">Určuje druh kořenové systém uvolňování paměti, který je zveřejněný prostřednictvím [icorprofilercallback2::rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="52451-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="52451-119">COR_PRF_HIGH_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="52451-120">Poskytuje příznaky kromě těch, které v nalezen [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet, který můžete vybrat profileru [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda při jeho načítání.</span><span class="sxs-lookup"><span data-stu-id="52451-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="52451-121">COR_PRF_JIT_CACHE – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="52451-122">Určuje výsledky hledání v mezipaměti funkce.</span><span class="sxs-lookup"><span data-stu-id="52451-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="52451-123">COR_PRF_MISC – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="52451-124">Obsahuje konstantní hodnoty, které určují speciální identifikátory.</span><span class="sxs-lookup"><span data-stu-id="52451-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="52451-125">COR_PRF_MODULE_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="52451-126">Určuje vlastnosti modulu.</span><span class="sxs-lookup"><span data-stu-id="52451-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="52451-127">COR_PRF_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="52451-128">Obsahuje hodnoty, které se používají k určení chování, možnosti nebo události, u kterých chce profileru přihlášení k odběru.</span><span class="sxs-lookup"><span data-stu-id="52451-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="52451-129">COR_PRF_RUNTIME_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="52451-130">Obsahuje hodnoty, které označují verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="52451-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="52451-131">COR_PRF_SNAPSHOT_INFO – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="52451-132">Určuje, kolik zpět předání dat s více snímků při každém volání do okna profilování `StackSnapshotCallback` funkce.</span><span class="sxs-lookup"><span data-stu-id="52451-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="52451-133">COR_PRF_STATIC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="52451-134">Určuje, jestli je statická pole a pokud ano, statické kvality, která platí pro pole.</span><span class="sxs-lookup"><span data-stu-id="52451-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="52451-135">COR_PRF_SUSPEND_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="52451-136">Určuje, z důvodu, že byl pozastaven modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="52451-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="52451-137">COR_PRF_TRANSITION_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="52451-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="52451-138">Označuje důvod pro přechod ze spravovaného na nespravovaný kód nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="52451-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52451-139">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="52451-139">Related Sections</span></span>  
 [<span data-ttu-id="52451-140">Přehled profilace</span><span class="sxs-lookup"><span data-stu-id="52451-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="52451-141">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="52451-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="52451-142">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="52451-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="52451-143">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="52451-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
