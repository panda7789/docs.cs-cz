---
title: ICorProfilerCallback3::ProfilerAttachComplete – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: 8168f6f1079ec34b9fb53a485da0f32175446719
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865425"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a>ICorProfilerCallback3::ProfilerAttachComplete – metoda
Volá se modulem CLR (Common Language Runtime), který označuje, že Profiler teď může volat metody Catch [ICorProfilerInfo3:: EnumJITedFunctions –](icorprofilerinfo3-enumjitedfunctions-method.md) a [ICorProfilerInfo3:: enummodules –](icorprofilerinfo3-enummodules-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Zpětné volání `ProfilerAttachComplete` je vystaveno po volání metody [ICorProfilerCallback3:: InitializeForAttach –](icorprofilercallback3-initializeforattach-method.md) . Označuje následující:  
  
- Byla aktivována zpětná volání, která požadoval Profiler v `InitializeForAttach`.  
  
- Profiler teď může provádět zachytávání u přidružených ID, aniž by se museli zabývat informacemi o chybějících oznámeních.  
  
 CLR ignoruje návratovou hodnotu z tohoto zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
