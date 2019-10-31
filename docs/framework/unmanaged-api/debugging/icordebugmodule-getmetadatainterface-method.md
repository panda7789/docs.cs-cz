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
ms.openlocfilehash: fb96949e22b4edfc0e64780a54bb38da44eb8369
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129550"
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
 mimo Ukazatel na adresu `T:IUnknown` objektu, který je jedním z [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program může pomocí metody `GetMetaDataInterface` vytvořit kopii původních metadat pro modul, který musí provést, aby bylo možné tento modul upravit. Ladicí program volá `GetMetaDataInterface` pro získání objektu rozhraní [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) pro modul, volá [IMetaDataEmit:: SaveToMemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) , aby uložil kopii metadat modulu do paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Metadata](../../../../docs/framework/unmanaged-api/metadata/index.md)
