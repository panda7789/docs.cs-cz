---
title: IMetaDataEmit::Merge – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 06894f238f9fda3111d5484bb1b2add183a5abb2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448053"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge – metoda
Přidá zadaný importovaný obor do seznamu rozsahů, které se mají sloučit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pImport`  
 pro Ukazatel na objekt [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , který identifikuje importovaný obor, který se má sloučit.  
  
 `pIMap`  
 pro Ukazatel na objekt [IMapToken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) , který určuje opětovné mapování tokenu.  
  
 `pHandler`  
 pro Ukazatel na objekt [IUnknown](/cpp/atl/iunknown) , který určuje chyby.  
  
## <a name="remarks"></a>Poznámky  
 Zavolejte [IMetaDataEmit:: MergeEnd –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) , aby se aktivovala fúze metadat do jednoho oboru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
