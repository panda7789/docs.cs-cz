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
# <a name="profiling-enumerations"></a>Profilace výčtů
Tato část popisuje nespravované výčty, které používá profilování API.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [COR_PRF_CLAUSE_TYPE – výčet](cor-prf-clause-type-enumeration.md)  
 Určuje typ klauzule Exception, kterou kód právě zadal, nebo doleva.  
  
 [COR_PRF_CODEGEN_FLAGS – výčet](cor-prf-codegen-flags-enumeration.md)  
 Definuje příznaky generování kódu, které lze nastavit pomocí metody [ICorProfilerFunctionControl:: SetCodegenFlags –](icorprofilerfunctioncontrol-setcodegenflags-method.md) .  
  
 [COR_PRF_FINALIZER_FLAGS – výčet](cor-prf-finalizer-flags-enumeration.md)  
 Popisuje finalizační metodu objektu.  
  
 [COR_PRF_GC_GENERATION – výčet](cor-prf-gc-generation-enumeration.md)  
 Identifikuje generování kolekce paměti.  
  
 [COR_PRF_GC_REASON – výčet](cor-prf-gc-reason-enumeration.md)  
 Označuje důvod, proč dochází k uvolňování paměti.  
  
 [COR_PRF_GC_ROOT_FLAGS – výčet](cor-prf-gc-root-flags-enumeration.md)  
 Určuje vlastnosti kořene uvolňování paměti.  
  
 [COR_PRF_GC_ROOT_KIND – výčet](cor-prf-gc-root-kind-enumeration.md)  
 Určuje druh kořene uvolňování paměti, který je vystavený zpětnému volání [ICorProfilerCallback2:: RootReferences2 –](icorprofilercallback2-rootreferences2-method.md) .  
  
 [COR_PRF_HIGH_MONITOR – výčet](cor-prf-high-monitor-enumeration.md)  
 Poskytuje příznaky kromě těch, které se nacházejí v [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) výčtu, které může Profiler zadat do metody [ICorProfilerInfo5:: SetEventMask2 –](icorprofilerinfo5-seteventmask2-method.md) při načítání.  
  
 [COR_PRF_JIT_CACHE – výčet](cor-prf-jit-cache-enumeration.md)  
 Označuje výsledek hledání funkce uložené v mezipaměti.  
  
 [COR_PRF_MISC – výčet](cor-prf-misc-enumeration.md)  
 Obsahuje konstantní hodnoty, které určují speciální identifikátory.  
  
 [COR_PRF_MODULE_FLAGS – výčet](cor-prf-module-flags-enumeration.md)  
 Určuje vlastnosti modulu.  
  
 [COR_PRF_MONITOR – výčet](cor-prf-monitor-enumeration.md)  
 Obsahuje hodnoty, které slouží k určení chování, schopností nebo událostí, ke kterým se chce Profiler přihlásit k odběru.  
  
 [COR_PRF_RUNTIME_TYPE – výčet](cor-prf-runtime-type-enumeration.md)  
 Obsahuje hodnoty, které označují verzi modulu CLR (Common Language Runtime).  
  
 [COR_PRF_SNAPSHOT_INFO – výčet](cor-prf-snapshot-info-enumeration.md)  
 Určuje, kolik dat se má zpětně předat snímku zásobníku v každém volání funkce `StackSnapshotCallback` profileru.  
  
 [COR_PRF_STATIC_TYPE – výčet](cor-prf-static-type-enumeration.md)  
 Označuje, zda je pole statické, a pokud ano, statická kvalita, která se vztahuje na pole.  
  
 [COR_PRF_SUSPEND_REASON – výčet](cor-prf-suspend-reason-enumeration.md)  
 Označuje důvod, proč byl modul runtime pozastaven.  
  
 [COR_PRF_TRANSITION_REASON – výčet](cor-prf-transition-reason-enumeration.md)  
 Označuje důvod přechodu ze spravovaného do nespravovaného kódu nebo naopak.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](profiling-overview.md)  
  
 [Rozhraní pro profilaci](profiling-interfaces.md)  
  
 [Globální statické funkce pro profilaci](profiling-global-static-functions.md)  
  
 [Struktury pro profilaci](profiling-structures.md)
