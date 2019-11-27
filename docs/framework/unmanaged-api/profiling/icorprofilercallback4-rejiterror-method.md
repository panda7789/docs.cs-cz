---
title: ICorProfilerCallback4::ReJITError – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 6ea9dee6e83870d1f2e0fdccffa53f16e6f18dba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430104"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError – metoda
Upozorní profileru, že kompilátor JIT (just-in-time) zjistil chybu v procesu opětovné kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 pro `ModuleID`, ve kterém byl proveden pokus o opětovnou kompilaci.  
  
 `methodId`  
 pro `MethodDef` metody, na které se provedl pokus o opětovnou kompilaci.  
  
 `functionId`  
 pro Instance funkce, která je rekompilována nebo označena pro rekompilaci. Tato hodnota může být `NULL`, pokud k selhání došlo na základě jednotlivých metod (například v případě, že Profiler zadal neplatný token metadat pro metodu, která má být zkompilován).  
  
 `hrStatus`  
 pro HRESULT, který označuje povahu selhání. Seznam hodnot naleznete v části stav HRESULTs.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratové hodnoty z tohoto zpětného volání jsou ignorovány.  
  
## <a name="status-hresults"></a>Stav HRESULTs  
  
|Stavové pole HRESULT|Popis|  
|--------------------------|-----------------|  
|E_INVALIDARG|Token `moduleID` nebo `methodDef` je `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Modul ještě není úplně načtený, nebo se jedná o proces, který se právě načítá.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Zadaný modul byl dynamicky generován (například `Reflection.Emit`), a proto není touto metodou podporován.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|Metoda je vytvořena do kolekční sestavení, a proto nemůže být znovu zkompilována. Všimněte si, že typy a funkce definované v kontextu bez reflexe (například `List<MyCollectibleStruct>`) mohou být vytvořeny do sestavení kolekční.|  
|E_OUTOFMEMORY|Při pokusu o označení zadané metody pro rekompilaci JIT došlo k nedostatku paměti CLR.|  
|Další|Operační systém vrátil selhání mimo ovládací prvek CLR. Například pokud systémové volání změny ochrany přístupu stránky paměti dojde k chybě, zobrazí se Chyba operačního systému.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
