---
title: IMetaDataImport::EnumTypeRefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: 778ebf1d4fad0c8703964be88fdc3ff8c033bc28
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449981"
---
# <a name="imetadataimportenumtyperefs-method"></a>IMetaDataImport::EnumTypeRefs – metoda
Enumerates TypeRef tokens defined in the current metadata scope.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] A pointer to the enumerator. This must be NULL for the first call of this method.  
  
 `rTypeRefs`  
 [out] The array used to store the TypeRef tokens.  
  
 `cMax`  
 [in] The maximum size of the `rTypeRefs` array.  
  
 `pcTypeRefs`  
 [out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeRefs` returned successfully.|  
|`S_FALSE`|There are no tokens to enumerate. In that case, `pcTypeRefs` is zero.|  
  
## <a name="remarks"></a>Poznámky  
 A TypeRef token represents a reference to a type.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
