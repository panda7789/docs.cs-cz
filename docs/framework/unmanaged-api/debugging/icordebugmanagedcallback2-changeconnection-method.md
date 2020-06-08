---
title: ICorDebugManagedCallback2::ChangeConnection – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
ms.openlocfilehash: 7d209b7c319baff912b3462f8ed5f3f30f127750
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501908"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection – metoda
Oznamuje ladicímu programu, že se změnila sada úloh přidružených k zadanému připojení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 pro Ukazatel na objekt "ICorDebugProcess", který představuje proces obsahující připojení, které bylo změněno.  
  
 `dwConnectionId`  
 pro ID připojení, které bylo změněno.  
  
## <a name="remarks"></a>Poznámky  
 `ChangeConnection`Zpětné volání bude aktivováno v jednom z následujících případů:  
  
- Když se ladicí program připojí k procesu, který obsahuje připojení. V tomto případě modul runtime vygeneruje a odešle událost [ICorDebugManagedCallback2:: CreateConnection](icordebugmanagedcallback2-createconnection-method.md) a `ChangeConnection` událost pro každé připojení v procesu. `ChangeConnection`Událost se generuje pro každé existující připojení, bez ohledu na to, jestli se od jejího vytvoření změnila sada úkolů daného připojení.  
  
- Když hostitel volá [ICLRDebugManager:: SetConnectionTasks –](../hosting/iclrdebugmanager-setconnectiontasks-method.md) v [rozhraní API hostování](../hosting/index.md).  
  
 Ladicí program by měl zkontrolovat všechny podprocesy v procesu a vybrat nové změny.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback2 – rozhraní](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
