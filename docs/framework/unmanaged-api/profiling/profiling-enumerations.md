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
# <a name="profiling-enumerations"></a>Profilace výčtů
Tato část popisuje nespravované výčty, které používá profilování API.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [COR_PRF_CLAUSE_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Určuje typ výjimky klauzuli, která je právě zadali kód nebo doleva.  
  
 [COR_PRF_CODEGEN_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 Definuje příznaky generování kódu, které lze nastavit [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metody.  
  
 [COR_PRF_FINALIZER_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 Popisuje finalizační metodu objektu.  
  
 [COR_PRF_GC_GENERATION – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Identifikuje generaci uvolňování paměti.  
  
 [COR_PRF_GC_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Označuje, že uvolňování paměti dochází důvod.  
  
 [COR_PRF_GC_ROOT_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Určuje vlastnosti root systému uvolňování paměti.  
  
 [COR_PRF_GC_ROOT_KIND – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 Označuje druh kořenové systému uvolňování paměti, který je zveřejněný prostřednictvím [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) zpětného volání.  
  
 [COR_PRF_HIGH_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 Poskytuje příznaky kromě v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet, který lze vybrat profiler [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda při jeho načítání.  
  
 [COR_PRF_JIT_CACHE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Určuje výsledky hledání funkce uložené v mezipaměti.  
  
 [COR_PRF_MISC – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Obsahuje konstantní hodnoty, které určují speciální identifikátory.  
  
 [COR_PRF_MODULE_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Určuje vlastnosti modulu.  
  
 [COR_PRF_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Obsahuje hodnoty, které se používají k určení chování, funkce nebo události, ke kterým profileru chce odběru.  
  
 [COR_PRF_RUNTIME_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Obsahuje hodnoty, které označují verzi modulu common language runtime.  
  
 [COR_PRF_SNAPSHOT_INFO – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Určuje, kolik předání dat zpět se zásobník snímků v každé volání profileru `StackSnapshotCallback` funkce.  
  
 [COR_PRF_STATIC_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Určuje, jestli je statická pole, a pokud ano, statické kvality platí pro pole.  
  
 [COR_PRF_SUSPEND_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Označuje, že byl pozastaven modulem důvod.  
  
 [COR_PRF_TRANSITION_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Označuje důvod pro přechod ze spravovaného do nespravovaného kódu a naopak.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
