---
title: "IMetaDataImport::GetMethodSemantics – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f8921c4f6a676c9647d4e8907a22f0d68b0b359
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmethodsemantics-method"></a>IMetaDataImport::GetMethodSemantics – metoda
Získá příznaky udávající vztah mezi metoda odkazuje zadaný token MethodDef a spárované vlastnosti a události odkazuje zadaný EventProp token.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mb`  
 [v] MethodDef token představující metodu k získání informací sémantického role pro.  
  
 `tkEventProp`  
 [v] Token představující spárované vlastností a událostí, pro které chcete získat role metody.  
  
 `pdwSemanticsFlags`  
 [out] Ukazatel na přidružené sémantiku příznaků. Tato hodnota je bitová maska z [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) výčtu.  
  
## <a name="remarks"></a>Poznámky  
 [Imetadataemit::defineproperty –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) metoda nastaví příznaky sémantiku metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
