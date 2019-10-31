---
title: ICorDebug::SetManagedHandler – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
ms.openlocfilehash: 88a007654646ba42ebcaf1b42e002282a1040c7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134055"
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler – metoda
Určuje objekt obslužné rutiny události pro spravované události.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCallback`  
 pro Ukazatel na objekt [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) , který je objektem obslužné rutiny události.  
  
## <a name="remarks"></a>Poznámky  
 `SetManagedHandler` musí být volána při vytváření.  
  
 Pokud implementace `ICorDebugManagedCallback` neobsahuje dostatečná rozhraní pro zpracování událostí ladění pro aplikaci, která je právě laděna, `SetManagedHandler` vrátí hodnotu HRESULT E_NOINTERFACE.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
