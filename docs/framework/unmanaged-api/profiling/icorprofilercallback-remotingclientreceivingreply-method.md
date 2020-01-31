---
title: ICorProfilerCallback::RemotingClientReceivingReply – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: 62973a36e899b1a8c618888e5245bfc00d8ad777
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866058"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a>ICorProfilerCallback::RemotingClientReceivingReply – metoda
Upozorní profileru, že je dokončena serverová část volání vzdálené komunikace a klient nyní přijímá a chystá zpracovat odpověď.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a>Parametry  
 `pCookie`  
 pro Hodnota, která bude odpovídat hodnotě zadané v [ICorProfilerCallback:: remotingserversendingreply –](icorprofilercallback-remotingserversendingreply-method.md) za těchto podmínek:  
  
- Soubory cookie vzdálené komunikace jsou aktivní.  
  
- Kanál se úspěšně přenáší do zprávy.  
  
- Soubory cookie GUID jsou v procesu na straně serveru aktivní.  
  
 To umožňuje snadné párování volání vzdálené komunikace.  
  
 `fIsAsync`  
 pro Hodnota, která je `true`, pokud je volání asynchronní; v opačném případě `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
