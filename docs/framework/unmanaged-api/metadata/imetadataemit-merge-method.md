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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3fee3c0b82bec102d8e292a76d3df5a14d40ace8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757668"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge – metoda
Přidá do seznamu oborů, která se má sloučit zadané importované oboru.  
  
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
 [in] Ukazatel [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objekt, který identifikuje importované oboru ke sloučení.  
  
 `pIMap`  
 [in] Ukazatel [imaptoken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) objekt, který určuje, token přemapovat.  
  
 `pHandler`  
 [in] Ukazatel [IUnknown](/cpp/atl/iunknown) objekt, který určuje chyby.  
  
## <a name="remarks"></a>Poznámky  
 Volání [imetadataemit::mergeend –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) k aktivaci spojení metadat do jednoho oboru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
