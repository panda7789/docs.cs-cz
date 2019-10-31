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
ms.openlocfilehash: d83ad530c8a61c2bfc38fb46ad2a33ef8d5077d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130593"
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
  
- Když se ladicí program připojí k procesu, který obsahuje připojení. V tomto případě modul runtime vygeneruje a odešle událost `CreateConnection` a událost [ICorDebugManagedCallback2:: ChangeConnection –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) pro každé připojení v procesu.  
  
- Když hostitel volá [ICLRDebugManager:: BeginConnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) v [rozhraní API hostování](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
