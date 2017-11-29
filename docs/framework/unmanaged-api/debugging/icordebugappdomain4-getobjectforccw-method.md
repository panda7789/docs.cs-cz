---
title: Metoda ICorDebugAppDomain4::GetObjectForCCW
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: abce5563e8cd7eb0c599e835d0217157cf073485
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní ICorDebugAppDomain4](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
