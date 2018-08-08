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
ms.openlocfilehash: 98997bfbb7d3c9343f78438b1195222565c5b9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444548"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge – metoda
Zadaný obor importované přidá do seznamu oborů, který se má sloučit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pImport`  
 [v] Ukazatel na [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objekt, který identifikuje importované oboru, který se má sloučit.  
  
 `pIMap`  
 [v] Ukazatel na [imaptoken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) objekt, který určuje, tokenu znovu namapovat.  
  
 `pHandleer`  
 [v] Ukazatel na <!--<<!--zzxref:IUnknown --> `IUnknown` >-->  `IUnknown` objekt, který určuje chyby.  
  
## <a name="remarks"></a>Poznámky  
 Volání [imetadataemit::mergeend –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) k aktivaci fúze metadat do jednoho oboru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
