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
ms.openlocfilehash: 58d11e9084f53c69f2656b4f0ee6bc7d2cc4ae21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495863"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 – rozhraní
Poskytuje metody, které profilery kódu používají ke komunikaci s modulem CLR (Common Language Runtime) pro řízení sledování událostí a informace o požadavcích. . `ICorProfilerInfo4`Rozhraní je rozšířením ostatních `ICorProfilerInfo` rozhraní. Poskytuje nové metody pro podporu opětovné kompilace JIT (just-in-time), přidané v .NET Framework 4,5.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[EnumJITedFunctions2 – metoda](icorprofilerinfo4-enumjitedfunctions2-method.md)|Vrátí enumerátor pro všechny funkce, které byly dříve kompilovány JIT a rekompilovány JIT.|  
|[EnumThreads – metoda](icorprofilerinfo4-enumthreads-method.md)|Získá enumerátor, který poskytuje metody pro sekvenční iteraci v kolekci všech spravovaných vláken v profilované procesu.|  
|[GetCodeInfo3 – metoda](icorprofilerinfo4-getcodeinfo3-method.md)|Získá rozsahy nativního kódu přidruženého k Rekompilované verzi JIT zadané funkce.|  
|[GetFunctionFromIP2 – metoda](icorprofilerinfo4-getfunctionfromip2-method.md)|Mapuje ukazatel na instrukci spravovaného kódu pro rekompilovaný verzi zadané funkce JIT.|  
|[GetILToNativeMapping2 – metoda](icorprofilerinfo4-getiltonativemapping2-method.md)|Získá mapu z posunu od jazyka MSIL (Microsoft Intermediate Language) k nativním posunům pro kód obsažený v překompilované verzi zadané funkce JIT.|  
|[GetObjectSize2 – metoda](icorprofilerinfo4-getobjectsize2-method.md)|Vrací velikost zadaného objektu.|  
|[GetReJITIDs – metoda](icorprofilerinfo4-getrejitids-method.md)|Vrátí pole ID, které identifikují všechny verze rekompilovaných kompilátorů JIT zadané funkce, které jsou stále přiděleny.|  
|[InitializeCurrentThread – metoda](icorprofilerinfo4-initializecurrentthread-method.md)|Inicializuje aktuální vlákno předem v následných voláních rozhraní API profileru ve stejném vlákně, aby bylo možné zablokování zabránit.|  
|[RequestReJIT – metoda](icorprofilerinfo4-requestrejit-method.md)|Vyžádá rekompilaci JIT všech instancí zadaných funkcí.|  
|[RequestRevert – metoda](icorprofilerinfo4-requestrevert-method.md)|Vrátí všechny výskyty zadaných funkcí do jejich původních verzí.|  
  
## <a name="remarks"></a>Poznámky  
 CLR implementuje metody `ICorProfilerInfo4` rozhraní pomocí modelu s volnými vlákny. Každá metoda vrátí hodnotu HRESULT, aby označovala úspěch nebo neúspěch. Seznam možných návratových kódů naleznete v souboru CorError. h.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
