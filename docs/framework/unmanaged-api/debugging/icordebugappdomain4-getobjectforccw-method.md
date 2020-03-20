---
title: Metoda ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 10d32314e46aba4f030b294cadc3cbb36e8742f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179053"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>Metoda ICorDebugAppDomain4::GetObjectForCCW
Získá spravovaný objekt z ukazatele obálky com volatelné (CCW).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ccwPointer`  
 [v] Com volatelné obálky (CCW) ukazatel.  
  
 `ppManagedObject`  
 [out] Ukazatel na adresu objektu "ICorDebugValue", který představuje spravovaný objekt, který odpovídá danému ukazateli CCW.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugAppDomain4 – rozhraní](icordebugappdomain4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
