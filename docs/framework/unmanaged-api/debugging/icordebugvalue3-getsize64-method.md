---
title: ICorDebugValue3::GetSize64 – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
ms.openlocfilehash: 72a1b6fdc40f3169500d8cf3b3028315106ecc69
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140229"
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64 – metoda
Získá velikost objektu [ICorDebugValue3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) v bajtech.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pSize  
 mimo Ukazatel na velikost (v bajtech) tohoto objektu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je typ této hodnoty odkazový typ, vrátí tato metoda velikost ukazatele, nikoli velikost objektu.  
  
 Metoda `ICorDebugValue3::GetSize` se liší od metody [ICorDebugValue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) v typu jeho výstupního parametru. V [ICorDebugValue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)je výstupní parametr `ULONG32`; v `ICorDebugValue3::GetSize`se jedná o `ULONG64`. To umožňuje, aby rozhraní [ICorDebugValue3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) nahlásilo velikost polí, která překračují 2 GB.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugValue3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
