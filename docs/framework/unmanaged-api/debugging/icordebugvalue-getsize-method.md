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
ms.openlocfilehash: 3d26ddb6d89af60acf6dc1214b0423ba75e488ff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791168"
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
  
 Metoda `ICorDebugValue::GetSize` vrátí `COR_E_OVERFLOW` pro objekty, které jsou větší než 4 GB na 64 – bitové platformy. Použijte raději metodu [ICorDebugValue3 –:: GetSize64 –](icordebugvalue3-getsize64-method.md) pro objekty, které jsou větší než 4 GB.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetSize64 – metoda](icordebugvalue3-getsize64-method.md)
