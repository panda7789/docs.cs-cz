---
title: "Rozhraní pro profilaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5c0423f9c8b01c1289e1107c0c16c59968a6e2a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-interfaces"></a>Rozhraní pro profilaci
Tato část popisuje nespravovaná rozhraní, které vám umožní profilu program, který je vykonáván common language runtime (CLR).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Iclrprofiling – rozhraní](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 Poskytuje [attachprofiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metoda, která umožňuje profileru pro připojení k spuštěných procesů.  
  
 [Rozhraní ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 Umožňuje profileru k informování CLR odkazů na sestavení, které profileru přidá [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.  
  
 [Icorprofilercallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 Poskytuje metody, které jsou používány modulu CLR profileru kód upozornit, když dojde k události, ke kterým se připojila profileru.  
  
 [Icorprofilercallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 Rozšiřuje `ICorProfilerCallback` rozhraní s zpětná volání, které jsou podporovány v rozhraní .NET Framework 2.0 a novějších verzích.  
  
 [Icorprofilercallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 Poskytuje metody zpětného volání, které modul CLR používá ke komunikaci připojení a odpojení informace o stavu do profileru.  
  
 [Icorprofilercallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 Poskytuje metody zpětného volání, které modul CLR používá ke sdělování informací profileru.  
  
 [Icorprofilercallback5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 Poskytne metodu, která identifikuje přechodné uzavření objekty odkazuje kořeny kolekce paměti.  
  
 [Rozhraní ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 Poskytuje metody zpětného volání, která používá modulu CLR oznámit profileru, který načítá sestavení.  
  
 [ICorProfilerCallback7 rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 Poskytuje metody zpětného volání, která používá modul common language runtime profileru oznámit, že se aktualizuje symbol datový proud přidružený modul v paměti.  
  
 [Icorprofilerfunctioncontrol – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 Poskytuje metody, které umožňují kódu profileru ke komunikaci s CLR řídit, jak by měla JIT kompilátoru generování kódu při nutnosti rekompilace konkrétní metody.  
  
 [Icorprofilerfunctionenum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 Poskytuje metody pro postupně iteraci přes kolekci funkcí v modulu CLR.  
  
 [Icorprofilerinfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 Poskytuje metody pro použití profilery kódu ke komunikaci s CLR řízení sledování událostí a vyžádání informací.  
  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 Rozšiřuje `ICorProfilerInfo` rozhraní s metod podporovaných v rozhraní .NET Framework 2.0 a novějších verzích.  
  
 [Icorprofilerinfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 Rozšiřuje `ICorProfilerInfo2` rozhraní s metod podporovaných v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] a novějších verzích.  
  
 [Icorprofilerinfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 Poskytuje metody, které profilery kódu se používají ke komunikaci s CLR řízení události monitorování a k požadavku na informace.  
  
 [Rozhraní ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 Poskytuje metody pro použití profilery kódu ke komunikaci s CLR řízení události monitorování.  
  
 [ICorProfilerInfo6 rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 Poskytuje enumerátor pro všechny metody, který patří k dané NGen modulu a které jsou vložená v těle dané metody.  
  
 [ICorProfilerInfo7 rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 Poskytuje metodu použít nově definovaná metadata modulu, který poskytuje přístup k datovému proudu symbol v paměti.  
  
 [Icorprofilermoduleenum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 Poskytuje metody pro postupně iteraci prostřednictvím kolekce moduly zavedené aplikace nebo profileru.  
  
 [Icorprofilerobjectenum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 Poskytuje metody pro postupně iteraci přes kolekci ukotvené objektů, které jsou generovány nástrojem [Ngen.exe (Generátor nativních obrázků)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [Icorprofilerthreadenum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 Poskytuje metody pro postupně iteraci prostřednictvím kolekce vláken v modulu CLR.  
  
 [Imethodmalloc – rozhraní](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 Poskytuje [alokační](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) metoda přidělení paměti pro nový tělo funkce (MSIL intermediate language) společnosti Microsoft.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profilace globálních statických funkcí](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profilace výčtů](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
