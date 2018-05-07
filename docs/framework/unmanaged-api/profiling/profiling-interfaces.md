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
ms.openlocfilehash: 059fadc5607e76b871083682136fda542ae9bacf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="profiling-interfaces"></a>Rozhraní pro profilaci
Tato část popisuje nespravovaná rozhraní, které vám umožní profilu program, který je vykonáván common language runtime (CLR).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ICLRProfiling – rozhraní](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 Poskytuje [attachprofiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metoda, která umožňuje profileru pro připojení k spuštěných procesů.  
  
 [ICorProfilerAssemblyReferenceProvider – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 Umožňuje profileru k informování CLR odkazů na sestavení, které profileru přidá [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.  
  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 Poskytuje metody, které jsou používány modulu CLR profileru kód upozornit, když dojde k události, ke kterým se připojila profileru.  
  
 [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 Rozšiřuje `ICorProfilerCallback` rozhraní s zpětná volání, které jsou podporovány v rozhraní .NET Framework 2.0 a novějších verzích.  
  
 [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 Poskytuje metody zpětného volání, které modul CLR používá ke komunikaci připojení a odpojení informace o stavu do profileru.  
  
 [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 Poskytuje metody zpětného volání, které modul CLR používá ke sdělování informací profileru.  
  
 [ICorProfilerCallback5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 Poskytne metodu, která identifikuje přechodné uzavření objekty odkazuje kořeny kolekce paměti.  
  
 [ICorProfilerCallback6 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 Poskytuje metody zpětného volání, která používá modulu CLR oznámit profileru, který načítá sestavení.  
  
 [ICorProfilerCallback7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 Poskytuje metody zpětného volání, která používá modul common language runtime profileru oznámit, že se aktualizuje symbol datový proud přidružený modul v paměti.  

[ICorProfilerCallback8 rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
Poskytuje metody zpětného volání, které používá modul common language runtime oznámit profileru, který má JIT – kompilace dynamické metody spuštění a dokončení.

[ICorProfilerCallback9 rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
Poskytuje metody zpětného volání, která používá modul common language runtime oznámit profileru, který je dynamická metoda shromážděných a následně uvolňování paměti.

 [ICorProfilerFunctionControl – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 Poskytuje metody, které umožňují kódu profileru ke komunikaci s CLR řídit, jak by měla JIT kompilátoru generování kódu při nutnosti rekompilace konkrétní metody.  
  
 [ICorProfilerFunctionEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 Poskytuje metody pro postupně iteraci přes kolekci funkcí v modulu CLR.  
  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 Poskytuje metody pro použití profilery kódu ke komunikaci s CLR řízení sledování událostí a vyžádání informací.  
  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 Rozšiřuje `ICorProfilerInfo` rozhraní s metod podporovaných v rozhraní .NET Framework 2.0 a novějších verzích.  
  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 Rozšiřuje `ICorProfilerInfo2` rozhraní s metod podporovaných v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] a novějších verzích.  
  
 [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 Poskytuje metody, které profilery kódu se používají ke komunikaci s CLR řízení události monitorování a k požadavku na informace.  
  
 [ICorProfilerInfo5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 Poskytuje metody pro použití profilery kódu ke komunikaci s CLR řízení události monitorování.  
  
 [ICorProfilerInfo6 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 Poskytuje enumerátor pro všechny metody, který patří k dané NGen modulu a které jsou vložená v těle dané metody.  
  
 [ICorProfilerInfo7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 Poskytuje metodu použít nově definovaná metadata modulu, který poskytuje přístup k datovému proudu symbol v paměti.  
  
 [ICorProfilerModuleEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 Poskytuje metody pro postupně iteraci prostřednictvím kolekce moduly zavedené aplikace nebo profileru.  
  
 [ICorProfilerObjectEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 Poskytuje metody pro postupně iteraci přes kolekci ukotvené objektů, které jsou generovány nástrojem [Ngen.exe (Generátor nativních obrázků)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 Poskytuje metody pro postupně iteraci prostřednictvím kolekce vláken v modulu CLR.  
  
 [IMethodMalloc – rozhraní](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 Poskytuje [alokační](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) metoda přidělení paměti pro nový tělo funkce (MSIL intermediate language) společnosti Microsoft.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
