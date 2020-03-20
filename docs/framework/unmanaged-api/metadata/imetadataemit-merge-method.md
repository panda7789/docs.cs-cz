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
ms.openlocfilehash: 759358822ed865c89f6f55084d1e7f6143506e93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175704"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge – metoda
Přidá zadaný importovaný obor do seznamu oborů, které mají být sloučeny.  
  
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
 [v] Ukazatel na objekt [IMetaDataImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) který identifikuje importovaný obor, který má být sloučen.  
  
 `pIMap`  
 [v] Ukazatel na objekt [IMapToken,](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) který určuje znovu namapovat token.  
  
 `pHandler`  
 [v] Ukazatel na objekt [IUnknown,](/cpp/atl/iunknown) který určuje chyby.  
  
## <a name="remarks"></a>Poznámky  
 Volání [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) pro aktivaci sloučení metadat do jednoho oboru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
