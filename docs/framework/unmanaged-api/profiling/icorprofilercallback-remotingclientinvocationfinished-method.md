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
ms.openlocfilehash: c9a750b941b29047206c98410d4b4673d1101a01
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445833"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a>ICorProfilerCallback::RemotingClientInvocationFinished – metoda
Upozorní profileru, že volání vzdálené komunikace bylo dokončeno na straně klienta.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud bylo volání vzdálené komunikace synchronní, bylo spuštěno také dokončení na serveru. Pokud bylo volání vzdálené komunikace asynchronní, může být při zpracování volání stále očekávána odpověď. Pokud je očekávána odpověď, bude provedena jako volání metody [ICorProfilerCallback:: remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) a dodatečné volání `RemotingClientInvocationFinished` pro indikaci požadovaného sekundárního zpracování asynchronního volání.  
  
 Každý z následujících dvojic zpětných volání bude proveden ve stejném vlákně:  
  
- `RemotingClientInvocationStarted` a [ICorProfilerCallback:: remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)  
  
- [ICorProfilerCallback:: remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) a [ICorProfilerCallback:: remotingclientinvocationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)  
  
- [ICorProfilerCallback:: remotingserverinvocationreturned –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) a [ICorProfilerCallback:: remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)  
  
 Při zpětném volání vzdálené komunikace byste měli mít na paměti tyto problémy:  
  
- Spuštění funkce vzdálené komunikace se neprojeví v rozhraní API profileru, takže oznámení funkcí volaných z klienta a prováděná na serveru nejsou správně přijatá. Ke skutečnému vyvolání dojde prostřednictvím objektu proxy; do profileru se zobrazí, že některé funkce jsou kompilovány JIT, ale nikdy se nepoužívají.  
  
- Profiler neobdrží přesná upozornění na asynchronní události vzdálené komunikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
