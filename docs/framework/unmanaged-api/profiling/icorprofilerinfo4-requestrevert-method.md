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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43a1954d75d37f68eb967eb714070a097573100a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert – metoda
Vrátí všechny výskyty určených funkcí jejich původní verze.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cFunctions`  
 [v] Počet funkcí vrátit zpátky.  
  
 `moduleIds`  
 [v] Určuje, `moduleId` část (`module`, `methodDef`) páry, které identifikují funkce se vrátí zpátky.  
  
 `methodIds`  
 [v] Určuje, `methodId` část (`module`, `methodDef`) páry, které identifikují funkce se vrátí zpátky.  
  
 `status`  
 [out] Pole hodnoty HRESULT uvedené v části "Hodnoty HRESULT stav" dál v tomto tématu. Každý HRESULT udává úspěch nebo selhání pokouší obnovit jednotlivé funkce zadané v poli paralelní `moduleIds` a `methodIds`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Došlo pokusu o vrátit zpět všechny požadavky; pole vrácené stav však musí být kontrolované k určení, funkcích, které byly úspěšně vráceny zpět.|  
|CORPROF_E_CALLBACK4_REQUIRED|Musí implementovat profileru [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní pro toto volání podporovaná.|  
|CORPROF_E_REJIT_NOT_ENABLED|JIT rekompilace nebylo povoleno. Je nutné povolit JIT rekompilace během inicializace s použitím [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodu a nastavit `COR_PRF_ENABLE_REJIT` příznak.|  
|E_INVALIDARG|`cFunctions` 0, nebo `moduleIds` nebo `methodIds` je `NULL`.|  
|E_OUTOFMEMORY|Modul CLR se nepodařilo dokončit požadavek, protože nedostatku paměti.|  
  
## <a name="status-hresults"></a>Stav hodnoty HRESULT  
  
|Stav pole HRESULT|Popis|  
|--------------------------|-----------------|  
|S_OK|Odpovídající funkce byla úspěšně obnovena.|  
|E_INVALIDARG|`moduleID` Nebo `methodDef` parametr `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Modul ještě není úplným načtením nebo je právě odpojení.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Zadaný modul dynamicky vygenerovalo (například podle `Reflection.Emit`). Proto není podporována touto metodou.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|Modul CLR nelze vrátit zadané funkce, protože nebyl nalezen odpovídající active rekompilace požadavek. Buď nikdy obdržel požadavek opětovnou kompilaci nebo funkce, byl již vrácen.|  
|Ostatní|Operační systém vrátil chybu mimo kontrolu modulu CLR. Například pokud selže volání systému změnit ochranu přístupu ke stránce paměti, se zobrazí chyba operačního systému.|  
  
## <a name="remarks"></a>Poznámky  
 Při příštím žádné instance funkce revereted se nazývají, původní verze funkcí se spustí. Pokud funkce je již spuštěna, bude dokončen provádění na verzi, která je spuštěná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
