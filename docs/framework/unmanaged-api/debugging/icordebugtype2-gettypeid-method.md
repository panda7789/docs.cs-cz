---
title: "ICorDebugType2::GetTypeID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugType2.GetTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30b5259bfd39ac0c8c8b717d59a8d3165f6b6cbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2::GetTypeID – metoda
Získá [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [out] Ukazatel [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento ICorDebugType.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kód při selhání. `HRESULT` Kódy zahrnují následující:  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|`S_OK`|Metoda byla úspěšná. Metoda má načíst platná [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).|  
|`CORDBG_E_CLASS_NOT_LOADED`|Typ nebyla načtena.|  
|`CORDBG_E_UNSUPPORTED`|Typ není podporován.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda poskytuje mapování z ICorDebugType, který představuje typ, který může nebo nemusí mít byla načtena do modulu runtime pro [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), která slouží jako neprůhledné zpracování, který identifikuje typu načíst do modulu runtime.  
  
 Pokud typ, který představuje ICorDebugType nebyl dosud bylo načteno, vrátí tato metoda `CORDBG_E_CLASS_NOT_LOADED`.  Pokud není podporován typ, vrátí `CORDBG_E_UNSUPPORTED`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugType2 rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
