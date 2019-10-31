---
title: ICorDebug::SetUnmanagedHandler – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
ms.openlocfilehash: 36d314211d95dff6648753f5d550a2cfd402a918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134049"
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler – metoda
Určuje objekt obslužné rutiny události pro nespravované události.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCallback`  
 pro Ukazatel na objekt [ICorDebugUnmanagedCallback –](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) , který představuje obslužnou rutinu události pro nespravované události.  
  
## <a name="remarks"></a>Poznámky  
 Objekt obslužné rutiny události pro nespravované události musí být nastaven po volání metody [ICorDebug:: Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) a před všemi voláními [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) nebo [ICorDebug::D ebugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md). Pro starší účely však není nutné nastavovat objekt obslužné rutiny události pro nespravované události, dokud nebude vyvolána první nativní událost ladění. Konkrétně, pokud `ICorDebug::CreateProcess` nastavil příznak CREATE_SUSPENDED, nativní události ladění nelze odeslat, dokud nebude obnoveno hlavní vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
