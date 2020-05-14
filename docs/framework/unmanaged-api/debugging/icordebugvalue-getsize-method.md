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
ms.openlocfilehash: 9ff7128f55236ae4d0c3a9067a279c496cfb6798
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396752"
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
  
 `ICorDebugValue::GetSize`Metoda vrací `COR_E_OVERFLOW` objekty, které jsou větší než 4 GB na 64 bitů. Použijte raději metodu [ICorDebugValue3 –:: GetSize64 –](icordebugvalue3-getsize64-method.md) pro objekty, které jsou větší než 4 GB.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetSize64 – metoda](icordebugvalue3-getsize64-method.md)
