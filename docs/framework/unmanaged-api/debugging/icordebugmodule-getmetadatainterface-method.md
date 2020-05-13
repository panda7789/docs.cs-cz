---
title: ICorDebugModule::GetMetaDataInterface – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
ms.openlocfilehash: 8f3cc16054d4b5340c9460e9c3fbcba6e563567a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212552"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface – metoda
Získá objekt rozhraní metadat, který lze použít k prohlédnutí metadat pro modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 pro Referenční ID, které určuje rozhraní metadat.  
  
 `ppObj`  
 mimo Ukazatel na adresu `T:IUnknown` objektu, který je jedním z [rozhraní metadat](../metadata/metadata-interfaces.md).  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program může použít `GetMetaDataInterface` metodu k vytvoření kopie původních metadat pro modul, který musí provést, aby bylo možné tento modul upravit. Ladicí program volá `GetMetaDataInterface` k získání objektu rozhraní [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) pro modul a pak zavolá [IMetaDataEmit:: SaveToMemory –](../metadata/imetadataemit-savetomemory-method.md) , aby uložil kopii metadat modulu do paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Metadata](../metadata/index.md)
