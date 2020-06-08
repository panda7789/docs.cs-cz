---
title: Rozhraní pro profilaci
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: f073794b4fdf89f289b70fed9967ee37b5f4e133
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494030"
---
# <a name="profiling-interfaces"></a>Rozhraní pro profilaci
Tato část popisuje nespravovaná rozhraní, která umožňují profilovat program, který je spuštěn modulem CLR (Common Language Runtime).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ICLRProfiling – rozhraní](iclrprofiling-interface.md)  
 Poskytuje metodu [AttachProfiler –](iclrprofiling-attachprofiler-method.md) , která umožňuje profileru připojit se k běžícímu procesu.  
  
 [Rozhraní ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)  
 Umožňuje profileru informovat modul CLR o odkazech na sestavení, které bude Profiler přidávat do zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .  
  
 [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)  
 Poskytuje metody, které používá modul CLR k oznamování profileru kódu, když dojde k událostem, ke kterým má Profiler odběr.  
  
 [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)  
 Rozšiřuje `ICorProfilerCallback` rozhraní o zpětná volání podporovaná v .NET Framework 2,0 a novějších verzích.  
  
 [ICorProfilerCallback3 – rozhraní](icorprofilercallback3-interface.md)  
 Poskytuje metody zpětného volání, které modul CLR používá ke komunikaci informací o stavu připojení a odpojení profileru.  
  
 [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)  
 Poskytuje metody zpětného volání, které modul CLR používá ke sdělování informací do profileru.  
  
 [ICorProfilerCallback5 – rozhraní](icorprofilercallback5-interface.md)  
 Poskytuje metodu, která identifikuje přenosný uzávěr objektů, na které odkazují kořeny uvolňování paměti.  
  
 [ICorProfilerCallback6 – rozhraní](icorprofilercallback6-interface.md)  
 Poskytuje metodu zpětného volání, kterou modul CLR používá pro upozornění profileru, že se sestavení načítá.  
  
 [ICorProfilerCallback7 – rozhraní](icorprofilercallback7-interface.md)  
 Poskytuje metodu zpětného volání, kterou modul CLR (Common Language Runtime) používá pro upozornění profileru, že je aktualizován datový proud symbolů přidružený k modulu v paměti.  

[ICorProfilerCallback8 – rozhraní](icorprofilercallback8-interface.md)  
Poskytuje metody zpětného volání, které modul CLR (Common Language Runtime) používá pro upozornění profileru o spuštění a dokončení kompilace JIT dynamické metody.

[ICorProfilerCallback9 – rozhraní](icorprofilercallback9-interface.md)  
Poskytuje metodu zpětného volání, kterou modul CLR (Common Language Runtime) používá pro upozornění profileru, že dynamická metoda je uvolněna z paměti a následně uvolněna.

 [ICorProfilerFunctionControl – rozhraní](icorprofilerfunctioncontrol-interface.md)  
 Poskytuje metody, které umožňují profileru kódu komunikovat s modulem CLR pro řízení způsobu, jakým má kompilátor JIT vygenerovat kód při rekompilaci konkrétní metody.  
  
 [ICorProfilerFunctionEnum – rozhraní](icorprofilerfunctionenum-interface.md)  
 Poskytuje metody pro sekvenční iteraci kolekcí funkcí v modulu CLR.  
  
 [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)  
 Poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR pro řízení událostí a informace o požadavcích.  
  
 [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)  
 Rozšiřuje `ICorProfilerInfo` rozhraní o metody podporované v .NET Framework 2,0 a novějších verzích.  
  
 [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)  
 Rozšiřuje `ICorProfilerInfo2` rozhraní o metody podporované .NET Framework 4 a novějšími verzemi.  
  
 [ICorProfilerInfo4 – rozhraní](icorprofilerinfo4-interface.md)  
 Poskytuje metody, které profilery kódu používají ke komunikaci s modulem CLR k řízení sledování událostí a k vyžádání informací.  
  
 [ICorProfilerInfo5 – rozhraní](icorprofilerinfo5-interface.md)  
 Poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR k řízení sledování událostí.  
  
 [ICorProfilerInfo6 – rozhraní](icorprofilerinfo6-interface.md)  
 Poskytuje enumerátor pro všechny metody, které patří do daného modulu NGen a které jsou v těle dané metody vložené.  
  
 [ICorProfilerInfo7 – rozhraní](icorprofilerinfo7-interface.md)  
 Poskytuje způsob, jak použít nově definovaná metadata na modul a který poskytuje přístup k datovému proudu symbolů v paměti.  
  
 [ICorProfilerModuleEnum – rozhraní](icorprofilermoduleenum-interface.md)  
 Poskytuje metody pro sekvenční iteraci kolekcí modulů načtených aplikací nebo profilerem.  
  
 [ICorProfilerObjectEnum – rozhraní](icorprofilerobjectenum-interface.md)  
 Poskytuje metody pro sekvenční iteraci kolekcí zmrazených objektů, které jsou generovány pomocí nástroje [Ngen. exe (generátor nativních imagí)](../../tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum – rozhraní](icorprofilerthreadenum-interface.md)  
 Poskytuje metody pro sekvenční iteraci v kolekci vláken v modulu CLR.  
  
 [IMethodMalloc – rozhraní](imethodmalloc-interface.md)  
 Poskytuje metodu [přidělení](imethodmalloc-alloc-method.md) pro přidělení paměti pro nové tělo funkce jazyka MSIL (Microsoft Intermediate Language).  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](profiling-overview.md)  
  
 [Profilace globálních statických funkcí](profiling-global-static-functions.md)  
  
 [Výčty pro profilaci](profiling-enumerations.md)  
  
 [Struktury pro profilaci](profiling-structures.md)
