---
title: ICorProfilerInfo4::RequestRevert – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: 73d122b1ffa890bfa43f8eef7e24595ac0d26ebe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861785"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert – metoda
Vrátí všechny výskyty zadaných funkcí do jejich původních verzí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cFunctions`  
 pro Počet funkcí, které mají být vráceny.  
  
 `moduleIds`  
 pro Určuje `moduleId` část párů (`module`, `methodDef`), které identifikují funkce, které mají být vráceny.  
  
 `methodIds`  
 pro Určuje `methodId` část párů (`module`, `methodDef`), které identifikují funkce, které mají být vráceny.  
  
 `status`  
 mimo Pole HRESULTs uvedené v části stav HRESULTs dále v tomto tématu. Každá hodnota HRESULT indikuje úspěch nebo neúspěch při pokusu o vrácení každé funkce zadané v paralelních polích `moduleIds` a `methodIds`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Byl proveden pokus o vrácení všech požadavků. aby bylo možné zjistit, které funkce byly úspěšně vráceny, je však nutné zkontrolovat vrácené pole stavu.|  
|CORPROF_E_CALLBACK4_REQUIRED|Aby bylo toto volání podporováno, Profiler musí implementovat rozhraní [ICorProfilerCallback4](icorprofilercallback4-interface.md) .|  
|CORPROF_E_REJIT_NOT_ENABLED|Opětovná kompilace JIT není povolená. Je nutné povolit rekompilaci JIT během inicializace pomocí metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaku `COR_PRF_ENABLE_REJIT`.|  
|E_INVALIDARG|`cFunctions` je 0 nebo `moduleIds` nebo `methodIds` `NULL`.|  
|E_OUTOFMEMORY|Modul CLR nemohl dokončit požadavek, protože nemá dostatek paměti.|  
  
## <a name="status-hresults"></a>Stav HRESULTs  
  
|Stavové pole HRESULT|Popis|  
|--------------------------|-----------------|  
|S_OK|Odpovídající funkce byla úspěšně vrácena.|  
|E_INVALIDARG|Parametr `moduleID` nebo `methodDef` má hodnotu `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Modul ještě není úplně načtený, nebo se jedná o proces, který se právě načítá.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Zadaný modul byl dynamicky generován (například `Reflection.Emit`). Proto není touto metodou podporována.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|CLR nemůže vrátit zadanou funkci, protože se nenašla odpovídající aktivní požadavek na opětovnou kompilaci. Buď není požadavek na opětovnou kompilaci, nebo již byla funkce vrácena.|  
|Další|Operační systém vrátil selhání mimo ovládací prvek CLR. Pokud například systémové volání změny ochrany přístupu stránky paměti selže, zobrazí se Chyba operačního systému.|  
  
## <a name="remarks"></a>Poznámky  
 Při příštím volání všech instancí funkcí revereted se spustí původní verze funkcí. Pokud už je funkce spuštěná, dokončí se spuštění verze, která je spuštěná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
