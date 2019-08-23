---
title: 'ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated – metoda'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 860ecde22dead112a42b6ac868e34f0e9cd3531d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916202"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated – metoda
[Podporováno v .NET Framework 4.6.1 a novějších verzích]  
  
 Upozorní profiler vždy, když je aktualizován datový proud symbolu přidružený k modulu v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pro`moduleId`  
 Identifikátor modulu v paměti, jehož datový proud symbolů je aktualizovaný.  
  
## <a name="remarks"></a>Poznámky  
 Toto zpětné volání je řízeno nastavením příznaku masky události [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) při volání metody [Icorprofilercallback5 –:: SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .  
  
> [!NOTE]
> Tato událost není aktuálně vyvolána pro symboly implicitně vytvořené nebo upravené prostřednictvím <xref:System.Reflection.Emit> rozhraní API.  
  
 I když se symboly zadávají před voláním jednoho z přetížení spravovaných <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> metod, které `rawSymbolStore` obsahují argument pro určení symbolů pro sestavení, modul runtime nemusí ve skutečnosti přidružit symbolické údaje k modulu. až do chvíle, kdy došlo k [ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětnému volání. Tato událost poskytuje později možnost shromažďovat symboly pro tyto moduly.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ModuleLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
