---
title: Metoda ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 973442a969746671e4d85c5d7881f51c5dfba535
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222260"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>Metoda ICorDebugAppDomain4::GetObjectForCCW
Získá z ukazatele (CCW) obálka volatelná aplikacemi COM spravovaný objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ccwPointer`  
 [in] Ukazatel (CCW) obálka volatelná aplikacemi COM.  
  
 `ppManagedObject`  
 [out] Ukazatel na adresu objektu "ICorDebugValue", který představuje spravovaný objekt, který odpovídá na daný objekt CCW ukazatel.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní ICorDebugAppDomain4](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
