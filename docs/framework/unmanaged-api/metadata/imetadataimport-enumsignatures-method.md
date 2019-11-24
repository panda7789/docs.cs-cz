---
title: IMetaDataImport::EnumSignatures – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: 9dbbdcc9d0fb9f0a8d2a64edfa4a0ad92570933c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450003"
---
# <a name="imetadataimportenumsignatures-method"></a>IMetaDataImport::EnumSignatures – metoda
Enumerates Signature tokens representing stand-alone signatures in the current scope.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] A pointer to the enumerator. This must be NULL for the first call of this method.  
  
 `rSignatures`  
 [out] The array used to store the Signature tokens.  
  
 `cMax`  
 [in] The maximum size of the `rSignatures` array.  
  
 `pcSignatures`  
 [out] The number of Signature tokens returned in `rSignatures`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumSignatures` returned successfully.|  
|`S_FALSE`|There are no tokens to enumerate. In that case, `pcSignatures` is zero.|  
  
## <a name="remarks"></a>Poznámky  
 The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
