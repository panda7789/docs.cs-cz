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
ms.openlocfilehash: f6dd10d196ffd3a653584e1bc8d1a5643850bc33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136610"
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
 [in] `moduleId`  
 Identifikátor modulu v paměti, jehož datový proud symbolů je aktualizovaný.  
  
## <a name="remarks"></a>Poznámky  
 Toto zpětné volání je řízeno nastavením příznaku masky události [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) při volání metody [Icorprofilercallback5 –:: SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .  
  
> [!NOTE]
> Tato událost není aktuálně vyvolána pro symboly implicitně vytvořené nebo upravené prostřednictvím rozhraní API <xref:System.Reflection.Emit>.  
  
 I když jsou symboly poskytovány před voláním jednoho z přetížení spravovaných <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> metod, které obsahují `rawSymbolStore` argument pro určení symbolů pro sestavení, modul runtime nemusí ve skutečnosti přidružit symbolické údaje k modulu, dokud Došlo k zpětnému volání [ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) . Tato událost poskytuje později možnost shromažďovat symboly pro tyto moduly.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ModuleLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
