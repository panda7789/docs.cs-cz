---
title: ICorProfilerCallback::RemotingServerSendingReply – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
ms.openlocfilehash: bf59d4e418223fd177bc5e19b173674b78e1f2ba
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499919"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a>ICorProfilerCallback::RemotingServerSendingReply – metoda
Upozorní profileru, že proces dokončil zpracování žádosti o vyvolání vzdálené metody a chystá se odeslat odpověď prostřednictvím kanálu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCookie`  
 pro Ukazatel na identifikátor GUID, který bude odpovídat hodnotě zadané v [ICorProfilerCallback:: remotingclientreceivingreply –](icorprofilercallback-remotingclientreceivingreply-method.md) za těchto podmínek:  
  
- Soubory cookie vzdálené komunikace jsou aktivní.  
  
- Kanál se úspěšně přenáší do zprávy.  
  
- Soubory cookie identifikátorů GUID jsou aktivní v procesu na straně klienta.  
  
 To umožňuje snadné párování volání vzdálené komunikace a vytváření logických zásobníků volání.  
  
 `fIsAsync`  
 pro Hodnota, která je v `true` případě, že volání je asynchronní, v opačném případě `false` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
