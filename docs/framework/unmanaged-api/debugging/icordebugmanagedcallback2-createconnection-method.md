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
ms.openlocfilehash: 8e31f0a649fd1ca80d6557a0a7176549c67bf203
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501921"
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
 `CreateConnection`Zpětné volání bude aktivováno v jednom z následujících případů:  
  
- Když se ladicí program připojí k procesu, který obsahuje připojení. V tomto případě modul runtime vytvoří a odešle `CreateConnection` událost a událost [ICorDebugManagedCallback2:: ChangeConnection –](icordebugmanagedcallback2-changeconnection-method.md) pro každé připojení v procesu.  
  
- Když hostitel volá [ICLRDebugManager:: BeginConnection –](../hosting/iclrdebugmanager-beginconnection-method.md) v [rozhraní API hostování](../hosting/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback2 – rozhraní](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
