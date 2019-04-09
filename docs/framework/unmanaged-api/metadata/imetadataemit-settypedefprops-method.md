---
title: IMetaDataEmit::SetTypeDefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 596888a8eb4a55c4cfe594b1911f17f6d32f56d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165929"
---
# <a name="imetadataemitsettypedefprops-method"></a>IMetaDataEmit::SetTypeDefProps – metoda
Nastaví funkce typu definované v předchozím volání [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [in] `mdTypeDef` Token získaný z volání původní [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atributy. To je bitová maska z `CorTypeAttr` hodnoty.  
  
 `tkExtends`  
 [in] `mdToken` Základní třídy. Získané z předchozího volání [imetadataemit::defineimporttype –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), nebo `null`.  
  
 `rtkImplements[]`  
 [in] Pole tokenů pro rozhraní, která tento typ implementuje. Tyto `mdTypeRef` tokeny jsou získány pomocí [imetadataemit::defineimporttype –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md). Poslední prvek pole musí být `mdTokenNil`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
