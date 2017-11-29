---
title: "ICorProfilerInfo4::RequestReJIT – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.RequestReJIT
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d62dbb2829480e8972d1d4966673ba8eb58f1831
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT – metoda
Požadavky JIT rekompilace všech instancí určených funkcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cFunctions`  
 [v] Počet funkcí její kompilace.  
  
 `moduleIds`  
 [v] Určuje, `moduleId` část (`module`, `methodDef`) páry, které identifikují funkce zopakovat.  
  
 `methodIds`  
 [v] Určuje, `methodId` část (`module`, `methodDef`) páry, které identifikují funkce zopakovat.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Došlo pokusu o označte všechny metody pro opětovnou kompilaci JIT. Musí implementovat profileru [icorprofilercallback4::rejiterror –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) metoda k určení, které metody byly úspěšně označen pro opětovnou kompilaci JIT.|  
|CORPROF_E_CALLBACK4_REQUIRED|Musí implementovat profileru [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní pro toto volání podporovaná.|  
|CORPROF_E_REJIT_NOT_ENABLED|JIT rekompilace nebylo povoleno. Je nutné povolit JIT rekompilace během inicializace s použitím [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodu a nastavit `COR_PRF_ENABLE_REJIT` příznak.|  
|E_INVALIDARG|`cFunctions`0, nebo `moduleIds` nebo `methodIds` je `NULL`.|  
|||  
|E_OUTOFMEMORY|Modul CLR se nepodařilo dokončit požadavek, protože nedostatku paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Volání `RequestReJIT` tak, aby měl modul runtime znovu zkompiluje zadaný sady funkcí. Pak můžete použít kód profileru [icorprofilerfunctioncontrol –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) rozhraní upravit kód, který se vygeneruje, když jsou překompilovat funkce. Aktuálně prováděné funkce a volání funkce jenom budoucí to nemá vliv. Pokud některé z určených funkcí byl dříve JIT překompilovat, požadavku opětovnou kompilaci je ekvivalentní návrat a nutnosti rekompilace funkce. Pokud chcete zachovat vratnost, když kompilátoru za běhu kompiluje původní verze funkce, považuje pouze původní verze jeho volané pro vložené rozhodnutí. Když JIT kompilátoru znovu zkompiluje funkci, považuje aktuální verze (Rekompilované nebo původní) jeho volané pro vložené.  
  
 Obvykle volá profileru `RequestReJIT` v reakci na vstup uživatele, vyžaduje, aby instrumentace profileru jedné nebo několika metod. `RequestReJIT`obvykle pozastaví modul runtime, aby bylo možné provést některé z svou práci a může potenciálně aktivační události kolekce paměti. Jako takový, by měly volat profileru `RequestReJIT` z vlákna ho dříve vytvořili, a z vlákna vytvořené CLR, aktuálně neprovádí profileru zpětné volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icorprofilerinfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
