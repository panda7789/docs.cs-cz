---
title: Rozhraní pro profilaci
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: adc47417265d32d79508af949c118c4d31a83365
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124198"
---
# <a name="profiling-interfaces"></a>Rozhraní pro profilaci
Tato část popisuje nespravovaná rozhraní, která umožňují profilovat program, který je spuštěn modulem CLR (Common Language Runtime).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ICLRProfiling – rozhraní](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 Poskytuje metodu [AttachProfiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) , která umožňuje profileru připojit se k běžícímu procesu.  
  
 [ICorProfilerAssemblyReferenceProvider – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 Umožňuje profileru informovat modul CLR o odkazech na sestavení, které bude Profiler přidávat do zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .  
  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 Poskytuje metody, které používá modul CLR k oznamování profileru kódu, když dojde k událostem, ke kterým má Profiler odběr.  
  
 [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 Rozšiřuje rozhraní `ICorProfilerCallback` pomocí zpětných volání podporovaných v .NET Framework 2,0 a novějších verzích.  
  
 [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 Poskytuje metody zpětného volání, které modul CLR používá ke komunikaci informací o stavu připojení a odpojení profileru.  
  
 [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 Poskytuje metody zpětného volání, které modul CLR používá ke sdělování informací do profileru.  
  
 [ICorProfilerCallback5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 Poskytuje metodu, která identifikuje přenosný uzávěr objektů, na které odkazují kořeny uvolňování paměti.  
  
 [ICorProfilerCallback6 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 Poskytuje metodu zpětného volání, kterou modul CLR používá pro upozornění profileru, že se sestavení načítá.  
  
 [ICorProfilerCallback7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 Poskytuje metodu zpětného volání, kterou modul CLR (Common Language Runtime) používá pro upozornění profileru, že je aktualizován datový proud symbolů přidružený k modulu v paměti.  

[ICorProfilerCallback8 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
Poskytuje metody zpětného volání, které modul CLR (Common Language Runtime) používá pro upozornění profileru o spuštění a dokončení kompilace JIT dynamické metody.

[ICorProfilerCallback9 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
Poskytuje metodu zpětného volání, kterou modul CLR (Common Language Runtime) používá pro upozornění profileru, že dynamická metoda je uvolněna z paměti a následně uvolněna.

 [ICorProfilerFunctionControl – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 Poskytuje metody, které umožňují profileru kódu komunikovat s modulem CLR pro řízení způsobu, jakým má kompilátor JIT vygenerovat kód při rekompilaci konkrétní metody.  
  
 [ICorProfilerFunctionEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 Poskytuje metody pro sekvenční iteraci kolekcí funkcí v modulu CLR.  
  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 Poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR pro řízení událostí a informace o požadavcích.  
  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 Rozšiřuje rozhraní `ICorProfilerInfo` s metodami podporovanými v .NET Framework 2,0 a novějších verzích.  
  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 Rozšiřuje rozhraní `ICorProfilerInfo2` o metody podporované .NET Framework 4 a novějšími verzemi.  
  
 [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 Poskytuje metody, které profilery kódu používají ke komunikaci s modulem CLR k řízení sledování událostí a k vyžádání informací.  
  
 [ICorProfilerInfo5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 Poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR k řízení sledování událostí.  
  
 [ICorProfilerInfo6 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 Poskytuje enumerátor pro všechny metody, které patří do daného modulu NGen a které jsou v těle dané metody vložené.  
  
 [ICorProfilerInfo7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 Poskytuje způsob, jak použít nově definovaná metadata na modul a který poskytuje přístup k datovému proudu symbolů v paměti.  
  
 [ICorProfilerModuleEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 Poskytuje metody pro sekvenční iteraci kolekcí modulů načtených aplikací nebo profilerem.  
  
 [ICorProfilerObjectEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 Poskytuje metody pro sekvenční iteraci kolekcí zmrazených objektů, které jsou generovány pomocí nástroje [Ngen. exe (generátor nativních imagí)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 Poskytuje metody pro sekvenční iteraci v kolekci vláken v modulu CLR.  
  
 [IMethodMalloc – rozhraní](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 Poskytuje metodu [přidělení](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) pro přidělení paměti pro nové tělo funkce jazyka MSIL (Microsoft Intermediate Language).  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
