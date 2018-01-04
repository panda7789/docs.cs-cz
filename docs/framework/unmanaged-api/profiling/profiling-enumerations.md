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
# <a name="profiling-enumerations"></a>Profilace výčtů
Tato část popisuje nespravovaná vyčíslení, které používá profilaci API.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [COR_PRF_CLAUSE_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Určuje typ výjimky klauzuli, který právě zadán kód nebo doleva.  
  
 [COR_PRF_CODEGEN_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 Definuje příznaky generování kódu, které lze nastavit pomocí [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metoda.  
  
 [COR_PRF_FINALIZER_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 Popisuje finalizační metodu pro objekt.  
  
 [COR_PRF_GC_GENERATION – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Určuje kolekci generace uvolňování paměti.  
  
 [COR_PRF_GC_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Určuje, z důvodu probíhající uvolňování paměti.  
  
 [COR_PRF_GC_ROOT_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Určuje vlastnosti root systém uvolňování paměti.  
  
 [COR_PRF_GC_ROOT_KIND – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 Určuje druh kořenové systém uvolňování paměti, který je zveřejněný prostřednictvím [icorprofilercallback2::rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) zpětného volání.  
  
 [COR_PRF_HIGH_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 Poskytuje příznaky kromě těch, které v nalezen [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet, který můžete vybrat profileru [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda při jeho načítání.  
  
 [COR_PRF_JIT_CACHE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Určuje výsledky hledání v mezipaměti funkce.  
  
 [COR_PRF_MISC – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Obsahuje konstantní hodnoty, které určují speciální identifikátory.  
  
 [COR_PRF_MODULE_FLAGS – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Určuje vlastnosti modulu.  
  
 [COR_PRF_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Obsahuje hodnoty, které se používají k určení chování, možnosti nebo události, u kterých chce profileru přihlášení k odběru.  
  
 [COR_PRF_RUNTIME_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Obsahuje hodnoty, které označují verzi modulu CLR.  
  
 [COR_PRF_SNAPSHOT_INFO – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Určuje, kolik zpět předání dat s více snímků při každém volání do okna profilování `StackSnapshotCallback` funkce.  
  
 [COR_PRF_STATIC_TYPE – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Určuje, jestli je statická pole a pokud ano, statické kvality, která platí pro pole.  
  
 [COR_PRF_SUSPEND_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Určuje, z důvodu, že byl pozastaven modulem runtime.  
  
 [COR_PRF_TRANSITION_REASON – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Označuje důvod pro přechod ze spravovaného na nespravovaný kód nebo naopak.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
