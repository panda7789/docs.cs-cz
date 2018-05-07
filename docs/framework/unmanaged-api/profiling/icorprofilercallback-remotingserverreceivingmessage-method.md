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
ms.openlocfilehash: c1874b5bea465eb31bcaad2d912b90d35cfc711b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a>ICorProfilerCallback::RemotingServerReceivingMessage – metoda
Upozorní profileru, že proces přijal žádost o vzdálené metody vyvolání nebo aktivace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCookie`  
 [v] Hodnota, která bude odpovídat s hodnota zadaná v [icorprofilercallback::remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) za těchto podmínek:  
  
-   Vzdálená komunikace GUID soubory cookie jsou aktivní.  
  
-   Kanál úspěšně přenosu zprávy.  
  
-   Identifikátor GUID soubory cookie jsou aktivní na straně klienta procesu.  
  
 To umožňuje snadno párování Vzdálená volání a vytvoření zásobníku logické volání.  
  
 `fIsAsync`  
 [v] Hodnotu, která je `true` Pokud volání je asynchronní, jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud požadavek zprávy je asynchronní, žádost může obsluhovány pomocí libovolného libovolný vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
