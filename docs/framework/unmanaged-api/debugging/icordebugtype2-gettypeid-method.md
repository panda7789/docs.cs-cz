---
title: 'ICorDebugType2:: GetTypeId. – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
ms.openlocfilehash: 944313893d88b8eff97291d2517e4863a5ae958a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092766"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2:: GetTypeId. – metoda
Načte [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 mimo Ukazatel na [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento ICorDebugType.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je `S_OK` při úspěchu nebo selhání `HRESULT` kódu při selhání. Mezi kódy `HRESULT` patří následující:  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|`S_OK`|Metoda byla úspěšná. Metoda načetla platný [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).|  
|`CORDBG_E_CLASS_NOT_LOADED`|Typ nebyl načten.|  
|`CORDBG_E_UNSUPPORTED`|Typ není podporován.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda poskytuje mapování z ICorDebugType, který představuje typ, který může nebo nemusí být načten do modulu runtime, do [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), který slouží jako neprůhledný popisovač, který identifikuje typ načtený do modulu runtime.  
  
 Pokud typ, který ICorDebugType představuje, ještě nebyl načten, vrátí tato metoda `CORDBG_E_CLASS_NOT_LOADED`.  Pokud typ není podporován, vrátí `CORDBG_E_UNSUPPORTED`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugType2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
