---
title: ICorProfilerCallback3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: db07e2afa64ea2bf80416e6ab8cba5a4dcdc8dcf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499672"
---
# <a name="icorprofilercallback3-interface"></a>ICorProfilerCallback3 – rozhraní
Poskytuje metody zpětného volání, které modul CLR (Common Language Runtime) používá ke komunikaci informací o stavu připojení a odpojení profileru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[InitializeForAttach – metoda](icorprofilercallback3-initializeforattach-method.md)|Volá se modulem CLR, aby Profiler mohl po operaci připojení inicializovat svůj stav.|  
|[ProfilerAttachComplete – metoda](icorprofilercallback3-profilerattachcomplete-method.md)|Volá se modulem CLR k označení toho, že Profiler teď může volat metody catch.|  
|[ProfilerDetachSucceeded – metoda](icorprofilercallback3-profilerdetachsucceeded-method.md)|Upozorní profileru, že modul CLR (Common Language Runtime) chystá uvolnění knihovny DLL profileru.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)
