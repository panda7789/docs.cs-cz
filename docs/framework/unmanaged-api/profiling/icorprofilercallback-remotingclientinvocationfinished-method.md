---
title: ICorProfilerCallback::RemotingClientInvocationFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dddaaea2421de9c63d5d45f7add85b5da3019aee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696487"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a>ICorProfilerCallback::RemotingClientInvocationFinished – metoda
Oznámí profileru, že dokončení běh vzdálené volání na straně klienta.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud se vzdáleným voláním synchronní, ji má také spustit dokončení na serveru. Pokud bylo vzdálené volání asynchronní, odpověď může stále očekávat při zpracování volání. Pokud se očekává odpověď, tato hodnota se vrátí jako volání [icorprofilercallback::remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) a další volání `RemotingClientInvocationFinished` udávajících vyžaduje sekundární zpracování asynchronního volání.  
  
 Každé z následujících dvojic zpětná volání dojde ve stejném vlákně:  
  
-   `RemotingClientInvocationStarted` a [icorprofilercallback::remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)  
  
-   [Icorprofilercallback::remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) a [icorprofilercallback::remotingclientinvocationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)  
  
-   [Icorprofilercallback::remotingserverinvocationreturned –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) a [icorprofilercallback::remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)  
  
 Byste měli vědět o následujících potíží u vzdálené komunikace zpětná volání:  
  
-   Provedení funkce vzdálené komunikace se neprojeví v Profilování rozhraní API, proto nejsou správně zasílána oznámení pro funkce, které jsou vyvolávány z klienta a spuštěny na serveru. Skutečné vyvolání se stane přes proxy server objektu. k profileru zdá se, že některé funkce jsou sestaveny JIT, ale nikdy použité.  
  
-   Profiler nezíská přesné oznámení o události asynchronní vzdálené komunikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
