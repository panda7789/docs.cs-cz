---
title: ICorDebugManagedCallback2::CreateConnection – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
ms.openlocfilehash: e98748b523b948dc002f2ebc4e2e79fc7d659918
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781592"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection – metoda
Oznamuje ladicímu programu, že bylo vytvořeno nové připojení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 pro Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém bylo vytvořeno připojení  
  
 `dwConnectionId`  
 pro ID nového připojení  
  
 `pConnName`  
 pro Ukazatel na název nového připojení.  
  
## <a name="remarks"></a>Poznámky  
 Zpětné volání `CreateConnection` se spustí v jednom z následujících případů:  
  
- Když se ladicí program připojí k procesu, který obsahuje připojení. V tomto případě modul runtime vygeneruje a odešle událost `CreateConnection` a událost [ICorDebugManagedCallback2:: ChangeConnection –](icordebugmanagedcallback2-changeconnection-method.md) pro každé připojení v procesu.  
  
- Když hostitel volá [ICLRDebugManager:: BeginConnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) v [rozhraní API hostování](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback2 – rozhraní](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
