---
title: "ICorProfilerCallback7::ModuleInMemorySymbolsUpdated – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfiler7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 898adf043e425c00d6e311e2f67c53ed65cacb33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7::ModuleInMemorySymbolsUpdated – metoda
[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]  
  
 Upozorní profileru při každé aktualizaci symbol datový proud přidružený modul v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 Identifikátor v paměti modulu, jehož symbol datového proudu se aktualizuje.  
  
## <a name="remarks"></a>Poznámky  
 Tato zpětné volání je řízena nastavením [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) příznak maska událostí při volání metody [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda.  
  
> [!NOTE]
>  Tato událost není aktuálně aktivována pro symboly implicitně vytvoření nebo úpravě prostřednictvím <xref:System.Reflection.Emit> rozhraní API.  
  
 I když symboly jsou součástí předem volání do jednoho z přetížení spravovaný <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> metody, které zahrnuje `rawSymbolStore` argument, abyste zadávali symboly pro sestavení, modul runtime nemusí ve skutečnosti přidružení symbolický dat s modulem dokud po [moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání došlo k chybě. Tato událost poskytuje novější příležitostí ke shromažďování symboly pro tyto moduly.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ModuleLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [SetEventMask2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [ICorProfilerCallback7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
