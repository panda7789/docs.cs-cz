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
Tato část popisuje nespravované výčty, které používá profilování API.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [COR_PRF_CLAUSE_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Určuje typ klauzule Exception, kterou kód právě zadal, nebo doleva.  
  
 [COR_PRF_CODEGEN_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 Definuje příznaky generování kódu, které lze nastavit pomocí metody [ICorProfilerFunctionControl:: SetCodegenFlags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) .  
  
 [COR_PRF_FINALIZER_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 Popisuje finalizační metodu objektu.  
  
 [COR_PRF_GC_GENERATION – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Identifikuje generování kolekce paměti.  
  
 [COR_PRF_GC_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Označuje důvod, proč dochází k uvolňování paměti.  
  
 [COR_PRF_GC_ROOT_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Určuje vlastnosti kořene uvolňování paměti.  
  
 [COR_PRF_GC_ROOT_KIND – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 Určuje druh kořene uvolňování paměti, který je vystavený zpětnému volání [ICorProfilerCallback2:: RootReferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) .  
  
 [COR_PRF_HIGH_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 Poskytuje příznaky kromě těch, které se nacházejí v [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu, které může Profiler zadat do metody [ICorProfilerInfo5:: SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) při načítání.  
  
 [COR_PRF_JIT_CACHE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Označuje výsledek hledání funkce uložené v mezipaměti.  
  
 [COR_PRF_MISC – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Obsahuje konstantní hodnoty, které určují speciální identifikátory.  
  
 [COR_PRF_MODULE_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Určuje vlastnosti modulu.  
  
 [COR_PRF_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Obsahuje hodnoty, které slouží k určení chování, schopností nebo událostí, ke kterým se chce Profiler přihlásit k odběru.  
  
 [COR_PRF_RUNTIME_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Obsahuje hodnoty, které označují verzi modulu CLR (Common Language Runtime).  
  
 [COR_PRF_SNAPSHOT_INFO – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Určuje, kolik dat se má zpětně předat snímku zásobníku v každém volání funkce `StackSnapshotCallback` profileru.  
  
 [COR_PRF_STATIC_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Označuje, zda je pole statické, a pokud ano, statická kvalita, která se vztahuje na pole.  
  
 [COR_PRF_SUSPEND_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Označuje důvod, proč byl modul runtime pozastaven.  
  
 [COR_PRF_TRANSITION_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Označuje důvod přechodu ze spravovaného do nespravovaného kódu nebo naopak.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
