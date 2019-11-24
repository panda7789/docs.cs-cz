---
title: IMetaDataImport::EnumFieldsWithName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: b240be3e5b0127de42cea43dd8e89a2cc656b28e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449512"
---
# <a name="imetadataimportenumfieldswithname-method"></a>IMetaDataImport::EnumFieldsWithName – metoda
Enumerates FieldDef tokens of the specified type with the specified name.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] A pointer to the enumerator.  
  
 `cl`  
 [in] The token of the type whose fields are to be enumerated.  
  
 `szName`  
 [in] The field name that limits the scope of the enumeration.  
  
 `rFields`  
 [out] Array used to store the FieldDef tokens.  
  
 `cMax`  
 [in] The maximum size of the `rFields` array.  
  
 `pcTokens`  
 [out] The actual number of FieldDef tokens returned in `rFields`.  
  
## <a name="remarks"></a>Poznámky  
 Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumFieldsWithName` returned successfully.|  
|`S_FALSE`|There are no fields to enumerate. In that case, `pcTokens` is zero.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
