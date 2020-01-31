---
title: ICorProfilerCallback::RemotingClientSendingMessage – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
ms.openlocfilehash: 8ae58344a7a17637bf08b9b5179abdba7e7060d6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866023"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a>ICorProfilerCallback::RemotingClientSendingMessage – metoda
Upozorní profileru, že klient posílá požadavek na server.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCookie`  
 pro Hodnota, která odpovídá hodnotě zadané v [ICorProfilerCallback:: remotingserverreceivingmessage –](icorprofilercallback-remotingserverreceivingmessage-method.md) za těchto podmínek:  
  
- Soubory cookie vzdálené komunikace jsou aktivní.  
  
- Kanál se úspěšně přenáší do zprávy.  
  
- Soubory cookie GUID jsou v procesu na straně serveru aktivní.  
  
 To umožňuje snadné párování volání vzdálené komunikace a vytváření logických zásobníků volání.  
  
 `fIsAsync`  
 pro Hodnota, která je `true`, pokud je volání asynchronní; v opačném případě `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
