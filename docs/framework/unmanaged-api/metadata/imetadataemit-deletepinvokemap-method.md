---
title: IMetaDataEmit::DeletePinvokeMap – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ea100ff86286cb98db5aa9fa6f3c12f5d318a90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217741"
---
# <a name="imetadataemitdeletepinvokemap-method"></a>IMetaDataEmit::DeletePinvokeMap – metoda
Zničí metadat PInvoke mapování pro objekt odkazovaný zadaným parametrem zadaného tokenu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [in] `mdFieldDef` Nebo `mdMethodDef` token, který představuje objekt, pro kterou chcete odstranit mapování metadat PInvoke.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
