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
ms.openlocfilehash: bbeada983e89a1ecae436a8d25ce2c86be0a9626
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494555"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert – metoda
Vrátí všechny výskyty zadaných funkcí na jejich původní verze.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cFunctions`  
 [in] Počet funkcí, které chcete vrátit zpět.  
  
 `moduleIds`  
 [in] Určuje `moduleId` část (`module`, `methodDef`) dvojice, které identifikují funkcí, které mají být vráceny zpět.  
  
 `methodIds`  
 [in] Určuje `methodId` část (`module`, `methodDef`) dvojice, které identifikují funkcí, které mají být vráceny zpět.  
  
 `status`  
 [out] Pole HRESULTs uvedených v části "Stav HRESULTs" dále v tomto tématu. Každý HRESULT označuje úspěšné nebo neúspěšné pokouší obnovit každá funkce zadané v poli paralelní `moduleIds` a `methodIds`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Vrátit zpět všechny požadavky; byl proveden pokus o však musí být zaškrtnuto pole vrácené stav k určení, které funkce byly úspěšně obnovena.|  
|CORPROF_E_CALLBACK4_REQUIRED|Profiler musí implementovat [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní pro toto volání a proto není podporován.|  
|CORPROF_E_REJIT_NOT_ENABLED|Rekompilace JIT není povolená. Musíte povolit rekompilace JIT při inicializaci pomocí [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody nastavte `COR_PRF_ENABLE_REJIT` příznak.|  
|E_INVALIDARG|`cFunctions` je 0, nebo `moduleIds` nebo `methodIds` je `NULL`.|  
|E_OUTOFMEMORY|Modul CLR nemohl dokončit požadavek, protože mu došla paměť.|  
  
## <a name="status-hresults"></a>HRESULT – stav  
  
|Stav pole HRESULT|Popis|  
|--------------------------|-----------------|  
|S_OK|Bylo úspěšně vráceno zpět odpovídající funkce.|  
|E_INVALIDARG|`moduleID` Nebo `methodDef` parametr `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Modul dosud není zcela načteno, nebo je právě uvolňován.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Zadaný modul se generuje dynamicky (například tím, že `Reflection.Emit`). Proto není podporována touto metodou.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|CLR nelze vrátit zadanou funkci, protože nebyl nalezen odpovídající požadavek aktivní opětovnou kompilaci. Nikdy byla vyžádána rekompilace nebo již vrácení funkce.|  
|Ostatní|Operační systém vrátil chybu mimo ovládací prvek CLR. Například pokud selže volání systému ke změně ochrany přístupu k paměti stránky, se zobrazí chyba operačního systému.|  
  
## <a name="remarks"></a>Poznámky  
 Při příštím všechny instance funkce revereted jsou volány, původní verze funkce se spustí. Pokud funkce je již spuštěn, dokončí provádění verze, na kterém běží.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
