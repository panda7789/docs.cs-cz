---
title: "ICorProfilerCallback4::ReJITError – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c746d0f7a6be96f95f1a051e22de0ad1bd2d2269
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError – metoda
Aby kompilátoru za běhu (JIT) došlo k chybě při procesu rekompilace upozorní profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleID`  
 [v] `ModuleID` Ve které byl proveden pokus o rekompilace se nezdařilo.  
  
 `methodId`  
 [v] `MethodDef` Metody, na kterém byl proveden pokus o rekompilace se nezdařilo.  
  
 `functionId`  
 [v] Instance funkce, která se Rekompilované nebo označený pro opětovnou kompilaci. Tato hodnota může být `NULL` -li k chybě došlo na základě za metoda místo základ pro vytvoření instance (například pokud profileru zadaný token neplatná metadata metodu zopakovat).  
  
 `hrStatus`  
 [v] HRESULT, která určuje podstatu tohoto selhání. Najdete v části hodnoty stavu HRESULT seznam hodnot.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratové hodnoty z této zpětné volání se ignorují.  
  
## <a name="status-hresults"></a>Stav hodnoty HRESULT  
  
|Stav pole HRESULT|Popis|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID` Nebo `methodDef` token je `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Modul ještě není úplným načtením nebo je právě odpojení.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Zadaný modul dynamicky vygenerovalo (například `Reflection.Emit`) a proto nepodporuje tuto metodu.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|Metoda vytvoření instance do collectible sestavení a není proto schopna zopakovat. Všimněte si, že typy a funkcí definovaných v kontextu jiných reflexe (například `List<MyCollectibleStruct>`) se dá vytvořit instance do collectible sestavení.|  
|E_OUTOFMEMORY|Modul CLR nedostatku paměti při pokusu označit zadanou metodu pro opětovnou kompilaci JIT.|  
|Ostatní|Operační systém vrátil chybu mimo kontrolu modulu CLR. Například pokud selže volání systému změnit ochranu přístupu ke stránce paměti, se zobrazí chyba operačního systému.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
