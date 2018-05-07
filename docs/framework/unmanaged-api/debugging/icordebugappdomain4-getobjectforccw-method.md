---
title: Metoda ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1089668aa19747f5f694360ebb87098e2df9ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>Metoda ICorDebugAppDomain4::GetObjectForCCW
Získá objekt spravovaného z COM ukazatel obálka volatelná aplikacemi (doleva).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ccwPointer`  
 [v] Obálka volatelná aplikacemi (doleva) ukazatel COM.  
  
 `ppManagedObject`  
 [out] Ukazatel na adresu "ICorDebugValue" objekt, který představuje spravovaný objekt, který odpovídá dané ukazatele doleva.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugAppDomain4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
