---
title: ICorDebugValue::GetSize – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 3d6caa02333229bcd49f4c6ccf8b93265181a0b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137083"
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize – metoda
Získá velikost objektu "ICorDebugValue" v bajtech.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pSize`  
 mimo Velikost objektu Value (v bajtech).  
  
## <a name="remarks"></a>Poznámky  
 Pokud je typ hodnoty odkazový typ, tato metoda vrátí velikost ukazatele místo velikosti objektu.  
  
 Metoda `ICorDebugValue::GetSize` vrátí `COR_E_OVERFLOW` pro objekty, které jsou větší než 4 GB na 64 – bitové platformy. Použijte raději metodu [ICorDebugValue3 –:: GetSize64 –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) pro objekty, které jsou větší než 4 GB.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetSize64 – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
