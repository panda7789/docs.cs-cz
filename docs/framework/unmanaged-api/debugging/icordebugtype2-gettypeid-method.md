---
title: ICorDebugType2::GetTypeID Method
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3098911bab2878876b93ee1ce23d9794d7e6cdbd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772466"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2::GetTypeID Method
Získá [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) u tohoto typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 [out] Ukazatel [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento ICorDebugType.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kódu při selhání. `HRESULT` Kódy patří následující:  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|`S_OK`|Metoda byla úspěšná. Metoda byla načtena platný [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).|  
|`CORDBG_E_CLASS_NOT_LOADED`|Typ se nenačetl.|  
|`CORDBG_E_UNSUPPORTED`|Tento typ není podporovaný.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda poskytuje mapování z ICorDebugType, který představuje typ, který může nebo nemusí byla načtena do modulu runtime, na [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), která slouží jako neprůhledným zpracování, který identifikuje typ zavedeny do modulu runtime.  
  
 Pokud typ, který představuje ICorDebugType nebyl dosud bylo načteno, vrátí tato metoda `CORDBG_E_CLASS_NOT_LOADED`.  Pokud typ není podporován, vrátí `CORDBG_E_UNSUPPORTED`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugType2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
