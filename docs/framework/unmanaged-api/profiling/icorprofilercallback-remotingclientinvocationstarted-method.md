---
title: ICorProfilerCallback::RemotingClientInvocationStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type:
- apiref
ms.openlocfilehash: 93bd1010374413f3f4ef7e1424ff8194dded8bb3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866042"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a>ICorProfilerCallback::RemotingClientInvocationStarted – metoda
Upozorní profileru, že bylo zahájeno volání vzdálené komunikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato událost je stejná pro synchronní a asynchronní volání.  
  
 Každý z následujících dvojic zpětných volání bude proveden ve stejném vlákně:  
  
- `RemotingClientInvocationStarted` a [ICorProfilerCallback:: remotingclientsendingmessage –](icorprofilercallback-remotingclientsendingmessage-method.md)  
  
- [ICorProfilerCallback:: remotingclientreceivingreply –](icorprofilercallback-remotingclientreceivingreply-method.md) a [ICorProfilerCallback:: remotingclientinvocationfinished –](icorprofilercallback-remotingclientinvocationfinished-method.md)  
  
- [ICorProfilerCallback:: remotingserverinvocationreturned –](icorprofilercallback-remotingserverinvocationreturned-method.md) a [ICorProfilerCallback:: remotingserversendingreply –](icorprofilercallback-remotingserversendingreply-method.md)  
  
 Při zpětném volání vzdálené komunikace byste měli mít na paměti tyto problémy:  
  
- Spuštění funkce vzdálené komunikace se neprojeví v rozhraní API profileru, takže oznámení funkcí volaných z klienta a prováděná na serveru nejsou správně přijatá. Ke skutečnému vyvolání dojde prostřednictvím objektu proxy; do profileru se zobrazí, že některé funkce jsou kompilovány JIT, ale nikdy se nepoužívají.  
  
- Profiler neobdrží přesná upozornění na asynchronní události vzdálené komunikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
