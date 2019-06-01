---
title: Rozhraní pro profilaci
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d97960a43e1d7ce625d96755a7c597a0425d0911
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457459"
---
# <a name="profiling-interfaces"></a>Rozhraní pro profilaci
Tato část popisuje nespravovaná rozhraní, které vám umožní profilování program, který se provádí modulem common language runtime (CLR).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ICLRProfiling – rozhraní](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 Poskytuje [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metodu, která umožňuje profileru připojit ke spuštěnému procesu.  
  
 [ICorProfilerAssemblyReferenceProvider – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 Umožňuje profileru informovat CLR odkazy na sestavení, které profiler přidá [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.  
  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 Poskytuje metody, které se používají modulem CLR upozornění profileru kód, pokud dojde k událostem, ke kterým se připojila profiler.  
  
 [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 Rozšiřuje `ICorProfilerCallback` rozhraní s zpětná volání, které jsou podporovány v rozhraní .NET Framework 2.0 a novějších verzích.  
  
 [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 Poskytuje metody zpětného volání, které používá modul CLR pro komunikaci připojení a odpojení profileru informace o stavu.  
  
 [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 Poskytuje metody zpětného volání, které používá modul CLR ke sdělování informací profileru.  
  
 [ICorProfilerCallback5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 Poskytuje metodu, která identifikuje přechodné uzavření objekty odkazuje kořeny kolekce uvolnění paměti.  
  
 [ICorProfilerCallback6 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 Poskytuje metodu zpětného volání, která používá modul CLR oznámit profiler, který se načítá sestavení.  
  
 [ICorProfilerCallback7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 Poskytuje metodu zpětného volání, která používá modul common language runtime pro oznámení profileru, je aktualizovaný symbol proud přidružený k modulu v paměti.  

[ICorProfilerCallback8 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
Poskytuje metody zpětného volání, které používá modul common language runtime pro oznámení profileru, který je spuštěn a dokončení kompilace JIT dynamické metody.

[ICorProfilerCallback9 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
Poskytuje metodu zpětného volání, která používá modul common language runtime pro oznámení profileru, který je dynamická metoda uvolňování paměti shromažďují a následně byla uvolněna.

 [ICorProfilerFunctionControl – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 Poskytuje metody, které umožňují profileru kód ke komunikaci s modulem CLR řídit, jak by měl kompilátor JIT generování kódu při opětovné kompilaci konkrétní metody.  
  
 [ICorProfilerFunctionEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 Poskytuje metody pro postupně iteraci prostřednictvím kolekce funkcí v CLR.  
  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 Poskytuje metody pro použití u profilery kódu ke komunikaci s modulem CLR řídit sledování událostí a žádost o informace.  
  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 Rozšiřuje `ICorProfilerInfo` rozhraní s metodami, které jsou podporovány v rozhraní .NET Framework 2.0 a novějších verzích.  
  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 Rozšiřuje `ICorProfilerInfo2` rozhraní s metodami, které jsou podporovány v rozhraní .NET Framework 4 a novější verze.  
  
 [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 Poskytuje metody, které profilery kódu se používají ke komunikaci s modulem CLR k řízení sledování událostí a požádat o informace.  
  
 [ICorProfilerInfo5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 Poskytuje metody pro použití u profilery kódu ke komunikaci s modulem CLR řízení události monitorování.  
  
 [ICorProfilerInfo6 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 Poskytuje enumerátor pro všechny metody, která patří do daného modulu NGen a, které jsou vloženy do těla dané metody.  
  
 [ICorProfilerInfo7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 Poskytuje způsob, jak použít nově definované v modulu metadat, který poskytuje přístup k datovému proudu symbolu v paměti.  
  
 [ICorProfilerModuleEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 Poskytuje metody pro postupně iteraci prostřednictvím kolekce moduly načtené aplikace nebo profileru.  
  
 [ICorProfilerObjectEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 Poskytuje metody, které postupně iterovat přes kolekci zmrazené objekty, které se vygenerovaly [Ngen.exe (Generátor nativních obrázků)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 Poskytuje metody pro postupně iterovat přes kolekci vláken v modulu CLR.  
  
 [IMethodMalloc – rozhraní](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 Poskytuje [alokační](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) metoda přidělení paměti pro nové tělo funkce Microsoft intermediate language (MSIL).  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
