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
ms.openlocfilehash: b85a7893cf5271c65bc842bb6ea598c825225376
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495720"
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
 pro Určuje `moduleId` část `module` párů (, `methodDef` ), které identifikují funkce, které mají být vráceny.  
  
 `methodIds`  
 pro Určuje `methodId` část `module` párů (, `methodDef` ), které identifikují funkce, které mají být vráceny.  
  
 `status`  
 mimo Pole HRESULTs uvedené v části stav HRESULTs dále v tomto tématu. Každá hodnota HRESULT indikuje úspěch nebo neúspěch při pokusu o vrácení všech funkcí určených v paralelních polích `moduleIds` a `methodIds` .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Byl proveden pokus o vrácení všech požadavků. aby bylo možné zjistit, které funkce byly úspěšně vráceny, je však nutné zkontrolovat vrácené pole stavu.|  
|CORPROF_E_CALLBACK4_REQUIRED|Aby bylo toto volání podporováno, Profiler musí implementovat rozhraní [ICorProfilerCallback4](icorprofilercallback4-interface.md) .|  
|CORPROF_E_REJIT_NOT_ENABLED|Opětovná kompilace JIT není povolená. Je nutné povolit opětovnou kompilaci JIT během inicializace pomocí metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení `COR_PRF_ENABLE_REJIT` příznaku.|  
|E_INVALIDARG|`cFunctions`je 0 nebo `moduleIds` nebo `methodIds` `NULL` .|  
|E_OUTOFMEMORY|Modul CLR nemohl dokončit požadavek, protože nemá dostatek paměti.|  
  
## <a name="status-hresults"></a>Stav HRESULTs  
  
|Stavové pole HRESULT|Description|  
|--------------------------|-----------------|  
|S_OK|Odpovídající funkce byla úspěšně vrácena.|  
|E_INVALIDARG|`moduleID`Parametr nebo `methodDef` je `NULL` .|  
|CORPROF_E_DATAINCOMPLETE|Modul ještě není úplně načtený, nebo se jedná o proces, který se právě načítá.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Zadaný modul byl dynamicky generován (například podle `Reflection.Emit` ). Proto není touto metodou podporována.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|CLR nemůže vrátit zadanou funkci, protože se nenašla odpovídající aktivní požadavek na opětovnou kompilaci. Buď není požadavek na opětovnou kompilaci, nebo již byla funkce vrácena.|  
|Ostatní|Operační systém vrátil selhání mimo ovládací prvek CLR. Pokud například systémové volání změny ochrany přístupu stránky paměti selže, zobrazí se Chyba operačního systému.|  
  
## <a name="remarks"></a>Poznámky  
 Při příštím volání všech instancí funkcí revereted se spustí původní verze funkcí. Pokud už je funkce spuštěná, dokončí se spuštění verze, která je spuštěná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
