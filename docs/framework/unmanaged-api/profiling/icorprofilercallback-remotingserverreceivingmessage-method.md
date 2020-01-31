---
title: ICorProfilerCallback::RemotingServerReceivingMessage – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 6e045a99de9ad30516fd12a7b490e26c860bde7e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866010"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a>ICorProfilerCallback::RemotingServerReceivingMessage – metoda
Upozorní profileru, že proces přijal volání vzdálené metody nebo žádost o aktivaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCookie`  
 pro Hodnota, která bude odpovídat hodnotě zadané v [ICorProfilerCallback:: remotingclientsendingmessage –](icorprofilercallback-remotingclientsendingmessage-method.md) za těchto podmínek:  
  
- Soubory cookie vzdálené komunikace jsou aktivní.  
  
- Kanál se úspěšně přenáší do zprávy.  
  
- Soubory cookie identifikátorů GUID jsou aktivní v procesu na straně klienta.  
  
 To umožňuje snadné párování volání vzdálené komunikace a vytváření logických zásobníků volání.  
  
 `fIsAsync`  
 pro Hodnota, která je `true`, pokud je volání asynchronní; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je žádost o zprávu asynchronní, může být žádost obsluhovaná libovolným vláknem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
