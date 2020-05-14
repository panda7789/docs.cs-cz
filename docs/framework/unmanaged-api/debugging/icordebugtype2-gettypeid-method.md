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
ms.openlocfilehash: 1c11946bc5ea69a090091c014aba859935b48b36
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396673"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2:: GetTypeId. – metoda
Získá [COR_TYPEID](cor-typeid-structure.md) pro tento typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 mimo Ukazatel na [COR_TYPEID](cor-typeid-structure.md) pro tento ICorDebugType.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je `S_OK` při úspěchu nebo při `HRESULT` selhání kódu chyby. `HRESULT`Mezi tyto kódy patří:  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|`S_OK`|Metoda byla úspěšná. Metoda načetla platný [COR_TYPEID](cor-typeid-structure.md).|  
|`CORDBG_E_CLASS_NOT_LOADED`|Typ nebyl načten.|  
|`CORDBG_E_UNSUPPORTED`|Typ není podporován.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda poskytuje mapování z ICorDebugType, který představuje typ, který může nebo nemusí být načten do modulu runtime, do [COR_TYPEID](cor-typeid-structure.md), který slouží jako neprůhledný popisovač, který identifikuje typ načtený do modulu runtime.  
  
 Pokud typ, který ICorDebugType představuje, ještě nebyl načten, vrátí tato metoda `CORDBG_E_CLASS_NOT_LOADED` .  Pokud typ není podporován, vrátí se `CORDBG_E_UNSUPPORTED` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugType2 – rozhraní](icordebugtype2-interface.md)
