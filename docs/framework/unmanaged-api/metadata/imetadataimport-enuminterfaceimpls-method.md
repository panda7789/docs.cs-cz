---
title: IMetaDataImport::EnumInterfaceImpls – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 4c819bff50e6644a733374e9863d670d3323ee68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449532"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls – metoda
Enumerates all interfaces implemented by the specified `TypeDef`. 
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] A pointer to the enumerator.  
  
 `td`  
 [in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.  
  
 `rImpls`  
 [out] The array used to store the MethodDef tokens.  
  
 `cMax`  
 [in] The maximum size of the `rImpls` array.  
  
 `pcImpls`  
 [out] The actual number of tokens returned in `rImpls`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` returned successfully.|  
|`S_FALSE`|There are no MethodDef tokens to enumerate. In that case, `pcImpls` is set to zero.|  

## <a name="remarks"></a>Poznámky

The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`. Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`). Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
