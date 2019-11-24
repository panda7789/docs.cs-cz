---
title: Profilace výčtů
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: bc90743fb348c31bd2f7487c1573ec38a43bd3af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447444"
---
# <a name="profiling-enumerations"></a>Profilace výčtů
This section describes the unmanaged enumerations that the profiling API uses.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [COR_PRF_CLAUSE_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Indicates the type of exception clause that the code has just entered or left.  
  
 [COR_PRF_CODEGEN_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.  
  
 [COR_PRF_FINALIZER_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 Describes the finalizer for an object.  
  
 [COR_PRF_GC_GENERATION – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Identifies a garbage collection generation.  
  
 [COR_PRF_GC_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Indicates the reason that garbage collection is occurring.  
  
 [COR_PRF_GC_ROOT_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Indicates properties of a garbage collector root.  
  
 [COR_PRF_GC_ROOT_KIND – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.  
  
 [COR_PRF_HIGH_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.  
  
 [COR_PRF_JIT_CACHE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Indicates the result of a cached function search.  
  
 [COR_PRF_MISC – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Contains constant values that specify special identifiers.  
  
 [COR_PRF_MODULE_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Specifies the properties of a module.  
  
 [COR_PRF_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.  
  
 [COR_PRF_RUNTIME_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Contains values that indicate the version of the common language runtime.  
  
 [COR_PRF_SNAPSHOT_INFO – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.  
  
 [COR_PRF_STATIC_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Indicates whether a field is static and, if so, the static quality that applies to the field.  
  
 [COR_PRF_SUSPEND_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Indicates the reason that the runtime was suspended.  
  
 [COR_PRF_TRANSITION_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Indicates the reason for a transition from managed to unmanaged code, or vice versa.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
