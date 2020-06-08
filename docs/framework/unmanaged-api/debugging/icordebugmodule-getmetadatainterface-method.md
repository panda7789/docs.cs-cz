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
ms.openlocfilehash: f5d0dd7a99087b21a5f827e4dce0f6342ae7b25a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501765"
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
 Ladicí program může použít `GetMetaDataInterface` metodu k vytvoření kopie původních metadat pro modul, který musí provést, aby bylo možné tento modul upravit. Ladicí program volá `GetMetaDataInterface` k získání objektu rozhraní [IMetaDataEmit](../metadata/imetadataemit-interface.md) pro modul a pak zavolá [IMetaDataEmit:: SaveToMemory –](../metadata/imetadataemit-savetomemory-method.md) , aby uložil kopii metadat modulu do paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Metadata](../metadata/index.md)
