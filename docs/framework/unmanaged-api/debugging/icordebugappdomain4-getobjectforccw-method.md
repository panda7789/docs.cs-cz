---
title: Metoda ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: a175a6b6c91c284348580e1d9dc9ef0c5f5fc5df
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895120"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>Metoda ICorDebugAppDomain4::GetObjectForCCW
Načte spravovaný objekt z ukazatele na obálku s přívolatelné v modelu COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ccwPointer`  
 pro Ukazatel na obálku s přívolatelné v modelu COM.  
  
 `ppManagedObject`  
 mimo Ukazatel na adresu objektu "ICorDebugValue", který představuje spravovaný objekt, který odpovídá zadanému ukazateli doleva.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugAppDomain4](icordebugappdomain4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
