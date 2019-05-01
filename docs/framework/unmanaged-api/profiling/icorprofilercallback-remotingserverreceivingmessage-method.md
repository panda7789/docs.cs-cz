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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30015cc6cae935c43cdbfec1a6eeae5c703ef9f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041818"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a>ICorProfilerCallback::RemotingServerReceivingMessage – metoda
Oznámí profileru, že proces přijal žádost o vzdálené metody volání nebo aktivace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCookie`  
 [in] Hodnotu, která bude odpovídat s hodnotou v [icorprofilercallback::remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) za těchto podmínek:  
  
- Vzdálená komunikace GUID soubory cookie jsou aktivní.  
  
- Kanál úspěšně odesílá zprávu.  
  
- Identifikátor GUID soubory cookie jsou aktivní na straně klienta procesu.  
  
 To umožňuje snadno párování tvorby logické volání zásobníku a Vzdálená volání.  
  
 `fIsAsync`  
 [in] Hodnotu, která je `true` Pokud je volání asynchronní; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud požadavek zprávy je asynchronní, žádost lze udržovat z žádného libovolného vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
