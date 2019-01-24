---
title: ICorProfilerInfo4 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78f9645ad31e7421e239089c5610f6523918228b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536620"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 – rozhraní
Poskytuje metody, které profilery kódu se používají ke komunikaci s common language runtime (CLR), která řídí sledování událostí a informace o žádostech. . `ICorProfilerInfo4` Rozhraní je rozšířením druhým `ICorProfilerInfo` rozhraní. Poskytuje nové metody pro podporu rekompilace just-in-time (JIT), přidá [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumJITedFunctions2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Vrátí enumerátor pro všechny funkce, které byly dříve zkompilován JIT Kompilátorem a překompilován JIT.|  
|[EnumThreads – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Získá enumerátor, který poskytuje metody, které postupně iterovat přes kolekci všechna spravovaná vlákna v profilovaný proces.|  
|[GetCodeInfo3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Získá rozsah nativního kódu přidružené verze překompilován JIT zadanou funkci.|  
|[GetFunctionFromIP2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Mapuje ukazatel na instrukci spravovaného kódu na verzi překompilován JIT zadanou funkci.|  
|[GetILToNativeMapping2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Získá mapování z Microsoft intermediate language (MSIL) kompenzuje do nativních posunů pro kód obsažený ve verzi překompilován JIT zadanou funkci.|  
|[GetObjectSize2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Vrátí velikost zadaného objektu.|  
|[GetReJITIDs – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Vrátí pole ID, které identifikují všechny překompilován JIT verze zadané funkce, které jsou pořád ještě přidělená.|  
|[InitializeCurrentThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Inicializuje aktuální vlákno s předstihem následné profiler volání rozhraní API ve stejném vlákně, takže se lze vyvarovat této zablokování.|  
|[RequestReJIT – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|Požadavků opětovnou kompilaci JIT všechny výskyty zadaných funkcí.|  
|[RequestRevert – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Vrátí všechny výskyty zadaných funkcí na jejich původní verze.|  
  
## <a name="remarks"></a>Poznámky  
 Implementuje metody CLR `ICorProfilerInfo4` rozhraní s použitím modelu volných vláken. Každá metoda vrátí HRESULT indikuje úspěch nebo selhání. Seznam možných návratové kódy naleznete v souboru CorError.h.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
