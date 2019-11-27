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
ms.openlocfilehash: cbd7c0d8fff55766a98e727ce22c77dd5214611b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448002"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 – rozhraní
Poskytuje metody, které profilery kódu používají ke komunikaci s modulem CLR (Common Language Runtime) pro řízení sledování událostí a informace o požadavcích. . Rozhraní `ICorProfilerInfo4` je rozšířením ostatních rozhraní `ICorProfilerInfo`. Poskytuje nové metody pro podporu opětovné kompilace JIT (just-in-time), přidané v .NET Framework 4,5.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumJITedFunctions2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Vrátí enumerátor pro všechny funkce, které byly dříve kompilovány JIT a rekompilovány JIT.|  
|[EnumThreads – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Získá enumerátor, který poskytuje metody pro sekvenční iteraci v kolekci všech spravovaných vláken v profilované procesu.|  
|[GetCodeInfo3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Získá rozsahy nativního kódu přidruženého k Rekompilované verzi JIT zadané funkce.|  
|[GetFunctionFromIP2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Mapuje ukazatel na instrukci spravovaného kódu pro rekompilovaný verzi zadané funkce JIT.|  
|[GetILToNativeMapping2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Získá mapu z posunu od jazyka MSIL (Microsoft Intermediate Language) k nativním posunům pro kód obsažený v překompilované verzi zadané funkce JIT.|  
|[GetObjectSize2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Vrací velikost zadaného objektu.|  
|[GetReJITIDs – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Vrátí pole ID, které identifikují všechny verze rekompilovaných kompilátorů JIT zadané funkce, které jsou stále přiděleny.|  
|[InitializeCurrentThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Inicializuje aktuální vlákno předem v následných voláních rozhraní API profileru ve stejném vlákně, aby bylo možné zablokování zabránit.|  
|[RequestReJIT – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|Vyžádá rekompilaci JIT všech instancí zadaných funkcí.|  
|[RequestRevert – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Vrátí všechny výskyty zadaných funkcí do jejich původních verzí.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR implementuje metody rozhraní `ICorProfilerInfo4` pomocí modelu s volnými vlákny. Každá metoda vrátí hodnotu HRESULT, aby označovala úspěch nebo neúspěch. Seznam možných návratových kódů naleznete v souboru CorError. h.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
