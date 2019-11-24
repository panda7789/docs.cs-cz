---
title: IMetaDataImport::FindTypeDefByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
ms.openlocfilehash: b1b1c557eea62cae6d2ad09303441e4635abc899
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437837"
---
# <a name="imetadataimportfindtypedefbyname-method"></a>IMetaDataImport::FindTypeDefByName – metoda
Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szTypeDef`  
 [in] The name of the type for which to get the TypeDef token.  
  
 `tkEnclosingClass`  
 [in] A TypeDef or TypeRef token representing the enclosing class. If the type to find is not a nested class, set this value to NULL.  
  
 `ptd`  
 [out] A pointer to the matching TypeDef token.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
