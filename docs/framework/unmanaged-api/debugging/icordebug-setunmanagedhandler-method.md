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
ms.openlocfilehash: 7c3251b2cf7a4d0d97df0e6ecc9b332e3ed8e500
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895330"
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
 pro Ukazatel na objekt [ICorDebugUnmanagedCallback –](icordebugunmanagedcallback-interface.md) , který představuje obslužnou rutinu události pro nespravované události.  
  
## <a name="remarks"></a>Poznámky  
 Objekt obslužné rutiny události pro nespravované události musí být nastaven po volání metody [ICorDebug:: Initialize](icordebug-initialize-method.md) a před všemi voláními [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) nebo [ICorDebug::D ebugactiveprocess](icordebug-debugactiveprocess-method.md). Pro starší účely však není nutné nastavovat objekt obslužné rutiny události pro nespravované události, dokud nebude vyvolána první nativní událost ladění. Konkrétně, pokud `ICorDebug::CreateProcess` má nastaven příznak CREATE_SUSPENDED, nativní události ladění nelze odeslat, dokud nebude obnoveno hlavní vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebug – rozhraní](icordebug-interface.md)
